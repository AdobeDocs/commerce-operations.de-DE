---
title: 'ACSD-57477: Die Verarbeitung von Verkaufsregeln verlangsamt die Leistung bei Warenkorbanfragen'
description: Wenden Sie den Patch ACSD-57477 an, um das Adobe Commerce-Problem zu beheben, bei dem in einem Projekt mit vielen verfügbaren Produktattributen (z. B. 1000 Attribute), wenn der GraphQL-Vorgang „AddProductsToCart“ mit Variablen ausgeführt wird, Commerce versucht, alle diese Produktattribute zu laden, und Probleme mit der langsamen Leistung des GraphQL-Vorgangs „AddProductsToCart“ verursacht.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477: Die Verarbeitung von Verkaufsregeln verlangsamt die Leistung bei Warenkorbanfragen

Der Patch ACSD-57477 behebt das Problem, dass die Verarbeitung von Verkaufsregeln bei Anfragen im Zusammenhang mit dem Warenkorb zu einer langsamen Leistung führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-57477. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.7 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Verarbeitung von Verkaufsregeln führt bei Anfragen zum Warenkorb zu langsamer Leistung, wenn Sie die Parameter als GraphQL-Variablen senden.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie 1.000 Produktattribute hinzu.
1. Erstellen Sie mithilfe der GraphQL-Abfrage unten einen Warenkorb.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. Fügen Sie mithilfe der folgenden GraphQL-Abfrage ein Produkt zum Warenkorb hinzu.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Legen Sie diese Variablen fest.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Dieses Problem tritt nur auf, wenn Sie die Parameter als GraphQL-Variablen senden. Wenn Sie die -Parameter in die GraphQL-Abfrage selbst einbeziehen, tritt dieses Problem nicht auf.
1. Senden Sie dieselbe **Zum Warenkorb hinzufügen**-Anfrage, nachdem Sie Parameter zur GraphQL-Abfrage selbst hinzugefügt haben.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Leistung des `AddProductsToCart` GraphQL-Vorgangs sollte nicht beeinträchtigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Leistung des `AddProductsToCart` GraphQL-Vorgangs verschlechtert sich, da alle Produktattribute geladen werden, wenn Parameter als Variablen gesendet werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
