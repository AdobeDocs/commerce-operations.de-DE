---
title: 'ACSD-50345: reCAPTCHA-Probleme beim Checkout'
description: Wenden Sie den Patch ACSD-50345 an, um das Adobe Commerce-Problem zu beheben, bei dem die reCAPTCHA v2- und v3-Validierungen beim Bestellen von Bestellungen und während des Checkouts fehlschlagen.
feature: Checkout, Orders
role: Admin
exl-id: eae9a6ad-0999-4581-b3c0-7667ee7beb54
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-Probleme beim Checkout

Der Patch ACSD-50345 behebt das Problem, bei dem die reCAPTCHA v2- und v3-Validierungen bei der Auftragserteilung und beim Checkout fehlschlagen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.31 installiert ist. Die Patch-ID ist ACSD-50345. Beachten Sie, dass das Problem teilweise in Adobe Commerce 2.4.6 behoben wurde und in Adobe Commerce 2.4.7 vollständig behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

**1. Fall**

Google reCAPTCHA v2 wird nach Übermittlung einer fehlgeschlagenen Zahlung nicht neu geladen.

<u>Zu reproduzierende Schritte</u>

1. Konfigurieren Sie **[!UICONTROL Google reCAPTCHA v2]** (*Ich bin kein Roboter*).
1. Aktivieren Sie den **[!UICONTROL reCAPTCHA]** für den Checkout.
1. Versuchen Sie, eine Bestellung aufzugeben, ohne auf **[!UICONTROL reCAPTCHA]** zu klicken.
1. Sobald der Benutzer die Fehlermeldung für die fehlende reCAPTCHA erhält (*reCAPTCHA-Validierung fehlgeschlagen, versuchen Sie es erneut*), klicken Sie auf die &quot;**[!UICONTROL reCAPTCHA]**&quot;, und versuchen Sie dann, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>

Die Bestellung wird nicht mit einem falschen reCAPTCHA platziert.

<u>Tatsächliche Ergebnisse</u>

Ein Fehler wird ausgegeben - *reCAPTCHA-Validierung fehlgeschlagen, versuchen Sie es erneut* und *Kein Warenkorb mit ID = 4*

**Case #2**

Google reCAPTCHA v3 Invisible funktioniert beim Checkout nicht und die Bestellung kann nicht platziert werden. Das `PlaceOrder` -Ereignis wird nicht ausgelöst.

<u>Zu reproduzierende Schritte</u>

1. Konfigurieren Sie die **[!UICONTROL reCAPTCHA v3 Invisible]** von **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Aktivieren Sie **[!UICONTROL reCAPTCHA v3 Invisible]** für das Auschecken/Platzieren einer Bestellung auf der Registerkarte **[!UICONTROL Storefront]**.
1. Versuchen Sie, eine Bestellung mit der Zahlungsmethode [!UICONTROL Check/Money order] zu tätigen.

<u>Erwartete Ergebnisse</u>

Die Reihenfolge sollte bei aktiviertem **[!UICONTROL reCAPTCHA]** platziert werden.

<u>Tatsächliche Ergebnisse</u>

Nachdem Sie auf die Schaltfläche &quot;**[!UICONTROL Place Order]**&quot; geklickt haben, wird sie deaktiviert, und nichts passiert weiter.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
