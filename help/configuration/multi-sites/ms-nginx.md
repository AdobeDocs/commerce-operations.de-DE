---
title: Einrichten mehrerer Websites mit Nginx
description: In diesem Tutorial können Sie mehrere Websites mit Nginx einrichten.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Einrichten mehrerer Websites mit Nginx

Wir gehen davon aus, dass

- Sie arbeiten auf einer Entwicklungsmaschine (Laptop, virtuelle Maschine oder Ähnliches).

  Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie bei Ihrem Hosting-Anbieter.

  Zum Einrichten von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Nachdem Sie die in diesem Thema besprochenen Aufgaben abgeschlossen haben, finden Sie weitere Informationen unter [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de) im Handbuch zu _Commerce in Cloud-Infrastruktur_.

- Sie akzeptieren mehrere Domains in einer Virtual-Host-Datei oder verwenden einen Virtual-Host pro Website. Die Virtual-Host-Konfigurationsdateien befinden sich in `/etc/nginx/sites-available`.
- Sie verwenden die von Commerce bereitgestellte `nginx.conf.sample` nur mit den Änderungen, die in diesem Tutorial erläutert werden.
- Die Commerce-Software ist in `/var/www/html/magento2` installiert.
- Neben der Standardeinstellung gibt es zwei weitere Websites:

   - `french.mysite.mg` mit Website-Code-`french` und Store-Ansicht-Code-`fr`
   - `german.mysite.mg` mit Website-Code-`german` und Store-Ansicht-Code-`de`
   - `mysite.mg` ist die standardmäßige Website- und Store-Ansicht

