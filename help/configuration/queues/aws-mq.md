---
title: Einrichten der Amazon-Nachrichtenwarteschlange
description: Erfahren Sie, wie Sie Commerce für die Verwendung des AWS MQ-Dienstes konfigurieren.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Einrichten der Amazon-Nachrichtenwarteschlange

Ab Commerce 2.4.3 ist Amazon Message Queue (MQ) als Cloud-fähiger Ersatz für lokale Nachrichtenwarteschlangeninstanzen verfügbar.

Informationen zum Erstellen einer Nachrichtenwarteschlange in AWS finden Sie unter [Einrichten von Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) in der _AWS-Dokumentation_.

## Konfigurieren von Commerce für AWS MQ

Um eine Verbindung zum AWS MQ-Dienst herzustellen, konfigurieren Sie das Objekt `queue.amqp` in der Datei `env.php` .
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

- `host`—Die URL für den AMQP-Endpunkt, die durch Klicken auf den Brokernamen in AWS verfügbar ist (Entfernen Sie &quot;https://&quot;und die nachfolgende Portnummer)
- `user` - Der Benutzername, der beim Erstellen des AWS MQ-Brokers eingegeben wurde
- `password` - Der bei der Erstellung des AWS MQ-Brokers eingegebene Kennwortwert

>[!INFO]
>
>Amazon MQ unterstützt nur TLS-Verbindungen. Die Peer-Verifizierung wird nicht unterstützt.

Führen Sie nach dem Bearbeiten der Datei &quot;`env.php`&quot;den folgenden Befehl aus, um das Setup abzuschließen:

```bash
bin/magento setup:upgrade
```

## Verwendung des AWS MQ-Dienstes durch Commerce

Der Benutzer der Nachrichtenwarteschlange `async.operations.all` verwendet die AMQP-Verbindung.

Dieser Kunde leitet jeden Themennamen, dem `async` vorangestellt ist, über die AWS-MQ-Verbindung weiter.

In `InventoryCatalog` gibt es beispielsweise Folgendes:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

Die Standardkonfiguration für `InventoryCatalog` veröffentlicht keine Nachrichten in [!DNL RabbitMQ]. Das Standardverhalten besteht darin, die Aktion im selben Benutzer-Thread durchzuführen. Um `InventoryCatalog` anzuweisen, Nachrichten zu veröffentlichen, aktivieren Sie `cataloginventory/bulk_operations/async`. Wechseln Sie vom Administrator zu &quot;**Stores**&quot;> &quot;Konfiguration&quot;> &quot;**Katalog**&quot;> &quot;**Inventar**&quot;> &quot;Admin-Massenvorgänge&quot;und legen Sie `Run asynchronously`auf &quot;**Ja**&quot;fest.

## Nachrichtenwarteschlange testen

So testen Sie den Nachrichtenversand von Commerce an [!DNL RabbitMQ]:

1. Melden Sie sich bei der Web-Konsole [!DNL RabbitMQ] in AWS an, um Warteschlangen zu überwachen.
1. Erstellen Sie in Admin ein Produkt.
1. Erstellen Sie eine Inventarquelle.
1. Aktivieren Sie **Stores** > Konfiguration > **Katalog** > **Bestand** > Massen-Vorgänge für Administratoren > asynchron ausführen.
1. Navigieren Sie zu **Katalog** > Produkte. Wählen Sie im Raster das oben erstellte Produkt aus und klicken Sie auf **Inventar Source zuweisen**.
1. Klicken Sie auf **Speichern und schließen** , um den Vorgang abzuschließen.

   In der Web-Konsole [!DNL RabbitMQ] sollten jetzt Meldungen angezeigt werden.

1. Starten Sie den Benutzer der Nachrichtenwarteschlange `async.operations.all` .

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Die in der Warteschlange befindliche Nachricht sollte nun in der Web-Konsole [!DNL RabbitMQ] verarbeitet werden.
Stellen Sie sicher, dass sich die Inventarquellen für das Produkt in der Admin-Konsole geändert haben.
