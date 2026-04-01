---
title: Installieren von Apache für On-Premise-Bereitstellungen
description: Erfahren Sie, wie Sie Apache für lokale Adobe Commerce-Bereitstellungen installieren und konfigurieren. Aktivieren Sie erforderliche Module, Neuschreibungen und ".htaccess“-Einstellungen.
feature: Install, Configuration
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Installieren von Apache für lokale Bereitstellungen {#apache}

Dieses Handbuch führt Sie durch die Installation von lokalen Apache für Adobe Commerce-Bereitstellungen und die Konfiguration der Apache-Einstellungen, die für Commerce erforderlich sind. Es enthält gemeinsame Apache-Anforderungen und betriebssystemspezifische Verfahren für Ubuntu und CentOS. Adobe empfiehlt, die Konfigurationsanweisungen in diesem Handbuch zu befolgen, um sowohl die Funktionalität als auch die Sicherheit des Commerce-Programms zu wahren.

Adobe unterstützt die Apache-Versionen, die in den [Systemanforderungen](../../system-requirements.md) für Ihre Adobe Commerce-Version aufgeführt sind. Unterstützte Versionen variieren je nach Version. Apache benötigt außerdem eine unterstützte PHP-Konfiguration. Weitere Informationen zu PHP-Anforderungen finden Sie unter [PHP-Einstellungen](../php-settings.md).

Beginnen Sie mit dem Abschnitt, der Ihrer Umgebung entspricht:

- Wenn Apache bereits installiert ist, beginnen Sie mit [Apache-Anforderungen ](#review-apache-requirements).
- Wenn Sie Apache auf Ubuntu installieren oder aktualisieren müssen, gehen Sie zu [Apache auf Ubuntu installieren oder aktualisieren](#installing-or-upgrading-apache-on-ubuntu).
- Wenn Sie Apache unter CentOS installieren müssen, navigieren Sie zu [Apache unter CentOS installieren](#installing-apache-on-centos).

## Apache-Anforderungen überprüfen

Sie müssen diese Anforderungen auf jedem Apache-Server erfüllen, der Adobe Commerce hostet.

### Erforderliche Anweisungen konfigurieren

Legen Sie `AllowEncodedSlashes` in der Server-Konfiguration (global) oder in den virtuellen Host-Konfigurationen fest, um zu vermeiden, dass die kodierten Schrägstriche dekodiert werden, die zu Problemen bei URLs führen können. Wenn Sie beispielsweise Produkte mit einem Schrägstrich in der SKU über die API abrufen, möchten Sie den Schrägstrich nicht konvertieren. Der folgende Beispielblock ist nicht vollständig und andere Anweisungen sind erforderlich.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Konfigurieren von Neuschreibungen und .htaccess {#apache-rewrites-and-htaccess}

Verwenden Sie diesen Abschnitt, um Apache-Neuschreibungen zu aktivieren und die [verteilte `.htaccess`-Datei](https://httpd.apache.org/docs/current/howto/htaccess.html) zu konfigurieren. Adobe Commerce verwendet Server-Neuschreibungen und -`.htaccess`, um Anweisungen auf Ordnerebene für Apache bereitzustellen.

>[!IMPORTANT]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden in der Regel keine Stile in Ihrer Storefront oder in Ihrem Administrator angezeigt. Außerdem kann es verhindern, dass Apache die in `.htaccess` definierten Adobe Commerce-Sicherheitsmaßnahmen anwendet.

1. Aktivieren Sie das Apache Rewrite-Modul:

   ```bash
   a2enmod rewrite
   ```

1. Aktivieren Sie die Anwendung, um die Konfigurationsdatei für verteilte `.htaccess` zu verwenden.

   1. Auf Ubuntu `/etc/apache2/sites-available/000-default.conf` bearbeiten. Informationen zu anderen Apache-Layouts oder zu erforderlichen zusätzlichen Parametern finden Sie unter [Apache-Dokumentation](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) und [Apache-Zugriffssteuerungsdokumentation](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Fügen Sie die `AllowOverride`-Anweisung für den Ordner hinzu, in dem Sie Adobe Commerce installieren möchten, oder aktualisieren Sie sie.

   Wenn Sie beispielsweise Adobe Commerce im `docroot` installieren, fügen Sie den folgenden Block zu `000-default.conf` hinzu:

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Wenn Sie ein Upgrade von einer früheren Apache-Version durchgeführt haben, suchen Sie zunächst in `<Directory "/var/www/html">` nach einem vorhandenen `<Directory "/var/www">`- oder `000-default.conf`. Wenn Sie Adobe Commerce in einer anderen `docroot` installieren, aktualisieren Sie den entsprechenden `<Directory>` für diesen Pfad.

1. Starten Sie Apache neu, um Ihre Änderungen anzuwenden:

   ```bash
   service apache2 restart
   ```

### Installieren erforderlicher Module

Adobe Commerce erfordert die Installation der folgenden Apache-Module:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Überprüfen, ob Apache installiert ist

Um sicherzustellen, dass Apache installiert ist, und die aktuelle Version anzuzeigen, geben Sie Folgendes ein:

```bash
apache2 -v
```

Das Ergebnis zeigt Informationen ähnlich den folgenden an:

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Wenn Apache *nicht installiert ist* lesen Sie:
   - [Installieren oder Aktualisieren von Apache auf Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Installieren von Apache unter CentOS](#installing-apache-on-centos)

## Installieren oder Aktualisieren von Apache auf Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

Die Installation und Konfiguration von Apache auf Ubuntu erfolgt in drei Schritten:

1. Installieren Sie die Software.
1. Umschreibungen aktivieren.
1. Geben Sie `.htaccess` an.

Wenn Sie Apache-Server-Neuschreibungen konfigurieren, müssen Sie den Typ der Anweisungen angeben, die in `.htaccess` verwendet werden können. Das Programm verwendet diese Anweisungen, um Neuschreibungsregeln und Sicherheitsschutz anzugeben.

### Installieren von Apache auf Ubuntu

1. Installieren Sie Apache, falls noch nicht geschehen:

   ```bash
   apt-get -y install apache2
   ```

1. Überprüfen Sie die Installation:

   ```bash
   apache2 -v
   ```

   Es werden Meldungen ähnlich der folgenden angezeigt, die bestätigen, dass die Installation erfolgreich war:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

   >[!NOTE]
   >
   >Auch wenn Apache standardmäßig mit Ubuntu bereitgestellt wird, lesen Sie den folgenden Abschnitt, um es zu konfigurieren.

### Aktualisieren von Apache auf Ubuntu

Wenn Apache bereits installiert ist und Sie eine Version verwenden, die älter als `2.4` ist, führen Sie ein Upgrade auf Apache `2.4` oder auf die neueste Version durch, die von der bereitgestellten Adobe Commerce-Version unterstützt wird. Siehe [Systemanforderungen](../../system-requirements.md).

1. Paketinformationen aktualisieren:

   ```bash
   apt-get -y update
   ```

1. Fügen Sie bei Bedarf ein Repository hinzu, das eine unterstützte Apache-Version für Ihre Umgebung bereitstellt.

1. Installieren oder aktualisieren Sie Apache:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Wenn der `apt-get install`-Befehl aufgrund von nicht erfüllten Abhängigkeiten fehlschlägt, konsultieren Sie die Dokumentation zum Betriebssystempaket oder die Ressourcen zur Verteilungsunterstützung.

1. Überprüfen Sie die Installation:

   ```bash
   apache2 -v
   ```

1. Vergewissern Sie sich, dass die installierte Version mit der Version übereinstimmt, die für Ihre Adobe Commerce-Version in [Systemanforderungen) unterstützt ](../../system-requirements.md).

1. Aktivieren [Umschreibungen und `.htaccess` für Ubuntu](#enable-rewrites-and-htaccess-for-ubuntu).

### Rewrites und .htaccess für Ubuntu aktivieren

1. Öffnen Sie die `/etc/apache2/sites-available/000-default.conf` zur Bearbeitung:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Suchen Sie den Block, der mit beginnt:

   ```conf
   <Directory "/var/www/html">
   ```

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

>[!IMPORTANT]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden in der Regel keine Stile in Ihrer Storefront oder in Ihrem Administrator angezeigt. Außerdem kann es verhindern, dass Apache die in `.htaccess` definierten Adobe Commerce-Sicherheitsmaßnahmen anwendet.

## Installieren von Apache unter CentOS {#installing-apache-on-centos}

Die Installation und Konfiguration von Apache unter CentOS erfolgt in drei Schritten:

1. Installieren der Software
2. Umschreibungen aktivieren
3. Geben Sie `.htaccess` an.

Wenn Sie Apache-Server-Neuschreibungen konfigurieren, müssen Sie den Typ der Anweisungen angeben, die in `.htaccess` verwendet werden können. Das Programm verwendet diese Anweisungen, um Neuschreibungsregeln und Sicherheitsschutz anzugeben.

### Installieren von Apache

1. Installieren Sie Apache, falls noch nicht geschehen.

   ```bash
   yum -y install httpd
   ```

1. Überprüfen Sie die Installation:

   ```bash
   httpd -v
   ```

   Es werden Meldungen ähnlich der folgenden angezeigt, die bestätigen, dass die Installation erfolgreich war:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

   >[!NOTE]
   >
   >Auch wenn Apache standardmäßig unter CentOS bereitgestellt wird, lesen Sie den folgenden Abschnitt, um dies zu konfigurieren.

### Rewrites und .htaccess für CentOS aktivieren

1. Öffnen Sie die `/etc/httpd/conf/httpd.conf` zur Bearbeitung:

   ```bash
   vim /etc/httpd/conf/httpd.conf
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
   >Die vorherigen Werte für `Order` funktionieren möglicherweise nicht in allen Fällen. Weitere Informationen finden Sie in der [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Speichern Sie die Datei und beenden Sie den Texteditor.

1. Um die Apache-Einstellungen anzuwenden, starten Sie Apache neu.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>Wenn diese Einstellungen nicht aktiviert werden, werden in der Regel keine Stile in Ihrer Storefront oder in Ihrem Administrator angezeigt. Außerdem kann es verhindern, dass Apache die in `.htaccess` definierten Adobe Commerce-Sicherheitsmaßnahmen anwendet.

## Beheben von 403-Fehlern (verboten)

Wenn beim Versuch, auf die Website zuzugreifen, 403 Fehler des Typs „Verboten“ auftreten, können Sie Ihre Apache-Konfiguration oder die Konfiguration Ihres virtuellen Hosts aktualisieren, um Besuchern die Website zu ermöglichen:

### Beheben von 403-Fehlern bei Apache

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
