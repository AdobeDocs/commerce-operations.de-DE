---
title: L2-Cache-Konfiguration zur Leistungsoptimierung
description: Erfahren Sie, wie Sie den L2-Cache in Adobe Commerce konfigurieren, um den Netzwerk-Traffic zu reduzieren und die Leistung zu verbessern. Entdecken Sie die Implementierungsoptionen von Legacy und Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
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
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# L2-Cache-Konfiguration zur Leistungsoptimierung

L2-Caching (auf zwei Ebenen) reduziert den Netzwerk-Traffic zwischen dem Remote-Cache-Speicher (Redis oder Valkey) und der Commerce-Anwendung, indem eine lokale Cache-Ebene auf jedem Web-Knoten hinzugefügt wird. Eine standardmäßige Commerce-Instanz überträgt etwa 300 KB pro Anfrage, und der Traffic kann in einigen Situationen schnell auf über 1.000 Anfragen wachsen.

Beim L2-Caching speichert jeder Web-Knoten häufig aufgerufene Daten lokal und verwendet den Remote-Cache für zwei Zwecke:

- Überprüfen der Cache-Datenversion, um sicherzustellen, dass der neueste Cache lokal gespeichert wird
- Übertragen aktualisierter Cache-Daten vom Remote-Speicher auf den lokalen Computer

Commerce speichert die Hash-Datenversion im Remote-Cache, wobei das Suffix `:hash` an den regulären Schlüssel angehängt wird. Wenn der lokale Cache veraltet ist, werden die Daten über einen Cache-Adapter vom Remote-Computer abgerufen.

In Adobe Commerce stehen zwei L2-Cache-Implementierungen zur Verfügung:

