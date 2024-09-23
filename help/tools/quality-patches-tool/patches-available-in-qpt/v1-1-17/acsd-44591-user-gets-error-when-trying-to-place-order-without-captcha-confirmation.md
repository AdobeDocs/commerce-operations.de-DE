---
title: "ACSD-44591: Fehler bei Bestellung ohne CAPTCHA-Bestätigung"
description: Der Patch ACSD-44591 behebt das Problem, bei dem der Benutzer beim Versuch, eine Bestellung ohne CAPTCHA-Bestätigung zu tätigen, Fehler erhält.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-44591: Fehler bei Bestellung ohne CAPTCHA-Bestätigung

Der Patch ACSD-44591 behebt das Problem, bei dem der Benutzer beim Versuch, eine Bestellung ohne CAPTCHA-Bestätigung zu tätigen, Fehler erhält.
Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-44591. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer erhält beim Versuch, eine Bestellung ohne CAPTCHA-Bestätigung zu tätigen, Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie Google ReCaptcha v2 (ich bin kein Roboter).
1. Aktivieren Sie ReCaptcha für den Checkout.
1. Versuchen Sie, eine Bestellung zu tätigen, ohne auf das ReCaptcha zu klicken.
1. Sobald Sie die Fehlermeldung für fehlende ReCaptcha (*ReCaptcha-Validierung fehlgeschlagen, versuchen Sie es erneut*), klicken Sie auf **ReCaptcha** und versuchen Sie dann, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird nicht mit falschem ReCaptcha platziert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgenden Fehler:

* *Erneutes Captcha-Validierung fehlgeschlagen, versuchen Sie es erneut*
* *Kein solcher Warenkorb mit ID = 1*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
