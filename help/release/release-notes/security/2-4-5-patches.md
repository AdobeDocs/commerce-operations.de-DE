---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.5
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.5-Sicherheits-Patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-P15

Die Adobe Commerce-Sicherheitsversion 2.4.5-p15 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>Erweiterte Support-Sicherheits-Patches für 2.4.5 sind nur für Adobe Commerce-Kunden verfügbar. Diese Patches sind für die Magento Open Source-Code-Basis nicht verfügbar. Siehe [Erweiterte Unterstützung](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).


## 2.4.5-P14

Die Adobe Commerce-Sicherheitsversion 2.4.5-p14 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.5-P13

Die Adobe Commerce-Sicherheitsversion 2.4.5-p13 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **API-Leistungsverbesserung**: Behebt die Leistungsbeeinträchtigung bei asynchronen Web-API-Endpunkten, die nach dem vorherigen Sicherheits-Patch eingeführt wurden.<!-- AC-14078 -->

* **CMS blockiert den Zugriff** - Löst ein Problem, bei dem Admin-Benutzer mit eingeschränkten Berechtigungen (z. B. Nur-Merchandising-Zugriff) die [!UICONTROL CMS Blocks] nicht anzeigen konnten.

  Zuvor trat bei diesen Benutzern ein Fehler aufgrund fehlender Konfigurationsparameter nach der Installation früherer Sicherheits-Patches auf.<!-- AC-14087 -->

* **Cookie-Kompatibilität** - Löst eine abwärtsinkompatible Änderung auf, die die `MAX_NUM_COOKIES` im Framework betrifft. Diese Aktualisierung stellt das erwartete Verhalten wieder her und stellt die Kompatibilität für Erweiterungen oder Anpassungen sicher, die mit Cookie-Beschränkungen interagieren.<!-- AC-14475 -->

* **Async-Vorgänge** - Eingeschränkte asynchrone Vorgänge zum Überschreiben früherer Kundenbestellungen.<!-- AC-13917 -->

## 2.4.5-P12

Die Adobe Commerce-Sicherheitsversion 2.4.5-p12 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.5-P11

Die Adobe Commerce-Sicherheitsversion 2.4.5-p11 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-P10

Die Adobe Commerce-Sicherheitsversion 2.4.5-p10 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.5-p9

Die Adobe Commerce-Sicherheitsversion 2.4.5-p9 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5-p8

Die Adobe Commerce-Sicherheitsversion 2.4.5-p8 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Plattform-Upgrades

* **MariaDB 10.5-Unterstützung**. Diese Patch-Version führt die Kompatibilität mit MariaDB Version 10.5 ein. Adobe Commerce ist weiterhin mit MariaDB Version 10.4 kompatibel. Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.5-p8 und allen kommenden Nur-Sicherheits-Patch-Versionen 2.4.5 nur mit MariaDB Version 10.5, da die Wartung von MariaDB 10.4 am 18. Juni 2024 endet. <!--AC-11530-->

### Highlights

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5-p7

Die Adobe Commerce-Sicherheitsversion 2.4.5-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.5-p6

Die Adobe Commerce-Sicherheitsversion 2.4.5-p6 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Highlights

Diese Version führt zwei wichtige Sicherheitsverbesserungen ein:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für -Blöcke enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Vorlagenanweisungssyntax oder die `setCacheKey`- oder `setData` festgelegt werden.)
   * Nicht generierte Cache-Schlüssel für -Blöcke dürfen jetzt nur noch Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Beschränkungen für die Anzahl der automatisch generierten Couponcodes**. Commerce begrenzt jetzt die Anzahl der Gutscheincodes, die automatisch generiert werden. Der standardmäßige Maximalwert ist 250.000. Händler können die neue **[!UICONTROL Code Quantity Limit]**-Konfigurationsoption (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) verwenden, um dieses neue Limit zu steuern. <!-- AC-8753 -->

## 2.4.5-p5

Die Adobe Commerce-Sicherheitsversion 2.4.5-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Highlights

