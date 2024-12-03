---
title: 'ACSD-60684: [!DNL GraphQL] Die Sortierung nach mehreren Feldern funktioniert nicht erwartungsgemäß'
description: Wenden Sie den Patch ACSD-60684 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!DNL GraphQL] Produktsortierung durch mehrere Felder nicht funktioniert, wenn die Sortierung in Variablen übergeben wird.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 1c29299b-c85f-4166-886b-357a1486e67e
source-git-commit: a5dda25e502889ee0a23e99b412aeeb863de452c
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-60684: [!DNL GraphQL] Produktsortierung durch mehrere Felder funktioniert nicht erwartungsgemäß

Der Patch ACSD-60684 behebt das Problem, dass die Sortierung von [!DNL GraphQL] Produkten durch mehrere Felder nicht funktioniert, wenn die Sortierung in Variablen übergeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60684. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL GraphQL] Produktsortierung nach mehreren Feldern funktioniert nicht erwartungsgemäß.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie drei Produkte mit den Namen A, B und C.
1. Rufen Sie die Produkte mit dem folgenden [!DNL GraphQL] ab:

   ```
   query FindProducts($search: String, $filter:ProductAttributeFilterInput!, $pageSize: Int!, $currentPage: Int!, $sort: ProductAttributeSortInput!){
       products(search: $search, filter: $filter, pageSize: $pageSize, currentPage: $currentPage, sort: $sort){
           total_count
           page_info{total_pages}
           items{
               __typename
               url_key
               sku
               name
               stock_status
               price_range{
                   minimum_price{
                       final_price{
                           value
                           currency
                       }
                   }
               }
           }
       }
   } 
   ```

   Variablen:

   ```
   {
       "search": null,
       "filter": {
   
       },
       "pageSize": 24,
       "currentPage": 1,
       "sort": {
           "name": "ASC"
       }
   }  
   ```

1. Wiederholen Sie die Abfrage mit `sort` : `DESC`

<u>Erwartete Ergebnisse</u>:

Die Ergebnisse werden entsprechend sortiert.

<u>Tatsächliche Ergebnisse</u>:

Die ausgewählte Sortierung wurde nicht angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
