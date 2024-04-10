---
title: Systemanforderungen
description: Verwenden Sie diese Referenz, um erforderliche Softwareabhängigkeiten zu identifizieren, die mit Adobe Commerce- und Magento Open Source-Versionen getestet wurden.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 4087d5f5de0bc11ce120d61a539800a3533893f0
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Systemanforderungen

Im Folgenden finden Sie eine Zusammenfassung der Softwareabhängigkeiten und Services, die für Adobe Commerce und Magento Open Source getestet wurden.

Es gibt einige Unterschiede bei den Abhängigkeiten für Commerce in der Cloud-Infrastruktur. Die Unterstützung der Service-Version und -Kompatibilität für Adobe Commerce auf Cloud-Infrastrukturen wird durch Services bestimmt, die in den gehosteten Cloud-Umgebungen getestet und bereitgestellt werden, und unterscheidet sich manchmal von Versionen, die von Adobe Commerce On-Premise-Bereitstellungen unterstützt werden. Beispielsweise wird Elasticsearch 7.17 für On-Premise-Bereitstellungen in Commerce 2.4.4 unterstützt, OpenSearch 1.2 jedoch für Commerce 2.4.4 in Cloud-Infrastrukturen.

Die folgenden Tabellen zeigen Versionen von Software-Abhängigkeiten von Drittanbietern, die Adobe mit bestimmten Adobe Commerce- und Magento Open Source-Versionen getestet hat.

Adobe unterstützt nur die in den folgenden Tabellen beschriebene Kombination von Systemanforderungen. Beispielsweise wurde 2.4.5 vollständig mit MariaDB 10.4 getestet. Adobe empfiehlt, auf MariaDB 10.4 zu aktualisieren, bevor Sie auf 2.4.5 aktualisieren.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die [Vorlage „Commerce in Cloud“](https://github.com/magento/magento-cloud) stellt eine Standardkonfiguration für Dienste bereit, die mit einer bestimmten Commerce-Version kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Die Services und Versionen werden definiert in [Die `services.yaml` Datei](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Im Folgenden finden Sie die standardmäßige Service-Konfiguration für Commerce 2.4.6 in der Cloud-Infrastruktur:

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

Siehe [Konfigurieren von Diensten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in der _Commerce mit Cloud-Infrastruktur_ Handbuch.

>[!TAB On-Premise-Commerce]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-Einstellungen

Es gibt bestimmte PHP-Konfigurationseinstellungen, wie zum Beispiel `memory_limit` -Einstellung verwenden, was Ihnen helfen kann, gängige Probleme bei der Verwendung von Adobe Commerce und Magento Open Source zu vermeiden. Siehe [Erforderliche PHP-Einstellungen](prerequisites/php-settings.md).

Anleitungen zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) in der _Commerce mit Cloud-Infrastruktur_ Handbuch.

### PHP-OP-Cache

Es wird empfohlen, Folgendes zu überprüfen [PHP-OP-Cache](https://www.php.net/manual/en/intro.opcache.php) ist aus Leistungsgründen aktiviert. Der OPcache ist in vielen PHP Distributionen aktiviert. Die `opcache` -Erweiterung wird standardmäßig in der Commerce on Cloud-Infrastruktur installiert.

Überprüfen Sie für On-Premise, ob PHP OPcache installiert ist, siehe [PHP-Einstellungen](prerequisites/php-settings.md). Spezifische Anleitungen zu Leistungseinstellungen finden Sie in den Softwareempfehlungen für [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) in der _Best Practices für die Leistung_ Handbuch.

Wenn Sie OPcache separat installieren müssen, lesen Sie die [PHP OPcache-Dokumentation](https://www.php.net/manual/en/opcache.setup.php).

### PHP-Prozesssteuerung

{{php-process-control}}

### PHPUnit

PHPUnit v9 (als Befehlszeilen-Tool).

### PHP-Erweiterungen

Die [PHP-Installationsanweisungen](prerequisites/php-settings.md) Schließen Sie einen Schritt zur Installation dieser Erweiterungen ein.

>[!TIP]
>
>Informationen zu PHP-Erweiterungen in der Cloud-Infrastruktur finden Sie unter [PHP-Erweiterungen aktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) in der _Commerce mit Cloud-Infrastruktur_ Handbuch.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die folgende Tabelle zeigt die unterstützten PHP-Erweiterungen bei der Bereitstellung von Adobe Commerce auf der Cloud-Plattform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB On-Premise-Commerce]

{{$include /help/_includes/templated/php-extensions.md}}

Siehe [offizielle PHP-Dokumentation](https://www.php.net/manual/en/extensions.php) für Installationsdetails.

>[!ENDTABS]

## Sonstiges

In diesem Abschnitt werden die Unterstützung und Kompatibilität für alle anderen erforderlichen und optionalen Softwaretypen beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce und Magento Open Source. Sofern relevant, wird eine Anleitung zu Commerce in Cloud-Infrastrukturen bereitgestellt.

### Browser

Storefront und Admin:

- Microsoft Edge (neueste und vorherige Hauptversion)
- Firefox (neueste und vorherige Hauptversion; alle Betriebssysteme)
- Chrome (neueste und vorherige Hauptversion; beliebiges Betriebssystem)
- Safari (neueste und vorherige Hauptversion; nur macOS)
- Safari für iOS (neueste und vorherige Hauptversion, für Storefront)
- Chrome für Android (neueste und vorherige Hauptversion, für Storefront)

### Mail-Server

Mail Transfer Agent (MTA) oder SMTP-Server. Commerce in Cloud-Infrastruktur verwendet die [SendGrid-E-Mail-Service](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Arbeitsspeicher

Für das Upgrade der Anwendungen und Erweiterungen, die Sie von der Commerce Marketplace und anderen Quellen erhalten, können bis zu 2 GB RAM erforderlich sein. Wenn Sie ein System mit weniger als 2 GB RAM verwenden, erstellen Sie ein [Auslagerungsdatei](https://support.magento.com/hc/en-us/articles/360032980432); andernfalls schlägt das Upgrade möglicherweise fehl.

### Betriebssysteme (Linux x86-64)

Linux-Distributionen wie RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian und ähnliche. Microsoft Windows und macOS werden nicht unterstützt.

Adobe Commerce und Magento Open Source erfordern für einige Vorgänge die folgenden Systemwerkzeuge:

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
- Transport Layer Security (TLS)-Anforderung - PayPal und `repo.magento.com` Für beide ist TLS 1.2 oder höher erforderlich.

Informationen zu Commerce in Cloud-Infrastrukturen finden Sie unter [Schnelle Konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in der _Commerce mit Cloud-Infrastruktur_ Handbuch.

### xdebug

Verwenden Sie für Adobe Commerce und Magento Open Source Folgendes [php_xdebug 2.5.x](https://xdebug.org/download) oder höher (nur Entwicklungsumgebungen; kann die Leistung beeinträchtigen).

Für Adobe Commerce on Cloud siehe [Konfigurieren von xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) in der _Commerce mit Cloud-Infrastruktur_ Handbuch.

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit `xdebug` die sich auf Adobe Commerce- oder Magento Open Source-Installationen auswirken oder nach der Installation auf die Storefront oder den Admin zugreifen können. Siehe [Bekanntes Problem mit folgenden Auswirkungen `xdebug` Installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) in der _Commerce-Support-Wissensdatenbank_.
