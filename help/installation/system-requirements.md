---
title: Systemanforderungen
description: Erfahren Sie mehr über Softwareabhängigkeiten und Systemanforderungen für Adobe Commerce. Informationen zur Kompatibilität mit Ihrer Bereitstellungsumgebung finden Sie unter Getestete Konfigurationen .
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: cba883644156d5eef54796003f46e4bc6cd08d5d
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%

---

# Systemanforderungen

Die folgenden Informationen enthalten eine Zusammenfassung der für Adobe Commerce getesteten Softwareabhängigkeiten und Services.

Es gibt einige Unterschiede in den Abhängigkeiten für Commerce in Cloud Manager. Die Unterstützung der Service-Version und -Kompatibilität für Adobe Commerce on Cloud wird durch Services bestimmt, die in den gehosteten Cloud-Umgebungen getestet und bereitgestellt werden und sich manchmal von den Versionen unterscheiden, die von lokalen Adobe Commerce-Bereitstellungen unterstützt werden.

>[!IMPORTANT]
>
>In der Tabelle mit den Systemanforderungen sind die Adobe Commerce-Versionen aufgeführt, für die sie gelten, einschließlich Versionen mit der Bezeichnung Beta oder früher Zugriff.
>In den [Versionshinweisen](../release/release-notes/overview.md) finden Sie die neuesten veröffentlichten Commerce-Versionen.
>
>Wenn Ihre Service-Versionen nicht mit der unterstützten Konfiguration für Ihre Commerce-Version übereinstimmen, kann sich das Verhalten von dem unterscheiden, was Adobe beim Testen reproduzieren kann. Der Adobe-Support bittet Sie möglicherweise, Ihre Umgebung an einer unterstützten Konfiguration auszurichten, bevor Sie das gemeldete Verhalten untersuchen, beheben oder validieren. Nachdem Sie Ihre Umgebung angepasst haben, kann der Adobe-Support die Untersuchung fortsetzen.

Die folgenden Tabellen zeigen Versionen von Software-Abhängigkeiten von Drittanbietern, die Adobe mit bestimmten Adobe Commerce-Versionen getestet hat.

Adobe unterstützt nur die in den folgenden Tabellen aufgeführten Systemanforderungskombinationen. Adobe unterstützt keine Konfigurationen, die mit keiner aufgelisteten Kombination übereinstimmen. Beispielsweise wird Adobe Commerce 2.4.9 mit MariaDB 12.3 getestet. Aktualisieren Sie auf MariaDB 12.3, bevor Sie auf 2.4.9 aktualisieren.

## Systemanforderungen für die neuesten Commerce-Versionen

