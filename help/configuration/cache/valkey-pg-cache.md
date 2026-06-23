---
title: Konfigurieren von Valley für Standard- und Seitencache
description: Erfahren Sie, wie Sie Valkey als Standard- und Seitencache-Backend für Adobe Commerce konfigurieren. Entdecken Sie CLI-Befehle, env.php-Einstellungen und die Verbindungsüberprüfung.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
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
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1281
ht-degree: 0%

---


# Konfigurieren von Valley für Standard- und Seitencache

Commerce bietet Befehlszeilenoptionen zum Konfigurieren der Valley-Standardeinstellungen und des Seiten-Caching. Obwohl Sie die Zwischenspeicherung durch Bearbeiten der `<Commerce-install-dir>app/etc/env.php` konfigurieren können, ist die Verwendung der Befehlszeile die empfohlene Methode, insbesondere für anfängliche Konfigurationen. Die Befehlszeile stellt eine Validierung bereit, um sicherzustellen, dass die Konfiguration syntaktisch korrekt ist.

{{cloud-cache-config}}

**Voraussetzung:**

[Installieren Sie Valkey](config-valkey.md#install-valkey) bevor Sie fortfahren.

## Unterstützte Frameworks

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 und früher)]

- **Zend Cache (2.4.8 und früher)** — Legacy Valkey Backend für Commerce 2.4.8 und früher:
   - **Legacy Valkey Backend** - Verwendet den vollständigen Klassenpfad (`Magento\Framework\Cache\Backend\Valkey`)
   - **Schlüssel vorladen** - Unterstützt das Vorabladen häufig verwendeter Cache-Schlüssel
   - **Lua-Skripte** - Lua für die Speicherbereinigung
   - **Komprimierung** - Unterstützt die Datenkomprimierung

>[!TAB Symfony-Cache (2.4.9+)]

- **Symfony Cache (2.4.9+)** - Ab Commerce 2.4.9 bietet Symfony Cache eine moderne, PSR-6-konforme Caching-Implementierung für Valkey mit erheblichen Leistungsverbesserungen:
   - **Automatische Valkey-**: Bündelt mehrere Vorgänge in einzelnen Anfragen und reduziert so die Latenz
   - **PSR-6 TagAwareAdapter** - Effiziente Tag-basierte Cache-Invalidierung mit atomischen Vorgängen
   - **Igbinary-Serialisierung** - Die binäre Serialisierung reduziert die Größe des Cache-Eintrags um 45 % und verbessert die Geschwindigkeit um 5-10 %
   - **Verbesserte persistente Verbindungen** - Stabileres Verbindungspooling mit besserer Handhabung von Gabelprozessen
   - **Optimierte Lua-Skripte** - Server-seitige Ausführung in Kombination mit Pipelining für maximale Effizienz

>[!ENDTABS]

## Valley-Standardzwischenspeicherung konfigurieren

Führen Sie den Befehl `setup:config:set` aus und geben Sie Parameter für das Valkey-Standardcaching an.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` aktiviert das Valkey-Standardcaching. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--cache-backend-valkey-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das standardmäßige Caching konfigurieren:

{{valkey-redis-cli-note}}

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert `127.0.0.1` bedeutet, dass Valkey auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `cache-backend-valkey-port` | Port | Lauschender Port des Valley-Servers | `6379` |
| `cache-backend-valkey-db` | Datenbank | Erforderlich, wenn Sie Valley sowohl für den Standard- als auch für den Vollseiten-Cache verwenden. Geben Sie die Datenbanknummer eines der Caches an; der andere Cache verwendet standardmäßig `0`.<br><br>**Wichtig**: Wenn Sie Valkey für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Adobe empfiehlt, `0` die standardmäßige Caching-Datenbanknummer, `1` die Seitencaching-Datenbanknummer und `2` die Sitzungsspeicher-Datenbanknummer zuzuweisen. | `0` |
| `cache-backend-valkey-password` | Passwort | Die Konfiguration eines Valley-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Das Kennwort wird direkt in der Konfigurationsdatei von Valkey konfiguriert: `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | Aktivieren oder Deaktivieren von LUA. <br><br>**LUA**: Mit Lua können wir einen Teil der Anwendungslogik in Valkey ausführen, die Leistung verbessern und die Datenkonsistenz durch ihre atomare Ausführung sicherstellen. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | Aktivieren oder deaktivieren Sie LUA für die Speicherbereinigung. <br><br>**LUA**: Mit Lua können wir einen Teil der Anwendungslogik in Valkey ausführen, die Leistung verbessern und die Datenkonsistenz durch ihre atomare Ausführung sicherstellen. | `1` |

