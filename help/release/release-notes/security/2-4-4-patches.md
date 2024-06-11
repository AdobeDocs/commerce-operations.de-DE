---
title: Versionshinweise für Adobe Commerce 2.4.4-Sicherheitspatches
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.4 enthalten sind.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.4-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.4-p9

Die Sicherheitsversion Adobe Commerce 2.4.4-p9 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Plattformaktualisierungen

* **MariaDB 10.5-Unterstützung**. Diese Patch-Version führt die Kompatibilität mit MariaDB Version 10.5 ein. Adobe Commerce ist weiterhin mit der MariaDB-Version 10.4 kompatibel, Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p9 und allen kommenden Sicherheits-Patch-Versionen 2.4.4 nur mit der MariaDB-Version 10.5, da die MariaDB 10.4-Wartung am 18. Juni 2024 endet. <!--AC-11530-->

## 2.4.4-p8

Die Sicherheitsversion Adobe Commerce 2.4.4-p8 enthält Sicherheitsfehlerbehebungen für Ihre Adobe Commerce 2.4.4-Bereitstellung. Diese Updates beheben Schwachstellen, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Die Adobe Commerce-Sicherheitsversion 2.4.4-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe Security Bulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Sicherheitshinweise

Mit dieser Version werden zwei wesentliche Sicherheitsverbesserungen eingeführt:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für Bausteine enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Syntax der Vorlagenanweisung oder die `setCacheKey` oder `setData` Methoden.)
   * Nicht generierte Cache-Schlüssel für Blöcke dürfen jetzt nur Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Einschränkungen bei der Anzahl der automatisch generierten Gutscheincodes**. Commerce beschränkt jetzt die Anzahl der automatisch generierten Couponcodes. Der Standardwert ist maximal 250.000. Händler können die neue **[!UICONTROL Code Quantity Limit]** Konfigurationsoption (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**), um diese neue Grenze zu steuern. <!-- AC-8753 -->

## 2.4.4-p6

Die Sicherheitsversion Adobe Commerce 2.4.4-p6 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

### Sicherheitshinweis

Mit dieser Version wird eine neue Einstellung für die vollständige Seiten-Cache-Konfiguration eingeführt, die dazu beiträgt, die mit dem `{BASE-URL}/page_cache/block/esi HTTP` -Endpunkt. Dieser Endpunkt unterstützt nicht eingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue **[!UICONTROL Handles Param]** -Konfigurationseinstellung legt den Wert des `handles` -Parameter, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert über Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Bekanntes Problem

**Problem**: Adobe Commerce zeigt eine **falsche Prüfsumme** Fehler beim Herunterladen durch Composer von `repo.magento.com`, und der Paketdownload wird unterbrochen. Dieses Problem kann beim Herunterladen von Release-Paketen auftreten, die während der Vorabversion bereitgestellt wurden und durch eine Neuverpackung der `magento/module-page-cache` Paket.

**Workaround**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie die `/vendor` -Verzeichnis innerhalb des Projekts, sofern vorhanden.
2) Führen Sie die `bin/magento composer update magento/module-page-cache` Befehl. Dieser Befehl aktualisiert nur die `page cache` Paket.

Wenn das Prüfsummenproblem fortbesteht, entfernen Sie die `composer.lock` Datei vor der erneuten Ausführung der `bin/magento composer update` -Befehl, um jedes Paket zu aktualisieren.

## 2.4.4-p5

