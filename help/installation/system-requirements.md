---
title: Systemanforderungen
description: Verwenden Sie diese Referenz, um erforderliche Softwareabhängigkeiten zu identifizieren, die mit Adobe Commerce- und Magento Open Source-Versionen getestet wurden.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# Systemanforderungen

Im Folgenden werden Softwareabhängigkeiten und Dienste zusammengefasst, die für Adobe Commerce und Magento Open Source getestet wurden.

Es gibt einige Unterschiede in den Abhängigkeiten von Commerce für die Cloud-Infrastruktur. Die Service-Version und Kompatibilitätsunterstützung für Adobe Commerce in der Cloud-Infrastruktur werden durch Dienste bestimmt, die in den gehosteten Cloud-Umgebungen getestet und bereitgestellt werden. Manchmal unterscheiden sie sich von den Versionen, die von lokalen Adobe Commerce-Implementierungen unterstützt werden. Elasticsearch 7.17 wird beispielsweise für Commerce 2.4.4 für On-Premise-Implementierungen unterstützt, OpenSearch 1.2 wird jedoch für Commerce 2.4.4 in der Cloud-Infrastruktur unterstützt.

Die folgenden Tabellen zeigen Versionen von Softwareabhängigkeiten von Drittanbietern, die Adobe mit bestimmten Adobe Commerce- und Magento Open Source-Versionen getestet hat.

Adobe unterstützt nur die in den folgenden Tabellen beschriebenen Systemanforderungen. Beispielsweise ist 2.4.5 vollständig mit MariaDB 10.4 getestet. Adobe empfiehlt ein Upgrade auf MariaDB 10.4, bevor Sie auf 2.4.5 aktualisieren.

>[!BEGINTABS]

>[!TAB Commerce in Cloud]

Die [Commerce in Cloud-Vorlage](https://github.com/magento/magento-cloud) bietet eine Standardkonfiguration für Dienste, die mit einer bestimmten Commerce-Version kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Die Dienste und Versionen werden in [die `services.yaml` file](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Im Folgenden finden Sie die standardmäßige Dienstkonfiguration für Commerce 2.4.6 in der Cloud-Infrastruktur:

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Siehe [Dienste konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) im _Handel mit Cloud-Infrastruktur_ Handbuch.

>[!TAB Handel vor Ort]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-Einstellungen

Es gibt bestimmte PHP-Konfigurationseinstellungen, z. B. die `memory_limit` -Einstellung, mit der Sie allgemeine Probleme bei der Verwendung von Adobe Commerce und Magento Open Source vermeiden können. Siehe [Erforderliche PHP-Einstellungen](prerequisites/php-settings.md).

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) im _Handel mit Cloud-Infrastruktur_ Handbuch.

### PHP OPcache

Es wird empfohlen, dass Sie überprüfen, ob [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) aus Leistungsgründen aktiviert ist. Der OPcache ist in vielen PHP-Distributionen aktiviert. Die `opcache` -Erweiterung wird standardmäßig in der Commerce on Cloud -Infrastruktur installiert.

Informationen zur On-Premesis-Installation finden Sie unter [PHP-Einstellungen](prerequisites/php-settings.md). Weitere Informationen zu Leistungseinstellungen finden Sie in den Softwareempfehlungen für [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) im _Best Practices für die Leistung_ Handbuch.

Wenn Sie OPcache separat installieren müssen, lesen Sie den Abschnitt [PHP OPcache-Dokumentation](https://www.php.net/manual/en/opcache.setup.php).

### PHP Process Control

{{php-process-control}}

### PHPUnit

PHPUnit (als Befehlszeilen-Tool) 9.0.0

### PHP-Erweiterungen

Die [Installationsanweisungen für PHP](prerequisites/php-settings.md) einen Schritt zur Installation dieser Erweiterungen enthalten.

>[!TIP]
>
>Informationen zu PHP-Erweiterungen in der Cloud-Infrastruktur finden Sie unter [PHP-Erweiterungen aktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) im _Handel mit Cloud-Infrastruktur_ Handbuch.

>[!BEGINTABS]

>[!TAB Commerce in Cloud]

Die folgende Tabelle zeigt die unterstützten PHP-Erweiterungen bei der Bereitstellung von Adobe Commerce auf der Cloud-Plattform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Handel vor Ort]

{{$include /help/_includes/templated/php-extensions.md}}

Siehe Abschnitt [offizielle PHP-Dokumentation](https://www.php.net/manual/en/extensions.php) für Installationsdetails.

>[!ENDTABS]

## Sonstiges

In diesem Abschnitt wird die Unterstützung und Kompatibilität für alle anderen Arten von erforderlicher und optionaler Software beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce und Magento Open Source. Gegebenenfalls wird Commerce on Cloud-Infrastruktur-Anleitungen bereitgestellt.

### Browser

Storefront und Admin:

- Microsoft Edge (neueste und frühere Hauptversion)
- Firefox (neueste und vorherige Hauptversion; beliebige Betriebssysteme)
- Chrome (neueste und vorherige Hauptversion; jedes Betriebssystem)
- Safari (neueste und vorherige Hauptversion, nur macOS)
- Safari Mobile für iPad 2, iPad Mini, iPad mit Retina Display (iOS 12 oder höher), für Desktop-Storefront
- Safari Mobile für iPhone 6 oder höher; iOS 12 oder höher für mobile Storefront
- Chrome für Mobilgeräte (neueste und frühere Hauptversion) [Android™ 4 oder höher] für mobile Storefront)

### Mail-Server

Mail Transfer Agent (MTA) oder ein SMTP-Server. Commerce in Cloud-Infrastruktur verwendet die [SendGrid-E-Mail-Dienst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Speicher

Die Aktualisierung der Anwendungen und Erweiterungen, die Sie über das Commerce Marketplace und andere Quellen erhalten, kann bis zu 2 GB RAM erfordern. Wenn Sie ein System mit weniger als 2 GB RAM verwenden, erstellen Sie eine [Datei tauschen](https://support.magento.com/hc/en-us/articles/360032980432); andernfalls kann das Upgrade fehlschlagen.

### Betriebssysteme (Linux x86-64)

Linux-Distributionen wie RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian und Ähnliches. Microsoft Windows und macOS werden nicht unterstützt.

Adobe Commerce und Magento Open Source benötigen für einige Vorgänge die folgenden Systemwerkzeuge:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Für HTTPS ist ein gültiges Sicherheitszertifikat erforderlich.
- Selbstsignierte SSL-Zertifikate werden nicht unterstützt.
- Transport Layer Security (TLS)-Anforderung - PayPal und `repo.magento.com` beide erfordern TLS 1.2 oder höher.

Informationen zum Commerce in Cloud-Infrastrukturen finden Sie unter [Schnelle Konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im _Handel mit Cloud-Infrastruktur_ Handbuch.

### Xdebug

Verwenden Sie für Adobe Commerce und Magento Open Source [php_xdebug 2.5.x](https://xdebug.org/download) oder höher (nur Entwicklungsumgebungen; kann sich nachteilig auf die Leistung auswirken).

Informationen zu Adobe Commerce on Cloud finden Sie unter [Xdebug konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) im _Handel mit Cloud-Infrastruktur_ Handbuch.

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit `xdebug` , die sich auf Installationen von Adobe Commerce oder Magento Open Sourcen oder den Zugriff auf die Storefront oder den Administrator nach der Installation auswirken können. Siehe [Bekanntes Problem, das sich auf `xdebug` Installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) im _Knowledge Base für Commerce-Support_.
