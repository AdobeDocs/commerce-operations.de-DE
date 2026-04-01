---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.7
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.7-Sicherheits-Patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0 erreicht das Ende der Unterstützung (End of Support, EOS) ab dem 30. April 2026.
>
>Nach diesem Datum bietet Adobe Commerce 2.4.7 keine Kompatibilität mehr oder
>Unterstützung für alle MySQL-Versionen, die nach MySQL 8.0 veröffentlicht wurden. Adobe nicht
>Validieren oder Bereitstellen von Unterstützung für neuere MySQL-Hauptversionen auf dieser Adobe
>Commerce-Release-Zeile.
>
>Bei allen Adobe Commerce On-Premise-Kunden, die Version 2.4.7 ausführen, sind die
>Es wird empfohlen, die Datenbankserver auf eine kompatible MariaDB-Version zu migrieren.

## 2.4.7-P9

Die Sicherheitsversion 2.4.7-p9 von Adobe Commerce bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Highlights

Diese Version umfasst die folgenden Highlights:

#### MyDHL REST API-Unterstützung für DHL-Versandintegration

Die DHL-Versandintegration unterstützt jetzt zusätzlich zur vorhandenen DHL Express XML-Integration MyDHL-REST-APIs. Diese Aktualisierung stimmt mit dem aktuellen API-Stack von DHL überein und bereitet die Einstellung der älteren XML-APIs vor.

#### Hinzufügen der Kompatibilität mit der neuesten Composer-Version

Adobe Commerce 2.4.7 wurde aktualisiert, um Composer 2.9.x zu unterstützen und gleichzeitig mit Composer 2.2 LTS kompatibel zu bleiben.

## 2.4.7-p8

Die Adobe Commerce-Sicherheitsversion 2.4.7-p8 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

Diese Version umfasst die folgenden Highlights:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### Bekannte Probleme

#### Die Checkout-Seite kann static.min.js und mixins.min.js nicht laden.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

Die Adobe Commerce-Sicherheitsversion 2.4.7-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

Die Adobe Commerce-Version 2.4.7-p6 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **MariaDB-Unterstützung** - Es wurde Unterstützung für MariaDB 10.11 hinzugefügt.

* **API-Leistungsverbesserung**: Behebt die Leistungsbeeinträchtigung bei asynchronen Web-API-Endpunkten, die nach dem vorherigen Sicherheits-Patch eingeführt wurden.<!-- AC-14078 -->

* **CMS blockiert den Zugriff** - Löst ein Problem, bei dem Admin-Benutzer mit eingeschränkten Berechtigungen (z. B. Nur-Merchandising-Zugriff) die [!UICONTROL CMS Blocks] nicht anzeigen konnten.

  Zuvor trat bei diesen Benutzern ein Fehler aufgrund fehlender Konfigurationsparameter nach der Installation früherer Sicherheits-Patches auf.<!-- AC-14087 -->

* **Cookie-Kompatibilität** - Löst eine abwärtsinkompatible Änderung auf, die die `MAX_NUM_COOKIES` im Framework betrifft. Diese Aktualisierung stellt das erwartete Verhalten wieder her und stellt die Kompatibilität für Erweiterungen oder Anpassungen sicher, die mit Cookie-Beschränkungen interagieren.<!-- AC-14475 -->

* **Async-Vorgänge** - Eingeschränkte asynchrone Vorgänge zum Überschreiben früherer Kundenbestellungen.<!-- AC-13917 -->

## 2.4.7-p5

Die Adobe Commerce-Sicherheitsversion 2.4.7-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Mit dieser Version wird auch die Unterstützung für die Adobe Commerce [HIPAA-fähige Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) eingeführt.

>[!ENDSHADEBOX]

### Bekannte Probleme

**Problem**: Bei der Installation von 2.4.7-p5 mit PHP 8.2 oder höher installiert das System `paypal/module-braintree` Version 4.7.0, die für 2.4.8 und höher vorgesehen ist. Für PHP 8.1 wird die richtige Braintree-Version 4.6.1-p5 verwendet. Diese Diskrepanz ist auf die lose Abhängigkeit von `adobe-commerce/extensions-metapackage: ~2.0` im Metapaket zurückzuführen. Dies wirkt sich auf die Kompatibilität und den unterstützten Funktionssatz für PHP 8.2+-Bereitstellungen aus.<!-- ACPLTSRV-6276) -->

Darüber hinaus kann für die Versionen 2.4.7-p3, 2.4.7-p4 und 2.4.7-p5 die Braintree-Erweiterungsversion 4.6.1-p5 installiert werden, während einige Anwender 4.6.1-p3 oder p4 erwarten, da frühere strengere Abhängigkeiten gelockert wurden, um Erweiterungs-Upgrades innerhalb einer Release-Zeile zu ermöglichen. <!-- AC-14430 -->

**Problemumgehung**: Um sicherzustellen, dass Sie die richtige Braintree-Version für Ihre PHP-Version haben, führen Sie `composer update` aus, um die entsprechende Version zu installieren, wie es die `adobe-commerce/extensions-metapackage:2.0.0`-Abhängigkeit vorschreibt.

## 2.4.7-p4

Die Adobe Commerce-Version 2.4.7-p4 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Die Adobe Commerce-Sicherheitsversion 2.4.7-p3 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Die Adobe Commerce-Version 2.4.7-p2 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Die Sicherheitsversion 2.4.7-p1 von Adobe Commerce bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **Aktualisieren [Einstellungen für einmaliges Kennwort (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) für Google Authenticator**-Dieses Update ist erforderlich, um einen Fehler zu beheben, der durch eine [abwärtsinkompatible Änderung](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7 eingeführt wurde. Die Beschreibung des Felds **[!UICONTROL OTP Window]** bietet nun eine genaue Erklärung der Einstellung, und der Standardwert wurde von `1` in `29` geändert.

* **B2B-Versionskompatibilität** - Zur Kompatibilität mit Commerce Version 2.4.7-p1 müssen Händler, die die Adobe Commerce B2B-Erweiterung haben, ein Upgrade auf [B2B Version 1.4.2-p1 durchführen](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.7-p1 löst ein Problem, das im Rahmen der UPS-Integrationsmigration von der SOAP zur REST-API eingeführt wurde. Dieses Problem betraf Kunden, die außerhalb der USA versenden, und hinderte sie daran, die metrischen System-/SI-Messungen von Kilogramm und Zentimeter für Pakete zu verwenden, um Sendungen mit UPS zu erstellen. Weitere Informationen finden Sie [&#x200B; Knowledgebase-Artikel zur Migration der UPS-Versandmethodenintegration von SOAP &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) RESTful-API.

<!-- Last updated from includes: 2026-03-19 11:29:47 -->