Die Sicherheitsversion Adobe Commerce 2.4.4-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Wenden Sie einen Patch an, um die Sicherheitslücke CVE-2022-31160 in der jQuery-UI-Bibliothek zu beheben.

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den im Abschnitt [Sicherheitslücke der jQuery-Benutzeroberfläche CVE-2022-31160-Fehlerbehebung für Versionen 2.4.4, 2.4.5 und 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Knowledge Base-Artikel.

## 2.4.4-p4

Die Sicherheitsversion Adobe Commerce 2.4.4-p4 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version umfasst auch Sicherheitsverbesserungen und Plattformaktualisierungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Wenden Sie einen Patch an, um die Sicherheitslücke CVE-2022-31160 in der jQuery-UI-Bibliothek zu beheben.

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den im Abschnitt [Sicherheitslücke der jQuery-Benutzeroberfläche CVE-2022-31160-Fehlerbehebung für Versionen 2.4.4, 2.4.5 und 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Knowledge Base-Artikel.

### Sicherheitshinweis

Das Standardverhalten der [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-Abfrage und ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Der REST-Endpunkt wurde geändert. Standardmäßig gibt die API jetzt immer `true`. Händler können das ursprüngliche Verhalten aktivieren, d. h. die Rückgabe `true` wenn die E-Mail nicht in der Datenbank vorhanden ist und `false` , wenn sie vorhanden ist. <!-- AC-6695 -->

### Plattformaktualisierungen

Plattformaktualisierungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung von Varnish Cache 7.3**. Diese Version ist mit der neuesten Version von Varnish Cache 7.3 kompatibel. Die Kompatibilität bleibt mit den Versionen 6.0.x und 7u.2.x bestehen, Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p4 nur mit Varnish Cache Version 7.3 oder Version 6.0 LTS.

* **RabbitMQ 3.11-Unterstützung**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt erhalten, was bis August 2023 unterstützt wird. Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p4 nur mit RabbitMQ 3.11.

* **JavaScript-Bibliotheken**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten kleineren oder Patch-Versionen aktualisiert, einschließlich `moment.js` Bibliothek (v2.29.4), `jQuery UI` Bibliothek (v1.13.2) und `jQuery` Validierungs-Plug-in-Bibliothek (v1.19.5).

## 2.4.4-p3

Die Sicherheitsversion Adobe Commerce 2.4.4-p3 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

Die Sicherheitsversion Adobe Commerce 2.4.4-p2 enthält Fehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Eine Korrektur umfasst die Erstellung einer neuen Konfigurationseinstellung. Die **E-Mail-Bestätigung erforderlich, wenn E-Mail geändert wurde** -Konfigurationseinstellungen ermöglichen es Administratoren, eine E-Mail-Bestätigung zu verlangen, wenn ein Administrator seine E-Mail-Adresse ändert. <!-- AC-6292-->

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Wenden Sie AC-3022.patch an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Merchants, die diese Versionen bereitstellen, sollten gelten `AC-3022.patch` so schnell wie möglich DHL als Reederei anbieten. Siehe [Wenden Sie einen Patch an, um DHL weiterhin als Versandunternehmen anzubieten.](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Knowledge Base-Artikel für Informationen zum Herunterladen und Installieren des Patches.

## 2.4.4-p1

Die Sicherheitsversion Adobe Commerce 2.4.4-p1 enthält Fehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Anwenden `AC-3022.patch` weiterhin DHL als Reederei anbieten

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Merchants, die diese Versionen bereitstellen, sollten gelten `AC-3022.patch` so schnell wie möglich DHL als Reederei anbieten. Siehe [Wenden Sie einen Patch an, um DHL weiterhin als Versandunternehmen anzubieten.](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Knowledge Base-Artikel für Informationen zum Herunterladen und Installieren des Patches.

### Sicherheitshinweise

Sicherheitsverbesserungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit, einschließlich:

* ACL-Ressourcen wurden zum Inventar hinzugefügt.
* Die Sicherheit der Lagerbestandsvorlage wurde verbessert.

### Bekannte Probleme

**Problem**: Web-API- und Integrationstests zeigen diesen Fehler an, wenn sie mit dem Paket 2.4.4-p1 ausgeführt werden: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Workaround**: Installieren Sie die vorherige Version von Monolog, indem Sie die `require monolog/monolog:2.6.0` Befehl. <!-- AC-3651-->

**Problem**: Bei einem Upgrade von Adobe Commerce 2.4.4 auf Adobe Commerce 2.4.4-p1 werden möglicherweise Hinweise zum Upgrade von Paketversionen angezeigt. Diese Nachrichten können ignoriert werden. Die Diskrepanz in Paketversionen resultiert aus Anomalien bei der Package-Erstellung. Die Produktfunktionalität wurde nicht beeinflusst. Siehe [Pakete wurden nach der Aktualisierung von 2.4.4 auf 2.4.4-p1 heruntergestuft](https://support.magento.com/hc/en-us/articles/8214752983949) Knowledgebase-Artikel für eine Diskussion der betroffenen Szenarien und Problemumgehungen.
