---
title: Best Practices für die Konfiguration des Redis-Dienstes
description: Erfahren Sie, wie Sie die Zwischenspeicherleistung verbessern können, indem Sie die erweiterte Redis-Cache-Implementierung für Adobe Commerce verwenden.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Best Practices für die Konfiguration des Redis-Dienstes

- Verwenden Sie die erweiterte Redis-Cache-Implementierung, die die folgenden Optimierungen enthält, um die Anzahl der Redis-Abfragen zu minimieren, die für jede Anfrage von Adobe Commerce ausgeführt werden:
   - Reduziert die Größe der Netzwerk-Datenübertragungen zwischen Redis und Adobe Commerce
   - Verringert den Verbrauch der CPU-Zyklen, indem die Fähigkeit des Adapters verbessert wird, automatisch zu bestimmen, was geladen werden muss
   - Reduziert Race-Bedingungen für Redis-Schreibvorgänge
- Trennen Sie den Redis-Cache von der Redis-Sitzung.
- Komprimieren Sie den Redis-Cache und verwenden Sie `gzip` Verbesserung der Leistung

## Erweiterte Redis-Cache-Implementierung

Aktualisieren Sie Ihre Konfiguration, um die erweiterte Redis-Cache-Implementierung zu verwenden. `\Magento\Framework\Cache\Backend\Redis`.

### Konfigurieren von Cloud-Bereitstellungen

Konfigurieren Sie den erweiterten Redis-Cache, indem Sie die `REDIS_BACKEND` Bereitstellungsvariable in der `.magento.env.yaml` Konfigurationsdatei.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Weitere Informationen finden Sie unter [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) Variablenbeschreibung in _Benutzerhandbuch zu Commerce on Cloud Infrastructure_.

>[!NOTE]
>
> Überprüfen Sie die `ece-tools` -Version, die in Ihrer lokalen Umgebung über die Befehlszeile mit dem `composer show magento/ece-tools` Befehl. Falls erforderlich, [Aktualisierung auf die neueste Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Do _not_ Konfigurieren einer Redis-Slave-Verbindung für Cloud-Infrastrukturprojekte mit einer [skalierte Architektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dies führt zu Redis-Verbindungsfehlern. Siehe [Anleitung zur Konfiguration von Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im _Handel mit Cloud-Infrastruktur_ Handbuch.

### Vor-Ort-Bereitstellungen konfigurieren

Für lokale Adobe Commerce-Bereitstellungen konfigurieren Sie die neue Redis-Cache-Implementierung mit dem `bin/magento:setup` Befehle. Anweisungen finden Sie unter [Verwenden von Redizes für den Standard-Cache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Separate Cache- und Sitzungsinstanzen

Durch Trennung des Redis-Cache von der Redis-Sitzung können Sie den Cache und die Sitzungen unabhängig verwalten, um zu verhindern, dass Cache-Probleme Sitzungen beeinträchtigen.

1. Aktualisieren Sie die `.magento/services.yaml` Konfigurationsdatei.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. Aktualisieren Sie die `.magento.app.yaml` Konfigurationsdatei.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Senden einer [Support-Ticket für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) , um die Konfiguration des Redis-Dienstes in Pro Production- und Staging-Umgebungen zu ändern. Aktualisieren einschließen `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie sich die Portnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Fügen Sie die Portnummer zum `.magento.env.yaml` Konfigurationsdatei.

   >[!NOTE]
   >`disable_locking` muss auf `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Entfernen Sie Sitzungen aus dem [Standarddatenbank](../../../configuration/cache/redis-pg-cache.md) (`db 0`) in der Redis-Cache-Instanz.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Während der Bereitstellung sollten die folgenden Zeilen in der [Protokoll erstellen und bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Cachekomprimierung

Verwenden Sie die Cachekomprimierung, beachten Sie jedoch, dass es einen Kompromiss mit der clientseitigen Leistung gibt. Wenn Sie über freie CPUs verfügen, aktivieren Sie sie. Siehe [Verwenden von Redizes für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md).

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Zusätzliche Informationen

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Verwenden von Redizes für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md)
