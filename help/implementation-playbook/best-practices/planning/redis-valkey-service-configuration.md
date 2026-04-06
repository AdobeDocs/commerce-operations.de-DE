---
title: Best Practices für die Konfiguration von Redis und Valley Service
description: Erfahren Sie, wie Sie Redis- und Valkey-Services für Adobe Commerce konfigurieren. Verbessern Sie die Caching-Leistung mit L2-Cache, Slave-Verbindungen, veraltetem Cache und Sitzungstrennung.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: aedff83fe473691340f0f254e7c79ef7e632ac0d
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Best Practices für die Konfiguration des Redis- und Valley-Service

Verwenden Sie diese Empfehlungen, um Redis oder Valkey für das Caching und die Sitzungen von Adobe Commerce zu konfigurieren.

- L2-Cache konfigurieren
- Slave-Verbindung aktivieren
- Schlüssel vorausfüllen
- Veralteten Cache aktivieren
- Cache und Sitzung trennen
- Komprimieren des Cache
- Konfigurationsbeispiele

>[!NOTE]
>
>Stellen Sie bei Commerce in Cloud-Infrastrukturumgebungen sicher, dass Sie die neueste Version des `ece-tools` verwenden. Falls nicht, [aktualisieren Sie auf die neueste Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Sie können die in Ihrer lokalen Umgebung installierte Version mithilfe des `composer show magento/ece-tools` CLI-Befehls überprüfen.

## L2-Cache konfigurieren

Konfigurieren Sie den L2-Cache, indem Sie die Bereitstellungsvariable `REDIS_BACKEND` oder `VALKEY_BACKEND` in der Konfigurationsdatei `.magento.env.yaml` festlegen.

>[!BEGINTABS]

>[!TAB Redis-Konfiguration]

Verwenden Sie für Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Informationen zur Umgebungskonfiguration in der Cloud-Infrastruktur finden Sie in [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) Konfigurationsreferenz im Handbuch _Commerce in der Cloud-Infrastruktur_.

Bei On-Premise-Installationen finden Sie weitere Informationen unter [Konfigurieren des Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)Seitencachings im _Konfigurationshandbuch_.

>[!TAB Valkey-Konfiguration]

Verwenden Sie für Valley Folgendes:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Informationen zur Umgebungskonfiguration in der Cloud-Infrastruktur finden Sie in [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) Konfigurationsreferenz im Handbuch _Commerce in der Cloud-Infrastruktur_.

Informationen zu On-Premise-Installationen finden Sie unter [Valkey konfigurieren](../../../configuration/cache/config-valkey.md) im _Konfigurationshandbuch_.

>[!ENDTABS]


### L2-Cache-Speicherdimensionierung für Adobe Commerce Cloud

Der L2-Cache nutzt ein [temporäres Dateisystem](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) als Speichermechanismus. Im Gegensatz zu spezialisierten Schlüssel-Wert-Speichern gibt es bei tmpfs keine Richtlinie zum Entfernen von Schlüsseln, sodass die Speichernutzung unbegrenzt ansteigen kann. Um eine Überlastung zu vermeiden, löscht Adobe Commerce automatisch den L2-Speicher, wenn die Nutzung einen konfigurierbaren Schwellenwert erreicht (standardmäßig 95 %). Sie können den Speicherverbrauch kontrollieren, indem Sie eine größere `/dev/shm` anfordern oder den Bereinigungsschwellenwert senken.

Passen Sie die maximale L2-Cache-Speichernutzung an Ihre Projektanforderungen an. Verwenden Sie eine der folgenden Methoden:

- Erstellen Sie ein Support-Ticket, um die Größe der `/dev/shm`-Bereitstellung anzupassen. Für dieses Szenario empfiehlt Adobe, die `/dev/shm`-Bereitstellungsgröße auf 15 GB festzulegen.
- Passen Sie die `cleanup_percentage` Eigenschaft auf Anwendungsebene an, um die Speicherauslastung zu begrenzen und den für andere Services verfügbaren freien Speicher zu nutzen.
Sie können die Konfiguration in der Bereitstellungskonfiguration unter der Cache-Konfigurationsgruppe `cache/frontend/default/backend_options/cleanup_percentage` anpassen.

>[!NOTE]
>
>Die `cleanup_percentage` konfigurierbare Option wurde in Adobe Commerce 2.4.4 eingeführt.

Die folgenden Beispiele zeigen den Konfigurations-Code in der `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Redis-Konfiguration]

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

>[!TAB Valkey-Konfiguration]

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

>[!ENDTABS]

Die Cache-Anforderungen variieren je nach Projektkonfiguration und benutzerdefiniertem Code von Drittanbietern. Größe des L2-Cache-Speichers, damit der Cache ohne häufige Schwellenwerttreffer arbeiten kann.

Idealerweise bleibt die Speicherauslastung des L2-Cache unter dem Schwellenwert, um eine häufige Speicherbereinigung zu vermeiden.

Sie können die Speicherauslastung des L2-Cache auf jedem Knoten des Clusters überprüfen, indem Sie den folgenden CLI-Befehl ausführen und die `/dev/shm` Zeile überprüfen.

```bash
df -h /dev/shm
```

Die Nutzung kann von Knoten zu Knoten variieren, sollte aber auf einen ähnlichen Wert konvergieren.

## Benutzerdefinierte Ordner für den L2-Cache konfigurieren

Bei der Optimierung der L2-Cache-Leistung können Sie die lokalen Cache-Dateien in einem benutzerdefinierten Hochleistungsverzeichnis speichern, z. B. auf einer RAM-Festplatte (`/dev/shm/`).

Um anwendungsweite Konsistenz zu gewährleisten und fragmentierten Cache-Speicher zu verhindern, konfigurieren Sie sowohl die spezifischen L2-Backend-Optionen als auch die globale Verzeichnisregistrierung in der `app/etc/env.php`.

**Best Practice:** Definieren Sie sowohl `local_backend_options['cache_dir']` als auch die globale `directories['cache']['path']`.

- **`local_backend_options['cache_dir']`**: Leitet den Backend-Cache-Adapter (z. B. `Cm_Cache_Backend_File`) an, seine synchronisierten L2-Cache-Dateien am angegebenen Speicherort zu speichern.
- **`directories['cache']['path']`**: Aktualisiert die Adobe Commerce `DirectoryList`-Registrierung und legt den benutzerdefinierten Pfad als endgültiges System-Cache-Verzeichnis für die gesamte Anwendung fest.

### Vermeiden von Split-Cache-Verzeichnissen und GlusterFS-Segmentierungsfehlern

Wenn Sie den benutzerdefinierten Pfad ausschließlich im `local_backend_options` definieren, funktioniert die L2-Cache-Engine ordnungsgemäß, aber die globale Anwendungsregistrierung erkennt `var/cache` weiterhin als standardmäßigen Cache-Speicherort.

Diese Konfigurationsabweichung führt zu einem „Split-Brain“-Szenario, in dem Drittanbietererweiterungen oder zentrale Ausweichprozesse temporäre Dateien in das standardmäßige `var/cache` schreiben.

**Kritische Auswirkungen auf Adobe Commerce Cloud:** Auf Pro-Architekturen wird das `var/`-Verzeichnis in einem freigegebenen verteilten Dateisystem gemountet. Das Erzwingen von Cache-E/A mit hoher Geschwindigkeit über diese Netzwerkbereitstellung überfordert den Client und ist ein primärer Trigger für **GlusterFS-Segmentierungsfehler und Cluster-weite Ausfälle**. Durch die Konfiguration beider Einstellungen wird sichergestellt, dass alle Cache-E/A-Vorgänge streng auf der lokalen, leistungsstarken Festplatte bleiben.

### Konfigurationsbeispiel

Um ein einzelnes, einheitliches Cache-Verzeichnis zu erzwingen, aktualisieren Sie Ihre `env.php`-Datei, um beide Konfigurationen einzuschließen:

```php
return [
    // 1. Override the global directory registry
    'directories' => [
        'cache' => [
            'path' => '/dev/shm/magento_cache'
        ]
    ],
    // 2. Configure the L2 cache engine
    'cache' => [
        'frontend' => [
            'default' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'server' => '127.0.0.1',
                    'port' => '6379',
                    'database' => '1',
                    // ... other redis configurations ...
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/magento_cache' 
                    ]
                ]
            ]
        ]
    ],
    // ...
];
```

## Slave-Verbindung aktivieren

Aktivieren Sie die Slave-Verbindung in der `.magento.env.yaml`, damit Adobe Commerce eine zusätzliche schreibgeschützte Cache-Verbindung für Lesevorgänge verwenden kann, während der primäre Endpunkt weiterhin für Schreibvorgänge verwendet wird. Durch diese Konfiguration kann die Leselast auf dem primären Cache-Service reduziert und der Lesetraffic effektiver verteilt werden.

>[!BEGINTABS]

>[!TAB Redis-Konfiguration]

Verwenden Sie für Redis:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Informationen zur Umgebungskonfiguration für die Commerce Cloud-Infrastruktur finden Sie unter [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) im _Handbuch für Commerce in Cloud-Infrastruktur_.

Konfigurieren Sie bei lokalen Adobe Commerce-Installationen die neue Redis-Cache-Implementierung mithilfe der `bin/magento setup`. Siehe [Verwenden von Redis für den ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)-Cache) im _Konfigurationshandbuch_.

>[!TAB Valkey-Konfiguration]

Verwenden Sie für Valley Folgendes:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Informationen zur Umgebungskonfiguration für die Commerce Cloud-Infrastruktur finden Sie unter [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) im _Handbuch für Commerce in Cloud-Infrastruktur_.

Konfigurieren Sie bei lokalen Adobe Commerce-Installationen die neue Valkey-Cache-Implementierung mithilfe der `bin/magento setup`. Siehe [Konfigurieren von Valkey](../../../configuration/cache/config-valkey.md) im _Konfigurationshandbuch_.

>[!ENDTABS]

## Schlüssel vorausfüllen

Magento lädt normalerweise Cache-Einträge aus Redis oder Valkey einzeln. Mit der Vorabladefunktion können Sie eine Liste häufig verwendeter Schlüssel bereitstellen, die Magento bei dem ersten Zugriff während einer Anfrage in einer einzigen Pipeline abruft. Magento speichert die abgerufenen Werte dann für den Rest der Anfrage im PHP-Speicher, was die wiederholten Roundtrips zu Redis oder Valkey reduziert und die Bootstrap-Performance der Anfragen für diese Schlüssel verbessern kann.

Häufig verwendete Tasten können durch die Überwachung aktiver Befehle auf Redis oder Valley identifiziert werden:

>[!BEGINTABS]

>[!TAB Konfiguration des Preload-Schlüssels für Redis]

Die Vorabladeschlüssel werden in der `.magento.env.yaml`-Konfigurationsdatei konfiguriert.

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

Drücken Sie nach 10 Sekunden **[!UICONTROL Ctrl+C]**. Führen Sie dann den folgenden Befehl aus:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In diesem Protokoll werden die Schlüssel aufgelistet, die Sie vorab laden können. Um den Inhalt eines Schlüssels anzuzeigen, führen Sie den folgenden Befehl aus:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

Bei On-Premise-Installationen finden Sie weitere Informationen unter [Redis-Vorabladefunktion](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) im _Konfigurationshandbuch_.

>[!TAB Konfiguration des Valkey-Vorabladeschlüssels]

Die Vorabladeschlüssel werden in der `.magento.env.yaml`-Konfigurationsdatei konfiguriert.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Drücken Sie nach 10 Sekunden **[!UICONTROL Ctrl+C]**. Führen Sie dann den folgenden Befehl aus:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In diesem Protokoll werden die Schlüssel aufgelistet, die Sie vorab laden können. Um den Inhalt eines Schlüssels anzuzeigen, führen Sie den folgenden Befehl aus:

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

Informationen zu lokalen Installationen finden Sie unter [Valkey-Vorabladefunktion](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) im _Konfigurationshandbuch_.

>[!ENDTABS]

## Veralteten Cache aktivieren

Veralteter Cache ist eine L2-Cache-Funktion von `RemoteSynchronizedCache`. Wenn diese Option aktiviert ist, kann Adobe Commerce einen vorhandenen lokalen Cache-Wert aus `/dev/shm` bereitstellen, während eine andere Anfrage bereits denselben Eintrag neu generiert, anstatt jede gleichzeitige Anfrage warten zu lassen. Dadurch werden Cache-Stampedes und Sperrkonflikte bei der Neuerstellung teurer Cache-Einträge reduziert.

### Funktionsweise

Mit `RemoteSynchronizedCache` verwaltet Magento zwei Kopien jedes Cache-Eintrags: eine lokale Kopie in `/dev/shm` und eine Remote-Kopie in Redis oder Valkey. Wenn die Remote Copy nicht verfügbar ist und bereits eine Regenerierungssperre für diesen Schlüssel vorhanden ist, können gleichzeitige -Anfragen den vorherigen lokalen Wert empfangen, anstatt zu warten, bis der neue Wert geschrieben wird.

Um den veralteten Cache zu aktivieren, konfigurieren Sie ihn in der `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Veralteten Cache für Redis konfigurieren]

