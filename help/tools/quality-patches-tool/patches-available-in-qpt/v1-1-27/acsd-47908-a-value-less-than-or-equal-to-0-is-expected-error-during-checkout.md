---
title: 'ACSD-47908: *Beim Auschecken wird ein Wert kleiner oder gleich 0 erwartet* Fehler'
description: Wenden Sie den Patch ACSD-47908 an, um den Adobe Commerce-Fehler zu beheben. *Es wird ein Wert kleiner oder gleich 0 erwartet, wenn Sie während des Checkouts die Quelle und Menge im Versandschritt auswählen.
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%
---
# ACSD-47908: *Es wird ein Wert kleiner oder gleich 0 erwartet* Fehler beim Auschecken

Der Patch ACSD-47908 behebt den Fehler *Ein Wert kleiner oder gleich 0 wird erwartet* wenn die Quelle und Menge im Versandschritt während des Checkouts ausgewählt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID ist ACSD-47908. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Auswahl der Quelle und Menge im Versandschritt während des Checkouts wird folgender Fehler ausgelöst: *Es wird ein Wert kleiner oder gleich 0 erwartet*.

<u>Voraussetzungen</u>:

Installieren Sie Adobe Commerce Inventory management (MSI)-Module.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** und konfigurieren Sie mehrere Quellen.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** und erstellen Sie ein neues Lager.
   * Weisen Sie nun die Quellen dem neuen Lager zu.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie mindestens ein Produkt.
   * Stellen Sie sicher, dass die Produkte den neuen Quellen zugewiesen sind, und geben Sie die verfügbare Menge an.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und erstellen Sie eine neue Bestellung.
1. Fügen Sie diese Produkte zur Bestellung hinzu und platzieren Sie sie.
1. Klicken Sie auf **[!UICONTROL Ship]**.
1. Quelle auswählen, von der aus geliefert werden soll.
1. Geben Sie die Menge jedes zu versendenden Artikels an.
1. Laden Sie die Seite neu.
1. Klicken Sie auf **[!UICONTROL Proceed to Shipment]**.

<u>Erwartete Ergebnisse</u>:

Die neue Sendungsseite wird ohne Fehler geöffnet.

<u>Tatsächliche Ergebnisse</u>:

* Die eingegebene Menge kann nicht validiert werden.
* Folgender Fehler wird ausgegeben: *Bitte einen Wert kleiner oder gleich 0 eingeben*.

  Der Fehler ist jedoch inkonsistent und tritt möglicherweise nicht immer auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
