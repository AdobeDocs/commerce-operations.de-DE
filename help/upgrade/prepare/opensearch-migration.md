---
title: Migration von Elasticsearch zu OpenSearch
description: Erfahren Sie mehr über die Ersetzung der Suchmaschine, die für lokale Installationen von Adobe Commerce und Magento Open Source verwendet wird.
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Migration zu OpenSearch

OpenSearch ist eine Open-Source-Abspaltung von Elasticsearch 7.10.2, die nach der Lizenzänderung von Elasticsearch erstellt wurde.

Ab 2.4.4, 2.4.3-p2 und 2.3.7-p3 unterstützen Adobe Commerce und Magento Open Source OpenSearch. Vor-Ort-Installationen unterstützen Elasticsearch weiterhin, obwohl es für Adobe Commerce in der Cloud-Infrastruktur nicht mehr unterstützt wird.

## Migrationspfad

Die Schritte zur Migration zu OpenSearch sind einfach und folgen weitgehend den Schritten zur Konfiguration von Elasticsearch. Bei diesen Schritten wird davon ausgegangen, dass Adobe Commerce die einzige Anwendung ist, die die Suchmaschine verwendet. Wenn mehrere Anwendungen die Suchmaschine verwenden, folgen Sie dem offiziellen Migrationshandbuch. [Wechsel vom Open-Source-Elasticsearch zu OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Stellen Sie sicher, dass Ihre Installation die [Voraussetzungen für Suchmaschinen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. Platzieren Sie die Site in [Wartungsmodus](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Deinstallieren Sie optional Elasticsearch.

1. [OpenSearch installieren](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Suchmaschine konfigurieren](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) und führt zugehörige Aufgaben aus, z. B. das Leeren des Caches und die Neuindizierung des Katalogsuchindex.

Es sind keine weiteren Konfigurationswertänderungen erforderlich.
