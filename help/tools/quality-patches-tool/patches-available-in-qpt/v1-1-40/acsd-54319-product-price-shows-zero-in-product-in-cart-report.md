---
title: 'ACSD-54319: Produktpreis zeigt Null im *[!UICONTROL Products in Carts]* Bericht'
description: Wenden Sie den Patch ACSD-54319 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktpreis im Bericht *[!UICONTROL Products in Carts]* null anzeigt
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319: Produktpreis zeigt Null *[!UICONTROL Products in Carts]* Bericht an

Mit dem Patch ACSD-54319 wird das Problem behoben, dass der Produktpreis in *[!UICONTROL Products in Carts]* Bericht null anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54319. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktpreis wird in *[!UICONTROL Products in Carts]* Bericht mit null angegeben.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie **[!UICONTROL Catalog Price Scope]** unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** auf **[!UICONTROL Website]** fest.
1. Erstellen Sie eine zweite Website unter **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Erstellen Sie ein Produkt über **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Dieses Produkt nur der zweiten Website zuweisen.
1. Fügen Sie von der zweiten Website aus ein Produkt zum Warenkorb hinzu.
1. Wechseln Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]**.
1. Überprüfen Sie die *[!UICONTROL Price]* Spalte *[!UICONTROL Products In Carts]* Raster.

<u>Erwartete Ergebnisse</u>:

Der Produktpreis ist in *[!UICONTROL Products in Carts]* Berichtsraster nicht null.

<u>Tatsächliche Ergebnisse</u>:

Der Produktpreis ist in *[!UICONTROL Products in Carts]* Berichtsraster gleich null.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
