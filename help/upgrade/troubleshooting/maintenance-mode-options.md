---
title: Optionen für den Wartungsmodus für die Aktualisierung
description: 'Erstellen Sie eine benutzerdefinierte Seite für den Wartungsmodus, die Ihre Kunden auf Ihrer Adobe Commerce- oder Magento Open Source-Storefront sehen, während Sie ein Upgrade durchführen. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Optionen für den Wartungsmodus für die Aktualisierung

In diesem Thema wird erläutert, wie Sie eine benutzerdefinierte Wartungsseite erstellen können, die Benutzern angezeigt wird, während die Magento-App aktualisiert wird. Die Erstellung einer benutzerdefinierten Seite ist optional, wird jedoch empfohlen, da während eines Teils des Upgrades auf Ihre Site zugegriffen werden kann.

Erstellen einer benutzerspezifischen Seite, auf die Benutzer umgeleitet werden sollen, um den Zugriff auf die Site zu verhindern, und informiert Ihre Benutzer darüber, dass die Site gewartet wird.

>[!NOTE]
>
>Sie müssen die Aufgaben in diesem Abschnitt als Benutzer mit `root` Berechtigungen. Benutzerdefinierte Wartungsseiten können während des Entwicklermodus nicht festgelegt werden.

## Benutzerdefinierte Wartungsseite erstellen

Um eine Wartungsseite zu erstellen und zu dieser umzuleiten, erstellen Sie zunächst eine Wartungsseite mit dem Namen:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

Fügen Sie den folgenden Inhalt hinzu:

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Benutzerdefinierte Wartungsseite für Apache

In diesem Abschnitt wird beschrieben, wie Sie eine benutzerdefinierte Wartungsseite erstellen und den Traffic darauf umleiten.

Das Beispiel in diesem Abschnitt zeigt, wie Sie die folgenden Dateien ändern können, um Ihre Wartungsseite einzurichten:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

So leiten Sie Traffic zu einer benutzerdefinierten Wartungsseite um:

1. Aktualisieren Sie Ihre Apache-Konfiguration, um Folgendes zu tun:

   - Umleiten des gesamten Traffics auf die Wartungsseite
   - Zulassungslisten bestimmter IPs, sodass ein Administrator die Magento-Software aktualisieren kann.

   Im folgenden Beispiel wird 192.0.2.110 auf die Zulassungsliste gesetzt.

   Fügen Sie am Ende Ihrer Apache-Konfigurationsdatei Folgendes hinzu:

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Starten Sie Apache neu:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Geben Sie den folgenden Befehl ein:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [System aktualisieren](../implementation/perform-upgrade.md).
1. Testen Sie Ihre Website, um sicherzustellen, dass sie ordnungsgemäß funktioniert.
1. Löschen Sie nach Abschluss des Upgrades `maintenance.enable`.

## Benutzerdefinierte Wartungsseite für nginx

In diesem Abschnitt wird beschrieben, wie Sie eine benutzerdefinierte Wartungsseite erstellen und den Traffic darauf umleiten.

So leiten Sie Traffic zu einer benutzerdefinierten Wartungsseite um:

1. Verwenden Sie einen Texteditor, um [nginx](https://glossary.magento.com/nginx) Konfigurationsdatei, die Ihren Serverblock enthält.
1. Fügen Sie dem Serverblock Folgendes hinzu (`server` nur aus Gründen der Klarheit angezeigt wird; keinen zweiten Serverblock hinzufügen).

   Im Folgenden werden die IP-Adressen 192.0.2.110 und 192.0.2.115 auf einem System auf die Zulassungsliste gesetzt, auf dem Magento in installiert ist. `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Geben Sie den folgenden Befehl ein:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Laden Sie die nginx-Konfiguration neu:

   ```bash
   service nginx reload
   ```

1. [System aktualisieren](../implementation/perform-upgrade.md).
1. Testen Sie Ihre Website, um sicherzustellen, dass sie ordnungsgemäß funktioniert.
1. Nach Abschluss des Upgrades löschen oder umbenennen `maintenance.enable`
1. Laden Sie die nginx-Konfiguration neu:

   ```bash
   service nginx reload
   ```
