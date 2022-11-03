---
title: Voraussetzungen für das Adobe Commerce 2.3.5-Upgrade für MariaDB
description: Erfahren Sie, wie Sie Ihre Adobe Commerce-Datenbank für die Aktualisierung von Adobe Commerce 2.3.5 vorbereiten.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Voraussetzungen für die Aktualisierung auf Adobe Commerce 2.3.5

In diesem Artikel wird beschrieben, wie Sie Ihre Datenbank vorbereiten, wenn Sie von Version 2.3.4 oder früher auf Adobe Commerce 2.3.5 aktualisieren.

Für dieses Upgrade muss das Supportteam MariaDB auf der Cloud-Infrastruktur von MariaDB 10.0 auf 10.2 aktualisieren, um die Anforderungen an Adobe Commerce zu erfüllen. Adobe Commerce-Version 2.3.5 und höher.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur mit Adobe Commerce-Version 2.3.4 oder früher und MariaDB-Version 10.0 oder früher.

## Vorbereiten Ihrer Datenbank auf die Aktualisierung

Bevor das Adobe Commerce-Supportteam mit dem Upgrade-Prozess beginnt, müssen Sie Ihre Datenbank vorbereiten, indem Sie das Format für alle Tabellen aus `COMPACT` nach `DYNAMIC`. Sie müssen außerdem den Speicher-Engine-Typ von `MyISAM` nach `InnoDB`.

Beachten Sie beim Erstellen des Plans und des Zeitplans für die Konvertierung der Datenbank die folgenden Richtlinien.

- Konvertieren aus `COMPACT` nach `DYNAMIC` -Tabellen können bei einer großen Datenbank mehrere Stunden dauern.

- Führen Sie die Konvertierung nicht durch, wenn Ihre Site live ist, um Datenbeschädigungen zu verhindern.

- Schließen Sie die Konversionsarbeit während eines niedrigen Traffic-Zeitraums auf Ihrer Site ab.

- Wechseln Sie zu [Wartungsmodus](../../../installation/tutorials/maintenance-mode.md) vor dem Ausführen der `ALTER` Befehle.

### Konvertieren von Datenbanktabellen

Sie können Tabellen auf einem Knoten im Cluster konvertieren. Die Änderungen werden auf den anderen Kernknoten in Ihrem Cluster repliziert.

1. Verwenden Sie in Ihrer Adobe Commerce-Umgebung für Cloud-Infrastruktur SSH, um eine Verbindung zu Knoten 1 herzustellen.

1. Melden Sie sich bei MariaDB an.

1. Konvertieren Sie das Tabellenformat.

   - Identifizieren Sie Tabellen, die von einem kompakten in ein dynamisches Format konvertiert werden sollen.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Legen Sie die Tabellengrößen fest, damit Sie die Konvertierungsarbeit planen können.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      Die Konvertierung größerer Tabellen dauert länger. Sie sollten entsprechend planen, wenn Sie Ihre Site in den Wartungsmodus wechseln und aus dem Wartungsmodus herausnehmen, welche Tabellen in welcher Reihenfolge konvertiert werden sollen, um die Zeitpläne der benötigten Wartungsfenster zu planen

   - Konvertieren Sie alle Tabellen einzeln in das dynamische Format.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Aktualisieren Sie die Engine für die Tabellenspeicherung.

   - Identifizieren von Tabellen, die `MyISAM` Speicher.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Konvertieren von Tabellen, die `MyISAM` Speicher in `InnoDB` Speicher.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Überprüfen Sie die Konvertierung.

   Dieser Schritt ist erforderlich, da Code-Bereitstellungen, die nach Abschluss der Konvertierung vorgenommen wurden, dazu führen können, dass einige Tabellen wieder in ihre ursprüngliche Konfiguration zurückgesetzt werden.

   - Melden Sie sich am Tag vor dem geplanten Upgrade auf MariaDB Version 10.2 bei Ihrer Datenbank an und führen Sie die Abfragen aus, um das Format und die Speichermodul zu überprüfen.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Wenn Tabellen zurückgesetzt wurden, wiederholen Sie die Schritte zum Ändern des Tabellenformats und der Speicher-Engine.

## Zusätzliche Informationen

[Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](../planning/database-on-cloud.md)
