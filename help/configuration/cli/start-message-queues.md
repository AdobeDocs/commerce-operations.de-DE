---
title: Starten von Nachrichtenwarteschlangen-Verbrauchern
description: Erfahren Sie, wie Sie eine Nachrichtenwarteschlange für Verbraucher starten.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Starten von Nachrichtenwarteschlangen-Verbrauchern

{{file-system-owner}}

Sie müssen einen [Benutzer der Nachrichtenwarteschlange](../queues/consumers.md) starten, um asynchrone Vorgänge wie Inventory management-Massenaktionen und REST-Massen- und asynchrone Endpunkte zu aktivieren. Um B2B-Funktionen zu aktivieren, müssen Sie mehrere Verbraucher starten. Für Drittanbietermodule ist möglicherweise auch das Starten eines benutzerdefinierten Verbrauchers erforderlich.

So zeigen Sie eine Liste aller Verbraucher an:

```bash
bin/magento queue:consumers:list
```

So starten Sie Verbraucher in der Nachrichtenwarteschlange:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Nach dem Abruf aller verfügbaren Nachrichten wird der Befehl beendet. Sie können den Befehl erneut manuell oder mit einem Cron-Auftrag ausführen. Sie können auch mehrere Instanzen des Befehls `magento queue:consumers:start` ausführen, um große Nachrichtenwarteschlangen zu verarbeiten. Sie können beispielsweise `&` an den Befehl anhängen, um ihn im Hintergrund auszuführen, zu einer Eingabeaufforderung zurückzukehren und mit den folgenden Befehlen fortzufahren:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Weitere Informationen zu den Befehlsoptionen, Parametern und Werten finden Sie unter [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) im Commerce-Abschnitt der Referenz zu Befehlszeilenwerkzeugen _._

>[!INFO]
>
>Die Option `--multi-process` ist im Befehl `queue:consumers:start` vorhanden. Um jedoch Verbraucher mit parallelen Prozessen auszuführen, konfigurieren Sie die Option [`multiple_processes`](../queues/manage-message-queues.md#configuration) in `/app/etc/env.php`. Wenn andernfalls `queue:consumers:start` mit der Option `--multi-process` aufgerufen wird, funktioniert dies nur bei einem einzelnen Thread.
