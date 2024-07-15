---
title: Systemanforderungen
description: Verwenden Sie diese Referenz, um erforderliche Softwareabhängigkeiten zu identifizieren, die mit Adobe Commerce-Versionen getestet wurden.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Systemanforderungen

Im Folgenden werden Softwareabhängigkeiten und Dienste zusammengefasst, die für Adobe Commerce getestet wurden.

Es gibt einige Unterschiede in den Abhängigkeiten von Commerce zur Cloud-Infrastruktur. Die Service-Version und Kompatibilitätsunterstützung für Adobe Commerce in der Cloud-Infrastruktur werden durch Dienste bestimmt, die in den gehosteten Cloud-Umgebungen getestet und bereitgestellt werden. Manchmal unterscheiden sie sich von den Versionen, die von lokalen Adobe Commerce-Implementierungen unterstützt werden. Elasticsearch 7.17 wird beispielsweise für Commerce 2.4.4 für On-Premise-Implementierungen unterstützt, OpenSearch 1.2 wird jedoch für Commerce 2.4.4 in der Cloud-Infrastruktur unterstützt.

Die folgenden Tabellen zeigen Versionen von Softwareabhängigkeiten von Drittanbietern, die Adobe mit bestimmten Adobe Commerce-Versionen getestet hat.

Adobe unterstützt nur die in den folgenden Tabellen beschriebenen Systemanforderungen. Beispielsweise ist 2.4.5 vollständig mit MariaDB 10.4 getestet. Adobe empfiehlt ein Upgrade auf MariaDB 10.4, bevor Sie auf 2.4.5 aktualisieren.

>[!BEGINTABS]

>[!TAB Commerce in Cloud]

Die Vorlage &quot;[Commerce on Cloud&quot;](https://github.com/magento/magento-cloud) bietet eine Standardkonfiguration für Dienste, die mit einer bestimmten Commerce-Version kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Die Dienste und Versionen werden in [der `services.yaml`-Datei](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) definiert. Im Folgenden finden Sie die standardmäßige Dienstkonfiguration für Commerce 2.4.6 in der Cloud-Infrastruktur:

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

Siehe [Konfigurieren von Diensten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) im Handbuch _Commerce on Cloud Infrastructure_.

>[!TAB Commerce vor Ort]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-Einstellungen

Es gibt bestimmte PHP-Konfigurationseinstellungen, wie z. B. die Einstellung &quot;`memory_limit`&quot;, die Ihnen helfen können, häufige Probleme bei der Verwendung von Adobe Commerce zu vermeiden. Siehe [Erforderliche PHP-Einstellungen](prerequisites/php-settings.md).

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) im Handbuch _Commerce on Cloud Infrastructure_ .

### PHP OPcache

Es wird empfohlen, zu überprüfen, ob [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) aus Leistungsgründen aktiviert ist. Der OPcache ist in vielen PHP-Distributionen aktiviert. Die Erweiterung `opcache` wird standardmäßig in der Commerce on Cloud-Infrastruktur installiert.

Überprüfen Sie für On-Premesis, ob PHP OPcache installiert ist, siehe [PHP-Einstellungen](prerequisites/php-settings.md). Weitere Informationen zu Leistungseinstellungen finden Sie in den Softwareempfehlungen für [PHP-Einstellungen](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) im Handbuch _Best Practices für die Leistung_ .

Wenn Sie OPcache separat installieren müssen, lesen Sie die [PHP OPcache-Dokumentation](https://www.php.net/manual/en/opcache.setup.php).

### PHP Process Control

{{php-process-control}}

### PHPUnit

PHPUnit v9 (als Befehlszeilen-Tool).

### PHP-Erweiterungen

Die [PHP-Installationsanweisungen](prerequisites/php-settings.md) enthalten einen Schritt zur Installation dieser Erweiterungen.

>[!TIP]
>
>Informationen zu PHP-Erweiterungen in der Cloud-Infrastruktur finden Sie unter [Aktivieren von PHP-Erweiterungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) im Handbuch _Commerce on Cloud Infrastructure_ .

>[!BEGINTABS]

>[!TAB Commerce in Cloud]

Die folgende Tabelle zeigt die unterstützten PHP-Erweiterungen bei der Bereitstellung von Adobe Commerce auf der Cloud-Plattform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce vor Ort]

{{$include /help/_includes/templated/php-extensions.md}}

Installationsdetails finden Sie in der [offiziellen PHP-Dokumentation](https://www.php.net/manual/en/extensions.php) .

>[!ENDTABS]

## Sonstiges

In diesem Abschnitt wird die Unterstützung und Kompatibilität für alle anderen Arten von erforderlicher und optionaler Software beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce. Gegebenenfalls wird Commerce on Cloud-Infrastruktur-Anleitungen bereitgestellt.

### Browser

Storefront und Admin:

- Microsoft Edge (neueste und vorherige Hauptversion)
- Firefox (neueste und vorherige Hauptversion; beliebige Betriebssysteme)
- Chrome (neueste und frühere Hauptversion, alle Betriebssysteme)
- Safari (neueste und vorherige Hauptversion, nur macOS)
- Safari für iOS (neueste und vorherige Hauptversion, für Storefront)
- Chrome für Android (neueste und vorherige Hauptversion, für Storefront)

### Mail-Server

Mail Transfer Agent (MTA) oder ein SMTP-Server. Commerce on Cloud-Infrastruktur verwendet den [SendGrid-E-Mail-Dienst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Speicher

Die Aktualisierung der Anwendungen und Erweiterungen, die Sie über das Commerce Marketplace und andere Quellen erhalten, kann bis zu 2 GB RAM erfordern. Wenn Sie ein System mit weniger als 2 GB RAM verwenden, erstellen Sie eine [Swap-Datei](https://support.magento.com/hc/en-us/articles/360032980432). Andernfalls schlägt das Upgrade möglicherweise fehl.

### Betriebssysteme (Linux x86-64)

Linux-Distributionen wie RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian und Ähnliches. Microsoft Windows und macOS werden nicht unterstützt.

Für einige Vorgänge erfordert Adobe Commerce die folgenden Systemwerkzeuge:

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
- Transport Layer Security (TLS)-Anforderungen - PayPal und `repo.magento.com` erfordern beide TLS 1.2 oder höher.

Informationen zu Commerce on Cloud-Infrastruktur finden Sie unter [Schnelle Konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Handbuch _Commerce on Cloud Infrastructure_ .

### Xdebug

Verwenden Sie für Adobe Commerce [php_xdebug 2.5.x](https://xdebug.org/download) oder höher (nur Entwicklungsumgebungen, die die Leistung beeinträchtigen können).

Informationen zu Adobe Commerce on Cloud finden Sie unter [Xdebug konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) im Handbuch _Commerce on Cloud Infrastructure_ .

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit `xdebug`, das sich auf Adobe Commerce-Installationen oder den Zugriff auf die Storefront oder den Administrator nach der Installation auswirken kann. Siehe [Bekanntes Problem, das sich auf `xdebug` Installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) auswirkt, in der _Wissensdatenbank zur Commerce-Unterstützung_.
