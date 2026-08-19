---
title: Best Practices für die Konfiguration von Valley und Redis Service
description: Erfahren Sie, wie Sie die Redis- und Valkey-Zwischenspeicherung für Adobe Commerce on Cloud konfigurieren, einschließlich Replikatverbindungen, L2-Cache, veraltetem Cache und Sitzungsspeicher.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce in Cloud Manager" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten."
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Best Practices für die Konfiguration des Valley- und Redis-Service

Verwenden Sie diese Empfehlungen beim Konfigurieren von Redis oder Valkey für Adobe Commerce-Anwendungscache, Sitzungsspeicher und L2-Cache für Adobe Commerce in Cloud-Bereitstellungen.

Informationen zur lokalen Cache-Konfiguration in Adobe Commerce finden Sie unter [L2-Cache-Konfiguration für die Leistungsoptimierung](/help/configuration/cache/level-two-cache.md).

>[!NOTE]
>
>In diesem Abschnitt werden der Anwendungscache und die Sitzungs-Backends von Commerce behandelt. Das HTTP-Caching ganzer Seiten, wie Fastly oder Varnish, ist eine separate Caching-Ebene und wird unabhängig konfiguriert. Änderungen am Anwendungs-Cache-Backend ersetzen oder konfigurieren nicht den HTTP-Vollseiten-Cache.

Diese Empfehlungen betreffen Folgendes:

- Einen unterstützten Cache-Service auswählen
- Replikatverbindung aktivieren
- Separate Cache- und Sitzungsinstanzen
- Cache-Komprimierung konfigurieren
- Asynchrone Freigabe aktivieren
- Multithread-E/A aktivieren
- Client-Zeitüberschreitungen und erneute Versuche erhöhen
- Konfigurieren des L2-Cache, einschließlich Vorabladeschlüssel, veralteten Cache und [!DNL Symfony] L2-Cache
- Konfigurationsbeispiele überprüfen

## Einen unterstützten Cache-Service auswählen

| Adobe Commerce-Version | Empfohlener Cache-Service | L2-Cache-Implementierung |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8 und früher, wenn von der exakten Version unterstützt | Redis oder Valkey | RemoteSynchronizedCache |
| 2.4.9 und höher | Tal | symfony_l2 |

Redis wird für die Cache-Konfiguration in Adobe Commerce 2.4.9 und in Patch-Versionen, in denen die Systemanforderungen stattdessen Valkey angeben, nicht unterstützt. Überprüfen Sie immer die genaue Commerce-Version, die Patch-Ebene und die Service-Version in [Cache-Backend-Optionen und Speicherreferenz](/help/configuration/cache/cache-options.md) und [Systemanforderungen](/help/installation/system-requirements.md).

