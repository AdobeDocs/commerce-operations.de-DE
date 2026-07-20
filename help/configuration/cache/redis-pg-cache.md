---
title: Konfigurieren von Redis für Standard- und Seitencache
description: Erfahren Sie, wie Sie Redis als Standard- und Seiten-Cache-Backend für Adobe Commerce konfigurieren. Entdecken Sie CLI-Befehle, env.php-Einstellungen und die Verbindungsüberprüfung.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ec95c99d060f3c45095236d41729648abf389dd1
workflow-type: tm+mt
source-wordcount: 1411
ht-degree: 0%

---

# Konfigurieren von Redis für Standard- und Seiten-Cache

{{cloud-cache-config}}

Commerce bietet Befehlszeilenoptionen zum Konfigurieren der Redis-Seite und des Standard-Caching. Obwohl Sie die Zwischenspeicherung durch Bearbeiten der `<Commerce-install-dir>app/etc/env.php` konfigurieren können, ist die Verwendung der Befehlszeile die empfohlene Methode, insbesondere für anfängliche Konfigurationen. Die Befehlszeile stellt eine Validierung bereit, um sicherzustellen, dass die Konfiguration syntaktisch korrekt ist.

**Voraussetzung:**

[Installieren Sie Redis](config-redis.md#install-redis) bevor Sie fortfahren.

>[!NOTE]
>
>Bei auf EC2 gehosteten Commerce-Instanzen können Sie AWS ElastiCache anstelle einer lokalen Redis-Instanz verwenden. Siehe [Konfigurieren von Elasticache für EC2-Instanzen](redis-elasticache-for-ec2.md).

## Redis-Cache-Implementierungen

Adobe Commerce hat die folgenden Redis-Cache-Backend-Implementierungen verwendet:

- **Legacy Redis Backend** (`Cm_Cache_Backend_Redis`) - Veraltete Implementierung in älteren Redis-Konfigurationen.
- **Redis Backend** (`Magento\Framework\Cache\Backend\Redis`) - Backend, das von der Befehlszeilenkonfiguration in diesem Thema für den Standard- und Seiten-Cache verwendet wird.
- **L2 Cache Backend** (`Magento\Framework\Cache\Backend\RemoteSynchronizedCache`) - Zwei-Ebenen-Cache-Implementierung, die Redis als Remote-Backend und lokalen Datei-Cache-Speicher verwendet, um Cache-Daten über Knoten hinweg zu synchronisieren. Siehe [Zwei-Ebenen-Cache-Konfiguration](level-two-cache.md).

## Konfigurieren des Redis-Standardcachings

Führen Sie den `setup:config:set` Befehl aus und geben Sie Parameter an, die spezifisch für das Redis-Standardcaching sind.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Zu den gebräuchlichen Parametern gehören:

- `--cache-backend=redis` aktiviert das Redis-Standard-Caching. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--cache-backend-redis-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das standardmäßige Caching konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
| --- | --- | --- | --- |
| `cache-backend-redis-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert 127.0.0.1 bedeutet, dass Redis auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `cache-backend-redis-port` | Port | Redis-Server-Listener-Port | `6379` |
| `cache-backend-redis-db` | Datenbank | Erforderlich, wenn Sie Redis sowohl für den Standard- als auch für den Vollseiten-Cache verwenden. Geben Sie die Datenbanknummer eines der Caches an; der andere Cache verwendet standardmäßig 0.<br><br>**Wichtig**: Wenn Sie Redis für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer 0, die Seitencaching-Datenbanknummer 1 und die Sitzungsspeicher-Datenbanknummer 2 zuzuweisen. | `0` |
| `cache-backend-redis-password` | Passwort | Die Konfiguration eines Redis-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Das Passwort wird direkt in der Redis-Konfigurationsdatei konfiguriert: `/etc/redis/redis.conf` | |
| `cache-backend-redis-compress-data` | compress_data | Auf `0` setzen, um die Komprimierung zu deaktivieren. | `1` |
| `cache-backend-redis-compression-lib` | compression_lib | Zu verwendende Komprimierungsbibliothek. Zu den unterstützten Werten gehören `snappy`, `lzf`, `l4z`, `zstd` und `gzip`. Leer lassen, um automatisch zu bestimmen. | |
| `cache-backend-redis-use-lua` | use_lua | Aktivieren oder deaktivieren Sie Lua-Skripte für alle Redis-Vorgänge. <br><br>**Standard: unter `0` halten.** Der Lua-Modus ist standardmäßig deaktiviert, um bekannte Leistungs-Regressionen und GraphQL-Cache-Fehler zu verhindern, die durch die gebündelte Redis-Bibliothek (1.17.x) eingeführt wurden, wenn Lua aktiviert wurde. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Aktivieren oder deaktivieren Sie Lua-Skripte für die Speicherbereinigung (den `backend_clean_cache` Cron-Auftrag). <br><br>**Standard: unter `1` halten.** Absichtlich aktiviert, um die atomare Tag-Set-Bereinigung während des GC sicherzustellen. Ohne sie kann eine Race-Bedingung auftreten, wenn der `backend_clean_cache` Cron gleichzeitig mit einem Cache-Speichervorgang ausgeführt wird, sodass Cache-Einträge ohne entsprechenden Eintrag im Cache-Tag-Index verbleiben. Dies führt dazu, dass die Tag-basierte Invalidierung im Hintergrund fehlschlägt. So kann z. B. die Aktualisierung eines Produktpreises den Produkt-Cache nicht invalidieren, sondern erfordert eine vollständige Cache-Leerung. | `1` |

### LUA-Modus

Wenn dieser Modus aktiviert ist, bündelt er mehrere Redis-Vorgänge (Cache-Schreibvorgänge, Tag-Updates, Garbage Collection) in einem einzigen atomaren Skript, das Server-seitig über `EVALSHA` ausgeführt wird. Dadurch wird verhindert, dass gleichzeitige Anfragen verschachtelt werden, z. B. indem sichergestellt wird, dass ein Cache-Eintrag und seine Tag-Zugehörigkeit zusammen geschrieben werden.

>[!WARNING]
>
>Ändern Sie die Standardwerte für `use_lua` und `use_lua_on_gc` nicht, ohne die Auswirkungen für Ihre Adobe Commerce-Version zu verstehen:
>
>- **`use_lua`**: Die Aktivierung dieser Funktion auf Adobe Commerce 2.4.7 oder 2.4.8 (Bibliothek `colinmollenhour/cache-backend-redis` 1.17.1) kann zu Cache-Beschädigungen und Problemen mit GraphQL-Cache-Fehlern führen.
>- **`use_lua_on_gc`**: Wenn Sie dies auf Adobe Commerce 2.4.8 deaktivieren, wird der atomare Schutz während der automatischen Bereinigung entfernt. Dies kann dazu führen, dass die Tag-basierte Cache-Invalidierung im Hintergrund fehlschlägt, was eine vollständige Cache-Leerung erforderlich macht, um dies wiederherzustellen.

## Beispielbefehl (Standard-Cache)

Das folgende Beispiel aktiviert die Redis-Standardzwischenspeicherung, legt den Host auf `127.0.0.1` fest und weist die Datenbanknummer auf 0 zu. Redis verwendet Standardwerte für alle anderen Parameter.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurieren des Redis-Seitencachings

Um das Caching der Redis-Seite in Commerce zu konfigurieren, führen Sie den Befehl `setup:config:set` mit zusätzlichen Parametern aus.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Zu den gebräuchlichen Parametern gehören:

- `--page-cache=redis` aktiviert das Caching von Redis-Seiten. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--page-cache-redis-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das Caching von Seiten konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
| --- | --- | --- | --- |
| `page-cache-redis-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert 127.0.0.1 bedeutet, dass Redis auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `page-cache-redis-port` | Port | Redis-Server-Listener-Port | `6379` |
| `page-cache-redis-db` | Datenbank | Erforderlich, wenn Sie Redis sowohl für den Standard- als auch für den vollständigen Seitencache verwenden. Geben Sie die Datenbanknummer eines der Caches an; der andere Cache verwendet standardmäßig 0.<br/>**Wichtig**: Wenn Sie Redis für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer 0, die Seitencaching-Datenbanknummer 1 und die Sitzungsspeicher-Datenbanknummer 2 zuzuweisen. | `0` |
| `page-cache-redis-password` | Passwort | Die Konfiguration eines Redis-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Konfigurieren Sie das Kennwort in der Redis-Konfigurationsdatei: `/etc/redis/redis.conf` | |
| `page-cache-redis-compress-data` | compress_data | Legen Sie hierfür `1` fest, um den Vollseiten-Cache zu komprimieren. Verwenden Sie `0`, um die Komprimierung zu deaktivieren. | `0` |
| `page-cache-redis-compression-lib` | compression_lib | Zu verwendende Komprimierungsbibliothek. Zu den unterstützten Werten gehören `snappy`, `lzf`, `l4z`, `zstd` und `gzip`. Leer lassen, um automatisch zu bestimmen. | |

Das folgende Beispiel aktiviert die Zwischenspeicherung der Redis-Seite, legt den Host auf `127.0.0.1` fest und weist `1` die Datenbanknummer zu. Alle anderen Parameter sind auf den Standardwert eingestellt.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Überprüfen der Commerce-Umgebungskonfiguration

Wenn Sie die Befehle zum Konfigurieren des Redis-Caching ausführen, wird die Commerce-Umgebungskonfiguration (`<Commerce-install-dir>app/etc/env.php`) aktualisiert:

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

## Konfigurieren zusätzlicher Caching-Optionen

### Vorabladefunktion neu einstellen

Da Commerce Konfigurationsdaten im Redis-Cache speichert, können Sie Daten vorab laden, die zwischen Seiten wiederverwendet werden. Um Schlüssel zu finden, die vorgeladen werden müssen, analysieren Sie Daten, die von Redis an Commerce übertragen werden. Adobe empfiehlt, Daten vorab zu laden, die auf jeder Seite geladen werden, z. B. `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` und `DB_IS_UP_TO_DATE`.

Redis verwendet die `pipeline` zum Zusammensetzen von Ladeanfragen. Schlüssel sollten das Datenbankpräfix enthalten. Wenn das Datenbankpräfix beispielsweise `061_` ist, sieht der Vorabladeschlüssel wie folgt aus: `061_SYSTEM_DEFAULT`

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

Bei Verwendung der Vorabladefunktion mit einem L2-Cache müssen Sie den Schlüsseln das `:hash` Suffix hinzufügen. Der L2-Cache überträgt nur den Hash der Daten, nicht die tatsächlichen Daten.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Parallelerzeugung

Mit der Commerce-Version 2.4.0 führte Adobe die `allow_parallel_generation`-Option für Benutzende ein, die das Warten auf Sperren verhindern möchten. Sie ist standardmäßig deaktiviert, und Adobe empfiehlt, sie zu deaktivieren, bis Sie übermäßige Konfigurationen und/oder Blockierungen haben.

**So aktivieren Sie die parallele Generierung**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

Da es sich um ein Flag handelt, können Sie es nicht mit einem Befehl deaktivieren. Legen Sie den Konfigurationswert manuell auf `false` fest:

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

## Leistungsoptimierung

Wenn Sie Symfony Cache verwenden, können Sie die Leistung weiter optimieren, indem Sie den Igbinary-Serializer konfigurieren, die igbinary PHP-Erweiterung und die phpredis-Erweiterung installieren und persistente Verbindungen aktivieren.

### Binäres Serialisierungsprogramm

Der Inbinary-Serialisierer bietet erhebliche Leistungsverbesserungen gegenüber der PHP-Standardserialisierung. Sie muss in `app/etc/env.php` manuell konfiguriert werden:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### Installieren der PHP Igbinary-Erweiterung

Um die inbinäre Serialisierung zu verwenden, müssen Sie die PHP Igbinary-Erweiterung installieren.

**Verwenden von apt (empfohlen für Debian/Ubuntu)**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**Verwendung von PECL (alternative Methode)**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### PHP Redis-Erweiterung

Verwenden Sie die native PHP Redis-Erweiterung (`phpredis`), wenn Ihre Umgebung dies unterstützt:

#### Verwenden von apt

Verwenden Sie für Debian oder Ubuntu `apt`:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

#### PECL verwenden

Verwenden Sie alternativ `pecl`:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/<version>/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Leistungsvergleich**:

| Bedienung | Predis | Phredis | Verbesserung |
|-----------|--------|----------|-------------|
| Cache-GET | 1-5 ms | 0,5 - 2 ms | 2- bis 3-mal schneller |
| Cache-SET | 2-6 ms | 0,8 - 2,5 ms | 2- bis 3-mal schneller |
| Tag-Vorgänge | 10-30 ms | 3-10 ms | 3- bis 4-mal schneller |

### Persistente Verbindungen

Persistente Verbindungen verwenden vorhandene Redis-Verbindungen anforderungsübergreifend wieder und ermöglichen so 5-15 % schnellere Cache-Vorgänge. Konfigurieren Sie in `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>Verwenden Sie einen eindeutigen `persistent_id` für jeden Cache-Typ, um Verbindungskonflikte zu vermeiden.

### Vollständige optimierte Konfiguration

Hier finden Sie eine produktionsbereite Redis-Konfiguration, die alle Leistungsoptimierungen kombiniert:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Überprüfen der Redis-Verbindung

So überprüfen Sie, ob Redis und Commerce ordnungsgemäß zusammenarbeiten:

1. Melden Sie sich bei dem Server an, auf dem Redis und Commerce ausgeführt werden.
1. Öffnen Sie ein Terminal.
1. Überprüfen Sie die Verbindung entweder mithilfe des Befehls `redis-cli monitor` oder des Befehls `redis-cli ping` .

Wenn die Befehle erfolgreich sind, wird Redis ausgeführt und kann mit der Commerce-Anwendung kommunizieren. Wenn sie fehlschlagen, gibt es ein Verbindungsproblem zwischen Redis und Commerce, das Sie beheben müssen.

### Redis-Monitorbefehl

```shell
redis-cli monitor
```

Beispielhafte Seitenzwischenspeicherungsausgabe:

```text
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
...
```

Wenn beide Befehle erfolgreich sind, wird Redis ordnungsgemäß eingerichtet.

### Überprüfen komprimierter Daten

Verwenden Sie das Tool [RESP.app](https://flathub.org/apps/details/app.resp.RESP), um komprimierte Sitzungsdaten und Seiten-Cache zu überprüfen. Es unterstützt die automatische Dekomprimierung von Commerce 2-Sitzungs- und Seiten-Cache-Daten und zeigt PHP-Sitzungsdaten in menschenlesbarer Form an.
