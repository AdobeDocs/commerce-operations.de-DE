---
title: '"Die [!UICONTROL Indexing] tab"'
description: Erfahren Sie mehr über die [!UICONTROL Indexing] Tab von [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Die [!UICONTROL Indexing] tab

Die **[!UICONTROL Indexing]** -Tab versucht, Probleme mit der Indizierung zu erklären und mögliche Ursachen zu identifizieren.

## [!UICONTROL Core index invalidated]

![Kernindex invalidiert](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Die **[!UICONTROL Core index invalidated]** frame betrachtet die Invalidierung der Indizierung über einen ausgewählten Zeitraum hinweg. Wenn die Indizierung gleichzeitig mit anderen ressourcenintensiven Kronen erfolgt, werden die Site-Ressourcen stark belastet.

* &#39;%Catalog Product Rule Indexer wurde invalidiert%&#39;) als &#39;catalog_product_rule_idx_reset&#39;
* &#39;%Catalog Rule Product Indexer wurde invalidiert%&#39;) als &#39;catalog_rule_product_idx_reset&#39;
* &#39;%Catalog Search indexer has been invalidiert%&#39;) as &#39;catalog_search_idx_reset&#39;
* &#39;%Category Products indexer has been invalidiert%&#39;) as &#39;category_products_idx_reset&#39;
* &#39;%Customer Grid Indexer wurde invalidiert%&#39;) als &#39;customer_grid_idx_reset&#39;
* &#39;%Design Config Grid Indexer wurde invalidiert%&#39;) als &#39;design_config_grid_idx_
* &#39;%Product Categories indexer has been invalidiert%&#39;) as &#39;product_categories_idx_reset&#39;
* &#39;%Product EAV indexer has been invalidiert%&#39;) as &#39;product_eav_idx_reset&#39;
* &#39;%Product Price indexer has been invalidiert%&#39;) as &#39;product_price_idx_reset&#39;
* &#39;%Stock indexer has been invalidiert%&#39;) as &#39;stock_idx_reset&#39;
* &#39;%Inventsindex wurde invalidiert%&#39;) als &#39;inventory_idx_reset&#39;
* &#39;%Inventsindex wurde invalidiert%&#39;) als &#39;inventory_idx_reset&#39;
* &#39;%Sales Rule Indexer wurde invalidiert%&#39;) als &#39;sales_rule_idx_reset&#39;

## [!UICONTROL Core index rebuilds]

![Neubauten von Core-Indizes](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Die **[!UICONTROL Core index rebuilds]** frame betrachtet zentrale Index-Neubauten über einen ausgewählten Zeitrahmen hinweg. Im Folgenden finden Sie die Zeichenfolgen, die aus den Protokollen geparst werden, um den Abschluss der Neuerstellung des Index anzuzeigen.

* &#39;%Catalog Product Rule Index has rebuilt%&#39;) as &#39;catalog_product_rule_idx&#39;
* &#39;%Catalog Rule Product Index has rebuilt%&#39;) as &#39;catalog_rule_product_idx&#39;
* &#39;%Catalog Search index has rebuilt%&#39;) as &#39;catalog_search_idx&#39;
* &#39;%Category Products index has been rebuilt succeeded%&#39;) as &#39;category_products_idx&#39;
* &#39;%Customer Grid Index has rebuilt%&#39;) as &#39;customer_grid_idx&#39;
* &#39;%Design Config Grid Index (Index des Design-Konfigurations-Rasters) wurde neu erstellt%&#39;) als &#39;design_config_grid_idx&#39;
* &#39;%Product Categories index has rebuilt%&#39;) as &#39;product_categories_idx&#39;
* &#39;%Product EAV index has rebuilt%&#39;) as &#39;product_eav_idx&#39;
* &#39;%Product Price index has rebuilt%&#39;) as &#39;product_price_idx&#39;
* &#39;%Stock index has rebuilt%&#39;) as &#39;stock_idx&#39;
* &#39;%Bestandsindex wurde erfolgreich neu erstellt%&#39;) als &#39;inventory_idx&#39;
* %Produkt-/Target-Regelindex wurde erfolgreich neu erstellt%&#39;) als &#39;prod_target_rule_idx&#39;
* &#39;%Sales Rule Index has been rebuilt succeeded%&#39;) as &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![Katalogsuchindex-Tabelle(n)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Die **[!UICONTROL catalogsearch index table(s)]** frame betrachtet Katalogsuchindex-Tabellen über einen ausgewählten Zeitrahmen. Diese Abfrage untersucht die Dauer von Datenspeichervorgängen für Tabellen mit &quot;%catalogsearch%&quot;im Tabellennamen.

## [!UICONTROL product index table(s)]

![Produktindex-Tabelle(n)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Die **[!UICONTROL product index table(s)]** frame betrachtet Produktindextabellen über einen ausgewählten Zeitrahmen. Diese Abfrage untersucht die Dauer von Datenspeichervorgängen für Tabellen mit &quot;%product%&quot;im Tabellennamen.
