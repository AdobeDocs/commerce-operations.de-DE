---
title: Einrichten der Amazon-Nachrichtenwarteschlange
description: Erfahren Sie, wie Sie Commerce für die Verwendung des AWS MQ-Service konfigurieren.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Einrichten der Amazon-Nachrichtenwarteschlange

Ab Commerce 2.4.3 ist Amazon Message Queue (MQ) als Cloud-fähiger Ersatz für lokale Nachrichtenwarteschlangeninstanzen verfügbar.

Informationen zum Erstellen einer Nachrichtenwarteschlange auf AWS finden Sie unter [Einrichten von Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) in der _AWS-Dokumentation_.

## Konfigurieren von Commerce für AWS MQ

Um eine Verbindung zum AWS MQ-Service herzustellen, konfigurieren Sie das `queue.amqp` in der `env.php`.
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

- `host` - Die URL für den AMQP-Endpunkt, verfügbar durch Klicken auf den Brokernamen in AWS (entfernen Sie &quot;https://&quot; und die nachfolgende Portnummer)
- `user` - Der beim Erstellen des AWS MQ-Brokers eingegebene Benutzername
- `password` - Der beim Erstellen des AWS MQ-Brokers eingegebene Kennwortwert

>[!INFO]
>
>Amazon MQ unterstützt nur TLS-Verbindungen. Die Peer-Überprüfung wird nicht unterstützt.

Führen Sie nach der Bearbeitung der `env.php`-Datei den folgenden Befehl aus, um die Einrichtung abzuschließen:

```bash
bin/magento setup:upgrade
```

## Wie Commerce den AWS MQ-Service verwendet

Der `async.operations.all` Message Queue Consumer verwendet die AMQP-Verbindung.

Dieser Verbraucher leitet jeden Themennamen mit dem Präfix `async` über die AWS MQ-Verbindung weiter.

In `InventoryCatalog` gibt es beispielsweise:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

Die Standardkonfiguration für `InventoryCatalog` veröffentlicht keine Nachrichten in [!DNL RabbitMQ]. Standardmäßig wird die Aktion im selben Benutzer-Thread ausgeführt. Um `InventoryCatalog` anzuweisen, Nachrichten zu veröffentlichen, aktivieren Sie `cataloginventory/bulk_operations/async`. Wechseln Sie von der -Admin-**zu** > Konfiguration > **Katalog** > **Inventar** > Massenvorgänge für Admin und setzen Sie `Run asynchronously` auf **Ja**.

## Testen der Nachrichtenwarteschlange

So testen Sie den Nachrichtenversand von Commerce an [!DNL RabbitMQ]:

1. Melden Sie sich bei der [!DNL RabbitMQ]-Web-Konsole in AWS an, um Warteschlangen zu überwachen.
1. Erstellen Sie in der Admin Console ein Produkt.
1. Erstellen Sie eine Inventarquelle.
1. Aktivieren Sie **Stores** > Konfiguration > **Katalog** > **Inventar** > Admin-Massenvorgänge > Asynchron ausführen.
1. Navigieren Sie **Katalog** > Produkte. Wählen Sie im Raster das oben erstellte Produkt aus und klicken Sie auf **Inventar-Source zuweisen**.
1. Klicken Sie **Speichern und schließen** um den Vorgang abzuschließen.

   Es sollten jetzt Meldungen in der [!DNL RabbitMQ] Web-Konsole angezeigt werden.

1. Starten Sie den `async.operations.all` Nachrichtenwarteschlange-Verbraucher.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Die in die Warteschlange gestellte Nachricht sollte nun in der [!DNL RabbitMQ] Web-Konsole verarbeitet werden.
Überprüfen Sie, ob sich die Inventarquellen für das Produkt in der Admin Console geändert haben.
