---
title: Message Broker (ActiveMQ Artemis)
description: Führen Sie diese Schritte aus, um Apache ActiveMQ Artemis Message Broker für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Message Broker (ActiveMQ Artemis)

Adobe Commerce unterstützt außerdem den Open-Source-Nachrichtenbroker ActiveMQ Artemis über das Simple Text Oriented Messaging Protocol (STOMP). Es bietet ein zuverlässiges und skalierbares Messaging-System, das Flexibilität für STOMP-basierte Integrationen bietet.


>[!NOTE]
>
>ActiveMQ Artemis wurde in Adobe Commerce 2.4.5 und höheren Versionen eingeführt. Weitere Informationen zur Installation von ActiveMQ Artemis in Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Einrichten des ActiveMQ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemq)Service im *Handbuch zu Commerce in Cloud*.

Nachrichtenwarteschlangen bieten einen asynchronen Kommunikationsmechanismus, bei dem sich Absender und Empfänger einer Nachricht nicht berühren. Sie müssen auch nicht gleichzeitig mit der Nachrichtenwarteschlange kommunizieren. Wenn ein Absender eine Nachricht in eine Warteschlange stellt, wird sie gespeichert, bis der Empfänger sie erhält.

Das Meldungswarteschlangensystem muss vor der Installation von Adobe Commerce eingerichtet werden. Die Grundsequenz ist:

1. Installieren Sie Apache ActiveMQ Artemis und alle Voraussetzungen.
1. Verbinden von ActiveMQ mit Adobe Commerce.

