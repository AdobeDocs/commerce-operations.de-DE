---
title: 'ACSD-45817: Die Mutation von GraphQL-Produkten bietet alle konfigurierbaren Varianten'
description: Der Patch ACSD-45817 behebt das Problem, dass eine GraphQL „products“-Mutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '491'
ht-degree: 0%
---
# ACSD-45817: Die Mutation von GraphQL-Produkten bietet alle konfigurierbaren Varianten

Mit dem Patch ACSD-45817 wird das Problem behoben, dass eine GraphQL-`products`-Mutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine GraphQL `products`-Mutation für einen bestimmten Store gibt alle konfigurierbaren Varianten zurück, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind.

<u>Voraussetzungen</u>:

Erstellen Sie eine zweite Website, einen zweiten Store und eine zweite Store-Ansicht.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei Unterprodukten: „configurable-a“ und „konfigurable-b“.
1. Weisen Sie beiden Websites das konfigurierbare Produkt zu.
1. Weisen Sie der zweiten Website nur eine Variante des Typs „konfigurierbar-a“ zu.
1. Wechseln Sie zur **Storefront**, zur zweiten Website und öffnen Sie das konfigurierbare Produkt.
1. Stellen Sie sicher, dass Sie nur eine untergeordnete Option sehen: „configurable-a“.
1. Ausführen einer GraphQL-Abfrage mit `POST: /graphql` Endpunkt und `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Variante „konfigurierbar-b“ ist der zweiten Website nicht zugewiesen und sollte in der Antwort nicht angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Variante „konfigurierbar-b“ wird in der Antwort angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
