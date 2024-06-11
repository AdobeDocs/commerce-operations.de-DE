---
title: Versionshinweise zu Adobe Commerce 2.4.7 Security Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.7 enthalten sind.
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.7-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Die Adobe Commerce-Sicherheitsversion 2.4.7-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.7 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Sicherheitshinweis

Diese Version enthält eine Aktualisierung der [Einstellungen für einmaliges Kennwort (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) für Google Authenticator zur Behebung eines Fehlers, der durch einen [Abwärtskompatible Änderung](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) 2.4.7. Die Beschreibung der **[!UICONTROL OTP Window]** -Feld bietet nun eine genaue Erläuterung der Einstellung und der Standardwert wurde geändert von `1` nach `29`.
