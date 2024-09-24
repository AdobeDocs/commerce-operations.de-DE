---
title: Best Practices für die Konfiguration des Redis-Dienstes
description: Erfahren Sie, wie Sie die Zwischenspeicherleistung verbessern können, indem Sie die erweiterte Redis-Cache-Implementierung für Adobe Commerce verwenden.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 7f277fe6245aba851aba7ddc70be40343bdaecc7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Best Practices für die Konfiguration des Redis-Dienstes

- Konfigurieren des L2-Cache für Redis
- Redis-Slave-Verbindung aktivieren
- Schlüssel vorab laden
- Gestalteten Cache aktivieren
- Trennen Sie den Redis-Cache von der Redis-Sitzung.
- Komprimieren Sie den Redis-Cache und verwenden Sie `gzip` für höhere Komprimierung.

## Konfigurieren des L2-Cache für Redis

Konfigurieren Sie den Cache L2 Redis , indem Sie die Bereitstellungsvariable `REDIS_BACKEND` in der Konfigurationsdatei `.magento.env.yaml` festlegen.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Informationen zur Umgebungskonfiguration in der Cloud-Infrastruktur finden Sie unter [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) im _Commerce on Cloud Infrastructure Guide_.

Informationen zu lokalen Installationen finden Sie unter [Konfigurieren des Redis-Seiten-Caching](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) im _Konfigurationshandbuch_.

