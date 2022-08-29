---
title: Schritte zur Migration nach der Datenmigration
description: Erfahren Sie, welche Schritte nach der Verwendung des [!DNL Data Migration Tool] , um Daten aus Magento 1 in Magento 2 zu migrieren.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Schritte zur Migration nach der Datenmigration

Nachdem Sie die Migration abgeschlossen und Ihre neue Magento 2-Site gründlich getestet haben, führen Sie die folgenden Schritte aus:

* Magento 1 in den Wartungsmodus versetzen und alle Elemente dauerhaft anhalten [Admin](https://glossary.magento.com/admin) activities

* Start von Magento 2-Cron-Aufträgen

* [Alle Cache-Typen von Magento 2 leeren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [Neuindizieren aller Indexe aus Magento 2](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* Ändern Sie DNS und Load Balancer so, dass sie auf die Produktionshardware von Magento 2 verweisen
