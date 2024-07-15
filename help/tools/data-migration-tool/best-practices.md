---
title: Best Practices für die Datenmigration
description: Befolgen Sie diese Best Practices für die Datenmigration, um eine erfolgreiche Aktualisierung von Magento 1 auf Magento 2 sicherzustellen.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Best Practices für die Datenmigration

Dieser Abschnitt enthält die besten Empfehlungen zur Beschleunigung und Vereinfachung Ihrer Migration sowie Hinweise dazu, wie viel Zeit benötigt wird.

* **Verwenden Sie beim Ausführen von Migrationstests eine Datenbankkopie von einer Magento 1-Instanz**. Verwenden Sie nicht die Produktionsinstanz Ihrer Magento 1 Store-Datenbank.

* **Entfernen Sie veraltete und redundante Daten** aus Ihrer Magento 1-Datenbank vor der Migration.

Zu diesen Daten können Protokolle, Bestellangebote, kürzlich aufgerufene oder verglichene Produkte, Besucher, ereignisspezifische Kategorien und Werberegeln gehören.

* **Befolgen Sie die [allgemeinen Regeln für eine erfolgreiche Migration](migrate-data/overview.md#migration-overview)**.

* Um die Leistung zu steigern, aktivieren Sie **die `direct_document_copy` Option** in Ihrer `config.xml`-Datei:

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
* Datenmigrationszeit: ca. 9 Stunden (alle Daten außer URL-Neuschreibungen, ca. 85 % der Gesamtdaten)
* Schätzung der Site-Ausfallzeiten: einige Minuten, um die DNS-Einstellungen neu zu indizieren und zu ändern. Zusätzliche Zeit, die zum Aufwärmen des Seiten-Cache erforderlich ist.
