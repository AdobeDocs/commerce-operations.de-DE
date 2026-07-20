---
title: L2-Cache-Konfiguration zur Leistungsoptimierung
description: Erfahren Sie, wie Sie den L2-Cache in Adobe Commerce konfigurieren, um den Netzwerk-Traffic zu reduzieren und die Leistung zu verbessern. Entdecken Sie die Implementierungsoptionen von Legacy und Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 5f20ef1b6e40728e38d06f5c9f90f72ba1eb43e0
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 0%

---

# L2-Cache-Konfiguration zur Leistungsoptimierung

L2-Caching (auf zwei Ebenen) reduziert den Netzwerk-Traffic zwischen dem Remote-Cache-Speicher (Redis oder Valkey) und der Commerce-Anwendung, indem eine lokale Cache-Ebene auf jedem Web-Knoten hinzugefügt wird. Eine standardmäßige Commerce-Instanz überträgt etwa 300 KB pro Anfrage, und der Traffic kann in einigen Situationen schnell auf über 1.000 Anfragen wachsen.

Beim L2-Caching speichert jeder Web-Knoten häufig aufgerufene Daten lokal und verwendet den Remote-Cache für zwei Zwecke:

- Überprüfen der Cache-Datenversion, um sicherzustellen, dass der neueste Cache lokal gespeichert wird
- Übertragen aktualisierter Cache-Daten vom Remote-Speicher auf den lokalen Computer

Commerce speichert die Hash-Datenversion im Remote-Cache, wobei das Suffix `:hash` an den regulären Schlüssel angehängt wird. Wenn der lokale Cache veraltet ist, werden die Daten über einen Cache-Adapter vom Remote-Computer abgerufen.

Es stehen zwei L2-Cache-Implementierungen zur Verfügung:

| Implementierung | Version | Beschreibung |
| -------------- | ------- | ----------- |
| [Legacy (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | 2.4.x | Zend-basierter Zwei-Ebenen-Cache mit `Cm_Cache_Backend_File` für lokalen Speicher |
| [Modern (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony Cache-basiertes L2 mit PSR-6-Konformität und verbesserter Leistung |

>[!NOTE]
>
>Konfigurieren Sie für Adobe Commerce on Cloud den L2-Cache, indem Sie die Variable [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=de#redis_backend) oder [`VALKEY_BACKEND`](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) in `.magento.env.yaml` festlegen. Konfigurationsbeispiele finden Sie [Konfigurieren des L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)Cache).

## Konfiguration des alten L2-Cache (RemoteSynchronizedCache)

Verwenden Sie das folgende Beispiel, um den vorhandenen Cache-Abschnitt in der `app/etc/env.php`-Datei zu ändern oder zu ersetzen.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

Dabei gilt:

- `backend` ist die L2-Cache-Implementierung.
- `backend_options` ist die L2-Cache-Konfiguration.
  - `remote_backend` ist die Remote-Cache-Implementierung: Redis oder MySQL.
  - `remote_backend_options` ist die Remote-Cache-Konfiguration.
  - `local_backend` ist die lokale Cache-Implementierung: `Cm_Cache_Backend_File`
  - `local_backend_options` ist die lokale Cache-Konfiguration.
  - `cache_dir` ist eine Datei-Cache-spezifische Option für das Verzeichnis, in dem der lokale Cache gespeichert ist.

Adobe empfiehlt die Verwendung von Redis für das Remote-Caching (`\Magento\Framework\Cache\Backend\Redis`) und `Cm_Cache_Backend_File` für das lokale Caching von Daten im gemeinsamen Speicher mit: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe empfiehlt die Verwendung der [`cache preload`](redis-pg-cache.md#redis-preload-feature)-Funktion, da sie den Druck auf Redis drastisch verringert. Vergessen Sie nicht, das Suffix &quot;:hash&quot; für Vorabladeschlüssel hinzuzufügen.

## Veraltete Cache-Optionen

Ab Commerce 2.4 kann die `use_stale_cache`-Option in bestimmten Fällen die Leistung verbessern, indem zuvor zwischengespeicherte Daten bereitgestellt werden, während in einem parallelen Prozess neue Cache-Daten generiert werden.

Im Allgemeinen ist der Kompromiss mit Sperrwartung aus Sicht der Leistung akzeptabel. Je mehr Blöcke oder Cache-Einträge vorhanden sind, desto länger dauert die Sperrwartung. In einigen Szenarien kann die Wartezeit für den Prozess bis zu **die Anzahl der Schlüssel** x **Lookup-**) betragen. In seltenen Fällen kann ein Händler Hunderte von Schlüsseln im `Block/Config`-Cache haben, sodass selbst eine kleine Zeitüberschreitung bei der Suche nach einer Sperre Sekunden kosten kann.

>[!IMPORTANT]
>
>Veralteter Cache funktioniert nur mit L2-Cache. Um sie zu aktivieren, fügen Sie `'use_stale_cache' => true` zur Konfiguration der obersten Ebene des L2-Cache-Frontends hinzu.

Adobe empfiehlt, die Option `use_stale_cache` nur für Cache-Typen zu aktivieren, die am meisten davon profitieren, darunter:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Es wird von Adobe nicht empfohlen, die Option `use_stale_cache` für den `default` Cache-Typ zu aktivieren.

Der folgende Code zeigt eine Beispielkonfiguration:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Moderne Symfony L2-Cache-Implementierung

Ab Commerce 2.4.9 können Sie die L2-Cache-basierte Implementierung von Symfony (`symfony_l2`-Backend) verwenden, die eine moderne, PSR-6-konforme Caching-Implementierung mit erheblichen Leistungsverbesserungen gegenüber herkömmlichen `RemoteSynchronizedCache` bietet.

>[!NOTE]
>
>Diese Funktion ist derzeit nur für Kunden von Adobe Commerce On Premises 2.4.9 verfügbar. Sie wird im Juli 2026 für Adobe Commerce on Cloud aktiviert.

### Vorteile des Symfony L2-Cache

- **Moderne Architektur**: Basierend auf Symfony-Cache-Komponenten (PSR-6-kompatibel)
- **Better Performance**: Native Unterstützung für Igbinary-Serialisierung, Gzip-Komprimierung und Lua-Skripte
- **Persistente Verbindungen**: Reduziert den Verbindungsaufwand für Redis oder Valkey beim Verbindungspooling
- **Schlüssel vorladen**: Unterstützt das Vorausfüllen von Cache-Schlüsseln für kritische Daten
- **Unterstützung für veralteten Cache**: Vollständige Kompatibilität mit der `use_stale_cache` Option
- **Vereinfachte Konfiguration**: Cleaner Backend-Typnamen (`redis`, `valkey`, `file`)

### Konfigurationsbeispiel mit Symfony L2-Cache

Verwenden Sie den vereinfachten `symfony_l2`-Backend-Typ für den L2-Cache:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Redis with Symfony Cache
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Symfony L2-Cache mit veraltetem Cache

Konfigurieren von separaten Frontends für die Unterstützung veralteter Caches:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Backend-Optionen für Symfony L2-Cache

| Option | Typ | Standard | Beschreibung |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | Zeichenfolge | `'redis'` | Remote-Backend-Typ: `redis`, `valkey` oder `file` |
| `remote_backend_options` | Array | `[]` | Konfiguration des Remote-Backends (siehe die Redis/Valley-Dokumentation) |
| `local_backend` | Zeichenfolge | `'file'` | Lokaler Backend-Typ: `file` oder `apcu` |
| `local_backend_options` | Array | `[]` | Lokale Backend-Konfiguration |
| `cleanup_percentage` | Ganzzahl | `90` | Schwellenwert für die L1-Cache-Bereinigung (1-100) |
| `use_stale_cache` | Boolesch | `false` | Veralteten Cache für hohe Verfügbarkeit aktivieren |

### Talstütze

Das `symfony_l2`-Backend unterstützt auch Valkey als Remote-Backend:

```php
'backend_options' => [
    'remote_backend' => 'valkey',  // Use Valkey instead of Redis
    'remote_backend_options' => [
        'server' => 'localhost',
        'database' => '0',
        'port' => '6379',
        'serializer' => 'igbinary',
        'compression_lib' => 'gzip',
    ],
    // ... rest of configuration
]
```

Detaillierte Konfigurationsoptionen finden Sie unter:
- [Redis-Cache-Konfiguration mit Symfony Cache](redis-pg-cache.md)
- [Valley-Cache-Konfiguration mit Symfony Cache](valkey-pg-cache.md)
