---
title: Cron-Aufträge
description: Erfahren Sie mehr über Cron-Gruppen und das Erstellen eines benutzerdefinierten Cron-Auftrags.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron-Aufträge

In diesen Themen wird beschrieben, wie Sie einen benutzerdefinierten Cron-Auftrag und optional eine benutzerdefinierte Cron-Gruppe einrichten. Wenn Ihre Commerce-Erweiterung die regelmäßige Ausführung geplanter Aufgaben erfordert, können Sie diese Themen verwenden, um einen Cron-_Auftrag_ (die geplante Aufgabe) und optional eine _Gruppe_ einzurichten, die benutzerdefinierte Aufgaben gleichzeitig ausführt.

Wenn Sie eine von Commerce bereitgestellte Cron-Gruppe verwenden, müssen Sie keine benutzerdefinierte Cron-Gruppe definieren. Wenn Sie jedoch möchten, dass Ihre Cron-Aufträge nach einem anderen Zeitplan ausgeführt werden oder alle gemeinsam ausgeführt werden sollen, sollten Sie eine Cron-Gruppe definieren

Das Commerce-Programm stellt die folgenden Cron-Gruppen bereit:

- `default`, das die meisten Cron-Aufträge enthält
- `index`, der &quot;[&quot; ](../cli/manage-indexers.md)
- `consumers`, der die Nachrichtenwarteschlange ([) ](../cli/start-message-queues.md)
- Diese Themen sind nur in Adobe Commerce verfügbar
   - `staging`, der [Staging-bezogene) ](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/staging/content-staging) ausführt
   - `catalog_event` führt Aufgaben für Target- und Warenkorbregeln aus
