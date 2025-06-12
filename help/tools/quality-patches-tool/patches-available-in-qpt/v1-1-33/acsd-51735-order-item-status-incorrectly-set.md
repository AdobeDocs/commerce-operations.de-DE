---
title: 'ACSD-51735: Status des Bestellartikels wird fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt, wenn der Produktvorrat 0 beträgt'
description: Wenden Sie den Patch ACSD-51735 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bestellartikelstatus fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt wird, wenn der Produktvorrat 0 beträgt.
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-51735: Der Bestellartikelstatus wurde fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt, wenn der Produktbestand 0 beträgt

Der Patch ACSD-51735 behebt das Problem, dass der Bestellartikelstatus fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt wird, wenn der Produktvorrat 0 beträgt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50895. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Bestellartikelstatus wird fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt, wenn der Produktbestand 0 beträgt.

<u>Voraussetzungen</u>:

* Adobe Commerce Inventory management (MSI)-Module sind installiert.
* Nachbestellungen sind in **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]** aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Neues Lager erstellen.
1. Erstellen Sie eine neue Quelle.
1. Weisen Sie dem neuen Lager die Standard-Website und die neue Quelle zu.
1. Erstellen Sie ein neues Produkt.

   * Legen Sie die standardmäßige Quellmenge auf 10 und die neue Quellmenge auf 0 fest.

1. Fügen Sie das Produkt dem Warenkorb auf der Storefront hinzu.
1. Beachten Sie die Rückstandswarnung beim Checkout, die angibt, dass das Produkt von einer neuen Quelle stammt.
1. Bestellung aufgeben.
1. Öffnen Sie die Bestellung in Admin und überprüfen Sie den Status der Rückstandsbestellung.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge zeigt, dass die Menge 1 rückgestellt ist.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge zeigt an, dass Menge 1 bestellt und nicht nachbestellt ist.

>[!MORELIKETHIS]
>
>[Status des Bestellartikels ist fälschlicherweise auf *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)gesetzt

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
