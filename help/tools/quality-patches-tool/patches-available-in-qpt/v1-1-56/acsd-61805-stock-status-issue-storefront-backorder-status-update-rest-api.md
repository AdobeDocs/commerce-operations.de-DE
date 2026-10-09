---
title: 'ACSD-61805: Behebt Stock-Problem in der Storefront nach der Backorder-Statusaktualisierung über die REST-API'
description: Wenden Sie den Patch ACSD-61805 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte nicht vorrätig sind, nachdem der Status der Rückstandsbestellung über die REST-API aktualisiert wurde
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-61805: Behebt Stock-Problem in der Storefront nach der Backorder-Statusaktualisierung über die REST-API

Mit dem Patch ACSD-61805 wird das Problem behoben, dass Produkte in der Storefront nicht vorrätig sind, nachdem der Status der Rückstandsbestellung über die REST-API aktualisiert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-61805. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produkte bleiben in der Storefront nicht vorrätig, nachdem der Auftragsstatus über die REST-API aktualisiert wurde.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Instanz mit Beispieldaten.
1. Erstellen Sie eine neue Inventarquelle.
1. Erstellen Sie einen neuen Lagerbestand und weisen Sie ihm die neue Quelle zu.
1. Weisen Sie dem Produkt 24-MB01 die neue Quelle zu.
1. Legen Sie **[!UICONTROL Source Item Status]** für beide Produktquellen auf `In Stock` fest.
1. Stellen Sie die Menge (**[!UICONTROL QTY]**) für beide Produktmengen auf *0* ein.
1. Speichern Sie das Produkt.
1. Admin-Token von dieser Endpunkt-URL abrufen: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Aktualisieren Sie das Produkt mithilfe des Endpunkts `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Führen Sie die Cron-Aufträge zweimal aus (einmal zum Erstellen von Zeitplänen und einmal zum Ausführen des Zeitplans):

   ```shell
   bin/magento cron:run
   ```

1. Wechseln Sie zum Frontend und überprüfen Sie das Produkt.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte *Auf Lager*.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt ist *nicht vorrätig*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
