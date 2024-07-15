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

Die Zwischenspeicherung ermöglicht eine Verringerung des Netzwerk-Traffics zwischen dem Remote-Cache-Speicher und der Commerce-Anwendung. Eine standardmäßige Commerce-Instanz überträgt etwa 300 KB pro Anforderung, und der Traffic kann in einigen Fällen schnell auf über etwa 1000 Anforderungen anwachsen.

Um die Netzwerkbandbreite auf Redis zu reduzieren, speichern Sie die Cachedaten lokal auf jedem Webknoten und verwenden Sie den Remote-Cache für zwei Zwecke:

- Überprüfen Sie die Cache-Datenversion und stellen Sie sicher, dass der aktuelle Cache lokal gespeichert wird.
- Den neuesten Cache vom Remotecomputer auf den lokalen Computer übertragen

Commerce speichert die Hash-Datenversion in Redis, wobei das Suffix &quot;:hash&quot;an den regulären Schlüssel angehängt wird. Wenn ein veralteter lokaler Cache vorhanden ist, werden die Daten mit einem Cache-Adapter auf den lokalen Computer übertragen.

>[!INFO]
>
>Für Adobe Commerce in der Cloud-Infrastruktur können Sie [Variablen bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) für die L2-Cache-Konfiguration verwenden.

## Konfigurationsbeispiel

Verwenden Sie das folgende Beispiel, um den vorhandenen Cache-Abschnitt in der Datei `app/etc/env.php` zu ändern oder zu ersetzen.

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
   - `cache_dir` ist eine Datei-Cache-spezifische Option für den Ordner, in dem der lokale Cache gespeichert ist.

Adobe empfiehlt die Verwendung von Redis für das Remote-Caching (`\Magento\Framework\Cache\Backend\Redis`) und `Cm_Cache_Backend_File` für die lokale Zwischenspeicherung von Daten im gemeinsamen Speicher mit: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe empfiehlt die Verwendung der Funktion [`cache preload`](redis-pg-cache.md#redis-preload-feature) , da dadurch der Druck auf Redis drastisch verringert wird. Vergessen Sie nicht, das Suffix &#39;:hash&#39; für Preload-Schlüssel hinzuzufügen.

## Optionen für veralteten Cache

Ab [!DNL Commerce] 2.4 kann die Option `use_stale_cache` die Leistung in bestimmten Fällen verbessern.

Im Allgemeinen ist der Kompromiss mit der Sperrwartung von der Leistungsseite aus akzeptabel, aber je größer die Anzahl der Blöcke oder des Cache des Händlers ist, desto mehr Zeit wird für das Warten auf Sperren benötigt. In einigen Szenarien können Sie eine **Anzahl von Schlüsseln** \* **Lookup-Timeout** Zeitdauer für den Prozess warten. In einigen seltenen Fällen kann der Händler Hunderte von Schlüsseln im Cache von `Block/Config` haben, sodass selbst ein kleiner Timeout beim Suchen nach einer Sperre Sekunden kosten kann.

Der alte Cache funktioniert nur mit einem L2-Cache. Mit einem veralteten Cache können Sie einen veralteten Cache senden, während ein neuer in einem parallelen Prozess generiert wird. Um den veralteten Cache zu aktivieren, fügen Sie `'use_stale_cache' => true` zur obersten Konfiguration des L2-Cache hinzu.

Adobe empfiehlt, die Option `use_stale_cache` nur für Cache-Typen zu aktivieren, die am meisten davon profitieren, darunter:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe rät davon ab, die Option `use_stale_cache` für den Cache-Typ `default` zu aktivieren.

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