>[!NOTE]
>
>Stellen Sie sicher, dass Sie die neueste Version des `ece-tools` verwenden. Falls nicht, [aktualisieren Sie auf die neueste Version](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Sie können die in Ihrer lokalen Umgebung installierte Version mithilfe des `composer show magento/ece-tools` CLI-Befehls überprüfen.

## Replikatverbindung aktivieren

Aktivieren Sie die Replikatverbindung in der `.magento.env.yaml`. Durch diese Änderung kann Adobe Commerce eine zusätzliche Cache-Verbindung für Lesevorgänge verwenden, während der primäre Endpunkt weiterhin für Schreibvorgänge verwendet wird. Durch diese Konfiguration kann die Leselast auf dem primären Cache-Service reduziert und der Lesetraffic effektiver verteilt werden.

>[!NOTE]
>
>Ob eine Replikatverbindung verfügbar ist, hängt von der Topologie Ihres Projekts (z. B. Single-Node- versus Split- oder HA-Architektur) und von der `ece-tools` Version ab. Bevor Sie diese Einstellung verwenden, überprüfen Sie, ob eine Replikatbeziehung für Ihren Dienst vorhanden ist, indem Sie `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp` ausführen und nach einem `USE_SLAVE_CONNECTION` Eintrag suchen. Um zu bestätigen, ob Ihre Topologie einen Replikat-Endpunkt bereitstellt, aktualisieren Sie `ece-tools` und stellen Sie erneut bereit oder wenden Sie sich an den Adobe Commerce-Support, wenn kein `USE_SLAVE_CONNECTION` vorhanden ist.
>
>`symfony_l2` wird die Unterstützung der Replikatverbindung über eine Aktualisierung der `ece-tools`- und Cloud-Patches bereitgestellt. Über eine Änderung der `VALKEY_USE_SLAVE_CONNECTION: true` hinaus ist keine zusätzliche Cache-Konfiguration erforderlich. Aktualisieren Sie auf die neueste `ece-tools` Version, um die Fehlerbehebung zu erhalten.

>[!BEGINTABS]

>[!TAB Valkey-Konfiguration]

Verwenden Sie für Valley Folgendes:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Details zur Konfiguration von Umgebungsvariablen finden Sie unter [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) im _Handbuch zu Commerce in Cloud Infrastructure_.

>[!TAB Redis-Konfiguration]

Verwenden Sie für Redis:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Details zur Konfiguration von Umgebungsvariablen finden Sie unter [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) im _Handbuch zu Commerce in Cloud Infrastructure_.

>[!ENDTABS]

## Separate Cache- und Sitzungsinstanzen

Cache- und Sitzungskonfiguration sind unabhängig. `SESSION_CONFIGURATION` beeinflusst das Cache-Verhalten nicht, unabhängig davon, welches Cache-Backend oder welche L2-Cache-Implementierung Sie verwenden. Wenn Sie den Cache von den Sitzungen trennen, können Sie diese unabhängig verwalten. Es verringert Konflikte zwischen Cache- und Sitzungs-Traffic, verhindert, dass Cache-bedingter Druck sich auf Sitzungen auswirkt, und ermöglicht die Dimensionierung und Abstimmung jeder Redis- oder Valley-Instanz auf ihre eigene Arbeitslast.

>[!IMPORTANT]
>
>Die Bereitstellung einer dedizierten Sitzungsinstanz für Produktion und Staging erfolgt nicht im Self-Service. Dazu müssen Sie ein [Adobe Commerce-Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)Ticket mit Ihren aktualisierten `.magento/services.yaml`- und `.magento.app.yaml` wie in Schritt 3 unten beschrieben einreichen.

Gehen Sie wie folgt vor, um eine dedizierte Instanz für Sitzungen bereitzustellen:

>[!BEGINTABS]

>[!TAB Valkey]

1. Aktualisieren Sie die `.magento/services.yaml` Konfigurationsdatei und ersetzen Sie `<version>` durch die verwendeten Service-Versionen. Siehe [Systemanforderungen](/help/installation/system-requirements.md) für unterstützte Service-Versionen nach Version.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
     disk: 2048
   ```

1. Aktualisieren Sie die `.magento.app.yaml` Konfigurationsdatei.

   ```yaml
   relationships:
     database: "mysql:mysql"
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Fordern Sie eine neue Valley-Instanz an, die Sitzungen zu Produktions- und Staging-Umgebungen gewidmet ist.

   Senden Sie ein [Adobe Commerce-Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Schließen Sie die aktualisierten `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien ein.

   Dieses Update verursacht keine Ausfallzeiten, erfordert jedoch eine Bereitstellung, um den neuen Service zu aktivieren.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie die Portnummer.

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Fügen Sie die Portnummer zur `.magento.env.yaml` hinzu.

   >[!IMPORTANT]
   >
   >Konfigurieren Sie den Valkey-Sitzungs-Port nur, wenn `ece-tools` ihn nicht automatisch aus der Definition des `MAGENTO_CLOUD_RELATIONSHIPS` Valkey-Sitzungs-Service erkennen kann.

   >[!NOTE]
   >
   >Für optimale Leistung `disable_locking` auf `1` gesetzt. In seltenen Fällen, in denen Wettlaufsituationen aufgrund einer hohen Aktivität von gleichzeitigen Sitzungen auftreten, aktivieren Sie die Sperrung, indem Sie `0` festlegen.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Entfernen Sie Sitzungen aus der [Standarddatenbank](/help/configuration/cache/redis-pg-cache.md) (`db 0`) auf der Valkey-Cache-Instanz.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis]

1. Aktualisieren Sie die `.magento/services.yaml` Konfigurationsdatei und ersetzen Sie `<version>` durch die verwendeten Service-Versionen.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

1. Fordern Sie eine neue Redis-Instanz für Sitzungen in Produktions- und Staging-Umgebungen an.

   Senden Sie ein [Adobe Commerce-Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Schließen Sie die aktualisierten `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien ein.

   Dieses Update verursacht keine Ausfallzeiten, erfordert jedoch eine Bereitstellung, um den neuen Service zu aktivieren.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie die Portnummer.

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Fügen Sie die Portnummer zur `.magento.env.yaml` hinzu.

   >[!IMPORTANT]
   >
   >Konfigurieren Sie den Redis-Sitzungs-Port nur, wenn `ece-tools` ihn nicht automatisch aus der Definition des `MAGENTO_CLOUD_RELATIONSHIPS` Redis-Sitzungs-Service erkennen kann.

   >[!NOTE]
   >
   >Für optimale Leistung `disable_locking` auf `1` gesetzt. In seltenen Fällen, in denen Wettlaufsituationen aufgrund einer hohen Aktivität von gleichzeitigen Sitzungen auftreten, aktivieren Sie die Sperrung, indem Sie `0` festlegen.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Entfernen Sie Sitzungen aus der [Standarddatenbank](/help/configuration/cache/redis-pg-cache.md) (`db 0`) auf der Redis-Cache-Instanz.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Cache-Komprimierung

Wenn Sie mehr als 6 GB Redis- oder Valkey-`maxmemory` verwenden, können Sie die Cache-Komprimierung aktivieren, um den von Schlüsseln belegten Speicherplatz zu reduzieren. Beachten Sie, dass diese Einstellung Client-seitige Leistung gegen Speichereinsparungen eintauscht. Wenn Sie über freie CPU-Kapazität verfügen, sollten Sie diese aktivieren. Siehe [Verwenden von Redis für ](/help/configuration/cache/redis-session.md) oder [Verwenden von Valkey für ](/help/configuration/cache/valkey-session.md) im _Konfigurationshandbuch_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Asynchrone Freigabe aktivieren

Um `lazyfree` in der Adobe Commerce-Cloud-Infrastruktur zu aktivieren, reichen Sie ein [Adobe Commerce-Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)Ticket ein, in dem Sie darum bitten, die folgende Redis- oder Valkey-Konfiguration auf Ihre Umgebungen anzuwenden:

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Wenn `lazyfree` aktiviert ist, lädt Redis oder Valley die Speicherrückgewinnung auf Hintergrund-Threads aus, um Auslagerungen, Abläufe, serverinitiierte Löschvorgänge, Benutzerlöschvorgänge und Replikatdatensatzleerungen durchzuführen. Dies reduziert die Blockierung des Haupt-Threads und kann die Anfragelatenz verringern.

>[!NOTE]
>
>Durch die Option `lazyfree-lazy-user-del yes` verhält sich der `DEL`-Befehl wie `UNLINK`, wodurch die Verknüpfung von Schlüsseln sofort aufgehoben wird und der Speicher asynchron freigegeben wird.

>[!WARNING]
>
>Da die Freigabe im Hintergrund erfolgt, wird Speicher, der von gelöschten, abgelaufenen oder entfernten Schlüsseln verwendet wird, zugewiesen, bis die Arbeit von Hintergrund-Threads abgeschlossen ist. Wenn Ihre Redis- oder Valley-Instanz bereits unter hohem Speicherdruck steht, testen Sie sie vorsichtig und erwägen Sie zuerst, den Speicherdruck zu reduzieren. Deaktivieren Sie beispielsweise den Block-Cache für bestimmte Fälle und trennen Sie die Cache- und Sitzungs-Redis-Instanzen wie oben beschrieben.

## Multithread-E/A aktivieren

Um das Redis-I/O-Threading in der Adobe Commerce-Cloud-Infrastruktur zu aktivieren, senden Sie ein [Adobe Commerce Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) mit der unten stehenden Anfrage zur I/O-Threading-Konfiguration. Durch diese Konfiguration kann der Durchsatz verbessert werden, indem Socket-Lese- und -Schreibvorgänge sowie das Parsen von Befehlen vom Haupt-Thread ausgelagert werden, was zulasten einer höheren CPU-Nutzung geht. Validieren Sie unter Last und überwachen Sie Ihre Hosts.

>[!BEGINTABS]

>[!TAB Konfigurieren von I/O-Threads für Redis]

Für Redis:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Konfigurieren von I/O-Threads für Valkey]

Für Valley:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]

