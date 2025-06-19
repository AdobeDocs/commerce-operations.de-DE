---
title: 'ACSD-52786: Katalogregel *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der SKU beginnen'
description: Wenden Sie den Patch ACSD-52786 an, um das Adobe Commerce-Problem zu beheben, bei dem die Katalogregelbedingung *[!UICONTROL SKU is]* für alle Produkte gilt, die mit der angegebenen SKU beginnen.
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52786: Katalogregel &quot;*[!UICONTROL SKU is]*&quot; gilt für alle Produkte, die mit der SKU beginnen

Mit dem Patch „ACSD-52786“ wird das Problem behoben, dass die Katalogregelbedingung *[!UICONTROL SKU is]* für alle Produkte gilt, die mit der angegebenen SKU beginnen. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52786. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Katalogregelbedingung *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der angegebenen SKU beginnen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Produkte, eines mit SKU „24“ und eines mit SKU „24-MB01“.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Wenden Sie die folgende Bedingung an:
   * *[!UICONTROL If ** ALLE **dieser Bedingungen sind** TRUE **]*: *[!UICONTROL SKU is 24]*
1. Legen Sie einen beliebigen Rabattbetrag in Aktionen fest.
1. Klicken Sie auf **[!UICONTROL Save and Apply]**.
1. Cache leeren.
1. Besuchen Sie die Storefront und überprüfen Sie den Preis von 24-MB01.

<u>Erwartete Ergebnisse</u>:

Katalogregel wird nur auf ein einzelnes Produkt mit einer SKU von 24 angewendet.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogregelbedingung *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der angegebenen SKU beginnen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
