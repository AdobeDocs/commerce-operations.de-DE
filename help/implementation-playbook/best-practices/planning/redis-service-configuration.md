---
title: Best Practices für die Konfiguration des Redis-Dienstes
description: Erfahren Sie, wie Sie die Zwischenspeicherleistung verbessern können, indem Sie die erweiterte Redis-Cache-Implementierung für Adobe Commerce verwenden.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 6772c4fe31cfcd18463b9112f12a2dc285b39324
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Best Practices für die Konfiguration des Redis-Dienstes

- Konfigurieren des L2-Cache für Redis
- Redis-Slave-Verbindung aktivieren
- Schlüssel vorab laden
- Gestalteten Cache aktivieren
- Trennen Sie den Redis-Cache von der Redis-Sitzung.
- Komprimieren Sie den Redis-Cache und verwenden Sie `gzip` für höhere Komprimierung

## Konfigurieren des L2-Cache für Redis

Konfigurieren Sie den L2-Cache von Redis, indem Sie die `REDIS_BACKEND` Bereitstellungsvariable in der `.magento.env.yaml` Konfigurationsdatei.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Informationen zur Umgebungskonfiguration in der Cloud-Infrastruktur finden Sie im Abschnitt [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) im _Benutzerhandbuch zu Commerce on Cloud Infrastructure_.

Informationen über Vor-Ort-Anlagen finden Sie unter [Konfigurieren des Redis-Seiten-Caching](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) im _Konfigurationshandbuch_.

>[!NOTE]
>
>Überprüfen Sie, ob Sie die neueste Version des `ece-tools` Paket. Wenn nicht, [Aktualisierung auf die neueste Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Sie können die in Ihrer lokalen Umgebung installierte Version mithilfe der Variablen `composer show magento/ece-tools` CLI-Befehl.


### L2-Cache-Speichergröße (Adobe Commerce Cloud)

Der L2-Cache verwendet eine [temporäres Dateisystem](https://en.wikipedia.org/wiki/Tmpfs) als Speichermechanismus. Im Vergleich zu spezialisierten Schlüssel-Wert-Datenbanksystemen verfügt ein temporäres Dateisystem nicht über eine Schlüsselausscheidungsrichtlinie, um die Speicherbelegung zu steuern.

Das Fehlen einer Speicherbelegungskontrolle kann dazu führen, dass die L2-Cache-Speicherbelegung mit der Zeit zunimmt, indem der veraltete Cache akkumuliert wird.

Um zu vermeiden, dass der Speicher von L2-Cache-Implementierungen erschöpft ist, löscht Adobe Commerce den Speicher, wenn ein bestimmter Schwellenwert erreicht wird. Der Standardschwellenwert beträgt 95 %.

Es ist wichtig, die maximale Auslastung des L2-Cache-Speichers basierend auf den Projektanforderungen für den Cache-Speicher anzupassen. Verwenden Sie eine der folgenden Methoden, um die Größe des Arbeitsspeichercache zu konfigurieren:

- Erstellen Sie ein Support-Ticket, um Größenänderungen der `/dev/shm` einhängen.
- Passen Sie die `cleanup_percentage` -Eigenschaft auf Anwendungsebene verwenden, um den maximalen Füllprozentsatz des Speichers zu begrenzen. Der verbleibende freie Speicher kann von anderen Diensten genutzt werden.
Sie können die Konfiguration in der Bereitstellungskonfiguration unter der Cache-Konfigurationsgruppe anpassen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>Die `cleanup_percentage` Die konfigurierbare Option wurde in Adobe Commerce 2.4.4 eingeführt.

Der folgende Code zeigt eine Beispielkonfiguration im `.magento.env.yaml` Datei:

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

Sie können die Speichernutzung des L2-Cache-Speichers auf jedem Knoten des Clusters mithilfe des folgenden CLI-Befehls überprüfen und nach der `/dev/shm` Linie.
Die Verwendung kann von Knoten zu Knoten variieren, sollte jedoch zum selben Wert konvertiert werden.

```bash
df -h
```

## Redis-Slave-Verbindung aktivieren

Aktivieren Sie die Redis-Slave-Verbindung im `.magento.env.yaml` Konfigurationsdatei, um nur einem Knoten den Lese- und Schreibverkehr zu ermöglichen, während die anderen Knoten den schreibgeschützten Traffic verarbeiten.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Siehe [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im _Benutzerhandbuch zu Commerce on Cloud Infrastructure_.

Konfigurieren Sie für lokale Adobe Commerce-Installationen die neue Redis-Cache-Implementierung mit der `bin/magento:setup` Befehle. Siehe [Verwenden von Redizes für den Standard-Cache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) im _Konfigurationshandbuch_.

>[!WARNING]
>
>Do _not_ Konfigurieren einer Redis-Slave-Verbindung für Cloud-Infrastrukturprojekte mit einer [skalierte/geteilte Architektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dies führt zu Redis-Verbindungsfehlern. Siehe [Anleitungen zur Redim-Konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im _Handel mit Cloud-Infrastruktur_ Handbuch.

## Schlüssel vorab laden

Um Daten zwischen Seiten wiederzuverwenden, listen Sie die Schlüssel für das Vorausfüllen im `.magento.env.yaml` Konfigurationsdatei.

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

Informationen über Vor-Ort-Anlagen finden Sie unter [Funktion zum Vorausfüllen umkehren](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) im _Konfigurationshandbuch_.

## Gestalteten Cache aktivieren

Reduzieren Sie die Wartezeiten von Sperren und verbessern Sie die Leistung - insbesondere bei zahlreichen Blöcken und Cache-Schlüsseln - durch Verwendung eines veralteten Caches, während Sie gleichzeitig einen neuen Cache generieren. Aktivieren Sie den veralteten Cache und definieren Sie die Cache-Typen in `.magento.env.yaml` Konfigurationsdatei:

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

Informationen zur Konfiguration von lokalen Installationen finden Sie unter [Optionen für veralteten Cache](../../../configuration/cache/level-two-cache.md#stale-cache-options) im _Konfigurationshandbuch_.

## Separate Redis-Cache- und Sitzungsinstanzen

Durch die Trennung des Redis-Cache von der Redis-Sitzung können Sie den Cache und die Sitzungen unabhängig verwalten. Dadurch wird verhindert, dass sich Cache-Probleme auf Sitzungen auswirken, was sich auf den Umsatz auswirken könnte. Jede Redis-Instanz wird auf ihrem eigenen Kern ausgeführt, was die Leistung verbessert.

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

1. Senden einer [Support-Ticket für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) , um die Bereitstellung einer neuen Redis-Instanz für Sitzungen in Produktions- und Staging-Umgebungen anzufordern. Aktualisieren einschließen `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien. Dies führt nicht zu Ausfallzeiten, erfordert jedoch eine Implementierung, um den neuen Dienst zu aktivieren.

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

Wenn Sie über 6 GB Redis verwenden `maxmemory`können Sie die Cache-Komprimierung verwenden, um den Speicherplatz zu reduzieren, der von den Schlüsseln belegt wird. Beachten Sie, dass es einen Kompromiss mit clientseitiger Leistung gibt. Wenn Sie über freie CPUs verfügen, aktivieren Sie sie. Siehe [Verwenden von Redizes für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md) im _Konfigurationshandbuch_.

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

- [Redis-Seiten-Cache](../../../configuration/cache/redis-pg-cache.md)
- [Verwenden von Redizes für die Sitzungsspeicherung](../../../configuration/cache/redis-session.md)