| Implementierung | Version | Beschreibung |
| -------------- | ------- | ----------- |
| [Legacy (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Zend-basierter Zwei-Ebenen-Cache mit `Cm_Cache_Backend_File` für lokalen Speicher |
| [Modern (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony Cache-basiertes L2 mit PSR-6-Konformität und verbesserter Leistung. Unterstützt Valley. |

Der Symfony L2-Cache ist die empfohlene Implementierung für Adobe Commerce 2.4.9 und neuere Versionen. Es bietet eine moderne, PSR-6-konforme Caching-Implementierung mit erheblichen Leistungsverbesserungen im Vergleich zu herkömmlichen `RemoteSynchronizedCache`.

## Konfiguration des alten L2-Cache (RemoteSynchronizedCache)

Die Konfigurationsanweisungen für den alten L2-Cache gelten für ältere Versionen von Adobe Commerce. Wenn Sie Adobe Commerce Version 2.4.9 oder höher verwenden, verwenden Sie Valkey mit der [Modern Symfony L2 Cache-Implementierung](#modern-symfony-l2-cache-implementation).

>[!NOTE]
>
>Diese Seite behandelt nur die lokale Konfiguration. Informationen zu Adobe Commerce on Cloud finden Sie unter [Konfigurieren des L2-Cache](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Für lokale Adobe Commerce-Versionen, die Redis unterstützen, verwenden Sie das folgende Beispiel, um den vorhandenen Cache-Abschnitt in der `app/etc/env.php`-Datei zu ändern oder zu ersetzen.

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
]
```

Dabei gilt:

- `backend` ist die L2-Cache-Implementierung.
- `backend_options` ist die L2-Cache-Konfiguration.
  - `remote_backend` ist die Remote-Cache-Implementierung: Redis oder MySQL.
  - `remote_backend_options` ist die Remote-Cache-Konfiguration.
  - `local_backend` ist die lokale Cache-Implementierung: `Cm_Cache_Backend_File`.
  - `local_backend_options` ist die lokale Cache-Konfiguration.
  - `cache_dir` ist eine Datei-Cache-spezifische Option für das Verzeichnis, in dem der lokale Cache gespeichert ist.

Für Adobe Commerce-Versionen vor 2.4.9, die Redis unterstützen, empfiehlt Adobe die Verwendung von Redis für das Remote-Caching (`\Magento\Framework\Cache\Backend\Redis`) und `Cm_Cache_Backend_File` für das lokale Caching von Daten im gemeinsamen Speicher mit: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`.

Adobe empfiehlt die Verwendung der [`cache preload`](redis-pg-cache.md#redis-preload-feature)-Funktion, da sie den Druck auf Redis drastisch verringert. Vergessen Sie nicht, das Suffix `:hash` für Vorabladeschlüssel hinzuzufügen.

## Veraltete Cache-Optionen

Ab Commerce 2.4 kann die `use_stale_cache`-Option in bestimmten Fällen die Leistung verbessern, indem zuvor zwischengespeicherte Daten bereitgestellt werden, während in einem parallelen Prozess neue Cache-Daten generiert werden. Die in diesem Abschnitt beschriebenen empfohlenen Cache-Typen und Kompromisse gelten sowohl für die veralteten `RemoteSynchronizedCache`- als auch für `symfony_l2`. Ein Beispiel für eine `symfony_l2` Konfiguration finden Sie unter [Symfony L2-Cache mit veraltetem Cache](#symfony-l2-cache-with-stale-cache).

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

Der folgende Code zeigt eine Beispielkonfiguration für das alte `RemoteSynchronizedCache`-Backend. Ein `symfony_l2` Beispiel finden Sie unter [Symfony L2 Cache with Stale Cache](#symfony-l2-cache-with-stale-cache).

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

Verwenden Sie in Commerce ab Version 2.4.9 die Symfony Cache-basierte L2-Cache-Implementierung (`symfony_l2`-Backend) anstelle des alten L2-Cache. Der Symfony L2-Cache bietet eine moderne, PSR-6-konforme Caching-Implementierung mit deutlichen Leistungsverbesserungen gegenüber herkömmlichen `RemoteSynchronizedCache`.

>[!IMPORTANT]
>
>Redis wird nicht als Remote-Cache-Backend unterstützt, das mit beginnt:
>
>- Adobe Commerce 2.4.9 und höher
>- 2.4.8-P4 und neuere Patches
>- 2.4.7-P9 und neuere Patches
>- 2.4.6-P14 und neuere Patches
>- 2.4.5-P16 und neuere Patches
>
>Wenn Sie ein Upgrade für frühere Versionen durchführen, richten Sie Valkey ein und aktualisieren Sie Ihre Cache-Konfiguration für die Verwendung von `symfony_l2`. Siehe [Einrichten von Valkey](config-valkey.md) und [Systemanforderungen](../../installation/system-requirements.md).

### Vorteile des Symfony L2-Cache

- **Moderne Architektur:** auf Symfony-Cache-Komponenten (PSR-6-kompatibel)
- **Bessere Leistung:** native Unterstützung für Igbinary-Serialisierung, Gzip-Komprimierung und Lua-Skripte
- **Persistente Verbindungen:** reduziert den Verbindungsaufwand in Valley durch Verbindungspools
- **Schlüssel vorladen:** unterstützt das Vorausfüllen von Cache-Schlüsseln für kritische Daten
- **Unterstützung veralteter Caches:** vollständige Kompatibilität mit der Option &quot;`use_stale_cache`&quot;
- **Vereinfachte Konfiguration:** Namen von Backend-Typen (`valkey`, `file`)

### Migration von RemoteSynchronizedCache zu Symfony L2

Wenn Sie ein Upgrade einer lokalen Installation vom alten `RemoteSynchronizedCache`-Backend auf `symfony_l2` durchführen, überprüfen Sie Folgendes, bevor Sie `app/etc/env.php` aktualisieren. Es reicht nicht aus, nur den `backend` zu ändern. Die Konfigurationsstruktur, die Schlüsselnamen und einige Standardverhaltensweisen unterscheiden sich.

- **Die Konfigurationsstruktur ändert sich.** `remote_backend`, `remote_backend_options` und `local_backend` verwenden unterschiedliche Werte unter `symfony_l2`. Beispielsweise wird `remote_backend` anstelle eines vollqualifizierten Klassennamens zu `'valkey'`. Verwenden Sie das [Konfigurationsbeispiel](#configuration-example-with-symfony-l2-cache) unten als Ausgangspunkt, anstatt die vorhandene Legacy-Konfiguration zu bearbeiten.

- **`preload_keys`wird nicht empfohlen mit `symfony_l2`.** Wenn Ihre ältere Konfiguration `preload_keys` enthält, entfernen Sie diese im Rahmen der Migration. Das Vorabladen von Schlüsseln verbessert die Leistung unter `symfony_l2` nicht und kann die Last auf Valkey erhöhen, indem zusätzliche, unnötige Schlüsselsuchen ausgelöst werden.

- **Komprimierung erfordert ein explizites Flag.** Wenn Sie `compression_lib` allein festlegen, wird die Komprimierung unter `symfony_l2` nicht aktiviert. Siehe [Backend-Optionen für Symfony L2-Cache](#backend-options-for-symfony-l2-cache) für die erforderliche `compress_data`.

- **Veralteter Cache ist bei manuell konfigurierten On-Premise-Bereitstellungen nicht standardmäßig aktiviert.** `use_stale_cache` ist standardmäßig unter `symfony_l2` auf `false` gesetzt (siehe Tabelle [Backend-Optionen](#backend-options-for-symfony-l2-cache)). Wenn Ihre alte Konfiguration das `stale_cache_enabled`-Frontend verwendet, müssen Sie es explizit mit dem Muster im [Symfony L2-Cache mit veraltetem Cache) &#x200B;](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>In Adobe Commerce in Cloud-Umgebungen, in denen die Variable &quot;`VALKEY_BACKEND: symfony_l2`-Bereitstellung“ festgelegt ist, wird die vollständige L2-Konfiguration, einschließlich des `stale_cache_enabled` Frontend, automatisch von `ece-tools` generiert. Siehe [Konfigurieren des Symfony L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)Cache für Cloud-spezifisches Verhalten.

- **Redis ist kein unterstütztes Remote-Backend für `symfony_l2`.** Migrieren Sie im Rahmen dieser Änderung nach Valley. Siehe [Einrichten von &#x200B;](config-valkey.md).

### Konfigurationsbeispiel mit Symfony L2-Cache

>[!NOTE]
>
>Dieses Beispiel dient zur On-Premise-`app/etc/env.php`. Für Adobe Commerce in Cloud Manager wird die Cache-Konfiguration automatisch von `ece-tools` verwaltet. Anstatt `env.php` direkt zu bearbeiten, siehe [Konfigurieren des Symfony L2-Cache](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

Verwenden Sie in der `app/etc/env.php`-Datei den vereinfachten `symfony_l2`-Backend-Typ für den L2-Cache. Dieses Beispiel umfasst nicht die `preload_keys` Konfiguration, was bei `symfony_l2` nicht empfohlen wird. Weitere Informationen finden Sie unter [Migration von RemoteSynchronizedCache zu Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
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

Siehe [Veraltete Cache-Optionen](#stale-cache-options), für welche Cache-Typen von veraltetem Cache profitieren und warum.

Verwenden Sie das folgende Beispiel, um separate Frontends für `symfony_l2` Unterstützung veralteter Caches zu konfigurieren:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | Zeichenfolge | `'valkey'` | Remote-Backend-Typ: `valkey` oder `file`. Verwenden Sie `valkey` für den L2-Cache. |
| `remote_backend_options` | Array | `[]` | Remote-Backend-Konfiguration (siehe Valley-Dokumentation) |
| `local_backend` | Zeichenfolge | `'file'` | Lokaler Backend-Typ: `file` oder `apcu` |
| `local_backend_options` | Array | `[]` | Lokale Backend-Konfiguration |
| `cleanup_percentage` | Ganzzahl | `95` | Schwellenwert für die L1-Cache-Bereinigung (1-100) |
| `use_stale_cache` | Boolesch | `false` | Veralteten Cache für hohe Verfügbarkeit aktivieren |
| `compress_data` | Boolesch | `false` | Komprimierung in Kombination mit `compression_lib`. Wenn Sie `compression_lib` allein festlegen, wird die Komprimierung nicht aktiviert. |
| `persistent` | Boolesch | `true` | Steuert persistente Verbindungen zum Remote-Backend. Setzen Sie diesen Wert auf `false` (`'0'`), um das veraltete Zend-Cache-Verhalten zu berücksichtigen, das standardmäßig auf nicht persistente Verbindungen eingestellt ist. |


>[!NOTE]
>
>- Die `remote_backend`-Option akzeptiert ebenfalls den Wert `redis`, Redis wird jedoch nicht offiziell unterstützt (siehe den obigen Hinweis unter &quot;[&#x200B; Symfony L2-Cache-Implementierung](#modern-symfony-l2-cache-implementation)).
>
>- `frontend_options.write_control`, das in der Legacy-`RemoteSynchronizedCache` verwendet wird, gilt nicht für `symfony_l2`.

### Verbesserte Symfony L2-Cache-Leistung und Zuverlässigkeit

>[!NOTE]
>
>Diese Verbesserungen gelten für Adobe Commerce 2.4.9-Bereitstellungen mit `symfony_l2` und sind im Patch ACP2E-5132 verfügbar. Wenden Sie diesen Patch für lokale Adobe Commerce-Installationen mithilfe des Quality Patches Tool (QPT) an. Für Adobe Commerce on Cloud wird dieser Patch automatisch über [Cloud-Patches für Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest) bereitgestellt.

Die neuesten Aktualisierungen verbessern die Skalierbarkeit des Symfony L2-Cache, reduzieren unnötige Dateisystem-E/A und verbessern die Cache-Konsistenz und -Zuverlässigkeit.

#### Optimierter Symfony L2-Cache-Tag-Speicher

Optimiertes Symfony L2-Cache-Verhalten für Valkey-gestützte Bereitstellungen durch Eliminierung redundanter Dateisystem-Tag-Index-Schreibvorgänge. Cache-Tags werden jetzt ausschließlich in Valkey gespeichert, wodurch das Symfony L2-Cache-Verhalten an der Legacy-Cache-Implementierung ausgerichtet wird. Dies reduziert unnötige Datenträger-E/A, verbessert die Cache-Schreibleistung und verhindert das Wachstum des `var/cache/symfony/tags/`.

#### Verbessertes dateibasiertes Cache-Verhalten

Bei Bereitstellungen mit dem dateibasierten Cache (ohne Valley) wird der lokale Tag-Index weiterhin gepflegt, um die Cache-Invalidierung zu unterstützen. Der Tag-Index wird jetzt in den konfigurierten `cache_dir` anstelle des zuvor hartcodierten `var/cache`-Speicherorts geschrieben, was eine konsistente Cache-Verzeichnisverwendung gewährleistet und die Unterstützung für benutzerdefinierte Cache-Konfigurationen verbessert.

#### Veraltete Tag-Mitgliedschaftskorrektur nach dem Retagging

Wenn Sie einen Cache-Eintrag erneut taggen, ist er möglicherweise mit Tags verknüpft, zu denen er nicht mehr gehört. Veraltete Tag-Mitgliedschaften werden jetzt beim erneuten Taggen gelöscht, sodass Cache-Einträge nur durch die ihnen derzeit zugewiesenen Tags ungültig gemacht werden.

#### Fehlerkorrektur - Redundante Remote-Schreibvorgänge für unveränderte Speichervorgänge

Beim Speichern eines Cache-Eintrags mit unverändertem Inhalt wird weiterhin ein Schreiben in das Remote-Backend (Valley) ausgelöst. Das Speichern wird jetzt übersprungen, wenn der Inhalt unverändert bleibt, wodurch unnötige Remote-Schreibvorgänge reduziert werden.

#### Größenbasierte Räumungskorrektur für L1 (cleanup_percentage)

Der `cleanup_percentage` Schwellenwert, der für die L1-größenbasierte Entfernung verwendet wurde, enthielt nicht konsistent Trigger-Bereinigung. Die L1-Cache-Entfernung berücksichtigt jetzt korrekt die konfigurierten `cleanup_percentage`.

#### Regenerationssperre für veralteten Cache

Wenn `use_stale_cache` aktiviert ist und die Remote-Kopie eines Eintrags vorübergehend nicht verfügbar ist, erhält jetzt nur ein Prozess eine kurzlebige Sperre, um diesen Eintrag neu zu generieren. Andere gleichzeitige Anfragen für denselben Eintrag bedienen weiterhin den vorhandenen lokalen Wert, anstatt ihn selbst zu regenerieren, was die Anzahl der Regenerierungsstempel und die redundante Backend-Last reduziert.

#### Auswirkung

- Beseitigt redundante Dateisystem-Tag-Indexschreibvorgänge für Valkey-unterstützte Symfony L2-Cache-Bereitstellungen, reduziert den Festplatten-E/A und verhindert unnötiges Wachstum des `var/cache/symfony/tags/`.
- Stellt sicher, dass dateibasierte Cache-Bereitstellungen konsistent die konfigurierten `cache_dir` für den lokalen Tag-Index verwenden, während das Verhalten bei der Cache-Invalidierung erhalten bleibt.
- Verhindert die falsche Cache-Invalidierung, die durch veraltete Tag-Mitgliedschaften verursacht wird, die nach dem Retagging zurückbleiben.
- Reduziert unnötige Remote-Schreibvorgänge für unveränderte Cache-Speichervorgänge und verringert so die Netzwerk- und Backend-Last.
- Stellt sicher, dass Trigger mit L1-Cache-Entfernung zuverlässig den konfigurierten `cleanup_percentage` erreichen.
- Reduziert die Anzahl von Regenerierungsstempeln für `use_stale_cache` Einträge, indem ein einzelner Regenerator pro Schlüssel ausgewählt wird, anstatt dass jede gleichzeitige Anforderung ihn neu erstellt.

Detaillierte Konfigurationsoptionen finden Sie unter:

- [Valley-Cache-Konfiguration mit Symfony Cache](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [Caching-Übersicht und Konfigurationsoptionen](caching-overview.md)
>- [Cache-Backend-Optionen und Speicherreferenz](cache-options.md)
>- [Konfigurieren von Cache-Frontends und -Typen](cache-types.md)
>- [Konfigurieren von Redis für Standard- und Seiten-Cache](redis-pg-cache.md)
