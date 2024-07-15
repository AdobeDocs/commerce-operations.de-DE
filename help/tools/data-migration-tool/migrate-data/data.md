---
title: Daten migrieren
description: Erfahren Sie, wie Sie mit der Migration von Daten von Magento 1 zu Magento 2 mit dem  [!DNL Data Migration Tool] beginnen.
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Daten migrieren

Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich bei Ihrem Anwendungsserver als [Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md) an.
1. Wechseln Sie zum Installationsverzeichnis der Anwendung oder stellen Sie sicher, dass es Ihrem System `PATH` hinzugefügt wird.

Weitere Informationen finden Sie im Abschnitt [Erste Schritte](overview.md#first-steps) .

## Führen Sie den Datenmigrationsbefehl aus

Um mit der Datenmigration zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`; dieses Argument ist erforderlich

In diesem Schritt erstellt der [!DNL Data Migration Tool] zusätzliche Tabellen und Trigger für die Migrationstabellen in der Magento 1-Datenbank. Sie werden im Migrationsschritt [inkrementell/delta](delta.md) verwendet. Zusätzliche Tabellen enthalten Informationen zu geänderten Datensätzen nach der letzten Migrationsausführung. Datenbanktabellen werden zum Ausfüllen dieser zusätzlichen Trigger verwendet. Wenn also ein neuer Vorgang für die jeweilige Tabelle ausgeführt wird (ein Datensatz wird hinzugefügt/geändert/entfernt), speichern diese Datenbankserver Informationen über diesen Vorgang in der zusätzlichen Tabelle. Wenn wir einen Delta-Migrationsprozess ausführen, prüft [!DNL Data Migration Tool] diese Tabellen auf nicht verarbeitete Datensätze und migriert den erforderlichen Inhalt in die Magento 2-Datenbank.

Jede neue Tabelle enthält:

* `m2_cl` Präfix
* `INSERT`, `UPDATE`, `DELETE` Ereignisereignis-Trigger.

Beispielsweise erstellt der [!DNL Data Migration Tool] für den `sales_flat_order` Folgendes:

* `m2_cl_sales_flat_order` table:

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` Trigger:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>Die [!DNL Data Migration Tool] speichert ihren aktuellen Fortschritt während der Ausführung. Wenn Fehler oder ein Benutzereingriff die Ausführung stoppt, setzt das Tool den Fortschritt beim letzten bekannten guten Zustand fort. Um die Ausführung von [!DNL Data Migration Tool] vom Anfang an zu erzwingen, verwenden Sie das `--reset` -Argument. In diesem Fall wird empfohlen, den Dump Ihrer Magento 2-Datenbank wiederherzustellen, um eine Duplizierung bereits migrierter Daten zu verhindern.


## Mögliche Konsistenzfehler

Während der Ausführung kann das [!DNL Data Migration Tool] Inkonsistenzen zwischen Magento 1- und Magento 2-Datenbanken melden und Nachrichten wie die folgenden anzeigen:

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Weitere Informationen und Empfehlungen finden Sie im Abschnitt [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360033020451) dieses Handbuchs.

## Nächster Migrationsschritt

[Migrieren von Änderungen](delta.md)
