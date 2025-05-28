---
title: Migrieren von Elasticsearch zu OpenSearch
description: Erfahren Sie, wie Sie die Suchmaschine für lokale Installationen von Adobe Commerce ersetzen.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migration zu OpenSearch

OpenSearch ist eine Open-Source-Version von Elasticsearch 7.10.2, die nach der Lizenzänderung von Elasticsearch erstellt wurde.

Ab Version 2.4.4, 2.4.3-p2 und 2.3.7-p3 unterstützt Adobe Commerce OpenSearch. On-Premise-Installationen unterstützen weiterhin Elasticsearch, werden aber für Adobe Commerce auf Cloud-Infrastrukturen nicht mehr unterstützt. Ab Version 2.4.6 verfügt OpenSearch über ein eigenes Modul und Felder in den Admin-Konfigurationseinstellungen.

## Migrationspfad

Die Schritte für die Migration zu OpenSearch sind einfach und folgen größtenteils den Schritten für die Elasticsearch-Konfiguration. Bei diesen Schritten wird davon ausgegangen, dass Adobe Commerce die einzige Anwendung ist, die die Suchmaschine verwendet. Wenn mehrere Anwendungen die Suchmaschine verwenden, folgen Sie dem offiziellen Migrationshandbuch [Wechseln von Open Source Elasticsearch zu OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Stellen Sie sicher, dass Ihre Installation die [Voraussetzungen für Suchmaschinen](../../installation/prerequisites/search-engine/overview.md) erfüllt.

1. Setzen Sie die Site in [Wartungsmodus](../../installation/tutorials/maintenance-mode.md).

1. Deinstallieren Sie optional Elasticsearch.

1. [OpenSearch installieren](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Konfigurieren Sie die Suchmaschine](../../configuration/search/configure-search-engine.md) und führen Sie zugehörige Aufgaben aus, z. B. das Leeren des Cache und die Neuindizierung des Katalogsuchindex.

Es sind keine weiteren Änderungen am Konfigurationswert erforderlich.
