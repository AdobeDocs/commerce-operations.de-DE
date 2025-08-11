---
title: 'ACSD-66072: GraphQL kann verwandte Produkte nicht auf der Produktdetailseite zurückgeben'
description: Wenden Sie den Patch ACSD-66072 an, um das Adobe Commerce-Problem zu beheben, bei dem verwandte Produkte aufgrund eines internen Serverfehlers nicht über GraphQL auf der Produktdetailseite zurückgegeben werden, wenn die entsprechenden Produktregeln konfiguriert sind.
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1cd5383d774ab0ed97b80a4abf7df5706706ea5
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66072: GraphQL kann verwandte Produkte nicht auf der Produktdetailseite zurückgeben

Mit dem Patch ACSD-66072 wird das Problem behoben, dass verwandte Produkte aufgrund eines internen Serverfehlers bei der Konfiguration von **[!UICONTROL Related Products Rule]** nicht über GraphQL auf der Produktdetailseite zurückgegeben werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66072. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.9 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Verwandte Produkte werden aufgrund eines internen Server-Fehlers bei der Konfiguration von **[!UICONTROL Related Products Rule]** nicht über GraphQL auf der Produktdetailseite zurückgegeben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie konfigurierbare Produkte:
   * **Produkt 1**: `config1` mit `option1`
   * **Produkt 2**: `config2` mit `option2`

1. Erstellen und Zuweisen von Produkten zu einer Kategorie
   * Erstellen Sie eine **neue Kategorie**.
   * Weisen Sie dieser Kategorie beide Produkte (`config1` und `config2`) zu.

1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]** und erstellen Sie dann eine neue Regel mit den folgenden Einstellungen:

   * **[!UICONTROL Priority]**: 1
   * **[!UICONTROL Applies To]**: **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**: 10
   * **[!UICONTROL Products to Match]**: **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**: `Product Category is the Same as Matched Product Categories`

1. Führen Sie die folgenden Magento-CLI-Befehle aus:

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. Senden Sie eine POST-Anfrage an `../graphql` mit der folgenden Payload:

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>Erwartete Ergebnisse</u>:

Die Abfrage gibt das zugehörige Produkt zurück (`config1`).

<u>Tatsächliche Ergebnisse</u>:

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

Die `var/log/exception.log` enthält:

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
