---
title: Schritte zur Migration nach der Datenmigration
description: Erfahren Sie, welche Schritte nach der Verwendung des [!DNL Data Migration Tool] , um Daten von Magento 1 auf Magento 2 zu migrieren.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Schritte zur Migration nach der Datenmigration

Nachdem Sie die Migration abgeschlossen und Ihre neue Magento 2-Site gründlich getestet haben, führen Sie die folgenden Schritte aus:

* Magento 1 in den Wartungsmodus versetzen und alle Admin-Aktivitäten dauerhaft beenden

* Starten von Magento 2-Cron-Aufträgen

* [Alle Magento 2-Cache-Typen leeren](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Neuindizieren aller Magento 2-Indexer](../../../configuration/cli/manage-indexers.md#reindex)

* Ändern Sie DNS und Load Balancer so, dass sie auf die Magento 2-Produktionshardware verweisen.
