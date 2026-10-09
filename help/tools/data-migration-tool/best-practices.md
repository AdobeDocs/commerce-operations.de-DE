---
title: Best Practices für die Datenmigration
description: Befolgen Sie diese Best Practices für die Datenmigration, um eine erfolgreiche Aktualisierung von Magento 1 auf Magento 2 sicherzustellen.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# Best Practices für die Datenmigration

In diesem Abschnitt finden Sie die besten Empfehlungen zur Beschleunigung und Vereinfachung Ihrer Migration sowie Anleitungen dazu, wie viel Zeit dies in Anspruch nehmen kann.

* **Verwenden Sie bei der Durchführung von Migrationstests eine Kopie** Datenbank aus einer Magento 1 -Instanz. Verwenden Sie nicht die Produktionsinstanz Ihrer Magento 1-Speicherdatenbank.

* **Entfernen Sie vor der Migration veraltete und redundante** aus Ihrer Magento 1-Datenbank.

Zu diesen Daten können Protokolle, Bestellangebote, kürzlich angesehene oder verglichene Produkte, Besucher, ereignisspezifische Kategorien und Werberegeln gehören.

* **Befolgen Sie die [allgemeinen Regeln für eine erfolgreiche Migration](migrate-data/overview.md#migration-overview)**.

* Um die Leistung zu steigern **(aktivieren Sie die Option `direct_document_copy`** in Ihrer `config.xml`:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Sowohl die Magento 1- als auch die Magento 2-Datenbank müssen sich auf demselben MySQL-Server befinden und das Datenbankkonto muss Zugriff auf beide Datenbanken haben.

## Benchmarking-Schätzungen

Adobe hat die Datenmigration auf dem folgenden System getestet:

* Virtual Box VM, CentOS 6, 2,5 GB RAM, CPU 1 Core 2,6 GHz
* Datenbank mit 177 000 Produkten, 355 000 Bestellungen und 214 000 Kunden

## Leistungsergebnisse

* Migrationszeit für Einstellungen: ~10 Minuten
* Datenmigrationszeit: ~9 Stunden (alle Daten außer URL-Neuschreibungen, ~85 % der Gesamtdaten)
* Geschätzte Ausfallzeiten der Site: einige Minuten, um die DNS-Einstellungen neu zu indizieren und zu ändern. Zusätzlicher Zeitaufwand zum Aufwärmen des Seiten-Caches.
