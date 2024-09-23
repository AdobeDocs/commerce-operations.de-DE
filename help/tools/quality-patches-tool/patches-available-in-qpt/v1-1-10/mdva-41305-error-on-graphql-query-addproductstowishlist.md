---
title: "MDVA-41305: Error on GraphQL Query addProductsToWishlist for Configurable Products"
description: Der Patch MDVA-41305 behebt das Problem, dass Benutzer einen Fehler in der GraphQL-Abfrage "addProductsToWishlist"für konfigurierbare Produkte erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-41305. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-41305: Fehler bei GraphQL Query addProductsToWishlist für konfigurierbare Produkte

Der Patch MDVA-41305 behebt das Problem, bei dem Benutzer einen Fehler bei der GraphQL-Abfrage `addProductsToWishlist` für konfigurierbare Produkte erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-41305. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Benutzer konfigurierbare Produkte (mit/ohne Konfiguration) von GraphQL zur Wunschliste hinzufügen, können sie als Antwort keine konfigurierbaren SKUs und konfigurierbaren Optionen erhalten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt (mit Blau, Grau und einer benutzerdefinierten Option).
1. Öffnen Sie das Frontend, melden Sie sich als Kunde an und erstellen Sie eine Wunschliste (siehe wishlist_id).
1. Öffnen Sie Postman und erstellen Sie ein Kunden-Token:

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(email: "", password: "") {
        token
      }
     }
     </code>
     </pre>

1. Legen Sie dieses Token für die Bearer-Autorisierung fest.
1. Versuchen Sie, der Wunschliste ein konfigurierbares Produkt *Blue* mit den folgenden Anweisungen hinzuzufügen:

<pre>
<code class="language-graphql">
mutation {
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: [
     {
       sku: "conf2"
       selected_options: [
            "Y29uZmlndXJhYmxlLzkzLzUw"
       ]
       quantity: 1
       entered_options: [
         {
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         }
       ]
     }
    ]
  ) {
    wishlist {
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) {
        items {
         id
         quantity
         ... on ConfigurableWishlistItem  {
           child_sku
           customizable_options {
             customizable_option_uid
           }
         }
         product {
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface {
             options {
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption {
                value {
                  uid
                  sku
                  price
                  price_type
                  max_characters
                }
              }
            }
          }
          price_range {
            minimum_price {
              regular_price {
                currency
                value
              }
            }
            maximum_price {
               regular_price {
                 currency
                 value
               }
             }
           }
         }
       }
     }
   }
  user_errors {
    code
    message
   }
 }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Benutzer können eine Reihe konfigurierter Produktoptionen in der Antwort sehen, die in der Payload angegeben und der Wunschliste hinzugefügt wurde.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten als Antwort einen *internen Server-Fehler*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
