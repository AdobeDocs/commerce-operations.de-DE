---
title: Cron-Aufträge
description: Erfahren Sie mehr über Cron-Gruppen und das Erstellen eines benutzerdefinierten Cron-Auftrags.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron-Aufträge

In diesen Themen wird beschrieben, wie Sie einen benutzerdefinierten Cron-Auftrag und optional eine benutzerdefinierte Cron-Gruppe einrichten. Wenn für Ihre Commerce-Erweiterung geplante Aufgaben regelmäßig ausgeführt werden müssen, können Sie diese Themen verwenden, um einen Cron _job_ (die geplante Aufgabe) und optional eine Cron _group_ einzurichten, die benutzerdefinierte Aufgaben gleichzeitig ausführt.

Wenn Sie eine von Commerce bereitgestellte Cron-Gruppe verwenden, müssen Sie keine benutzerdefinierte Cron-Gruppe definieren. Wenn Sie jedoch möchten, dass Ihre Cron-Aufträge zu einem anderen Zeitplan ausgeführt werden oder alle zusammen ausgeführt werden sollen, sollten Sie eine Cron-Gruppe definieren

Die Commerce-Anwendung stellt die folgenden Cron-Gruppen bereit:

- `default`, der die meisten Cron-Aufträge enthält
- `index`, wodurch [indexers](../cli/manage-indexers.md) aktualisiert wird
- `consumers`, wodurch die Nachrichtenwarteschlange [consumer](../cli/start-message-queues.md) ausgeführt wird
- Diese Themen sind nur in Adobe Commerce verfügbar
   - `staging`, der [Staging-bezogene ](https://docs.magento.com/user-guide/cms/content-staging.html) Aufgaben ausführt
   - `catalog_event`, wodurch Aufgaben für Ziel- und Warenkorbregeln ausgeführt werden
