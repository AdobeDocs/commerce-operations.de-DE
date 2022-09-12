---
title: Schritte zur Migration nach der Datenmigration
description: Erfahren Sie, welche Schritte nach der Verwendung des [!DNL Data Migration Tool] , um Daten aus Magento 1 in Magento 2 zu migrieren.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# Schritte zur Migration nach der Datenmigration

Nachdem Sie die Migration abgeschlossen und Ihre neue Magento 2-Site gründlich getestet haben, führen Sie die folgenden Schritte aus:

* Magento 1 in den Wartungsmodus versetzen und alle Elemente dauerhaft anhalten [Admin](https://glossary.magento.com/admin) activities

* Start von Magento 2-Cron-Aufträgen

* [Alle Cache-Typen von Magento 2 leeren](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Neuindizieren aller Indexe aus Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Ändern Sie DNS und Load Balancer so, dass sie auf die Produktionshardware von Magento 2 verweisen
