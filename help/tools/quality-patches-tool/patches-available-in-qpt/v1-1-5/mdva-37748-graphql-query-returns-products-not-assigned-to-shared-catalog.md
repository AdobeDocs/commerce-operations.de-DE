---
title: 'MDVA-37748: GraphQL-Abfrage gibt Produkte zurück, die keinem freigegebenen Katalog zugewiesen sind'
description: Der Patch MDVA-37748 behebt das Problem, dass eine GraphQL-Abfrage Produkte zurückgibt, die keinem freigegebenen Katalog zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-37748. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
exl-id: 8aa00953-dbf0-4533-9b53-b809bf59ec20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-37748: GraphQL-Abfrage gibt Produkte zurück, die keinem freigegebenen Katalog zugewiesen sind

Der Patch MDVA-37748 behebt das Problem, dass eine GraphQL-Abfrage Produkte zurückgibt, die keinem freigegebenen Katalog zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-37748. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL-Abfrage gibt Produkte zurück, die keinem freigegebenen Katalog zugewiesen sind.

<u>Voraussetzungen</u>:

B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Produkte und weisen Sie sie einer Kategorie zu:
   * Produkt 1: Öffentlich
   * Produkt 2

1. Weisen Sie „Produkt 1 - Öffentlich“ dem freigegebenen Katalog „Standard (Allgemein)“ zu.
1. Erstellen Sie einen zusätzlichen benutzerdefinierten freigegebenen Katalog und weisen Sie ihn „Produkt 2“ zu.
1. Erstellen Sie eine neue Firma und weisen Sie sie dem zusätzlichen freigegebenen Katalog zu, der in Schritt 3 erstellt wurde.
1. Überprüfen Sie nach der Cron-Ausführung/-Neuindizierung im Frontend, ob Sie „Produkt 1 - Öffentlich“ sehen können, wenn Sie nicht angemeldet sind.
1. Melden Sie sich als Administrator des in Schritt 4 erstellten Unternehmens an und stellen Sie sicher, dass nur „Produkt 2“ angezeigt wird.
1. Anfordern eines Autorisierungs-Tokens mithilfe der folgenden GraphQL-Abfrage:

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) {
        token
      }
    }
    </code>
    </pre>

1. Fügen Sie die Kopfzeile **Autorisierungsanbieter-Wert des Tokens“ hinzu** führen Sie die folgende GraphQL-Abfrage aus:

   <pre>
    <code class="language-graphql">
    {
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) {
          total_count
          page_info {
            page_size
            current_page
          }
          aggregations {
            attribute_code
            count
            label
            options {
              label
              value
              count
            }
          }
          items {
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers{
              final_price{
                  value
                  currency
                }
              discount{
                  amount_off
                  percent_off
                }
              quantity
            }
            price_range {
             maximum_price {
              regular_price {
                value
              }
              final_price {
                value
              }
            }
            minimum_price {
              regular_price {
                value
              }
              final_price {
               value
              }
            }
          }
          image {
           url
          }
          thumbnail {
           url
          }
          small_image {
           url
          }
          media_gallery {
           url
          }
          ... on ConfigurableProduct {
            configurable_options {
             id

             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
               swatch_data {
                 value
               }
            }
            product_id
          }
          variants {
            product {
              id
              name
              sku
              #margin
              #margin_percentage
              image {
                url
              }
              small_image {
                url
              }
              thumbnail {
                url
              }
              media_gallery{
                url
              }
              attribute_set_id
              ... on PhysicalProductInterface {
                weight
              }
              price_range {
                minimum_price {
                  regular_price {
                    value
                    currency
                  }
                }
              }
            }
            attributes {
              label
              code
              value_index
            }
          }
        }
      }

    }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Die Anzahl und das von GraphQL zurückgegebene Produkt berücksichtigen nur das Produkt, das dem freigegebenen Katalog zugewiesen ist, der mit dem angemeldeten Benutzer verknüpft ist.

<u>Tatsächliche Ergebnisse</u>:

Nur „Produkt 2“ wird zurückgegeben, aber die `total_count` zeigt zwei.

<pre>
<code class="language-graphql">
{
  "data": {
    "products": {
      "total_count": 2,
      "page_info": {
        "page_size": 100,
        "current_page": 1
      },
      "aggregations": [
        {
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": [
            {
              "label": "0-100",
              "value": "0_100",
              "count": 1
            },
            {
              "label": "100-200",
              "value": "100_200",
              "count": 1
            }
          ]
        },
        {
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": [
            {
              "label": "Cat 1",
              "value": "3",
              "count": 2
            }
          ]
        }
      ],
      "items": [
        {
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": {
            "html": ""
          },
          "short_description": {
            "html": ""
          },
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": [
            {
              "final_price": {
                "value": 90,
                "currency": "USD"
              },
              "discount": {
                "amount_off": 10,
                "percent_off": 10
              },
              "quantity": 1
            }
          ],
          "price_range": {
            "maximum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            },
            "minimum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            }
          },
          "image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          },
          "thumbnail": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          },
          "small_image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          },
          "media_gallery": []
        }
      ]
    }
  }
}
</code>
</pre>

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