>[!TIP]
>
>Unter [Erstellen von Websites](ms-admin.md#step-2-create-websites) und [Erstellen von Store-Ansichten](ms-admin.md#step-4-create-store-views) erhalten Sie Hilfe beim Suchen dieser Werte.

Im Folgenden finden Sie eine Roadmap für die Einrichtung mehrerer Websites mit nginx:

1. [Einrichten von Websites, Stores und Store-Ansichten](ms-admin.md) im Admin-Bereich.
1. Erstellen Sie einen [virtuellen Nginx-Host](#step-2-create-nginx-virtual-hosts)), um viele Websites oder einen virtuellen Nginx-Host pro Commerce-Website zuzuordnen (Schritte unten beschrieben).
1. Übergeben Sie die Werte der [MAGE-Variablen](ms-overview.md) `$MAGE_RUN_TYPE` und `$MAGE_RUN_CODE` mithilfe der von Magento bereitgestellten `nginx.conf.sample` an nginx (Schritte unten beschrieben).

   - `$MAGE_RUN_TYPE` kann entweder `store` oder `website` sein:

      - Verwenden Sie `website` , um Ihre Website in Ihre Storefront zu laden.
      - Verwenden Sie `store`, um eine beliebige Store-Ansicht in Ihre Storefront zu laden.

   - `$MAGE_RUN_CODE` ist der eindeutige Website- oder Store-Ansichts-Code, der `$MAGE_RUN_TYPE` entspricht.

1. Aktualisieren Sie die Basis-URL-Konfiguration auf der Commerce-Admin.

## Schritt 1: Erstellen von Websites, Stores und Store-Ansichten im Admin-Bereich

Siehe [Einrichten mehrerer Websites, Stores und Store-Ansichten im Admin](ms-admin.md).

## Schritt 2: Erstellen virtueller nginx-Hosts

In diesem Schritt wird beschrieben, wie Websites in die Storefront geladen werden. Sie können entweder Websites oder Store-Ansichten verwenden. Wenn Sie Store-Ansichten verwenden, müssen Sie die Parameterwerte entsprechend anpassen. Sie müssen die Aufgaben in diesem Abschnitt als Benutzer mit `sudo` Berechtigungen ausführen.

Mit nur einer [nginx Virtual Host-Datei](#step-2-create-nginx-virtual-hosts) können Sie Ihre nginx-Konfiguration einfach und sauber halten. Durch die Verwendung mehrerer Virtual-Host-Dateien können Sie jeden Store anpassen (um z. B. einen benutzerdefinierten Speicherort für `french.mysite.mg` zu verwenden).

**So erstellen Sie einen virtuellen Host** (vereinfacht):

Diese Konfiguration erweitert die [nginx-Konfiguration](../../installation/prerequisites/web-server/nginx.md).

1. Öffnen Sie einen Texteditor und fügen Sie folgende Inhalte zu einer neuen Datei mit dem Namen `/etc/nginx/sites-available/magento` hinzu:

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
1. Überprüfen Sie die Server-Konfiguration:

   ```bash
   nginx -t
   ```

1. Bei erfolgreicher Ausführung wird die folgende Meldung angezeigt:

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Wenn Fehler angezeigt werden, überprüfen Sie die Syntax Ihrer virtuellen Host-Konfigurationsdateien.

1. Erstellen Sie eine symbolische Verknüpfung im `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Weitere Informationen zur Map-Direktive finden Sie unter [nginx-Dokumentation zur Map-Direktive](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**So erstellen Sie mehrere virtuelle Hosts**:

1. Öffnen Sie einen Texteditor und fügen Sie folgende Inhalte zu einer neuen Datei mit dem Namen `/etc/nginx/sites-available/french.mysite.mg` hinzu:

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
1. Überprüfen Sie die Server-Konfiguration:

   ```bash
   nginx -t
   ```

1. Bei erfolgreicher Ausführung wird die folgende Meldung angezeigt:

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Wenn Fehler angezeigt werden, überprüfen Sie die Syntax Ihrer virtuellen Host-Konfigurationsdateien.

1. Erstellen Sie symbolische Links im `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Schritt 3: Ändern Sie nginx.conf.sample

>[!TIP]
>
>Bearbeiten Sie die `nginx.conf.sample` nicht. Es handelt sich dabei um eine Commerce-Kerndatei, die mit jeder neuen Version aktualisiert werden kann. Kopieren Sie stattdessen die `nginx.conf.sample`, benennen Sie sie um und bearbeiten Sie dann die kopierte Datei.

**So bearbeiten Sie den PHP-Einstiegspunkt für die Hauptanwendung**:

So ändern Sie die `nginx.conf.sample`**:

1. Öffnen Sie einen Texteditor und überprüfen Sie die `nginx.conf.sample` Datei ,`<magento2_installation_directory>/nginx.conf.sample`. Suchen Sie nach dem folgenden Abschnitt:

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

1. Aktualisieren Sie die `nginx.conf.sample` mit den folgenden beiden Zeilen vor der include-Anweisung:

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

Sie müssen die Basis-URL für die `french` und die `german` Websites in Commerce Admin aktualisieren.

### Aktualisierung der französischen Website-Basis-URL

1. Melden Sie sich bei Commerce Admin an und navigieren Sie zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.
1. Ändern Sie den _Konfigurationsbereich_ auf die `french`-Website.
1. Erweitern Sie **Abschnitt „Basis** URLs“ und aktualisieren Sie den **Basis-URL** und **Basis-Link-URL** Wert auf `http://french.magento24.com/`.
1. Erweitern Sie **Basis-URLs (sicher** und aktualisieren Sie den **Sichere Basis-URL** und **Sichere Basis-Link-**) auf `https://french.magento24.com/`.
1. Klicken Sie **Konfiguration speichern** und speichern Sie die Konfigurationsänderungen.

### Aktualisieren der deutschen Website-Basis-URL

1. Melden Sie sich bei Commerce Admin an und navigieren Sie zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.
1. Ändern Sie den _Konfigurationsbereich_ auf die `german`-Website.
1. Erweitern Sie **Abschnitt „Basis** URLs“ und aktualisieren Sie den **Basis-URL** und **Basis-Link-URL** Wert auf `http://german.magento24.com/`.
1. Erweitern Sie **Basis-URLs (sicher** und aktualisieren Sie den **Sichere Basis-URL** und **Sichere Basis-Link-**) auf `https://german.magento24.com/`.
1. Klicken Sie **Konfiguration speichern** und speichern Sie die Konfigurationsänderungen.

### Cache leeren

Führen Sie den folgenden Befehl aus, um die `config`- und `full_page` zu bereinigen.

```bash
bin/magento cache:clean config full_page
```

## Überprüfen der Site

Sofern Sie kein DNS für die URLs Ihrer Stores eingerichtet haben, müssen Sie eine statische Route zum Host in Ihrer `hosts`-Datei hinzufügen:

1. Suchen Sie die `hosts` Ihres Betriebssystems.
1. Fügen Sie die statische Route im folgenden Format hinzu:

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
>- Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie bei Ihrem Hosting-Anbieter.
>- Zum Einrichten von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Siehe [Einrichten mehrerer Cloud-Websites oder -Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de) im Handbuch zu _Commerce in der Cloud-Infrastruktur_.

### Fehlerbehebung

- Wenn Ihre französischen und deutschen Websites 404 s zurückgeben, aber Ihr Administrator geladen wird, stellen Sie sicher, dass Sie [ abgeschlossen haben (Schritt 6: Hinzufügen des Store-Codes zur Basis-URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Wenn alle URLs den Wert 404 zurückgeben, stellen Sie sicher, dass Sie Ihren Webserver neu gestartet haben.
- Wenn der Administrator nicht ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie die virtuellen Hosts ordnungsgemäß einrichten.