>[!NOTE]
>
>I/O-Threads parallelisieren nur Client-I/O und Parsing. Die Ausführung des Redis-Befehls erfolgt weiterhin in einem einzigen Thread.

>[!WARNING]
>
>Die Aktivierung von I/O-Threads kann die Nutzung von CPU erhöhen und nützt nicht jeder Arbeitslast. Beginnen Sie mit einem konservativen Wert und Benchmark. Wenn die Latenz ansteigt oder CPU überlastet ist, reduzieren Sie `io-threads` oder deaktivieren Sie Lesevorgänge in I/O-Threads.

## Client-Zeitüberschreitungen und erneute Versuche erhöhen

Erhöhen Sie die Toleranz des Redis- oder Valkey-Cache-Clients auf kurze Zeiträume der Sättigung, indem Sie die Backend-Optionen in `.magento.env.yaml` anpassen.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Diese Einstellungen können unregelmäßige Verbindungs- und Lesezeitüberschreitungsfehler während kurzer Spitzen reduzieren, indem die Verbindungseinrichtung wiederholt wird und mehr Zeit für Antworten von Redis oder Valley bleibt.

>[!NOTE]
>
>Diese Einstellungen können bei einer kurzen Überlastung helfen, aber sie beheben nicht die dauerhafte Überlastung.

