---
title: 'ACSD-57643: Produkte mit benutzerdefinierten Optionen werden fälschlicherweise über GraphQL zum Warenkorb hinzugefügt'
description: Wenden Sie den Patch ACSD-57643 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte mit benutzerdefinierten Optionen fälschlicherweise über GraphQL zum Warenkorb hinzugefügt werden.
feature: Shopping Cart, GraphQL, Products
role: Admin, Developer
exl-id: 568f820b-ecab-4839-b32e-b0b42c1d2342
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-57643: Produkte mit benutzerdefinierten Optionen werden fälschlicherweise über GraphQL zum Warenkorb hinzugefügt

Der Patch ACSD-57643 behebt das Problem, dass Produkte mit benutzerdefinierten Optionen fälschlicherweise über GraphQL zum Warenkorb hinzugefügt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57643. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produkte mit benutzerdefinierten Optionen werden fälschlicherweise über GraphQL zum Warenkorb hinzugefügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein benutzerdefiniertes Optionsfeld für das Produkt.
1. Generieren Sie ein Kunden-Token mit GraphQL.
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

1. Sie werden sehen, dass das Produkt nur einmal hinzugefügt wird:

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

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
