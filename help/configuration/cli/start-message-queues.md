---
title: Nachrichtenwarteschlangen-Verbraucher starten
description: Erfahren Sie, wie Sie Nachrichtenwarteschlangen-Verbraucher für asynchrone Vorgänge in Adobe Commerce starten. Erfahren Sie mehr über die Einrichtung von Verbraucherverwaltung und B2B-Funktionen.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Nachrichtenwarteschlangen-Verbraucher starten

{{file-system-owner}}

Sie müssen einen [Nachrichtenwarteschlangenbenutzer“ starten](../queues/consumers.md) um asynchrone Vorgänge wie Inventory management-Massenaktionen und REST-Massenaktionen und asynchrone Endpunkte zu aktivieren. Um die B2B-Funktionalität zu aktivieren, müssen Sie mehrere Verbraucher starten. Module von Drittanbietern erfordern möglicherweise auch, dass Sie einen benutzerdefinierten Verbraucher starten.

So zeigen Sie eine Liste aller Verbraucher an:

```bash
bin/magento queue:consumers:list
```

So starten Sie Nachrichtenwarteschlangen-Verbraucher:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Nachdem alle verfügbaren Nachrichten verarbeitet wurden, wird der Befehl beendet. Sie können den Befehl manuell oder mit einem Cron-Auftrag erneut ausführen. Sie können auch mehrere Instanzen des `magento queue:consumers:start`-Befehls ausführen, um große Nachrichtenwarteschlangen zu verarbeiten. Sie können beispielsweise `&` an den Befehl anhängen, um ihn im Hintergrund auszuführen, zu einer Eingabeaufforderung zurückzukehren und mit der Ausführung von Befehlen fortzufahren:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) Informationen zu den Befehlsoptionen, Parametern und Werten finden Sie _Abschnitt &quot;Commerce_ in der Referenz zu-Befehlszeilen-Tools.

>[!INFO]
>
>Die Option `--multi-process` ist im `queue:consumers:start`-Befehl vorhanden. Um jedoch Verbraucher mit parallelen Prozessen auszuführen, konfigurieren Sie die Option [`multiple_processes`](../queues/manage-message-queues.md#configuration) in `/app/etc/env.php`. Wenn `queue:consumers:start` jedoch mit der Option `--multi-process` aufgerufen wird, funktioniert sie nur in einem einzigen Thread.
