---
title: Verwalten von Nachrichtenwarteschlangen
description: Erfahren Sie, wie Sie Nachrichtenwarteschlangen über die Befehlszeile für Adobe Commerce verwalten können.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Verwalten von Nachrichtenwarteschlangen

Sie können Nachrichtenwarteschlangen über die Befehlszeile mithilfe von Cron-Aufträgen oder einem externen Prozessmanager verwalten, um sicherzustellen, dass Verbraucher Nachrichten abrufen.

## Prozessverwaltung

Cron-Aufträge sind der Standardmechanismus zum Neustart von Verbrauchern. Von `cron` gestartete Prozesse verarbeiten die angegebene Anzahl an Nachrichten und beenden diese. Beim erneuten Ausführen von `cron` wird der Verbraucher neu gestartet.

Das folgende Beispiel zeigt die `crontab` für das Ausführen von Verbrauchern:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>Wie oft Sie Nachrichtenwarteschlangen überprüfen, hängt von Ihrer Geschäftslogik und den verfügbaren Systemressourcen ab. Im Allgemeinen ist es empfehlenswert, nach neuen Kunden zu suchen und Willkommens-E-Mails häufiger zu senden als bei einem ressourcenintensiveren Prozess, z. B. dem Aktualisieren Ihres Katalogs. Sie sollten `cron` entsprechend Ihren Geschäftsanforderungen definieren.
>
>Sie können ihn in den Konfigurationsoptionen Admin Stores > Einstellungen > Konfiguration > Erweitert > System > Cron für Gruppe: Verbraucher konfigurieren.
>
>Weitere [ zur Verwendung von `cron` mit Commerce finden ](../cli/configure-cron-jobs.md) unter „Konfigurieren und Ausführen von“.

Sie können auch einen Prozess-Manager wie [Supervisor](https://supervisord.readthedocs.io/en/latest/) verwenden, um den Status von Prozessen zu überwachen. Der Manager kann die Befehlszeile verwenden, um die Prozesse nach Bedarf neu zu starten.

## Konfiguration

### Standardverhalten

- Cron-`consumers_runner` ist aktiviert
- Cron-`consumers_runner` führt alle definierten Verbraucher aus
- Jeder Verbraucher verarbeitet 10000 Nachrichten und beendet dann

>[!INFO]
>
>Wenn Ihr Adobe Commerce-Store auf der Cloud-Plattform gehostet wird, konfigurieren Sie mit dem [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=de#cron_consumers_runner) den `consumers_runner` Cron-Auftrag.

### Spezifische Konfiguration

Bearbeiten Sie die `/app/etc/env.php` Datei, um die Cron-Job-`consumers_runner` zu konfigurieren.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Ein boolescher Wert, der den `consumers_runner` Cron-Auftrag aktiviert oder deaktiviert (Standard = `true`).
- `max_messages` - Die maximale Anzahl von Nachrichten, die jeder Verbraucher vor dem Beenden verarbeiten muss (Standard = `10000`). Obwohl wir dies nicht empfehlen, können Sie 0 verwenden, um zu verhindern, dass der Verbraucher beendet. Siehe [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages), um zu konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten.
- `consumers` - Ein Array von Zeichenfolgen, das angibt, welche Verbraucher ausgeführt werden sollen. Ein leeres Array führt &quot;*&quot;*.
- `multiple_processes` : Ein Array von Schlüssel-Wert-Paaren, die angeben, welcher Consumer in wie vielen Prozessen ausgeführt werden soll. Wird in Commerce 2.4.4 oder höher unterstützt.

  >[!INFO]
  >
  >Es wird nicht empfohlen, mehrere Verbraucher in einer von MySQL betriebenen Warteschlange auszuführen. Weitere [ finden Sie unter „Meldungswarteschlange von MySQL auf ](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) ändern“.

  >[!INFO]
  >
  >Wenn Ihr Adobe Commerce-Store auf der Cloud-Plattform gehostet wird, konfigurieren Sie mit dem [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=de#consumers_wait_for_max_messages), wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten.

Siehe [Starten von Nachrichtenwarteschlangen-Verbrauchern](../cli/start-message-queues.md).
