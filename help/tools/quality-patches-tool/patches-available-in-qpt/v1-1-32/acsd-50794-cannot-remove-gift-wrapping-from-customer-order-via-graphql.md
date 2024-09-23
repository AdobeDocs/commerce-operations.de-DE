---
title: "ACSD-50794: Kann Geschenkverpackungen nicht aus Kundenbestellung über GraphQL entfernen."
description: Wenden Sie den Patch ACSD-50794 an, um das Adobe Commerce-Problem zu beheben, bei dem Benutzer die Geschenkverpackung nicht aus der Kundenbestellung über GraphQL entfernen können.
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: Geschenkverpackung kann nicht aus der Kundenbestellung über GraphQL entfernt werden

Der Patch ACSD-50794 behebt das Problem, dass Benutzer keine Geschenkverpackung aus der Kundenbestellung über GraphQL entfernen können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-50794. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können die Geschenkverpackung nicht über GraphQL aus der Kundenbestellung entfernen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden über das Frontend.
1. Erstellen Sie ein einfaches Produkt.
1. Aktivieren Sie *[!UICONTROL Gift Messages]*, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** gehen und *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]* festlegen.
1. Erstellen Sie *[!UICONTROL Gift Wrapping]*, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]** gehen.
1. Kundentoken abrufen.
1. Erstellen Sie einen leeren Warenkorb customerCart.
   * Produkte zum Warenkorb hinzufügen: `addProductsToCart` Mutation
   * Rechnungsadresse festlegen: `setBillingAddressOnCart` Mutation
   * Lieferadresse festlegen: `setShippingAddressesOnCart` Mutation
   * Versandmethode festlegen: `setShippingMethodsOnCart` Mutation (Floatrate)
   * Zahlungsmethode festlegen: `setPaymentMethodOnCart` Mutation (checkmo)
1. Überprüfen Sie nun die Geschenkverpackung *Uid* mit dieser Warenkorbabfrage:

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Setzen Sie die Geschenkverpackung mit `setGiftOptionsOnCart` ein.
1. Überprüfen Sie die Warenkorbabfrage.
1. Heben Sie die Geschenkverpackung mit &quot;`setGiftOptionsOnCart`&quot; auf (legen Sie den Wert auf null fest).
1. Überprüfen Sie erneut die Abfrage zum Warenkorb: Warenkorb .
1. Reihenfolge festlegen: `placeOrder` Mutation.
1. Kundenabfrage ausführen: Kunde.

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

Sobald ein Benutzer einen Geschenkpacker festlegt und ihn aufhebt, gibt die Kundenabfrage null zurück.

<u>Tatsächliche Ergebnisse</u>:

Die Kundenabfrage gibt nach wie vor eine Geschenkverpackung zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
