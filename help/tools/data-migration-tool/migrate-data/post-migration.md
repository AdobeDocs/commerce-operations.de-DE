---
title: Schritte zur Migration nach der Datenmigration
description: Erfahren Sie, welche Schritte nach der Verwendung des [!DNL Data Migration Tool] , um Daten aus Magento 1 in Magento 2 zu migrieren.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Schritte zur Migration nach der Datenmigration

Nachdem Sie die Migration abgeschlossen und Ihre neue Magento 2-Site gründlich getestet haben, führen Sie die folgenden Schritte aus:

* Magento 1 in den Wartungsmodus versetzen und alle Admin-Aktivitäten dauerhaft beenden

* Start von Magento 2-Cron-Aufträgen

* [Alle Cache-Typen von Magento 2 leeren](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Neuindizieren aller Indexe aus Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Ändern Sie DNS und Load Balancer so, dass sie auf die Produktionshardware von Magento 2 verweisen
