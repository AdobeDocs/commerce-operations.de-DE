---
title: 'MDVA-39305: Anmeldeproblem mit aktiviertem Google reCAPTCHA'
description: Wenden Sie den MDVA-39305-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem sich registrierte Kunden nicht anmelden können, wenn Google reCAPTCHA aktiviert ist.
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
source-git-commit: 007fcb1308ba2c5b42755ee4c4c2ca598eb0e62e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305: Anmeldeproblem mit aktiviertem Google reCAPTCHA

>[!NOTE]
>
>Dieser Patch wurde aktualisiert, und die neueste Patch-ID ist MDVA-39305-V3. Der neue Patch wurde für die Adobe Commerce-Versionen 2.4.4, 2.4.5-p2 und 2.4.7 erstellt. Weitere Informationen finden Sie im Patch[Artikel (MDVA-39305-V3](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha).

Der Patch MDVA-39305 behebt das Problem, dass sich registrierte Kunden nicht anmelden können, wenn Google reCAPTCHA aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-39305. Beachten Sie, dass das Problem in den Adobe Commerce-Versionen 2.4.4 und 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Registrierte Kunden können sich nicht mit dem aktivierten Google reCAPTCHA anmelden.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Store** > **Configuration** > **Security** > **Google reCAPTCHA Storefront** und aktivieren Sie **Google reCAPTCHA**.
1. Gehen Sie zu **Frontend**.
1. Öffnen Sie **Entwickler-Tool** Konsole im Browser.

<u>Erwartete Ergebnisse</u>:

Keine CSP-Warnungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

CSP-Warnungen in der Konsole.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
