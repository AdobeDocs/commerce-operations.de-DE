---
title: PHP-Einstellungen
description: Führen Sie diese Schritte aus, um die erforderlichen PHP-Erweiterungen zu installieren und die erforderlichen PHP-Einstellungen für lokale Installationen von Adobe Commerce zu konfigurieren.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 766226dc998aafe54bc84d77cabee6fb0a969e6c
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 0%

---


# PHP-Einstellungen

In diesem Abschnitt wird beschrieben, wie Sie die erforderlichen PHP-Optionen festlegen.

>[!NOTE]
>
>Unterstützte PHP-Versionen variieren je nach Adobe Commerce-Version. Siehe [Systemanforderungen](../system-requirements.md) für die genauen PHP-Versionen, die von der Version unterstützt werden, die Sie installieren.

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) im _Handbuch zu Commerce_ Cloud-Infrastruktur.

## PHP-Prozesssteuerung

{{php-process-control}}

## Überprüfen, ob PHP installiert ist

PHP ist auf den meisten Linux-Distributionen standardmäßig installiert. Dieses Thema setzt voraus, dass Sie PHP bereits installiert haben. Um zu überprüfen, ob PHP installiert ist, geben Sie Folgendes in die Befehlszeile ein:

```bash
php -v
```

Wenn PHP installiert ist, wird eine Meldung ähnlich der folgenden angezeigt:

```
PHP <supported-version> (cli) (built: <build-date>) (NTS)
Copyright (c) The PHP Group
Zend Engine v<matching-version>, Copyright (c) Zend Technologies
    with Zend OPcache v<matching-version>, Copyright (c), by Zend Technologies
```

Wenn PHP nicht installiert ist (oder ein Upgrade benötigt), installieren Sie es, indem Sie die Anweisungen für Ihre Linux-Distribution befolgen.

## Überprüfen installierter Erweiterungen

Adobe Commerce erfordert bestimmte PHP-Erweiterungen. In den folgenden Listen sind die erforderlichen Erweiterungen für jede Edition von Commerce aufgeführt. Die Listen werden automatisch aus einer Bereitstellung generiert, auf der die neueste Version jeder Edition ausgeführt wird.

{{$include /help/_includes/templated/php-extensions.md}}

So überprüfen Sie installierte Erweiterungen:

1. Installierte Module auflisten.

   ```bash
   php -m
   ```

1. Stellen Sie sicher, dass alle erforderlichen Erweiterungen installiert sind.
1. Fügen Sie alle fehlenden Module mit demselben Workflow hinzu, der für die Installation von PHP verwendet wurde.

## PHP-Einstellungen überprüfen

