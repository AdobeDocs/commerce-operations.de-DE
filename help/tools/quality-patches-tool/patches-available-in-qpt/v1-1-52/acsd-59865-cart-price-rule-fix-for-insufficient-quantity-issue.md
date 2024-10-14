---
title: "ACSD-59865: [!UICONTROL Cart Price Rule] kann frühere Regeln aufgrund unzureichender Produktmenge nicht stornieren."
description: Wenden Sie den Patch ACSD-59865 an, um das Adobe Commerce-Problem zu beheben, bei dem der Wert *Mengenrabatt für Rabatt für feste Beträge*,* *Prozent des Rabatts für Produktpreise* und *Kauf X für Y* [!UICONTROL Cart Price Rules] die Aktion der vorherigen Regeln nicht mehr abbricht.
feature: Price Rules
role: Admin, Developer
source-git-commit: 602a839708eab2551bd99a4f24e66edbde511150
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] kann frühere Regeln aufgrund unzureichender Produktmenge nicht stornieren

Der Patch ACSD-59865 behebt das Problem, dass der *[!UICONTROL Discount quantity step]* -Wert in *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* und *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] die Aktion vorheriger Regeln nicht mehr abbricht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59865. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die [!UICONTROL Cart Price Rule] kann die zuvor angewendeten Regeln aufgrund einer unzureichenden Produktmenge im Warenkorb nicht abbrechen.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Administrator an.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** und klicken Sie auf **[!UICONTROL Add New rule]**.
   * Setzen Sie **[!UICONTROL Rule Name]** = *Test - 1*
   * Alle *Websites* und *Kundengruppen* auswählen
   * Legen Sie **[!UICONTROL Priority]** = *0* fest
   * Gehen Sie zum Abschnitt **[!UICONTROL Actions]** :
      * Setzen Sie **[!UICONTROL Apply]** = *Prozent des Produktpreisrabatts*
      * Setzen Sie **[!UICONTROL Discount amount]** = *10*
      * Setzen Sie **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Legen Sie **[!UICONTROL Discount Qty Step (Buy X)]** = *0* fest
      * Setzen Sie **[!UICONTROL Discard subsequent rules]** auf *Nein*
1. Löschen Sie den Cache.
1. Gehen Sie zur Storefront, fügen Sie ein Element zum Warenkorb hinzu und fahren Sie mit *Checkout/Warenkorb* fort.
1. Stellen Sie sicher, dass der Rabatt von *10%* auf Ihren Warenkorb angewendet wird.
1. Kehren Sie zu &quot;**[!UICONTROL Cart Price Rules]**&quot;zurück und erstellen Sie eine neue Regel.
   * Setzen Sie **[!UICONTROL Rule Name]** = *Test - 2*
   * Alle **[!UICONTROL Websites]** und **[!UICONTROL Customer Groups]** auswählen
   * Legen Sie **[!UICONTROL Priority]** = *2* fest
   * Navigieren Sie zum Abschnitt **[!UICONTROL Actions]** :
      * Setzen Sie **[!UICONTROL Apply]** = *Prozent des Produktpreisrabatts*
      * Setzen Sie **[!UICONTROL Discount amount]** = *20*
      * Setzen Sie **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Legen Sie **[!UICONTROL Discount Qty Step (Buy X)]** = *3* fest
1. Löschen Sie den Cache.
1. Gehen Sie wieder zurück zur Storefront.
1. Aktualisieren Sie den Warenkorb, um die Regeln zu aktualisieren. Vergewissern Sie sich, dass der Rabatt von *10%* nicht mehr angewendet wird.
1. Fügen Sie Artikel in Ihren Warenkorb ein, bis die Menge den für die zweite Regel erforderlichen *Schritt* -Wert erfüllt.

<u>Erwartete Ergebnisse</u>:

Der erste [!UICONTROL Cart Price Rule] wird angewendet, wenn die Bedingungen der zweiten Regel erfüllt sind.

<u>Tatsächliche Ergebnisse</u>:

Preisregeln werden wie im Admin-Dashboard konfiguriert angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
