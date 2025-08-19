---
title: 'ACSD-62146: Die ausgewählte Rechnungsadresse verschwindet auf der Zahlungsseite der Kasse'
description: Wenden Sie den Patch ACSD-62146 an, um das Adobe Commerce-Problem zu beheben, bei dem die ausgewählte Rechnungsadresse auf der Kaufbestätigungsseite ausgeblendet wird, wenn die Adresssuche aktiviert ist und das Limit für die Anzahl der Kundenadressen auf 1 festgelegt ist.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
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
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