## Beispielbefehl (Standard-Cache)

Das folgende Beispiel aktiviert die Valkey-Standardzwischenspeicherung, legt den Host auf `127.0.0.1` fest und weist die Datenbanknummer `0` zu. Valley verwendet Standardwerte für alle anderen Parameter.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Konfigurieren des Valley-Seitencachings

Um das Caching von Valkey-Seiten auf Commerce zu konfigurieren, führen Sie den Befehl `setup:config:set` mit zusätzlichen Parametern aus.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Mit den folgenden Parametern:

- `--page-cache=valkey` aktiviert das Caching von Valkey-Seiten. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--page-cache-valkey-<parameter>=<value>` ist eine Liste von Schlüssel-Wert-Paaren, die das Caching von Seiten konfigurieren:

| Befehlszeilenparameter | Wert | Bedeutung | Standardwert |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | Server | Vollqualifizierter Hostname, IP-Adresse oder ein absoluter Pfad zu einem UNIX-Socket. Der Standardwert `127.0.0.1` bedeutet, dass Valkey auf dem Commerce-Server installiert ist. | `127.0.0.1` |
| `page-cache-valkey-port` | Port | Lauschender Port des Valley-Servers | `6379` |
| `page-cache-valkey-db` | Datenbank | Erforderlich, wenn Sie Valley sowohl für den Standard- als auch für den Vollseiten-Cache verwenden. Geben Sie die Datenbanknummer eines der Caches an; der andere Cache verwendet standardmäßig `0`.<br/>**Wichtig**: Wenn Sie Valkey für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, `0` die standardmäßige Caching-Datenbanknummer, `1` die Seitencaching-Datenbanknummer und `2` die Sitzungsspeicher-Datenbanknummer zuzuweisen. | `0` |
| `page-cache-valkey-password` | Passwort | Die Konfiguration eines Valley-Kennworts ermöglicht eine der integrierten Sicherheitsfunktionen: den `auth`-Befehl, für den sich Clients authentifizieren müssen, um auf die Datenbank zuzugreifen. Konfigurieren Sie das Kennwort in der Valkey-Konfigurationsdatei: `/etc/valkey/valkey.conf` | |

### Beispielbefehl (Seiten-Cache)

Das folgende Beispiel aktiviert das Caching von Valkey-Seiten, legt den Host auf `127.0.0.1` fest und weist `1` die Datenbanknummer zu. Alle anderen Parameter sind auf den Standardwert eingestellt.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Überprüfen der Commerce-Umgebungskonfiguration

Wenn Sie die Befehle zum Konfigurieren des Valkey-Caching ausführen, wird die Commerce-Umgebungskonfiguration (`<Commerce-install-dir>app/etc/env.php`) aktualisiert:

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 und früher)]

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

>[!TAB Symfony-Cache (2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>Verwenden Sie ab Commerce 2.4.9 den vereinfachten Backend-Typ `'backend' => 'valkey'` anstelle des vollständigen Klassenpfads. Der Symfony-Cache wird automatisch verwendet, wenn der vereinfachte Name angegeben wird.

>[!ENDTABS]

## Konfigurieren zusätzlicher Caching-Optionen

### Talvoreinstellung

Da Commerce Konfigurationsdaten im Valley-Cache speichert, können Sie Daten vorab laden, die zwischen Seiten wiederverwendet werden. Um Schlüssel zu finden, die vorgeladen werden müssen, analysieren Sie Daten, die von Valkey an Commerce übertragen werden. Adobe empfiehlt, Daten vorab zu laden, die auf jeder Seite geladen werden, z. B. `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` und `DB_IS_UP_TO_DATE`.

Valkey verwendet die `pipeline` zum Zusammensetzen von Ladeanfragen. Schlüssel sollten das Datenbankpräfix enthalten. Wenn das Datenbankpräfix beispielsweise `061_` ist, sieht der Vorabladeschlüssel wie folgt aus: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Zend Cache]

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

>[!TAB Symfony-Cache]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
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

>[!ENDTABS]

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

>[!BEGINTABS]

>[!TAB Zend Cache]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB Symfony-Cache]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Symfony Cache-Leistungsoptimierung

Wenn Sie Symfony Cache verwenden, können Sie die Leistung weiter optimieren, indem Sie den Igbinary-Serializer konfigurieren, die igbinary PHP-Erweiterung und die phpredis-Erweiterung installieren und persistente Verbindungen aktivieren.

### Binäres Serialisierungsprogramm

Der Inbinary-Serialisierer bietet erhebliche Leistungsverbesserungen gegenüber der PHP-Standardserialisierung. Sie muss in `app/etc/env.php` manuell konfiguriert werden:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### Installieren der PHP Igbinary-Erweiterung

Um die binäre Serialisierung zu verwenden, müssen Sie die PHP Igbinary-Erweiterung installieren.

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

### PHP Redis-Erweiterungen: phpredis vs Predis

Commerce 2.4.9+ enthält einen automatischen Fallback zwischen phpredis (native C-Erweiterung) und Predis (reine PHP-Bibliothek). Installieren Sie phpredis, um eine optimale Leistung zu erzielen:

**Verwenden von apt (empfohlen für Debian/Ubuntu)**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Verwendung von PECL (alternative Methode)**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
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

Persistente Verbindungen verwenden bestehende Valkey-Verbindungen anforderungsübergreifend wieder und bieten so 5-15 % schnellere Cache-Vorgänge. Konfigurieren Sie in `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
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
                'server' => 'valkey',
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

