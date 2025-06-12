---
title: 'ACSD-54418: Fester Rabattbetrag, der fälschlicherweise dem untergeordneten Produkt des dynamisch Preispakets hinzugefügt wurde'
description: Wenden Sie den Patch ACSD-54418 an, um das Adobe Commerce-Problem zu beheben, bei dem der feste Rabattbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch berechneten Bundles angewendet wird.
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54418: Fester Rabattbetrag, der fälschlicherweise zum untergeordneten Produkt des dynamisch preispflichtigen Pakets hinzugefügt wurde.

Mit dem Patch ACSD-54418 wird das Problem behoben, dass der feste Rabattbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch preispflichtigen Pakets angewendet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.42 installiert ist. Die Patch-ID ist ACSD-54418. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der feste Rabattbetrag wird fälschlicherweise auf jedes untergeordnete Produkt des Pakets mit dynamischem Preis angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine **[!UICONTROL bundle product]** mit dynamischen Preis- und *2*-Bundle-Optionen.
1. Erstellen Sie eine **[!UICONTROL cart price rule]** mit einem bestimmten Gutscheincode, der nur für die gebündelte **[!UICONTROL SKU]** gilt und einen festen Rabatt hat.
1. Fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Wenden Sie die **[!UICONTROL coupon code]** an.
1. Überprüfen Sie den auf den Warenkorb angewendeten Rabatt.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nur einmal auf das gesamte gebündelte Produkt angewendet.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird auf jedes untergeordnete Bundle-Produkt angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
