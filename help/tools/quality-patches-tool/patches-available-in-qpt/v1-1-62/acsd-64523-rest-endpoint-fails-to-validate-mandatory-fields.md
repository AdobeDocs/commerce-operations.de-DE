---
title: 'ACSD-64523: REST-Endpunkt kann Pflichtfelder nicht validieren'
description: Wenden Sie den Patch ACSD-64523 an, um das Problem zu beheben, dass der REST-Endpunkt "[V1/import/csv]" Pflichtfelder nicht validieren kann, sodass Produkte erstellt werden können, ohne die erforderlichen Pflichtfelder bereitzustellen.
feature: REST, Products, Admin Workspace
role: Admin, Developer
source-git-commit: 4bf9a5eb2e423f5981ee9234be57230a6dff3913
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# ACSD-64523: REST-Endpunkt kann Pflichtfelder nicht validieren

Mit dem Patch ACSD-64523 wird ein Problem behoben, bei dem der REST-Endpunkt [V1/import/csv] Pflichtfelder nicht validieren kann, sodass eine Produkterstellung ohne erforderliche Daten möglich ist. Um dies zu beheben, aktualisieren Sie die Autorisierungs-Kopfzeile. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 installiert ist. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der REST-Endpunkt `[V1/import/csv]` kann Pflichtfelder nicht validieren, sodass Produkte erstellt werden können, ohne diese Pflichtfelder bereitzustellen.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie die folgende Payload aus (aktualisieren Sie die Autorisierungs-Kopfzeile):

   ```
   curl --location 'http://<domain>/rest/default/V1/import/json' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: Bearer xxxxx' \
   --data '{
       "source": {
           "locale": "en_AU",
           "entity": "catalog_product",
           "behavior": "append",
           "validation_strategy": "validation-stop-on-errors",
           "allowed_error_count": 0,
           "items": [
               {
                   "sku": "product_sku",
                   "product_online": "no",
                   "attribute_set_code": "Default",
                   "product_type": "configurable",
                   "product_websites": "base",
                   "store_view_code": "default",
                   "name": null,
                   "description": null,
                   "short_description": null,
                   "weight": null,
                   "tax_class_name": null,
                   "visibility": null,
                   "price": null,
                   "url_key": null,
                   "cost": null,
                   "additional_attributes": {
                       "special_price": "",
                       "retail_price": ""
                   },
                   "configurable_variations": []
               }
           ]
       }
   }'
   ```

<u>Erwartete Ergebnisse</u>:

Die Anwendung sollte verhindern, dass ein Produkt ohne Pflichtfelder gespeichert wird.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wurde erfolgreich gespeichert, ohne den Produktnamen anzugeben, der ein erforderliches Attribut ist. Infolgedessen können wir nicht auf das Backend-Produktraster zugreifen, und es wird der folgende Fehler angezeigt.

`Warning: Undefined array key "name" in /app/code/Magento/Catalog/Ui/Component/Listing/Columns/Thumbnail.php on line 91`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
