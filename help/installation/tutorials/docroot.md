---
title: Ändern des Stammverzeichnisses zur Verbesserung der Sicherheit
description: Verhindern Sie nicht autorisierten browserbasierten Zugriff auf das lokale Dateisystem von Adobe Commerce.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Ändern des Stammverzeichnisses zur Verbesserung der Sicherheit

Bei einer Standardinstallation mit einem Apache-Webserver wird Adobe Commerce im Standard-Webstamm installiert: `/var/www/html/magento2`.

Das `magento2/`-Verzeichnis enthält Folgendes:

- `pub/`
- `setup/`
- `var/`

Die Anwendung wird von `/var/www/html/magento2/pub` bereitgestellt. Der Rest des Dateisystems ist anfällig, weil es von einem Browser aus zugänglich ist.
Wenn Sie den Webstamm auf das `pub/` Verzeichnis setzen, können Besucher der Site von einem Browser aus nicht auf sensible Bereiche des Dateisystems zugreifen.

In diesem Thema wird beschrieben, wie Sie den Apache-Stamm in einer vorhandenen Instanz so ändern, dass Dateien aus dem sichereren `pub/` bereitgestellt werden.

## Ein Hinweis zu nginx

Wenn Sie [nginx](../prerequisites/web-server/nginx.md) verwenden und die [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) Datei im Installationsverzeichnis enthalten ist, stellen Sie wahrscheinlich bereits Dateien aus dem `pub/` Verzeichnis bereit.

Bei Verwendung in Ihrem Server-Block, der Ihre Site definiert, überschreibt die `nginx.conf.sample`-Konfiguration die docroot-Einstellungen Ihres Servers, um Dateien aus dem `pub/` Verzeichnis bereitzustellen. Ein Beispiel finden Sie in der letzten Zeile in der folgenden Konfiguration:

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

Um dieses Tutorial abzuschließen, benötigen Sie Zugriff auf eine funktionierende Installation, die auf einem LAMP-Stack ausgeführt wird:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) oder OpenSearch (1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>Weitere Informationen finden [&#x200B; unter &#x200B;](../prerequisites/overview.md) und [Installationshandbuch](../overview.md).

## &#x200B;1. Serverkonfiguration bearbeiten

Name und Speicherort der virtuellen Host-Datei hängen davon ab, welche Apache-Version Sie ausführen. Dieses Beispiel zeigt den Namen und den Speicherort der virtuellen Host-Datei in Apache v2.4.

1. Melden Sie sich beim Anwendungs-Server an.
1. Bearbeiten der virtuellen Host-Datei:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Fügen Sie den Pfad zu Ihrem `pub/`-Verzeichnis zur `DocumentRoot`-Anweisung hinzu:

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

1. Apache neu starten:

   ```bash
   systemctl restart apache2
   ```

## &#x200B;2. Aktualisieren der Basis-URL

Wenn Sie bei der Installation der Anwendung einen Verzeichnisnamen an den Hostnamen oder die IP-Adresse Ihres Servers angehängt haben, um die Basis-URL zu erstellen (z. B. `http://192.168.33.10/magento2`), müssen Sie sie entfernen.

>[!NOTE]
>
>Ersetzen Sie `192.168.33.10` durch den Hostnamen Ihres Servers.

1. Melden Sie sich bei der Datenbank an:

   ```bash
   mysql -u <user> -p
   ```

1. Geben Sie die Datenbank an, die Sie bei der Installation der Anwendung erstellt haben:

   ```shell
   use <database-name>
   ```

1. Aktualisieren Sie die Basis-URL:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## &#x200B;3. Aktualisieren Sie die Datei env.php

Hängen Sie den folgenden Knoten an die `env.php` an.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Weitere Informationen finden Sie in [env.php](../../configuration/reference/config-reference-envphp.md)Referenz.

## &#x200B;4. Modi wechseln

[Anwendungsmodi](../../configuration/bootstrap/application-modes.md) zu denen `production` und `developer` gehören, wurden entwickelt, um die Sicherheit zu verbessern und die Entwicklung zu erleichtern. Wie aus den Namen hervorgeht, sollten Sie beim Erweitern oder Anpassen der Anwendung in den `developer` Modus und beim Ausführen in einer Live-Umgebung in den `production` Modus wechseln.

Der Wechsel zwischen den Modi ist ein wichtiger Schritt, um zu überprüfen, ob Ihre Server-Konfiguration ordnungsgemäß funktioniert. Mit dem CLI-Tool können Sie zwischen den Modi wechseln:

1. Navigieren Sie zu Ihrem Installationsverzeichnis.
1. Wechseln Sie in den `production`.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aktualisieren Sie Ihren Browser und stellen Sie sicher, dass die Storefront ordnungsgemäß angezeigt wird.
1. Wechseln Sie in den `developer`.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aktualisieren Sie Ihren Browser und stellen Sie sicher, dass die Storefront ordnungsgemäß angezeigt wird.

## &#x200B;5. Überprüfen Sie die Storefront

Gehen Sie zur Storefront in einem Webbrowser, um zu überprüfen, ob alles funktioniert.

1. Öffnen Sie einen Webbrowser und geben Sie den Hostnamen oder die IP-Adresse Ihres Servers in die Adressleiste ein. Beispiel: `http://192.168.33.10`.

   Die folgende Abbildung zeigt eine Beispiel-Storefront-Seite. Wenn sie wie folgt angezeigt wird, war Ihre Installation erfolgreich!

   ![Storefront, die eine erfolgreiche Installation überprüft](../../assets/installation/install-success_store.png)

   Siehe den Abschnitt [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360032994352), wenn auf der Seite die Meldung 404 (Nicht gefunden) angezeigt wird oder andere Assets wie Bilder, CSS und JS nicht geladen werden können.

1. Versuchen Sie, über einen Browser auf ein Anwendungsverzeichnis zuzugreifen. Hängen Sie den Verzeichnisnamen an den Hostnamen oder die IP-Adresse Ihres Servers in der Adressleiste an:

   Wenn die Meldung „Zugriff verweigert“ oder „404“ angezeigt wird, haben Sie den Zugriff auf das Dateisystem erfolgreich eingeschränkt.

   ![Zugriff verweigert](../../assets/installation/access-denied.png)
