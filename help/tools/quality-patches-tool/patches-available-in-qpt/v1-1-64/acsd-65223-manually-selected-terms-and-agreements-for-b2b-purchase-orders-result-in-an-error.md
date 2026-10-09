---
title: 'ACSD-65223: Manuell ausgewählte Bedingungen für B2B-Bestellungen führen zu einem Fehler'
description: Wenden Sie den ACSD-65223 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem mit [!UICONTROL Purchase Orders] erstellte Bestellungen nicht mit Online-Zahlungsmethoden wie Kreditkarten abgeschlossen werden können, wenn für den Checkout Bedingungen erforderlich sind.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '457'
ht-degree: 0%
---
# ACSD-65223: Manuell ausgewählte Bedingungen für B2B-Bestellungen führen zu einem Fehler

Der Patch von ACSD-65223 behebt das Problem, dass mit **[!UICONTROL Purchase Orders]** erstellte Bestellungen nicht mit Online-Zahlungsmethoden wie Kreditkarten abgeschlossen werden können, wenn für den Checkout Bedingungen erforderlich sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-65223.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) B2B 1.5.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) B2B 1.5.1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn für eine Bestellung Geschäftsbedingungen erforderlich sind und Sie versuchen, eine mit [!UICONTROL Purchase Orders] erstellte Bestellung abzuschließen, kann die Bestellung nicht über Online-Zahlungsmethoden wie Kreditkarten aufgegeben werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** und wählen Sie **[!UICONTROL B2B Features]**.
1. Legen Sie **[!UICONTROL Enable Company]** und **[!UICONTROL Enable Purchase Orders]** auf *Ja* fest.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** und erstellen Sie eine neue Bedingung. Legen Sie **[!UICONTROL Applied]** auf *[!UICONTROL Manually]* fest.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** und setzen Sie **[!UICONTROL Enable Terms and Conditions]** auf *Ja*.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** und konfigurieren Sie [!DNL Braintree].
1. Erstellen Sie in der Storefront eine Firma.
1. Navigieren Sie in der Admin-Liste zu **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.
1. Genehmigen Sie das Unternehmen und lassen Sie **[!UICONTROL Purchase Orders]** zu.
1. Melden Sie sich am Frontend beim Konto an.
1. Fügen Sie dem Warenkorb einen Artikel hinzu.
1. Bestellen Sie mit **[!UICONTROL Purchase Order]**.
1. Klicken Sie im Kunden-Dashboard auf die Registerkarte **[!UICONTROL Purchase Orders]** .
1. Erstellen Sie eine Bestellung aus der neuen Bestellung. Wählen Sie dann Kreditkarte als Zahlungsmethode.
1. Stimmen Sie den Nutzungsbedingungen zu.
1. Bestellung aufgeben.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung über eine Online-Zahlungsmethode für genehmigte Bestellungen aufgeben, wenn für den Checkout Bedingungen erforderlich sind.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung über eine Online-Zahlungsmethode für genehmigte Bestellungen aufgeben, wenn für den Checkout Bedingungen erforderlich sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
