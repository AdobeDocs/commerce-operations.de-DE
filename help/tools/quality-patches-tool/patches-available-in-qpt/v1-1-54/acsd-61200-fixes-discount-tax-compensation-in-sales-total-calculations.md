---
title: 'ACSD-61200: Korrektur der Rabattsteuervergütung in Berechnungen der Verkaufssumme'
description: Wenden Sie den Patch ACSD-61200 an, um das Adobe Commerce-Problem zu beheben, bei dem *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* in den Berechnungen der Verkaufssummen fehlen, was zu Diskrepanzen zwischen den Auftragsdaten und den Gutscheindaten führt.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: Korrektur der Rabattsteuervergütung in Berechnungen der Verkaufssumme

Der Patch ACSD-61200 behebt das Problem, dass *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* in *[!UICONTROL Total Amount]*- und *[!UICONTROL Total Amount Actual]* fehlen, was zu Diskrepanzen zwischen den Auftragsdaten und den Couponberichtsdaten führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61200. Beachten Sie, dass das Problem in Adobe Commerce Version 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

- Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

- Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ungenauigkeiten in den Berichtsdaten zu Kundenaufträgen und Coupons aufgrund fehlender *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* in den Berechnungen der Verkaufssummen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine [!UICONTROL Tax Zone] und eine [!UICONTROL Tax Rule].
1. Legen Sie die folgenden Steuerkonfigurationen fest:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Aktualisieren Sie die folgenden Anzeigeeinstellungen für Bestellungen, Rechnungen und Gutschriften:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Erstellen Sie eine [!UICONTROL Cart Price Rule] mit einem Gutschein für einen Rabatt von 10 %.
1. Mit dem Gutschein eine Bestellung abschließen und eine Rechnung und Lieferung generieren.
1. Navigieren Sie zu **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** und erstellen Sie einen Bericht.
1. Vergleichen Sie die Daten in der Bestellzusammenfassung mit denen des Berichts.

<u>Erwartete Ergebnisse</u>:

Die *[!UICONTROL Total Amount]*- und *[!UICONTROL Total Amount Actual]* umfassen sowohl *[!UICONTROL Discount Tax Compensation Amount]* als auch *[!UICONTROL Shipping Discount Tax Compensation Amount]*, wobei die Bestellzusammenfassung mit den Berichtsdaten abgeglichen wird.

<u>Tatsächliche Ergebnisse</u>:

Die Berichtsdaten zu Kundenaufträgen und Coupons stimmen nicht überein, da die *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* in den Berechnungen fehlen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

- Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
- Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) im Tools-Handbuch.
