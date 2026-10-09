---
title: Schritte nach der Datenmigration
description: Erfahren Sie, welche Schritte nach der Verwendung des [!DNL Data Migration Tool] unternommen werden müssen, um Daten von Magento 1 zu Magento 2 zu migrieren.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '84'
ht-degree: 0%
---
# Schritte nach der Datenmigration

Nachdem Sie die Migration abgeschlossen und Ihre neue Magento 2-Site gründlich getestet haben, führen Sie die folgenden Aufgaben aus:

* Setzen Sie Magento 1 in den Wartungsmodus und stoppen Sie dauerhaft alle Administratoraktivitäten

* Magento 2 Cron-Aufträge starten

* [Alle Magento 2-Cache-Typen leeren](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Alle Magento 2-Indexer neu indizieren](../../../configuration/cli/manage-indexers.md#reindex)

* Ändern Sie die DNS- und Lastenausgleichsmodule so, dass sie auf die Magento 2-Produktions-Hardware verweisen.
