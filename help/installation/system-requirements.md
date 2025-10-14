---
title: Systemanforderungen
description: Erfahren Sie mehr über Softwareabhängigkeiten und Systemanforderungen für Adobe Commerce. Entdecken Sie getestete Konfigurationen, um die Kompatibilität mit Ihrer Bereitstellungsumgebung sicherzustellen.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b1a202fde89ab05626194aff010111577ef6993
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Systemanforderungen

Im Folgenden werden die für Adobe Commerce getesteten Softwareabhängigkeiten und Services zusammengefasst.

Es gibt einige Unterschiede in den Abhängigkeiten für Commerce in Cloud Manager. Die Unterstützung der Service-Version und -Kompatibilität für Adobe Commerce on Cloud wird durch Services bestimmt, die in den gehosteten Cloud-Umgebungen getestet und bereitgestellt werden und sich manchmal von den Versionen unterscheiden, die von lokalen Adobe Commerce-Bereitstellungen unterstützt werden. Beispielsweise wird Elasticsearch 7.17 für Commerce 2.4.4 für On-Premise-Bereitstellungen unterstützt, aber OpenSearch 1 wird für 2.4.4 Adobe Commerce on Cloud unterstützt.

>[!NOTE]
>
>Die Systemanforderungen gelten nur für freigegebene Versionen von Adobe Commerce. Beta- oder Early-Access-Versionen sind nicht enthalten. Weitere [ zu den neuesten Versionen ](../release/release-notes/overview.md) Adobe Commerce finden Sie in den Versionshinweisen .

Die folgenden Tabellen zeigen Versionen von Software-Abhängigkeiten von Drittanbietern, die Adobe mit bestimmten Adobe Commerce-Versionen getestet hat.

Adobe unterstützt nur die in den folgenden Tabellen beschriebene Kombination von Systemanforderungen. Beispielsweise wurde 2.4.5 vollständig mit MariaDB 10.4 getestet. Adobe empfiehlt, auf MariaDB 10.4 zu aktualisieren, bevor Sie ein Upgrade auf 2.4.5 durchführen.

Um einen reibungslosen Upgrade-Prozess sicherzustellen und Bereitstellungsfehler zu vermeiden, empfiehlt Adobe, die RabbitMQ-Versionen schrittweise zu aktualisieren. Wenn Sie beispielsweise von Version 3.8 auf 4.1 aktualisieren, sollten Sie zunächst von 3.8 auf 3.9, dann von 3.9 auf 3.10 usw. aktualisieren. Erst nach dem Erreichen von Version 3.13 sollten Sie mit dem Upgrade auf Version 4.1 fortfahren.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die [Commerce on Cloud-Vorlage](https://github.com/magento/magento-cloud) stellt eine Standardkonfiguration für Services bereit, die mit einer bestimmten Commerce-Version kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Die Services und Versionen werden in [der `services.yaml`-Datei) ](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Im Folgenden finden Sie die standardmäßige Service-Konfiguration für Commerce 2.4.6 in der Cloud-Infrastruktur:

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

Siehe [Konfigurieren von Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) im _Handbuch zu Commerce_ Cloud-Infrastruktur.

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-Einstellungen

Es gibt bestimmte PHP-Konfigurationseinstellungen, wie zum Beispiel die `memory_limit`, die Ihnen helfen können, gängige Probleme bei der Verwendung von Adobe Commerce zu vermeiden. Siehe [Erforderliche PHP-](prerequisites/php-settings.md).

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) im _Handbuch zu Commerce_ Cloud-Infrastruktur.

### PHP-OP-Cache

Es wird empfohlen zu überprüfen, ob [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) aus Leistungsgründen aktiviert ist. Der OPcache ist in vielen PHP Distributionen aktiviert. Die `opcache`-Erweiterung wird standardmäßig in der Commerce in der Cloud-Infrastruktur installiert.

