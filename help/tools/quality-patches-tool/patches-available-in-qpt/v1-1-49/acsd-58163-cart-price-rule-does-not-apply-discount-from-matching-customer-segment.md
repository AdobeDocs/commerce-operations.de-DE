---
title: 'ACSD-58163: [!UICONTROL Cart Price Rule] wendet keinen Rabatt vom übereinstimmenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode an'
description: Wenden Sie den Patch ACSD-58163 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!UICONTROL Cart Price Rule] keinen Rabatt für einen Gast vom entsprechenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode anwendet.
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163: [!UICONTROL Cart Price Rule] wendet keinen Rabatt vom übereinstimmenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode an

Der Patch ACSD-58163 behebt das Problem, dass der [!UICONTROL Cart Price Rule] keinen Rabatt vom entsprechenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode anwendet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58163. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule] wendet für einen Gast keinen Rabatt vom entsprechenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode an.

<u>Zu reproduzierende Schritte</u>:

1. Kundensegment erstellen:
   * Für Besucher.
   * Mit der Bedingung, dass ein Produkt im Warenkorb ist.

1. Erstellen Sie eine *[!UICONTROL Cart Price Rule]*:
   * Ohne Couponcode.
   * Mit der Bedingung, die mit dem Besucher-Kundensegment übereinstimmt.

1. Erstellen Sie ein einfaches Produkt.
1. Öffnen Sie die Storefront als Gast.
1. Fügen Sie dem Warenkorb ein einfaches Produkt hinzu.
1. Gehen Sie zum Warenkorb.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Cart Price Rule]* Rabatt wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL Cart Price Rule]* Rabatt wird nicht angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
