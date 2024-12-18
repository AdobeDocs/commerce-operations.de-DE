---
title: Nachrichten-Broker
description: Führen Sie diese Schritte aus, um die erforderliche Message Broker-Software (z. B.  [!DNL RabbitMQ]) für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Nachrichten-Broker

Adobe Commerce verwendet den [!DNL RabbitMQ] Open-Source-Nachrichtenbroker. Es bietet ein zuverlässiges, hochverfügbares, skalierbares und tragbares Messaging-System.

Nachrichtenwarteschlangen bieten einen asynchronen Kommunikationsmechanismus, bei dem sich Absender und Empfänger einer Nachricht nicht berühren. Sie müssen auch nicht gleichzeitig mit der Nachrichtenwarteschlange kommunizieren. Wenn ein Absender eine Nachricht in eine Warteschlange stellt, wird sie gespeichert, bis der Empfänger sie erhält.

Das Meldungswarteschlangensystem muss vor der Installation von Adobe Commerce eingerichtet werden. Die Grundsequenz ist:

1. Installieren Sie [!DNL RabbitMQ] und alle Voraussetzungen.
1. Verbinden von [!DNL RabbitMQ] mit Adobe Commerce.

>[!NOTE]
>
>Sie können MySQL oder [!DNL RabbitMQ] für die Verarbeitung der Nachrichtenwarteschlange verwenden. Einzelheiten zum Einrichten des Meldungswarteschlangen-Systems finden Sie unter [Meldungswarteschlangen - Übersicht](https://developer.adobe.com/commerce/php/development/components/message-queues/). Wenn Sie die Bulk API mit Adobe Commerce verwenden, verwendet die Systemkonfiguration für die Nachrichtenwarteschlange standardmäßig [!DNL RabbitMQ] als Nachrichtenbroker. Weitere Informationen [ Sie unter ](../../configuration/cli/start-message-queues.md) starten.

## Installieren von [!DNL RabbitMQ] auf Ubuntu

Um [!DNL RabbitMQ] auf Ubuntu 16 zu installieren, geben Sie den folgenden Befehl ein:

```bash
sudo apt install -y rabbitmq-server
```

Mit diesem Befehl werden auch die erforderlichen Erlang-Pakete installiert.

Wenn Sie eine ältere Version von Ubuntu haben, empfiehlt [!DNL RabbitMQ], das Paket von ihrer Website zu installieren.

1. Laden Sie das Paket &quot;.deb“ von [rabbitmq-server](https://www.rabbitmq.com/download.html) herunter.
1. Installieren Sie das Paket mit `dpkg`.

Siehe [Installieren auf Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) für weitere Informationen.

## Installieren von [!DNL RabbitMQ] auf CentOS

### Installieren von Erlang

[!DNL RabbitMQ] wurde mit der Programmiersprache Erlang geschrieben, die auf dem gleichen System wie [!DNL RabbitMQ] installiert werden muss.

Weitere Informationen finden [ unter ](https://www.erlang-solutions.com/downloads/) Installation.

Siehe die [[!DNL RabbitMQ]/Erlang-Versionsmatrix](https://www.rabbitmq.com/which-erlang.html) um die richtige Version zu installieren.

### Installieren von [!DNL RabbitMQ]

Der [!DNL RabbitMQ]-Server ist in CentOS enthalten, aber die Version ist oft alt. [!DNL RabbitMQ] empfiehlt, das Paket von ihrer Website aus zu installieren.

Die neueste unterstützte Version finden Sie auf der [!DNL RabbitMQ]-Installationsseite . Adobe Commerce 2.3 und 2.4 unterstützen [!DNL RabbitMQ] 3.8.x.

Weitere Informationen finden [ unter „Installieren unter RPM-](https://www.rabbitmq.com/install-rpm.html) Linux“.

## Konfigurieren von [!DNL RabbitMQ]

Lesen Sie die offizielle [!DNL RabbitMQ]-Dokumentation, um [!DNL RabbitMQ] zu konfigurieren und zu verwalten. Achten Sie auf die folgenden Elemente:

* Umgebungsvariablen
* Portzugang
* Standard-Benutzerkonten
* Broker starten und stoppen
* Systembeschränkungen

## Mit [!DNL RabbitMQ] installieren und verbinden

Wenn Sie Adobe Commerce _nach_ installieren, fügen Sie [!DNL RabbitMQ] während der Installation die folgenden Befehlszeilenparameter hinzu:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dabei gilt:

| Parameter | Beschreibung |
|--- |--- |
| `--amqp-host` | Der Hostname, auf dem [!DNL RabbitMQ] installiert ist. |
| `--amqp-port` | Der Port, über den eine Verbindung zu [!DNL RabbitMQ] hergestellt wird. Der Standardwert lautet `5672`. |
| `--amqp-user` | Der Benutzername für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht die standardmäßige `guest`. |
| `--amqp-password` | Das Kennwort für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht die `guest` Standardkennwort. |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung mit [!DNL RabbitMQ]. Der Standardwert lautet `/`. |
| `--amqp-ssl` | Gibt an, ob eine Verbindung zu [!DNL RabbitMQ] hergestellt werden soll. Der Standardwert lautet `false`. Wenn Sie den Wert auf „true“ gesetzt haben, finden Sie weitere Informationen unter Konfigurieren von SSL . |

## [!DNL RabbitMQ] verbinden

Wenn Sie Adobe Commerce bereits installiert hatten und Sie eine Verbindung mit [!DNL RabbitMQ] herstellen möchten, fügen Sie der `<install_directory>/app/etc/env.php` einen `queue` Abschnitt hinzu, sodass er etwa wie folgt aussieht:

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

Sie können [!DNL RabbitMQ] Konfigurationswerte auch mithilfe des `bin/magento setup:config:set` Befehls festlegen:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Nachdem Sie den Befehl ausgeführt oder die `<install_directory>/app/etc/env.php`-Datei mit AMQP-Konfigurationswerten aktualisiert haben, führen Sie `bin/magento setup:upgrade` aus, um die Änderungen anzuwenden und die erforderlichen Warteschlangen und Austausche in [!DNL RabbitMQ] zu erstellen.

## Konfigurieren von SSL

Um die Unterstützung für SSL zu konfigurieren, bearbeiten Sie die `ssl`- und `ssl_options` in der `<install_directory>/app/etc/env.php`-Datei so, dass sie den folgenden ähneln:

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

## Starten der Nachrichtenwarteschlangen-Verbraucher

Nachdem Sie Adobe Commerce und [!DNL RabbitMQ] verbunden haben, müssen Sie die Nachrichtenwarteschlangen-Verbraucher starten. Weitere [ finden Sie unter &quot;](../../configuration/cli/start-message-queues.md) konfigurieren“.
