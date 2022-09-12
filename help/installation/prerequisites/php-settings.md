---
title: PHP-Einstellungen
description: Führen Sie diese Schritte aus, um erforderliche PHP-Erweiterungen zu installieren und die erforderlichen PHP-Einstellungen für lokale Installationen von Adobe Commerce und Magento Open Source zu konfigurieren.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# PHP-Einstellungen

In diesem Thema wird beschrieben, wie Sie die erforderlichen [PHP](https://glossary.magento.com/php) Optionen.

>[!NOTE]
>
>Siehe [Systemanforderungen](../system-requirements.md) für unterstützte PHP-Versionen.

## Überprüfen, ob PHP installiert ist

Die meisten Versionen von Linux haben PHP standardmäßig installiert. Dieses Thema setzt voraus, dass Sie PHP bereits installiert haben. Um zu überprüfen, ob PHP bereits installiert ist, geben Sie in der Befehlszeile Folgendes ein:

```bash
php -v
```

Wenn [PHP](https://glossary.magento.com/php) installiert ist, wird eine Meldung ähnlich der folgenden angezeigt:

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce und Magento Open Source 2.4 sind mit PHP 7.3 kompatibel, aber wir testen mit PHP 7.4 und empfehlen die Verwendung.

Wenn PHP nicht installiert ist oder ein Upgrade der Version erforderlich ist, installieren Sie es entsprechend den Anweisungen für Ihren jeweiligen Linux-Variante.
Unter CentOS: [zusätzliche Schritte erforderlich sein können](https://wiki.centos.org/HowTos/php7).

## Überprüfen installierter Erweiterungen

Für Adobe Commerce und Magento Open Source ist die Installation einer Reihe von Erweiterungen erforderlich.

{{$include /help/_includes/php-extensions.md}}

Überprüfen installierter Erweiterungen:

1. Liste der installierten Module.

   ```bash
   php -m
   ```

1. Stellen Sie sicher, dass alle erforderlichen Erweiterungen installiert sind.
1. Fügen Sie alle fehlenden Module mit dem gleichen Workflow hinzu, der für die Installation von PHP verwendet wird. Wenn Sie beispielsweise `yum` Um PHP zu installieren, können die PHP 7.4-Module wie folgt hinzugefügt werden:

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## Überprüfen der PHP-Einstellungen

>[!WARNING]
>
>Wenn Sie PHP 7.4.20 verwenden, setzen Sie `pcre.jit=0` in `php.ini` -Datei. Dies umgibt PHP [Fehler](https://bugs.php.net/bug.php?id=81101) verhindert, dass CSS geladen wird.

- Legen Sie die Systemzeitzone für PHP fest. Andernfalls funktionieren Fehler wie die folgende Anzeige während der Installation und zeitbezogene Vorgänge wie Cron möglicherweise nicht:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Setzen Sie das PHP-Speicherlimit.

   Unsere detaillierten Empfehlungen sind:

   - Kompilieren von Code oder Bereitstellen von statischen Assets, `1G`
   - Debugging, `2G`
   - Test, `~3-4G`

- Erhöhen Sie die Werte für PHP `realpath_cache_size` und `realpath_cache_ttl` zu den empfohlenen Einstellungen:

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   Diese Einstellungen ermöglichen es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie bei jedem Laden einer Seite zu suchen. Siehe [Leistungsoptimierung](https://www.php.net/manual/en/ini.core.php) in der PHP-Dokumentation.

- Aktivieren [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), was für Adobe Commerce und Magento Open Source 2.1 und höher erforderlich ist.

   Es wird empfohlen, die [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) aus Leistungsgründen. Der OPcache ist in vielen PHP-Distributionen aktiviert.

   Adobe Commerce und Magento Open Source 2.1 und höher verwenden PHP-Code-Kommentare zur Codegenerierung.

>[!NOTE]
>
>Um Probleme während der Installation und Aktualisierung zu vermeiden, empfehlen wir dringend, die gleichen PHP-Einstellungen sowohl auf die PHP-Befehlszeilenkonfiguration als auch auf die PHP-Webserver-Plug-in-Konfiguration anzuwenden. Weitere Informationen finden Sie im nächsten Abschnitt.

## PHP-Konfigurationsdateien suchen

In diesem Abschnitt wird beschrieben, wie Sie die Konfigurationsdateien finden, die zum Aktualisieren der erforderlichen Einstellungen erforderlich sind.

### Suchen `php.ini` Konfigurationsdatei

Führen Sie einen [`phpinfo.php` file](optional-software.md#create-phpinfophp) in Ihrem Webbrowser nach `Loaded Configuration File` wie folgt:

![PHP-Infoseite](../../assets/installation/config_phpini-webserver.png)

Um die PHP-Befehlszeilenkonfiguration zu finden, geben Sie

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Wenn Sie nur eine `php.ini` -Datei, nehmen Sie die Änderungen in dieser Datei vor. Wenn Sie zwei `php.ini` Dateien, nehmen Sie die Änderungen in *all* Dateien. Andernfalls kann die Leistung unvorhersehbar sein.

### OPcache-Konfigurationseinstellungen suchen

PHP OPcache-Einstellungen befinden sich normalerweise entweder in `php.ini` oder `opcache.ini`. Der Speicherort kann von Ihrem Betriebssystem und Ihrer PHP-Version abhängen. Die OPcache-Konfigurationsdatei verfügt möglicherweise über eine `opcache` Abschnitt oder Einstellungen, z. B. `opcache.enable`.

Verwenden Sie die folgenden Richtlinien, um sie zu finden:

- Apache-Webserver:

   Für Ubuntu mit Apache befinden sich die OPcache-Einstellungen normalerweise im `php.ini` -Datei.

   Bei CentOS mit Apache oder nginx befinden sich die OPcache-Einstellungen normalerweise in `/etc/php.d/opcache.ini`

   Wenn nicht, suchen Sie mit dem folgenden Befehl:

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- nginx-Webserver mit PHP-FPM: `/etc/php/7.2/fpm/php.ini`

Wenn Sie mehr als eine `opcache.ini`, ändern Sie alle.

## Festlegen von PHP-Optionen

So legen Sie PHP-Optionen fest:

1. Öffnen Sie eine `php.ini` in einem Texteditor.
1. Suchen Sie die Zeitzone Ihres Servers in der verfügbaren [Zeitzoneneinstellungen](https://www.php.net/manual/en/timezones.php)
1. Suchen Sie die folgende Einstellung und heben Sie die Auskommentierung bei Bedarf auf:

   ```conf
   date.timezone =
   ```

1. Fügen Sie die Zeitzoneneinstellung hinzu, die Sie in Schritt 2 gefunden haben.

1. Ändern Sie den Wert von `memory_limit` zu einem der am Anfang dieses Abschnitts empfohlenen Werte.

   Beispiel:

   ```conf
   memory_limit=2G
   ```

1. Hinzufügen oder Aktualisieren der `realpath_cache` Konfiguration, um die folgenden Werte zu erfüllen:

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.

1. Öffnen Sie die andere `php.ini` (wenn sie unterschiedlich sind) und die gleichen Änderungen daran vornehmen.

## OPcache-Optionen festlegen

Zum Festlegen `opcache.ini` options:

1. Öffnen Sie die OPcache-Konfigurationsdatei in einem Texteditor:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/7.2/fpm/php.ini` (nginx-Webserver (CentOS oder Ubuntu))

1. Suchen `opcache.save_comments` und entfernen Sie gegebenenfalls die Kommentar.
1. Stellen Sie sicher, dass der Wert auf `1`.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu und CentOS: `service nginx restart`

## Fehlerbehebung

In den folgenden Adobe Commerce-Supportartikeln finden Sie Hilfe zur Fehlerbehebung bei PHP-Problemen:

- [PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce im Browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Fehler bei PHP-Einstellungen](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP mcrypt-Erweiterung nicht ordnungsgemäß installiert](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Probleme bei der Überprüfung der PHP-Versionsbereitschaft](https://support.magento.com/hc/en-us/articles/360033546411)
- [Häufige Fehler und Lösungen bei PHP](https://support.magento.com/hc/en-us/articles/360030568432)
