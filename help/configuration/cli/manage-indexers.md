---
title: Verwalten der Indexer
description: Hier finden Sie Beispiele zum Anzeigen und Verwalten von Commerce-Indexern.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ceefb9371dd0a85046cc5bfc0ddc72144d649608
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Verwalten der Indexer

{{file-system-owner}}

So zeigen Sie eine Liste aller Indexer an:

```bash
bin/magento indexer:info
```

Die Liste wird wie folgt angezeigt:

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> Adobe Commerce-Händler, die die Live-Suche, den Katalog-Service oder Produktempfehlungen verwenden, haben die Möglichkeit, eine [SaaS-basierte Preisindizierung](https://experienceleague.adobe.com/en/docs/commerce/price-indexer/price-indexing) zu verwenden.

## Anzeigen des Indexerstatus

Verwenden Sie diesen Befehl, um den Status aller Indexer oder bestimmter Indexer anzuzeigen. Finden Sie beispielsweise heraus, ob ein Indexer neu indiziert werden muss.

Befehlsoptionen:

```bash
bin/magento indexer:status [indexer]
```

Dabei ist `[indexer]` eine durch Leerzeichen getrennte Liste von Indexern. Lassen Sie `[indexer]` aus, um den Status aller Indexer anzuzeigen.

Beispielergebnis:

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## neu indizieren

Verwenden Sie diesen Befehl, um alle oder ausgewählte Indexer nur einmal neu zu indizieren.

>[!INFO]
>
>Dieser Befehl indiziert nur einmal neu. Um Indexer auf dem neuesten Stand zu halten, müssen Sie einen [Cron-Auftrag“ ](../cli/configure-cron-jobs.md).

Befehlsoptionen:

```bash
bin/magento indexer:reindex [indexer]
```

Dabei ist `[indexer]` eine durch Leerzeichen getrennte Liste von Indexern. Lassen Sie `[indexer]` aus, um alle Indexer neu zu indizieren.

Beispielergebnis:

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>Bei Geschäften mit einer großen Anzahl von Produkten, Kunden, Kategorien und Werberegeln kann die Neuindizierung aller Indexer lange dauern.

### Neuindizierung im Parallelmodus

{{php-process-control}}

Indexer sind Scoping- und Multi-Thread-fähig, um die Neuindizierung im parallelen Modus zu unterstützen. Er wird durch die Dimension des Indexers parallelisiert und über mehrere Threads ausgeführt, wodurch die Verarbeitungszeit verkürzt wird.

In diesem Zusammenhang `dimension` der Umfang der Neuindizierung, z. B. ein `website` oder nur ein bestimmter `customer_group`.

Die Parallelisierung von Indizes betrifft nur Indexer im Umfang. Das bedeutet, dass Commerce die Daten mithilfe des Indexers als Umfang in mehrere Tabellen aufteilt, anstatt alle Daten in einer Tabelle zu speichern.

Sie können die folgenden Indizes parallel ausführen:

- `Catalog Search Fulltext` können von Store-Ansichten parallel ausgeführt werden.
- `Category Product` können von Store-Ansichten parallel ausgeführt werden.
- `Catalog Price` kann von Websites und Kundengruppen parallel durchgeführt werden.
- `Catalog Permissions` kann von Kundengruppen parallel durchgeführt werden.

>[!INFO]
>
>Die Parallelisierung für die Katalogsuche Volltext und Produktkategorie ist standardmäßig aktiviert.

Um die Parallelisierung zu verwenden, legen Sie einen der verfügbaren Dimensionsmodi für den Produktpreisindizierer fest:

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

Um die Neuindizierung im parallelen Modus durchzuführen, führen Sie den Befehl „reindex“ mit dem Umgebungsvariablen-`MAGE_INDEXER_THREADS_COUNT` aus oder fügen Sie der `env.php`-Datei eine Umgebungsvariable hinzu. Diese Variable legt die Anzahl der Threads für die Neuindizierung fest.

Beispielsweise führt der folgende Befehl den `Catalog Search Fulltext`-Indexer über drei Threads aus:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Indexer zurücksetzen

Verwenden Sie diesen Befehl, um den Status aller Indexer oder bestimmter Indexer ungültig zu machen.

Befehlsoptionen:

```bash
bin/magento indexer:reset [indexer]
```

Dabei ist ```[indexer]``` eine durch Leerzeichen getrennte Liste von Indexern. `[indexer]` auslassen, um alle Indexer ungültig zu machen.

Beispielergebnis:

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## Indexer konfigurieren

Verwenden Sie diesen Befehl, um die folgenden Indexeroptionen festzulegen:

- **Aktualisierung beim Speichern (`realtime`)**: Indizierte Daten werden aktualisiert, wenn eine Änderung in der Admin vorgenommen wird. (Zum Beispiel wird der Kategorie-Produkt-Index neu indiziert, nachdem Produkte in der Admin-Liste zu einer Kategorie hinzugefügt wurden.)
- **Nach Zeitplan aktualisieren (`schedule`)**: Die Daten werden gemäß dem von Ihrem Cron-Auftrag festgelegten Zeitplan indiziert.

[Weitere Informationen zur Indizierung](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Anzeigen der aktuellen Konfiguration

So zeigen Sie die aktuelle Indexerkonfiguration an:

```bash
bin/magento indexer:show-mode [indexer]
```

Dabei ist `[indexer]` eine durch Leerzeichen getrennte Liste von Indexern. Lassen Sie `[indexer]` aus, um alle Indexermodi anzuzeigen. So zeigen Sie beispielsweise den Modus aller Indexer an:

Beispielergebnis:

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### Einstellen des Indexermodus

>[!IMPORTANT]
>
>Das [!DNL Customer Grid] Indexerverhalten hat sich in Version 2.4.8 geändert:
>
>- **Vor 2.4.8**: Der [!DNL Customer Grid]-Indexer kann nur mithilfe der Option &quot;[!UICONTROL Update on Save]&quot; neu indiziert werden und unterstützt die Option &quot;[!UICONTROL Update by Schedule]&quot; nicht.
>
>   Verwenden Sie den folgenden Befehl, um diesen Indexer beim Speichern zu aktualisieren:
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8 und höher**: Der [!DNL Customer Grid] Indexer unterstützt sowohl [!UICONTROL Update on Save]- als auch [!UICONTROL Update by Schedule] Modi und [!UICONTROL Update by Schedule] standardmäßig.
>
>Siehe [Best Practices für die Indexerkonfiguration](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration) im _Implementierungs-Playbook_.

>[!INFO]
>
>Bevor Sie den Indexermodus wechseln, stellen Sie Ihre Website auf [Wartungsmodus](../../installation/tutorials/maintenance-mode.md) und [Deaktivieren von Cron-Aufträgen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) ein. Dadurch wird sichergestellt, dass keine Datenbanksperren auftreten.

So legen Sie die Indexerkonfiguration fest:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dabei gilt:

- `realtime` - Legt die ausgewählten Indexer fest, die beim Speichern aktualisiert werden.
- `schedule` - Legt die angegebenen Indexer entsprechend dem Cron-Zeitplan zum Speichern fest.
- `indexer` - Eine durch Leerzeichen getrennte Liste von Indexern. Lassen Sie `indexer` aus, um alle Indexer auf die gleiche Weise zu konfigurieren.

Um beispielsweise nur die Indexer für Kategorien und Produktkategorien zu ändern, die planmäßig aktualisiert werden sollen, geben Sie Folgendes ein:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Beispielergebnis:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Die indexerbezogenen Datenbank-Trigger werden hinzugefügt, wenn der Indexermodus auf &quot;`schedule`&quot; festgelegt ist, und entfernt, wenn der Indexermodus auf &quot;`realtime`&quot; festgelegt ist. Wenn die Trigger in Ihrer Datenbank fehlen, während die Indexer auf `schedule` eingestellt sind, ändern Sie die Indexer in `realtime` und ändern Sie sie dann wieder zurück in `schedule`. Dadurch werden die Trigger zurückgesetzt.

### Indexerstatus festlegen

Der Befehl `bin/magento indexer:set-status` wurde in Adobe Commerce 2.4.7 eingeführt. Sie ermöglicht es Administratoren, den Betriebsstatus eines oder mehrerer Indexer zu ändern und so die Systemleistung bei umfangreichen Vorgängen wie Datenimporten, Aktualisierungen oder Wartungsarbeiten zu optimieren.

Befehlssyntax:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Dabei gilt:

- `invalid` - Markiert Indexer als veraltet und fordert bei der nächsten Cron-Ausführung zur Neuindizierung auf, es sei denn, sie werden ausgesetzt.
- `suspended` - Beendet vorübergehend automatische cron-ausgelöste Aktualisierungen für Indexer. Dieser Status gilt sowohl für den Echtzeit- als auch für den Zeitplanmodus, sodass automatische Aktualisierungen bei intensiven Vorgängen angehalten werden.
- `valid` - Zeigt an, dass die Indexerdaten auf dem neuesten Stand sind und nicht neu indiziert werden müssen.
- `indexer` - Eine durch Leerzeichen getrennte Liste von Indexern. Lassen Sie `indexer` aus, um alle Indexer auf die gleiche Weise zu konfigurieren.

Um beispielsweise bestimmte Indexer auszusetzen, geben Sie Folgendes ein:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Beispielergebnis:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Verwalten des Status ausgesetzter Indexer

Wenn ein Indexer auf einen `suspended` gesetzt ist, wirkt sich dies in erster Linie auf die automatische Neuindizierung und die Aktualisierungen der materialisierten Ansicht aus. Im Folgenden finden Sie einen kurzen Überblick:

**Neuindizierung übersprungen**: Das System überspringt die automatische Neuindizierung für `suspended` Indexer und alle Indexer, die denselben `shared_index` nutzen. Durch diesen Ansatz werden Systemressourcen geschont, da die Neuindizierung von Daten im Zusammenhang mit ausgesetzten Prozessen vermieden wird.

**Aktualisierungen der materialisierten Ansicht übersprungen**: Ähnlich wie bei der Neuindizierung hält das System auch Aktualisierungen an materialisierten Ansichten an, die sich auf `suspended` Indexer oder deren freigegebene Indizes beziehen. Durch diese Pause wird die Systemlast während der Aussetzphasen weiter reduziert.

>[!INFO]
>
>Der Befehl `indexer:reindex` indiziert alle Indexer neu, einschließlich der als `suspended` markierten Indexer, sodass manuelle Aktualisierungen nützlich sind, wenn automatische pausiert werden.

>[!IMPORTANT]
>
>Das Ändern des Status eines Indexers in `valid` von `suspended` oder `invalid` erfordert Vorsicht. Diese Aktion kann zu Leistungseinbußen führen, wenn nicht indizierte Daten gesammelt werden.
>
>Es ist wichtig sicherzustellen, dass alle Daten korrekt indiziert werden, bevor Sie den Status manuell auf `valid` aktualisieren, um die Systemleistung und Datenintegrität aufrechtzuerhalten.
