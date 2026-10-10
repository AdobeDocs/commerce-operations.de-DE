---
title: 'MDVA-41305: Fehler bei GraphQL Query addProductsToWishlist für konfigurierbare Produkte'
description: Der Patch MDVA-41305 löst das Problem, dass Benutzende einen Fehler in der GraphQL-Abfrage „addProductsToWishlist“ für konfigurierbare Produkte erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-41305. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: 985c3c46-d2c8-4479-b9e4-e5f9504ab03b
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
source-wordcount: '466'
ht-degree: 0%
---
# MDVA-41305: Fehler bei GraphQL Query addProductsToWishlist für konfigurierbare Produkte

Der Patch MDVA-41305 löst das Problem, dass Benutzende einen Fehler in GraphQL Query `addProductsToWishlist` für konfigurierbare Produkte erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-41305. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Benutzende von GraphQL konfigurierbare Produkte (mit/ohne Konfiguration) zur Wunschliste hinzufügen, können sie als Antwort keine konfigurierbaren SKUs und konfigurierbaren Optionen abrufen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt (mit einer blauen, grauen und einer benutzerdefinierten Option).
1. Öffnen Sie das Frontend, melden Sie sich als Kunde an und erstellen Sie eine Wunschliste (check wishlist_id).
1. Öffnen Sie Postman und erstellen Sie ein Kunden-Token:

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(email: "", password: "") &lbrace;
        token
      &rbrace;
     &rbrace;
     </code>
     </pre>

1. Legen Sie dieses Token für die Bearer-Autorisierung fest.
1. Versuchen Sie, ein konfigurierbares Produkt *Blau* zur Wunschliste hinzuzufügen, indem Sie folgende Anweisungen befolgen:

<pre>
<code class="language-graphql">
mutation &lbrace;
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: &lbrack;
     &lbrace;
       sku: "conf2"
       selected_options: &lbrack;
            "Y29uZmlndXJhYmxlLzkzLzUw"
       &rbrack;
       quantity: 1
       entered_options: &lbrack;
         &lbrace;
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         &rbrace;
       &rbrack;
     &rbrace;
    &rbrack;
  ) &lbrace;
    wishlist &lbrace;
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) &lbrace;
        items &lbrace;
         id
         quantity
         ... on ConfigurableWishlistItem  &lbrace;
           child_sku
           customizable_options &lbrace;
             customizable_option_uid
           &rbrace;
         &rbrace;
         product &lbrace;
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface &lbrace;
             options &lbrace;
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption &lbrace;
                value &lbrace;
                  uid
                  sku
                  price
                  price_type
                  max_characters
                &rbrace;
              &rbrace;
            &rbrace;
          &rbrace;
          price_range &lbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                currency
                value
              &rbrace;
            &rbrace;
            maximum_price &lbrace;
               regular_price &lbrace;
                 currency
                 value
               &rbrace;
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
  user_errors &lbrace;
    code
    message
   &rbrace;
 &rbrace;
&rbrace;
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Benutzer können eine Reihe konfigurierter Produktoptionen in der Antwort sehen, die in der Payload angegeben und zur Wunschliste hinzugefügt wurde.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten als Antwort *Interner Server* Fehler.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
