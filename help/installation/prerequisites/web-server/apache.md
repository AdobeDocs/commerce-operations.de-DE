---
title: Apache
description: Führen Sie diese Schritte aus, um den Apache-Webserver für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce unterstützt Apache 2.4.x.

## Apache erforderte Anweisungen

1. Legen Sie `AllowEncodedSlashes` in der Serverkonfiguration (global) oder in den Konfigurationen des virtuellen Hosts fest, um zu vermeiden, dass die kodierten Schrägstriche dekodiert werden, die Probleme für URLs verursachen können. Wenn Sie beispielsweise Produkte mit einem Schrägstrich in der SKU über die API abrufen, soll dieser nicht konvertiert werden. Der Beispielblock ist nicht vollständig und andere Anweisungen sind erforderlich.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache-Neuschreibungen und HTML-Zugriff

In diesem Thema wird beschrieben, wie Sie Apache 2.4-Neuschreibungen aktivieren und eine Einstellung für die verteilte Konfigurationsdatei [1}](https://httpd.apache.org/docs/current/howto/htaccess.html) festlegen.`.htaccess`

Adobe Commerce verwendet Server-Neuschreibungen und `.htaccess`, um Anweisungen auf Ordnerebene für Apache bereitzustellen. Die folgenden Anweisungen sind auch in allen anderen Abschnitten dieses Themas enthalten.

Verwenden Sie diesen Abschnitt, um Apache 2.4-Neuschreibungen zu aktivieren und eine Einstellung für die verteilte Konfigurationsdatei [1}](https://httpd.apache.org/docs/current/howto/htaccess.html) festzulegen.`.htaccess`

Adobe Commerce verwendet Server-Neuschreibungen und `.htaccess`, um Anweisungen auf Ordnerebene für Apache bereitzustellen.

>[!NOTE]
>
>Wenn Sie diese Einstellungen nicht aktivieren, werden in der Regel keine Stile auf der Storefront oder im Admin angezeigt.

1. Aktivieren Sie das Apache-Rewrite-Modul:

   ```bash
   a2enmod rewrite
   ```

1. Informationen dazu, wie Sie die Anwendung in die verteilte Konfigurationsdatei `.htaccess` einbinden können, finden Sie in den Richtlinien in der Dokumentation zu [Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) .

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
   >Manchmal sind zusätzliche Parameter erforderlich. Weitere Informationen finden Sie in der Dokumentation zu [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order) .

1. Wenn Sie die Apache-Einstellungen geändert haben, starten Sie Apache neu:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Wenn Sie von einer früheren Apache-Version aktualisiert haben, suchen Sie zunächst in `000-default.conf` nach `<Directory "/var/www/html">` oder `<Directory "/var/www">`.
   >- Sie müssen den Wert von `AllowOverride` in der Anweisung für den Ordner ändern, in den Sie die Adobe Commerce-Software installieren. Um beispielsweise im Basisverzeichnis des Webservers zu installieren, bearbeiten Sie die Anweisung in `<Directory /var/www>`.

>[!NOTE]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden Stile normalerweise nicht auf der Storefront oder im Admin angezeigt.

## Apache-erforderliche Module

Für Adobe Commerce müssen die folgenden Apache-Module installiert sein:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Überprüfen der Apache-Version

Geben Sie Folgendes ein, um die derzeit ausgeführte Apache-Version zu überprüfen:

```bash
apache2 -v
```

Das Ergebnis sieht in etwa wie folgt aus:

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Wenn Apache *nicht* installiert ist, lesen Sie:
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

1. Aktivieren Sie [rewrites und `.htaccess`](#apache-rewrites-and-htaccess).

### Aktualisieren von Apache auf Ubuntu

So aktualisieren Sie auf Apache 2.4:

1. Fügen Sie das Repository `ppa:ondrej` hinzu, das über Apache 2.4 verfügt:

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
   >Wenn der Befehl &quot;apt-get install&quot;aufgrund von nicht erfüllten Abhängigkeiten fehlschlägt, konsultieren Sie eine Ressource wie [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Überprüfen Sie die Installation.

   ```bash
   apache2 -v
   ```

   Meldungen, die dem Folgenden ähneln, sollten angezeigt werden:

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Aktivieren Sie [rewrites und `.htaccess`](#apache-rewrites-and-htaccess).

## Installieren von Apache unter CentOS

Für Adobe Commerce sind Neuschreibungen des Apache-Servers erforderlich. Sie müssen auch den Typ der Direktiven angeben, die in `.htaccess` verwendet werden können, mit dem die Anwendung Neuschreibungsregeln spezifiziert.

Die Installation und Konfiguration von Apache erfolgt in drei Schritten: Installieren Sie die Software, aktivieren Sie Neuschreibungen und geben Sie `.htaccess` -Anweisungen an.

### Installieren von Apache

1. Installieren Sie Apache 2.4 , falls noch nicht geschehen.

   ```bash
   yum -y install httpd
   ```

1. Überprüfen Sie die Installation:

   ```bash
   httpd -v
   ```

   In Meldungen, die der folgenden ähneln, wird angezeigt, um zu bestätigen, dass die Installation erfolgreich war:

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

   >[!NOTE]
   >
   >Selbst wenn Apache 2.4 standardmäßig mit CentOS bereitgestellt wird, finden Sie Informationen zur Konfiguration im folgenden Abschnitt.

### Aktivieren von Neuschreibungen und .htaccess für CentOS

1. Öffnen Sie die Datei `/etc/httpd/conf/httpd.conf` zur Bearbeitung:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Suchen Sie den Block, der mit folgenden Begriffen beginnt:

   ```conf
   <Directory "/var/www/html">
   ```

1. Ändern Sie den Wert von `AllowOverride` in `All`.

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
   >Die vorherigen Werte für `Order` funktionieren möglicherweise nicht in allen Fällen. Weitere Informationen finden Sie in der Apache-Dokumentation ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Speichern Sie die Datei und beenden Sie den Texteditor.

1. Um Apache-Einstellungen anzuwenden, starten Sie Apache neu.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Wenn Sie diese Einstellungen nicht aktivieren, werden in der Regel keine Stile auf der Storefront oder im Admin angezeigt.

### Aktivieren von Neuschreibungen und .htaccess für Ubuntu

1. Öffnen Sie die Datei `/etc/apache2/sites-available/default` zur Bearbeitung:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Suchen Sie den Block, der mit folgenden Begriffen beginnt:

   `<Directory "/var/www/html">`

1. Ändern Sie den Wert von `AllowOverride` in `All`.

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

1. Konfigurieren Sie Apache für die Verwendung des `mod_rewrite`-Moduls:

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

## Beheben von 403-Fehlern (Verboten)

Wenn Sie beim Zugriff auf die Site auf 403 Verbotene Fehler stoßen, können Sie Ihre Apache-Konfiguration oder Ihre Konfiguration des virtuellen Hosts aktualisieren, um Besuchern die Website zu ermöglichen:

### Beheben von 403 Verbotenen Fehlern für Apache 2.4

Um Website-Besuchern den Zugriff auf Ihre Site zu ermöglichen, verwenden Sie eine der [Require instructions](https://httpd.apache.org/docs/2.4/howto/access.html) .

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
