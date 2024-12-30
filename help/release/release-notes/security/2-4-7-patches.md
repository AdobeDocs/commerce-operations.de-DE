---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.7
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Versionshinweise für Adobe Commerce 2.4.7-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7-p3

Die Adobe Commerce-Sicherheitsversion 2.4.7-p3 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.7-p2

Die Adobe Commerce-Version 2.4.7-p2 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/2024-08/security.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7-p1

Die Sicherheitsversion 2.4.7-p1 von Adobe Commerce bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **Aktualisieren [Einstellungen für einmaliges Kennwort (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) für Google Authenticator**-Dieses Update ist erforderlich, um einen Fehler zu beheben, der durch eine [abwärtsinkompatible Änderung](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7 eingeführt wurde. Die Beschreibung des Felds **[!UICONTROL OTP Window]** bietet nun eine genaue Erklärung der Einstellung, und der Standardwert wurde von `1` in `29` geändert.

* **B2B-Versionskompatibilität** - Zur Kompatibilität mit Commerce Version 2.4.7-p1 müssen Händler, die die Adobe Commerce B2B-Erweiterung haben, ein Upgrade auf [B2B Version 1.4.2-p1 durchführen](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.7-p1 löst ein Problem, das im Rahmen der UPS-Integrationsmigration von der SOAP zur REST-API eingeführt wurde. Dieses Problem betraf Kunden, die außerhalb der USA versenden, und hinderte sie daran, die metrischen System-/SI-Messungen von Kilogramm und Zentimeter für Pakete zu verwenden, um Sendungen mit UPS zu erstellen. Weitere Informationen finden Sie [ Knowledgebase-Artikel zur Migration der UPS-Versandmethodenintegration von SOAP ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) RESTful-API .
