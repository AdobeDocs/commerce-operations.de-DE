---
title: Versionshinweise zu Adobe Commerce 2.4.4 Security Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.4 enthalten sind.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 3a2d104f0a689ac3715af302d470a1660857543c
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.4-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4-p10

Die Adobe Commerce-Sicherheitsversion 2.4.4-p10 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/2024-08/security.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.4-p9

Die Sicherheitsversion Adobe Commerce 2.4.4-p9 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Plattformaktualisierungen

* **Unterstützung für MariaDB 10.5**. Diese Patch-Version führt die Kompatibilität mit MariaDB Version 10.5 ein. Adobe Commerce ist weiterhin mit der MariaDB-Version 10.4 kompatibel, Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p9 und alle kommenden Sicherheits-Patch-Versionen 2.4.4 nur mit der MariaDB-Version 10.5, da die Wartung von MariaDB 10.4 am 18. Juni 2024 endet. <!--AC-11530-->

### Highlights

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.4-p8

Die Sicherheitsversion Adobe Commerce 2.4.4-p8 enthält Sicherheitsfehlerbehebungen für Ihre Adobe Commerce 2.4.4-Bereitstellung. Diese Updates beheben Schwachstellen, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Die Adobe Commerce-Sicherheitsversion 2.4.4-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Highlights

Mit dieser Version werden zwei wesentliche Sicherheitsverbesserungen eingeführt:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für Bausteine enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Syntax der Vorlagenanweisung oder die Methoden `setCacheKey` oder `setData` festgelegt werden.)
   * Nicht generierte Cache-Schlüssel für Blöcke dürfen jetzt nur Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Beschränkungen der Anzahl der automatisch generierten Couponcodes**. Commerce beschränkt jetzt die Anzahl der automatisch generierten Couponcodes. Der Standardwert ist maximal 250.000. Händler können die neue Konfigurationsoption **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) verwenden, um diese neue Begrenzung zu steuern. <!-- AC-8753 -->

## 2.4.4-p6

Die Sicherheitsversion Adobe Commerce 2.4.4-p6 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

### Highlights

Mit dieser Version wird eine neue Einstellung für die vollständige Seiten-Cache-Konfiguration eingeführt, die dazu beiträgt, die Risiken im Zusammenhang mit dem `{BASE-URL}/page_cache/block/esi HTTP` -Endpunkt zu verringern. Dieser Endpunkt unterstützt nicht eingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue Konfigurationseinstellung **[!UICONTROL Handles Param]** legt den Wert des Parameters `handles` dieses Endpunkts fest, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert über Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**) ändern. <!-- AC-9113 -->

### Bekannte Probleme

**Problem**: Adobe Commerce zeigt einen **falschen Prüfsummenfehler** beim Herunterladen durch den Composer von `repo.magento.com` an und der Paketdownload wird unterbrochen. Dieses Problem kann beim Herunterladen von Release-Paketen auftreten, die während der Vorabversion bereitgestellt wurden und durch eine Neuverpackung des `magento/module-page-cache` -Pakets verursacht werden.

**Problemumgehung**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie das Verzeichnis &quot;`/vendor`&quot; im Projekt, sofern vorhanden.
2) Führen Sie den Befehl `bin/magento composer update magento/module-page-cache` aus. Dieser Befehl aktualisiert nur das `page cache` -Paket.

Wenn das Prüfsummenproblem fortbesteht, entfernen Sie die Datei &quot;`composer.lock`&quot;, bevor Sie den Befehl &quot;`bin/magento composer update`&quot;erneut ausführen, um jedes Paket zu aktualisieren.

## 2.4.4-p5

Die Sicherheitsversion Adobe Commerce 2.4.4-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Knowledge Base-Artikel 2.4.4, 2.4.5 und 2.4.6 zur Sicherheitslücke CVE-2022-31160 in der jQuery-Benutzeroberfläche angegeben ist.[](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)

## 2.4.4-p4

Die Sicherheitsversion Adobe Commerce 2.4.4-p4 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version umfasst auch Sicherheitsverbesserungen und Plattformaktualisierungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Knowledge Base-Artikel 2.4.4, 2.4.5 und 2.4.6 zur Sicherheitslücke CVE-2022-31160 in der jQuery-Benutzeroberfläche angegeben ist.[](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)

