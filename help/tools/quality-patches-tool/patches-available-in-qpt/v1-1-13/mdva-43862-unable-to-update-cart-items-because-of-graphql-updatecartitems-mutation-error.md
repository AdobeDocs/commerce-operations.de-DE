---
title: 'MDVA-43862: Kundin oder Kunde kann Artikel im Warenkorb aufgrund eines Fehlers in der GraphQL UpdateCartItems-Mutation nicht aktualisieren'
description: Der Patch MDVA-43862 löst das Problem, dass der Kunde die Warenkorbelemente aufgrund eines GraphQL UpdateCartItems-Mutationsfehlers nicht aktualisieren kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43862. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: GraphQL, Orders, Shopping Cart
role: Admin
exl-id: d8a2579f-58f5-4407-8006-d58794a84b1f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%
---
# MDVA-43862: Kundin oder Kunde kann Artikel im Warenkorb aufgrund eines Fehlers in der GraphQL UpdateCartItems-Mutation nicht aktualisieren

Der Patch MDVA-43862 löst das Problem, dass der Kunde die Warenkorbelemente aufgrund eines GraphQL UpdateCartItems-Mutationsfehlers nicht aktualisieren kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43862. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1, 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Kunde kann Warenkorbelemente aufgrund eines GraphQL-Fehlers der UpdateCartItems-Mutation nicht aktualisieren.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt (MH01), indem Sie ein einfaches (MH01-XL-Grey) zuweisen.
1. Navigieren Sie zu Commerce Admin > **Katalog** > **Produkte** > **SKU** > **MH01** > **Anpassbare Optionen**.
1. Fügen Sie dem Produkt eine benutzerdefinierte Option hinzu.
   * Optionstitel: Option1
   * Optionstyp: Feld
   * Erforderlich: Ja
   * Preis: 10.00
   * Preisart: Festpreis
   * SKU: MHC1
   * Max. Zeichen: 25
1. Führen Sie die folgende GraphQL-Abfrage aus, um die Warenkorb-ID zu generieren.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Notieren Sie sich den Warenkorb-ID-Code.
1. Führen Sie die folgende Abfrage aus, um das konfigurierbare Produkt zum Warenkorb hinzuzufügen:

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. Sie werden feststellen, dass der Warenkorb mit dem konfigurierbaren Element gefüllt ist.
1. Notieren Sie sich die zurückgegebene UID.
1. Führen Sie erneut die folgende Abfrage aus, um das Warenkorbelement zu aktualisieren.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Beobachten Sie die Antwort.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb wird ohne Probleme aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Es wird die folgende Fehlermeldung angezeigt:

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
