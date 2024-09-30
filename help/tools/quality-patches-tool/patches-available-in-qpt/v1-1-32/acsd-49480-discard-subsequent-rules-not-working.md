---
title: "ACSD-49480: Nachfolgende Regeln verwerfen funktioniert nicht"
description: Wenden Sie den Patch ACSD-49480 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!UICONTROL Cart Price Rule - Discard Subsequent Rules] nicht wie gewünscht funktioniert.
feature: Price Rules
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie vorgesehen

Der Patch ACSD-49480 behebt das Problem, dass der [!UICONTROL Cart Price Rule - Discard Subsequent Rules] nicht wie gewünscht funktioniert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID lautet ACSD-49480. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie gewünscht.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit einem Couponcode (nennen Sie ihn *TEST*), der der *Produkt-ID 1* auf der Registerkarte **[!UICONTROL Actions]** einen Rabatt von 10 USD gewährt, wobei [!UICONTROL Discard Subsequent Rules] auf *[!UICONTROL Yes]* und [!UICONTROL Priority] auf *1* eingestellt ist.
1. Erstellen Sie einen weiteren **[!UICONTROL Cart Price Rule]** ohne Couponcode, der *Produkt-ID 2* im Tab **[!UICONTROL Actions]** einen Rabatt von 5 USD gewährt, wobei [!UICONTROL Priority] auf *2* eingestellt ist. Hier nehmen wir an, dass es sich um einen globalen Verkauf für die *Produkt-ID 2* handelt.
1. Gehen Sie zur Frontend-Site und fügen Sie *Produkt-ID 1* und *Produkt-ID 2* in den Warenkorb ein.
1. Wenden Sie den Couponcode *TEST* an.

<u>Erwartete Ergebnisse</u>

* *Rabatt 1* wird auf *Produkt-ID 1* angewendet.
* *Rabatt 2* wird auf *Produkt-ID 2* angewendet.

<u>Tatsächliche Ergebnisse</u>

* Nur *Rabatt 1* wird auf *Produkt-ID 1* angewendet.
* *Rabatt 2* wird nicht auf *Produkt-ID 2* angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
