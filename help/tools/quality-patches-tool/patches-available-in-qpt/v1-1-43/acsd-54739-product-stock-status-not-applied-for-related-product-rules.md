---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* Status nicht angewendet für *[!UICONTROL Related Product Rules]*'
description: Wenden Sie den Patch ACSD-54739 an, um das Adobe Commerce-Problem zu beheben, bei dem der Status *[!UICONTROL Product Stock]* für *[!UICONTROL Related Product Rules]* nicht angewendet wird.
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* Status für *[!UICONTROL Related Product Rules]* nicht angewendet

Mit dem Patch ACSD-54739 wird das Problem behoben, dass der *[!UICONTROL Product stock]* nicht für *[!UICONTROL Related Product Rules]* angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54739. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

*[!UICONTROL Product stock]* Status wird für *[!UICONTROL Related Product Rules]* nicht angewendet.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie die **[!UICONTROL Display Out of Stock Products]** auf *Ja* fest.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** und setzen Sie *Ja* für die Bedingung der Promo-Regel.
1. Erstellen Sie die zugehörige Produktregel. Gehen Sie zu **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Bedingung mit Attributmenge hinzufügen (wählen Sie „Auf Lager/Nicht vorrätig„).
1. Überprüfen Sie die Produkte am Frontend.

<u>Erwartete Ergebnisse</u>:

Das vorrätige/nicht vorrätige Produkt stimmt *[!UICONTROL Related Product Rules]* überein.

<u>Tatsächliche Ergebnisse</u>:

Das vorrätige/nicht vorrätige Produkt entspricht nicht der *[!UICONTROL Related Product Rules]*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
