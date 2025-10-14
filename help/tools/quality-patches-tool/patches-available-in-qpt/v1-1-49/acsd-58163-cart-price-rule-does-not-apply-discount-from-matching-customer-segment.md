---
title: 'ACSD-58163: [!UICONTROL Cart Price Rule] wendet keinen Rabatt vom Abgleich [!UICONTROL Customer Segment] Warenkorbs ohne Gutscheincode an'
description: Wenden Sie den Patch ACSD-58163 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!UICONTROL Cart Price Rule] ohne Couponcode keinen Rabatt für einen Gast aus dem entsprechenden [!UICONTROL Customer Segment] anwendet.
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163: [!UICONTROL Cart Price Rule] wendet keinen Rabatt vom Abgleich [!UICONTROL Customer Segment] Warenkorbs ohne Gutscheincode an

Mit dem Patch ACSD-58163 wird das Problem behoben, dass der [!UICONTROL Cart Price Rule] ohne Couponcode keinen Rabatt auf den entsprechenden [!UICONTROL Customer Segment] Warenkorb anwendet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58163. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule] wendet ohne Gutscheincode keinen Rabatt für einen Gast aus dem passenden [!UICONTROL Customer Segment] an.

<u>Schritte zur Reproduktion</u>:

1. Kundensegment erstellen:
   * Für Besucher.
   * Mit der Bedingung, dass ein Produkt im Warenkorb ist.

1. *[!UICONTROL Cart Price Rule]* erstellen:
   * Ohne Gutscheincode.
   * Mit der Bedingung, die mit dem Besucher-Kundensegment übereinstimmt.

1. Erstellen Sie ein einfaches Produkt.
1. Öffne die Storefront als Gast.
1. Fügen Sie ein einfaches Produkt zum Warenkorb hinzu.
1. Gehen Sie zum Warenkorb.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Cart Price Rule]* Rabatt wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL Cart Price Rule]* Rabatt wird nicht angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