>[!NOTE]
>
>Vergewissern Sie sich, dass Sie die neueste Version des `ece-tools`-Pakets verwenden. Wenn nicht, [aktualisieren Sie auf die neueste Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Sie können die in Ihrer lokalen Umgebung installierte Version mithilfe des Befehls `composer show magento/ece-tools` CLI überprüfen.


### L2-Cache-Speichergröße (Adobe Commerce Cloud)

Der L2-Cache verwendet ein [temporäres Dateisystem](https://en.wikipedia.org/wiki/Tmpfs) als Speichermechanismus. Im Vergleich zu spezialisierten Schlüssel-Wert-Datenbanksystemen verfügt ein temporäres Dateisystem nicht über eine Schlüsselausscheidungsrichtlinie, um die Speicherbelegung zu steuern.

Das Fehlen einer Speicherbelegungskontrolle kann dazu führen, dass die L2-Cache-Speicherbelegung mit der Zeit zunimmt, indem der veraltete Cache akkumuliert wird.

Um zu vermeiden, dass der Speicher von L2-Cache-Implementierungen erschöpft ist, löscht Adobe Commerce den Speicher, wenn ein bestimmter Schwellenwert erreicht wird. Der Standardschwellenwert beträgt 95 %.

Es ist wichtig, die maximale Auslastung des L2-Cache-Speichers basierend auf den Projektanforderungen für den Cache-Speicher anzupassen. Verwenden Sie eine der folgenden Methoden, um die Größe des Arbeitsspeichercache zu konfigurieren:

- Erstellen Sie ein Support-Ticket, um Größenänderungen des `/dev/shm` -Runs anzufordern.
- Passen Sie die Eigenschaft `cleanup_percentage` auf Anwendungsebene an, um den maximalen Füllprozentsatz des Speichers zu begrenzen. Der verbleibende freie Speicher kann von anderen Diensten genutzt werden.
Sie können die Konfiguration in der Bereitstellungskonfiguration unter der Cache-Konfigurationsgruppe `cache/frontend/default/backend_options/cleanup_percentage` anpassen.

>[!NOTE]
>
>Die konfigurierbare `cleanup_percentage` -Option wurde in Adobe Commerce 2.4.4 eingeführt.

Der folgende Code zeigt eine Beispielkonfiguration in der Datei `.magento.env.yaml` :

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

Die Cache-Anforderungen können je nach Projektkonfiguration und benutzerdefiniertem Drittanbieter-Code variieren. Die Skalierung des L2-Cache-Speichers ermöglicht es, den L2-Cache ohne zu viele Schwellentreffer zu betreiben.
Idealerweise sollte sich die L2-Cache-Speichernutzung auf einer bestimmten Ebene unterhalb des Schwellenwerts stabilisieren, um häufige Speicherbereinigungen zu vermeiden.

Sie können die Speicherbelegung des L2-Cache-Speichers auf jedem Knoten des Clusters mithilfe des folgenden CLI-Befehls überprüfen und nach der Zeile `/dev/shm` suchen.
Die Verwendung kann von Knoten zu Knoten variieren, sollte jedoch zum selben Wert konvertiert werden.

```bash
df -h
```

## Redis-Slave-Verbindung aktivieren

Aktivieren Sie eine Redis-Slave-Verbindung in der Konfigurationsdatei `.magento.env.yaml`, damit nur ein Knoten Lese- und Schreibvorgänge-Traffic verarbeiten kann, während die anderen Knoten den schreibgeschützten Traffic verarbeiten.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Siehe [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im Leitfaden _Commerce on Cloud Infrastructure Guide_.

Bei lokalen Installationen von Adobe Commerce konfigurieren Sie die neue Redis-Cache-Implementierung mit den Befehlen `bin/magento:setup` . Siehe [Verwenden von Redis für den Standardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) im _Konfigurationshandbuch_.

>[!WARNING]
>
>Konfigurieren Sie _nicht_ eine Redis-Slave-Verbindung für Cloud-Infrastrukturprojekte mit einer [skalierten/geteilten Architektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dies führt zu Redis-Verbindungsfehlern. Siehe [Anleitung zur Redis-Konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im Handbuch _Commerce on Cloud Infrastructure_.

## Schlüssel vorab laden

Um Daten zwischen Seiten wiederzuverwenden, listen Sie die Schlüssel für das Vorausfüllen in der Konfigurationsdatei `.magento.env.yaml` auf.

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

Informationen zu lokalen Installationen finden Sie unter [Vorabladefunktion umkehren](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) im _Konfigurationshandbuch_.

## Gestalteten Cache aktivieren

Reduzieren Sie die Wartezeiten von Sperren und verbessern Sie die Leistung - insbesondere bei zahlreichen Blöcken und Cache-Schlüsseln - durch Verwendung eines veralteten Caches, während Sie gleichzeitig einen neuen Cache generieren. Aktivieren Sie den veralteten Cache und definieren Sie die Cache-Typen in der Konfigurationsdatei `.magento.env.yaml` :

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
>Im vorherigen Beispiel ist der Cache `full_page` für Adobe Commerce in Cloud-Infrastrukturprojekten nicht relevant, da er [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) verwendet.

Informationen zum Konfigurieren von lokalen Installationen finden Sie unter [Veraltete Cache-Optionen](../../../configuration/cache/level-two-cache.md#stale-cache-options) im _Konfigurationshandbuch_.

## Separate Redis-Cache- und Sitzungsinstanzen

Durch die Trennung des Redis-Cache von der Redis-Sitzung können Sie den Cache und die Sitzungen unabhängig verwalten. Dadurch wird verhindert, dass sich Cache-Probleme auf Sitzungen auswirken, was sich auf den Umsatz auswirken könnte. Jede Redis-Instanz wird auf ihrem eigenen Kern ausgeführt, was die Leistung verbessert.

1. Aktualisieren Sie die Konfigurationsdatei `.magento/services.yaml` .

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

1. Aktualisieren Sie die Konfigurationsdatei `.magento.app.yaml` .

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Senden Sie ein [Adobe Commerce-Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) , um die Bereitstellung einer neuen Redis-Instanz für Sitzungen in Produktions- und Staging-Umgebungen anzufordern. Schließen Sie die aktualisierten Konfigurationsdateien `.magento/services.yaml` und `.magento.app.yaml` ein. Dies führt nicht zu Ausfallzeiten, erfordert jedoch eine Implementierung, um den neuen Dienst zu aktivieren.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie sich die Portnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Fügen Sie die Portnummer zur Konfigurationsdatei `.magento.env.yaml` hinzu.

   >[!NOTE]
   >`disable_locking` muss auf `1` gesetzt sein.
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

1. Entfernen Sie Sitzungen aus der [Standarddatenbank](../../../configuration/cache/redis-pg-cache.md) (`db 0`) in der Redis-Cache-Instanz.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Während der Bereitstellung sollten im [Build- und Bereitstellungsprotokoll](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs) die folgenden Zeilen angezeigt werden:

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

## Cachekomprimierung

Wenn Sie mehr als 6 GB Redis `maxmemory` verwenden, können Sie die Cache-Komprimierung verwenden, um den von den Schlüsseln belegten Speicherplatz zu reduzieren. Beachten Sie, dass es einen Kompromiss mit clientseitiger Leistung gibt. Wenn Sie über freie CPUs verfügen, aktivieren Sie sie. Siehe [Verwenden von Redis für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md) im _Konfigurationshandbuch_.

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

- [Redis-Seiten-Cache](../../../configuration/cache/redis-pg-cache.md)
- [Verwenden von Redizes für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md)
