---
title: Daten migrieren
description: Erfahren Sie, wie Sie mit der Migration von Daten von Magento 1 auf Magento 2 mit dem  [!DNL Data Migration Tool] beginnen.
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Daten migrieren

Bevor Sie beginnen, führen Sie die folgenden Schritte aus, um Folgendes vorzubereiten:

1. Melden Sie sich bei Ihrem Anwendungs-Server [als „Dateisystembesitzer“ ](../../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie zum Installationsverzeichnis der Anwendung oder stellen Sie sicher, dass es zum `PATH` hinzugefügt wird.

Weitere Informationen finden Sie [ Abschnitt ](overview.md#first-steps) Schritte .

## Ausführen des Datenmigrationsbefehls

Um mit der Datenmigration zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn Fehler bei der Integritätsprüfung auftreten.

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`. Dieses Argument ist erforderlich

In diesem Schritt erstellt der [!DNL Data Migration Tool] zusätzliche Tabellen und Trigger für die Migrationstabellen in der Magento 1-Datenbank. Sie werden im Migrationsschritt [inkrementell/delta](delta.md) verwendet. Zusätzliche Tabellen enthalten Informationen zu geänderten Datensätzen nach der endgültigen Ausführung der Migration. Datenbanktabellen werden zum Ausfüllen dieser zusätzlichen Trigger Trigger verwendet. Wenn also ein neuer Vorgang für eine bestimmte Tabelle ausgeführt wird (ein Datensatz wird hinzugefügt/geändert/entfernt), speichern diese Datenbanktabellen Informationen über diesen Vorgang in der zusätzlichen Tabelle. Wenn wir einen Delta-Migrationsprozess ausführen, prüft der [!DNL Data Migration Tool] diese Tabellen auf die nicht verarbeiteten Datensätze und migriert die erforderlichen Inhalte in die Magento 2-Datenbank.

Jede neue Tabelle enthält:

* `m2_cl`
* `INSERT`, `UPDATE`, `DELETE` Ereignis-Trigger.

Für den `sales_flat_order` erstellt der [!DNL Data Migration Tool] beispielsweise:

* `m2_cl_sales_flat_order`:

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
>Der [!DNL Data Migration Tool] speichert den aktuellen Fortschritt während der Ausführung. Wenn Fehler oder ein Benutzereingriff die Ausführung stoppen, setzt das Tool den Fortschritt im letzten zweifelsfrei funktionierenden Zustand fort. Um die Ausführung der [!DNL Data Migration Tool] von Anfang an zu erzwingen, verwenden Sie das `--reset`. In diesem Fall empfehlen wir, den Magento 2-Datenbank-Dump wiederherzustellen, um das Duplizieren zuvor migrierter Daten zu verhindern.


## Mögliche Konsistenzfehler

Während der Ausführung meldet der [!DNL Data Migration Tool] möglicherweise Inkonsistenzen zwischen Magento 1- und Magento 2-Datenbanken und zeigt Meldungen wie die folgenden an:

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

Weitere Informationen [ Empfehlungen finden ](https://support.magento.com/hc/en-us/articles/360033020451) im Abschnitt „Fehlerbehebung“ dieses Handbuchs.

## Nächster Migrationsschritt

[Änderungen migrieren](delta.md)
