---
title: 'ACSD-45817: Die GraphQL-Produktmutation liefert alle konfigurierbaren Varianten'
description: Der Patch ACSD-45817 behebt das Problem, dass eine GraphQL-Mutation "products"für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-45817: Die GraphQL-Produktmutation liefert alle konfigurierbaren Varianten

Der Patch ACSD-45817 behebt das Problem, dass eine GraphQL `products` -Mutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der nicht dem angeforderten Store zugewiesenen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine GraphQL `products` -Mutation für einen bestimmten Store gibt alle konfigurierbaren Varianten zurück, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind.

<u>Voraussetzungen</u>:

Erstellen Sie eine zweite Website, einen zweiten Store und eine zweite Store-Ansicht.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei Unterprodukten: &quot;konfigurable-a&quot;und &quot;configuring-b&quot;.
1. Weisen Sie das konfigurierbare Produkt beiden Websites zu.
1. Weisen Sie der zweiten Website nur eine &quot;konfigurierbare a&quot;-Variante zu.
1. Wechseln Sie zur **Storefront**, wechseln Sie zur zweiten Website und öffnen Sie das konfigurierbare Produkt.
1. Stellen Sie sicher, dass nur eine untergeordnete Option angezeigt wird: &quot;konfigurierbar-a&quot;.
1. Führen Sie eine GraphQL-Abfrage mit dem Endpunkt `POST: /graphql` und dem Endpunkt `Headers: "store" = "new"` aus

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

Die &quot;konfigurierbare b&quot;-Variante wird der zweiten Website nicht zugewiesen und sollte nicht in der Antwort angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Variante &quot;konfigurierbar-b&quot;wird in der Antwort angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
