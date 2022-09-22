---
title: Systemanforderungen
description: Verwenden Sie diese Referenz, um erforderliche Softwareabhängigkeiten zu identifizieren, die mit Adobe Commerce- und Magento Open Source-Versionen getestet wurden.
source-git-commit: 3ba17b62f595e5a02ca56753d81d67166ddbc413
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Systemanforderungen

Diese Tabelle zeigt Versionen von Softwareabhängigkeiten von Drittanbietern, die Adobe mit bestimmten Adobe Commerce- und Magento Open Source-Versionen getestet hat. Adobe unterstützt nur die Kombination von Systemanforderungen, die in der folgenden Tabelle beschrieben wird.

Beispielsweise ist 2.4.3 vollständig mit MariaDB 10.4 getestet. Adobe empfiehlt ein Upgrade auf MariaDB 10.4, bevor Sie auf 2.4.3 aktualisieren.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Sonstiges

In diesem Abschnitt wird die Unterstützung und Kompatibilität für alle anderen Arten von erforderlicher und optionaler Software beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce und Magento Open Source.

### Mail-Server

Mail Transfer Agent (MTA) oder SMTP-Server

### Betriebssysteme (Linux x86-64)

Linux-Distributionen wie RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian und Ähnliches. Microsoft Windows und macOS werden nicht unterstützt.

### PHP-Erweiterungen

>[!NOTE]
>
>Die [Installationsanweisungen für PHP](prerequisites/php-settings.md) einen Schritt zur Installation dieser Erweiterungen enthalten.

{{$include /help/_includes/php-extensions.md}}

Siehe [offizielle PHP-Dokumentation](https://php.net/manual/en/extensions.php) für Installationsdetails.

### PHP OPcache

Wir empfehlen dringend, zu überprüfen, ob [PHP OPcache](https://php.net/manual/en/intro.opcache.php) aus Leistungsgründen aktiviert ist. Der OPcache ist in vielen PHP-Distributionen aktiviert. Um zu überprüfen, ob es installiert ist, lesen Sie unsere [PHP-Dokumentation](prerequisites/php-settings.md).

Wenn Sie es separat installieren müssen, lesen Sie den Abschnitt [PHP OPcache-Dokumentation](https://php.net/manual/en/opcache.setup.php).

### PHP-Einstellungen

Wir empfehlen bestimmte PHP-Konfigurationseinstellungen wie `memory_limit`, um häufige Probleme bei der Verwendung von Adobe Commerce und Magento Open Source zu vermeiden.

Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (als Befehlszeilen-Tool) 9.0.0

### RAM

Die Aktualisierung der Anwendungen und Erweiterungen, die Sie über das Commerce Marketplace und andere Quellen erhalten, kann bis zu 2 GB RAM erfordern. Wenn Sie ein System mit weniger als 2 GB RAM verwenden, empfehlen wir, eine [Datei tauschen](https://support.magento.com/hc/en-us/articles/360032980432); Andernfalls kann das Upgrade fehlschlagen.

### Systemabhängigkeiten

Adobe Commerce und Magento Open Source benötigen für einige Vorgänge die folgenden Systemwerkzeuge:

- [Bash](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [lsof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [nett](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [sed](https://www.gnu.org/software/sed/manual/sed.html)
- [tar](https://linux.die.net/man/1/tar)

### SSL

- Eine gültige [Sicherheitszertifikat](https://glossary.magento.com/security-certificate) ist für HTTPS erforderlich.
- Selbstsignierte SSL-Zertifikate werden nicht unterstützt.
- Transport Layer Security (TLS)-Anforderung - PayPal und `repo.magento.com` beide erfordern TLS 1.2 oder höher.

### Unterstützte Browser

Storefront und Admin:

- Microsoft Edge (neueste und frühere Hauptversion)
- Firefox (neueste und frühere Hauptversion) alle Betriebssysteme)
- Chrome (aktuelle und vorherige Hauptversion) alle Betriebssysteme)
- Safari (aktuelle und vorherige Hauptversion) Nur macOS)
- Safari Mobile für iPad 2, iPad Mini, iPad mit Retina Display (iOS 12 oder höher), für Desktop-Storefront
- Safari Mobile für iPhone 6 oder höher; iOS 12 oder höher für mobile Storefront
- Chrome für Mobilgeräte (neueste und frühere Hauptversion) [Android 4 oder höher] für mobile Storefront)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) oder höher (nur Entwicklungsumgebungen; kann sich nachteilig auf die Leistung auswirken)

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit `xdebug` , die sich auf Installationen von Adobe Commerce oder Magento Open Sourcen oder den Zugriff auf die Storefront oder den Administrator nach der Installation auswirken können. Weitere Informationen finden Sie unter [Bekanntes Problem mit xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
