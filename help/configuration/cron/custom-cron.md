---
title: Cron-Aufträge
description: Erfahren Sie mehr über Cron-Gruppen und das Erstellen benutzerdefinierter Cron-Aufträge in Adobe Commerce. Erkunden Sie die Einrichtung geplanter Aufgaben und die Cron-Gruppenkonfiguration.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Cron-Aufträge

In diesen Themen wird beschrieben, wie Sie einen benutzerdefinierten Cron-Auftrag und optional eine benutzerdefinierte Cron-Gruppe einrichten. Wenn Ihre Commerce-Erweiterung die regelmäßige Ausführung geplanter Aufgaben erfordert, können Sie diese Themen verwenden, um einen Cron-_Auftrag_ (die geplante Aufgabe) und optional eine _Gruppe_ einzurichten, die benutzerdefinierte Aufgaben gleichzeitig ausführt.

Wenn Sie eine von Commerce bereitgestellte Cron-Gruppe verwenden, müssen Sie keine benutzerdefinierte Cron-Gruppe definieren. Wenn Sie jedoch möchten, dass Ihre Cron-Aufträge nach einem anderen Zeitplan ausgeführt werden oder alle gemeinsam ausgeführt werden sollen, sollten Sie eine Cron-Gruppe definieren

Das Commerce-Programm stellt die folgenden Cron-Gruppen bereit:

- `default`, das die meisten Cron-Aufträge enthält
- `index`, der &quot;[&quot; &#x200B;](../cli/manage-indexers.md)
- `consumers`, der die Nachrichtenwarteschlange ([) &#x200B;](../cli/start-message-queues.md)
- Diese Themen sind nur in Adobe Commerce verfügbar
   - `staging`, der [Staging-bezogene) &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging) ausführt
   - `catalog_event` führt Aufgaben für Target- und Warenkorbregeln aus
