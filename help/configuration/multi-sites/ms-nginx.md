---
title: Mehrere Websites mit Nginx einrichten
description: In diesem Tutorial erfahren Sie, wie Sie mehrere Websites mit Nginx einrichten.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '962'
ht-degree: 0%

---


# Mehrere Websites mit Nginx einrichten

Wir gehen davon aus, dass

- Sie arbeiten an einer Entwicklungsmaschine (Laptop, virtuelle Maschine oder Ähnliches).

   Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie von Ihrem Hosting-Provider.

   Für die Einrichtung von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Nachdem Sie die in diesem Thema behandelten Aufgaben abgeschlossen haben, lesen Sie [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) im _Leitfaden zu Commerce on Cloud Infrastructure_.

- Sie akzeptieren mehrere Domänen in einer Virtual-Host-Datei oder verwenden einen virtuellen Host pro Website. die Konfigurationsdateien des virtuellen Hosts befinden sich unter `/etc/nginx/sites-available`.
- Sie verwenden die `nginx.conf.sample` von Commerce bereitgestellt werden, wobei nur die in diesem Tutorial behandelten Änderungen enthalten sind.
- Die Commerce-Software ist in `/var/www/html/magento2`.
- Sie haben zwei andere Websites als die Standardwebsite:

   - `french.mysite.mg` mit Website-Code `french` und Store-Ansichtscode `fr`
   - `german.mysite.mg` mit Website-Code `german` und Store-Ansichtscode `de`
   - `mysite.mg` ist die standardmäßige Website- und Store-Ansicht

