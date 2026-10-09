---
title: Die Registerkarte [!UICONTROL Indexing]
description: Erfahren Sie mehr über die Registerkarte [!UICONTROL Indexing] von [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%
---
# Die Registerkarte [!UICONTROL Indexing]

Auf der Registerkarte **[!UICONTROL Indexing]** wird versucht, Probleme mit der Indizierung zu erklären und mögliche Ursachen zu identifizieren.

## [!UICONTROL Core index invalidated]

![Kernindex ungültig](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Der **[!UICONTROL Core index invalidated]**-Frame untersucht die Indizierungsinvalidierung über einen ausgewählten Zeitraum. Wenn die Indizierung gleichzeitig mit anderen ressourcenintensiven [!DNL crons] erfolgt, bedeutet dies eine hohe Belastung für die Site-Ressourcen.

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

![Neuerstellung des Kernindex](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Der **[!UICONTROL Core index rebuilds]** betrachtet die Neuerstellung des Kernindex über einen ausgewählten Zeitraum. Im Folgenden finden Sie die Zeichenfolgen, die aus den Protokollen analysiert werden, um den Abschluss der Neuerstellung des Index anzuzeigen.

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

![CatalogSearch-Indextabelle(n)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Der **[!UICONTROL catalogsearch index table(s)]** zeigt Katalogsuchindex-Tabellen für einen ausgewählten Zeitraum an. Bei dieser Abfrage wird die Dauer aller Datenspeichervorgänge für Tabellen mit `%catalogsearch%` im Tabellennamen untersucht.

## [!UICONTROL product index table(s)]

![Produktindex-Tabelle(n)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Der **[!UICONTROL product index table(s)]** betrachtet die Produktindextabellen in einem ausgewählten Zeitraum. Bei dieser Abfrage wird die Dauer aller Datenspeichervorgänge für Tabellen mit `%product%` im Tabellennamen untersucht.