Hier finden Sie eine produktionsbereite Konfiguration, die alle Leistungsoptimierungen kombiniert:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

## Valley-Verbindung überprüfen

So überprüfen Sie, ob Valkey und Commerce ordnungsgemäß zusammenarbeiten:

1. Melden Sie sich bei dem Server an, auf dem Valkey und Commerce ausgeführt werden.
1. Öffnen Sie ein Terminal.
1. Überprüfen Sie die Verbindung entweder mithilfe des Befehls `valkey-cli monitor` oder des Befehls `valkey-cli ping` .

Wenn die Befehle erfolgreich sind, wird Valkey ausgeführt und kann mit der Commerce-Anwendung kommunizieren. Wenn sie fehlschlagen, gibt es ein Verbindungsproblem zwischen Valkey und Commerce, das Sie beheben müssen.

### Valley-Überwachungsbefehl

```shell
valkey-cli monitor
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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Valley-Ping-Befehl

```shell
valkey-cli ping
```

Die erwartete Antwort lautet: `PONG`

Wenn beide Befehle erfolgreich waren, ist Valkey richtig eingerichtet.

### Überprüfen komprimierter Daten

Verwenden Sie das Tool [RESP.app](https://flathub.org/apps/app.resp.RESP), um komprimierte Sitzungsdaten und Seiten-Cache zu überprüfen. Es unterstützt die automatische Dekomprimierung von Commerce 2-Sitzungs- und Seiten-Cache-Daten und zeigt PHP-Sitzungsdaten in einem menschenlesbaren Format an.