Diese Version führt eine neue Konfigurationseinstellung für den vollständigen Seiten-Cache ein, die dazu beiträgt, die mit dem `{BASE-URL}/page_cache/block/esi HTTP`-Endpunkt verbundenen Risiken zu minimieren. Dieser Endpunkt unterstützt uneingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue **[!UICONTROL Handles Param]**-Konfigurationseinstellung legt den Wert des `handles`-Parameters dieses Endpunkts fest, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert unter Admin ändern (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Bekannte Probleme

**Problem**: Adobe Commerce zeigt beim Herunterladen durch Composer aus **den Fehler** falsche `repo.magento.com`) an und der Paket-Download wird unterbrochen. Dieses Problem kann beim Herunterladen von Veröffentlichungspaketen auftreten, die während der Vorabversion verfügbar gemacht wurden, und wird durch eine Neuverpackung des `magento/module-page-cache`-Pakets verursacht.

**Problemumgehung**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie das `/vendor` Verzeichnis innerhalb des Projekts, falls vorhanden.
2) Führen Sie den `bin/magento composer update magento/module-page-cache` Befehl aus. Dieser Befehl aktualisiert nur das `page cache`.

Wenn das Prüfsummenproblem weiterhin besteht, entfernen Sie die `composer.lock`-Datei, bevor Sie den `bin/magento composer update`-Befehl erneut ausführen, um jedes Paket zu aktualisieren.

## 2.4.5-p4

Die Adobe Commerce-Sicherheitsversion 2.4.5-p4 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Händler, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Artikel [jQuery UI Security Vulnerability CVE-2022-31160 Fix for 2.4.4, 2.4.5 und 2.4.6 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6).

## 2.4.5-p3

Die Adobe Commerce-Version 2.4.5-p3 bietet Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Händler, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Artikel [Sicherheitslücke der Abfrage-Benutzeroberfläche CVE-2022-31160 Fehlerbehebung für die Versionen 2.4.4, 2.4.5 und 2.4.6](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) der Wissensdatenbank angegeben ist.

### Highlights

Das Standardverhalten der [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-Abfrage und des ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-Endpunkts hat sich geändert. Standardmäßig gibt die API jetzt immer `true` zurück. Händler können das ursprüngliche Verhalten aktivieren, d. h. `true` zurückgeben, wenn die E-Mail nicht in der Datenbank vorhanden ist, und `false`, ob sie vorhanden ist. <!-- AC-6695 -->

### Plattform-Upgrades

Plattform-Upgrades für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung des Lackcache 7.3**. Diese Version ist kompatibel mit der neuesten Version von Varnish Cache 7.3. Die Kompatibilität mit den Versionen 6.0.x und 7.2.x bleibt bestehen, wir haben jedoch empfohlen, Adobe Commerce 2.4.5-p3 nur mit Varnish Cache Version 7.3 oder Version 6.0 LTS zu verwenden.

* **Unterstützung von RabbitMQ 3.11**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt bestehen, was bis August 2023 unterstützt wird, aber wir haben empfohlen, Adobe Commerce 2.4.5-p3 nur mit RabbitMQ 3.11 zu verwenden.

* **JavaScript-**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten Neben- oder Patch-Versionen aktualisiert, einschließlich `moment.js`-Bibliothek (v2.29.4), `jQuery UI`-Bibliothek (v1.13.2) und `jQuery` Validierungs-Plug-in-Bibliothek (v1.19.5).

## 2.4.5-p2

Die Adobe Commerce-Version 2.4.5-p2 bietet drei Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.5-p1

Die Adobe Commerce-Sicherheitsversion 2.4.5-p1 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.5 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Eine der Sicherheitsfehlerbehebungen umfasste die Erstellung einer neuen Konfigurationseinstellung. Mit der [!UICONTROL **E-Mail-Bestätigung verlangen, wenn die E-Mail geändert wurde**] können Administratoren eine E-Mail-Bestätigung verlangen, wenn ein Administrator bzw. eine Administratorin ihre E-Mail-Adresse ändert. <!-- AC-6292-->

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
