---
title: 'ACSD-50794: Geschenkverpackung kann nicht von der Kundenbestellung über GraphQL entfernt werden'
description: Wenden Sie den Patch ACSD-50794 an, um das Adobe Commerce-Problem zu beheben, bei dem Benutzende Geschenkverpackungen nicht über GraphQL aus der Kundenbestellung entfernen können.
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-50794: Geschenkverpackung kann nicht von der Kundenbestellung über GraphQL entfernt werden

Mit dem Patch ACSD-50794 wird das Problem behoben, dass Benutzende Geschenkverpackungen nicht über GraphQL aus der Kundenbestellung entfernen können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-50794. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können Geschenkverpackungen nicht über GraphQL aus der Kundenbestellung entfernen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Kunden aus dem Frontend.
1. Erstellen Sie ein einfaches Produkt.
1. Aktivieren Sie *[!UICONTROL Gift Messages]*, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** wechseln und *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]* festlegen.
1. Erstellen Sie *[!UICONTROL Gift Wrapping]* über **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Kunden-Token abrufen.
1. Erstellen Sie einen leeren Warenkorb, customerCart.
   * Fügen Sie Produkte zum Warenkorb hinzu: `addProductsToCart` Mutation
   * Rechnungsadresse festlegen: `setBillingAddressOnCart` Mutation
   * Lieferadresse festlegen: `setShippingAddressesOnCart` Mutation
   * Versandmethode festlegen: `setShippingMethodsOnCart` Mutation (Flatrate)
   * Zahlungsmethode festlegen: `setPaymentMethodOnCart` Mutation (checkmo)
1. Überprüfen Sie nun mit dieser Warenkorbabfrage *Geschenkverpackung* UID):

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Geschenkverpackung mit `setGiftOptionsOnCart` festlegen.
1. Überprüfen Sie den Warenkorb: Warenkorbabfrage.
1. Geschenkverpackung mit `setGiftOptionsOnCart` aufheben (Wert auf null setzen).
1. Überprüfen Sie erneut den Warenkorb: Warenkorbabfrage.
1. Place order: `placeOrder` Mutation.
1. Führen Sie die Kundenabfrage aus: customer.

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Sobald ein Benutzer einen Geschenkumbruch einstellt und aufhebt, gibt die Kundenabfrage null zurück.

<u>Tatsächliche Ergebnisse</u>:

Die Kundenabfrage gibt weiterhin den angewendeten Geschenkumbruch zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
