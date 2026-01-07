---
title: Konfigurieren von Redis mit AWS ElastiCache
description: Erfahren Sie, wie Sie für auf EC2 gehostete Commerce-Instanzen AWS ElastiCache anstelle einer lokalen Redis-Instanz verwenden. Erfahren Sie mehr über Befehlszeileneinrichtung, Konfigurationsoptionen und Validierungstechniken.
feature: Configuration, Cache
source-git-commit: 908796587e78b80d699354c0506ca948d0f37518
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Konfigurieren von Redis mit AWS ElastiCache

Ab Commerce 2.4.3 können auf Amazon EC2 gehostete Instanzen einen AWS ElastiCache anstelle einer lokalen Redis-Instanz verwenden.

>[!WARNING]
>
>Dieser Abschnitt gilt nur für Commerce-Instanzen, die auf Amazon EC2-VPCs ausgeführt werden. Dies funktioniert nicht für lokale Installationen.

## Voraussetzungen

- **Erstellen eines Server-losen Redis-OSS-Cache** - Erstellen Sie über die AWS Management Console den Redis-Cache in derselben Region und in VPC der EC2-Instanz. Anweisungen finden Sie in der [AWS Elasticache-Dokumentation]&#x200B;(https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html.

- **Überprüfen Sie die Verbindung mit Ihrer EC2 Commerce-Instanz**

   - Öffnen Sie eine SSH-Verbindung zu Ihrer EC2-Instanz
   - Installieren Sie auf der EC2-Instanz den Redis-Client:

     ```bash
     sudo apt-get install redis
     ```

   - Fügen Sie eine Eingangsregel zur EC2-Sicherheitsgruppe hinzu: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Fügen Sie eine Eingangsregel zur ElastiCache-Cluster-Sicherheitsgruppe hinzu: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Stellen Sie eine Verbindung zur Redis-CLI her:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Konfigurieren von Commerce für die Verwendung des Clusters

Commerce unterstützt verschiedene Arten von Caching-Konfigurationen. Im Allgemeinen werden die Caching-Konfigurationen auf Frontend und Backend aufgeteilt. Die Frontend-Zwischenspeicherung ist als `default` klassifiziert und wird für jeden Cache-Typ verwendet. Sie können Caches auf niedrigerer Ebene anpassen oder aufteilen, um eine bessere Leistung zu erzielen. Eine gängige Redis-Konfiguration besteht darin, den Standard-Cache und den Seiten-Cache in eine eigene Redis-Datenbank (RDB) zu unterteilen.

Führen Sie `setup` Befehle aus, um die Redis-Endpunkte anzugeben.

So konfigurieren Sie Commerce für Redis als Standard-Caching:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

So konfigurieren Sie das Caching von Commerce für Redis-Seiten:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

So konfigurieren Sie Commerce für die Verwendung von Redis für die Sitzungsspeicherung:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Überprüfen der Verbindung

**So überprüfen Sie, ob Commerce mit ElastiCache kommuniziert**:

1. Öffnen Sie eine SSH-Verbindung zur Commerce EC2-Instanz.
1. Starten Sie den Redis-Monitor.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Öffnen Sie eine Seite in der Commerce-Benutzeroberfläche.
1. Überprüfen Sie die [Cache-Ausgabe](#verify-the-redis-connection) in Ihrem Terminal.