In den folgenden Tabellen sind die Systemanforderungen für die neueste Version aller unterstützten Commerce-Versionen zusammengefasst. Adobe empfiehlt allen Kunden, ein Upgrade auf diese Versionen durchzuführen.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die [Commerce on Cloud-Vorlage](https://github.com/magento/magento-cloud) stellt eine Standardkonfiguration für Services bereit, die mit der neuesten Commerce-Version für jede Release-Zeile kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Für die Standardkonfiguration werden die Services und Versionen in [der `services.yaml`-Datei) &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Weitere Informationen finden Sie unter [Services konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) im *Handbuch zu Commerce in Cloud-*.

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 hat am 30. April 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.7, 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität mehr oder
Unterstützung für alle MySQL-Versionen, die nach MySQL 8.0 veröffentlicht wurden. Adobe nicht
Validieren oder Bereitstellen von Unterstützung für neuere MySQL-Hauptversionen auf dieser Adobe
Commerce-Release-Zeile.
Bei allen Adobe Commerce On-Premises-Kunden, die die Versionen 2.4.7, 2.4.6, 2.4.5 und 2.4.4 ausführen, werden die
Es wird empfohlen, die Datenbankserver auf eine kompatible MariaDB-Version zu migrieren.

Adobe Commerce on Cloud-Kunden müssen Plattformabhängigkeiten für unterstützte Versionen beibehalten. Siehe [Platform-Abhängigkeiten](../release/lifecycle-policy.md#platform-dependencies) in der Lebenszyklusrichtlinie.

**Elasticsearch 7.17 hat am 15. Januar 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität mehr oder
Unterstützung für alle Elasticsearch-Versionen, die nach Elasticsearch 7 veröffentlicht wurden. Adobe nicht
Validieren oder Bereitstellen von Unterstützung für neuere Elasticsearch-Hauptversionen auf dieser Adobe
Commerce-Release-Zeile.
Bei allen Adobe Commerce On-Premises-Kunden, die die Versionen 2.4.6, 2.4.5 und 2.4.4 ausführen, werden die
empfohlen, ihre Suchinfrastruktur auf eine kompatible OpenSearch-Version zu migrieren.

>[!ENDTABS]

## Systemanforderungen für frühere Versionen von Commerce

In den folgenden Tabellen sind die Systemanforderungen für Adobe Commerce-Versionen aufgeführt, einschließlich der Anforderungen an die erweiterte Unterstützung. Diese Tabellen dienen nur zu Referenzzwecken. Adobe rät davon ab, nicht unterstützte Versionen von Softwareabhängigkeiten zu verwenden. Der Support erfordert, dass Sie Ihre Umgebung an einer unterstützten Konfiguration ausrichten, bevor wir gemeldetes Verhalten untersuchen, beheben oder validieren können.

>[!NOTE]
>
>Adobe Commerce 2.4.6 wird bis [30. **2027](../release/lifecycle-policy.md#extended-support) unterstützt,** gefolgt von einem [Übergangszeitraum, &#x200B;](../release/lifecycle-policy.md#security-only-transitional-period) bis **31. Mai 2028**. Diese Bestimmungen stehen nur Kunden von Adobe Commerce zur Verfügung. Sie erweitern die Unterstützung für Drittanbieterabhängigkeiten wie MySQL nicht.
>
>Wenn Sie Adobe Commerce on Cloud ausführen, müssen Sie vor dem Erzwingungsdatum des **1. Juni 2028) ein Upgrade auf eine unterstützte Version** oder [&#x200B; [!DNL Adobe Commerce as a Cloud Service] &#x200B;](../release/version-upgrade-enforcement-policy.md). Vollständige Lebenszyklusdaten finden Sie in [&#x200B; Tabelle &#x200B;](../release/lifecycle-policy.md#end-of-support-dates)Ende der Support-Daten“.
>
>Die Tabelle wird reduziert, um die Länge dieses Artikels zu minimieren. Wählen Sie die Kopfzeile aus, um sie zu erweitern.

+++Anforderungen für frühere Versionen

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die [Commerce on Cloud-Vorlage](https://github.com/magento/magento-cloud) stellt eine Standardkonfiguration für Services bereit, die mit einer bestimmten Commerce-Version kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Für die Standardkonfiguration werden die Services und Versionen in [der `services.yaml`-Datei) &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Weitere Informationen finden Sie unter [Services konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) im *Handbuch zu Commerce in Cloud-*.

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 hat am 30. April 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.7, 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität mehr oder
Unterstützung für alle MySQL-Versionen, die nach MySQL 8.0 veröffentlicht wurden. Adobe nicht
Validieren oder Bereitstellen von Unterstützung für neuere MySQL-Hauptversionen auf dieser Adobe
Commerce-Release-Zeile.
Bei allen Adobe Commerce On-Premises-Kunden, die die Versionen 2.4.7, 2.4.6, 2.4.5 und 2.4.4 ausführen, werden die
Es wird empfohlen, die Datenbankserver auf eine kompatible MariaDB-Version zu migrieren.

Adobe Commerce on Cloud-Kunden müssen Plattformabhängigkeiten für unterstützte Versionen beibehalten. Siehe [Platform-Abhängigkeiten](../release/lifecycle-policy.md#platform-dependencies) in der Lebenszyklusrichtlinie.

**Elasticsearch 7.17 hat am 15. Januar 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität mehr oder
Unterstützung für alle Elasticsearch-Versionen, die nach Elasticsearch 7 veröffentlicht wurden. Adobe nicht
Validieren oder Bereitstellen von Unterstützung für neuere Elasticsearch-Hauptversionen auf dieser Adobe
Commerce-Release-Zeile.
Bei allen Adobe Commerce On-Premises-Kunden, die die Versionen 2.4.6, 2.4.5 und 2.4.4 ausführen, werden die
empfohlen, ihre Suchinfrastruktur auf eine kompatible OpenSearch-Version zu migrieren.

>[!ENDTABS]

+++

## PHP-Einstellungen

Es gibt bestimmte PHP-Konfigurationseinstellungen, wie zum Beispiel die `memory_limit`, die Ihnen helfen können, gängige Probleme bei der Verwendung von Adobe Commerce zu vermeiden. Siehe [Erforderliche PHP-](prerequisites/php-settings.md).

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/app/php-settings) im *Handbuch zu Commerce* Cloud-Infrastruktur.

### PHP-OP-Cache

Adobe empfiehlt aus Leistungsgründen zu überprüfen, ob [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) aktiviert ist. Der OPcache ist in vielen PHP Distributionen aktiviert.

- **Bei Adobe Commerce in Cloud** Infrastrukturbereitstellungen wird die `opcache`-Erweiterung standardmäßig installiert.
- **Für lokale Adobe Commerce-Bereitstellungen:**
  - [Überprüfen Sie, ob die PHP OPcache-Erweiterung installiert ist](prerequisites/php-settings.md#verify-php-is-installed).
  - Spezifische Anleitungen zu Leistungseinstellungen finden Sie in den Softwareempfehlungen für [PHP-Einstellungen](../performance/software.md#php-settings) im *Performance Best Practices*-Handbuch.


Wenn Sie OPcache separat installieren müssen, lesen Sie die [PHP OPcache-Dokumentation](https://www.php.net/manual/en/opcache.setup.php).

### PHP-Prozesssteuerung

{{php-process-control}}

### PHPUnit

Die unterstützte PHPUnit-Hauptversion hängt von der Adobe Commerce-Version ab. Adobe testet 2.4.9 mit PHPUnit 12, 2.4.8-p5 mit PHPUnit 10 und 2.4.7-p10 bis 2.4.4-p18 mit PHPUnit 9. Installieren Sie PHPUnit als Befehlszeilen-Tool auf der Hauptversion, die den von Adobe getesteten Konfigurationen für Ihre Version entspricht.

### PHP-Erweiterungen

Die [PHP-Installationsanweisungen](prerequisites/php-settings.md) enthalten einen Schritt zur Installation dieser Erweiterungen.

>[!TIP]
>
>Informationen zu PHP-Erweiterungen in der Cloud-Infrastruktur finden Sie unter [Aktivieren von PHP-Erweiterungen](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) im _Handbuch zu Commerce in_.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die folgende Tabelle zeigt die unterstützten PHP-Erweiterungen bei der Bereitstellung von Adobe Commerce auf der Cloud-Plattform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/php-extensions.md}}

Siehe [Offizielle PHP-Dokumentation](https://www.php.net/manual/en/extensions.php) für Installationsdetails.

>[!ENDTABS]

## Sonstige Softwareanforderungen

In diesem Abschnitt werden die Unterstützung und Kompatibilität für alle anderen erforderlichen und optionalen Softwaretypen beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce. Gegebenenfalls wird eine Anleitung zur Commerce-Cloud-Infrastruktur bereitgestellt.

### Browser

Storefront und Admin:

- Microsoft Edge (neueste und vorherige Hauptversion)
- Firefox (neueste und vorherige Hauptversion auf jedem Betriebssystem)
- Chrome (neueste und vorherige Hauptversion auf jedem Betriebssystem)
- Safari (nur neueste und vorherige Hauptversion auf macOS)
- Safari für iOS (neueste und vorherige Hauptversion für die Storefront)
- Chrome für Android (neueste und vorherige Hauptversion für die Storefront)

### Mail-Server

Mail Transfer Agent (MTA) oder SMTP-Server. Commerce in der Cloud-Infrastruktur verwendet den [SendGrid-E-Mail-Service](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Arbeitsspeicher

Für das Upgrade der Anwendungen und Erweiterungen, die Sie über die Commerce Marketplace und andere Quellen erhalten, können bis zu 2 GB RAM erforderlich sein. Wenn Sie ein System mit weniger als 2 GB RAM verwenden, erstellen Sie eine [Auslagerungsdatei](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Andernfalls schlägt das Upgrade möglicherweise fehl.

### Betriebssysteme (Linux x86-64)

Linux-Distributionen wie Red Hat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian und ähnliche.

Microsoft Windows und macOS **nicht**.

Adobe Commerce erfordert für einige Vorgänge die folgenden Systemtools:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- Für HTTPS ist ein gültiges Sicherheitszertifikat erforderlich.
- Selbstsignierte SSL-Zertifikate werden nicht unterstützt.
- Transport Layer Security (TLS)-Anforderung - PayPal und `repo.magento.com` erfordern beide TLS 1.2 oder höher.

Informationen zu Commerce in Cloud-Infrastrukturen finden Sie unter [Fastly-](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)) im Handbuch *Commerce in Cloud-*.

### xdebug

Verwenden Sie für Adobe Commerce [php_xdebug 2.5.x](https://xdebug.org/download) oder höher (nur Entwicklungsumgebungen; kann die Leistung beeinträchtigen).

Informationen zu Adobe Commerce on Cloud finden Sie [Konfigurieren von Xdebug](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/test/debug) im Handbuch *Commerce on Cloud Infrastructure*.

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit `xdebug`, das sich auf Adobe Commerce-Installationen oder den Zugriff auf die Storefront oder den Admin nach der Installation auswirken kann. Siehe [Bekanntes Problem, das `xdebug` Installation betrifft](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) in der _Commerce Support Knowledge Base_.

<!-- Last updated from includes: 2026-07-22 16:57:39 -->
