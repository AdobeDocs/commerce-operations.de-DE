---
title: 'ACSD-49286: Produkt zweimal in den Warenkorb gelegt, wenn mehrere Produkt-Widgets vorhanden sind'
description: Wenden Sie den Patch ACSD-49286 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286: Produkt zweimal in den Warenkorb gelegt, wenn mehrere Produkt-Widgets vorhanden sind

Mit dem Patch ACSD-49286 wird das Problem behoben, dass das Produkt zweimal in den Warenkorb gelegt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49286. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produkt wird zweimal zum Warenkorb hinzugefügt, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin an und gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Klicken Sie im Abschnitt Inhalt auf **[!UICONTROL Edit]** mithilfe von [!DNL Page Builder].
1. Fügen Sie zwei Zeilenelemente zu **[!UICONTROL Content]** hinzu.
1. Fügen Sie Produkte in beide Zeilenelemente hinzu.
1. Legen Sie in der ersten Zeile das Erscheinungsbild des Produkts auf [!UICONTROL Product Grid] fest und wählen Sie eine anzuzeigende Kategorie aus.
1. Legen Sie in der zweiten Zeile das Erscheinungsbild des Produkts auf [!UICONTROL Product Carousel] fest und wählen Sie eine andere anzuzeigende Kategorie aus.
1. Gehen Sie zur Storefront-**[!UICONTROL Home Page]** und fügen Sie ein Produkt aus dem Produktraster hinzu.
1. Ein weiteres Produkt aus [!UICONTROL Product Carousel] hinzufügen.

<u>Erwartete Ergebnisse</u>:

Die Produktmenge sollte sich nicht verdoppeln, nachdem ein Produkt aus [!UICONTROL Product Grid] zum Warenkorb hinzugefügt wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Produktmenge verdoppelt sich, nachdem ein Produkt aus [!UICONTROL Product Grid] zum Warenkorb hinzugefügt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
