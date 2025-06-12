---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]** Schaltfläche ausgegraut, wenn die Zwischensumme größer ist als der konfigurierte Mindestbestellwert'
description: Wenden Sie den Patch ACSD-46617 an, um das Adobe Commerce-Problem zu lösen, bei dem die Schaltfläche **[!UICONTROL Continue to Checkout]** ausgegraut ist, selbst wenn die Zwischensumme größer als der konfigurierte Mindestbestellbetrag ist.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617: Schaltfläche &quot;[!UICONTROL Continue to Checkout]&quot; ist ausgegraut, wenn die Zwischensumme größer als &quot;[!UICONTROL Minimum Order Amount]&quot; ist

Mit diesem Patch von ACSD-46617 wird das Problem behoben, dass die Schaltfläche **[!UICONTROL Continue to Checkout]** ausgegraut ist, selbst wenn die Zwischensumme größer als der konfigurierte Mindestbestellwert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-46617. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Schaltfläche **[!UICONTROL Continue to Checkout]** ist auch dann ausgegraut, wenn die Zwischensumme größer ist als der konfigurierte Mindestbestellwert.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** und stellen Sie Folgendes ein:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Erstellen Sie eine [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Erstellen Sie ein Produkt zum Preis von 25 $.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Gehen Sie zum Warenkorb, wählen Sie die $5-**[!UICONTROL Flat Rate shipping]**-Methode aus und wenden Sie den Gutscheincode an.
1. Wechseln Sie zur Kasse, schließen Sie den Versand ab und navigieren Sie zum Abschnitt **[!UICONTROL Paytment]** .
1. Kehren Sie zum Warenkorb zurück.

<u>Erwartete Ergebnisse</u>:

Es gibt keinen Fehler im Zusammenhang mit dem Mindestbestellbetrag, da die Gesamtsumme von $2.4 größer ist als der erforderliche Betrag von $2.

<u>Tatsächliche Ergebnisse</u>:

* Es liegt ein Fehler im Zusammenhang mit dem Mindestbestellbetrag vor, selbst wenn der Gesamtwert von $2.4 größer ist als der Mindestbestellbetrag von $2.
* Die **[!UICONTROL Continue to Checkout]** ist ausgegraut.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
