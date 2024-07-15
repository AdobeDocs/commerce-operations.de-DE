---
title: Voraussetzungen für das Adobe Commerce-Upgrade für MariaDB
description: Erfahren Sie, wie Sie Ihre Adobe Commerce-Datenbank für die Aktualisierung von MariaDB von einer früheren Version vorbereiten.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Upgrade-Voraussetzungen für MariaDB

Vor der Aktualisierung von Adobe Commerce auf Cloud-Infrastruktur müssen Sie möglicherweise auch Ihre Datenbanksoftware aktualisieren, wenn Sie MariaDB verwenden. Beispiel:

- Adobe Commerce 2.4.6 mit MariaDB-Version 10.5.1 oder höher
- Adobe Commerce 2.3.5 mit MariaDB-Version 10.3 oder früher

## Adobe Commerce 2.4.6

Ab MariaDB 10.5.1 werden Spalten mit alten temporalen Formaten in der Ausgabe der Anweisungen `SHOW CREATE TABLE`, `SHOW COLUMNS` und `DESCRIBE` sowie in der Spalte `COLUMN_TYPE` der Tabelle `INFORMATION_SCHEMA.COLUMNS` mit einem `/* mariadb-5.3 */` -Kommentar markiert. [Siehe MariaDB-Dokumentation](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce kann die Datumsspalten aufgrund des MariaDB-Kommentars nicht einem geeigneten Datentyp zuordnen, was zu unerwartetem Verhalten im benutzerspezifischen Code führen kann.

Um unerwartetes Verhalten bei der Aktualisierung von MariaDB von älteren Versionen auf Version 10.6 zu vermeiden, empfiehlt Adobe, die Spalten in das neue interne Format zu migrieren.

### Standardkonfiguration

In MariaDB 10.1.2 wurde ein neues temporales Format von MySQL 5.6 eingeführt. Mit der Systemvariablen `mysql56_temporal_format` kann die Datenbank das alte Datumsformat automatisch in das neue konvertieren, wenn eine geänderte Tabelle ausgeführt oder eine Datenbank importiert wird. Die Standardkonfiguration für `mysql56_temporal_format` ist in Adobe Commerce in der Cloud-Infrastruktur immer aktiviert.

### Datumsspalten migrieren

Die folgende Abfrage zeigt die betroffene Tabelle und die Spalten, die nach der Aktualisierung von MariaDB auf 10.5.1 oder höher migriert werden müssen:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

Für die Migration der Spalten in das neue interne Datumsformat ist es erforderlich, die Datenbank erneut zu importieren oder Änderungen an der identifizierten Spalte mit derselben Spaltendefinition auszuführen. Die folgende Abfrage erzeugt die erforderlichen Abfrageänderungen:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Es ist wichtig, die Spalten in das neue interne Datumsformat _zu migrieren, bevor_ den neuen Code bereitstellt, um unerwartetes Verhalten zu vermeiden.

## Adobe Commerce 2.3.5

Die Aktualisierung des MariaDB-Diensts auf der Cloud-Infrastruktur von Version 10.0 oder 10.2 auf Version 10.3, 10.4 oder 10.5. MariaDB-Version 10.3 und höher erfordert, dass die Datenbank das dynamische Tabellenzeilenformat verwendet, und Adobe Commerce erfordert die Verwendung der InnoDB-Speicher-Engine für Tabellen. In diesem Artikel wird beschrieben, wie Sie Ihre Datenbank aktualisieren, um diese MariaDB-Anforderungen zu erfüllen.

Nachdem Sie die Datenbank vorbereitet haben, senden Sie ein Adobe Commerce-Supportticket, um die MariaDB-Dienstversion in Ihrer Cloud-Infrastruktur zu aktualisieren, bevor Sie mit dem Adobe Commerce-Upgrade-Prozess fortfahren.

### Vorbereiten Ihrer Datenbank auf die Aktualisierung

Bevor das Adobe Commerce-Supportteam mit dem Upgrade-Prozess beginnt, bereiten Sie Ihre Datenbank vor, indem Sie Ihre Datenbanktabellen konvertieren:

- Konvertieren des Zeilenformats von `COMPACT` in `DYNAMIC`
- Ändern Sie die Speicher-Engine von `MyISAM` in `InnoDB`

Beachten Sie beim Planen und Planen der Konvertierung die folgenden Überlegungen:

- Die Konvertierung von `COMPACT` in `DYNAMIC` Tabellen kann bei einer großen Datenbank mehrere Stunden dauern.

- Führen Sie zur Vermeidung von Datenbeschädigung keine Konversionsarbeiten auf einer Live-Site durch.

- Schließen Sie die Konversionsarbeit während eines niedrigen Traffic-Zeitraums auf Ihrer Site ab.

- Wechseln Sie Ihre Site in den [Wartungsmodus](../../../installation/tutorials/maintenance-mode.md) , bevor Sie die Befehle zum Konvertieren von Datenbanktabellen ausführen.

#### Tabellenzeilenformat der Datenbank konvertieren

Sie können Tabellen auf einem Knoten im Cluster konvertieren. Die Änderungen werden automatisch auf den anderen Dienstknoten repliziert.

1. Verwenden Sie in Ihrer Adobe Commerce-Umgebung für Cloud-Infrastruktur SSH, um eine Verbindung zu Knoten 1 herzustellen.

1. Melden Sie sich bei MariaDB an.

1. Identifizieren Sie Tabellen, die vom kompakten in das dynamische Format konvertiert werden sollen.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Legen Sie die Tabellengrößen fest, damit Sie die Konvertierungsarbeit planen können.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Die Konvertierung größerer Tabellen dauert länger. Überprüfen Sie die Tabellen und erstellen Sie einen Batch der Konvertierungsarbeit nach Priorität und Tabellengröße, um die erforderlichen Wartungsfenster zu planen.

1. Konvertieren Sie alle Tabellen einzeln in das dynamische Format.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Dateispeicherformat der Datenbank konvertieren

Sie können Tabellen auf einem Knoten im Cluster konvertieren. Die Änderungen werden automatisch auf den anderen Dienstknoten repliziert.

Die Konvertierung des Speicherformats unterscheidet sich bei Adobe Commerce Starter- und Adobe Commerce Pro-Projekten.

- Verwenden Sie für Starter-Architektur den Befehl MySQL `ALTER` , um das Format zu konvertieren.
- Verwenden Sie in der Pro-Architektur die Befehle MySQL `CREATE` und `SELECT` , um eine Datenbanktabelle mit `InnoDB` Speicher zu erstellen und die Daten aus der vorhandenen Tabelle in die neue Tabelle zu kopieren. Diese Methode stellt sicher, dass die Änderungen auf allen Knoten im Cluster repliziert werden.

**Konvertieren des Tabellenspeicherformats für Adobe Commerce Pro-Projekte**

1. Identifizieren Sie Tabellen, die `MyISAM` Speicher verwenden.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertieren Sie alle Tabellen einzeln in das Speicherformat `InnoDB`.

   - Benennen Sie die vorhandene Tabelle um, um Namenskonflikte zu vermeiden.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Erstellen Sie eine Tabelle, die den `InnoDB`-Speicher verwendet, indem Sie die Daten aus der vorhandenen Tabelle verwenden.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Stellen Sie sicher, dass die neue Tabelle alle erforderlichen Daten enthält.

   - Löschen Sie die ursprüngliche Tabelle, die Sie umbenannt haben.


**Konvertieren des Tabellenspeicherformats für Adobe Commerce Starter-Projekte**

1. Identifizieren Sie Tabellen, die `MyISAM` Speicher verwenden.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertieren Sie Tabellen, die den `MyISAM`-Speicher verwenden, in den `InnoDB`-Speicher.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Überprüfen der Datenbankkonvertierung

Überprüfen Sie am Tag vor der geplanten Aktualisierung auf die MariaDB-Version 10.3, 10.4 oder 10.6, ob alle Tabellen über das richtige Zeilenformat und die richtige Speichermodul verfügen. Eine Verifizierung ist erforderlich, da Code-Bereitstellungen nach Abschluss der Konvertierung dazu führen können, dass einige Tabellen wieder in ihre ursprüngliche Konfiguration zurückgesetzt werden.

1. Melden Sie sich bei Ihrer Datenbank an.

1. Suchen Sie nach Tabellen, die weiterhin das Zeilenformat `COMPACT` aufweisen.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Suchen Sie nach Tabellen, die weiterhin das Speicherformat `MyISAM` verwenden.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Wenn Tabellen zurückgesetzt wurden, wiederholen Sie die Schritte zum Ändern des Tabellenzeilenformats und der Speicher-Engine.

### Speicher-Engine ändern

Siehe [Konvertieren von MyISAM-Tabellen in InnoDB](../planning/database-on-cloud.md).