>[!NOTE]
>
>Sie können MySQL, ActiveMQ oder [!DNL RabbitMQ] für die Verarbeitung von Nachrichtenwarteschlangen verwenden. Einzelheiten zum Einrichten des Meldungswarteschlangen-Systems finden Sie unter [Meldungswarteschlangen - Übersicht](https://developer.adobe.com/commerce/php/development/components/message-queues/). Wenn Sie die Bulk API mit Adobe Commerce verwenden, verwendet die Systemkonfiguration für die Nachrichtenwarteschlange standardmäßig [!DNL RabbitMQ] als Nachrichtenbroker. Weitere Informationen [&#x200B; Sie unter &#x200B;](../../configuration/cli/start-message-queues.md) starten.

>[!TIP]
>
>Überprüfen Sie vor der [&#x200B; immer die Download-Seite &#x200B;](https://activemq.apache.org/components/artemis/download/)Apache ActiveMQ Artemis) auf die neueste stabile Version. Die Beispiele in diesem Dokument verwenden Version 2.42.0, die die neueste stabile Version vom September 2025 war.


## Installieren von Apache ActiveMQ Artemis

Sie können ActiveMQ Artemis entweder mit Docker (für die Entwicklung empfohlen) oder mit der manuellen Installation (für die Produktion empfohlen) installieren.

### Option 1: Docker-Installation (für die Entwicklung empfohlen)

#### Voraussetzungen

Stellen Sie sicher, dass Docker auf Ihrem System installiert ist und ausgeführt wird.

>[!TIP]
>
>Weitere Informationen zum offiziellen ActiveMQ Artemis Docker-Image finden Sie auf der [Apache ActiveMQ Artemis Docker Hub-Seite](https://hub.docker.com/r/apache/activemq-artemis).

#### Installationsschritte

1. Führen Sie ActiveMQ Artemis mit dem offiziellen Docker-Image aus:

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Mit benutzerdefinierten Anmeldeinformationen ausführen:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Docker-Verwaltungsbefehle

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Zugriff auf Dienste

Sobald der Docker-Container ausgeführt wird, können Sie auf Folgendes zugreifen:

- **Web-Konsole**: http://localhost:8161/console (Standardanmeldeinformationen: artemis/artemis)
- **STOMP-Port**: localhost:61613 (für Adobe Commerce-Verbindung)

>[!NOTE]
>
>Die Docker-Installation wird für die Entwicklung und Tests empfohlen. Für die Produktion sollten Sie die manuelle Installation mit den richtigen Sicherheitskonfigurationen verwenden.

### Option 2: Manuelle Installation auf Ubuntu/CentOS

#### Voraussetzungen

Stellen Sie sicher, dass Java 17 oder höher installiert ist (erforderlich für ActiveMQ Artemis 2.42.0+).

### Installationsschritte

1. Herunterladen und Installieren der neuesten Version von der [Apache ActiveMQ Artemis-Website](https://activemq.apache.org/components/artemis/download/). Seit September 2025 ist die neueste stabile Version 2.42.0:

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Erstellen Sie den `artemis` Benutzer und legen Sie die Eigentümerschaft fest:

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Erstellen Sie eine Broker-Instanz:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Broker starten:

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## Konfigurieren von ActiveMQ Artemis

Lesen Sie die offizielle ActiveMQ Artemis-Dokumentation, um den Broker zu konfigurieren und zu verwalten. Achten Sie auf die folgenden Elemente:

- Umgebungsvariablen
- Portzugriff (STOMP-Protokoll)
- Standardbenutzerkonten und -anmeldeinformationen
- Broker starten und stoppen
- Systembeschränkungen und Ressourcenoptimierung

### Wichtige Konfigurationsdateien

- `/var/lib/artemis-instance/etc/broker.xml` - Hauptbrokerkonfiguration
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Benutzerauthentifizierung
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Benutzerrollen
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrap-Konfiguration

### STOMP-Protokoll aktivieren

Überprüfen Sie `/var/lib/artemis-instance/etc/broker.xml` , um sicherzustellen, dass der STOMP-Akzeptor konfiguriert ist:

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Um SSL auf STOMP zu aktivieren, müssen Sie den `stomp-ssl` explizit hinzufügen.

## Mit ActiveMQ Artemis installieren und verbinden

Wenn Sie Adobe Commerce _nachdem_ installieren, fügen Sie während der Installation die folgenden Befehlszeilenparameter hinzu:

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Dabei gilt:

| Parameter | Beschreibung |
|--- |--- |
| `--stomp-host` | Der Hostname, auf dem ActiveMQ installiert ist. |
| `--stomp-port` | Der Port, der für die Verbindung mit ActiveMQ verwendet werden soll. Der Standardwert lautet `61613`. |
| `--stomp-user` | Der Benutzername für die Verbindung mit ActiveMQ. Verwenden Sie nicht die standardmäßige `artemis`. |
| `--stomp-password` | Das Kennwort für die Verbindung mit ActiveMQ. Verwenden Sie nicht die `artemis` Standardkennwort. |
| `--stomp-ssl` | Gibt an, ob eine Verbindung zu ActiveMQ hergestellt werden soll. Der Standardwert lautet `false`. Wenn Sie den Wert auf „true“ gesetzt haben, finden Sie weitere Informationen unter Konfigurieren von SSL . |

## ActiveMQ Artemis verbinden

Wenn Sie bereits eine Adobe Commerce-Instanz mit einer RabbitMQ (AMQP)-Konfiguration in der `<install_directory>/app/etc/env.php` haben und Sie sie mit ActiveMQ verbinden möchten, ersetzen Sie den `queue`-Abschnitt durch STOMP, sodass er in etwa wie folgt aussieht:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

Sie können die ActiveMQ-Konfigurationswerte auch mithilfe des `bin/magento setup:config:set`-Befehls festlegen (entfernen Sie die AMQP-Konfiguration, sofern sie in der `app/etc/env.php` vorhanden ist):

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

Nachdem Sie den Befehl ausgeführt oder die `<install_directory>/app/etc/env.php` mit STOMP-Konfigurationswerten aktualisiert haben, führen Sie `bin/magento setup:upgrade` aus, um die Änderungen anzuwenden und die erforderlichen Warteschlangen in ActiveMQ zu erstellen.

## Konfigurieren von SSL

Um die Unterstützung für SSL zu konfigurieren, bearbeiten Sie die `ssl`- und `ssl_options` in der `<install_directory>/app/etc/env.php`-Datei so, dass sie den folgenden ähneln:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### SSL-Konfigurationsoptionen

| Option | Beschreibung | Standard |
|--- |--- |--- |
| `verify_peer` | SSL-Zertifikat des Brokers überprüfen | `true` |
| `verify_peer_name` | Überprüfen, ob der Hostname des Brokers mit dem Zertifikat übereinstimmt | `true` |
| `allow_self_signed` | Zulassen selbstsignierter Zertifikate | `false` |
| `cafile` | Pfad zur CA-Zertifikatdatei für die Broker-Überprüfung | Erforderlich für SSL |
| `certfile` | Pfad zur Client-Zertifikatdatei (für gegenseitiges SSL) | optional |
| `keyfile` | Pfad zur Client-Datei mit privatem Schlüssel (für gegenseitiges SSL) | optional |
| `passphrase` | Passphrase für privaten Client-Schlüssel | optional |

### SSL-Entwicklungskonfiguration

Für Entwicklungsumgebungen können Sie entspannte SSL-Einstellungen verwenden:

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Leistungsoptimierung

ActiveMQ Artemis bietet mehrere Optionen zur Leistungsoptimierung:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Überwachung und Verwaltung

### Web-Konsole

ActiveMQ Artemis bietet eine Web-basierte Verwaltungskonsole, auf die unter folgender Adresse zugegriffen werden kann:
- URL: `http://localhost:8161/console`
- Standardmäßige Anmeldedaten: `artemis/artemis`

## Fehlerbehebung

### Häufige Probleme

1. **Verbindung verweigert**: Stellen Sie sicher, dass ActiveMQ Artemis ausgeführt wird und der STOMP-Akzeptor konfiguriert ist.
1. **Authentifizierung fehlgeschlagen**: Überprüfen Sie den Benutzernamen/das Kennwort sowohl in der Broker-Konfiguration als auch in der `env.php`.
1. **SSL-Handshake fehlgeschlagen**: SSL-Zertifikate und -Konfiguration überprüfen.




### STOMP-Verbindung überprüfen

Testen der STOMP-Verbindung mit Telnet:

```bash
telnet localhost 61613
```

Es sollte eine Verbindung hergestellt sein. Testen mit einem STOMP-Befehl:

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

Die erwartete Ausgabe sollte die hergestellte Verbindung und die STOMP-Protokollantwort anzeigen.

## Starten der Nachrichtenwarteschlangen-Verbraucher

Nachdem Sie Adobe Commerce und ActiveMQ Artemis verbunden haben, müssen Sie die Nachrichtenwarteschlange für Verbraucher starten. Weitere [&#x200B; finden Sie unter &quot;](../../configuration/cli/start-message-queues.md) konfigurieren“.

