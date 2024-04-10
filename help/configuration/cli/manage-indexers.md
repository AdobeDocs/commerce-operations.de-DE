---
title: Verwalten der Indexer
description: Sehen Sie sich Beispiele zum Anzeigen und Verwalten von Commerce-Indexern an.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Verwalten der Indexer

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

>[!NOTE]
> Adobe Commerce-Händler, die die Live-Suche, den Katalog-Service oder die Produkt-Recommendations verwenden, haben die Möglichkeit, Folgendes zu verwenden [SaaS-basierte Preisindizierung](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Anzeigen des Indexerstatus

Verwenden Sie diesen Befehl, um den Status aller Indexer oder bestimmter Indexer anzuzeigen. Finden Sie beispielsweise heraus, ob ein Indexer neu indiziert werden muss.

Befehlsoptionen:

```bash
bin/magento indexer:status [indexer]
```

Hierbei gilt `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. weglassen `[indexer]` , um den Status aller Indexer anzuzeigen.

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

## neu indizieren

Verwenden Sie diesen Befehl, um alle oder ausgewählte Indexer nur einmal neu zu indizieren.

>[!INFO]
>
>Dieser Befehl indiziert nur einmal neu. Um Indexer auf dem neuesten Stand zu halten, müssen Sie einen [Cron-Job](../cli/configure-cron-jobs.md).

Befehlsoptionen:

```bash
bin/magento indexer:reindex [indexer]
```

Hierbei gilt `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. weglassen `[indexer]` Neuindizieren aller Indexer.

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
>Bei Geschäften mit einer großen Anzahl von Produkten, Kunden, Kategorien und Werberegeln kann die Neuindizierung aller Indexer lange dauern.

### Neuindizierung im Parallelmodus

{{php-process-control}}

Indexer sind Scoping- und Multi-Thread-basiert, um die Neuindizierung im parallelen Modus zu unterstützen. Er wird durch die Dimension des Indexers parallelisiert und über mehrere Threads ausgeführt, wodurch die Verarbeitungszeit verkürzt wird.

In diesem Zusammenhang `dimension` ist der Umfang der Neuindizierung, z. B. eine `website` oder nur eine bestimmte `customer_group`.

Die Indexparallelisierung betrifft nur Indexer mit Scope, was bedeutet, dass Commerce die Daten mithilfe des Indexers als Scope in mehrere Tabellen aufteilt, anstatt alle Daten in einer Tabelle zu speichern.

Sie können die folgenden Indizes im parallelen Modus ausführen:

- `Catalog Search Fulltext` kann von Store-Ansichten parallel geschaltet werden.
- `Category Product` kann von Store-Ansichten parallel geschaltet werden.
- `Catalog Price` kann von Website- und Kundengruppen parallel durchgeführt werden.
- `Catalog Permissions` kann von Kundengruppen parallel geschaltet werden.

>[!INFO]
>
>Die Parallelisierung für die Katalogsuche - Volltext und Produktkategorie ist standardmäßig aktiviert.

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

Um die Neuindizierung im parallelen Modus auszuführen, führen Sie den Befehl „reindex“ mithilfe der Umgebungsvariablen aus `MAGE_INDEXER_THREADS_COUNT`, oder fügen Sie eine Umgebungsvariable zur `env.php` -Datei. Diese Variable legt die Anzahl der Threads für die Neuindizierung fest.

Mit dem folgenden Befehl wird beispielsweise das `Catalog Search Fulltext` Indexer in drei Threads:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Reset Indexer

Verwenden Sie diesen Befehl, um den Status aller Indexer oder bestimmter Indexer ungültig zu machen.

Befehlsoptionen:

```bash
bin/magento indexer:reset [indexer]
```

Hierbei gilt ```[indexer]``` ist eine durch Leerzeichen getrennte Liste von Indexern. weglassen `[indexer]` , um alle Indexer ungültig zu machen.

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

## Konfigurieren von Indexern

Verwenden Sie diesen Befehl, um die folgenden Indexeroptionen festzulegen:

- **Aktualisierung zum Speichern (`realtime`)**: Indizierte Daten werden aktualisiert, wenn eine Änderung in der Admin vorgenommen wird. (Beispielsweise wird der Kategorie-Produkt-Index neu indiziert, nachdem Produkte in der Admin-Liste zu einer Kategorie hinzugefügt wurden.) Dies ist die Standardeinstellung.
- **Nach Zeitplan aktualisieren (`schedule`)**: Daten werden gemäß dem Zeitplan indiziert, der von Ihrem Cron-Auftrag festgelegt wird.

[Weitere Informationen zur Indizierung](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Anzeigen der aktuellen Konfiguration

So zeigen Sie die aktuelle Indexerkonfiguration an:

```bash
bin/magento indexer:show-mode [indexer]
```

Hierbei gilt `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. weglassen `[indexer]` , um alle Indexermodi anzuzeigen. So zeigen Sie beispielsweise den Modus aller Indexer an:

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

### Einstellen des Indexermodus

>[!IMPORTANT]
>
>Stellen Sie sicher, dass [!DNL Customer Grid] mit `realtime` anstelle von `schedule`. Die [!DNL Customer Grid] kann nur mit dem neu indiziert werden [!UICONTROL Update on Save] Option. Dieser Index unterstützt nicht den `Update by Schedule` Option. Verwenden Sie die folgende Befehlszeile, um diesen Indexer so festzulegen, dass er beim Speichern aktualisiert wird: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Siehe [Best Practices für die Indexerkonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) in der _Implementierungs-Playbook_.

>[!INFO]
>
>Bevor Sie den Indexermodus wechseln, stellen Sie Ihre Website auf Folgendes ein [Unterhalt](../../installation/tutorials/maintenance-mode.md) Modus und [Cron-Aufträge deaktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Dadurch wird sichergestellt, dass Sie keine Datenbanksperren erleiden.

So legen Sie die Indexerkonfiguration fest:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dabei gilt:

- `realtime`- Legt die ausgewählten Indexer fest, die beim Speichern aktualisiert werden.
- `schedule`- Legt die angegebenen Indexer gemäß dem Cron-Zeitplan zum Speichern fest.
- `indexer`- Ist eine durch Leerzeichen getrennte Liste von Indexern. weglassen `indexer` um alle Indexer auf die gleiche Weise zu konfigurieren.

Um beispielsweise nur die Indexer für Kategorien, Produkte und Produktkategorien zu ändern und sie planmäßig zu aktualisieren, geben Sie Folgendes ein:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Beispielergebnis:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Die indexerbezogenen Datenbank-Trigger werden hinzugefügt, wenn der Indexermodus auf festgelegt ist. `schedule` und entfernt, wenn der Indexermodus auf eingestellt ist. `realtime`. Wenn die Trigger in der Datenbank fehlen, während die Indexer auf gesetzt sind `schedule`, ändern Sie die Indexer zu `realtime` und sie dann wieder ändern in `schedule`. Dadurch werden die Trigger zurückgesetzt.

### Indexerstatus festlegen

Mit diesem Befehl können Administratoren den Betriebsstatus eines oder mehrerer Indexer ändern und so die Systemleistung bei umfangreichen Vorgängen wie Datenimporten, Aktualisierungen oder Wartungsarbeiten optimieren.

Befehlssyntax:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Dabei gilt:

- `invalid`- Markiert Indexer als veraltet, weshalb beim nächsten Cron-Durchgang eine Neuindizierung durchgeführt wird, es sei denn, sie werden ausgesetzt.
- `suspended`- Beendet vorübergehend automatische cron-ausgelöste Aktualisierungen für Indexer. Dieser Status gilt sowohl für den Echtzeit- als auch für den Zeitplanmodus, sodass automatische Aktualisierungen bei intensiven Vorgängen angehalten werden.
- `valid`- Zeigt an, dass die Indexerdaten auf dem neuesten Stand sind, sodass keine Neuindizierung erforderlich ist.
- `indexer`- Ist eine durch Leerzeichen getrennte Liste von Indexern. weglassen `indexer` um alle Indexer auf die gleiche Weise zu konfigurieren.

Um beispielsweise bestimmte Indexer auszusetzen, geben Sie Folgendes ein:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Beispielergebnis:

```terminal
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Verwalten des Status ausgesetzter Indexer

Wenn ein Indexer auf einen `suspended` -Status, wirkt sich dies in erster Linie auf die automatische Neuindizierung und Materialized View-Aktualisierungen aus. Im Folgenden finden Sie einen kurzen Überblick:

**Neuindizierung übersprungen**: Die automatische Neuindizierung wird für umgangen. `suspended` Indexer und alle Indexer, die dieselben verwenden `shared_index`. Dadurch wird sichergestellt, dass Systemressourcen geschützt werden, indem Daten im Zusammenhang mit ausgesetzten Prozessen nicht neu indiziert werden.

**Aktualisierungen der materialisierten Ansicht übersprungen**: Ähnlich wie bei der Neuindizierung werden Aktualisierungen an materialisierten Ansichten vorgenommen, die sich auf Folgendes beziehen `suspended` Indexer oder ihre freigegebenen Indizes werden ebenfalls angehalten. Dadurch wird die Systemlast während der Aussetzphasen weiter reduziert.

>[!INFO]
>
>Die `indexer:reindex` -Befehl indiziert alle Indexer neu, einschließlich der als `suspended`Dies macht es nützlich für manuelle Aktualisierungen, wenn automatische angehalten werden.

>[!IMPORTANT]
>
>Ändern des Status eines Indexers in `valid` von `suspended` oder `invalid` Erfordert Vorsicht. Diese Aktion kann zu Leistungseinbußen führen, wenn nicht indizierte Daten gesammelt werden.
>
>Es ist wichtig sicherzustellen, dass alle Daten korrekt indiziert werden, bevor der Status manuell auf aktualisiert wird `valid` um die Systemleistung und Datenintegrität zu erhalten.