## L2-Cache konfigurieren

Konfigurieren Sie den L2-Cache, indem Sie die Bereitstellungsvariable `VALKEY_BACKEND` oder `REDIS_BACKEND` in der Konfigurationsdatei `.magento.env.yaml` festlegen.

Es gibt zwei L2-Cache-Implementierungen für Adobe Commerce in der Cloud-Infrastruktur.

- Legacy-Implementierung verwendet `RemoteSynchronizedCache` mit `Cm_Cache_Backend_File` für lokalen Speicher
- Die moderne Implementierung nutzt `symfony_l2` mit PSR-6-Konformität und verbesserter Leistung. Die moderne Implementierung unterstützt nur Valkey.

| Commerce-Version | RemoteSynchronizedCache mit Valley | Empfohlene Konfiguration |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8 und früher<br>(wenn Valkey unterstützt wird) | Unterstützter Legacy-L2-Pfad | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9 und höher | Nicht unterstützt | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>Redis-Cache wird für Adobe Commerce 2.4.9 oder für Patch-Versionen nach 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 und 2.4.8-p4 nicht unterstützt. Verwenden Sie Valley für die Cache-Konfiguration, bei der Redis nicht unterstützt wird. Siehe [Systemanforderungen](/help/installation/system-requirements.md) für unterstützte Cache-Services nach Version.

>[!BEGINTABS]

>[!TAB Valkey-Konfiguration]

Verwenden Sie unter Commerce 2.4.8 und früheren Versionen, die Valkey unterstützen, diese Konfiguration:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Verwenden Sie in Commerce 2.4.9 und höher die folgende Konfiguration mit der [!DNL Symfony] L2-Implementierung:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Redis-Konfiguration]

