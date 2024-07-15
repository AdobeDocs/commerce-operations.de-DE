---
title: PHP-Einstellungen
description: Führen Sie diese Schritte aus, um erforderliche PHP-Erweiterungen zu installieren und die erforderlichen PHP-Einstellungen für lokale Installationen von Adobe Commerce zu konfigurieren.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# PHP-Einstellungen

In diesem Thema wird beschrieben, wie Sie die erforderlichen PHP-Optionen festlegen.

>[!NOTE]
>
>Die neueste Version von Adobe Commerce erfordert mindestens PHP 8.1. Unter [Systemanforderungen](../system-requirements.md) finden Sie alle unterstützten PHP-Versionen.

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) im Handbuch _Commerce on Cloud Infrastructure_ .

## PHP Process Control

{{php-process-control}}

## Überprüfen, ob PHP installiert ist

PHP wird standardmäßig auf den meisten Linux-Distributionen installiert. Dieses Thema setzt voraus, dass Sie PHP bereits installiert haben. Um zu überprüfen, ob PHP installiert ist, geben Sie Folgendes in die Befehlszeile ein:

```bash
php -v
```

Wenn PHP installiert ist, wird eine ähnliche Meldung wie die folgende angezeigt:

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Wenn PHP nicht installiert ist (oder ein Upgrade erforderlich ist), installieren Sie es, indem Sie die Anweisungen für Ihre Linux-Distribution befolgen.

## Überprüfen installierter Erweiterungen

Adobe Commerce erfordert bestimmte PHP-Erweiterungen. In den folgenden Listen werden die erforderlichen Erweiterungen für jede Version von Commerce aufgeführt. Die Listen werden von einer Bereitstellung automatisch generiert, bei der die neueste Version jeder Edition ausgeführt wird.

{{$include /help/_includes/templated/php-extensions.md}}

Überprüfen installierter Erweiterungen:

1. Liste installierter Module.

   ```bash
   php -m
   ```

1. Stellen Sie sicher, dass alle erforderlichen Erweiterungen installiert sind.
1. Fügen Sie alle fehlenden Module mit dem gleichen Workflow hinzu, der für die Installation von PHP verwendet wird.

## Überprüfen der PHP-Einstellungen

