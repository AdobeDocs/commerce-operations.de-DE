---
title: 'ACSD-52160: Produktvalidierungsergebnis anhand der Warenkorb-Preisregel'
description: Wenden Sie den Patch ACSD-52160 an, um das Adobe Commerce-Problem zu beheben, bei dem das Ergebnis der Produktvalidierung anhand der Warenkorbpreisregel basierend auf der Regelbedingung *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* nicht ordnungsgemäß bewertet wird.
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160: Ergebnis der Produktvalidierung anhand der Warenkorbpreisregel wird nicht ordnungsgemäß ausgewertet

Mit dem Patch ACSD-52160 wird das Problem behoben, dass das Produktvalidierungsergebnis in Bezug auf die Warenkorbpreisregel basierend auf der *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* der Regelbedingung nicht ordnungsgemäß ausgewertet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-52160. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Ergebnis der Produktvalidierung anhand der Preisregel für den Warenkorb wird nicht ordnungsgemäß auf der Grundlage der *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* der Regelbedingung ausgewertet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Produkte, die zwei verschiedenen Kategorien zugewiesen sind.
1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit Bedingungen wie:

   * **SKU 1** im *[!UICONTROL FOUND]*
   * **SKU 2** im *[!UICONTROL NOT FOUND]*

1. Fügen Sie beide Produkte zum Warenkorb hinzu.
1. Wenden Sie den Gutscheincode an.

<u>Erwartete Ergebnisse</u>

Der Couponcode wird nicht angewendet, da der Warenkorb Produkte aus der eingeschränkten Kategorie enthält.

<u>Tatsächliche Ergebnisse</u>

Der Couponcode wird angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
