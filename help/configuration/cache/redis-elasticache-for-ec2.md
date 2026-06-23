---
title: Konfigurieren von Redis mit AWS ElastiCache
description: Erfahren Sie, wie Sie AWS ElastiCache als Redis-Backend für Adobe Commerce auf EC2 verwenden. Hier finden Sie Informationen zu Einrichtung, Konfiguration und Validierung über die Befehlszeile.
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fbb1d92d5f8537e6f1436cd985af120114883df6
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---


# Konfigurieren von Redis mit AWS ElastiCache

Ab Commerce 2.4.3 können auf Amazon EC2 gehostete Instanzen einen AWS ElastiCache anstelle einer lokalen Redis-Instanz verwenden.

>[!WARNING]
>
>Dieser Abschnitt gilt nur für Commerce-Instanzen, die auf Amazon EC2-VPCs ausgeführt werden.

## Voraussetzungen

- **Erstellen eines Server-losen Redis-OSS-Cache** - Erstellen Sie über die AWS Management Console den Redis-Cache in derselben Region und in VPC der EC2-Instanz. Anweisungen finden Sie in der [AWS Elasticache-Dokumentation](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Überprüfen Sie die Verbindung mit Ihrer EC2 Commerce-Instanz**

   - Öffnen Sie eine SSH-Verbindung zu Ihrer EC2-Instanz
   - Installieren Sie auf der EC2-Instanz den Redis-Client:

     ```shell
     sudo apt-get install redis
     ```

   - Fügen Sie eine Eingangsregel zur EC2-Sicherheitsgruppe hinzu: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Fügen Sie eine Eingangsregel zur ElastiCache-Cluster-Sicherheitsgruppe hinzu: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Stellen Sie eine Verbindung zur Redis-CLI her:

     ```shell
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Konfigurieren von Commerce für die Verwendung des Clusters

Commerce unterstützt verschiedene Arten von Caching-Konfigurationen. Im Allgemeinen werden die Caching-Konfigurationen auf Frontend und Backend aufgeteilt. Die Frontend-Zwischenspeicherung ist als `default` klassifiziert und wird für jeden Cache-Typ verwendet. Sie können Caches auf niedrigerer Ebene anpassen oder aufteilen, um eine bessere Leistung zu erzielen. Eine gängige Redis-Konfiguration besteht darin, den Standard-Cache und den Seiten-Cache in eine eigene Redis-Datenbank (RDB) zu unterteilen.

Führen Sie `setup` Befehle aus, um die Redis-Endpunkte anzugeben.

So konfigurieren Sie Commerce für Redis als Standard-Caching:

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

So konfigurieren Sie das Caching von Commerce für Redis-Seiten:

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

So konfigurieren Sie Commerce für die Verwendung von Redis für die Sitzungsspeicherung:

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Überprüfen der Verbindung

**So überprüfen Sie, ob Commerce mit ElastiCache kommuniziert**:

1. Öffnen Sie eine SSH-Verbindung zur Commerce EC2-Instanz.
1. Starten Sie den Redis-Monitor.

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Öffnen Sie eine Seite in der Commerce-Benutzeroberfläche.
1. Überprüfen Sie die [Cache-Ausgabe](#verify-connectivity) in Ihrem Terminal.
