---
title: 'ACSD-62146: Die ausgewählte Rechnungsadresse verschwindet auf der Zahlungsseite der Kasse'
description: Wenden Sie den Patch ACSD-62146 an, um das Adobe Commerce-Problem zu beheben, bei dem die ausgewählte Rechnungsadresse auf der Kaufbestätigungsseite ausgeblendet wird, wenn die Adresssuche aktiviert ist und das Limit für die Anzahl der Kundenadressen auf 1 festgelegt ist.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 2a2f1afe-8a48-4beb-b78d-a894b685717d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%
---
# ACSD-62146: Die ausgewählte Rechnungsadresse verschwindet auf der Zahlungsseite der Kasse

Der Patch ACSD-62146 behebt das Problem, dass die ausgewählte Rechnungsadresse auf der Zahlungsseite der Kasse verschwindet, wenn die Adresssuche aktiviert ist und die [!UICONTROL Number of Customer Addresses Limit] auf 1 gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-62146. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die ausgewählte Rechnungsadresse verschwindet auf der Kaufbestätigungsseite, wenn die Adresssuche aktiviert ist und die **[!UICONTROL Number of Customer Addresses Limit]** auf 1 gesetzt ist.

<u>Schritte zur Reproduktion</u>:

1. Um die Adresssuche zu aktivieren, gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
1. Setzen Sie **[!UICONTROL Number of Customer Addresses Limit]** auf 1.
1. Erstellen Sie einen Kunden und fügen Sie zwei verschiedene Adressen hinzu.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
1. Klicken Sie auf **[!UICONTROL Change Address]** und verwenden Sie das Popup-Fenster, um die Adresse zu ändern.
1. Wählen Sie als Lieferadresse die Adresse 2 aus.
1. Klicken Sie auf **[!UICONTROL Next]** , um mit dem Zahlungsschritt fortzufahren.
1. Überprüfen Sie, ob die Rechnungs- und Lieferadresse identisch sind.
1. Aktualisieren Sie die Seite, ohne die Zahlung vorzunehmen.

<u>Erwartete Ergebnisse</u>:

Die Lieferadresse wird angezeigt, wenn die Rechnungs- und Lieferadressen identisch sind.

<u>Tatsächliche Ergebnisse</u>:

Standardmäßige Rechnungsadresse und ausgewählte Lieferadresse sind nicht sichtbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
