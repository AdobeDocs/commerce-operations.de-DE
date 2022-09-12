---
title: Nachrichtenbroker
description: Führen Sie diese Schritte aus, um die erforderliche Software für den Nachrichtenbroker (wie RabbitMQ) für lokale Installationen von Adobe Commerce und Magento Open Source zu installieren und zu konfigurieren.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Nachrichtenbroker

Adobe Commerce verwendet den Open-Source-Nachrichtenbroker RabbitMQ. Es bietet ein zuverlässiges, hochverfügbares, skalierbares und portables Messaging-System.

Nachrichtenwarteschlangen bieten einen asynchronen Kommunikationsmechanismus, bei dem sich Absender und Empfänger einer Nachricht nicht miteinander in Verbindung setzen. Sie müssen auch nicht gleichzeitig mit der Nachrichtenwarteschlange kommunizieren. Wenn ein Absender eine Nachricht in eine Warteschlange stellt, wird sie so lange gespeichert, bis der Empfänger sie erhält.

Das Meldungswarteschlangesystem muss eingerichtet werden, bevor Sie Adobe Commerce oder Magento Open Source installieren. Die grundlegende Sequenz lautet:

1. Installieren Sie RabbitMQ und alle Voraussetzungen.
1. Verbinden Sie RabbitMQ mit Adobe Commerce oder Magento Open Source.

>[!NOTE]
>
>Sie können MySQL oder RabbitMQ zur Verarbeitung von Nachrichtenwarteschlangen verwenden. Weitere Informationen zum Einrichten des Nachrichtenwarteschlangensystems finden Sie unter [Übersicht über Nachrichtenwarteschlangen](https://developer.adobe.com/commerce/php/development/components/message-queues/). Wenn Sie die Bulk API mit Adobe Commerce verwenden, wird bei der Konfiguration des Nachrichtenwarteschlangesystems standardmäßig RabbitMQ als Nachrichtenbroker verwendet. Siehe [Starten von Nachrichtenwarteschlangen-Verbrauchern](../../configuration/cli/start-message-queues.md) für weitere Informationen.

## Installieren von RabbitMQ auf Ubuntu

Um RabbitMQ auf Ubuntu 16 zu installieren, geben Sie den folgenden Befehl ein:

```bash
sudo apt install -y rabbitmq-server
```

Mit diesem Befehl werden auch die erforderlichen Erlang-Pakete installiert.

Wenn Sie eine ältere Version von Ubuntu haben, empfiehlt RabbitMQ die Installation des Pakets von seiner Website aus.

1. Laden Sie das .deb-Paket herunter von [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installieren Sie das Paket mit `dpkg`.

Siehe [Installieren auf Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) für weitere Informationen.

## Installieren von RabbitMQ auf CentOS

### Installieren von Erlang

RabbitMQ wurde mit der Programmiersprache Erlang geschrieben, die auf demselben System wie RabbitMQ installiert sein muss.

Siehe [Manuelle Installation](https://www.erlang-solutions.com/downloads/) für weitere Informationen.

Siehe Abschnitt [Versionsmatrix von RabbitMQ/Erlang](https://www.rabbitmq.com/which-erlang.html) um die richtige Version zu installieren.

### Installieren von RabbitMQ

Der RabbitMQ-Server ist in CentOS enthalten, aber die Version ist oft alt. RabbitMQ empfiehlt die Installation des Pakets von seiner Website aus.

Auf der Installationsseite von RabbitMQ finden Sie die neueste unterstützte Version. Adobe Commerce und Magento Open Source 2.3 und 2.4 unterstützen RabbitMQ 3.8.x.

Siehe [Installieren unter RPM-basiertem Linux](https://www.rabbitmq.com/install-rpm.html) für weitere Informationen.

## Konfigurieren von RabbitMQ

Lesen Sie die offizielle RabbitMQ-Dokumentation, um RabbitMQ zu konfigurieren und zu verwalten. Beachten Sie die folgenden Punkte:

* Umgebungsvariablen
* Port-Zugriff
* Standardbenutzerkonten
* Starten und Beenden des Brokers
* Systembeschränkungen

## Installieren mit RabbitMQ und Verbinden

Wenn Sie Adobe Commerce oder Magento Open Source installieren _after_ Wenn Sie RabbitMQ installieren, fügen Sie während der Installation die folgenden Befehlszeilenparameter hinzu:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dabei gilt:

| Parameter | Beschreibung |
|--- |--- |
| `--amqp-host` | Der Hostname, auf dem RabbitMQ installiert ist. |
| `--amqp-port` | Der für die Verbindung mit RabbitMQ zu verwendende Port. Der Standardwert ist `5672`. |
| `--amqp-user` | Der Benutzername für die Verbindung mit RabbitMQ. Verwenden Sie nicht den Standardbenutzer `guest`. |
| `--amqp-password` | Das Kennwort für die Verbindung mit RabbitMQ. Verwenden Sie nicht das Standardkennwort `guest`. |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung mit RabbitMQ. Der Standardwert ist `/`. |
| `--amqp-ssl` | Gibt an, ob eine Verbindung zu RabbitMQ hergestellt werden soll. Der Standardwert ist `false`. Wenn Sie den Wert auf &quot;true&quot;setzen, finden Sie weitere Informationen unter SSL konfigurieren . |

## KanbitMQ verbinden

Wenn Sie bereits Adobe Commerce oder Magento Open Source installiert haben und diese mit RabbitMQ verbinden möchten, fügen Sie eine `queue` im Abschnitt `<install_directory>/app/etc/env.php` -Datei, sodass sie der folgenden ähnelt:

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

Sie können auch RabbitMQ-Konfigurationswerte festlegen, indem Sie die `bin/magento setup:config:set` command:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Nach dem Ausführen des Befehls oder Aktualisieren der `<install_directory>/app/etc/env.php` Datei mit AMQP-Konfigurationswerten, ausführen `bin/magento setup:upgrade` , um die Änderungen anzuwenden und die erforderlichen Warteschlangen und Austausche in RabbitMQ zu erstellen.

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

Nachdem Sie Adobe Commerce und RabbitMQ verbunden haben, müssen Sie die Benutzer der Nachrichtenwarteschlange starten. Siehe [Nachrichtenwarteschlangen konfigurieren](../../configuration/cli/start-message-queues.md) für Details.
