---
title: 'ACSD-57643: Produkte mit benutzerdefinierten Optionen werden fälschlicherweise über GraphQL zum Warenkorb hinzugefügt'
description: Wenden Sie den Patch ACSD-57643 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte mit benutzerdefinierten Optionen fälschlicherweise über GraphQL zum Warenkorb hinzugefügt werden.
feature: Shopping Cart, GraphQL, Products
role: Admin, Developer
exl-id: 568f820b-ecab-4839-b32e-b0b42c1d2342
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-57643: Produkte mit benutzerdefinierten Optionen werden fälschlicherweise über GraphQL zum Warenkorb hinzugefügt

Der Patch ACSD-57643 behebt das Problem, dass Produkte mit benutzerdefinierten Optionen fälschlicherweise über GraphQL zum Warenkorb hinzugefügt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57643. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produkte mit benutzerdefinierten Optionen werden fälschlicherweise über GraphQL zum Warenkorb hinzugefügt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein benutzerdefiniertes Feld vom Typ „Option“ für das Produkt.
1. Generieren eines Kunden-Tokens mit GraphQL.
1. Erstellen Sie einen leeren Warenkorb.
1. Fügen Sie das Produkt mithilfe der folgenden Payload zum Warenkorb hinzu:

   ```graphql
   mutation {
     addProductsToCart(
       cartId: "wNVOTaE6sDCJoObZCCqikHQI3GyFaVif"
       cartItems: [
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product1 option1 "
           }]
         },
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product2 option1"
           }]
         }
         {
           quantity: 3
           sku: "24-MB01",
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x"
             value:"product3 option1"
           }]        
         }
       ]
     ) {
       cart {
         items {
           product {
             name
             sku
           }
           ... on SimpleCartItem {
             customizable_options {
               customizable_option_uid
               label
               values {
                 customizable_option_value_uid
                 value
               }
             }
           }
           quantity
         }
       }
       user_errors {
         code
         message
       }
     }
   }
   ```

1. Das Produkt wird nur einmal hinzugefügt:

   ```json
   {
     "data": {
       "addProductsToCart": {
         "cart": {
           "items": [
             {
               "product": {
                 "name": "Joust Duffle Bag",
                 "sku": "24-MB01"
               },
               "customizable_options": [
                 {
                   "customizable_option_uid": "Y3VzdG9tLW9wdGlvbi8x",
                   "label": "Option1",
                   "values": [
                     {
                       "customizable_option_value_uid": "Y3VzdG9tLW9wdGlvbi8x",
                       "value": "product1 option1"
                     }
                   ]
                 }
               ],
               "quantity": 5
             }
           ]
         },
         "user_errors": []
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Ein Produkt kann mit verschiedenen benutzerdefinierten Optionen für dieselbe SKU gleichzeitig zum Warenkorb hinzugefügt werden.

<u>Tatsächliche Ergebnisse</u>:

Es ist nicht möglich, ein Produkt mit verschiedenen benutzerdefinierten Optionen für dieselbe SKU gleichzeitig zum Warenkorb hinzuzufügen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