Überprüfen Sie für On-Premises, ob PHP OPcache installiert ist, siehe [PHP-Einstellungen](prerequisites/php-settings.md). Spezifische Anleitungen zu Leistungseinstellungen finden Sie in den Softwareempfehlungen für [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) im _Performance Best Practices_-Handbuch.

Wenn Sie OPcache separat installieren müssen, lesen Sie die [PHP OPcache-Dokumentation](https://www.php.net/manual/en/opcache.setup.php).

### PHP-Prozesssteuerung

{{php-process-control}}

### PHPUnit

PHPUnit v9 (als Befehlszeilen-Tool).

### PHP-Erweiterungen

Die [PHP-Installationsanweisungen](prerequisites/php-settings.md) enthalten einen Schritt zur Installation dieser Erweiterungen.

>[!TIP]
>
>Informationen zu PHP-Erweiterungen in der Cloud-Infrastruktur finden Sie unter [Aktivieren von PHP-Erweiterungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) im _Handbuch zu Commerce in_.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die folgende Tabelle zeigt die unterstützten PHP-Erweiterungen bei der Bereitstellung von Adobe Commerce auf der Cloud-Plattform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/php-extensions.md}}

Siehe [Offizielle PHP-Dokumentation](https://www.php.net/manual/en/extensions.php) für Installationsdetails.

>[!ENDTABS]

## Verschiedenes

In diesem Abschnitt werden die Unterstützung und Kompatibilität für alle anderen erforderlichen und optionalen Softwaretypen beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce. Gegebenenfalls wird eine Anleitung zur Commerce-Cloud-Infrastruktur bereitgestellt.

### Browser

Storefront und Admin:

- Microsoft Edge (neueste und vorherige Hauptversion)
- Firefox (neueste und vorherige Hauptversion; alle Betriebssysteme)
- Chrome (neueste und vorherige Hauptversion; beliebiges Betriebssystem)
- Safari (neueste und vorherige Hauptversion; nur macOS)
- Safari für iOS (neueste und vorherige Hauptversion, für Storefront)
- Chrome für Android (neueste und vorherige Hauptversion, für Storefront)

### Mail-Server

Mail Transfer Agent (MTA) oder SMTP-Server. Commerce in der Cloud-Infrastruktur verwendet den [SendGrid-E-Mail-Service](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Arbeitsspeicher

Für das Upgrade der Anwendungen und Erweiterungen, die Sie über die Commerce Marketplace und andere Quellen erhalten, können bis zu 2 GB RAM erforderlich sein. Wenn Sie ein System mit weniger als 2 GB RAM verwenden, erstellen Sie eine [Auslagerungsdatei](https://support.magento.com/hc/en-us/articles/360032980432) andernfalls schlägt Ihr Upgrade möglicherweise fehl.

### Betriebssysteme (Linux x86-64)

Linux-Distributionen wie RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian und ähnliche.

Microsoft Windows und macOS **nicht**.

Adobe Commerce erfordert für einige Vorgänge die folgenden Systemtools:

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
- Transport Layer Security (TLS)-Anforderung - PayPal und `repo.magento.com` erfordern beide TLS 1.2 oder höher.

Informationen zu Commerce in Cloud-Infrastrukturen finden Sie unter [Fastly-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)) im Handbuch _Commerce in Cloud-_.

### xdebug

Verwenden Sie für Adobe Commerce [php_xdebug 2.5.x](https://xdebug.org/download) oder höher (nur Entwicklungsumgebungen; kann die Leistung beeinträchtigen).

Informationen zu Adobe Commerce on Cloud finden Sie [Konfigurieren von Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) im Handbuch _Commerce on Cloud Infrastructure_.

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit `xdebug`, das sich auf Adobe Commerce-Installationen oder den Zugriff auf die Storefront oder den Admin nach der Installation auswirken kann. Siehe [Bekanntes Problem, das `xdebug` Installation betrifft](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) in der _Commerce Support Knowledge Base_.


<!-- Last updated from includes: 2025-10-09 19:48:53 -->
