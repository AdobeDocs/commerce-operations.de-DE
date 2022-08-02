---
title: Starten von Nachrichtenwarteschlangen-Verbrauchern
description: Erfahren Sie, wie Sie eine Nachrichtenwarteschlange für Verbraucher starten.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Starten von Nachrichtenwarteschlangen-Verbrauchern

{{file-system-owner}}

Sie müssen einen Nachrichtenwarteschlange-Benutzer starten, um asynchrone Vorgänge wie Massenaktionen in Inventory management sowie REST-Massen- und asynchrone Endpunkte zu aktivieren. Um B2B-Funktionen zu aktivieren, müssen Sie mehrere Verbraucher starten. Für Drittanbietermodule ist möglicherweise auch das Starten eines benutzerdefinierten Verbrauchers erforderlich.

So zeigen Sie eine Liste aller Verbraucher an:

```bash
bin/magento queue:consumers:list
```

So starten Sie Verbraucher in der Nachrichtenwarteschlange:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Nach dem Abruf aller verfügbaren Nachrichten wird der Befehl beendet. Sie können den Befehl erneut manuell oder mit einem Cron-Auftrag ausführen. Sie können auch mehrere Instanzen der `magento queue:consumers:start` -Befehl zum Verarbeiten großer Nachrichtenwarteschlangen. Sie können beispielsweise `&` zum Befehl zum Ausführen im Hintergrund, kehren Sie zu einer Eingabeaufforderung zurück und fahren Sie mit der Ausführung der Befehle fort:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Siehe [queue:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) im Abschnitt &quot;Handel&quot;des _Referenz zu Befehlszeilen-Tools_ für Details zu den Befehlsoptionen, Parametern und Werten.

>[!INFO]
>
>Die `--multi-process` ist in der `queue:consumers:start` -Befehl, aber um Verbraucher mit parallelen Prozessen auszuführen, konfigurieren Sie die [`multiple_processes`](../queues/manage-message-queues.md#configuration) Option in `/app/etc/env.php`. Wenn andernfalls `queue:consumers:start` wird mit der `--multi-process` -Option, funktioniert sie nur in einem einzigen Thread.
