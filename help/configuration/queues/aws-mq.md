---
title: Einrichten der Amazon-Nachrichtenwarteschlange
description: Erfahren Sie, wie Sie Commerce für die Verwendung des AWS MQ-Dienstes konfigurieren.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Einrichten der Amazon-Nachrichtenwarteschlange

Ab Commerce 2.4.3 ist Amazon Message Queue (MQ) als Cloud-fähiger Ersatz für lokale Nachrichtenwarteschlangeninstanzen verfügbar.

Informationen zum Erstellen einer Nachrichtenwarteschlange in AWS finden Sie unter [Einrichten von Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) im _AWS-Dokumentation_.

## Konfigurieren von Commerce für AWS MQ

Um eine Verbindung zum AWS MQ-Dienst herzustellen, konfigurieren Sie die `queue.amqp` -Objekt im `env.php` -Datei.
AWS Message Queue erfordert eine SSL-/TLS-Verbindung.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Dabei gilt:

- `host`—Die URL für den AMQP-Endpunkt; verfügbar, indem Sie in AWS auf den Namen des Brokers klicken (Entfernen Sie &quot;https://&quot;und die nachfolgende Portnummer)
- `user`—Der Benutzername, der beim Erstellen des AWS MQ-Brokers eingegeben wurde
- `password`—Der bei der Erstellung des AWS MQ-Brokers eingegebene Kennwortwert

>[!INFO]
>
>Amazon MQ unterstützt nur TLS-Verbindungen. Die Peer-Verifizierung wird nicht unterstützt.

Nach der Bearbeitung des `env.php` Führen Sie den folgenden Befehl aus, um das Setup abzuschließen:

```bash
bin/magento setup:upgrade
```

## Verwendung des AWS MQ-Dienstes durch Commerce

Die `async.operations.all` Der Benutzer der Nachrichtenwarteschlange verwendet die AMQP-Verbindung.

Dieser Verbraucher leitet jeden Themennamen weiter, dem vorangestellt wird `async` über die AWS MQ-Verbindung.

Beispiel: in `InventoryCatalog` es gibt:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

Die Standardkonfiguration für `InventoryCatalog` veröffentlicht keine Nachrichten in RabbitMQ; Das Standardverhalten besteht darin, die Aktion im selben Benutzer-Thread durchzuführen. Zu sagen `InventoryCatalog` zum Veröffentlichen von Nachrichten aktivieren `cataloginventory/bulk_operations/async`. Wechseln Sie vom Administrator zu **Stores** > Konfiguration > **Katalog** > **Bestand** > Massenvorgänge für Administratoren und Festlegen  `Run asynchronously`nach **Ja**.

## Nachrichtenwarteschlange testen

So testen Sie den Nachrichtenversand von Commerce an RabbitMQ:

1. Melden Sie sich bei der Webkonsole von RabbitMQ in AWS an, um Warteschlangen zu überwachen.
1. Erstellen Sie in Admin ein Produkt.
1. Erstellen Sie eine Inventarquelle.
1. Aktivieren **Stores** > Konfiguration > **Katalog** > **Bestand** > Massenvorgänge für Administratoren > Asynchron ausführen.
1. Navigieren Sie zu **Katalog** > Produkte. Wählen Sie im Raster das oben erstellte Produkt aus und klicken Sie auf **Inventarquelle zuweisen**.
1. Klicken **Speichern und schließen** , um den Prozess abzuschließen.

   In der Webkonsole von RabbitMQ sollten jetzt Meldungen angezeigt werden.

1. Starten Sie die `async.operations.all` Benutzer der Nachrichtenwarteschlange.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Sie sollten nun sehen, dass die in die Warteschlange gestellte Nachricht in der Webkonsole von RabbitMQ verarbeitet wird.
Stellen Sie sicher, dass sich die Inventarquellen für das Produkt in der Admin-Konsole geändert haben.
