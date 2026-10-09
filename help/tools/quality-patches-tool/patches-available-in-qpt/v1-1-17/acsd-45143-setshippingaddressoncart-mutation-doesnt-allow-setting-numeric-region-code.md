---
title: 'ACSD-45143: setShippingAddressesOnCart-Mutation setzt keinen numerischen Regionen-Code auf „region“'
description: Der Patch ACSD-45143 behebt das Problem, dass die Mutation setShippingAddressesOnCart das Festlegen des numerischen Regionen-Codes als „Region“ nicht zulässt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45143. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: c7d9d1f2-4731-406f-93bd-036f0fe75b1d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%
---
# ACSD-45143: setShippingAddressesOnCart-Mutation setzt keinen numerischen Regionen-Code auf „region“

Der Patch ACSD-45143 behebt das Problem, dass die Mutation setShippingAddressesOnCart das Festlegen des numerischen Regionen-Codes als „Region“ nicht zulässt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45143. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die setShippingAddressesOnCart-Mutation lässt das Festlegen des numerischen Regionen-Codes als „Region“ nicht zu.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie mithilfe der folgenden Abfrage einen Warenkorb.

   <pre>
    <code class="language-graphql">
    mutation {
      createEmptyCart
    }
    </code>
    </pre>

1. Senden Sie eine Anfrage, um die Versandadresse auf den Warenkorb festzulegen.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) {
      setShippingAddressesOnCart(
        input: {
          cart_id: $cartId
          shipping_addresses: {
            address: {
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            }
          }
        }
        ) {
          cart {
            shipping_addresses {
              firstname
              lastname
              company
              street
              city
              region {
                code
                label
              }
              postcode
              telephone
              country {
                code
                label
              }
            }
          }
        }
      }
      </code>
      </pre>

   Hinweis: Für den Länder-Code ist in diesem Beispiel „FR“ und für den Regionen-Code „58“ festgelegt. Nach der `directory_country_region` DB-Tabelle lautet der Regionscode 58 „Nièvre“.

1. Überprüfen Sie die zurückgegebene Antwort.

<u>Erwartete Ergebnisse</u>:

Adobe Commerce ermöglicht das Festlegen des numerischen Regions-Codes in der GraphQL-Anfrage.

<u>Tatsächliche Ergebnisse</u>:

Der Regions-Code wird in 47 geändert.

<pre>
<code class="language-graphql">
{
  "data": {
    "setShippingAddressesOnCart": {
      "cart": {
        "shipping_addresses": [
        {
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": [
          "234 Rue de Rivoli"
          ],
          "city": "Lille",
          "region": {
            "code": "47",
            "label": "Lot-et-Garonne"
            },
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": {
              "code": "FR",
              "label": "FR"
            }
          }
        ]
      }
    }
  }
}
</code>
</pre>

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
