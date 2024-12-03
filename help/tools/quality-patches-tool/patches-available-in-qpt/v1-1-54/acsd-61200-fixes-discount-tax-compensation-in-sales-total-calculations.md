---
title: 'ACSD-61200: Korrekturen des Rabattsteuerausgleichs bei der Berechnung der Verkaufssumme'
description: Wenden Sie den Patch ACSD-61200 an, um das Adobe Commerce-Problem zu beheben, bei dem *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* bei Berechnungen der Verkaufsgesamtwerte fehlen, was zu Diskrepanzen zwischen den Daten der Verkaufsaufträge und den Gutscheinberichten führt.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
source-git-commit: 2e82c935145d71d0c66c531003fa51f564da6e41
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: Korrekturen des Rabattsteuerausgleichs bei der Berechnung der Verkaufssumme

Der Patch ACSD-61200 behebt das Problem, dass *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* bei den Berechnungen *[!UICONTROL Total Amount]* und *[!UICONTROL Total Amount Actual]* fehlen, was zu Diskrepanzen zwischen den Daten von Verkaufsbestellungen und den Gutscheinberichten führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61200. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

- Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

- Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ungenauigkeiten bei den Daten zu Verkaufsbestellungen und Gutscheinberichten aufgrund fehlender Werte für *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* in den Berechnungen der Verkaufsgesamtwerte.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine [!UICONTROL Tax Zone] und eine [!UICONTROL Tax Rule].
1. Legen Sie die folgenden Steuerkonfigurationen fest:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Aktualisieren Sie die folgenden Anzeigeeinstellungen für Bestellungen, Rechnungen und Kreditkarten:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Erstellen Sie eine [!UICONTROL Cart Price Rule] mit einem Gutschein für einen 10-%-Rabatt.
1. Führen Sie eine Bestellung mit dem Gutschein aus und generieren Sie eine Rechnung und eine Sendung.
1. Gehen Sie zu **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** und generieren Sie einen Bericht.
1. Vergleichen Sie die Daten in der Bestellübersicht mit denen des Berichts.

<u>Erwartete Ergebnisse</u>:

Die Berechnungen *[!UICONTROL Total Amount]* und *[!UICONTROL Total Amount Actual]* enthalten sowohl *[!UICONTROL Discount Tax Compensation Amount]* als auch *[!UICONTROL Shipping Discount Tax Compensation Amount]*, wobei die Bestellzusammenfassung mit den Berichtsdaten übereinstimmt.

<u>Tatsächliche Ergebnisse</u>:

Die Daten zu Verkaufsbestellungen und Gutscheinberichten stimmen nicht überein, da die *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* in den Berechnungen fehlen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

- Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
- Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) im Tools-Handbuch.
