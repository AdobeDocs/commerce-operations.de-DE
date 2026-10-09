---
title: Migrieren von Elasticsearch zu OpenSearch
description: Erfahren Sie, wie Sie die Suchmaschine für lokale Installationen von Adobe Commerce ersetzen.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '201'
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
