---
title: Best Practices für die Datenmigration
description: Befolgen Sie diese Best Practices für die Datenmigration, um eine erfolgreiche Aktualisierung von Magento 1 auf Magento 2 sicherzustellen.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Best Practices für die Datenmigration

Dieser Abschnitt enthält die besten Empfehlungen zur Beschleunigung und Vereinfachung Ihrer Migration sowie Hinweise dazu, wie viel Zeit benötigt wird.

* **Eine Datenbankkopie aus einer Magento 1-Instanz verwenden** beim Ausführen von Migrationstests. Verwenden Sie nicht die Produktionsinstanz Ihrer Magento 1 Store-Datenbank.

* **Entfernen veralteter und redundanter Daten** vor der Migration aus Ihrer Magento 1-Datenbank migrieren.

Zu diesen Daten können Protokolle, Bestellangebote, kürzlich aufgerufene oder verglichene Produkte, Besucher, ereignisspezifische Kategorien und Werberegeln gehören.

* **Befolgen Sie die [allgemeine Regeln für eine erfolgreiche Migration](migrate-data/overview.md#migration-overview)**.

* So steigern Sie die Leistung: **aktivieren Sie die `direct_document_copy` option** in `config.xml` Datei:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Die Datenbanken von Magento 1 und Magento 2 müssen sich auf demselben MySQL-Server befinden und das Datenbankkonto muss Zugriff auf beide Datenbanken haben.

## Benchmarking-Schätzungen

Adobe hat die Datenmigration auf dem folgenden System getestet:

* Virtual Box VM, CentOS 6, 2,5 GB RAM, CPU 1 Core 2,6 GHz
* Datenbank mit 177.000 Produkten, 355.000 Bestellungen und 214.000 Kunden

## Leistungsergebnisse

* Migrationszeit der Einstellungen: ca. 10 Minuten
* Datenmigrationszeit: ~9 Stunden (alle Daten außer URL-Neuschreibungen, ca. 85 % der Gesamtdaten)
* Schätzung der Site-Ausfallzeiten: einige Minuten Zeit, um die DNS-Einstellungen neu zu indizieren und zu ändern. Zusätzliche Zeit, die zum Aufwärmen des Seiten-Cache erforderlich ist.
