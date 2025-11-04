---
title: Best Practices für die Konfiguration von Valley-Services
description: Erfahren Sie, wie Sie die Caching-Leistung mithilfe der erweiterten Valkey-Cache-Implementierung für Adobe Commerce verbessern können.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 75dc606da65196619028e99ec44841db3988a73e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Best Practices für die Konfiguration von Valley-Services

Adobe empfiehlt die folgenden Best Practices beim Konfigurieren des Valkey-Service:

## Valkey L2-Cache konfigurieren

Konfigurieren Sie den Valkey L2-Cache, indem Sie die Bereitstellungsvariable `VALKEY_BACKEND` in der Konfigurationsdatei `.magento.env.yaml` festlegen.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Informationen zur Umgebungskonfiguration in der Cloud-Infrastruktur finden Sie in den [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) im Handbuch zu _Commerce in der Cloud-Infrastruktur_.

Informationen zu On-Premise-Installationen finden Sie unter [Konfigurieren des Valkey](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching)Seitencachings im _Konfigurationshandbuch_.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie die neueste Version des `ece-tools` verwenden. Falls nicht, [aktualisieren Sie auf die neueste Version](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Sie können die in Ihrer lokalen Umgebung installierte Version mithilfe des `composer show magento/ece-tools` CLI-Befehls überprüfen.

### L2-Cache-Speicherdimensionierung (Adobe Commerce Cloud)

Der L2-Cache verwendet ein [temporäres Dateisystem](https://en.wikipedia.org/wiki/Tmpfs) als Speichermechanismus. Im Vergleich zu spezialisierten Schlüssel-Wert-Datenbanksystemen verfügt ein temporäres Dateisystem nicht über eine Richtlinie zum Verdrängen von Schlüsseln, um die Speichernutzung zu kontrollieren.

Fehlende Speicherbelegungskontrolle kann dazu führen, dass die Speicherbelegung im L2-Cache im Laufe der Zeit zunimmt, indem der veraltete Cache gesammelt wird.

Um zu vermeiden, dass der Arbeitsspeicher bei L2-Cache-Implementierungen erschöpft ist, löscht Adobe Commerce den Speicher, wenn ein bestimmter Schwellenwert erreicht wird. Der standardmäßige Schwellenwert ist 95 %.

Es ist wichtig, die maximale Speicherauslastung des L2-Cache basierend auf den Projektanforderungen für Cache-Speicher anzupassen. Verwenden Sie eine der folgenden Methoden, um die Cache-Größe des Speichers zu konfigurieren:

- Erstellen Sie ein Support-Ticket, um Größenänderungen der `/dev/shm` anzufordern.
- Passen Sie die `cleanup_percentage` auf Anwendungsebene an, um den maximalen Füllprozentsatz des Speichers zu begrenzen. Der verbleibende freie Speicher kann von anderen Diensten genutzt werden.
Sie können die Konfiguration in der Bereitstellungskonfiguration unter der Cache-Konfigurationsgruppe `cache/frontend/default/backend_options/cleanup_percentage` anpassen.

>[!NOTE]
>
>Die `cleanup_percentage` wurde mit Adobe Commerce 2.4.4 eingeführt.

Das folgende Beispiel zeigt eine `CACHE_CONFIGURATION` in der `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

Die Cache-Anforderungen können je nach Projektkonfiguration und benutzerdefiniertem Code von Drittanbietern variieren. Aufgrund des Umfangs der Speicherdimensionierung für den L2-Cache kann der L2-Cache ohne unnötige Schwellenwertüberschreitungen betrieben werden.
Idealerweise sollte sich die Speicherauslastung des L2-Cache auf einem bestimmten Niveau unterhalb des Schwellenwerts stabilisieren, um eine häufige Speicherbereinigung zu vermeiden.

Sie können die Speicherauslastung des L2-Cache-Speichers auf jedem Knoten des Clusters mit dem folgenden CLI-Befehl überprüfen und dann nach der `/dev/shm` suchen.
Die Nutzung kann von Knoten zu Knoten variieren, sollte aber auf denselben Wert fallen.

```bash
df -h
```

## Valley Slave-Verbindung aktivieren

Aktivieren Sie in der `.magento.env.yaml`-Konfigurationsdatei eine Valley-Slave-Verbindung, damit nur ein Knoten Lese-/Schreibverkehr verarbeiten kann, während die anderen Knoten nur den schreibgeschützten Verkehr verarbeiten.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Weitere Informationen finden Sie unter [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) im _Handbuch zu Commerce in Cloud-Infrastruktur_.

Konfigurieren Sie bei lokalen Adobe Commerce-Installationen die neue Valkey-Cache-Implementierung mithilfe der `bin/magento:setup`. Weitere Informationen finden Sie unter [Valkey für Standardcache verwenden](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) im _Konfigurationshandbuch_.

>[!WARNING]
>
>Konfigurieren _nicht_ eine Valkey-Slave-Verbindung für Cloud-Infrastrukturprojekte mit einer [skalierten/geteilten Architektur](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Dies verursacht Valley-Verbindungsfehler. Weitere Informationen finden Sie in der [Valkey-Konfigurationsanleitung](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) im _Handbuch zu Commerce in Cloud-_.

## Schlüssel vorab laden

Um Daten zwischen Seiten wiederzuverwenden, listen Sie die Schlüssel zum Vorausfüllen in der `.magento.env.yaml`-Konfigurationsdatei auf.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

Informationen zu lokalen Installationen finden Sie unter [Valkey-Vorabladefunktion](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) im _Konfigurationshandbuch_.

## Veralteten Cache aktivieren

Verringern Sie die Sperrwartezeiten und verbessern Sie die Leistung, insbesondere bei der Verarbeitung zahlreicher Blöcke und Cache-Schlüssel, indem Sie einen veralteten Cache verwenden und gleichzeitig einen neuen Cache generieren. Aktivieren Sie den veralteten Cache und definieren Sie Cache-Typen in der `.magento.env.yaml`-Konfigurationsdatei:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
>Im vorherigen Beispiel ist der `full_page`-Cache für Adobe Commerce für Cloud-Infrastrukturprojekte nicht relevant, da sie „Fastly[&#x200B; verwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly).

Informationen zum Konfigurieren von On-Premise-Installationen finden Sie unter [Veraltete Cache](../../../configuration/cache/level-two-cache.md#stale-cache-options) im _Konfigurationshandbuch_.

Während der Bereitstellung sollten die folgenden Zeilen im „Build- [&#x200B; Bereitstellungsprotokoll“ angezeigt &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations#build-and-deploy-logs):

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Cache-Komprimierung

Wenn Sie mehr als 6 GB Valkey-`maxmemory` verwenden, können Sie die Cache-Komprimierung verwenden, um den von den Schlüsseln belegten Speicherplatz zu reduzieren. Beachten Sie, dass es einen Zielkonflikt mit der Client-seitigen Leistung gibt. Wenn Sie über CPUs verfügen, empfiehlt Adobe, diese zu aktivieren. Siehe [Verwenden von Valkey für &#x200B;](../../../configuration/cache/valkey-session.md) Sitzungsspeicherung“ im _Konfigurationshandbuch_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
