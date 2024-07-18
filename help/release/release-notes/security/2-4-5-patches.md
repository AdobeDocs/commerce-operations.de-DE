---
title: Versionshinweise zu Adobe Commerce 2.4.5 Sicherheits-Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.5 enthalten sind.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 2269c99908c0f8292ad62bd5837b1b8cebd50cb3
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.5-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

Die Adobe Commerce-Sicherheitsversion 2.4.5-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Plattformaktualisierungen

* **Unterstützung für MariaDB 10.5**. Diese Patch-Version führt die Kompatibilität mit MariaDB Version 10.5 ein. Adobe Commerce ist weiterhin mit der MariaDB-Version 10.4 kompatibel. Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.5-p8 und alle kommenden Sicherheits-Patch-Versionen 2.4.5 nur mit der MariaDB-Version 10.5, da die MariaDB 10.4-Wartung am 18. Juni 2024 endet. <!--AC-11530-->

### Zusätzliche Sicherheitsverbesserungen

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

Die Adobe Commerce-Sicherheitsversion 2.4.5-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

Die Adobe Commerce-Sicherheitsversion 2.4.5-p6 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Sicherheitshinweise

Mit dieser Version werden zwei wesentliche Sicherheitsverbesserungen eingeführt:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für Bausteine enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Syntax der Vorlagenanweisung oder die Methoden `setCacheKey` oder `setData` festgelegt werden.)
   * Nicht generierte Cache-Schlüssel für Blöcke dürfen jetzt nur Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Beschränkungen der Anzahl der automatisch generierten Couponcodes**. Commerce beschränkt jetzt die Anzahl der automatisch generierten Couponcodes. Der Standardwert ist maximal 250.000. Händler können die neue Konfigurationsoption **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) verwenden, um diese neue Begrenzung zu steuern. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Die Sicherheitsversion Adobe Commerce 2.4.5-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Sicherheitshinweis

Mit dieser Version wird eine neue Einstellung für die vollständige Seiten-Cache-Konfiguration eingeführt, die dazu beiträgt, die Risiken im Zusammenhang mit dem `{BASE-URL}/page_cache/block/esi HTTP` -Endpunkt zu verringern. Dieser Endpunkt unterstützt nicht eingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue Konfigurationseinstellung **[!UICONTROL Handles Param]** legt den Wert des Parameters `handles` dieses Endpunkts fest, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert über Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**) ändern. <!-- AC-9113 -->

### Bekanntes Problem

**Problem**: Adobe Commerce zeigt einen **falschen Prüfsummenfehler** beim Herunterladen durch den Composer von `repo.magento.com` an und der Paketdownload wird unterbrochen. Dieses Problem kann beim Herunterladen von Release-Paketen auftreten, die während der Vorabversion bereitgestellt wurden und durch eine Neuverpackung des `magento/module-page-cache` -Pakets verursacht werden.

**Problemumgehung**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie das Verzeichnis &quot;`/vendor`&quot; im Projekt, sofern vorhanden.
2) Führen Sie den Befehl `bin/magento composer update magento/module-page-cache` aus. Dieser Befehl aktualisiert nur das `page cache` -Paket.

Wenn das Prüfsummenproblem fortbesteht, entfernen Sie die Datei &quot;`composer.lock`&quot;, bevor Sie den Befehl &quot;`bin/magento composer update`&quot;erneut ausführen, um jedes Paket zu aktualisieren.

## Adobe Commerce 2.4.5-p4

Die Sicherheitsversion Adobe Commerce 2.4.5-p4 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Wenden Sie einen Patch an, um die Sicherheitslücke CVE-2022-31160 in der jQuery-UI-Bibliothek zu beheben.

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Knowledge Base-Artikel 2.4.4, 2.4.5 und 2.4.6 zur Sicherheitslücke CVE-2022-31160 in der jQuery-Benutzeroberfläche angegeben ist.[](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)

## Adobe Commerce 2.4.5-p3

Die Sicherheitsversion Adobe Commerce 2.4.5-p3 enthält Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Wenden Sie einen Patch an, um die Sicherheitslücke CVE-2022-31160 in der jQuery-UI-Bibliothek zu beheben.

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Knowledge Base-Artikel 2.4.4, 2.4.5 und 2.4.6 der Sicherheitslücke CVE-2022-31160 im Abschnitt zur Fehlerbehebung der Query UI angegeben ist.[](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)

### Sicherheitshinweis

Das Standardverhalten der GraphQL-Abfragen [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) und des REST-Endpunkts ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) wurde geändert. Standardmäßig gibt die API jetzt immer `true` zurück. Händler können das ursprüngliche Verhalten aktivieren, d. h. `true` zurückgeben, wenn die E-Mail nicht in der Datenbank vorhanden ist, und `false`, wenn sie existiert. <!-- AC-6695 -->

### Plattformaktualisierungen

Plattformaktualisierungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung des Unterschiedlichen Cache 7.3**. Diese Version ist mit der neuesten Version von Varnish Cache 7.3 kompatibel. Die Kompatibilität mit den Versionen 6.0.x und 7.2.x bleibt erhalten. Wir empfehlen jedoch die Verwendung von Adobe Commerce 2.4.5-p3 nur mit Version 7.3 (Varnish Cache) oder Version 6.0 LTS (LTS).

* **RabbitMQ 3.11-Unterstützung**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt erhalten, was bis August 2023 unterstützt wird. Es wird jedoch empfohlen, Adobe Commerce 2.4.5-p3 nur mit RabbitMQ 3.11 zu verwenden.

* **JavaScript-Bibliotheken**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten kleineren oder Patch-Versionen aktualisiert, einschließlich der `moment.js` -Bibliothek (v2.29.4), der `jQuery UI` -Bibliothek (v1.13.2) und der `jQuery` -Validierungs-Plug-in-Bibliothek (v1.19.5).

## Versionshinweise zu Adobe Commerce 2.4.5-p2

Die Sicherheitsversion Adobe Commerce 2.4.5-p2 enthält drei Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

Die Adobe Commerce-Sicherheitsversion 2.4.5-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in der vorherigen Version (Adobe Commerce 2.4.5 und Magento Open Source 2.4.5) identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Eine der Sicherheitsfehlerbehebungen umfasste die Erstellung einer neuen Konfigurationseinstellung. Mit der Konfigurationseinstellung **E-Mail-Bestätigung erforderlich , wenn E-Mail geändert wurde** können Administratoren eine E-Mail-Bestätigung benötigen, wenn ein Administrator seine E-Mail-Adresse ändert. <!-- AC-6292-->
