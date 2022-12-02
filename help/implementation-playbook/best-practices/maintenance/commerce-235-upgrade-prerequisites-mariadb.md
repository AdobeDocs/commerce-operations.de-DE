---
title: Voraussetzungen für das Adobe Commerce 2.3.5-Upgrade für MariaDB
description: Erfahren Sie, wie Sie Ihre Adobe Commerce-Datenbank für die Aktualisierung von Adobe Commerce 2.3.5 vorbereiten.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 071e88c6a07df0f74b6d4b09cce858710c9332cc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Voraussetzungen für die Aktualisierung auf Adobe Commerce 2.3.5

In diesem Artikel wird beschrieben, wie Sie Ihre Datenbank vorbereiten, wenn Sie von Version 2.3.4 oder früher auf Adobe Commerce 2.3.5 aktualisieren.

Für dieses Upgrade muss das Supportteam MariaDB auf der Cloud-Infrastruktur von MariaDB 10.0 auf 10.2 aktualisieren, um die Anforderungen für Adobe Commerce-Version 2.3.5 und höher zu erfüllen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur mit Adobe Commerce-Version 2.3.4 oder früher und MariaDB-Version 10.0 oder früher.

## Vorbereiten Ihrer Datenbank auf die Aktualisierung

Bereiten Sie Ihre Datenbank vor Beginn des Aktualisierungsprozesses durch Konvertieren Ihrer Datenbanktabellen vor:

- Konvertieren des Zeilenformats aus `COMPACT` nach `DYNAMIC`
- Konvertieren der Speicher-Engine aus `MyISAM` nach `InnoDB`

Beachten Sie beim Planen und Planen der Konvertierung die folgenden Überlegungen:

- Konvertieren aus `COMPACT` nach `DYNAMIC` -Tabellen können bei einer großen Datenbank mehrere Stunden dauern.

- Führen Sie zur Vermeidung von Datenbeschädigung keine Konversionsarbeiten auf einer Live-Site durch.

- Schließen Sie die Konversionsarbeit während eines niedrigen Traffic-Zeitraums auf Ihrer Site ab.

- Wechseln Sie zu [Wartungsmodus](../../../installation/tutorials/maintenance-mode.md) bevor Sie die Befehle zum Konvertieren von Datenbanktabellen ausführen.

### Tabellenzeilenformat der Datenbank konvertieren

Sie können Tabellen auf einem Knoten im Cluster konvertieren. Die Änderungen werden automatisch auf den anderen Dienstknoten repliziert.

1. Verwenden Sie in Ihrer Adobe Commerce-Umgebung für Cloud-Infrastruktur SSH, um eine Verbindung zu Knoten 1 herzustellen.

1. Melden Sie sich bei MariaDB an.

1. Identifizieren Sie Tabellen, die von einem kompakten in ein dynamisches Format konvertiert werden sollen.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
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

### Dateispeicherformat der Datenbank konvertieren

Sie können Tabellen auf einem Knoten im Cluster konvertieren. Die Änderungen werden automatisch auf den anderen Dienstknoten repliziert.

Die Konvertierung des Speicherformats unterscheidet sich bei Adobe Commerce Starter- und Adobe Commerce Pro-Projekten.

- Verwenden Sie für die Starter-Architektur MySQL `ALTER` zum Konvertieren des Formats.
- Verwenden Sie auf Pro-Architektur MySQL `CREATE` und `SELECT` Befehle zum Erstellen einer Datenbanktabelle mit `InnoDB` speichern und kopieren Sie die Daten aus der vorhandenen Tabelle in die neue Tabelle. Diese Methode stellt sicher, dass die Änderungen auf allen Knoten im Cluster repliziert werden.

**Konvertieren des Tabellenspeicherformats für Adobe Commerce Pro-Projekte**

1. Identifizieren von Tabellen, die `MyISAM` Speicher.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Alle Tabellen in `InnoDB` Speicherformat einzeln.

   - Benennen Sie die vorhandene Tabelle um, um Namenskonflikte zu vermeiden.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Erstellen Sie eine Tabelle, die `InnoDB` Speicher mithilfe der Daten aus der vorhandenen Tabelle.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Stellen Sie sicher, dass die neue Tabelle alle erforderlichen Daten enthält.

   - Löschen Sie die ursprüngliche Tabelle, die Sie umbenannt haben.


**Konvertieren des Tabellenspeicherformats für Adobe Commerce Starter-Projekte**

1. Identifizieren von Tabellen, die `MyISAM` Speicher.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertieren von Tabellen, die `MyISAM` Speicher in `InnoDB` Speicher.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### Überprüfen der Datenbankkonvertierung

Überprüfen Sie am Tag vor der geplanten Aktualisierung auf MariaDB Version 10.2, ob alle Tabellen über das richtige Zeilenformat und die richtige Speichermodul verfügen. Eine Verifizierung ist erforderlich, da Code-Bereitstellungen nach Abschluss der Konvertierung dazu führen können, dass einige Tabellen wieder in ihre ursprüngliche Konfiguration zurückgesetzt werden.

1. Melden Sie sich bei Ihrer Datenbank an.

1. Suchen Sie nach Tabellen, für die noch die Variable `COMPACT` Zeilenformat.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Suchen Sie nach Tabellen, die weiterhin die `MyISAM` Speicherformat

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Wenn Tabellen zurückgesetzt wurden, wiederholen Sie die Schritte zum Ändern des Tabellenzeilenformats und der Speicher-Engine.

## Zusätzliche Informationen

[Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](../planning/database-on-cloud.md)
