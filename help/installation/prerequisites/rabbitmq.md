---
title: Nachrichtenbroker
description: Führen Sie diese Schritte aus, um die erforderliche Message Broker-Software (z. B. [!DNL RabbitMQ]) für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Nachrichtenbroker

Adobe Commerce verwendet den Open-Source-Nachrichtenbroker [!DNL RabbitMQ]. Es bietet ein zuverlässiges, hochverfügbares, skalierbares und portables Messaging-System.

Nachrichtenwarteschlangen bieten einen asynchronen Kommunikationsmechanismus, bei dem sich Absender und Empfänger einer Nachricht nicht miteinander in Verbindung setzen. Sie müssen auch nicht gleichzeitig mit der Nachrichtenwarteschlange kommunizieren. Wenn ein Absender eine Nachricht in eine Warteschlange stellt, wird sie so lange gespeichert, bis der Empfänger sie erhält.

Das Meldungswarteschlangesystem muss eingerichtet werden, bevor Sie Adobe Commerce installieren. Die grundlegende Sequenz lautet:

1. Installieren Sie [!DNL RabbitMQ] und alle Voraussetzungen.
1. Verbinden Sie [!DNL RabbitMQ] mit Adobe Commerce.

>[!NOTE]
>
>Sie können MySQL oder [!DNL RabbitMQ] für die Verarbeitung von Nachrichtenwarteschlangen verwenden. Weitere Informationen zum Einrichten des Nachrichtenwarteschlangensystems finden Sie unter [Übersicht über Nachrichtenwarteschlangen](https://developer.adobe.com/commerce/php/development/components/message-queues/). Wenn Sie die Bulk-API mit Adobe Commerce verwenden, verwendet die Nachrichtenwarteschlangensystemkonfiguration standardmäßig [!DNL RabbitMQ] als Nachrichtenbroker. Weitere Informationen finden Sie unter [Start message queue consumer](../../configuration/cli/start-message-queues.md) .

## Installieren Sie [!DNL RabbitMQ] auf Ubuntu

Um [!DNL RabbitMQ] auf Ubuntu 16 zu installieren, geben Sie den folgenden Befehl ein:

```bash
sudo apt install -y rabbitmq-server
```

Mit diesem Befehl werden auch die erforderlichen Erlang-Pakete installiert.

Wenn Sie eine ältere Version von Ubuntu haben, empfiehlt [!DNL RabbitMQ], das Paket von ihrer Website aus zu installieren.

1. Laden Sie das .deb-Paket von [rabbitmq-server](https://www.rabbitmq.com/download.html) herunter.
1. Installieren Sie das Paket mit `dpkg`.

Weitere Informationen finden Sie unter [Installieren auf Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) .

## Installieren Sie [!DNL RabbitMQ] auf CentOS

### Installieren von Erlang

[!DNL RabbitMQ] wurde mit der Programmiersprache Erlang geschrieben, die auf demselben System wie [!DNL RabbitMQ] installiert sein muss.

Weitere Informationen finden Sie unter [Manuelle Installation](https://www.erlang-solutions.com/downloads/) .

Informationen zum Installieren der richtigen Version finden Sie in der [[!DNL RabbitMQ]/Erlang-Versionsmatrix](https://www.rabbitmq.com/which-erlang.html) .

### Installieren Sie [!DNL RabbitMQ]

Der [!DNL RabbitMQ] -Server ist in CentOS enthalten, aber die Version ist häufig alt. [!DNL RabbitMQ] empfiehlt die Installation des Pakets von seiner Website aus.

Die neueste unterstützte Version finden Sie auf der Seite [!DNL RabbitMQ] install . Adobe Commerce 2.3 und 2.4 unterstützen [!DNL RabbitMQ] 3.8.x.

Weitere Informationen finden Sie unter [Installieren auf RPM-basiertem Linux](https://www.rabbitmq.com/install-rpm.html) .

## Konfigurieren von [!DNL RabbitMQ]

Lesen Sie die offizielle [!DNL RabbitMQ] Dokumentation, um [!DNL RabbitMQ] zu konfigurieren und zu verwalten. Beachten Sie die folgenden Punkte:

* Umgebungsvariablen
* Port-Zugriff
* Standardbenutzerkonten
* Starten und Beenden des Brokers
* Systembeschränkungen

## Installieren mit [!DNL RabbitMQ] und Verbinden

Wenn Sie Adobe Commerce _nach_ installieren, fügen Sie während der Installation die folgenden Befehlszeilenparameter hinzu:[!DNL RabbitMQ]

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dabei gilt:

| Parameter | Beschreibung |
|--- |--- |
| `--amqp-host` | Der Hostname, auf dem [!DNL RabbitMQ] installiert ist. |
| `--amqp-port` | Der Anschluss, über den eine Verbindung zu [!DNL RabbitMQ] hergestellt werden soll. Der Standardwert ist `5672`. |
| `--amqp-user` | Der Benutzername für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht den Standardbenutzer `guest`. |
| `--amqp-password` | Das Kennwort für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht das Standardkennwort `guest`. |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung mit [!DNL RabbitMQ]. Der Standardwert ist `/`. |
| `--amqp-ssl` | Gibt an, ob eine Verbindung zu [!DNL RabbitMQ] hergestellt werden soll. Der Standardwert ist `false`. Wenn Sie den Wert auf &quot;true&quot;setzen, finden Sie weitere Informationen unter SSL konfigurieren . |

## [!DNL RabbitMQ] verbinden

Wenn Sie Adobe Commerce bereits installiert haben und eine Verbindung mit [!DNL RabbitMQ] herstellen möchten, fügen Sie in der Datei `<install_directory>/app/etc/env.php` den Abschnitt `queue` hinzu, damit er dem folgenden ähnelt:

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

Sie können auch [!DNL RabbitMQ] -Konfigurationswerte mithilfe des Befehls `bin/magento setup:config:set` festlegen:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Führen Sie nach dem Ausführen des Befehls oder Aktualisieren der `<install_directory>/app/etc/env.php`-Datei mit AMQP-Konfigurationswerten `bin/magento setup:upgrade` aus, um die Änderungen anzuwenden und die erforderlichen Warteschlangen und Austausche in [!DNL RabbitMQ] zu erstellen.

## SSL konfigurieren

Um die Unterstützung für SSL zu konfigurieren, bearbeiten Sie die Parameter `ssl` und `ssl_options` in der Datei `<install_directory>/app/etc/env.php` , sodass sie den folgenden ähneln:

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

Nachdem Sie Adobe Commerce und [!DNL RabbitMQ] verbunden haben, müssen Sie die Verbraucher in der Nachrichtenwarteschlange starten. Weitere Informationen finden Sie unter [Konfigurieren von Nachrichtenwarteschlangen](../../configuration/cli/start-message-queues.md) .
