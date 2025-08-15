---
title: Schritte nach der Datenmigration
description: Erfahren Sie, welche Schritte nach der Verwendung von  [!DNL Data Migration Tool] zum Migrieren von Daten von Magento 1 zu Magento 2 unternommen werden müssen.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Schritte nach der Datenmigration

Nachdem Sie die Migration abgeschlossen und Ihre neue Magento 2-Site gründlich getestet haben, führen Sie die folgenden Aufgaben aus:

* Magento 1 in den Wartungsmodus versetzen und alle Admin-Aktivitäten dauerhaft stoppen

* Magento 2 Cron-Aufträge starten

* [Alle Magento 2-Cache-Typen leeren](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Alle Magento 2-Indexer neu indizieren](../../../configuration/cli/manage-indexers.md#reindex)

* Ändern Sie die DNS- und Lastenausgleichsmodule so, dass sie auf die Magento 2-Produktionshardware verweisen.
