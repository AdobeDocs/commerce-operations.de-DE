---
title: Daten migrieren
description: Erfahren Sie, wie Sie mit der Migration von Daten aus Magento 1 zu Magento 2 beginnen können. [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Daten migrieren

Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich bei Ihrem Anwendungsserver als [der Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Wechseln Sie zum Installationsverzeichnis der Anwendung oder stellen Sie sicher, dass es zum System hinzugefügt wird. `PATH`.

Siehe [Erste Schritte](overview.md#first-steps) für weitere Details.

## Führen Sie den Datenmigrationsbefehl aus

Um mit der Datenmigration zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`; Dieses Argument ist erforderlich

In diesem Schritt wird die [!DNL Data Migration Tool] erstellt zusätzliche Tabellen und Trigger für die Migrationstabellen in der Datenbank von Magento 1. Sie werden im [inkrementell/delta](delta.md) Migrationsschritt. Zusätzliche Tabellen enthalten Informationen zu geänderten Datensätzen nach der letzten Migrationsausführung. Datenbanktabellen werden zum Ausfüllen dieser zusätzlichen Trigger verwendet. Wenn also ein neuer Vorgang für die jeweilige Tabelle ausgeführt wird (ein Datensatz wird hinzugefügt/geändert/entfernt), speichern diese Datenbankserver Informationen über diesen Vorgang in der zusätzlichen Tabelle. Wenn wir einen Delta-Migrationsprozess ausführen, wird die [!DNL Data Migration Tool] überprüft diese Tabellen auf die nicht verarbeiteten Datensätze und migriert den erforderlichen Inhalt in die Datenbank von Magento 2.

Jede neue Tabelle enthält:

* `m2_cl` prefix
* `INSERT`, `UPDATE`, `DELETE` Ereignis-Trigger.

Beispiel: für die `sales_flat_order` die [!DNL Data Migration Tool] erstellt:

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
>Die [!DNL Data Migration Tool] speichert den aktuellen Fortschritt während der Ausführung. Wenn Fehler oder ein Benutzereingriff die Ausführung stoppt, setzt das Tool den Fortschritt beim letzten bekannten guten Zustand fort. So erzwingen Sie die [!DNL Data Migration Tool] , um von Anfang an zu starten, verwenden Sie die `--reset` -Argument. In diesem Fall wird empfohlen, die Datenbank-Dump von Magento 2 wiederherzustellen, um eine Duplizierung bereits migrierter Daten zu verhindern.


## Mögliche Konsistenzfehler

Während der Ausführung wird die [!DNL Data Migration Tool] kann Inkonsistenzen zwischen Magento 1- und Magento 2-Datenbanken melden und Meldungen wie die folgenden anzeigen:

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

Siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360033020451) für weitere Informationen und Empfehlungen.

## Nächster Migrationsschritt

[Migrieren von Änderungen](delta.md)
