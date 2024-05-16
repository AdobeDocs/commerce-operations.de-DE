---
title: Versionshinweise zu Adobe Commerce 2.4.5 Sicherheits-Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.5 enthalten sind.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.5-Sicherheitspatches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p7

Die Adobe Commerce-Sicherheitsversion 2.4.5-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

Die Adobe Commerce-Sicherheitsversion 2.4.5-p6 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe Security Bulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Sicherheitshinweise

Mit dieser Version werden zwei wesentliche Sicherheitsverbesserungen eingeführt:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für Bausteine enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Syntax der Vorlagenanweisung oder die `setCacheKey` oder `setData` Methoden.)
   * Nicht generierte Cache-Schlüssel für Blöcke dürfen jetzt nur Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten.  <!-- AC-9831 -->

* **Einschränkungen bei der Anzahl der automatisch generierten Gutscheincodes**. Commerce beschränkt jetzt die Anzahl der automatisch generierten Couponcodes. Der Standardwert ist maximal 250.000. Händler können die neue **[!UICONTROL Code Quantity Limit]** Konfigurationsoption (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**), um diese neue Grenze zu steuern. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Die Sicherheitsversion Adobe Commerce 2.4.5-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Sicherheitshinweis

Mit dieser Version wird eine neue Einstellung für die vollständige Seiten-Cache-Konfiguration eingeführt, die dazu beiträgt, die mit dem `{BASE-URL}/page_cache/block/esi HTTP` -Endpunkt. Dieser Endpunkt unterstützt nicht eingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue **[!UICONTROL Handles Param]** -Konfigurationseinstellung legt den Wert des `handles` -Parameter, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert über Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Bekanntes Problem

**Problem**: Adobe Commerce zeigt eine **falsche Prüfsumme** Fehler beim Herunterladen durch Composer von `repo.magento.com`, und der Paketdownload wird unterbrochen. Dieses Problem kann beim Herunterladen von Release-Paketen auftreten, die während der Vorabversion bereitgestellt wurden und durch eine Neuverpackung der `magento/module-page-cache` Paket.

**Workaround**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie die `/vendor` -Verzeichnis innerhalb des Projekts, sofern vorhanden.
2) Führen Sie die `bin/magento composer update magento/module-page-cache` Befehl. Dieser Befehl aktualisiert nur die `page cache` Paket.

Wenn das Prüfsummenproblem fortbesteht, entfernen Sie die `composer.lock` Datei vor der erneuten Ausführung der `bin/magento composer update` -Befehl, um jedes Paket zu aktualisieren.

## Adobe Commerce 2.4.5-p4

Die Sicherheitsversion Adobe Commerce 2.4.5-p4 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Wenden Sie einen Patch an, um die Sicherheitslücke CVE-2022-31160 in der jQuery-UI-Bibliothek zu beheben.

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den im Abschnitt [Sicherheitslücke der jQuery-Benutzeroberfläche CVE-2022-31160-Fehlerbehebung für Versionen 2.4.4, 2.4.5 und 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Knowledge Base-Artikel.

## Adobe Commerce 2.4.5-p3

Die Sicherheitsversion Adobe Commerce 2.4.5-p3 enthält Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Wenden Sie einen Patch an, um die Sicherheitslücke CVE-2022-31160 in der jQuery-UI-Bibliothek zu beheben.

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den im Abschnitt [Sicherheitslücke in der Query UI CVE-2022-31160-Fehlerbehebung für Versionen 2.4.4, 2.4.5 und 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Knowledge Base-Artikel.

### Sicherheitshinweis

Das Standardverhalten der [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-Abfrage und ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Der REST-Endpunkt wurde geändert. Standardmäßig gibt die API jetzt immer `true`. Händler können das ursprüngliche Verhalten aktivieren, d. h. die Rückgabe `true` wenn die E-Mail nicht in der Datenbank vorhanden ist und `false` , wenn sie vorhanden ist. <!-- AC-6695 -->

### Plattformaktualisierungen

Plattformaktualisierungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung von Varnish Cache 7.3**. Diese Version ist mit der neuesten Version von Varnish Cache 7.3 kompatibel. Die Kompatibilität mit den Versionen 6.0.x und 7.2.x bleibt erhalten. Wir empfehlen jedoch die Verwendung von Adobe Commerce 2.4.5-p3 nur mit Version 7.3 (Varnish Cache) oder Version 6.0 LTS (LTS).

* **RabbitMQ 3.11-Unterstützung**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt erhalten, was bis August 2023 unterstützt wird. Es wird jedoch empfohlen, Adobe Commerce 2.4.5-p3 nur mit RabbitMQ 3.11 zu verwenden.

* **JavaScript-Bibliotheken**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten kleineren oder Patch-Versionen aktualisiert, einschließlich `moment.js` Bibliothek (v2.29.4), `jQuery UI` Bibliothek (v1.13.2) und `jQuery` Validierungs-Plug-in-Bibliothek (v1.19.5).

## Versionshinweise zu Adobe Commerce 2.4.5-p2

Die Sicherheitsversion Adobe Commerce 2.4.5-p2 enthält drei Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

Die Adobe Commerce-Sicherheitsversion 2.4.5-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in der vorherigen Version (Adobe Commerce 2.4.5 und Magento Open Source 2.4.5) identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Eine der Sicherheitsfehlerbehebungen umfasste die Erstellung einer neuen Konfigurationseinstellung. Die **E-Mail-Bestätigung erforderlich, wenn E-Mail geändert wurde** -Konfigurationseinstellungen ermöglichen es Administratoren, eine E-Mail-Bestätigung zu verlangen, wenn ein Administrator seine E-Mail-Adresse ändert. <!-- AC-6292-->


