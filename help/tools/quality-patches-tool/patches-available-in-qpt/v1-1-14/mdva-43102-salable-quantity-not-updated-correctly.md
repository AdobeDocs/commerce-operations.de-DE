---
title: 'MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert'
description: Der MDVA-43102 Patch behebt das Problem, dass die verkaufbare Menge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%
---
# MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert

Der MDVA-43102 Patch behebt das Problem, dass die verkaufbare Menge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die verkaufbare Menge wird nicht korrekt aktualisiert, wenn eine Rückerstattung mithilfe der REST-API erfolgt.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie dem Warenkorb einen Artikel hinzu.
1. Überprüfen Sie die Lagermenge und die verkaufbare Menge.
1. Erstellen Sie eine Bestellung.
1. Erstellen Sie bei Bedarf eine Rechnung.
1. Senden Sie eine REST-Anfrage, um die Rechnung mit der folgenden Payload zurückzuerstatten:

   * Offline-Methode/Bestellung/`<order_id>`/Rückerstattung
   * Online-Methode/Rechnung/`<invoice_id>`/Rückerstattung

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Die Artikel nicht versenden.
1. Vergleichen Sie die Lagermenge mit der Verkaufsmenge von zuvor. Sie sollten beide um denselben Betrag aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die verkaufsfähige Menge wird korrekt aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung ausgestellt wird und das Produkt an den Lagerbestand zurückgegeben wird.

<u>Tatsächliche Ergebnisse</u>:

Die Verkaufsmenge wird nicht aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung ausgestellt wird und das Produkt an den Lagerbestand zurückgegeben wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
