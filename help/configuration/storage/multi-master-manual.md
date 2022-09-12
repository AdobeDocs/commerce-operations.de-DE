---
title: Übergeordnete Datenbanken manuell konfigurieren
description: Siehe Anleitungen zum manuellen Konfigurieren der geteilten Datenbanklösung.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1388'
ht-degree: 0%

---


# Übergeordnete Datenbanken manuell konfigurieren

{{ee-only}}

{{deprecate-split-db}}

Wenn die Commerce-Anwendung bereits in Produktion ist oder Sie bereits benutzerdefinierten Code oder Komponenten installiert haben, müssen Sie die Aufspaltungsdatenbanken möglicherweise manuell konfigurieren. Wenden Sie sich vor dem Fortfahren an den Adobe Commerce-Support , um zu erfahren, ob dies für Ihren Fall erforderlich ist.

Die manuelle Aufspaltung von Datenbanken beinhaltet:

- Erstellen Sie die [Kasse](https://glossary.magento.com/checkout) und Datenbanken des Bestellmanagementsystems (OMS)
- Führen Sie eine Reihe von SQL-Skripten aus, die:

   - Fremdschlüssel ablegen
   - Sichern von Verkaufs- und Anführungsdatentabellen
   - Verschieben Sie Tabellen aus Ihrer Hauptdatenbank in die Verkaufs- und Kursdatenbanken.

>[!WARNING]
>
>Wenn ein benutzerdefinierter Code JOINs mit Tabellen in den Verkaufs- und Anführungsdatenbanken verwendet, können Sie _cannot_ Verwendung von geteilten Datenbanken. Wenden Sie sich im Zweifelsfall an die Autoren von benutzerdefiniertem Code oder Erweiterungen, um sicherzustellen, dass ihr Code keine JOINs verwendet.

Dieses Thema verwendet die folgenden Benennungskonventionen:

- Der Name der Hauptdatenbank lautet `magento` und sein Benutzername und Kennwort beide `magento`
- Der Name der Anführungsdatenbank lautet `magento_quote` und sein Benutzername und Kennwort beide `magento_quote`

   Die Angebotsdatenbank wird auch als _Kasse_ Datenbank.

- Der Name der Verkaufsdatenbank lautet `magento_sales` und sein Benutzername und Kennwort beide `magento_sales`

   Die Verkaufsdatenbank wird auch als OMS-Datenbank bezeichnet.

>[!INFO]
>
>In diesem Handbuch wird davon ausgegangen, dass sich alle drei Datenbanken auf demselben Host wie die Commerce-Anwendung befinden. Sie können jedoch selbst entscheiden, wo die Datenbanken zu finden sind und wie sie benannt sind. Wir hoffen, dass unsere Beispiele die Befolgung der Anweisungen erleichtern.

## Sichern des Commerce-Systems

Adobe empfiehlt dringend, Ihre aktuelle Datenbank und Ihr Dateisystem zu sichern, damit Sie diese wiederherstellen können, wenn während des Vorgangs Probleme auftreten.

**Sichern des Systems**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zu der [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Geben Sie die folgenden Befehle ein:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Einrichten zusätzlicher Übergeordneter Datenbanken

In diesem Abschnitt wird beschrieben, wie Sie Datenbankinstanzen für Verkäufe erstellen und [Anführungszeichen](https://glossary.magento.com/quote) -Tabellen.

**So erstellen Sie Verkaufs- und OMS-Anführungsdatenbanken**:

1. Melden Sie sich bei Ihrem Datenbankserver als ein beliebiger Benutzer an.
1. Geben Sie den folgenden Befehl ein, um zu einer MySQL-Eingabeaufforderung zu gelangen:

   ```bash
   mysql -u root -p
   ```

1. MySQL eingeben `root` das Kennwort des Benutzers bei Aufforderung.
1. Geben Sie die folgenden Befehle in der angezeigten Reihenfolge ein, um Datenbankinstanzen mit dem Namen `magento_quote` und `magento_sales` mit denselben Benutzernamen und Kennwörtern:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Eingabe `exit` , um die Eingabeaufforderung zu beenden.

1. Überprüfen Sie die Datenbanken einzeln:

   Anführungsdatenbank:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Wenn der MySQL-Monitor angezeigt wird, haben Sie die Datenbank ordnungsgemäß erstellt. Wenn ein Fehler angezeigt wird, wiederholen Sie die vorherigen Befehle.

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Verkaufsdatenbank konfigurieren

In diesem Abschnitt wird beschrieben, wie Sie SQL-Skripte erstellen und ausführen, die Kursdatenbanktabellen ändern und Daten aus diesen Tabellen sichern.

Tabellennamen der Verkaufsdatenbank beginnen mit:

- `salesrule_`
- `sales_`
- `magento_sales_`
- Die `magento_customercustomattributes_sales_flat_order` ebenfalls betroffen

>[!INFO]
>
>Dieser Abschnitt enthält Skripte mit bestimmten Datenbanktabellennamen. Wenn Sie Anpassungen vorgenommen haben oder eine vollständige Liste der Tabellen anzeigen möchten, bevor Sie Aktionen daran durchführen, lesen Sie [Referenzskripte](#reference-scripts).

Weitere Informationen finden Sie unter:

- [SQL-Scripts für Verkaufsdatenbank erstellen](#create-sales-database-sql-scripts)
- [Verkaufsdaten sichern](#back-up-sales-data)

### SQL-Scripts für Verkaufsdatenbank erstellen

Erstellen Sie die folgenden SQL-Skripte an einem Speicherort, auf den der Benutzer zugreifen kann, der sich bei Ihrem Commerce-Server anmeldet. Wenn Sie sich beispielsweise anmelden oder Befehle als `root`, können Sie die Skripte im `/root/sql-scripts` Verzeichnis.

#### Fremdschlüssel entfernen

Dieses Skript entfernt ausländische Schlüssel, die auf nicht verkaufte Tabellen verweisen, aus der Verkaufsdatenbank.

Erstellen Sie das folgende Skript und geben Sie ihm einen Namen wie `1_foreign-sales.sql`. Ersetzen `<your main DB name>` mit dem Namen Ihrer Datenbank.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### Verkaufsdatenbank konfigurieren

Führen Sie das vorherige Skript aus:

1. Melden Sie sich bei Ihrer MySQL-Datenbank als `root` oder administrativer Benutzer:

   ```bash
   mysql -u root -p
   ```

1. Im `mysql>` auffordern, führen Sie das Skript wie folgt aus:

   ```shell
   source <path>/<script>.sql
   ```

   Beispiel:

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Geben Sie nach Ausführung des Skripts `exit`.

### Verkaufsdaten sichern

In diesem Abschnitt wird beschrieben, wie Sie Verkaufstabellen aus der wichtigsten Commerce-Datenbank sichern, damit Sie sie in einer separaten Verkaufsdatenbank wiederherstellen können.

Wenn Sie sich derzeit im `mysql>` Eingabeaufforderung eingeben `exit` , um zur Befehlszeile zurückzukehren.

Führen Sie Folgendes aus: `mysqldump` -Befehle, einzeln, aus der Kommandos-Shell. Ersetzen Sie jeweils Folgendes:

- `<your database root username>` mit dem Namen Ihres Datenbankstammbenutzers
- `<your database root user password>` mit dem Kennwort des Benutzers
- `<your main Commerce DB name>` mit dem Namen Ihrer Commerce-Datenbank
- `<path>` mit einem beschreibbaren Dateisystempfad

#### Script 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Script 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Script 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Script 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Verkaufsdaten wiederherstellen

Dieses Skript stellt Verkaufsdaten in Ihrer Anführungsdatendatenbank wieder her.

#### NDB-Anforderung

Wenn Sie eine [Netzwerkdatenbank (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) Cluster:

1. Konvertieren Sie Tabellen aus InnoDb in NDB-Typ in Dump-Dateien:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Entfernen Sie Zeilen mit einem FULLTEXT-Schlüssel aus Dumps, da NDB-Tabellen FULLTEXT nicht unterstützen.

#### Daten wiederherstellen

Führen Sie die folgenden Befehle aus:

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Wo

- `<your sales DB name>` mit dem Namen Ihrer Verkaufsdatenbank.

   In diesem Thema lautet der Beispiel-Datenbankname `magento_sales`.

- `<root username>` mit Ihrem MySQL-Stammbenutzernamen
- `<root user password>` mit dem Kennwort des Benutzers
- Überprüfen Sie den Speicherort der zuvor erstellten Sicherungsdateien (z. B. `/var/sales.sql`)

## Angebotsdatenbank konfigurieren

In diesem Abschnitt werden die Aufgaben zum Ablegen von Fremdschlüsseln aus den Tabellen der Verkaufsdatenbank und zum Verschieben von Tabellen in die Verkaufsdatenbank erläutert.

>[!INFO]
>
>Dieser Abschnitt enthält Skripte mit bestimmten Datenbanktabellennamen. Wenn Sie Anpassungen vorgenommen haben oder eine vollständige Liste der Tabellen anzeigen möchten, bevor Sie Aktionen daran durchführen, lesen Sie [Referenzskripte](#reference-scripts).

Anführungszeichen für Datenbanktabellennamen setzen auf `quote`. Die `magento_customercustomattributes_sales_flat_quote` und `magento_customercustomattributes_sales_flat_quote_address` sind auch betroffen

### Fremdschlüssel aus Anführungszeichen ablegen

Dieses Skript entfernt Fremdschlüssel, die auf nichtkursive Tabellen verweisen, aus Anführungszeichentabellen. Ersetzen `<your main Commerce DB name>` mit dem Namen Ihrer Commerce-Datenbank.

Erstellen Sie das folgende Skript und geben Sie ihm einen Namen wie `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Führen Sie das Skript wie folgt aus:

1. Melden Sie sich bei Ihrer MySQL-Datenbank als Root- oder Administratorbenutzer an:

   ```bash
   mysql -u root -p
   ```

1. Im `mysql >` auffordern, führen Sie das Skript wie folgt aus:
   `source <path>/<script>.sql`

   Beispiel:

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Geben Sie nach Ausführung des Skripts `exit`.

### Sichern von Anführungszeichentabellen

In diesem Abschnitt wird beschrieben, wie Sie Angebote aus der Hauptdatenbank sichern und in Ihrer Anführungsdatenbank wiederherstellen können.

Führen Sie den folgenden Befehl an einer Eingabeaufforderung aus:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB-Anforderung

Wenn Sie eine [Netzwerkdatenbank (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) Cluster:

1. Konvertieren Sie Tabellen aus InnoDb in NDB-Typ in Dump-Dateien:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Entfernen Sie Zeilen mit einem FULLTEXT-Schlüssel aus Dumps, da NDB-Tabellen FULLTEXT nicht unterstützen.

### Tabellen in der Anführungsdatenbank wiederherstellen

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Verkaufs- und Zitatentabellen aus der Datenbank löschen

Dieses Skript verkauft und zitiert Tabellen aus der Commerce-Datenbank. Ersetzen `<your main DB name>` mit dem Namen Ihrer Commerce-Datenbank.

Erstellen Sie das folgende Skript und geben Sie ihm einen Namen wie `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Führen Sie das Skript wie folgt aus:

1. Melden Sie sich bei Ihrer MySQL-Datenbank als Root- oder Administratorbenutzer an:

   ```bash
   mysql -u root -p
   ```

1. Im `mysql>` auffordern, führen Sie das Skript wie folgt aus:

   ```shell
   source <path>/<script>.sql
   ```

   Beispiel:

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Geben Sie nach Ausführung des Skripts `exit`.

## Aktualisierung der Bereitstellungskonfiguration

Der letzte Schritt bei der manuellen Aufspaltung von Datenbanken besteht darin, der Implementierungskonfiguration von Commerce Verbindungs- und Ressourceninformationen hinzuzufügen. `env.php`.

So aktualisieren Sie die Bereitstellungskonfiguration:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zu der [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Sichern Sie Ihre Bereitstellungskonfiguration:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Öffnen `<magento_root>/app/etc/env.php` in einem Texteditor erstellen und mithilfe der in den folgenden Abschnitten beschriebenen Richtlinien aktualisieren.

### Datenbankverbindungen aktualisieren

Suchen Sie den Block, der mit `'default'` (unter `'connection'`) und fügen Sie `'checkout'` und `'sales'` Abschnitte. Ersetzen Sie die Beispielwerte durch die für Ihre Site geeigneten Werte.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Ressourcen aktualisieren

Suchen Sie den Block, der mit `'resource'` und hinzufügen `'checkout'` und `'sales'` -Abschnitte wie folgt hinzu:

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Referenzskripte

In diesem Abschnitt finden Sie Skripte, mit denen Sie eine vollständige Liste der betroffenen Tabellen drucken können, ohne Aktionen daran vornehmen zu müssen. Sie können sie verwenden, um zu sehen, welche Tabellen betroffen sind, bevor Sie Datenbanken manuell aufteilen. Dies kann nützlich sein, wenn Sie Erweiterungen verwenden, die die [Datenbankschema](https://glossary.magento.com/database-schema).

So verwenden Sie diese Skripte:

1. Erstellen Sie ein SQL-Skript mit dem Inhalt jedes Skripts in diesem Abschnitt.
1. Ersetzen Sie in jedem Skript `<your main DB name>` mit dem Namen Ihrer Commerce-Datenbank.

   In diesem Thema lautet der Beispiel-Datenbankname `magento`.

1. Führen Sie jedes Skript aus dem `mysql>` Eingabeaufforderung `source <script name>`
1. Überprüfen Sie die Ausgabe.
1. Kopieren Sie das Ergebnis jedes Skripts in ein anderes SQL-Skript und entfernen Sie die Pipe-Zeichen (`|`).
1. Führen Sie jedes Skript aus dem `mysql>` Eingabeaufforderung `source <script name>`.

   Beim Ausführen dieses zweiten Skripts werden die Aktionen in Ihrer Haupt-Commerce-Datenbank ausgeführt.

### Fremdschlüssel entfernen (Verkaufstabellen)

Dieses Skript entfernt ausländische Schlüssel, die auf nicht verkaufte Tabellen verweisen, aus der Verkaufsdatenbank.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Fremdschlüssel entfernen (Anführungszeichen)

Dieses Skript entfernt Fremdschlüssel, die auf nichtkursive Tabellen verweisen, aus Anführungszeichentabellen.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Absatztabellen ablegen

Dieses Skript entfernt Verkaufstabellen aus der Commerce-Datenbank.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Löschen von Anführungszeichentabellen

Legen Sie alle Tabellen ab, die mit `quote_`.
