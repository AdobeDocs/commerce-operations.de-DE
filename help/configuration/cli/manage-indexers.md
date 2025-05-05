---
title: Verwalten der Indexer
description: Hier finden Sie Beispiele zum Anzeigen und Verwalten von Commerce-Indexern.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Verwalten der Indexer

{{file-system-owner}}

So zeigen Sie eine Liste aller Indexer an:

```bash
bin/magento indexer:info
```

Die Liste wird wie folgt angezeigt:

```
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
> Adobe Commerce-Händler, die die Live-Suche, den Katalog-Service oder Produktempfehlungen verwenden, haben die Möglichkeit, eine [SaaS-basierte Preisindizierung](https://experienceleague.adobe.com/docs/commerce/price-indexer/index.html) zu verwenden.

## Ansicht Indexerstatus

Verwenden Sie diesen Befehl, um den Status aller oder bestimmter Indexer zu Ansicht. So können Sie z. B. herausfinden, ob ein Indexer neu indiziert werden muss.

Befehl Optionen:

```bash
bin/magento indexer:status [indexer]
```

Wobei `[indexer]` eine durch Leerzeichen getrennte Liste von Indexern ist. Auslassung `[indexer]` , um den Status aller Indexer zu Ansicht.

Beispielergebnis:

```
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

## Neu indizieren

Verwenden Sie diesen Befehl, um alle oder ausgewählte Indexer nur einmal neu zu indizieren.

>[!INFO]
>
>Dieser Befehl indiziert nur einmal neu. Um die Indexer auf dem neuesten Stand zu halten, müssen Sie einen [Cron-Job](../cli/configure-cron-jobs.md) einrichten.

Befehl Optionen:

```bash
bin/magento indexer:reindex [indexer]
```

Wobei `[indexer]` eine durch Leerzeichen getrennte Liste von Indexern ist. Lassen Sie `[indexer]` aus, um alle Indexer neu zu indizieren.

Beispielergebnis:

```
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

```
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

```
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
>Stellen Sie sicher, dass Sie die [!DNL Customer Grid] auf `realtime` statt auf `schedule` setzen. Die [!DNL Customer Grid] kann nur mit der Option [!UICONTROL Update on Save] neu indiziert werden. Dieser Index unterstützt die `Update by Schedule` nicht. Verwenden Sie die folgende Befehlszeile, um diesen Indexer so festzulegen, dass er beim Speichern aktualisiert wird: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Siehe [Best Practices für die Indexerkonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html?lang=de) im _Implementierungs-Playbook_.

>[!INFO]
>
>Bevor Sie den Indexermodus wechseln, stellen Sie Ihre Website auf [Wartungsmodus](../../installation/tutorials/maintenance-mode.md) und [Deaktivieren von Cron-Aufträgen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=de#disable-cron-jobs) ein. Dadurch wird sichergestellt, dass es nicht zu Datenbanksperren kommt.

So legen Sie die Indexerkonfiguration fest:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dabei gilt:

- `realtime` - Legt die ausgewählten Indexer fest, die beim Speichern aktualisiert werden.
- `schedule` - Legt die angegebenen Indexer entsprechend dem Cron-Zeitplan zum Speichern fest.
- `indexer` - Eine durch Leerzeichen getrennte Liste von Indexern. Lassen Sie `indexer` aus, um alle Indexer auf die gleiche Weise zu konfigurieren.

Geben Sie beispielsweise Folgendes ein, um nur die Indexer für Kategorie Produkte und Produktkategorien zu ändern, die planmäßig aktualisiert werden sollen:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Beispielergebnis:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Die indexerbezogenen Datenbanktrigger werden hinzugefügt, wenn der Indexermodus auf `schedule` festgelegt ist, und entfernt, wenn der Indexermodus auf `realtime`festgelegt ist. Wenn die Trigger in der Datenbank fehlen, während die Indexer auf `schedule`festgelegt sind, ändern Sie die Indexer in `realtime` und ändern Sie sie dann wieder in `schedule`. Dadurch werden die Trigger zurückgesetzt.

### Festlegen Indexerstatus

Der Befehl `bin/magento indexer:set-status` wurde in Adobe Commerce 2.4.7 eingeführt. Sie ermöglicht es Administratoren, den Betriebsstatus eines oder mehrerer Indexer zu ändern und so die Systemleistung bei umfangreichen Vorgängen wie Datenimporten, Aktualisierungen oder Wartungsarbeiten zu optimieren.

Befehl Syntax:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Wo:

- `invalid`: Markiert Indexer als veraltet und fordert beim nächsten Cron-Lauf eine Neuindizierung an, es sei denn, sie werden angehalten.
- `suspended`– Stoppt vorübergehend automatische, durch Cron ausgelöste Updates für Indexer. Dieser Status gilt sowohl für den Echtzeit- als auch für den Zeitplanmodus und stellt sicher, dass automatische Aktualisierungen während intensiver Vorgänge pausiert werden.
- `valid`: Gibt an, dass die Indexer-Daten aktuell sind und keine Neuindizierung erforderlich ist.
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

**Neuindizierung übersprungen**: Die automatische Neuindizierung wird für `suspended` Indexer und alle Indexer mit derselben `shared_index` umgangen. Dadurch wird sichergestellt, dass Systemressourcen geschützt werden, indem Daten im Zusammenhang mit ausgesetzten Prozessen nicht neu indiziert werden.

**Aktualisierungen der materialisierten Ansicht übersprungen**: Ähnlich wie bei der Neuindizierung werden auch Aktualisierungen der materialisierten Ansichten, die sich auf `suspended` Indexer oder deren freigegebene Indizes beziehen, angehalten. Dadurch wird die Systemlast während der Aussetzphasen weiter reduziert.

>[!INFO]
>
>Der Befehl `indexer:reindex` indiziert alle Indexer neu, einschließlich der als `suspended` markierten Indizes, sodass manuelle Aktualisierungen nützlich sind, wenn automatische angehalten werden.

>[!IMPORTANT]
>
>Das Ändern des Status eines Indexers in `valid` von `suspended` oder `invalid` erfordert Vorsicht. Diese Aktion kann zu Leistungseinbußen führen, wenn nicht indizierte Daten gesammelt werden.
>
>Es ist wichtig sicherzustellen, dass alle Daten korrekt indiziert werden, bevor Sie den Status manuell auf `valid` aktualisieren, um die Systemleistung und Datenintegrität aufrechtzuerhalten.
