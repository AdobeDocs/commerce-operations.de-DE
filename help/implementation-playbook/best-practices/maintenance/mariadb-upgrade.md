---
title: Voraussetzungen für ein Adobe Commerce-Upgrade für MariaDB
description: Erfahren Sie, wie Sie Ihre Adobe Commerce-Datenbank auf ein Upgrade von MariaDB von einer früheren Version vorbereiten.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Upgrade-Voraussetzungen für MariaDB

Vor einem Upgrade von Adobe Commerce auf die Cloud-Infrastruktur müssen Sie möglicherweise auch Ihre Datenbanksoftware aktualisieren, wenn Sie MariaDB verwenden. Beispiel:

- Adobe Commerce 2.4.6 mit MariaDB-Version 10.5.1 oder höher
- Adobe Commerce 2.3.5 mit MariaDB Version 10.3 oder früher

## Adobe Commerce 2.4.6

Ab MariaDB 10.5.1 werden Spalten mit alten zeitlichen Formaten in der Ausgabe der `SHOW CREATE TABLE`-, `SHOW COLUMNS`-, `DESCRIBE`-Anweisungen sowie in der `COLUMN_TYPE` Spalte der `INFORMATION_SCHEMA.COLUMNS` mit einem `/* mariadb-5.3 */` markiert. [Siehe MariaDB-](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce kann die Datumsspalten aufgrund des MariaDB-Kommentars nicht einem richtigen Datentyp zuordnen, was zu unerwartetem Verhalten im benutzerdefinierten Code führen kann.

Um unerwartetes Verhalten beim Upgrade von MariaDB von älteren Versionen auf Version 10.6 zu vermeiden, empfiehlt Adobe, die Spalten in das neue interne Format zu migrieren.

### Standardkonfiguration

In MariaDB 10.1.2 wurde von MySQL 5.6 ein neues Zeitformat eingeführt. Mit der Systemvariablen `mysql56_temporal_format` kann die Datenbank das alte Datumsformat automatisch in das neue konvertieren, wenn eine Tabelle ALTER ausgeführt oder die Datenbank importiert wird. Die Standardkonfiguration für `mysql56_temporal_format` ist in Adobe Commerce in der Cloud-Infrastruktur immer aktiviert.

### Datumsspalten migrieren

Die folgende Abfrage zeigt die betroffenen Tabellen und Spalten, die nach einem Upgrade von MariaDB auf 10.5.1 oder höher migriert werden müssen:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

Für die Migration der Spalten in das neue interne Datumsformat ist der erneute Import der Datenbank oder die Ausführung einer Änderung an der identifizierten Spalte mit derselben Spaltendefinition erforderlich. Die folgende Abfrage generiert die erforderlichen alternativen Abfragen:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Um unerwartetes Verhalten zu vermeiden, ist es wichtig, die Spalten _das neue interne Datumsformat (vor_ Bereitstellung des neuen Codes) zu migrieren.

## Adobe Commerce 2.3.5

Upgrade des MariaDB-Service in der Cloud-Infrastruktur von Version 10.0 oder 10.2 auf Version 10.3, 10.4 oder 10.5. Für MariaDB Version 10.3 und höher muss die Datenbank das dynamische Tabellenzeilenformat verwenden. Für Adobe Commerce muss die InnoDB-Speicher-Engine für Tabellen verwendet werden. In diesem Artikel wird erläutert, wie Sie Ihre Datenbank aktualisieren können, um diese MariaDB-Anforderungen zu erfüllen.

Senden Sie nach der Datenbankvorbereitung ein Adobe Commerce-Support-Ticket, um die Version des MariaDB-Service in Ihrer Cloud-Infrastruktur zu aktualisieren, bevor Sie mit dem Adobe Commerce-Upgrade-Prozess fortfahren.

### Datenbank für das Upgrade vorbereiten

Bevor das Adobe Commerce-Supportteam mit dem Upgrade-Prozess beginnt, sollten Sie Ihre Datenbank vorbereiten, indem Sie Ihre Datenbanktabellen konvertieren:

- Konvertieren des Zeilenformats von `COMPACT` nach `DYNAMIC`
- Ändern der Speicher-Engine von `MyISAM` in `InnoDB`

Beachten Sie bei der Planung und dem Zeitplan der Konvertierung die folgenden Überlegungen:

- Die Konvertierung von `COMPACT` in `DYNAMIC` kann bei einer großen Datenbank mehrere Stunden dauern.

- Führen Sie zum Schutz vor Datenbeschädigungen keine Konvertierungsarbeiten an einer Live-Site durch.

- Schließen Sie die Konversionsarbeiten in einer Zeit mit geringem Traffic auf Ihrer Site ab.

- Wechseln Sie die Site in [Wartungsmodus](../../../installation/tutorials/maintenance-mode.md), bevor Sie die Befehle zum Konvertieren von Datenbanktabellen ausführen.

#### Datenbanktabellen-Zeilenformat konvertieren

Sie können Tabellen auf einem Knoten in Ihrem Cluster konvertieren. Die Änderungen werden automatisch auf den anderen Service-Knoten repliziert.

1. Verwenden Sie in Ihrer Adobe Commerce in der Cloud-Infrastrukturumgebung SSH, um eine Verbindung zu Knoten 1 herzustellen.

1. Anmelden bei MariaDB.

1. Identifizieren Sie die Tabellen, die vom kompakten in das dynamische Format konvertiert werden sollen.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Bestimmen Sie die Tabellengrößen, um die Konvertierungsarbeiten zu planen.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Die Konvertierung größerer Tabellen dauert länger. Überprüfen Sie die Tabellen und stapeln Sie die Konvertierungsarbeiten nach Priorität und Tabellengröße, um die erforderlichen Wartungsfenster zu planen.

1. Konvertieren Sie alle Tabellen nacheinander in das dynamische Format.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Datenbanktabellen-Speicherformat konvertieren

Sie können Tabellen auf einem Knoten in Ihrem Cluster konvertieren. Die Änderungen werden automatisch auf den anderen Service-Knoten repliziert.

Der Prozess zum Konvertieren des Speicherformats unterscheidet sich für Adobe Commerce Starter- und Adobe Commerce Pro-Projekte.

- Verwenden Sie für die Startarchitektur den Befehl MySQL `ALTER` , um das Format zu konvertieren.
- Verwenden Sie in der Pro-Architektur die Befehle MySQL `CREATE` und `SELECT` , um eine Datenbanktabelle mit `InnoDB` Speicher zu erstellen und die Daten aus der vorhandenen Tabelle in die neue Tabelle zu kopieren. Durch diese Methode wird sichergestellt, dass die Änderungen auf allen Knoten in Ihrem Cluster repliziert werden.

**Konvertieren des Tabellenspeicherformats für Adobe Commerce Pro-Projekte**

1. Identifizieren Sie Tabellen, die `MyISAM` Speicher verwenden.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertieren Sie alle Tabellen einzeln in `InnoDB` Speicherformat.

   - Benennen Sie die vorhandene Tabelle um, um Namenskonflikte zu vermeiden.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Erstellen Sie eine Tabelle, die `InnoDB` Speicher verwendet, indem Sie die Daten aus der vorhandenen Tabelle verwenden.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Stellen Sie sicher, dass die neue Tabelle über alle erforderlichen Daten verfügt.

   - Löschen Sie die umbenannte ursprüngliche Tabelle.


**Konvertieren des Tabellenspeicherformats für Adobe Commerce Starter-Projekte**

1. Identifizieren Sie Tabellen, die `MyISAM` Speicher verwenden.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertieren von Tabellen, die `MyISAM` Speicher verwenden, in `InnoDB` Speicher.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Datenbankkonvertierung überprüfen

Überprüfen Sie am Tag vor dem geplanten Upgrade auf MariaDB-Version 10.3, 10.4 oder 10.6, ob alle Tabellen das richtige Zeilenformat und die richtige Speicher-Engine haben. Die Überprüfung ist erforderlich, da Code-Bereitstellungen, die nach Abschluss der Konvertierung vorgenommen werden, dazu führen können, dass einige Tabellen auf ihre ursprüngliche Konfiguration zurückgesetzt werden.

1. Melden Sie sich bei Ihrer Datenbank an.

1. Suchen Sie nach Tabellen, die noch das `COMPACT` Zeilenformat aufweisen.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Überprüfen Sie, ob Tabellen noch das `MyISAM` Speicherformat verwenden

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Wenn Tabellen zurückgesetzt wurden, wiederholen Sie die Schritte, um das Tabellenzeilenformat und die Speicher-Engine zu ändern.

### Ändern der Speicher-Engine

Siehe [Konvertieren von MyISAM-Tabellen in InnoDB](../planning/database-on-cloud.md).
