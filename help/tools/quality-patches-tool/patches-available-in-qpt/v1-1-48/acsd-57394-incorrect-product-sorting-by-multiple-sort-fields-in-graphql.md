---
title: "ACSD-57394: Falsche Produktsortierung nach mehreren Sortierungsattributen in [!DNL GraphQL]"
description: Wenden Sie den Patch ACSD-57394 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte bei Verwendung mehrerer Sortierattribute in  [!DNL GraphQL] falsch sortiert werden.
feature: GraphQL, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-57394: Falsche Produktsortierung nach mehreren Sortierungsattributen in [!DNL GraphQL]

Der Patch ACSD-57394 behebt das Problem, dass Produkte bei Verwendung mehrerer Sortierattribute in [!DNL GraphQL] falsch sortiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-57394. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produkte werden bei Verwendung mehrerer Sortierattribute in [!DNL GraphQL] falsch sortiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einige Produkte mit unterschiedlichen Preisen und Namen.
1. Erstellen Sie eine Kategorie und weisen Sie ihr die erstellten Produkte zu.
1. Senden Sie eine [!DNL GraphQL] -Produktanfrage für die erstellte Kategorie mit einigen *sort* -Attributen. Beispiel:

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. Überprüfen Sie die Antwort, nachdem Sie *sort* -Attribute erstellt haben.

<u>Erwartete Ergebnisse</u>:

Die Produkte sollten in der richtigen Reihenfolge zurückgegeben werden. Die Sortierung der Produkte nach mehreren Attributen sollte funktionieren.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht in der richtigen Reihenfolge zurückgegeben. Die Sortierung der Produkte nach mehreren Attributen funktioniert nicht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.

