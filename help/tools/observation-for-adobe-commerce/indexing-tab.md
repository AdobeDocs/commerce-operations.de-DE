---
title: Die [!UICONTROL Indexing] tab
description: Erfahren Sie mehr über die [!UICONTROL Indexing] Tab von [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Die [!UICONTROL Indexing] tab

Die **[!UICONTROL Indexing]** -Tab versucht, Probleme mit der Indizierung zu erklären und mögliche Ursachen zu identifizieren.

## [!UICONTROL Core index invalidated]

![Kernindex invalidiert](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Die **[!UICONTROL Core index invalidated]** frame betrachtet die Invalidierung der Indizierung über einen ausgewählten Zeitraum hinweg. Wenn die Indizierung gleichzeitig mit anderen ressourcenintensiven [!DNL crons], werden die Site-Ressourcen stark belastet.

* `%Catalog Product Rule indexer has been invalidated%`) als `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) als `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) als `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) als `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) als `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) als `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) als `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) als `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) als `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) als `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) als `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) als `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) als `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Neubauten von Core-Indizes](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Die **[!UICONTROL Core index rebuilds]** frame betrachtet zentrale Index-Neubauten über einen ausgewählten Zeitrahmen hinweg. Im Folgenden finden Sie die Zeichenfolgen, die aus den Protokollen geparst werden, um den Abschluss der Neuerstellung des Index anzuzeigen.

* `%Catalog Product Rule index has been rebuilt%`) als `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) als `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) als `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) als `category_products_idx`
* `%Customer Grid index has been rebuilt%`) als `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) als `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) als `product_categories_idx`
* `%Product EAV index has been rebuilt%`) als `product_eav_idx`
* `%Product Price index has been rebuilt%`) als `product_price_idx`
* `%Stock index has been rebuilt%`) als `stock_idx`
* `%Inventory index has been rebuilt successfully%`) als `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) als `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) als `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![Katalogsuchindex-Tabelle(n)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Die **[!UICONTROL catalogsearch index table(s)]** frame betrachtet Katalogsuchindex-Tabellen über einen ausgewählten Zeitrahmen. Diese Abfrage untersucht die Dauer von Datenspeichervorgängen für Tabellen mit `%catalogsearch%` im Tabellennamen.

## [!UICONTROL product index table(s)]

![Produktindex-Tabelle(n)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Die **[!UICONTROL product index table(s)]** frame betrachtet Produktindextabellen über einen ausgewählten Zeitrahmen. Diese Abfrage untersucht die Dauer von Datenspeichervorgängen für Tabellen mit `%product%` im Tabellennamen.