>[!WARNING]
>
>Wenn Sie Probleme mit einer alten Umgebung beheben möchten, die von PHP [Bug 81101](https://bugs.php.net/bug.php?id=81101) betroffen ist, legen Sie `pcre.jit=0` in Ihrer `php.ini` fest, um das Problem zu umgehen, dass CSS nicht geladen wird.

- Legen Sie die Systemzeitzone für PHP fest; andernfalls funktionieren Fehler wie die folgende Anzeige während der Installation und zeitbezogene Vorgänge wie cron möglicherweise nicht:

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Setzen Sie das PHP-Speicherlimit.

  Adobe empfiehlt Folgendes:

   - Kompilieren von Code oder Bereitstellen statischer Assets, `1G`
   - Debugging, `2G`
   - Tests, `~3-4G`

- Erhöhen Sie die Werte für die PHP-`realpath_cache_size` und `realpath_cache_ttl` Sie auf empfohlene Einstellungen:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Diese Einstellungen ermöglichen es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie beim Laden der Seite zu suchen. Siehe [Leistungsoptimierung](https://www.php.net/manual/en/ini.core.php) in der PHP-Dokumentation.

- Aktivieren Sie [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments) , was für Adobe Commerce 2.1 und höher erforderlich ist.

  Aus Leistungsgründen empfiehlt Adobe, [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) zu aktivieren. Der OPcache ist in vielen PHP Distributionen aktiviert.

  Adobe Commerce 2.1 und höher verwenden PHP-Codekommentare für die Codegenerierung.

>[!NOTE]
>
>Um Probleme während der Installation und des Upgrades zu vermeiden, empfiehlt Adobe dringend, dieselben PHP-Einstellungen sowohl auf die PHP-Befehlszeilenkonfiguration als auch auf die PHP-Webserver-Plug-in-Konfiguration anzuwenden. Weitere Informationen finden Sie im nächsten Abschnitt.

## PHP-Konfigurationsdateien suchen

In diesem Abschnitt wird beschrieben, wie Sie die Konfigurationsdateien finden, die zum Aktualisieren der erforderlichen Einstellungen erforderlich sind.

### Suchen `php.ini` Konfigurationsdatei

Um die Webserver-Konfiguration zu finden, führen Sie eine [`phpinfo.php`-Datei &#x200B;](optional-software.md#create-phpinfophp) Ihrem Webbrowser aus und suchen Sie wie folgt nach der `Loaded Configuration File`:

![PHP-Informationsseite](../../assets/installation/config_phpini-webserver.png)

Um die PHP-Befehlszeilenkonfiguration zu finden, geben Sie ein

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Wenn Sie nur eine `php.ini` haben, ändern Sie diese Datei. Wenn Sie zwei `php.ini` haben, ändern Sie *beide* Dateien. Andernfalls kann es zu unvorhersehbarer Leistung kommen.

### OPcache-Konfigurationseinstellungen suchen

PHP OPcache-Einstellungen befinden sich normalerweise entweder in `php.ini` oder `opcache.ini`. Der Speicherort hängt möglicherweise von Ihrem Betriebssystem und der PHP-Version ab. Die OPcache-Konfigurationsdatei kann einen `opcache` Abschnitt oder Einstellungen wie `opcache.enable` aufweisen.

Verwenden Sie die folgenden Richtlinien, um sie zu finden:

- Apache-Webserver:

  Bei Ubuntu mit Apache befinden sich OPcache-Einstellungen normalerweise in der `php.ini`.

  Bei CentOS mit Apache oder Nginx befinden sich die OPcache-Einstellungen normalerweise in `/etc/php.d/opcache.ini`

  Wenn nicht, verwenden Sie den folgenden Befehl, um sie zu finden:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- nginx Webserver mit PHP-FPM: `/etc/php/<supported-php-version>/fpm/php.ini`

Wenn Sie mehr als ein `opcache.ini` haben, ändern Sie alle.

## Wie man PHP-Optionen einstellt

So legen Sie PHP-Optionen fest:

1. Öffnen Sie eine `php.ini` in einem Texteditor.
1. Suchen Sie die Zeitzone Ihres Servers in den verfügbaren [Zeitzoneneinstellungen](https://www.php.net/manual/en/timezones.php)
1. Suchen Sie die folgende Einstellung und heben Sie ggf. die Auskommentierung auf:

   ```conf
   date.timezone =
   ```

1. Fügen Sie die Zeitzoneneinstellung hinzu, die Sie in Schritt 2 gefunden haben.

1. Ändern Sie den Wert von `memory_limit` in einen der am Anfang dieses Abschnitts empfohlenen Werte.

   Beispiel:

   ```conf
   memory_limit=2G
   ```

1. Fügen Sie die `realpath_cache`-Konfiguration hinzu oder aktualisieren Sie sie, damit sie den folgenden Werten entspricht:

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

1. Öffnen Sie die andere `php.ini` (sofern sie unterschiedlich sind) und nehmen Sie die gleichen Änderungen vor.

## OPcache-Optionen festlegen

So legen Sie `opcache.ini` fest:

1. Öffnen Sie Ihre OP-Cache-Konfigurationsdatei in einem Texteditor:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/<supported-php-version>/fpm/php.ini` (nginx Webserver (CentOS oder Ubuntu))

1. Suchen Sie `opcache.save_comments` und heben Sie ggf. die Auskommentierung auf.
1. Stellen Sie sicher, dass der Wert auf `1` gesetzt ist.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu und CentOS: `service nginx restart`

## Fehlerbehebung

In den folgenden Adobe Commerce-Support-Artikeln finden Sie Hilfe bei der Fehlerbehebung bei PHP-Problemen:

- [PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce in einem Browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP-Einstellungsfehler](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/php-settings-errors)
- [PHP mcrypt-Erweiterung nicht ordnungsgemäß installiert](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/php-mcrypt-extension-not-installed-properly)
- [Probleme bei der Prüfung der PHP-Version](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues)
- [Häufige schwerwiegende PHP-Fehler und -Lösungen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions)

<!-- Last updated from includes: 2025-04-04 22:27:22 -->
