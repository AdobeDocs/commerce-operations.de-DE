---
title: Versionshinweise zu Adobe Commerce 2.4.7 Security Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.7 enthalten sind.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 3a2d104f0a689ac3715af302d470a1660857543c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Versionshinweise für Adobe Commerce 2.4.7-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7-p2

Die Sicherheitsfreigabe Adobe Commerce 2.4.7-p2 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/2024-08/security.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7-p1

Die Adobe Commerce-Sicherheitsversion 2.4.7-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **Aktualisieren der Einstellungen für das einmalige Kennwort (OTP) ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) für den Google Authenticator** - Diese Aktualisierung ist erforderlich, um einen Fehler zu beheben, der durch eine mit [abwärtskompatible Änderung](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7 eingeführt wurde. Die Beschreibung des Felds **[!UICONTROL OTP Window]** bietet jetzt eine genaue Erläuterung der Einstellung, und der Standardwert wurde von `1` in `29` geändert.[

* **B2B-Versionskompatibilität**: Zur Kompatibilität mit Commerce Version 2.4.7-p1 müssen Händler, die über die Adobe Commerce B2B-Erweiterung verfügen, auf [B2B-Version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) aktualisieren.

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.7-p1 behebt ein Problem, das beim Umfang der UPS-Integrationsmigration von der SOAP auf die REST-API eingeführt wurde. Dieses Problem betraf Kunden, die außerhalb der USA versenden, und hinderte sie daran, die Metrik-System-/SI-Messungen von Kilogramm und Zentimetern für Pakete zu verwenden, um Sendungen mit UPS zu erstellen. Weitere Informationen finden Sie im Artikel zur Wissensdatenbank der [UPS Versandmethodenintegration von SOAP zu RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) .
