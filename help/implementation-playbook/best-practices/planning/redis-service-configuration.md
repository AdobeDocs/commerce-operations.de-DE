---
title: Best Practices für die Konfiguration des Redis-Service
description: Erfahren Sie, wie Sie die Caching-Leistung mithilfe der erweiterten Redis-Cache-Implementierung für Adobe Commerce verbessern können.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 7f277fe6245aba851aba7ddc70be40343bdaecc7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Best Practices für die Konfiguration des Redis-Service

- Konfigurieren des Redis-L2-Cache
- Redis-Slave-Verbindung aktivieren
- Schlüssel vorab laden
- Veralteten Cache aktivieren
- Trennen des Redis-Cache von der Redis-Sitzung
- Komprimiert den Redis-Cache und verwendet `gzip` für eine höhere Komprimierung.

## Konfigurieren des Redis-L2-Cache

Konfigurieren Sie den Redis-L2-Cache, indem Sie die `REDIS_BACKEND`-Bereitstellungsvariable in der `.magento.env.yaml`-Konfigurationsdatei festlegen.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Informationen zur Umgebungskonfiguration in der Cloud-Infrastruktur finden Sie in den [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) im Handbuch zu _Commerce in der Cloud-Infrastruktur_.

Bei On-Premise-Installationen finden Sie weitere Informationen unter [Konfigurieren des Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)Seitencachings im _Konfigurationshandbuch_.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie die neueste Version des `ece-tools` verwenden. Falls nicht, [aktualisieren Sie auf die neueste Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Sie können die in Ihrer lokalen Umgebung installierte Version mithilfe des `composer show magento/ece-tools` CLI-Befehls überprüfen.


### Speicherdimensionierung des L2-Cache (Adobe Commerce Cloud)

Der L2-Cache verwendet ein [temporäres Dateisystem](https://en.wikipedia.org/wiki/Tmpfs) als Speichermechanismus. Im Vergleich zu spezialisierten Schlüssel-Wert-Datenbanksystemen verfügt ein temporäres Dateisystem nicht über eine Richtlinie zum Verdrängen von Schlüsseln, um die Speichernutzung zu kontrollieren.

Fehlende Speicherbelegungskontrolle kann dazu führen, dass die Speicherbelegung im L2-Cache im Laufe der Zeit zunimmt, indem der veraltete Cache gesammelt wird.

Um zu vermeiden, dass der Arbeitsspeicher bei L2-Cache-Implementierungen erschöpft ist, löscht Adobe Commerce den Speicher, wenn ein bestimmter Schwellenwert erreicht wird. Der standardmäßige Schwellenwert ist 95 %.

Es ist wichtig, die maximale Speicherauslastung des L2-Cache basierend auf den Projektanforderungen für Cache-Speicher anzupassen. Verwenden Sie eine der folgenden Methoden, um die Cache-Größe des Speichers zu konfigurieren:

- Erstellen Sie ein Support-Ticket, um Größenänderungen der `/dev/shm` anzufordern.
- Passen Sie die `cleanup_percentage` auf Anwendungsebene an, um den maximalen Füllprozentsatz des Speichers zu begrenzen. Der verbleibende freie Speicher kann von anderen Diensten genutzt werden.
Sie können die Konfiguration in der Bereitstellungskonfiguration unter der Cache-Konfigurationsgruppe `cache/frontend/default/backend_options/cleanup_percentage` anpassen.

>[!NOTE]
>
>Die `cleanup_percentage` konfigurierbare Option wurde in Adobe Commerce 2.4.4 eingeführt.

Der folgende Code zeigt eine Beispielkonfiguration in der `.magento.env.yaml`:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

Die Cache-Anforderungen können je nach Projektkonfiguration und benutzerdefiniertem Code von Drittanbietern variieren. Aufgrund des Umfangs der Speicherdimensionierung für den L2-Cache kann der L2-Cache ohne zu viele Schwellenwerttreffer ausgeführt werden.
Idealerweise sollte sich die Speicherauslastung des L2-Caches auf einem bestimmten Niveau unterhalb des Schwellenwerts stabilisieren, nur um eine häufige Speicherbereinigung zu vermeiden.

Sie können die Speicherauslastung des L2-Cache-Speichers auf jedem Knoten des Clusters mit dem folgenden CLI-Befehl überprüfen und nach der `/dev/shm` suchen.
Die Nutzung kann von Knoten zu Knoten variieren, sollte aber auf denselben Wert fallen.

```bash
df -h
```

## Redis-Slave-Verbindung aktivieren

Aktivieren Sie in der `.magento.env.yaml`-Konfigurationsdatei eine Redis-Slave-Verbindung, damit nur ein Knoten Lese-/Schreibdatenverkehr verarbeiten kann, während die anderen Knoten nur den schreibgeschützten Datenverkehr verarbeiten.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Siehe [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im _Handbuch zu Commerce in Cloud-Infrastrukturen_.

Konfigurieren Sie bei lokalen Adobe Commerce-Installationen die neue Redis-Cache-Implementierung mithilfe der `bin/magento:setup`. Siehe [Verwenden von Redis für den ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)-Cache) im _Konfigurationshandbuch_.

>[!WARNING]
>
>Konfigurieren _nicht_ eine Redis-Slave-Verbindung für Cloud-Infrastrukturprojekte mit einer [skalierten/geteilten Architektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dies verursacht Redis-Verbindungsfehler. Siehe [Anleitung zur Redis-Konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im _Handbuch zu Commerce_ Cloud-Infrastruktur.

## Schlüssel vorab laden

Um Daten zwischen Seiten wiederzuverwenden, listen Sie die Schlüssel zum Vorausfüllen in der `.magento.env.yaml`-Konfigurationsdatei auf.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Bei On-Premise-Installationen finden Sie weitere Informationen unter [Redis-Vorabladefunktion](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) im _Konfigurationshandbuch_.

## Veralteten Cache aktivieren

Verringern Sie die Sperrwartezeiten und verbessern Sie die Leistung - insbesondere bei der Verarbeitung zahlreicher Blöcke und Cache-Schlüssel - durch die Verwendung eines veralteten Cache bei gleichzeitiger Generierung eines neuen Cache. Aktivieren Sie veralteten Cache und definieren Sie Cache-Typen in der `.magento.env.yaml` Konfigurationsdatei:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>Im vorherigen Beispiel ist der `full_page`-Cache für Adobe Commerce für Cloud-Infrastrukturprojekte nicht relevant, da sie „Fastly[ verwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly).

Informationen zum Konfigurieren von On-Premise-Installationen finden Sie unter [Veraltete Cache](../../../configuration/cache/level-two-cache.md#stale-cache-options) im _Konfigurationshandbuch_.

## Separater Redis-Cache und Sitzungsinstanzen

Wenn Sie den Redis-Cache von der Redis-Sitzung trennen, können Sie den Cache und die Sitzungen unabhängig verwalten. Cache-Probleme werden so verhindert, dass Sitzungen beeinträchtigt werden, was sich auf den Umsatz auswirken könnte. Jede Redis-Instanz wird auf ihrem eigenen Kern ausgeführt, wodurch die Leistung verbessert wird.

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

1. Senden Sie ein [Adobe Commerce-Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)-Ticket, um die Bereitstellung einer neuen Redis-Instanz anzufordern, die Sitzungen in Produktions- und Staging-Umgebungen gewidmet ist. Schließen Sie die aktualisierten `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien ein. Dies führt zu keinen Ausfallzeiten, erfordert jedoch eine Bereitstellung, um den neuen Service zu aktivieren.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie sich die Portnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Fügen Sie die Portnummer zur `.magento.env.yaml` hinzu.

   >[!NOTE]
   >`disable_locking` muss auf `1` gesetzt werden.
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

1. Entfernen Sie Sitzungen aus der [Standarddatenbank](../../../configuration/cache/redis-pg-cache.md) (`db 0`) auf der Redis-Cache-Instanz.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Während der Bereitstellung sollten die folgenden Zeilen im „Build- [ Bereitstellungsprotokoll“ angezeigt ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```
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

## Cache-Komprimierung

Wenn Sie mehr als 6 GB Redis-`maxmemory` verwenden, können Sie die Cache-Komprimierung verwenden, um den von den Schlüsseln belegten Speicherplatz zu reduzieren. Beachten Sie, dass es einen Zielkonflikt mit der Client-seitigen Leistung gibt. Wenn Sie CPUs haben, aktivieren Sie diese. Siehe [Verwenden von Redis für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md) im _Konfigurationshandbuch_.

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

## Weitere Informationen

- [Redis-Seitencache](../../../configuration/cache/redis-pg-cache.md)
- [Redis für Sitzungsspeicher verwenden](../../../configuration/cache/redis-session.md)
