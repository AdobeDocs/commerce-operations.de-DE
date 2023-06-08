---
title: Verwalten von Nachrichtenwarteschlangen
description: Erfahren Sie, wie Sie Nachrichtenwarteschlangen über die Befehlszeile für Adobe Commerce verwalten können.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Verwalten von Nachrichtenwarteschlangen

Sie können Nachrichtenwarteschlangen über die Befehlszeile mit Cron-Aufträgen oder einem externen Prozess-Manager verwalten, um sicherzustellen, dass Verbraucher Nachrichten abrufen.

## Prozessverwaltung

Cron-Aufträge sind der Standardmechanismus zum Neustart von Verbrauchern. Von `cron` nutzen Sie die angegebene Anzahl von Nachrichten und beenden Sie sie. Wiederholen `cron` startet den Verbraucher neu.

Das folgende Beispiel zeigt die `crontab` Konfiguration für laufende Verbraucher:

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
>Wie oft Sie Nachrichtenwarteschlangen überprüfen, hängt von Ihrer Geschäftslogik und den verfügbaren Systemressourcen ab. Im Allgemeinen möchten Sie möglicherweise öfter nach neuen Kunden suchen und Begrüßungs-E-Mails senden als einen ressourcenintensiveren Prozess, z. B. die Aktualisierung Ihres Katalogs. Sie sollten `cron` Zeitpläne entsprechend Ihren Geschäftsanforderungen.
>
>Sie kann unter Admin Stores > Einstellungen > Konfiguration > Erweitert > System > Cron-Konfigurationsoptionen für die Gruppe konfiguriert werden: Verbraucher.
>
>Siehe [Cron konfigurieren und ausführen](../cli/configure-cron-jobs.md) Weitere Informationen zur Verwendung von `cron` mit Commerce.

Sie können auch einen Prozessmanager wie [Supervisor](https://supervisord.readthedocs.io/en/latest/) zur Überwachung des Status von Prozessen. Der Manager kann die Befehlszeile verwenden, um die Prozesse nach Bedarf neu zu starten.

## Konfiguration

### Standardverhalten

- Cron-Auftrag `consumers_runner` ist aktiviert
- Cron-Auftrag `consumers_runner` Alle definierten Verbraucher ausführen
- Jeder Verbraucher verarbeitet 10000 Nachrichten und beendet dann

>[!INFO]
>
>Wenn Ihr Adobe Commerce-Store auf der Cloud-Plattform gehostet wird, verwenden Sie die [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) , um die `consumers_runner` Cron-Auftrag.

### Spezifische Konfiguration

Bearbeiten Sie die `/app/etc/env.php` Datei zum Konfigurieren des Cron-Auftrags `consumers_runner`.

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

- `cron_run` - Ein boolean -Wert, der die `consumers_runner` Cron-Auftrag (Standard = `true`).
- `max_messages` - Die maximale Anzahl von Nachrichten, die jeder Verbraucher vor dem Beenden verarbeiten muss (Standard = `10000`). Obwohl wir es nicht empfehlen, können Sie 0 verwenden, um zu verhindern, dass der Verbraucher beendet wird. Siehe [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) um zu konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten.
- `consumers` - Ein Array von Zeichenfolgen, die angeben, welche Verbraucher ausgeführt werden sollen. Ein leeres Array wird ausgeführt *all* Verbraucher.
- `multiple_processes` - Ein Array von Schlüssel-Wert-Paaren, die angeben, welcher Verbraucher in wie vielen Prozessen ausgeführt werden soll. Unterstützt in Commerce 2.4.4 oder höher.

  >[!INFO]
  >
  >Es wird nicht empfohlen, mehrere Benutzer in einer MySQL-Warteschlange auszuführen. Siehe [Nachrichtenwarteschlange von MySQL in AMQP ändern](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) für weitere Informationen.

  >[!INFO]
  >
  >Wenn Ihr Adobe Commerce-Store auf der Cloud-Plattform gehostet wird, verwenden Sie die [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) um zu konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten.

Siehe [Starten von Nachrichtenwarteschlangen-Verbrauchern](../cli/start-message-queues.md).