Für Redis:

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

>[!TAB Konfigurieren des veralteten Cache für Valkey]

Für Valley:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>Der `full_page`-Cache-Typ ist für Adobe Commerce in Cloud-Infrastrukturprojekten nicht relevant, da sie &quot;[&quot; ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly).

Informationen zu On-Premise-Installationen finden Sie unter [Veraltete Cache](../../../configuration/cache/level-two-cache.md#stale-cache-options) im _Konfigurationshandbuch_.

>[!WARNING]
>
>Die obige Konfiguration ermöglicht veralteten Cache im Frontend für den `default`-Cache, das veraltetes Cache-Verhalten auf alle Cache-Einträge anwendet, die dieses Frontend verwenden. Magento Core-Cache-Typen funktionieren in der Regel mit dieser Einstellung wie erwartet. Wenn Ihr Projekt jedoch benutzerdefinierten Code oder Erweiterungen enthält, die über die generische `\Magento\Framework\App\Cache`-API (z. B. `$this->cache->save()`) ohne dediziertes Cache-Frontend in den Cache schreiben, können diese Einträge während der Regenerierung auch veraltete Werte liefern.
>
>
>Wenn dies zu unerwartetem Verhalten in Ihren Anpassungen führt, lassen Sie den veralteten Cache im `default`-Frontend deaktiviert und aktivieren Sie ihn nur für ausgewählte Cache-Typen, wie es häufig [lokal) ](../../../configuration/cache/level-two-cache.md#stale-cache-options).

### Veralteter Cache pro Cache-Typ einzeln aktivieren

Sie können veralteten Cache nur für ausgewählte Cache-Typen aktivieren, indem Sie ein dediziertes Cache-Frontend in `.magento.env.yaml` definieren und die ausgewählten Cache-Typen ihm zuordnen.

Um ordnungsgemäß zu funktionieren, muss das benutzerdefinierte Frontend als vollständiges Frontend unter `CACHE_CONFIGURATION.frontend` definiert werden. Es reicht nicht aus, nur `use_stale_cache: true` für einen neuen Frontend-Namen zu definieren.

**Beispielkonfigurationen**

>[!BEGINTABS]

>[!TAB Veralteten Cache für Redis konfigurieren]

Für Redis:

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

>[!TAB Konfigurieren des veralteten Cache für Valkey]

Für Valley:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

>[!ENDTABS]

>[!NOTE]
>
>Wenn das Quell-Frontend mit zusätzlichen Backend-Optionen wie Komprimierung, erneuten Versuchen, Vorabladen von Schlüsseln oder anderen Optimierungswerten konfiguriert ist, kopieren Sie diese Optionen in `stale_cache_enabled`, damit das neue Frontend dasselbe Verhalten beibehält.


## Separate Cache- und Sitzungsinstanzen

Wenn Sie den Cache von den Sitzungen trennen, können Sie diese unabhängig verwalten. Es verringert Konflikte zwischen Cache- und Sitzungs-Traffic, verhindert, dass Cache-bedingter Druck sich auf Sitzungen auswirkt, und ermöglicht die Dimensionierung und Abstimmung jeder Redis- oder Valley-Instanz auf ihre eigene Arbeitslast.

Gehen Sie wie folgt vor, um eine dedizierte Instanz für Sitzungen bereitzustellen:

>[!BEGINTABS]

>[!TAB Redis]

1. Aktualisieren Sie die `.magento/services.yaml` Konfigurationsdatei.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
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

1. Fordern Sie eine neue Redis-Instanz für Sitzungen in Produktions- und Staging-Umgebungen an.

   Senden Sie ein [Adobe Commerce-Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Schließen Sie die aktualisierten `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien ein.

   Dieses Update verursacht keine Ausfallzeiten, erfordert jedoch eine Bereitstellung, um den neuen Service zu aktivieren.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie die Portnummer.

   ```bash
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

1. Entfernen Sie Sitzungen aus der [Standarddatenbank](../../../configuration/cache/redis-pg-cache.md) (`db 0`) auf der Redis-Cache-Instanz.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. Aktualisieren Sie die `.magento/services.yaml` Konfigurationsdatei.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
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
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Fordern Sie eine neue Valley-Instanz an, die Sitzungen zu Produktions- und Staging-Umgebungen gewidmet ist.

   Senden Sie ein [Adobe Commerce-Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Schließen Sie die aktualisierten `.magento/services.yaml` und `.magento.app.yaml` Konfigurationsdateien ein.

   Dieses Update verursacht keine Ausfallzeiten, erfordert jedoch eine Bereitstellung, um den neuen Service zu aktivieren.

1. Stellen Sie sicher, dass die neue Instanz ausgeführt wird, und notieren Sie die Portnummer.

   ```bash
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

1. Entfernen Sie Sitzungen aus der [Standarddatenbank](../../../configuration/cache/redis-pg-cache.md) (`db 0`) auf der Valkey-Cache-Instanz.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Cache-Komprimierung

Wenn Sie mehr als 6 GB Redis- oder Valkey-`maxmemory` verwenden, können Sie die Cache-Komprimierung aktivieren, um den von Schlüsseln belegten Speicherplatz zu reduzieren. Beachten Sie, dass diese Einstellung Client-seitige Leistung gegen Speichereinsparungen eintauscht. Wenn Sie über freie CPU-Kapazität verfügen, sollten Sie diese aktivieren. Siehe [Verwenden von Redis für ](../../../configuration/cache/redis-session.md) oder [Verwenden von Valkey für ](../../../configuration/cache/valkey-session.md) im _Konfigurationshandbuch_.

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

Um die `lazyfree` in Adobe Commerce auf der Cloud-Infrastruktur zu aktivieren, reichen Sie ein [Adobe Commerce-Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)Ticket ein, in dem Sie darum bitten, die folgende Redis- oder Valkey-Konfiguration auf Ihre Umgebungen anzuwenden:

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

Um das Redis-I/O-Threading in Adobe Commerce in der Cloud-Infrastruktur zu aktivieren, senden Sie ein [Adobe Commerce Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) mit der unten stehenden Anfrage zur I/O-Threading-Konfiguration. Diese Konfiguration kann den Durchsatz verbessern, indem Socket-Lese- und -Schreibvorgänge sowie das Parsen von Befehlen vom Haupt-Thread ausgelagert werden, was zulasten einer höheren CPU-Nutzung geht. Validieren Sie unter Last und überwachen Sie Ihre Hosts.

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

## Konfigurationsbeispiele

Verwenden Sie die folgenden Beispiele als Ausgangspunkt für Ihre Redis- oder Valley-Service-Konfigurationen.


### Anwendung aller Best Practice-Empfehlungen

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
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

>[!TAB Beispiel für eine Valkey-Konfiguration]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
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

### Wenden Sie alle Best Practice-Empfehlungen an und trennen Sie veraltete Caches nach Cache-Typ

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
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

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
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
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
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
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Weitere Informationen

Siehe die folgenden verwandten Themen:

- [Redis-Seitencache](../../../configuration/cache/redis-pg-cache.md)
- [Redis für Sitzungsspeicher verwenden](../../../configuration/cache/redis-session.md)
- [Valley für Standard-Cache verwenden](../../../configuration/cache/valkey-pg-cache.md)
- [Valley für Sitzungsspeicherung verwenden](../../../configuration/cache/valkey-session.md)
