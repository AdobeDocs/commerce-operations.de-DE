---
title: Nachrichtenwarteschlangen-Verbraucher starten
description: Erfahren Sie, wie Sie Nachrichtenwarteschlangen-Verbraucher für asynchrone Vorgänge in Adobe Commerce starten. Erfahren Sie mehr über die Einrichtung von Verbraucherverwaltung und B2B-Funktionen.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
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
source-wordcount: '191'
ht-degree: 0%
---
# Nachrichtenwarteschlangen-Verbraucher starten

{{file-system-owner}}

Sie müssen einen [Nachrichtenwarteschlangenbenutzer“ starten](../queues/consumers.md) um asynchrone Vorgänge wie Inventory management-Massenaktionen und REST-Massenaktionen und asynchrone Endpunkte zu aktivieren. Um die B2B-Funktionalität zu aktivieren, müssen Sie mehrere Verbraucher starten. Module von Drittanbietern erfordern möglicherweise auch, dass Sie einen benutzerdefinierten Verbraucher starten.

So zeigen Sie eine Liste aller Verbraucher an:

```shell
bin/magento queue:consumers:list
```

So starten Sie Nachrichtenwarteschlangen-Verbraucher:

```shell
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Nachdem alle verfügbaren Nachrichten verarbeitet wurden, wird der Befehl beendet. Sie können den Befehl manuell oder mit einem Cron-Auftrag erneut ausführen. Sie können auch mehrere Instanzen des `magento queue:consumers:start`-Befehls ausführen, um große Nachrichtenwarteschlangen zu verarbeiten. Sie können beispielsweise `&` an den Befehl anhängen, um ihn im Hintergrund auszuführen, zu einer Eingabeaufforderung zurückzukehren und mit der Ausführung von Befehlen fortzufahren:

```shell
bin/magento queue:consumers:start <consumer_name> &
```

[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) Informationen zu den Befehlsoptionen, Parametern und Werten finden Sie _Abschnitt &quot;Commerce_ in der Referenz zu-Befehlszeilen-Tools.

>[!INFO]
>
>Die Option `--multi-process` ist im `queue:consumers:start`-Befehl vorhanden. Um jedoch Verbraucher mit parallelen Prozessen auszuführen, konfigurieren Sie die Option [`multiple_processes`](../queues/manage-message-queues.md#configuration) in `/app/etc/env.php`. Wenn `queue:consumers:start` jedoch mit der Option `--multi-process` aufgerufen wird, funktioniert sie nur in einem einzigen Thread.
