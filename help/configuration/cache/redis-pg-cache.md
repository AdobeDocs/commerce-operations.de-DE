---
title: Verwenden von Redizes für den Standard-Cache
description: Erfahren Sie, wie Sie Redis als Standardcache für Adobe Commerce konfigurieren.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 0%

---

# Verwenden von Redizes für den Standard-Cache

Commerce bietet Befehlszeilenoptionen zum Konfigurieren der Seite &quot;Redis&quot;und zum standardmäßigen Caching. Obwohl Sie die Zwischenspeicherung durch Bearbeiten der Datei `<Commerce-install-dir>app/etc/env.php` konfigurieren können, ist die Verwendung der Befehlszeile die empfohlene Methode, insbesondere für erste Konfigurationen. Die Befehlszeile bietet eine Validierung, um sicherzustellen, dass die Konfiguration syntaktisch korrekt ist.

Sie müssen [Redis](config-redis.md#install-redis) installieren, bevor Sie fortfahren.

## Konfigurieren der standardmäßigen Zwischenspeicherung von Redis

Führen Sie den Befehl `setup:config:set` aus und geben Sie Parameter an, die spezifisch für die standardmäßige Zwischenspeicherung von Redis sind.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Mit den folgenden Parametern:

- `--cache-backend=redis` aktiviert die standardmäßige Zwischenspeicherung von Redis. Wenn diese Funktion bereits aktiviert wurde, lassen Sie diesen Parameter weg.

- `--cache-backend-redis-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die die standardmäßige Zwischenspeicherung konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad zu einem UNIX-Socket. Der Standardwert 127.0.0.1 zeigt an, dass Redis auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `cache-backend-redis-port` | port | Überwachungsanschluss des Redis-Servers | `6379` |
| `cache-backend-redis-db` | Datenbank | Erforderlich, wenn Sie Redis sowohl für den Standard- als auch für den Vollseitencache verwenden. Sie müssen die Datenbanknummer eines der Caches angeben. Der andere Cache verwendet standardmäßig 0.<br><br>**Wichtig**: Wenn Sie Redis für mehr als einen Typ von Zwischenspeicherung verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer auf 0, die Datenbank-Nummer für die Seitenspeicherung auf 1 und die Datenbanknummer für die Sitzungsspeicherung auf 2 zuzuweisen. | `0` |
| `cache-backend-redis-password` | password | Die Konfiguration eines Kennworts für Redis ermöglicht eine der integrierten Sicherheitsfunktionen: den Befehl `auth`, für den Clients sich für den Zugriff auf die Datenbank authentifizieren müssen. Das Kennwort wird direkt in der Konfigurationsdatei von Redis konfiguriert: `/etc/redis/redis.conf` | |

### Beispiel, Befehl

Im folgenden Beispiel wird die standardmäßige Zwischenspeicherung von Redis aktiviert, der Host auf `127.0.0.1` gesetzt und die Datenbanknummer auf 0 gesetzt. Redis verwendet Standardwerte für alle anderen Parameter.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurieren des Redis-Seiten-Caching

Um das Redis-Seiten-Caching in Commerce zu konfigurieren, führen Sie den Befehl `setup:config:set` mit zusätzlichen Parametern aus.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Mit den folgenden Parametern:

- `--page-cache=redis` aktiviert die Zwischenspeicherung von Redis-Seiten. Wenn diese Funktion bereits aktiviert wurde, lassen Sie diesen Parameter weg.

- `--page-cache-redis-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die die Zwischenspeicherung von Seiten konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad zu einem UNIX-Socket. Der Standardwert 127.0.0.1 zeigt an, dass Redis auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `page-cache-redis-port` | port | Überwachungsanschluss des Redis-Servers | `6379` |
| `page-cache-redis-db` | Datenbank | Erforderlich, wenn Sie Redis sowohl für den standardmäßigen als auch für den vollständigen Seiten-Cache verwenden. Sie müssen die Datenbanknummer eines der Caches angeben. Der andere Cache verwendet standardmäßig 0.<br/>**Wichtig**: Wenn Sie Redis für mehr als einen Typ von Zwischenspeicherung verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer auf 0, die Datenbank-Nummer für die Seitenspeicherung auf 1 und die Datenbanknummer für die Sitzungsspeicherung auf 2 zuzuweisen. | `0` |
| `page-cache-redis-password` | password | Die Konfiguration eines Kennworts für Redis ermöglicht eine der integrierten Sicherheitsfunktionen: den Befehl `auth`, für den Clients sich für den Zugriff auf die Datenbank authentifizieren müssen. Konfigurieren Sie das Kennwort in der Redis-Konfigurationsdatei: `/etc/redis/redis.conf` | |

### Beispiel, Befehl

Im folgenden Beispiel wird das Zwischenspeichern von Redis-Seiten aktiviert, der Host auf `127.0.0.1` gesetzt und die Datenbanknummer auf 1 gesetzt. Alle anderen Parameter werden auf den Standardwert gesetzt.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Ergebnisse

Aufgrund der beiden Beispielbefehle fügt Commerce Zeilen ähnlich den folgenden zu `<Commerce-install-dir>app/etc/env.php` hinzu:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Verwenden von AWS ElastiCache mit Ihrer EC2-Instanz

Ab Commerce 2.4.3 können auf Amazon EC2 gehostete Instanzen einen AWS ElastiCache anstelle einer lokalen Redis-Instanz verwenden.

>[!WARNING]
>
>Dieser Abschnitt funktioniert nur bei Commerce-Instanzen, die auf Amazon EC2 VPCs ausgeführt werden. Es funktioniert nicht für Vor-Ort-Anlagen.

### Konfigurieren eines Redis-Clusters

Nachdem Sie [ einen Redis-Cluster auf AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/) eingerichtet haben, konfigurieren Sie die EC2-Instanz für die Verwendung des ElastiCache.

1. [Erstellen Sie einen ElastiCache-Cluster](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) in derselben Region und in demselben VPC der EC2-Instanz.
1. Überprüfen Sie die Verbindung.

   - Öffnen Sie eine SSH-Verbindung zu Ihrer EC2-Instanz.
   - Installieren Sie auf der EC2-Instanz den Redis-Client:

     ```bash
     sudo apt-get install redis
     ```

   - Fügen Sie der Sicherheitsgruppe EC2 eine eingehende Regel hinzu: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Fügen Sie der Sicherheitsgruppe des ElastiCache-Clusters eine eingehende Regel hinzu: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Stellen Sie eine Verbindung zur Redis-CLI her:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Konfigurieren von Commerce für die Verwendung des Clusters

Commerce unterstützt mehrere Arten von Caching-Konfigurationen. Im Allgemeinen werden die Cachekonfigurationen zwischen Frontend und Backend aufgeteilt. Die Frontend-Zwischenspeicherung wird als `default` klassifiziert und für jeden Cache-Typ verwendet. Sie können Caches auf niedrigerer Ebene anpassen oder aufteilen, um eine bessere Leistung zu erzielen. Eine allgemeine Redis-Konfiguration trennt den Standard-Cache und den Seiten-Cache von der eigenen Redis-Datenbank (RDB).

Führen Sie `setup` -Befehle aus, um die Redis-Endpunkte anzugeben.

So konfigurieren Sie Commerce for Redis als Standard-Zwischenspeicherung:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

So konfigurieren Sie die Zwischenspeicherung von Commerce für Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

So konfigurieren Sie Commerce für die Verwendung von Redis für die Sitzungsspeicherung:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Verbindung überprüfen

**Überprüfen, ob Commerce mit ElastiCache** kommuniziert:

1. Öffnen Sie eine SSH-Verbindung zur Commerce EC2-Instanz.
1. Starten Sie den Redis-Monitor.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Öffnen Sie eine Seite in der Commerce-Benutzeroberfläche.
1. Überprüfen Sie die [Cache-Ausgabe](#verify-redis-connection) in Ihrem Terminal.

## Neue Redis-Cache-Implementierung

Ab Commerce 2.3.5 wird empfohlen, die erweiterte Redis-Cache-Implementierung zu verwenden: `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Funktion zum Vorausfüllen umkehren

Da Commerce Konfigurationsdaten im Redis-Cache speichert, können wir Daten, die zwischen Seiten wiederverwendet werden, vorab ausfüllen. Um Schlüssel zu finden, die vorgeladen werden müssen, analysieren Sie Daten, die von Redis an Commerce übertragen werden. Wir empfehlen, Daten, die auf jeder Seite geladen werden, vorab zu laden, z. B. `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis verwendet den `pipeline`, um Ladeanforderungen zusammenzufassen. Die Schlüssel sollten das Datenbankpräfix enthalten. Wenn beispielsweise das Datenbankpräfix `061_` ist, sieht der Vorladeschlüssel wie folgt aus: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Wenn Sie die Funktion zum Vorausfüllen mit dem L2-Cache verwenden, vergessen Sie nicht, den Suffix `:hash` zu Ihren Schlüsseln hinzuzufügen, da der L2-Cache nur den Hash der Daten, nicht die Daten selbst, überträgt:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallele Erzeugung

Ab Version 2.4.0 haben wir die Option `allow_parallel_generation` für Benutzer eingeführt, die auf Sperren warten möchten.
Er ist standardmäßig deaktiviert. Wir empfehlen, ihn zu deaktivieren, bis Sie über übermäßige Konfigurationen und/oder Blöcke verfügen.

**So aktivieren Sie die parallele Generierung**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Da es sich um ein Flag handelt, können Sie es nicht mit einem Befehl deaktivieren. Sie müssen den Konfigurationswert manuell auf `false` setzen:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Rediv-Verbindung überprüfen

Um sicherzustellen, dass Redis und Commerce zusammenarbeiten, melden Sie sich bei dem Server an, auf dem Redis ausgeführt wird, öffnen Sie ein Terminal und verwenden Sie den Befehl Redis Monitor oder den Ping-Befehl.

### Redis Monitor, Befehl

```bash
redis-cli monitor
```

Beispielausgabe für Seiten-Caching:

```terminal
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Redis, Ping, Befehl

```bash
redis-cli ping
```

Die erwartete Antwort lautet: `PONG`

Wenn beide Befehle erfolgreich waren, wird Redis ordnungsgemäß eingerichtet.

### Überprüfen komprimierter Daten

Um komprimierte Sitzungsdaten und Seiten-Cache zu untersuchen, unterstützt [RESP.app](https://flathub.org/apps/details/app.resp.RESP) die automatische Dekomprimierung des Commerce 2-Sitzungs- und Seiten-Caches und zeigt PHP-Sitzungsdaten in einer für Menschen lesbaren Form an.
