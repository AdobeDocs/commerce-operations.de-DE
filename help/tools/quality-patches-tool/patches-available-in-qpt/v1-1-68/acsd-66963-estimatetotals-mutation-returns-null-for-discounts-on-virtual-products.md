---
title: 'ACSD-66963: Mutation „estimatedTotals“ gibt für Rabatte auf virtuelle Produkte null zurück'
description: Wenden Sie den Patch ACSD-66963 an, um das Adobe Commerce-Problem zu beheben, bei dem „estimatedTotals“ bei Rabatten *null* zurückgibt, wenn ein Rabattcode auf einen Warenkorb mit nur virtuellen Produkten angewendet wird.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963: `estimateTotals`-Mutation gibt für Rabatte auf virtuelle Produkte null zurück

Der Patch ACSD-66963 behebt das Problem, dass `estimateTotals` bei Rabatten *null* zurückgibt, wenn ein Rabattcode auf einen Warenkorb mit nur virtuellen Produkten angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66963. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `estimateTotals`-Mutation gibt *null* für Rabatte zurück, wenn ein Rabattcode auf einen Warenkorb angewendet wird, der nur virtuelle Produkte enthält.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Warenkorb, der nur virtuelle Produkte enthält.
1. Rabattcode anwenden:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Rabattinformationen sind für Warenkörbe enthalten, die nur virtuelle Produkte enthalten.

    &quot;
    &lbrace;
    „data“: &lbrace;
    „estimatedTotals“: &lbrace;
    „cart“: &lbrace;
    „prices“: &lbrace;
    „rabatte“: &lbrack;
    &lbrace;
    „amount“: &lbrace;
    „value“: 100.5,
    „currency“: „USD“
    &rbrace;,
    „label“: „Ein zweiter Rabattcode für Tests“,
    „coupon“: &lbrace;
    „code&rbrace;
    &rbrace;0r0
    &rbrace;
    ,APPLIED_TO ITEM“&quot;
    „ITEM“: 
    null
    &rbrace;Erweiterungen: 
    
     
     
    {} 
     
     

<u>Tatsächliche Ergebnisse</u>:

Rabattinformationen werden für Warenkörbe mit nur virtuellen Produkten als *null* zurückgegeben.

    &quot;
    &lbrace;
    „data“: &lbrace;
    „estimatedTotals“: &lbrace;
    „cart“: &lbrace;
    „prices“: &lbrace;
    „rabatte“: null
    &rbrace;
    &rbrace;
    &rbrace;
    &rbrace;,
    „extensions“: {}
    &rbrace;
    &quot;

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
