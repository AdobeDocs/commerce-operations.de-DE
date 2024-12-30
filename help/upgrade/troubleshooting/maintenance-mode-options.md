---
title: Wartungsmodusoptionen für das Upgrade
description: Erstellen Sie eine benutzerdefinierte Wartungsmodusseite, die Ihre Kunden in Ihrer Adobe Commerce-Storefront sehen, während Sie ein Upgrade ausführen.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Wartungsmodusoptionen für das Upgrade

In diesem Abschnitt wird beschrieben, wie Sie eine benutzerdefinierte Wartungsseite erstellen, die Benutzern angezeigt wird, während Ihre Magento-Anwendung aktualisiert wird. Das Erstellen einer benutzerdefinierten Seite ist optional, wird jedoch empfohlen, da die Website während eines Teils des Upgrades zugänglich ist.

Das Erstellen einer benutzerdefinierten Seite, zu der Benutzer umgeleitet werden, verhindert jeden Zugriff auf die Website und informiert Ihre Benutzer auch darüber, dass die Website gewartet wird.

>[!NOTE]
>
>Sie müssen die Aufgaben in diesem Abschnitt als Benutzer mit `root` ausführen. Benutzerdefinierte Wartungsseiten können im Entwicklermodus nicht festgelegt werden.

## Erstellen der benutzerdefinierten Wartungsseite

Um eine Wartungsseite zu erstellen und zu ihr umzuleiten, erstellen Sie zunächst eine Wartungsseite mit dem Namen:

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

In diesem Abschnitt wird beschrieben, wie Sie eine benutzerdefinierte Wartungsseite erstellen und Traffic zu ihr umleiten.

Das Beispiel in diesem Abschnitt zeigt, wie die folgenden Dateien geändert werden können. Dies ist eine Möglichkeit, Ihre Wartungsseite einzurichten:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

So leiten Sie Traffic auf eine benutzerdefinierte Wartungsseite um:

1. Aktualisieren Sie Ihre Apache-Konfiguration, um Folgendes zu tun:

   - Gesamten Traffic zur Wartungsseite umleiten
   - Zulassungsliste bestimmter IPs, damit ein Administrator die Magento-Software aktualisieren kann.

   Auf die Zulassungsliste setzen Im folgenden Beispiel wird 192.0.2.110.

   Fügen Sie am Ende Ihrer Apache-Konfigurationsdatei Folgendes hinzu:

   ```
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Apache neu starten:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Geben Sie den folgenden Befehl ein:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [System aktualisieren](../implementation/perform-upgrade.md).
1. Testen Sie die Site, um sicherzustellen, dass sie korrekt funktioniert.
1. Löschen Sie `maintenance.enable` nach Abschluss des Upgrades.

## Benutzerdefinierte Wartungsseite für nginx

In diesem Abschnitt wird beschrieben, wie Sie eine benutzerdefinierte Wartungsseite erstellen und Traffic zu ihr umleiten.

So leiten Sie Traffic auf eine benutzerdefinierte Wartungsseite um:

1. Verwenden Sie einen Texteditor, um die nginx-Konfigurationsdatei zu öffnen, die Ihren Serverblock enthält.
1. Fügen Sie dem Serverblock Folgendes hinzu (`server` wird nur der Übersichtlichkeit halber angezeigt; fügen Sie keinen zweiten Serverblock hinzu).

   Auf die Zulassungsliste setzen Mit der folgenden IP-Adresse 192.0.2.110 und 192.0.2.115 Sie auf einem System, auf dem Magento in `/var/www/html/magento2` installiert ist:

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
1. Testen Sie die Site, um sicherzustellen, dass sie korrekt funktioniert.
1. Löschen oder benennen Sie `maintenance.enable` nach Abschluss des Upgrades um
1. Laden Sie die nginx-Konfiguration neu:

   ```bash
   service nginx reload
   ```
