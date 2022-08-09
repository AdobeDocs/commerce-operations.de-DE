---
title: Indexer verwalten
description: Sehen Sie sich Beispiele für das Anzeigen und Verwalten von Commerce-Indizes an.
source-git-commit: dd84039be22b6bd25d57912615d64bad91970926
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Indexer verwalten

{{file-system-owner}}

So zeigen Sie eine Liste aller Indexer an:

```bash
bin/magento indexer:info
```

Die Liste wird wie folgt angezeigt:

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

## Indexstatus anzeigen

Verwenden Sie diesen Befehl, um den Status aller Indexer oder Indexer anzuzeigen. Ermitteln Sie beispielsweise, ob ein Indexer neu indiziert werden muss.

Befehlsoptionen:

```bash
bin/magento indexer:status [indexer]
```

Wo `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. Omit `[indexer]` um den Status aller Indexer anzuzeigen.

Beispielergebnis:

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Neuindizierung

Verwenden Sie diesen Befehl, um alle oder ausgewählte Indexer nur einmal neu zu indizieren.

>[!INFO]
>
>Dieser Befehl wird nur einmal neu indiziert. Um die Indexer auf dem neuesten Stand zu halten, müssen Sie eine [Cron-Auftrag](../cli/configure-cron-jobs.md).

Befehlsoptionen:

```bash
bin/magento indexer:reindex [indexer]
```

Wo `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. Omit `[indexer]` , um alle Indexer neu zu indizieren.

Beispielergebnis:

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>Die Neuindizierung aller Indexer kann bei Geschäften mit einer großen Anzahl von Produkten, Kunden, Kategorien und Werberegeln lange dauern.

### Neuindizierung im Parallelmodus

Indexer werden in einem Umfang und mit mehreren Threads angezeigt, um die Neuindizierung im Parallelmodus zu unterstützen. Sie wird anhand der Dimension des Indexers parallelisiert und über mehrere Threads hinweg ausgeführt, was die Verarbeitungszeit verkürzt.

In diesem Zusammenhang `dimension` ist der Umfang der Neuindizierung, z. B. ein `website` oder nur bestimmte `customer_group`.

Die Indexparallelisierung betrifft nur Scoped-Indexer. Das bedeutet, dass Commerce die Daten mithilfe des Indexers in mehrere Tabellen aufteilt, anstatt alle Daten in einer Tabelle zu speichern.

Sie können die folgenden Indizes im Parallelmodus ausführen:

- `Catalog Search Fulltext` kann von Store-Ansichten parallelisiert werden.
- `Category Product` kann von Store-Ansichten parallelisiert werden.
- `Catalog Price` kann von Website- und Kundengruppen parallelisiert werden.
- `Catalog Permissions` kann von Kundengruppen parallelisiert werden.

Um die Parallelisierung zu verwenden, legen Sie einen der verfügbaren Dimensionsmodi für den Produktpreisindex fest:

- `none` (Standard)
- `website`
- `customer_group`
- `website_and_customer_group`

So legen Sie beispielsweise den Modus pro Website fest:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Um die Parallelisierung für Katalogberechtigungen zu verwenden, legen Sie einen der verfügbaren Dimensionsmodi für den Indexer für Katalogberechtigungen fest:

- `none` (Standard)
- `customer_group`

Oder um den aktuellen Modus zu überprüfen:

```bash
bin/magento indexer:show-dimensions-mode
```

Um eine Neuindizierung im Parallelmodus durchzuführen, führen Sie den Befehl reindex mit der Umgebungsvariablen aus. `MAGE_INDEXER_THREADS_COUNT`oder fügen Sie der `env.php` -Datei. Diese Variable legt die Anzahl der Threads für die Neuindizierungsverarbeitung fest.

Der folgende Befehl führt beispielsweise die `Catalog Search Fulltext` Indexer über drei Threads hinweg:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Indexer zurücksetzen

Verwenden Sie diesen Befehl, um den Status aller Indexer oder bestimmter Indexer ungültig zu machen.

Befehlsoptionen:

```bash
bin/magento indexer:reset [indexer]
```

Wo ```[indexer]``` ist eine durch Leerzeichen getrennte Liste von Indexern. Omit `[indexer]` , um alle Indexer ungültig zu machen.

Beispielergebnis:

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Indexer konfigurieren

Verwenden Sie diesen Befehl, um die folgenden Indexoptionen festzulegen:

- **Aktualisierung beim Speichern (`realtime`)**: Indexierte Daten werden aktualisiert, wenn eine Änderung in der Admin-Konsole vorgenommen wird. (Beispielsweise wird der Index der Kategorie &quot;products&quot;neu indiziert, nachdem Produkte einer Kategorie in Admin hinzugefügt wurden.) Dies ist die Standardeinstellung.
- **Nach Zeitplan aktualisieren (`schedule`)**: Die Daten werden entsprechend dem von Ihrem Cron-Auftrag festgelegten Zeitplan indexiert.

[Weitere Informationen zur Indizierung](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Aktuelle Konfiguration anzeigen

So zeigen Sie die aktuelle Indexkonfiguration an:

```bash
bin/magento indexer:show-mode [indexer]
```

Wo `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. Omit `[indexer]` , um alle Indexmodi anzuzeigen. So zeigen Sie beispielsweise den Modus aller Indexer an:

Beispielergebnis:

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### Indexer konfigurieren

>[!INFO]
>
>Bevor Sie den Indexmodus wechseln, empfehlen wir, Ihre Website auf [Wartung](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) Modus und [Deaktivieren von Cron-Aufträgen](https://devdocs.magento.com/cloud/configure/setup-cron-jobs.html#disable-cron-jobs). Dadurch wird sichergestellt, dass Sie nicht unter Datenbanksperren leiden.

So legen Sie die Indexkonfiguration fest:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dabei gilt:

- `realtime`—Legt die ausgewählten Indexer fest, die beim Speichern aktualisiert werden sollen.
- `schedule`—Legt die angegebenen Indexer fest, die gemäß dem Cron-Zeitplan gespeichert werden sollen.
- `indexer`—Eine durch Leerzeichen getrennte Liste von Indexern. Omit `indexer` um alle Indexer auf die gleiche Weise zu konfigurieren.

Um beispielsweise nur die Indexer für Kategorie-Produkte und Produktkategorien zu ändern, die planmäßig aktualisiert werden sollen, geben Sie Folgendes ein:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Beispielergebnis:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Die indexbezogenen Datenbank-Trigger werden hinzugefügt, wenn der Indexmodus auf `schedule` und entfernt, wenn der Indexmodus auf `realtime`. Wenn die Trigger in Ihrer Datenbank fehlen, während die Indexer auf `schedule`, ändern Sie die Indexer in `realtime` und ändern Sie sie dann zurück zu `schedule`. Dadurch werden die Trigger zurückgesetzt.
