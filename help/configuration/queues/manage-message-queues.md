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

Sie können Nachrichtenwarteschlangen über die Befehlszeile mit Cron-Aufträgen oder einem externen Prozess-Manager verwalten, um sicherzustellen, dass Verbraucher Nachrichten abrufen.

## Prozessverwaltung

Cron-Aufträge sind der Standardmechanismus zum Neustart von Verbrauchern. Prozesse, die mit `cron` gestartet wurden, verbrauchen die angegebene Anzahl von Nachrichten und enden dann. Beim erneuten Ausführen von `cron` wird der Verbraucher neu gestartet.

Das folgende Beispiel zeigt die `crontab` -Konfiguration für laufende Verbraucher:

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
>Wie oft Sie Nachrichtenwarteschlangen überprüfen, hängt von Ihrer Geschäftslogik und den verfügbaren Systemressourcen ab. Im Allgemeinen möchten Sie möglicherweise öfter nach neuen Kunden suchen und Begrüßungs-E-Mails senden als einen ressourcenintensiveren Prozess, z. B. die Aktualisierung Ihres Katalogs. Sie sollten `cron`-Zeitpläne entsprechend Ihren Geschäftsanforderungen definieren.
>
>Die Konfiguration erfolgt über Admin Stores > Einstellungen > Konfiguration > Erweitert > System > Cron-Konfigurationsoptionen für die Gruppe Consumer.
>
>Weitere Informationen zur Verwendung von `cron` mit Commerce finden Sie unter [CRON konfigurieren und ausführen](../cli/configure-cron-jobs.md) .

Sie können auch einen Prozessmanager wie [Supervisor](https://supervisord.readthedocs.io/en/latest/) verwenden, um den Status von Prozessen zu überwachen. Der Manager kann die Befehlszeile verwenden, um die Prozesse nach Bedarf neu zu starten.

## Konfiguration

### Standardverhalten

- Cron-Auftrag `consumers_runner` ist aktiviert
- Cron-Auftrag `consumers_runner` führt alle definierten Verbraucher aus
- Jeder Verbraucher verarbeitet 10000 Nachrichten und beendet dann

>[!INFO]
>
>Wenn Ihr Adobe Commerce-Store auf der Cloud-Plattform gehostet wird, verwenden Sie den [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner), um den `consumers_runner`-Cron-Auftrag zu konfigurieren.

### Spezifische Konfiguration

Bearbeiten Sie die Datei `/app/etc/env.php` , um den Cron-Auftrag `consumers_runner` zu konfigurieren.

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
- `max_messages` - Die maximale Anzahl von Nachrichten, die jeder Verbraucher vor dem Beenden verarbeiten muss (Standard = `10000`). Obwohl wir es nicht empfehlen, können Sie 0 verwenden, um zu verhindern, dass der Verbraucher beendet wird. Siehe [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) , um zu konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten.
- `consumers` - Ein Array von Zeichenfolgen, die angeben, welche Verbraucher ausgeführt werden sollen. Ein leeres Array führt *alle* -Verbraucher aus.
- `multiple_processes` - Ein Array von Schlüssel-Wert-Paaren, die angeben, welcher Verbraucher in wie vielen Prozessen ausgeführt werden soll. Unterstützt in Commerce 2.4.4 oder höher.

  >[!INFO]
  >
  >Es wird nicht empfohlen, mehrere Benutzer in einer MySQL-Warteschlange auszuführen. Weitere Informationen finden Sie unter [Nachrichtenwarteschlange von MySQL in AMQP ändern](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) .

  >[!INFO]
  >
  >Wenn Ihr Adobe Commerce-Store auf der Cloud-Plattform gehostet wird, verwenden Sie den [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages), um zu konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten.

Siehe [Starten von Verbrauchern in der Nachrichtenwarteschlange](../cli/start-message-queues.md).
