---
title: Cron-Aufträge
description: Erfahren Sie mehr über Cron-Gruppen und das Erstellen eines benutzerdefinierten Cron-Auftrags.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Cron-Aufträge

In diesen Themen wird beschrieben, wie Sie einen benutzerdefinierten Cron-Auftrag und optional eine benutzerdefinierte Cron-Gruppe einrichten. Wenn Ihre Commerce-Erweiterung die regelmäßige Ausführung geplanter Aufgaben erfordert, können Sie diese Themen verwenden, um einen Cron einzurichten. _job_ (die geplante Aufgabe) und optional ein Cron _Gruppe_, wodurch benutzerdefinierte Aufgaben gleichzeitig ausgeführt werden.

Wenn Sie eine von Commerce bereitgestellte Cron-Gruppe verwenden, müssen Sie keine benutzerdefinierte Cron-Gruppe definieren. Wenn Sie jedoch möchten, dass Ihre Cron-Aufträge zu einem anderen Zeitplan ausgeführt werden oder dass sie alle zusammen ausgeführt werden, sollten Sie eine Cron-Gruppe definieren

Die Commerce-Anwendung stellt die folgenden Cron-Gruppen bereit:

- `default`, der die meisten Cron-Aufträge enthält
- `index`, die aktualisiert [Indexer](../cli/manage-indexers.md)
- `consumers`, wodurch die Nachrichtenwarteschlange ausgeführt wird [Verbraucher](../cli/start-message-queues.md)
- Diese Themen sind nur in Adobe Commerce verfügbar
   - `staging`, die ausgeführt wird [Staging-bezogen](https://docs.magento.com/user-guide/cms/content-staging.html) Aufgaben
   - `catalog_event`, wodurch Aufgaben für Ziel- und Warenkorbregeln ausgeführt werden
