---
title: Valley für Standard-Cache verwenden
description: Erfahren Sie, wie Sie Valkey als Standardcache für Adobe Commerce konfigurieren. Erfahren Sie mehr über Befehlszeileneinrichtung, Konfigurationsoptionen und Validierungstechniken.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: e9f1bef9f97a0e1d738f1221758f1b9a0a238da1
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# Valley für Standard-Cache verwenden

Commerce bietet Befehlszeilenoptionen zum Konfigurieren der Valley-Seite und des Standard-Caching. Obwohl Sie die Zwischenspeicherung durch Bearbeiten der `<Commerce-install-dir>app/etc/env.php` konfigurieren können, ist die Verwendung der Befehlszeile die empfohlene Methode, insbesondere für anfängliche Konfigurationen. Die Befehlszeile stellt eine Validierung bereit, um sicherzustellen, dass die Konfiguration syntaktisch korrekt ist.

Sie müssen [Valkey](config-redis.md#install-redis) installieren, bevor Sie fortfahren.

## Valley-Standardzwischenspeicherung konfigurieren

Führen Sie den Befehl `setup:config:set` aus und geben Sie Parameter für das Valkey-Standardcaching an.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` aktiviert die standardmäßige Zwischenspeicherung von VALkey. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--cache-backend-valkey-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das standardmäßige Caching konfigurieren:

>[!NOTE]
>
>Ab **Adobe Commerce 2.4.9-alpha2** hat **Valkey** Redis im CLI-Tool aufgrund von Änderungen in der Lizenzierung offiziell ersetzt. Valkey ist eine Abspaltung von Redis und verfügt über nahezu identische Funktionen. Für **Versionen 2.4.8 und früher** bleiben die zur Konfiguration von Valkey verwendeten CLI-Befehle die gleichen wie für Redis, wodurch eine nahtlose Abwärtskompatibilität gewährleistet und die Migration oder Unterstützung von zwei Umgebungen vereinfacht wird. Das folgende Beispiel zeigt den valley-spezifischen Befehl.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert `127.0.0.1` bedeutet, dass Valkey auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `cache-backend-valkey-port` | Port | Lauschender Port des Valley-Servers | `6379` |
| `cache-backend-valkey-db` | Datenbank | Erforderlich, wenn Sie Valley sowohl für den Standard- als auch für den Vollseiten-Cache verwenden. Sie müssen die Datenbanknummer eines der Caches angeben; der andere Cache verwendet standardmäßig `0`.<br><br>**Wichtig**: Wenn Sie Valkey für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Adobe empfiehlt, `0` die standardmäßige Caching-Datenbanknummer, `1` die Seitencaching-Datenbanknummer und `2` die Sitzungsspeicher-Datenbanknummer zuzuweisen. | `0` |
| `cache-backend-valkey-password` | Passwort | Die Konfiguration eines Valley-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Das Kennwort wird direkt in der Konfigurationsdatei von Valkey konfiguriert: `/etc/valkey/valkey.conf` | |

### Beispielbefehl

Das folgende Beispiel aktiviert die Valkey-Standardzwischenspeicherung, legt den Host auf `127.0.0.1` fest und weist die Datenbanknummer `0` zu. Valley verwendet Standardwerte für alle anderen Parameter.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>Ab **Adobe Commerce 2.4.9-alpha2** hat **Valkey** Redis im CLI-Tool aufgrund von Änderungen in der Lizenzierung offiziell ersetzt. Valkey ist eine Abspaltung von Redis und verfügt über nahezu identische Funktionen. Für **Versionen 2.4.8 und früher** bleiben die zur Konfiguration von Valkey verwendeten CLI-Befehle die gleichen wie für Redis, wodurch eine nahtlose Abwärtskompatibilität gewährleistet und die Migration oder Unterstützung von zwei Umgebungen vereinfacht wird. Das folgende Beispiel zeigt den valley-spezifischen Befehl.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurieren der Seitenzwischenspeicherung

Um das Caching von Valkey-Seiten auf Commerce zu konfigurieren, führen Sie den Befehl `setup:config:set` mit zusätzlichen Parametern aus.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Mit den folgenden Parametern:

- `--page-cache=valkey` aktiviert das Caching von Valkey-Seiten. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--page-cache-valkey-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das Caching von Seiten konfigurieren:

>[!NOTE]
>
>Ab **Adobe Commerce 2.4.9-alpha2** hat **Valkey** Redis im CLI-Tool aufgrund von Änderungen in der Lizenzierung offiziell ersetzt. Valkey ist eine Abspaltung von Redis und verfügt über nahezu identische Funktionen. Für **Versionen 2.4.8 und früher** bleiben die zur Konfiguration von Valkey verwendeten CLI-Befehle die gleichen wie für Redis, wodurch eine nahtlose Abwärtskompatibilität gewährleistet und die Migration oder Unterstützung von zwei Umgebungen vereinfacht wird. Das folgende Beispiel zeigt den valley-spezifischen Befehl.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert `127.0.0.1` bedeutet, dass Valkey auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `page-cache-valkey-port` | Port | Lauschender Port des Valley-Servers | `6379` |
| `page-cache-valkey-db` | Datenbank | Erforderlich, wenn Sie Valley sowohl für den Standard- als auch für den Vollseiten-Cache verwenden. Sie müssen die Datenbanknummer eines der Caches angeben; der andere Cache verwendet standardmäßig `0`.<br/>**Wichtig**: Wenn Sie Valkey für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, `0` die standardmäßige Caching-Datenbanknummer, `1` die Seitencaching-Datenbanknummer und `2` die Sitzungsspeicher-Datenbanknummer zuzuweisen. | `0` |
| `page-cache-valkey-password` | Passwort | Die Konfiguration eines Valley-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Konfigurieren Sie das Kennwort in der Valkey-Konfigurationsdatei: `/etc/valkey/valkey.conf` | |

### Beispielbefehl

Das folgende Beispiel aktiviert das Caching von Valkey-Seiten, legt den Host auf `127.0.0.1` fest und weist `1` die Datenbanknummer zu. Alle anderen Parameter sind auf den Standardwert eingestellt.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>Ab **Adobe Commerce 2.4.9-alpha2** hat **Valkey** Redis im CLI-Tool aufgrund von Änderungen in der Lizenzierung offiziell ersetzt. Valkey ist eine Abspaltung von Redis und verfügt über nahezu identische Funktionen. Für **Versionen 2.4.8 und früher** bleiben die zur Konfiguration von Valkey verwendeten CLI-Befehle die gleichen wie für Redis, wodurch eine nahtlose Abwärtskompatibilität gewährleistet und die Migration oder Unterstützung von zwei Umgebungen vereinfacht wird. Das folgende Beispiel zeigt den valley-spezifischen Befehl.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## Ergebnisse

Als Ergebnis der beiden Beispielbefehle fügt Commerce Zeilen ähnlich den folgenden zu `<Commerce-install-dir>app/etc/env.php` hinzu:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Neue Valley-Cache-Implementierung

[!BADGE 2.4.9-alpha]{type=Negative tooltip="Nur in 2.4.9-Alpha verfügbar."}

Ab Adobe Commerce 2.4.9 empfiehlt Adobe die Verwendung der Valkey-Cache-Implementierung: `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Talvoreinstellung

Da Commerce Konfigurationsdaten im Valley-Cache speichert, können Sie Daten vorab laden, die zwischen Seiten wiederverwendet werden. Um Schlüssel zu finden, die vorgeladen werden müssen, analysieren Sie Daten, die von Valkey an Commerce übertragen werden. Adobe empfiehlt, Daten vorab zu laden, die auf jeder Seite geladen werden, z. B. `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` und `DB_IS_UP_TO_DATE`.

Valkey verwendet die `pipeline` zum Zusammensetzen von Ladeanfragen. Schlüssel sollten das Datenbankpräfix enthalten. Wenn beispielsweise das Datenbankpräfix `061_` ist, sieht der Vorabladeschlüssel wie folgt aus: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

Bei Verwendung der Vorabladefunktion mit einem L2-Cache müssen Sie den Schlüsseln das `:hash` Suffix hinzufügen. Der L2-Cache überträgt nur den Hash der Daten, nicht die tatsächlichen Daten.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallelerzeugung

Seit der Commerce-Version 2.4.0 bietet Adobe die `allow_parallel_generation` Option für Benutzer, die das Warten auf Sperren verhindern möchten.
Sie ist standardmäßig deaktiviert, und Adobe empfiehlt, sie zu deaktivieren, bis Sie übermäßige Konfigurationen und/oder Blockierungen haben.

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
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Valley-Verbindung überprüfen

Um sicherzustellen, dass Valkey und Commerce ordnungsgemäß zusammenarbeiten, melden Sie sich bei dem Server an, auf dem Valkey ausgeführt wird, öffnen Sie ein Terminal und verwenden Sie entweder den Befehl `valkey-cli monitor` oder den Befehl `redis-cli ping`.

### Valley-Überwachungsbefehl

```bash
valkey-cli monitor
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

### Valley-Ping-Befehl

```bash
valkey-cli ping
```

Die erwartete Antwort lautet: `PONG`

Wenn beide Befehle erfolgreich waren, ist Valkey richtig eingerichtet.

### Überprüfen komprimierter Daten

Um komprimierte Sitzungsdaten und den Seitencache zu überprüfen, unterstützt [RESP.app](https://flathub.org/apps/app.resp.RESP) die automatische Dekomprimierung von Commerce 2-Sitzungs- und Seitencache und zeigt PHP-Sitzungsdaten in einem für Menschen lesbaren Format an.
