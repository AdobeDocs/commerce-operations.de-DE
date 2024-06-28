---
title: Versionshinweise zu Adobe Commerce 2.4.7 Security Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.7 enthalten sind.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Versionshinweise für Adobe Commerce 2.4.7-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Die Adobe Commerce-Sicherheitsversion 2.4.7-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Sicherheitshinweise

* **Aktualisieren [Einstellungen für einmaliges Kennwort (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) für Google Authenticator**-Diese Aktualisierung ist erforderlich, um einen Fehler zu beheben, der durch ein [Abwärtskompatible Änderung](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) 2.4.7. Die Beschreibung der **[!UICONTROL OTP Window]** -Feld bietet nun eine genaue Erläuterung der Einstellung und der Standardwert wurde geändert von `1` nach `29`.

* **Kompatibilität der B2B-Versionen**—Zur Kompatibilität mit Commerce Version 2.4.7-p1 müssen Händler mit der Adobe Commerce B2B-Erweiterung auf [B2B Version 1.4.2-p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.7-p1 behebt ein Problem, das beim Umfang der UPS-Integrationsmigration von der SOAP auf die REST-API eingeführt wurde. Dieses Problem betraf Kunden, die außerhalb der USA versenden, und hinderte sie daran, die Metrik-System-/SI-Messungen von Kilogramm und Zentimetern für Pakete zu verwenden, um Sendungen mit UPS zu erstellen. Siehe [Integration der UPS-Versandmethode von der SOAP in die RESTful-API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) Knowledgebase-Artikel .
