---
title: Apache
description: Führen Sie diese Schritte aus, um den Apache-Webserver für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce unterstützt Apache 2.4.x.

## Erforderliche Anweisungen für Apache

1. Legen Sie `AllowEncodedSlashes` in der Server-Konfiguration (global) oder in den virtuellen Host-Konfigurationen fest, um zu vermeiden, dass die kodierten Schrägstriche dekodiert werden, die zu Problemen bei URLs führen können. Wenn Sie beispielsweise Produkte mit einem Schrägstrich in der SKU über die API abrufen, möchten Sie dies nicht konvertiert haben. Der Musterblock ist nicht vollständig und andere Anweisungen sind erforderlich.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache-Neuschreibungen und HTTAccess

In diesem Thema wird beschrieben, wie Sie Apache 2.4-Neuschreibungen aktivieren und eine Einstellung für die `.htaccess`[&#128279;](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample) &quot; Konfigurationsdatei“ angeben.

Adobe Commerce verwendet Server-Neuschreibungen und -`.htaccess`, um Anweisungen auf Ordnerebene für Apache bereitzustellen. Die folgenden Anweisungen sind auch in allen anderen Abschnitten dieses Themas enthalten.

Verwenden Sie diesen Abschnitt, um Apache 2.4-Neuschreibungen zu aktivieren und eine Einstellung für die [verteilte Konfigurationsdatei `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce verwendet Server-Neuschreibungen und -`.htaccess`, um Anweisungen auf Ordnerebene für Apache bereitzustellen.

>[!NOTE]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden in der Regel keine Stile in Ihrer Storefront oder in Ihrem Administrator angezeigt.

1. Aktivieren Sie das Apache Rewrite-Modul:

   ```bash
   a2enmod rewrite
   ```

1. Informationen dazu, wie Sie der Anwendung die Verwendung der Konfigurationsdatei für verteilte `.htaccess` ermöglichen, finden Sie in den Richtlinien in der [Apache 2.4-Dokumentation](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >In Apache 2.4 ist die standardmäßige Site-Konfigurationsdatei des Servers `/etc/apache2/sites-available/000-default.conf`.

   Sie können beispielsweise Folgendes am Ende von `000-default.conf` hinzufügen:

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Manchmal sind zusätzliche Parameter erforderlich. Weitere Informationen finden Sie in der [Apache 2.4-Dokumentation](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Wenn Sie die Apache-Einstellungen geändert haben, starten Sie Apache neu:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Wenn Sie von einer früheren Apache-Version aktualisiert haben, suchen Sie zunächst in `000-default.conf` nach `<Directory "/var/www/html">` oder `<Directory "/var/www">`.
   >- Sie müssen den Wert von `AllowOverride` in der Anweisung für den Ordner ändern, in dem Sie die Adobe Commerce-Software installieren möchten. Um beispielsweise die Installation im Stammverzeichnis des Webservers vorzunehmen, bearbeiten Sie die -Direktive in `<Directory /var/www>`.

>[!NOTE]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden Stile normalerweise nicht in der Storefront oder in der Admin-Benutzeroberfläche angezeigt.

## Für Apache erforderliche Module

Adobe Commerce erfordert die Installation der folgenden Apache-Module:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Überprüfen der Apache-Version

Um die Apache-Version zu überprüfen, die Sie derzeit ausführen, geben Sie Folgendes ein:

```bash
apache2 -v
```

Das Ergebnis sieht in etwa wie folgt aus:

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Wenn Apache *nicht installiert ist* lesen Sie:
   - [Installieren oder Aktualisieren von Apache auf Ubuntu](#installing-apache-on-ubuntu)
   - [Installieren von Apache unter CentOS](#installing-apache-on-centos)

## Installieren oder Aktualisieren von Apache auf Ubuntu

In den folgenden Abschnitten wird beschrieben, wie Sie Apache installieren oder aktualisieren:

- Installieren von Apache
- Aktualisieren Sie auf Apache 2.4 auf Ubuntu, um PHP 7.4 zu verwenden.

### Installieren von Apache auf Ubuntu

So installieren Sie die Standardversion von Apache:

1. Installieren von Apache

   ```bash
   apt-get -y install apache2
   ```

1. Überprüfen Sie die Installation.

   ```bash
   apache2 -v
   ```

   Das Ergebnis sieht in etwa wie folgt aus:

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Aktivieren Sie [Umschreibungen und `.htaccess`](#apache-rewrites-and-htaccess).

### Aktualisieren von Apache auf Ubuntu

So aktualisieren Sie auf Apache 2.4:

1. Fügen Sie das `ppa:ondrej`-Repository hinzu, das Apache 2.4 enthält:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Installieren Sie Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Wenn der Befehl „apt-get install“ aufgrund von nicht erfüllten Abhängigkeiten fehlschlägt, konsultieren Sie eine Ressource wie [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Überprüfen Sie die Installation.

   ```bash
   apache2 -v
   ```

   Meldungen ähnlich den folgenden sollten angezeigt werden:

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Aktivieren Sie [Umschreibungen und `.htaccess`](#apache-rewrites-and-htaccess).

## Installieren von Apache unter CentOS

Adobe Commerce erfordert Neuschreibungen des Apache-Servers. Sie müssen auch den Typ der Anweisungen angeben, die in `.htaccess` verwendet werden können. Die Anwendung verwendet diese Anweisungen, um Neuschreibungsregeln anzugeben.

Die Installation und Konfiguration von Apache ist im Grunde ein dreistufiger Prozess: die Software installieren, Rewrites aktivieren und `.htaccess` Anweisungen spezifizieren.

### Installieren von Apache

1. Installieren Sie Apache 2.4, falls noch nicht geschehen.

   ```bash
   yum -y install httpd
   ```

1. Überprüfen Sie die Installation:

   ```bash
   httpd -v
   ```

   Es werden Meldungen ähnlich der folgenden angezeigt, die bestätigen, dass die Installation erfolgreich war:

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

   >[!NOTE]
   >
   >Auch wenn Apache 2.4 standardmäßig mit CentOS bereitgestellt wird, lesen Sie den folgenden Abschnitt, um es zu konfigurieren.

### Rewrites und .htaccess für CentOS aktivieren

1. Öffnen Sie `/etc/httpd/conf/httpd.conf` Datei zur Bearbeitung:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Suchen Sie den Block, der mit beginnt:

   ```conf
   <Directory "/var/www/html">
   ```

1. Ändern Sie den Wert von `AllowOverride` auf `All`.

   Beispiel:

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >Die vorherigen Werte für `Order` funktionieren möglicherweise nicht in allen Fällen. Weitere Informationen finden Sie in der Apache-Dokumentation [2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Speichern Sie die Datei und beenden Sie den Texteditor.

1. Um Apache-Einstellungen anzuwenden, starten Sie Apache neu.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden in der Regel keine Stile in Ihrer Storefront oder in Ihrem Administrator angezeigt.

### Rewrites und .htaccess für Ubuntu aktivieren

1. Öffnen Sie `/etc/apache2/sites-available/default` Datei zur Bearbeitung:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Suchen Sie den Block, der mit beginnt:

   `<Directory "/var/www/html">`

1. Ändern Sie den Wert von `AllowOverride` auf `All`.

   Beispiel:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Speichern Sie die Datei und beenden Sie den Texteditor.

1. Konfigurieren Sie Apache für die Verwendung des `mod_rewrite` Moduls:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Starten Sie Apache neu, um Änderungen anzuwenden:

   ```bash
   service apache2 restart
   ```

## Beheben von 403-Fehlern (verboten)

Wenn beim Versuch, auf die Website zuzugreifen, 403 Fehler des Typs „Verboten“ auftreten, können Sie Ihre Apache-Konfiguration oder die Konfiguration Ihres virtuellen Hosts aktualisieren, um Besuchern die Website zu ermöglichen:

### Beheben von 403-Fehlern (Verboten) für Apache 2.4

Damit Website-Besuchende auf Ihre Website zugreifen können, verwenden Sie eine der [Require-Anweisungen](https://httpd.apache.org/docs/2.4/howto/access.html).

Beispiel:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>Die vorherigen Werte für `Order` funktionieren möglicherweise nicht in allen Fällen. Weitere Informationen finden Sie in der [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
