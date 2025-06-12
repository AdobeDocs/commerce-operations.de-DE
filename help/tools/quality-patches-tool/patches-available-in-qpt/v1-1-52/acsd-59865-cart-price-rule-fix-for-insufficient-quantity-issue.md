---
title: 'ACSD-59865: [!UICONTROL Cart Price Rule] kann frühere Regeln aufgrund unzureichender Produktmenge nicht aufheben'
description: Wenden Sie den Patch ACSD-59865 an, um das Adobe Commerce-Problem zu beheben, bei dem der Wert „Rabattmengenschritt“ in „Fester Betragsrabatt“, „Prozentsatz des Produktpreisrabatts“ und „X kaufen und Y erhalten“ die Aktion der vorherigen Regeln nicht mehr [!UICONTROL Cart Price Rules].
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] kann frühere Regeln aufgrund unzureichender Produktmenge nicht aufheben

Mit dem Patch ACSD-59865 wird das Problem behoben, dass der *[!UICONTROL Discount quantity step]* in *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* und *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] die Aktion der vorherigen Regeln nicht mehr abbricht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59865. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der [!UICONTROL Cart Price Rule] kann zuvor angewendete Regeln aufgrund einer unzureichenden Produktmenge im Warenkorb nicht stornieren.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Administrator an.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** und klicken Sie auf **[!UICONTROL Add New rule]**.
   * **[!UICONTROL Rule Name]** = *Test - 1*
   * Wählen Sie alle *Websites* und *Kundengruppen*
   * **[!UICONTROL Priority]** = *0*
   * Gehen Sie zum Abschnitt **[!UICONTROL Actions]**:
      * **[!UICONTROL Apply]** = *Prozent des Produktpreisrabatts*
      * **[!UICONTROL Discount amount]** = *10*
      * **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Setzen Sie **[!UICONTROL Discard subsequent rules]** auf *Nein*
1. Löschen Sie den Cache.
1. Gehen Sie zur Storefront, fügen Sie einen Artikel zum Warenkorb hinzu und fahren Sie mit *Checkout/Warenkorb* fort.
1. Überprüfen Sie, ob der *10%* Rabatt auf Ihren Warenkorb angewendet wird.
1. Kehren Sie zur **[!UICONTROL Cart Price Rules]** zurück und erstellen Sie eine neue Regel.
   * **[!UICONTROL Rule Name]** = *Test - 2*
   * Alle **[!UICONTROL Websites]** und **[!UICONTROL Customer Groups]** auswählen
   * **[!UICONTROL Priority]** = *2*
   * Navigieren Sie zum Abschnitt **[!UICONTROL Actions]** :
      * **[!UICONTROL Apply]** = *Prozent des Produktpreisrabatts*
      * **[!UICONTROL Discount amount]** = *20*
      * **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Löschen Sie den Cache.
1. Geh wieder zurück in die Storefront.
1. Aktualisieren Sie den Warenkorb, um die Regeln zu aktualisieren. Stellen Sie sicher, dass der *10%* Rabatt nicht mehr angewendet wird.
1. Fügen Sie Artikel zu Ihrem Warenkorb hinzu, bis die Menge den Wert *Schritt* erfüllt, der für die zweite Regel erforderlich ist.

<u>Erwartete Ergebnisse</u>:

Die erste [!UICONTROL Cart Price Rule] wird angewendet, wenn die Bedingungen der zweiten Regel erfüllt sind.

<u>Tatsächliche Ergebnisse</u>:

Die Preisregeln werden wie im Admin-Dashboard konfiguriert angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
