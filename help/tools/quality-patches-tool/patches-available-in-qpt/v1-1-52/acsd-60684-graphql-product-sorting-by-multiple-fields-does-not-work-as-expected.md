---
title: 'ACSD-60684: [!DNL GraphQL]  Sortieren nach mehreren Feldern funktioniert nicht wie erwartet'
description: Wenden Sie den Patch ACSD-60684 an, um das Adobe Commerce-Problem zu beheben [!DNL GraphQL]  bei dem die Sortierung nach mehreren Feldern nicht funktioniert, wenn die Sortierung in Variablen übergeben wird.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 1c29299b-c85f-4166-886b-357a1486e67e
source-git-commit: a5dda25e502889ee0a23e99b412aeeb863de452c
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-60684: Die Sortierung [!DNL GraphQL] Produkts nach mehreren Feldern funktioniert nicht wie erwartet

Mit dem Patch ACSD-60684 wird das Problem behoben, dass [!DNL GraphQL] Sortieren von Produkten nach mehreren Feldern nicht funktioniert, wenn die Sortierung in Variablen übergeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60684. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL GraphQL] Sortieren von Produkten nach mehreren Feldern funktioniert nicht wie erwartet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie drei Produkte mit den Namen A, B und C.
1. Rufen Sie die Produkte mithilfe der folgenden [!DNL GraphQL] ab:

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

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
