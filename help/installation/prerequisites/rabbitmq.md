---
title: Nachrichtenbroker
description: Führen Sie die folgenden Schritte aus, um die erforderliche Message Broker-Software (wie [!DNL RabbitMQ]) für Vor-Ort-Anlagen von Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Nachrichtenbroker

Adobe Commerce verwendet die [!DNL RabbitMQ] Open-Source-Nachrichtenbroker. Es bietet ein zuverlässiges, hochverfügbares, skalierbares und portables Messaging-System.

Nachrichtenwarteschlangen bieten einen asynchronen Kommunikationsmechanismus, bei dem sich Absender und Empfänger einer Nachricht nicht miteinander in Verbindung setzen. Sie müssen auch nicht gleichzeitig mit der Nachrichtenwarteschlange kommunizieren. Wenn ein Absender eine Nachricht in eine Warteschlange stellt, wird sie so lange gespeichert, bis der Empfänger sie erhält.

Das Meldungswarteschlangesystem muss eingerichtet werden, bevor Sie Adobe Commerce installieren. Die grundlegende Sequenz lautet:

1. Installieren [!DNL RabbitMQ] und alle Voraussetzungen.
1. Verbinden [!DNL RabbitMQ] nach Adobe Commerce.

>[!NOTE]
>
>Sie können MySQL oder [!DNL RabbitMQ] für die Verarbeitung der Nachrichtenwarteschlange. Weitere Informationen zum Einrichten des Nachrichtenwarteschlangensystems finden Sie unter [Übersicht über Nachrichtenwarteschlangen](https://developer.adobe.com/commerce/php/development/components/message-queues/). Wenn Sie die Bulk API mit Adobe Commerce verwenden, wird bei der Konfiguration des Nachrichtenwarteschlangensystems standardmäßig die Verwendung von [!DNL RabbitMQ] als Nachrichtenbroker. Siehe [Starten von Nachrichtenwarteschlangen-Verbrauchern](../../configuration/cli/start-message-queues.md) für weitere Informationen.

## Installieren [!DNL RabbitMQ] zu Ubuntu

Installieren [!DNL RabbitMQ] Geben Sie auf Ubuntu 16 den folgenden Befehl ein:

```bash
sudo apt install -y rabbitmq-server
```

Mit diesem Befehl werden auch die erforderlichen Erlang-Pakete installiert.

Wenn Sie eine ältere Version von Ubuntu haben, [!DNL RabbitMQ] empfiehlt die Installation des Pakets von seiner Website aus.

1. Laden Sie das .deb-Paket herunter von [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installieren Sie das Paket mit `dpkg`.

Siehe Abschnitt [Installieren auf Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) für weitere Informationen.

## Installieren [!DNL RabbitMQ] auf CentOS

### Installieren von Erlang

[!DNL RabbitMQ] wurde mit der Programmiersprache Erlang geschrieben, die auf demselben System installiert sein muss wie [!DNL RabbitMQ].

Siehe [Manuelle Installation](https://www.erlang-solutions.com/downloads/) für weitere Informationen.

Siehe Abschnitt [[!DNL RabbitMQ]/Erlang-Versionsmatrix](https://www.rabbitmq.com/which-erlang.html) um die richtige Version zu installieren.

### Installieren [!DNL RabbitMQ]

Die [!DNL RabbitMQ] -Server ist in CentOS enthalten, aber die -Version ist häufig alt. [!DNL RabbitMQ] empfiehlt die Installation des Pakets von seiner Website aus.

Siehe Abschnitt [!DNL RabbitMQ] installieren Seite, um die neueste unterstützte Version zu erhalten. Unterstützung für Adobe Commerce 2.3 und 2.4 [!DNL RabbitMQ] 3.8.x.

Siehe Abschnitt [Installieren unter RPM-basiertem Linux](https://www.rabbitmq.com/install-rpm.html) für weitere Informationen.

## Konfigurieren [!DNL RabbitMQ]

Überprüfen Sie den Beamten [!DNL RabbitMQ] Dokumentation zur Konfiguration und Verwaltung [!DNL RabbitMQ]. Beachten Sie die folgenden Punkte:

* Umgebungsvariablen
* Port-Zugriff
* Standardbenutzerkonten
* Starten und Beenden des Brokers
* Systembeschränkungen

## Installieren mit [!DNL RabbitMQ] und verbinden

Wenn Sie Adobe Commerce installieren _after_ Installieren [!DNL RabbitMQ]Fügen Sie während der Installation die folgenden Befehlszeilenparameter hinzu:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dabei gilt:

| Parameter | Beschreibung |
|--- |--- |
| `--amqp-host` | Der Hostname, in dem [!DNL RabbitMQ] installiert ist. |
| `--amqp-port` | Der Anschluss, mit dem die Verbindung hergestellt werden soll [!DNL RabbitMQ]. Der Standardwert ist `5672`. |
| `--amqp-user` | Der Benutzername für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht den Standardbenutzer `guest`. |
| `--amqp-password` | Das Kennwort für die Verbindung zu [!DNL RabbitMQ]. Verwenden Sie nicht das Standardkennwort `guest`. |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung zu [!DNL RabbitMQ]. Der Standardwert ist `/`. |
| `--amqp-ssl` | Gibt an, ob eine Verbindung hergestellt werden soll [!DNL RabbitMQ]. Der Standardwert ist `false`. Wenn Sie den Wert auf &quot;true&quot;setzen, finden Sie weitere Informationen unter SSL konfigurieren . |

## Verbinden [!DNL RabbitMQ]

Wenn Sie Adobe Commerce bereits installiert haben und eine Verbindung mit [!DNL RabbitMQ], fügen Sie eine `queue` im Abschnitt `<install_directory>/app/etc/env.php` -Datei, sodass sie der folgenden ähnelt:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

Sie können auch [!DNL RabbitMQ] Konfigurationswerte mithilfe der `bin/magento setup:config:set` command:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Nach dem Ausführen des Befehls oder Aktualisieren der `<install_directory>/app/etc/env.php` Datei mit AMQP-Konfigurationswerten, ausführen `bin/magento setup:upgrade` , um die Änderungen anzuwenden und die erforderlichen Warteschlangen und Austausche in [!DNL RabbitMQ].

## SSL konfigurieren

Um die Unterstützung für SSL zu konfigurieren, bearbeiten Sie das `ssl` und `ssl_options` Parameter in `<install_directory>/app/etc/env.php` -Datei, sodass sie der folgenden ähneln:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Starten der Verbraucher in der Nachrichtenwarteschlange

Nachdem Sie Adobe Commerce verbunden haben und [!DNL RabbitMQ], müssen Sie die Verbraucher in der Nachrichtenwarteschlange starten. Siehe [Nachrichtenwarteschlangen konfigurieren](../../configuration/cli/start-message-queues.md) für Details.
