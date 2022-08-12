---
title: L2-Cache-Konfiguration
description: Erfahren Sie, wie Sie den L2-Cache konfigurieren.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# L2-Cache-Konfiguration

Die Zwischenspeicherung ermöglicht eine Verringerung des Netzwerk-Traffics zwischen dem Remote-Cache-Speicher und der Commerce-Anwendung. Eine Standard-Commerce-Instanz transferiert ca. 300 kb pro Anforderung, und der Traffic kann in einigen Situationen schnell auf über ca. 1000 Anfragen anwachsen.

Um die Netzwerkbandbreite auf Redis zu reduzieren, speichern Sie die Cachedaten lokal auf jedem Webknoten und verwenden Sie den Remote-Cache für zwei Zwecke:

- Überprüfen Sie die Cache-Datenversion und stellen Sie sicher, dass der aktuelle Cache lokal gespeichert wird.
- Den neuesten Cache vom Remotecomputer auf den lokalen Computer übertragen

Commerce speichert die gehashte Datenversion in Redis, wobei das Suffix &quot;:hash&quot;an den regulären Schlüssel angehängt wird. Wenn ein veralteter lokaler Cache vorhanden ist, werden die Daten mit einem Cache-Adapter auf den lokalen Computer übertragen.

>[!INFO]
>
>Beachten Sie bei Adobe Commerce zur Cloud-Infrastruktur die Best Practices im Abschnitt [Erweiterte Redis-Cache-Implementierung](https://support.magento.com/hc/en-us/articles/360049292532) Support-Artikel.

## Konfigurationsbeispiel

Verwenden Sie das folgende Beispiel, um den vorhandenen Cache-Abschnitt im `app/etc/env.php` -Datei.

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
                ],
                'use_stale_cache' => false,
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
      - `cache_dir` ist eine Datei-Cache-spezifische Option für den Ordner, in dem der lokale Cache gespeichert wird.
   - `use_stale_cache` ist ein Flag, das die Verwendung von veraltetem Cache aktiviert oder deaktiviert.

Adobe empfiehlt die Verwendung von Redis für Remote-Zwischenspeicherung (`\Magento\Framework\Cache\Backend\Redis`) und `Cm_Cache_Backend_File` für die lokale Zwischenspeicherung von Daten im gemeinsamen Speicher mit: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe empfiehlt die Verwendung der [`cache preload`](redis-pg-cache.md#redis-preload-feature) Funktion, da sie den Druck auf Redis drastisch verringert. Vergessen Sie nicht, das Suffix &#39;:hash&#39; für Preload-Schlüssel hinzuzufügen.

## Optionen für veralteten Cache

Einstieg in [!DNL Commerce] 2.4. `stale_cache` -Option kann die Leistung in bestimmten Fällen verbessern.

Im Allgemeinen ist der Kompromiss mit der Sperrwartung von der Leistungsseite aus akzeptabel, aber je größer die Anzahl der Blöcke oder des Cache des Händlers ist, desto mehr Zeit wird für das Warten auf Sperren benötigt. In einigen Szenarien können Sie einen **Anzahl der Schlüssel** \* **Lookup-Timeout** Zeitdauer für den Prozess. In einigen seltenen Fällen kann der Händler Hunderte von Schlüsseln im `Block/Config` zwischenspeichern, sodass selbst ein kleiner Timeout beim Suchen für das Sperren Sekunden kosten kann.

Der alte Cache funktioniert nur mit einem L2-Cache. Mit einem veralteten Cache können Sie einen veralteten Cache senden, während ein neuer in einem parallelen Prozess generiert wird. Um veralteten Cache zu aktivieren, fügen Sie `'use_stale_cache' => true` , um die Konfiguration des L2-Caches zu beenden.