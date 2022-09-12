---
title: Basisverzeichnis zur Verbesserung der Sicherheit ändern
description: Verhindern des nicht autorisierten browserbasierten Zugriffs auf Adobe Commerce oder die Magento Open Source des lokalen Dateisystems.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Basisverzeichnis zur Verbesserung der Sicherheit ändern

Bei einer Standardinstallation mit einem Apache-Webserver werden Adobe Commerce und Magento Open Source im Standardwebstamm installiert: `/var/www/html/magento2`.

Die `magento2/` -Verzeichnis enthält Folgendes:

- `pub/`
- `setup/`
- `var/`

Der Antrag wird von `/var/www/html/magento2/pub`. Der Rest des Dateisystems ist anfällig, da er über einen Browser zugänglich ist.
Festlegen des Webstamms auf `pub/` verhindert, dass Site-Besucher über einen Browser auf sensible Bereiche des Dateisystems zugreifen.

Hier wird beschrieben, wie Sie das Apache-Basisverzeichnis auf einer vorhandenen Instanz ändern, um Dateien aus dem `pub/` -Verzeichnis, das sicherer ist.

## Ein Hinweis zu nginx

Wenn Sie [nginx](../prerequisites/web-server/nginx.md) und [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) -Datei im Installationsverzeichnis enthalten ist, werden Sie wahrscheinlich bereits Dateien aus dem `pub/` Verzeichnis.

Bei Verwendung in Ihrem Serverblock, der Ihre Site definiert, wird die Variable `nginx.conf.sample` -Konfiguration überschreibt die Basisverzeichnis-Einstellungen Ihres Servers, um Dateien aus dem `pub/` Verzeichnis. Siehe beispielsweise die letzte Zeile in der folgenden Konfiguration:

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Bevor Sie beginnen

Um dieses Tutorial abzuschließen, benötigen Sie Zugriff auf eine funktionierende Installation, die auf einer [LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) stack:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) oder OpenSearch (1.2)
- Adobe Commerce oder Magento Open Source (2.4+)

>[!NOTE]
>
>Siehe [Voraussetzungen](../prerequisites/overview.md) und [Installationsanleitung](../overview.md) für weitere Informationen.

## 1. Bearbeiten der Serverkonfiguration

Der Name und der Speicherort Ihrer Virtual-Host-Datei hängt davon ab, welche Version von Apache Sie ausführen. Dieses Beispiel zeigt den Namen und den Speicherort der virtuellen Host-Datei auf Apache v2.4.

1. Melden Sie sich bei Ihrem Anwendungsserver an.
1. Bearbeiten Sie Ihre virtuelle Host-Datei:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Fügen Sie den Pfad zu Ihrem `pub/` Verzeichnis in `DocumentRoot` Richtlinie:

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Starten Sie Apache neu:

   ```bash
   systemctl restart apache2
   ```

## 2. Aktualisieren der Basis-URL

Wenn Sie einen Ordnernamen an den Hostnamen oder die IP-Adresse Ihres Servers angehängt haben, um die Basis-URL zu erstellen, wenn Sie die Anwendung installiert haben (z. B. `http://192.168.33.10/magento2`), müssen Sie sie entfernen.

>[!NOTE]
>
>Ersetzen `192.168.33.10` mit dem Hostnamen Ihres Servers.

1. Melden Sie sich bei der Datenbank an:

   ```bash
   mysql -u <user> -p
   ```

1. Geben Sie die Datenbank an, die Sie bei der Installation des Programms erstellt haben:

   ```shell
   use <database-name>
   ```

1. Aktualisieren Sie die Basis-URL:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Aktualisieren Sie die Datei env.php .

Hängen Sie den folgenden Knoten an die `env.php` -Datei.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Siehe Abschnitt [env.php-Referenz](../../configuration/reference/config-reference-envphp.md) für weitere Informationen.

## 4. Wechseln der Modi

[Anwendungsmodi](../../configuration/bootstrap/application-modes.md), zu denen `production` und `developer`, die die Sicherheit verbessern und die Entwicklung erleichtern sollen. Wie die Namen nahe legen, sollten Sie zu `developer` Modus beim Erweitern oder Anpassen der Anwendung und Wechseln zu `production` -Modus, wenn sie in einer Live-Umgebung ausgeführt wird.

Der Wechsel zwischen den Modi ist ein wichtiger Schritt, um zu überprüfen, ob Ihre Serverkonfiguration ordnungsgemäß funktioniert. Sie können mit dem CLI-Tool zwischen den Modi wechseln:

1. Wechseln Sie zu Ihrem Installationsverzeichnis.
1. Wechseln zu `production` -Modus.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aktualisieren Sie Ihren Browser und überprüfen Sie, ob die Storefront korrekt angezeigt wird.
1. Wechseln zu `developer` -Modus.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aktualisieren Sie Ihren Browser und überprüfen Sie, ob die Storefront korrekt angezeigt wird.

## 5. Überprüfen der Storefront

Navigieren Sie zu [storefront](https://glossary.magento.com/storefront) in einem Webbrowser, um zu überprüfen, ob alles funktioniert.

1. Öffnen Sie einen Webbrowser und geben Sie den Hostnamen oder die IP-Adresse Ihres Servers in die Adressleiste ein. Beispiel, `http://192.168.33.10`.

   Die folgende Abbildung zeigt eine Beispiel-Storefront-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

   ![Storefront, die eine erfolgreiche Installation überprüft](../../assets/installation/install-success_store.png)

   Siehe Abschnitt [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360032994352) , wenn auf der Seite ein 404-Fehler (Nicht gefunden) angezeigt wird oder andere Assets wie Bilder, CSS und JS nicht geladen werden können.

1. Versuchen Sie, über einen Browser auf ein Anwendungsverzeichnis zuzugreifen. Hängen Sie den Ordnernamen an den Hostnamen oder die IP-Adresse Ihres Servers in der Adressleiste an:

   Wenn die Meldung 404 oder &quot;Zugriff verweigert&quot;angezeigt wird, haben Sie den Zugriff auf das Dateisystem erfolgreich eingeschränkt.

   ![Zugriff verweigert](../../assets/installation/access-denied.png)