Verwenden Sie unter Version 2.4.8 und früheren Commerce-Versionen, die Redis unterstützen:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Weitere Informationen zur Umgebungskonfiguration finden Sie unter [`REDIS_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) im Handbuch zu _Commerce in Cloud-Infrastrukturen_.

>[!ENDTABS]

### Migrieren nach Valkey mit [!DNL Symfony] L2-Cache

Wenn Sie ein vorhandenes Adobe Commerce on Cloud-Projekt von `RemoteSynchronizedCache` (Redis oder Valkey) nach `symfony_l2` migrieren, lesen Sie Folgendes, bevor Sie `.magento.env.yaml` aktualisieren.

- **Die Bereitstellungsvariable muss geändert werden, um die `symfony_l2` zu aktivieren.** Wenn Sie `VALKEY_BACKEND: symfony_l2` allein festlegen, wird die vollständige L2-Cache-Konfiguration automatisch erstellt. Sie müssen die `backend_options` Ihrer zuvor verwendeten `RemoteSynchronizedCache`-Konfiguration nicht manuell neu erstellen. Siehe [Konfigurieren [!DNL Symfony] L2-Cache](#configure-symfony-l2-cache).

- **Entfernen Sie `preload_keys` aus Ihrer vorhandenen Konfiguration.** Wenn Ihre `RemoteSynchronizedCache`-Konfiguration `preload_keys` unter `CACHE_CONFIGURATION` enthält, entfernen Sie sie im Rahmen der Migration. Siehe [Vorabladen von Schlüsseln](#preload-keys) für Details.

- **Das veraltete Cache-Verhalten ändert sich automatisch.** Unter `symfony_l2` aktiviert `ece-tools` automatisch veralteten Cache für gängige Cache-Typen (z. B. `layout`, `block_html`, `full_page` und `translate`), ohne dass die erforderliche manuelle Frontend-Konfiguration erforderlich `RemoteSynchronizedCache`. Wenn Sie den veralteten Cache zuvor manuell konfiguriert haben und Ihr exaktes früheres Verhalten beibehalten möchten, lesen Sie [Veralteten Cache aktivieren](#enable-stale-cache) bevor Sie migrieren.

- **Komprimierung erfordert ein explizites Flag.** Wenn Sie `symfony_l2` Komprimierung über `CACHE_CONFIGURATION` anpassen, wird die Komprimierung durch Festlegen von `compression_lib` allein nicht aktiviert - `compress_data` muss ebenfalls festgelegt werden. Siehe [Cache-Komprimierung](#cache-compression).

- **Redis ist kein unterstütztes Remote-Backend für `symfony_l2`.** Migrieren Sie im Rahmen dieser Änderung nach Valley. Siehe [Einrichten des Valkey-Service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey).

- **Die Sitzungskonfiguration ist von dieser Migration nicht betroffen.** `SESSION_CONFIGURATION` ist unabhängig vom Cache-Backend und muss beim Wechsel zu `symfony_l2` nicht geändert werden. Siehe [Trennen von Cache- und Sitzungsinstanzen](#separate-cache-and-session-instances).

>[!IMPORTANT]
>
>Konfigurieren Sie `symfony_l2` nicht manuell in `app/etc/env.php`. Konfigurieren Sie sie über `.magento.env.yaml` so, `ece-tools` die Einstellung während der Bereitstellung anwendet und beibehält. Siehe [Konfigurieren [!DNL Symfony] L2-Cache](#configure-symfony-l2-cache).

### Schlüssel vorausfüllen

Schlüssel zum Vorausfüllen können auf eine `symfony_l2` angewendet werden, wenn Sie die richtige Platzierung verwenden (unter `backend_options` oder `remote_backend_options`). Es wird jedoch von Adobe nicht empfohlen, Preload-Schlüssel mit `symfony_l2` zu verwenden. Die Implementierung der `symfony_l2`-Vorabladung ruft Schlüssel einzeln ab, sodass Roundtrips nicht so reduziert werden wie bei `RemoteSynchronizedCache`. Außerdem kann die Last auf Valkey erhöht werden, ohne dass ein Leistungsvorteil entsteht.

Mit der Vorabladefunktion können Sie eine Liste häufig verwendeter Schlüssel bereitstellen, die Magento bei dem ersten Zugriff während einer Anfrage in einer einzigen Pipeline abruft. Magento speichert die abgerufenen Werte dann für den Rest der Anfrage im PHP-Speicher, was die wiederholten Roundtrips zu Redis oder Valkey reduziert und die Bootstrap-Performance der Anfragen für diese Schlüssel verbessern kann.

Häufig verwendete Tasten können durch die Überwachung aktiver Befehle auf Redis oder Valley identifiziert werden:

Die Vorabladeschlüssel werden in der `.magento.env.yaml`-Konfigurationsdatei konfiguriert. Dieses Beispiel zeigt die Konfiguration für Adobe Commerce 2.4.8 und frühere Versionen, die `RemoteSynchronizedCache` unterstützen.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Um die Schlüssel aufzulisten, führen Sie den folgenden Befehl aus:

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Drücken Sie nach 10 Sekunden **Strg+C**. Führen Sie dann den folgenden Befehl aus:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In diesem Protokoll werden die Schlüssel aufgelistet, die Sie vorab laden können. Um den Inhalt eines Schlüssels anzuzeigen, führen Sie den folgenden Befehl aus:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### Veralteten Cache aktivieren

Veralteter Cache ist eine L2-Cache-Funktion, mit der Adobe Commerce einen vorhandenen lokalen Cache-Wert aus `/dev/shm` bereitstellen kann, während derselbe Eintrag bereits durch eine andere Anfrage neu generiert wird. Dies verhindert, dass gleichzeitige Anfragen warten. Dadurch werden Cache-Stampedes und Sperrkonflikte bei der Neuerstellung teurer Cache-Einträge reduziert.

Legen Sie für Adobe Commerce 2.4.9 und höher `VALKEY_BACKEND: symfony_l2` in der `.magento.env.yaml` fest:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools` generiert automatisch sowohl ein `default` Frontend als auch ein `stale_cache_enabled` Frontend und ordnet dem veralteten Frontend die folgenden Cache-Typen zu: `layout`, `block_html`, `reflection`, `config_integration`, `config_integration_api`, `full_page` und `translate`. Für diese Typen ist keine manuelle `use_stale_cache` oder Frontend-Konfiguration erforderlich. Diese automatische Zuordnung ist selbst ein Beispiel für die Aktivierung des selektiven veralteten Caches. Nur bestimmte Cache-Typen verwenden das veraltete Frontend, nicht alle. Informationen zum Anpassen der `stale_cache_enabled` zugeordneten Typen oder zum Hinzufügen von Typen über die Standardwerte hinaus finden Sie unter [Anpassen der L2 [!DNL Symfony] Cache-Konfiguration](#customize-the-symfony-l2-cache-configuration).

>[!NOTE]
>
>Der `full_page`-Cache-Typ ist für Adobe Commerce in Cloud-Infrastrukturprojekten nicht relevant, da sie Fastly für die Zwischenspeicherung ganzer Seiten verwenden. In den manuellen Konfigurationsbeispielen in diesem Abschnitt werden `full_page` aus diesem Grund weggelassen, obwohl `ece-tools` sie in die standardmäßige `symfony_l2`-Zuordnung einbezieht.

Die folgende Legacy-Konfiguration gilt für Adobe Commerce 2.4.8 und früher, die `RemoteSynchronizedCache` verwenden und manuellen veralteten Cache und Frontend-Konfiguration erfordern. Dieselbe selektive, globale Empfehlung gilt hier.

#### Funktionsweise des alten RemoteSynchronizedCache-Backends

Mit `RemoteSynchronizedCache` verwaltet Magento zwei Kopien jedes Cache-Eintrags: eine lokale Kopie in `/dev/shm` und eine Remote-Kopie in Redis oder Valkey. Wenn die Remote Copy nicht verfügbar ist und bereits eine Regenerierungssperre für diesen Schlüssel vorhanden ist, können gleichzeitige -Anfragen den vorherigen lokalen Wert empfangen, anstatt zu warten, bis der neue Wert geschrieben wird.

Um den veralteten Cache für 2.4.8 und frühere Versionen zu aktivieren, konfigurieren Sie ihn in der `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!WARNING]
>
>Die obige Konfiguration ermöglicht veralteten Cache im Frontend für den `default`-Cache, das veraltetes Cache-Verhalten auf alle Cache-Einträge anwendet, die dieses Frontend verwenden. Magento Core-Cache-Typen funktionieren mit dieser Einstellung erwartungsgemäß. Wenn Ihr Projekt jedoch benutzerdefinierten Code oder Erweiterungen enthält, die über die generische `\Magento\Framework\App\Cache`-API (z. B. `$this->cache->save()`) ohne dediziertes Cache-Frontend in den Cache schreiben, können diese Einträge während der Regenerierung auch veraltete Werte liefern.
>
>
>Wenn dies zu unerwartetem Verhalten in Ihren Anpassungen führt, lassen Sie den veralteten Cache im `default`-Frontend deaktiviert und aktivieren Sie ihn nur für ausgewählte Cache-Typen, wie unten dargestellt.

#### Veralteten Cache pro Cache-Typ einzeln aktivieren (veraltet)

Sie können veralteten Cache nur für ausgewählte Cache-Typen aktivieren, indem Sie ein dediziertes Cache-Frontend in `.magento.env.yaml` definieren und die ausgewählten Cache-Typen ihm zuordnen. Dieser manuelle Ansatz gilt für das alte `RemoteSynchronizedCache`-Backend. `symfony_l2` führt diese Zuordnung wie oben beschrieben automatisch durch.

Um ordnungsgemäß zu funktionieren, muss das benutzerdefinierte Frontend als vollständiges Frontend unter `CACHE_CONFIGURATION.frontend` definiert werden. Es reicht nicht aus, nur `use_stale_cache: true` für einen neuen Frontend-Namen zu definieren.

**Beispielkonfigurationen**

Für Redis ab Version 2.4.8 aktiviert die folgende Konfiguration veralteten Cache für die Cache-Typen `layout`, `reflection`, `config_integration`, `config_integration_api` und `translate`, während andere mit dem standardmäßigen Frontend mit deaktiviertem veralteten Cache verbleiben:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!NOTE]
>
>Wenn das Quell-Frontend mit zusätzlichen Backend-Optionen konfiguriert ist, kopieren Sie diese Optionen in `stale_cache_enabled`, damit das neue Frontend dasselbe Verhalten beibehält.

### Konfigurieren [!DNL Symfony] L2-Cache

Adobe Commerce 2.4.9 und höher unterstützt das `symfony_l2`-Cache-Backend. Das `symfony_l2`-Backend ist die Cache-Implementierung, die Adobe Commerce verwendet, um das L1- und L2-Cache-Verhalten zu verwalten. **Redis oder Valkey als Remote-Cache-Service werden nicht ersetzt.**

>[!IMPORTANT]
>
>Konfigurieren Sie `symfony_l2` über die `.magento.env.yaml` Bereitstellungsvariable so, `ece-tools` die Einstellung während der Bereitstellung angewendet und beibehalten wird. Konfigurieren Sie `symfony_l2` nicht manuell in `app/etc/env.php`, da die Bereitstellung manuelle `env.php` überschreiben kann. Wenn `ece-tools` keine `symfony_l2` anwendet, kann Commerce auf dateibasierten Cache zurückgreifen, was den Festplatten-E/A erhöhen, den Dateisystem-Replikationsaufwand in Umgebungen mit mehreren Knoten erhöhen und die Leistung beeinträchtigen kann.

Um `symfony_l2` Cache für Adobe Commerce 2.4.9 zu verwenden, führen Sie die folgenden Schritte aus:

- Stellen Sie sicher, dass das Cloud-Projekt [`ece-tools` Paket v2002.2.12 ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) höher verwendet.

- Legen Sie die Bereitstellungsvariable in der `.magento.env.yaml` fest: `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

Wenn Sie die `VALKEY_BACKEND` Bereitstellungsvariable auf `symfony_l2` setzen, wird automatisch die vollständige L2-Cache-Konfiguration aus Ihren Valkey-Service-Verbindungsdetails erstellt, einschließlich `default` und `stale_cache_enabled`-Frontends, wobei die gängigen Cache-Typen bereits zugeordnet sind. Die Definition von `CACHE_CONFIGURATION` ist optional und nur erforderlich, wenn Sie bestimmte Backend-Optionen anpassen möchten.

>[!NOTE]
>
>Patch von ACP2E-5132 für Adobe Commerce 2.4.9 verbessert die Leistung und Zuverlässigkeit [!DNL Symfony] L2-Cache durch Optimierung der Tag-Speicherung, Hinzufügen einer Veraltungs-Cache-Regenerierungssperre und Beheben von Problemen mit veralteten Tag-Mitgliedschaften, redundanten Remote-Schreibvorgängen und einer L1-Größenbasierten Entfernung (`cleanup_percentage`). Dadurch werden Datenträger-E/A und Backend-Last reduziert und gleichzeitig die Cache-Konsistenz verbessert. Siehe [Verbesserte Leistung und Zuverlässigkeit des Symfony L2](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability)Cache im _Adobe Commerce-Konfigurationshandbuch_.
>
>Der Patch ist im Paket [Cloud-Patches für Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches) enthalten (eine Abhängigkeit von `ece-tools`) und wird automatisch während der Bereitstellung angewendet, wenn Sie auf die neueste `ece-tools` aktualisieren. Aktualisieren Sie auf die neueste Version von `ece-tools`, um den Patch zu erhalten.

#### Anpassen der [!DNL Symfony] L2-Cache-Konfiguration

`ece-tools` leitet automatisch die Valkey-Verbindungsdetails (`server`, `port`, `database`, `serializer`, `compression_lib`, `persistent_id`) für die `default` und `stale_cache_enabled` Frontends ab. Um andere Backend-Optionen anzupassen, z. B. das lokale Cache-Verzeichnis, definieren Sie `CACHE_CONFIGURATION` mit `_merge: true` neben `VALKEY_BACKEND: symfony_l2`. Die hier definierten Werte überschreiben die entsprechenden automatisch generierten Standardwerte. Alle Optionen, die Sie weglassen, verwenden weiterhin die automatisch von `ece-tools` abgeleiteten Werte.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>Überschreiben Sie beim Definieren von `CACHE_CONFIGURATION` für `symfony_l2` nur `server` oder `port`, wenn Sie absichtlich auf einen anderen Cache-Endpunkt als den Valkey-Service Ihres Projekts verweisen. Das `ece-tools` leitet diese Werte automatisch von Ihrer Valkey-Service-Beziehung ab.
>
>Wenn Sie `server` überschreiben, muss sein Wert beim Herstellen einer Verbindung mit dem Valkey-Service des Projekts `localhost` werden. Wenn Sie einen falschen `server`- oder `port` angeben, schlägt die Bereitstellung mit einem Cache-Verbindungsfehler fehl.

### L2-Cache-Speicherdimensionierung für Adobe Commerce Cloud

Der L2-Cache nutzt ein [temporäres Dateisystem](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) als Speichermechanismus. Im Gegensatz zu spezialisierten Schlüssel-Wert-Speichern gibt es bei tmpfs keine Richtlinie zum Entfernen von Schlüsseln, sodass die Speichernutzung unbegrenzt ansteigen kann. Um eine Überlastung zu vermeiden, löscht Adobe Commerce automatisch den L2-Speicher, wenn die Nutzung einen konfigurierbaren Schwellenwert erreicht (standardmäßig 95 %). Sie können den Speicherverbrauch kontrollieren, indem Sie eine größere `/dev/shm` anfordern oder den Bereinigungsschwellenwert senken.

Passen Sie die maximale L2-Cache-Speichernutzung an Ihre Projektanforderungen an. Verwenden Sie eine der folgenden Methoden:

- Erstellen Sie ein Support-Ticket, um die Größe der `/dev/shm`-Halterung anzupassen. Für dieses Szenario empfiehlt Adobe, die `/dev/shm`-Bereitstellungsgröße auf 15 GB festzulegen.
- Passen Sie die `cleanup_percentage` Eigenschaft auf Anwendungsebene an, um die Speicherauslastung zu begrenzen und den für andere Services verfügbaren freien Speicher zu nutzen.
Sie können die Konfiguration in der Bereitstellungskonfiguration unter der Cache-Konfigurationsgruppe `cache/frontend/default/backend_options/cleanup_percentage` anpassen.

>[!NOTE]
>
>Die `cleanup_percentage` konfigurierbare Option wurde in Adobe Commerce 2.4.4 eingeführt.

Die folgenden Beispiele zeigen den Konfigurations-Code in der `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Valkey-Konfiguration]

Verwenden Sie für Commerce 2.4.9 und höher die folgende Konfiguration, um den Bereinigungsschwellenwert auf 90 % festzulegen:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Redis-Konfiguration]

Verwenden Sie für Commerce 2.4.8 und früher die folgende Konfiguration, um den Bereinigungsschwellenwert auf 90 % festzulegen:

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

>[!ENDTABS]

Die Cache-Anforderungen variieren je nach Projektkonfiguration und benutzerdefiniertem Code von Drittanbietern. Größe des L2-Cache-Speichers, damit der Cache ohne häufige Schwellenwerttreffer arbeiten kann.

Idealerweise bleibt die Speicherauslastung des L2-Cache unter dem Schwellenwert, um eine häufige Speicherbereinigung zu vermeiden.

Sie können die Speicherauslastung des L2-Cache auf jedem Knoten des Clusters überprüfen, indem Sie den folgenden CLI-Befehl ausführen und die `/dev/shm` Zeile überprüfen.

```shell
df -h /dev/shm
```

Die Nutzung variiert je nach Knoten, konvergiert jedoch zu einem ähnlichen Wert.

## Konfigurationsbeispiele

Verwenden Sie die folgenden Beispiele als Ausgangspunkt für Ihre Redis- oder Valley-Service-Konfigurationen.


### Anwendung aller Best Practice-Empfehlungen

>[!BEGINTABS]

>[!TAB Beispiel für eine Valkey-Konfiguration]

Generieren `ece-tools` `VALKEY_BACKEND: symfony_l2` die `default`- und `stale_cache_enabled`-Frontends und deren Cache-Typ-Zuordnungen. Legen Sie keine `use_stale_cache` auf der Frontend-`default` fest. Der nachstehende `CACHE_CONFIGURATION`-Block enthält nur explizite Überschreibungen der Backend-Optionen.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Beispiel für eine Redis-Konfiguration]

Verwenden Sie die folgende Konfiguration für Redis in Adobe Commerce 2.4.8 und früher:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Veralteten Cache nach Cache-Typ trennen

>[!BEGINTABS]

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [Einrichten des Valkey-Service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [Einrichten des Redis-Service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [Variablen bereitstellen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
