---
title: Indexer verwalten
description: Sehen Sie sich Beispiele für das Anzeigen und Verwalten von Commerce-Indizes an.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 5e1684d4d910f2ea52e12eeccdc291a54372f8d6
workflow-type: tm+mt
source-wordcount: '951'
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

>[!NOTE]
> Adobe Commerce-Händler, die Live Search, Catalog Service oder Product Recommendations verwenden, haben die Möglichkeit, [SaaS-basierte Preisindizierung](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Indexstatus anzeigen

Verwenden Sie diesen Befehl, um den Status aller Indexer oder Indexer anzuzeigen. Ermitteln Sie beispielsweise, ob ein Indexer neu indiziert werden muss.

Befehlsoptionen:

```bash
bin/magento indexer:status [indexer]
```

Wo `[indexer]` ist eine durch Leerzeichen getrennte Liste von Indexern. Omit `[indexer]` , um den Status aller Indexer anzuzeigen.

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

## Reindex

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

{{php-process-control}}

Indexer werden in einem Umfang und mit mehreren Threads angezeigt, um die Neuindizierung im Parallelmodus zu unterstützen. Sie wird anhand der Dimension des Indexers parallelisiert und wird über mehrere Threads hinweg ausgeführt, wodurch die Verarbeitungszeit verkürzt wird.

In diesem Zusammenhang `dimension` ist der Umfang der Neuindizierung, z. B. ein `website` oder nur eine bestimmte `customer_group`.

Die Indexparallelisierung betrifft nur Scoped-Indexer. Das bedeutet, dass Commerce die Daten mithilfe des Indexers in mehrere Tabellen aufteilt, anstatt alle Daten in einer Tabelle zu speichern.

Sie können die folgenden Indizes im Parallelmodus ausführen:

- `Catalog Search Fulltext` kann von Store-Ansichten parallelisiert werden.
- `Category Product` kann von Store-Ansichten parallelisiert werden.
- `Catalog Price` kann von Website- und Kundengruppen parallelisiert werden.
- `Catalog Permissions` kann von Kundengruppen parallelisiert werden.

>[!INFO]
>
>Die Parallelisierung für Volltext der Katalogsuche und Kategorieprodukt ist standardmäßig aktiviert.

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

### Indexmodus festlegen

>[!IMPORTANT]
>
>Stellen Sie die [!DNL Customer Grid] mit `realtime` anstelle von `schedule`. Die [!DNL Customer Grid] kann nur mit der [!UICONTROL Update on Save] -Option. Dieser Index unterstützt die `Update by Schedule` -Option. Verwenden Sie die folgende Befehlszeile, um diesen Indexer beim Speichern zu aktualisieren: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Siehe [Best Practices für die Indexkonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) im _Implementierungs-Playbook_.

>[!INFO]
>
>Bevor Sie den Indexmodus wechseln, setzen Sie Ihre Website auf [Wartung](../../installation/tutorials/maintenance-mode.md) Modus und [Cron-Aufträge deaktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Dadurch wird sichergestellt, dass Sie nicht unter Datenbanksperren leiden.

So legen Sie die Indexkonfiguration fest:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dabei gilt:

- `realtime`—Legt die beim Speichern zu aktualisierenden ausgewählten Indexer fest.
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

### Indexstatus festlegen

Die `bin/magento indexer:set-status` wurde in Adobe Commerce 2.4.7 eingeführt. Administratoren können den Betriebsstatus eines oder mehrerer Indexer ändern und so die Systemleistung bei umfangreichen Vorgängen wie Datenimport, -aktualisierungen oder -wartung optimieren.

Befehlssyntax:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Dabei gilt:

- `invalid`—Markiert Indexer als veraltet und fordert bei der nächsten Cron-Ausführung eine Neuindizierung auf, es sei denn, sie werden ausgesetzt.
- `suspended`—Stoppt vorübergehend automatische, durch Cron ausgelöste Aktualisierungen für Indexer. Dieser Status gilt sowohl für den Echtzeitmodus als auch für den Zeitplanmodus, sodass automatische Aktualisierungen während intensiver Vorgänge angehalten werden.
- `valid`—Gibt an, dass Indexerdaten aktuell sind, ohne dass eine Neuindizierung erforderlich ist.
- `indexer`—Eine durch Leerzeichen getrennte Liste von Indexern. Omit `indexer` um alle Indexer auf die gleiche Weise zu konfigurieren.

Um beispielsweise bestimmte Indexer auszusetzen, geben Sie Folgendes ein:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Beispielergebnis:

```terminal
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Status des ausgesetzten Indexers verwalten

Wenn ein Indexer auf einen `suspended` -Status, wirkt sich dies in erster Linie auf die automatische Neuindizierung und die materialisierten Ansichtsaktualisierungen aus. Im Folgenden finden Sie eine kurze Übersicht:

**Neuindizierung übersprungen**: Die automatische Neuindizierung wird umgangen für `suspended` Indexer und alle Indexer, die dieselbe `shared_index`. Dadurch wird sichergestellt, dass Systemressourcen erhalten bleiben, indem Daten im Zusammenhang mit ausgesetzten Prozessen nicht neu indiziert werden.

**Übersprungene Aktualisierungen der materialisierten Ansicht**: Ähnlich wie bei der Neuindizierung werden Aktualisierungen materialisierter Ansichten im Zusammenhang mit `suspended` Indexer oder ihre freigegebenen Indizes werden ebenfalls angehalten. Dadurch wird die Systemlast während der Aussetzzeit weiter reduziert.

>[!INFO]
>
>Die `indexer:reindex` -Befehl indiziert alle Indizes, einschließlich der Indizes, die als `suspended`, sodass es für manuelle Aktualisierungen nützlich ist, wenn automatische angehalten werden.

>[!IMPORTANT]
>
>Ändern des Status eines Indexers in `valid` von `suspended` oder `invalid` erfordert Vorsicht. Diese Aktion kann zu einer Leistungsbeeinträchtigung führen, wenn gesammelte nicht indizierte Daten vorhanden sind.
>
>Es ist wichtig sicherzustellen, dass alle Daten genau indiziert werden, bevor der Status manuell auf `valid` zur Gewährleistung der Systemleistung und Datenintegrität.