### Highlights

Das Standardverhalten der GraphQL-Abfragen [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) und des REST-Endpunkts ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) wurde geändert. Standardmäßig gibt die API jetzt immer `true` zurück. Händler können das ursprüngliche Verhalten aktivieren, d. h. `true` zurückgeben, wenn die E-Mail nicht in der Datenbank vorhanden ist, und `false`, wenn sie existiert. <!-- AC-6695 -->

### Plattformaktualisierungen

Plattformaktualisierungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung des Unterschiedlichen Cache 7.3**. Diese Version ist mit der neuesten Version von Varnish Cache 7.3 kompatibel. Die Kompatibilität bleibt mit den Versionen 6.0.x und 7u.2.x bestehen, Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p4 nur mit Varnish Cache Version 7.3 oder Version 6.0 LTS.

* **RabbitMQ 3.11-Unterstützung**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt erhalten, was bis August 2023 unterstützt wird. Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p4 nur mit RabbitMQ 3.11.

* **JavaScript-Bibliotheken**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten kleineren oder Patch-Versionen aktualisiert, einschließlich der `moment.js` -Bibliothek (v2.29.4), der `jQuery UI` -Bibliothek (v1.13.2) und der `jQuery` -Validierungs-Plug-in-Bibliothek (v1.19.5).

## 2.4.4-p3

Die Sicherheitsversion Adobe Commerce 2.4.4-p3 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

Die Sicherheitsversion Adobe Commerce 2.4.4-p2 enthält Fehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Eine Korrektur umfasst die Erstellung einer neuen Konfigurationseinstellung. Mit der Konfigurationseinstellung **E-Mail-Bestätigung erforderlich , wenn E-Mail geändert wurde** können Administratoren eine E-Mail-Bestätigung benötigen, wenn ein Administrator seine E-Mail-Adresse ändert. <!-- AC-6292-->

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Wenden Sie AC-3022.patch an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten so schnell wie möglich `AC-3022.patch` anwenden, um DHL weiterhin als Versandunternehmen anzubieten. Informationen zum Herunterladen und Installieren des Patches finden Sie im Artikel [Anwenden eines Patches, um DHL weiterhin als Versandunternehmen anzubieten](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Knowledge Base .

## 2.4.4-p1

Die Sicherheitsversion Adobe Commerce 2.4.4-p1 enthält Fehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Wenden Sie `AC-3022.patch` an, um DHL weiterhin als Versandunternehmen anzubieten.

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten so schnell wie möglich `AC-3022.patch` anwenden, um DHL weiterhin als Versandunternehmen anzubieten. Informationen zum Herunterladen und Installieren des Patches finden Sie im Artikel [Anwenden eines Patches, um DHL weiterhin als Versandunternehmen anzubieten](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Knowledge Base .

### Highlights

Sicherheitsverbesserungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit, einschließlich:

* ACL-Ressourcen wurden zum Inventar hinzugefügt.
* Die Sicherheit der Lagerbestandsvorlage wurde verbessert.

### Bekannte Probleme

**Problem**: Web-API- und Integrationstests zeigen diesen Fehler an, wenn sie mit dem Paket 2.4.4-p1 ausgeführt werden: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Problemumgehung**: Installieren Sie die vorherige Version von Monolog, indem Sie den Befehl `require monolog/monolog:2.6.0` ausführen. <!-- AC-3651-->

**Problem**: Bei einem Upgrade von Adobe Commerce 2.4.4 auf Adobe Commerce 2.4.4-p1 werden möglicherweise Hinweise zum Upgrade der Paketversion angezeigt. Diese Nachrichten können ignoriert werden. Die Diskrepanz in Paketversionen resultiert aus Anomalien bei der Package-Erstellung. Die Produktfunktionalität wurde nicht beeinflusst. Im Knowledge Base-Artikel [Pakete, die nach dem Upgrade von 2.4.4 auf 2.4.4-p1 herabgestuft wurden, finden Sie eine Diskussion der betroffenen Szenarien und Problemumgehungen.](https://support.magento.com/hc/en-us/articles/8214752983949)
