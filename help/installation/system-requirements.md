---
title: Systemanforderungen
description: Erfahren Sie mehr über Softwareabhängigkeiten und Systemanforderungen für Adobe Commerce. Informationen zur Kompatibilität mit Ihrer Bereitstellungsumgebung finden Sie unter Getestete Konfigurationen .
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-10-13
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 37a993a1f9b187dcfa74ecde581cf705eb66570d
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# Systemanforderungen

Die folgenden Informationen enthalten eine Zusammenfassung der für Adobe Commerce getesteten Softwareabhängigkeiten und Services.

Die Softwareabhängigkeiten für Adobe Commerce auf Cloud-Infrastruktur unterscheiden sich von denen für lokale Bereitstellungen. Adobe bestimmt unterstützte Dienstversionen und Kompatibilität basierend auf Diensten, die in gehosteten Cloud-Umgebungen getestet und bereitgestellt werden. Diese Versionen unterscheiden sich manchmal von den Versionen, die für lokale Bereitstellungen unterstützt werden.

>[!IMPORTANT]
>
>In der Tabelle mit den Systemanforderungen sind die Adobe Commerce-Versionen aufgeführt, für die sie gelten, einschließlich Versionen mit der Bezeichnung Beta oder früher Zugriff.
>Die [&#x200B; veröffentlichten Commerce-Versionen finden &#x200B;](../release/release-notes/overview.md) in den Versionshinweisen .
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

Die [`services.yaml`-Datei &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) die Standard-Services und -Versionen.
Siehe [Konfigurieren von Services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) im *Handbuch zu Commerce* Cloud-Infrastruktur.

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 hat am 30. April 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.7, 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität und keine Unterstützung für MySQL-Versionen, die nach MySQL 8.0 veröffentlicht wurden.
Adobe validiert oder unterstützt keine neueren MySQL-Hauptversionen für diese Commerce-Versionen.
Wenn Sie die Adobe Commerce On-Premises-Versionen 2.4.7, 2.4.6, 2.4.5 oder 2.4.4 ausführen, empfiehlt Adobe dringend, Ihre Datenbankserver auf eine kompatible MariaDB-Version zu migrieren.

Adobe Commerce on Cloud-Kunden müssen Plattformabhängigkeiten für unterstützte Versionen beibehalten. Siehe [Platform-Abhängigkeiten](../release/lifecycle-policy.md#platform-dependencies) in der Lebenszyklusrichtlinie.

**Elasticsearch 7.17 hat am 15. Januar 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität mehr und keine Unterstützung für Elasticsearch-Versionen, die nach Elasticsearch 7 veröffentlicht wurden.
Adobe validiert oder unterstützt keine neueren Elasticsearch-Hauptversionen für diese Commerce-Versionen.
Wenn Sie die lokalen Adobe Commerce-Versionen 2.4.6, 2.4.5 oder 2.4.4 ausführen, empfiehlt Adobe dringend, Ihre Suchinfrastruktur auf eine kompatible OpenSearch-Version zu migrieren.

>[!ENDTABS]

## Systemanforderungen für Version 2.4.10-alpha der Commerce-Version

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## Systemanforderungen für frühere Versionen von Commerce

In den folgenden Tabellen sind die Systemanforderungen für Adobe Commerce-Versionen aufgeführt, einschließlich der Anforderungen an die erweiterte Unterstützung. Verwenden Sie diese Tabellen nur als Referenz. Adobe rät davon ab, nicht unterstützte Versionen von Softwareabhängigkeiten zu verwenden. Bevor der Adobe-Support das gemeldete Verhalten untersucht, behebt oder validiert, müssen Sie Ihre Umgebung an einer unterstützten Konfiguration ausrichten.

>[!NOTE]
>
>Adobe Commerce 2.4.6 wird bis [30. **2027](../release/lifecycle-policy.md#extended-support) unterstützt,** gefolgt von einem [Übergangszeitraum, &#x200B;](../release/lifecycle-policy.md#security-only-transitional-period) bis **31. Mai 2028**. Diese Bestimmungen stehen nur Kunden von Adobe Commerce zur Verfügung. Sie erweitern die Unterstützung für Drittanbieterabhängigkeiten wie MySQL nicht.
>
>Wenn Sie Adobe Commerce auf Cloud Manager ausführen, müssen Sie vor dem 1. **2028 (Sicherheitsanforderungen und -fristen** ein Upgrade auf eine unterstützte Version durchführen [&#x200B; zu [!DNL Adobe Commerce as a Cloud Service] &#x200B;](../release/security-enforcement-policy.md). Vollständige Lebenszyklusdaten finden Sie in [&#x200B; Tabelle &#x200B;](../release/lifecycle-policy.md#end-of-support-dates)Ende der Support-Daten“.
>
>Die Tabelle wird reduziert, um die Länge dieses Artikels zu minimieren. Wählen Sie die Kopfzeile aus, um sie zu erweitern.

+++Anforderungen für frühere Versionen

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die [Commerce on Cloud-Vorlage](https://github.com/magento/magento-cloud) stellt eine Standardkonfiguration für Services bereit, die mit einer bestimmten Commerce-Version kompatibel sind.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Die [`services.yaml`-Datei &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) die Standard-Services und -Versionen.
Siehe [Konfigurieren von Services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) im *Handbuch zu Commerce* Cloud-Infrastruktur.

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 hat am 30. April 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.7, 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität und keine Unterstützung für MySQL-Versionen, die nach MySQL 8.0 veröffentlicht wurden.
Adobe validiert oder unterstützt keine neueren MySQL-Hauptversionen für diese Commerce-Versionen.
Wenn Sie die Adobe Commerce On-Premises-Versionen 2.4.7, 2.4.6, 2.4.5 oder 2.4.4 ausführen, empfiehlt Adobe dringend, Ihre Datenbankserver auf eine kompatible MariaDB-Version zu migrieren.

Adobe Commerce on Cloud-Kunden müssen Plattformabhängigkeiten für unterstützte Versionen beibehalten. Siehe [Platform-Abhängigkeiten](../release/lifecycle-policy.md#platform-dependencies) in der Lebenszyklusrichtlinie.

**Elasticsearch 7.17 hat am 15. Januar 2026 das Ende der Unterstützung (End of Support, EOS) erreicht.**
Nach diesem Datum bieten Adobe Commerce 2.4.6, 2.4.5 und 2.4.4 keine Kompatibilität mehr und keine Unterstützung für Elasticsearch-Versionen, die nach Elasticsearch 7 veröffentlicht wurden.
Adobe validiert oder unterstützt keine neueren Elasticsearch-Hauptversionen für diese Commerce-Versionen.
Wenn Sie die lokalen Adobe Commerce-Versionen 2.4.6, 2.4.5 oder 2.4.4 ausführen, empfiehlt Adobe dringend, Ihre Suchinfrastruktur auf eine kompatible OpenSearch-Version zu migrieren.

>[!ENDTABS]

+++

## PHP-Einstellungen

Konfigurieren Sie PHP-Einstellungen wie `memory_limit`, um häufige Probleme bei der Verwendung von Adobe Commerce zu vermeiden. Siehe [Erforderliche PHP-](prerequisites/php-settings.md).

Eine Anleitung zur Cloud-Konfiguration finden Sie unter [PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) im *Handbuch zu Commerce* Cloud-Infrastruktur.

### PHP-OP-Cache

Adobe empfiehlt zu überprüfen, ob [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) aktiviert ist, um die Leistung zu verbessern. Viele PHP-Distributionen ermöglichen OPcache.

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
>Informationen zu PHP-Erweiterungen in der Cloud-Infrastruktur finden Sie unter [Aktivieren von PHP-Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) im _Handbuch zu Commerce in_.

>[!BEGINTABS]

>[!TAB Commerce in der Cloud]

Die folgende Tabelle zeigt die unterstützten PHP-Erweiterungen bei der Bereitstellung von Adobe Commerce auf der Cloud-Plattform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce On-Premises]

{{$include /help/_includes/templated/php-extensions.md}}

Siehe die [offizielle PHP-Dokumentation](https://www.php.net/manual/en/extensions.php) für Installationsdetails.

>[!ENDTABS]

## Sonstige Softwareanforderungen

In diesem Abschnitt werden die Unterstützung und Kompatibilität für alle anderen erforderlichen und optionalen Softwaretypen beschrieben.

>[!NOTE]
>
>Die folgenden Anforderungen gelten für die neueste Patch-Version 2.4.x von Adobe Commerce. Gegebenenfalls wird eine Anleitung zur Commerce-Cloud-Infrastruktur bereitgestellt.

### Browser

Adobe Commerce unterstützt die neuesten und vorherigen Hauptversionen der folgenden Browser für die Storefront und Admin, sofern nicht anders angegeben:

- Microsoft Edge
- Firefox (beliebiges Betriebssystem)
- Chrome (beliebiges Betriebssystem)
- Safari (nur macOS)
- Safari für iOS (nur Storefront)
- Chrome für Android (nur Storefront)

### Mail-Server

Mail Transfer Agent (MTA) oder SMTP-Server. Commerce in der Cloud-Infrastruktur verwendet den [SendGrid-E-Mail-Service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Arbeitsspeicher

Das Upgrade von Anwendungen und Erweiterungen aus Commerce Marketplace und anderen Quellen kann bis zu 2 GB RAM erfordern. Wenn Ihr System weniger als 2 GB RAM hat, erstellen Sie eine [Auslagerungsdatei](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Ohne eine Auslagerungsdatei schlägt das Upgrade möglicherweise fehl.

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

Informationen zu Commerce in Cloud-Infrastrukturen finden Sie unter [Fastly-](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)) im Handbuch *Commerce in Cloud-*.

### xdebug

Verwenden Sie nur für Adobe Commerce-Entwicklungsumgebungen [php_xdebug 2.5.x](https://xdebug.org/download) oder höher. Xdebug kann die Leistung beeinträchtigen.

Informationen zu Adobe Commerce on Cloud finden Sie [Konfigurieren von Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) im Handbuch *Commerce on Cloud Infrastructure*.

>[!NOTE]
>
>Ein bekanntes Problem mit Xdebug kann Adobe Commerce-Installationen oder den Zugriff auf die Storefront oder den Admin nach der Installation beeinträchtigen. Siehe [Bekanntes Problem, das `xdebug` Installation betrifft](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) in der _Commerce Support Knowledge Base_.

<!-- Last updated from includes: 2026-10-13 09:11:06 -->