>[!WARNING]
>
>Wenn Sie PHP 7.4.20 verwenden, setzen Sie `pcre.jit=0` in Ihrer `php.ini` -Datei. Dadurch wird ein PHP [bug](https://bugs.php.net/bug.php?id=81101) umgangen, der verhindert, dass CSS geladen wird.

- Legen Sie die Systemzeitzone für PHP fest. Andernfalls funktionieren Fehler wie die folgende Anzeige während der Installation und zeitbezogene Vorgänge wie Cron möglicherweise nicht:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Setzen Sie das PHP-Speicherlimit.

  Adobe empfiehlt Folgendes:

   - Kompilieren von Code oder Bereitstellen von statischen Assets, `1G`
   - Debugging, `2G`
   - Test, `~3-4G`

- Erhöhen Sie die Werte für PHP `realpath_cache_size` und `realpath_cache_ttl` auf empfohlene Einstellungen:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Diese Einstellungen ermöglichen es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie beim Laden der Seite zu suchen. Siehe [Leistungsoptimierung](https://www.php.net/manual/en/ini.core.php) in der PHP-Dokumentation.

- Aktivieren Sie [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), was für Adobe Commerce 2.1 und höher erforderlich ist.

  Adobe empfiehlt aus Leistungsgründen die Aktivierung des [PHP OPcache](https://www.php.net/manual/en/book.opcache.php). Der OPcache ist in vielen PHP-Distributionen aktiviert.

  Adobe Commerce 2.1 und höher verwenden PHP-Code-Kommentare zur Codegenerierung.

>[!NOTE]
>
>Um Probleme während der Installation und Aktualisierung zu vermeiden, empfiehlt Adobe dringend, dass Sie die gleichen PHP-Einstellungen sowohl auf die PHP-Befehlszeilenkonfiguration als auch auf die PHP-Webserver-Plug-in-Konfiguration anwenden. Weitere Informationen finden Sie im nächsten Abschnitt.

## PHP-Konfigurationsdateien suchen

In diesem Abschnitt wird beschrieben, wie Sie die Konfigurationsdateien finden, die zum Aktualisieren der erforderlichen Einstellungen erforderlich sind.

### Suchen Sie die Konfigurationsdatei `php.ini` .

Um die Webserverkonfiguration zu finden, führen Sie eine [`phpinfo.php` -Datei](optional-software.md#create-phpinfophp) in Ihrem Webbrowser aus und suchen Sie nach dem `Loaded Configuration File` wie folgt:

![PHP-Infoseite](../../assets/installation/config_phpini-webserver.png)

Um die PHP-Befehlszeilenkonfiguration zu finden, geben Sie

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Wenn Sie nur eine `php.ini` -Datei haben, ändern Sie diese Datei. Wenn Sie zwei `php.ini` -Dateien haben, ändern Sie die *beide* -Dateien. Andernfalls kann die Leistung unvorhersehbar sein.

### OPcache-Konfigurationseinstellungen suchen

PHP OPcache-Einstellungen befinden sich normalerweise entweder in `php.ini` oder in `opcache.ini`. Der Speicherort kann von Ihrem Betriebssystem und Ihrer PHP-Version abhängen. Die OPcache-Konfigurationsdatei kann einen Abschnitt &quot;`opcache`&quot; oder Einstellungen wie &quot;`opcache.enable`&quot; enthalten.

Verwenden Sie die folgenden Richtlinien, um sie zu finden:

- Apache-Webserver:

  Bei Ubuntu mit Apache befinden sich die OPcache-Einstellungen normalerweise in der Datei `php.ini` .

  Bei CentOS mit Apache oder nginx befinden sich die OPcache-Einstellungen normalerweise in `/etc/php.d/opcache.ini`

  Wenn nicht, suchen Sie mit dem folgenden Befehl:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- nginx-Webserver mit PHP-FPM: `/etc/php/8.1/fpm/php.ini`

Wenn Sie mehr als einen `opcache.ini` haben, ändern Sie alle.

## Festlegen von PHP-Optionen

Festlegen von PHP-Optionen:

1. Öffnen Sie eine `php.ini` in einem Texteditor.
1. Suchen Sie die Zeitzone Ihres Servers in den verfügbaren [Zeitzoneneinstellungen](https://www.php.net/manual/en/timezones.php) .
1. Suchen Sie die folgende Einstellung und heben Sie die Auskommentierung auf, falls erforderlich:

   ```conf
   date.timezone =
   ```

1. Fügen Sie die Zeitzoneneinstellung hinzu, die Sie in Schritt 2 gefunden haben.

1. Ändern Sie den Wert von `memory_limit` in einen der am Anfang dieses Abschnitts empfohlenen Werte.

   Beispiel:

   ```conf
   memory_limit=2G
   ```

1. Fügen Sie die `realpath_cache` -Konfiguration hinzu oder aktualisieren Sie sie, sodass sie den folgenden Werten entspricht:

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

1. Öffnen Sie die anderen `php.ini` (sofern sie unterschiedlich sind) und nehmen Sie die gleichen Änderungen daran vor.

## OPcache-Optionen festlegen

So legen Sie `opcache.ini` -Optionen fest:

1. Öffnen Sie die OPcache-Konfigurationsdatei in einem Texteditor:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (nginx-Webserver (CentOS oder Ubuntu)

1. Suchen Sie `opcache.save_comments` und heben Sie die Auskommentierung auf, falls erforderlich.
1. Stellen Sie sicher, dass der Wert auf `1` eingestellt ist.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu und CentOS: `service nginx restart`

## Fehlerbehebung

In den folgenden Adobe Commerce-Supportartikeln finden Sie Hilfe zur Fehlerbehebung bei PHP-Problemen:

- [PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce in einem Browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Fehler bei PHP-Einstellungen](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP-Mcrypt-Erweiterung nicht ordnungsgemäß installiert](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Probleme bei der PHP-Versionsbereitschaftsprüfung](https://support.magento.com/hc/en-us/articles/360033546411)
- [Häufige PHP-Fatal-Fehler und -Lösungen](https://support.magento.com/hc/en-us/articles/360030568432)