>[!TIP]
>
>Siehe [Websites erstellen](ms-admin.md#step-2-create-websites) und [Erstellen von Store-Ansichten](ms-admin.md#step-4-create-store-views) für Hilfe bei der Suche nach diesen Werten.

Im Folgenden finden Sie eine Roadmap zum Einrichten mehrerer Websites mit nginx:

1. [Einrichten von Websites, Geschäften und Speichern von Ansichten](ms-admin.md) im Admin.
1. Erstellen Sie eine [Nginx-virtueller Host](#step-2-create-nginx-virtual-hosts)), um viele Websites oder einen virtuellen Nginx-Host pro Commerce-Website zuzuordnen (siehe folgende Schritte).
1. Übergeben Sie die Werte der [MAGE-Variablen](ms-overview.md) `$MAGE_RUN_TYPE` und `$MAGE_RUN_CODE` nginx mit dem bereitgestellten Magento `nginx.conf.sample` (siehe folgende Schritte).

   - `$MAGE_RUN_TYPE` kann `store` oder `website`:

      - Verwendung `website` , um Ihre Website in Ihre Storefront zu laden.
      - Verwendung `store` , um eine beliebige Store-Ansicht in Ihre Storefront zu laden.
   - `$MAGE_RUN_CODE` ist der eindeutige Website- oder Store-Ansichtscode, der `$MAGE_RUN_TYPE`.


1. Aktualisieren Sie die Basis-URL-Konfiguration auf dem Commerce-Administrator.

## Schritt 1: Erstellen von Websites, Geschäften und Speichern von Ansichten in der Admin-Konsole

Siehe [Einrichten mehrerer Websites, Stores und Speichern von Ansichten in der Admin-Konsole](ms-admin.md).

## Schritt 2: Erstellen nginx virtueller Hosts

In diesem Schritt wird beschrieben, wie Sie Websites auf der [storefront](https://glossary.magento.com/storefront). Sie können entweder Websites oder Ansichten speichern. Wenn Sie Store-Ansichten verwenden, müssen Sie die Parameterwerte entsprechend anpassen. Sie müssen die Aufgaben in diesem Abschnitt als Benutzer mit `sudo` Berechtigungen.

Durch Verwendung von nur einer [nginx virtual host file](#step-2-create-nginx-virtual-hosts), können Sie Ihre nginx-Konfiguration einfach und sauber halten. Durch die Verwendung mehrerer virtueller Host-Dateien können Sie jeden Store anpassen (um einen benutzerdefinierten Speicherort für `french.mysite.mg` z. B. ).

**So erstellen Sie einen virtuellen Host** (vereinfacht):

Diese Konfiguration erweitert auf [nginx-Konfiguration](../../installation/prerequisites/web-server/nginx.md).

1. Öffnen Sie den Texteditor und fügen Sie die folgenden Inhalte zu einer neuen Datei mit dem Namen `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Speichern Sie Ihre Änderungen in den Dateien und beenden Sie den Texteditor.
1. Überprüfen Sie die Serverkonfiguration:

   ```bash
   nginx -t
   ```

1. Bei Erfolg wird die folgende Meldung angezeigt:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Wenn Fehler angezeigt werden, überprüfen Sie die Syntax Ihrer Konfigurationsdateien für virtuelle Hosts.

1. Erstellen Sie eine symbolische Verknüpfung im `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Weitere Informationen zur Zuordnungsrichtlinie finden Sie unter [nginx-Dokumentation zur Zuordnungsrichtlinie](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**So erstellen Sie mehrere virtuelle Hosts**:

1. Öffnen Sie den Texteditor und fügen Sie die folgenden Inhalte zu einer neuen Datei mit dem Namen `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Erstellen Sie eine weitere Datei mit dem Namen `german.mysite.mg` im selben Verzeichnis mit folgendem Inhalt:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Speichern Sie Ihre Änderungen in den Dateien und beenden Sie den Texteditor.
1. Überprüfen Sie die Serverkonfiguration:

   ```bash
   nginx -t
   ```

1. Bei Erfolg wird die folgende Meldung angezeigt:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Wenn Fehler angezeigt werden, überprüfen Sie die Syntax Ihrer Konfigurationsdateien für virtuelle Hosts.

1. Erstellen Sie symbolische Verknüpfungen in der `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Schritt 3: Ändern Sie nginx.conf.sample.

>[!TIP]
>
>Bearbeiten Sie nicht die `nginx.conf.sample` Datei; Es handelt sich um eine Commerce-Kerndatei, die mit jeder neuen Version aktualisiert werden kann. Kopieren Sie stattdessen die `nginx.conf.sample` -Datei, benennen Sie sie um und bearbeiten Sie dann die kopierte Datei.

**Bearbeiten des PHP-Einstiegspunkts für die Hauptanwendung**:

So ändern Sie die `nginx.conf.sample` file**:

1. Öffnen Sie den Texteditor und überprüfen Sie die `nginx.conf.sample` Datei ,`<magento2_installation_directory>/nginx.conf.sample`. Suchen Sie nach dem folgenden Abschnitt:

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Aktualisieren Sie die `nginx.conf.sample` -Datei mit den folgenden beiden Zeilen vor der Include-Anweisung:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Ein Beispiel für einen aktualisierten PHP-Einstiegspunkt für die Hauptanwendung sieht wie folgt aus:

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Schritt 4: Aktualisieren der Basis-URL-Konfiguration

Sie müssen die Basis-URL für die `french` und `german` Websites in der Commerce-Admin.

### Aktualisieren der Basis-URL der französischen Website

1. Melden Sie sich beim Commerce-Administrator an und navigieren Sie zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.
1. Ändern Sie die _Konfigurationsbereich_ der `french` Website.
1. Erweitern **Basis-URLs** und aktualisieren Sie die **Basis-URL** und **Basis-Link-URL** Wert zu `http://french.magento24.com/`.
1. Erweitern **Basis-URLs (sicher)** und aktualisieren Sie die **Sichere Basis-URL** und **Sichere Basis-Link-URL** Wert zu `https://french.magento24.com/`.
1. Klicken **Konfiguration speichern** und speichern Sie die Konfigurationsänderungen.

### Aktualisieren der deutschen Website-Basis-URL

1. Melden Sie sich beim Commerce-Administrator an und navigieren Sie zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.
1. Ändern Sie die _Konfigurationsbereich_ der `german` Website.
1. Erweitern **Basis-URLs** und aktualisieren Sie die **Basis-URL** und **Basis-Link-URL** Wert zu `http://german.magento24.com/`.
1. Erweitern **Basis-URLs (sicher)** und aktualisieren Sie die **Sichere Basis-URL** und **Sichere Basis-Link-URL** Wert zu `https://german.magento24.com/`.
1. Klicken **Konfiguration speichern** und speichern Sie die Konfigurationsänderungen.

### Cache leeren

Führen Sie den folgenden Befehl aus, um den `config` und `full_page` Caches.

```bash
bin/magento cache:clean config full_page
```

## Überprüfen der Site

Sofern kein DNS für die URLs Ihrer Stores eingerichtet ist, müssen Sie eine statische Route zum Host in Ihrem `hosts` Datei:

1. Betriebssystem suchen `hosts` -Datei.
1. Fügen Sie die statische Route im Format hinzu:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Rufen Sie eine der folgenden URLs in Ihrem Browser auf:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie von Ihrem Hosting-Provider.
>- Für die Einrichtung von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. see [Einrichten mehrerer Cloud-Websites oder -Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) im _Leitfaden zu Commerce on Cloud Infrastructure_.


### Fehlerbehebung

- Wenn Ihre französischen und deutschen Sites 404 s zurückgeben, Ihr Admin jedoch geladen wird, stellen Sie sicher, dass Sie [Schritt 6: Fügen Sie den Store-Code zur Basis-URL hinzu.](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Wenn alle URLs 404 s zurückgeben, stellen Sie sicher, dass Sie Ihren Webserver neu starten.
- Wenn der Administrator nicht ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie Ihre virtuellen Hosts ordnungsgemäß eingerichtet haben.
