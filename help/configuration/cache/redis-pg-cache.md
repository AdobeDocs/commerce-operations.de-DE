---
title: Redis für Standard-Cache verwenden
description: Erfahren Sie, wie Sie Redis als Standard-Cache für Adobe Commerce konfigurieren. Erfahren Sie mehr über Befehlszeileneinrichtung, Konfigurationsoptionen und Validierungstechniken.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---

# Redis für Standard-Cache verwenden

Commerce bietet Befehlszeilenoptionen zum Konfigurieren der Redis-Seite und des Standard-Caching. Obwohl Sie die Zwischenspeicherung durch Bearbeiten der `<Commerce-install-dir>app/etc/env.php` konfigurieren können, ist die Verwendung der Befehlszeile die empfohlene Methode, insbesondere für anfängliche Konfigurationen. Die Befehlszeile stellt eine Validierung bereit, um sicherzustellen, dass die Konfiguration syntaktisch korrekt ist.

Sie müssen [Redis](config-redis.md#install-redis) installieren, bevor Sie fortfahren.

## Konfigurieren des Redis-Standardcachings

Führen Sie den `setup:config:set` Befehl aus und geben Sie Parameter an, die spezifisch für das Redis-Standardcaching sind.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Mit den folgenden Parametern:

- `--cache-backend=redis` aktiviert das Redis-Standard-Caching. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--cache-backend-redis-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das standardmäßige Caching konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert 127.0.0.1 bedeutet, dass Redis auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `cache-backend-redis-port` | Port | Redis-Server-Listener-Port | `6379` |
| `cache-backend-redis-db` | Datenbank | Erforderlich, wenn Sie Redis sowohl für den Standard- als auch für den Vollseiten-Cache verwenden. Sie müssen die Datenbanknummer eines der Caches angeben; der andere Cache verwendet standardmäßig 0.<br><br>**Wichtig**: Wenn Sie Redis für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer 0, die Seitencaching-Datenbanknummer 1 und die Sitzungsspeicher-Datenbanknummer 2 zuzuweisen. | `0` |
| `cache-backend-redis-password` | Passwort | Die Konfiguration eines Redis-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Das Passwort wird direkt in der Redis-Konfigurationsdatei konfiguriert: `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | Aktivieren oder Deaktivieren von LUA. <br><br>**LUA**: Mit Lua können wir einen Teil der Anwendungslogik in Redis ausführen, die Leistung verbessern und die Datenkonsistenz durch ihre atomare Ausführung sicherstellen. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Aktivieren oder deaktivieren Sie LUA für die Speicherbereinigung. <br><br>**LUA**: Mit Lua können wir einen Teil der Anwendungslogik in Redis ausführen, die Leistung verbessern und die Datenkonsistenz durch ihre atomare Ausführung sicherstellen. | `1` |

### Beispielbefehl

Das folgende Beispiel aktiviert die Redis-Standardzwischenspeicherung, legt den Host auf `127.0.0.1` fest und weist die Datenbanknummer auf 0 zu. Redis verwendet Standardwerte für alle anderen Parameter.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurieren des Redis-Seitencachings

Um das Caching der Redis-Seite in Commerce zu konfigurieren, führen Sie den Befehl `setup:config:set` mit zusätzlichen Parametern aus.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Mit den folgenden Parametern:

- `--page-cache=redis` aktiviert das Caching von Redis-Seiten. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--page-cache-redis-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das Caching von Seiten konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert 127.0.0.1 bedeutet, dass Redis auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `page-cache-redis-port` | Port | Redis-Server-Listener-Port | `6379` |
| `page-cache-redis-db` | Datenbank | Erforderlich, wenn Sie Redis sowohl für den Standard- als auch für den vollständigen Seitencache verwenden. Sie müssen die Datenbanknummer eines der Caches angeben; der andere Cache verwendet standardmäßig 0.<br/>**Wichtig**: Wenn Sie Redis für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer 0, die Seitencaching-Datenbanknummer 1 und die Sitzungsspeicher-Datenbanknummer 2 zuzuweisen. | `0` |
| `page-cache-redis-password` | Passwort | Die Konfiguration eines Redis-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Konfigurieren Sie das Kennwort in der Redis-Konfigurationsdatei: `/etc/redis/redis.conf` | |

### Beispielbefehl

Das folgende Beispiel aktiviert die Zwischenspeicherung der Redis-Seite, legt den Host auf `127.0.0.1` fest und weist die Datenbanknummer 1 zu. Alle anderen Parameter sind auf den Standardwert eingestellt.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Ergebnisse

Als Ergebnis der beiden Beispielbefehle fügt Commerce Zeilen ähnlich den folgenden zu `<Commerce-install-dir>app/etc/env.php` hinzu:

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
>Dieser Abschnitt funktioniert nur für Commerce-Instanzen, die auf Amazon EC2-VPCs ausgeführt werden. Dies funktioniert nicht für lokale Installationen.

### Konfigurieren eines Redis-Clusters

Nach dem [Einrichten eines Redis-Clusters auf AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/) konfigurieren Sie die EC2-Instanz für die Verwendung von ElastiCache.

1. [Erstellen Sie einen ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html)Cluster in derselben Region und in VPC der EC2-Instanz.
1. Überprüfen Sie die Verbindung.

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

### Überprüfen der Verbindung

**So überprüfen Sie, ob Commerce mit ElastiCache kommuniziert**:

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

## Vorabladefunktion neu einstellen

Da Commerce Konfigurationsdaten im Redis-Cache speichert, können wir Daten vorab laden, die zwischen Seiten wiederverwendet werden. Um Schlüssel zu finden, die vorgeladen werden müssen, analysieren Sie Daten, die von Redis an Commerce übertragen werden. Wir empfehlen, Daten, die auf jeder Seite geladen werden, wie `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` `DB_IS_UP_TO_DATE` vorab zu laden.

Redis verwendet die `pipeline`, um zusammengesetzte Ladeanfragen zu erstellen. Schlüssel sollten das Datenbankpräfix enthalten. Wenn beispielsweise das Datenbankpräfix `061_` ist, sieht der Vorabladeschlüssel wie folgt aus: `061_SYSTEM_DEFAULT`

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

Falls Sie die Vorabladefunktion mit dem L2-Cache verwenden, vergessen Sie nicht, das `:hash` Suffix zu Ihren Schlüsseln hinzuzufügen, da der L2-Cache nur den Hash der Daten überträgt, nicht die Daten selbst:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallelerzeugung

Mit Version 2.4.0 haben wir die `allow_parallel_generation` für die Benutzer eingeführt, die das Warten auf Sperren verhindern möchten.
Sie ist standardmäßig deaktiviert, und wir empfehlen, sie zu deaktivieren, bis Sie übermäßige Konfigurationen und/oder Blöcke haben.

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

## Redis-Verbindung überprüfen

Um sicherzustellen, dass Redis und Commerce zusammenarbeiten, melden Sie sich bei dem Server an, auf dem Redis ausgeführt wird, öffnen Sie ein Terminal und verwenden Sie den Befehl Redis Monitor oder den Befehl ping.

### Redis-Monitorbefehl

```bash
redis-cli monitor
```

Beispielhafte Seitenzwischenspeicherungsausgabe:

```
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

### Redigieren des Befehls

```bash
redis-cli ping
```

Die erwartete Antwort lautet: `PONG`

Wenn beide Befehle erfolgreich waren, wird Redis ordnungsgemäß eingerichtet.

### Überprüfen komprimierter Daten

Um komprimierte Sitzungsdaten und Seiten-Cache zu überprüfen, unterstützt [RESP.app](https://flathub.org/apps/details/app.resp.RESP) die automatische Dekomprimierung des Commerce 2 Sitzungs- und Seiten-Caches und zeigt PHP-Sitzungsdaten in einer für Menschen lesbaren Form an.
