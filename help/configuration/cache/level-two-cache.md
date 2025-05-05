---
title: L2-Cache-Konfiguration
description: Erfahren Sie, wie Sie den L2-Cache konfigurieren.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# L2-Cache-Konfiguration

Die Zwischenspeicherung ermöglicht eine Verringerung des Netzwerk-Traffics zwischen dem Remote-Cache-Speicher und der Commerce-Anwendung. Eine standardmäßige Commerce-Instanz überträgt etwa 300 KB pro Anfrage, und der Traffic kann in einigen Situationen schnell auf über ~1.000 Anfragen wachsen.

Um die Netzwerkbandbreite von Redis zu reduzieren, speichern Sie die Cache-Daten lokal auf jedem Web-Knoten und verwenden Sie den Remote-Cache für zwei Zwecke:

- Überprüfen Sie die Version der Cache-Daten und stellen Sie sicher, dass der neueste Cache lokal gespeichert wird
- Neuesten Cache vom Remote-Computer auf den lokalen Computer übertragen

Commerce speichert die Hash-Datenversion in Redis, wobei das Suffix &quot;:hash“ an den regulären Schlüssel angehängt wird. Wenn ein veralteter lokaler Cache vorhanden ist, werden die Daten mit einem Cache-Adapter auf den lokalen Computer übertragen.

>[!INFO]
>
>Für Adobe Commerce in Cloud-Infrastrukturen können Sie [Variablen bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=de#redis_backend) für die L2-Cache-Konfiguration verwenden.

## Konfigurationsbeispiel

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

Adobe empfiehlt die Verwendung der [`cache preload`](redis-pg-cache.md#redis-preload-feature)-Funktion, da sie den Druck auf Redis drastisch verringert. Vergessen Sie nicht, das Suffix &quot;:hash“ für Preload-Schlüssel hinzuzufügen.

## Veraltete Cache-Optionen

Ab [!DNL Commerce] 2.4 kann die `use_stale_cache` in bestimmten Fällen die Leistung verbessern.

Im Allgemeinen ist der Kompromiss mit dem Warten auf Sperren von der Leistungsseite aus akzeptabel, aber je mehr Sperren oder Cache der Händler hat, desto mehr Zeit wird damit verbracht, auf Sperren zu warten. In einigen Szenarien können Sie eine **Anzahl von Schlüsseln** \* **Lookup-Timeout** für den Prozess warten. In einigen seltenen Fällen kann der Händler Hunderte von Schlüsseln im `Block/Config`-Cache haben, sodass selbst ein kleines Lookup-Timeout für eine Sperre Sekunden kosten kann.

Veralteter Cache funktioniert nur mit einem L2-Cache. Mit einem veralteten Cache können Sie einen veralteten Cache senden, während ein neuer in einem parallelen Prozess generiert wird. Um veralteten Cache zu aktivieren, fügen Sie `'use_stale_cache' => true` zur oberen Konfiguration des L2-Cache hinzu.

Adobe empfiehlt, die Option `use_stale_cache` nur für Cache-Typen zu aktivieren, die am meisten davon profitieren, einschließlich:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Beim Adobe wird nicht empfohlen, die Option `use_stale_cache` für den `default` Cache-Typ zu aktivieren.

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
