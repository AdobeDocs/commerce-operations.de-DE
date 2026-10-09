---
title: 'MDVA-39993: Inventaränderungen, die über API durchgeführt werden, werden nicht in der Storefront angezeigt'
description: Mit dem Patch MDVA-39993 wird das Problem behoben, dass die Inventaränderungen, die über die API vorgenommen werden, nicht in der Storefront angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39993. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%
---
# MDVA-39993: Inventaränderungen, die über API durchgeführt werden, werden nicht in der Storefront angezeigt

Mit dem Patch MDVA-39993 wird das Problem behoben, dass die Inventaränderungen, die über die API vorgenommen werden, nicht in der Storefront angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39993. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.3.7-p2 und 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die über die API vorgenommenen Bestandsänderungen werden nicht auf der Storefront-Produktseite angezeigt.

<u>Voraussetzungen</u>:

Installierte Inventarmodule.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass die Warteschlange so eingestellt ist, dass sie mit cron ausgeführt wird und cron installiert und ausgeführt wird.
1. Erstellen Sie ein konfigurierbares Produkt (COC001) mit zwei Farben (Schwarz und Rot) und zwei Größen (M und L).
1. Mache eine Option nicht vorrätig (COC001-Red-M).
1. Laden Sie die konfigurierbare Produktseite in die Storefront und versuchen Sie, auf jede Farbe zu klicken. Wenn Sie auf **Rot** klicken, **die Größe M** durchgestrichen werden, da sie nicht vorrätig ist.
1. Stellen Sie COC001-Red-M mit dem folgenden API-Endpunkt und der Payload auf Lager:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Überprüfen Sie dieses einfache Produkt vom Backend und überprüfen Sie, ob es auf Lager aktualisiert wurde.
1. Laden Sie das konfigurierbare Produkt aus dem Frontend und klicken Sie auf jede Farbe. Beachten Sie die Größe **M**, wenn Sie auf **Rot** klicken.

<u>Erwartete Ergebnisse</u>:

Die Option COC001-Red-M ist nicht durchgestrichen, da wir sie über die API auf Lager aktualisiert haben.

<u>Tatsächliche Ergebnisse</u>:

COC001-Red-M Option ist noch gestrichen, obwohl es auf Lager ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
