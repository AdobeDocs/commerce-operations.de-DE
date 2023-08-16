---
title: Adobe Commerce-Upgrade-Voraussetzungen für MariaDB
description: Erfahren Sie, wie Sie Ihre Adobe Commerce-Datenbank für die Aktualisierung von MariaDB von einer früheren Version vorbereiten.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Upgrade-Voraussetzungen für MariaDB

Die Aktualisierung des MariaDB-Diensts auf der Cloud-Infrastruktur von Version 10.0 oder 10.2 auf Version 10.3, 10.4 oder 10.5. MariaDB-Version 10.3 und höher erfordert, dass die Datenbank das dynamische Tabellenzeilenformat verwendet, und Adobe Commerce erfordert die Verwendung der InnoDB-Speicher-Engine für Tabellen. In diesem Artikel wird beschrieben, wie Sie Ihre Datenbank aktualisieren, um diese MariaDB-Anforderungen zu erfüllen.

Nachdem Sie die Datenbank vorbereitet haben, senden Sie ein Adobe Commerce-Supportticket, um die MariaDB-Dienstversion in Ihrer Cloud-Infrastruktur zu aktualisieren, bevor Sie mit dem Adobe Commerce-Upgrade-Prozess fortfahren.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur mit MariaDB-Version 10.3 oder früher.

## Vorbereiten Ihrer Datenbank auf die Aktualisierung

Bevor das Adobe Commerce-Supportteam mit dem Upgrade-Prozess beginnt, bereiten Sie Ihre Datenbank vor, indem Sie Ihre Datenbanktabellen konvertieren:

- Konvertieren des Zeilenformats aus `COMPACT` nach `DYNAMIC`
- Ändern Sie die Speicher-Engine von `MyISAM` nach `InnoDB`

Beachten Sie beim Planen und Planen der Konvertierung die folgenden Überlegungen:

- Konvertieren aus `COMPACT` nach `DYNAMIC` -Tabellen können bei einer großen Datenbank mehrere Stunden dauern.

- Führen Sie zur Vermeidung von Datenbeschädigung keine Konversionsarbeiten auf einer Live-Site durch.

- Schließen Sie die Konversionsarbeit während eines niedrigen Traffic-Zeitraums auf Ihrer Site ab.

- Wechseln Sie zu [Wartungsmodus](../../../installation/tutorials/maintenance-mode.md) bevor Sie die Befehle zum Konvertieren von Datenbanktabellen ausführen.

### Tabellenzeilenformat der Datenbank konvertieren

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

Überprüfen Sie am Tag vor der geplanten Aktualisierung auf die MariaDB-Version 10.3, 10.4 oder 10.6, ob alle Tabellen über das richtige Zeilenformat und die richtige Speichermodul verfügen. Eine Verifizierung ist erforderlich, da Code-Bereitstellungen nach Abschluss der Konvertierung dazu führen können, dass einige Tabellen wieder in ihre ursprüngliche Konfiguration zurückgesetzt werden.

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

## Speicher-Engine ändern

Siehe [Konvertieren von MyISAM-Tabellen in InnoDB](../planning/database-on-cloud.md).

## Zusätzliche Informationen

- [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](../planning/database-on-cloud.md)
- [Aktualisieren von MariaDB von 10.0 auf 12.0 für Adobe Commerce on Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)
