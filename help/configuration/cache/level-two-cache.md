---
title: L2-Cache-Konfiguration zur Leistungsoptimierung
description: Erfahren Sie, wie Sie den L2-Cache lokal in Adobe Commerce konfigurieren, um den Netzwerk-Traffic zu reduzieren und die Leistung zu verbessern. Vergleichen Sie die alte RemoteSynchronizedCache-Implementierung mit der modernen Symfony L2-Implementierung.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# L2-Cache-Konfiguration zur Leistungsoptimierung

L2-Caching (auf zwei Ebenen) reduziert den Netzwerkverkehr zwischen dem Remote-Cache-Service und der Commerce-Anwendung, indem auf jedem Webknoten eine lokale Cache-Ebene hinzugefügt wird. Eine standardmäßige Commerce-Instanz kann etwa 300 KB pro Anfrage übertragen. Bei hohen Anforderungsvolumina kann der resultierende Netzwerkverkehr erheblich sein.

Beim L2-Caching speichert jeder Web-Knoten häufig aufgerufene Daten lokal und verwendet den Remote-Cache für zwei Zwecke:

- Überprüfen der Cache-Datenversion, um sicherzustellen, dass der neueste Cache lokal gespeichert wird
- Übertragen aktualisierter Cache-Daten vom Remote-Cache-Service auf den lokalen Computer

Commerce speichert die Hash-Datenversion im Remote-Cache, wobei das Suffix `:hash` an den regulären Schlüssel angehängt wird. Wenn der lokale Cache veraltet ist, werden die Daten über einen Cache-Adapter vom Remote-Cache-Service abgerufen.

Die verfügbare L2-Cache-Implementierung hängt von der Commerce-Version und der Patch-Ebene ab:

| Implementierung | Commerce-Version | Remote-Cache-Service | Beschreibung |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | Vor 2.4.9, sofern unterstützt | Redis oder Valley, je nach Release- und Patch-Level | Zend-basierter Zwei-Ebenen-Cache mit `Cm_Cache_Backend_File` für lokalen Speicher |
| [Symfony L2 (`symfony_l2`)](#symfony-l2-cache-implementation) | 2.4.9 und höher | Tal | Moderne Symfony Cache-basierte L2-Implementierung mit PSR-6-Konformität |

## Konfiguration des RemoteSynchronizedCache L2-Cache


>[!NOTE]
>
>Dieser Abschnitt enthält Informationen zur `RemoteSynchronizedCache` L2-Konfiguration für lokale Adobe Commerce-Versionen vor 2.4.9, die von der exakten Support-Matrix für Commerce-Versionen und Patches unterstützt wird.
>
>Verwenden Sie für Adobe Commerce 2.4.9 und höher Valkey mit [Symfony L2-Cache](#symfony-l2-cache-implementation).
>
>Konfigurieren Sie für Adobe Commerce in der Cloud-Infrastruktur den L2-Cache über Bereitstellungsvariablen in `.magento.env.yaml`. `app/etc/env.php` nicht direkt bearbeiten. Siehe [Konfigurieren des L2-Cache](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Die Anweisungen zur Cache-Konfiguration hängen von Ihrer Commerce-Version ab:

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
  - `remote_backend` ist die Remote-Cache-Implementierung: Redis oder Valkey, je nach Commerce-Version und Patch-Unterstützung.
  - `remote_backend_options` ist die Remote-Cache-Konfiguration.
  - `local_backend` ist die lokale Cache-Implementierung: `Cm_Cache_Backend_File`.
  - `local_backend_options` ist die lokale Cache-Konfiguration.
  - `cache_dir` ist eine Datei-Cache-spezifische Option, die das Verzeichnis definiert, in dem der lokale Cache gespeichert wird.

Für Adobe Commerce-Versionen vor 2.4.9, die Redis oder Valkey unterstützen, empfiehlt Adobe die Verwendung von Redis oder Valkey für das Remote-Caching, wie von der exakten Version unterstützt, und `Cm_Cache_Backend_File` für das lokale Caching. Der lokale Cache wird normalerweise in einem temporären Dateisystem gespeichert, z. B. `/dev/shm/`:

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

Adobe empfiehlt die Verwendung der `[cache preload](redis-pg-cache.md#redis-preload-feature)`-Funktion, da dadurch die Redis-Last reduziert wird. Stellen Sie sicher, dass Sie das Suffix `:hash` für Vorabladeschlüssel hinzufügen.

## Veraltete Cache-Optionen

Ab Commerce 2.4 kann die `use_stale_cache`-Option in bestimmten Fällen die Leistung verbessern, indem zuvor zwischengespeicherte Daten bereitgestellt werden, während in einem parallelen Prozess neue Cache-Daten generiert werden. Die in diesem Abschnitt beschriebenen empfohlenen Cache-Typen und Kompromisse gelten sowohl für die `RemoteSynchronizedCache`- als auch für `symfony_l2`. Ein Beispiel für eine `symfony_l2` Konfiguration finden Sie unter [Symfony L2-Cache mit veraltetem Cache](#symfony-l2-cache-with-stale-cache).

Im Allgemeinen ist der Kompromiss mit Sperrwartung aus Sicht der Leistung akzeptabel. Je mehr Blöcke oder Cache-Einträge vorhanden sind, desto länger dauert die Sperrwartung. In einigen Szenarien kann die Wartezeit für den Prozess bis zu **die Anzahl der Schlüssel** x **Lookup-**) betragen. In seltenen Fällen kann ein Benutzer Hunderte von Schlüsseln im `Block/Config`-Cache haben, sodass selbst ein kleines Lookup-Timeout für eine Sperre Sekunden kosten kann.

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

Der folgende Code zeigt eine Beispielkonfiguration für das `RemoteSynchronizedCache`-Backend. Ein `symfony_l2` Beispiel finden Sie unter [Symfony L2 Cache with Stale Cache](#symfony-l2-cache-with-stale-cache).

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

## Symfony L2-Cache-Implementierung

Verwenden Sie in Commerce ab Version 2.4.9 die Symfony L2-Cache-Implementierung (`symfony_l2`-Backend) anstelle von `RemoteSynchronizedCache`. Der Symfony L2-Cache bietet eine PSR-6-konforme Caching-Implementierung mit Valkey.

>[!IMPORTANT]
>
>Redis wird für die Cache-Konfiguration in den folgenden Adobe Commerce-Versionen nicht unterstützt:
>
>- Adobe Commerce 2.4.9 und höher
>- Patches für Adobe Commerce 2.4.8-P4 und höher
>- Adobe Commerce 2.4.7-p9 und neuere Patches
>- Adobe Commerce 2.4.6-P14 und neuere Patches
>- Adobe Commerce 2.4.5-P16 und neuere Patches
>
>Konfigurieren Sie für diese Versionen Valley.
>
>Wenn Sie `symfony_l2` für das L2-Caching unter Adobe Commerce 2.4.9 oder höher konfigurieren, müssen Sie Valkey für den Remote-Cache-Service verwenden. Siehe [Einrichten von &#x200B;](config-valkey.md).

### Migration von RemoteSynchronizedCache zu Symfony L2

Wenn Sie ein Upgrade einer On-Premise-Installation vom `RemoteSynchronizedCache`-Backend auf `symfony_l2` durchführen, überprüfen Sie Folgendes, bevor Sie `app/etc/env.php` aktualisieren. Es reicht nicht aus, nur den `backend` zu ändern. Die Konfigurationsstruktur, die Schlüsselnamen und einige Standardverhaltensweisen unterscheiden sich.

- **Die Konfigurationsstruktur ändert sich.** `remote_backend`, `remote_backend_options` und `local_backend` verwenden unterschiedliche Werte unter `symfony_l2`. Beispielsweise wird `remote_backend` anstelle eines vollqualifizierten Klassennamens zu `'valkey'`. Verwenden Sie das [Konfigurationsbeispiel](#configuration-example-with-symfony-l2-cache) unten als Ausgangspunkt, anstatt die vorhandene `RemoteSynchronizedCache`-Konfiguration zu bearbeiten.

- **`preload_keys`wird nicht empfohlen mit `symfony_l2`.** Wenn Ihre `RemoteSynchronizedCache`-Konfiguration `preload_keys` enthält, entfernen Sie sie im Rahmen der Migration. Das Vorabladen von Schlüsseln verbessert die Leistung unter `symfony_l2` nicht und kann die Last auf Valkey erhöhen, indem zusätzliche, unnötige Schlüsselsuchen ausgelöst werden.

- **Komprimierung erfordert ein explizites Flag.** Wenn Sie `compression_lib` allein festlegen, wird die Komprimierung unter `symfony_l2` nicht aktiviert. Siehe [Backend-Optionen für Symfony L2-Cache](#backend-options-for-symfony-l2-cache) für die erforderliche `compress_data`.

- **Bei manuell konfigurierten lokalen Bereitstellungen ist veralteter Cache nicht standardmäßig aktiviert.** `use_stale_cache` ist standardmäßig unter `symfony_l2` auf `false` gesetzt (siehe Tabelle [Backend-Optionen](#backend-options-for-symfony-l2-cache)). Wenn Ihre `RemoteSynchronizedCache`-Konfiguration das `stale_cache_enabled`-Frontend verwendet, müssen Sie es explizit mit dem Muster im [Symfony L2-Cache mit veraltetem Cache) &#x200B;](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>In Adobe Commerce in Cloud-Umgebungen, in denen die Variable &quot;`VALKEY_BACKEND: symfony_l2`-Bereitstellung“ festgelegt ist, wird die vollständige L2-Konfiguration, einschließlich des `stale_cache_enabled` Frontend, automatisch von `ece-tools` generiert. Siehe [Konfigurieren des Symfony L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)Cache für Cloud-spezifisches Verhalten.

- **Redis ist kein unterstütztes Remote-Backend für `symfony_l2`.** Migrieren Sie im Rahmen dieser Änderung nach Valley. Siehe [Einrichten von &#x200B;](config-valkey.md).

### Konfigurationsbeispiel mit Symfony L2-Cache

>[!IMPORTANT]
>
>Dieses `app/etc/env.php` Beispiel gilt nur für lokale Installationen. Bearbeiten Sie für Adobe Commerce in der Cloud-Infrastruktur `app/etc/env.php` nicht direkt. `VALKEY_BACKEND: symfony_l2` in `.magento.env.yaml` festlegen. `ece-tools` generiert und verwaltet die L2-Cache-Konfiguration während der Bereitstellung. Siehe [Konfigurieren des Symfony L2-Cache](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

Verwenden Sie in der `app/etc/env.php`-Datei den vereinfachten `symfony_l2`-Backend-Typ für den L2-Cache. Dieses Beispiel umfasst nicht die `preload_keys` Konfiguration, was bei `symfony_l2` nicht empfohlen wird. Weitere Informationen finden Sie unter [Migration von RemoteSynchronizedCache zu Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

Im Beispiel wird `cleanup_percentage` auf `90` gesetzt. Der Standardwert ist `95`. Passen Sie diesen Wert entsprechend dem verfügbaren lokalen Cache-Speicher und den Anforderungen Ihrer Commerce-Bereitstellung an.

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
| -------- | ------ | --------- | ----------- |
| `remote_backend` | Zeichenfolge | `'valkey'` | Remote-Cache-Backend. Verwenden Sie `valkey` mit Symfony L2. Redis wird offiziell nicht unterstützt. |
| `remote_backend_options` | Array | `[]` | Remote Valley Backend-Konfiguration |
| `local_backend` | Zeichenfolge | `'file'` | Lokaler Backend-Typ: `file` oder `apcu` |
| `local_backend_options` | Array | `[]` | Lokale Backend-Konfiguration |
| `cleanup_percentage` | Ganzzahl | `95` | Schwellenwert für die L1-Cache-Bereinigung, ausgedrückt als Prozentsatz von 1 bis 100 |
| `use_stale_cache` | Boolesch | `false` | Ermöglicht veralteten Cache für das Frontend |
| `compress_data` | Boolesch | `false` | Komprimierung in Kombination mit `compression_lib`. Legen Sie diese Option in den Remote Valley Backend-Optionen fest. |
| `persistent` | Boolesch | `true` | Steuert persistente Verbindungen zum Remote-Backend. Legen Sie hierfür `false` (`'0'`) fest, um das Zend-Cache-Verhalten zu berücksichtigen, das standardmäßig auf nicht persistente Verbindungen festgelegt ist. |

>[!NOTE]
>
>Die Option `frontend_options.write_control` gilt für die `RemoteSynchronizedCache` Konfiguration und nicht für `symfony_l2`.

### Verbesserte Symfony L2-Cache-Leistung und Zuverlässigkeit

>[!NOTE]
>
>Diese Verbesserungen gelten für Adobe Commerce 2.4.9-Bereitstellungen mit `symfony_l2` und sind im Patch ACP2E-5132 verfügbar.
>
>Wenden Sie diesen Patch für lokale Adobe Commerce-Installationen mithilfe des Quality Patches Tool (QPT) an. Für Adobe Commerce in der Cloud-Infrastruktur ist der Patch im Paket Cloud-Patches für Commerce enthalten, das eine Abhängigkeit von `ece-tools` ist. Aktualisieren Sie auf die neueste Version von `ece-tools`, um während der Bereitstellung die neuesten Cloud-Patches zu erhalten.

Die neuesten Aktualisierungen verbessern die Skalierbarkeit des Symfony L2-Cache, reduzieren unnötige Dateisystem-E/A und verbessern die Cache-Konsistenz und -Zuverlässigkeit.

#### Optimierter Symfony L2-Cache-Tag-Speicher

Bei Valkey-unterstützten Symfony L2-Cache-Bereitstellungen werden Cache-Tags ausschließlich in Valkey gespeichert. Dadurch werden redundante Tag-Index-Schreibvorgänge im Dateisystem eliminiert, Datenträger-E/A reduziert und unnötiges Wachstum des `var/cache/symfony/tags/`-Verzeichnisses verhindert.

#### Verbessertes dateibasiertes Cache-Verhalten

Bei Bereitstellungen mit dem dateibasierten Cache (ohne Valley) wird der lokale Tag-Index weiterhin gepflegt, um die Cache-Invalidierung zu unterstützen. Der Tag-Index wird jetzt in den konfigurierten `cache_dir` anstelle des zuvor hartcodierten `var/cache`-Speicherorts geschrieben, was eine konsistente Cache-Verzeichnisverwendung gewährleistet und die Unterstützung für benutzerdefinierte Cache-Konfigurationen verbessert.

#### Veraltete Tag-Mitgliedschaftskorrektur nach dem Retagging

Wenn Sie einen Cache-Eintrag erneut taggen, kann er mit Tags verknüpft bleiben, zu denen er nicht mehr gehört. Veraltete Tag-Mitgliedschaften werden jetzt beim erneuten Taggen gelöscht, sodass Cache-Einträge nur durch die ihnen derzeit zugewiesenen Tags ungültig gemacht werden.

#### Fehlerkorrektur - Redundante Remote-Schreibvorgänge für unveränderte Speichervorgänge

Beim Speichern eines Cache-Eintrags mit unverändertem Inhalt wird weiterhin ein Schreiben in das Remote-Backend (Valley) ausgelöst. Das Speichern wird jetzt übersprungen, wenn der Inhalt unverändert bleibt, wodurch unnötige Remote-Schreibvorgänge reduziert werden.

#### Größenbasierte Räumungskorrektur für L1 (cleanup_percentage)

Der `cleanup_percentage` Schwellenwert, der für die L1-größenbasierte Entfernung verwendet wurde, enthielt nicht konsistent Trigger-Bereinigung. Die L1-Cache-Entfernung berücksichtigt jetzt korrekt die konfigurierten `cleanup_percentage`.

#### Regenerationssperre für veralteten Cache

Wenn `use_stale_cache` aktiviert ist und die Remote-Kopie eines Eintrags vorübergehend nicht verfügbar ist, erhält jetzt nur ein Prozess eine kurzlebige Sperre, um diesen Eintrag neu zu generieren. Andere gleichzeitige Anfragen für denselben Eintrag bedienen weiterhin den vorhandenen lokalen Wert, anstatt ihn selbst zu regenerieren, was die Anzahl der Regenerierungsstempel und die redundante Backend-Last reduziert.

#### Auswirkung

- Beseitigt redundante Dateisystem-Tag-Index-Schreibvorgänge für Valkey-gestützte Symfony L2-Cache-Bereitstellungen, reduziert Festplatten-E/A und verhindert unnötiges Wachstum des `var/cache/symfony/tags/`.
- Stellt sicher, dass dateibasierte Cache-Bereitstellungen konsistent die konfigurierten `cache_dir` für den lokalen Tag-Index verwenden, während das Verhalten bei der Cache-Invalidierung erhalten bleibt.
- Verhindert die falsche Cache-Invalidierung, die durch veraltete Tag-Mitgliedschaften verursacht wird, die nach dem Retagging zurückbleiben.
- Reduziert unnötige Remote-Schreibvorgänge für unveränderte Cache-Speichervorgänge und verringert so die Netzwerk- und Backend-Last.
- Stellt sicher, dass Trigger mit L1-Cache-Entfernung zuverlässig den konfigurierten `cleanup_percentage` erreichen.
- Reduziert die Anzahl von Regenerierungsstempeln für `use_stale_cache` Einträge, indem ein einzelner Regenerator pro Schlüssel ausgewählt wird, anstatt den Eintrag bei jeder gleichzeitigen Anforderung neu erstellen zu lassen.

Detaillierte Konfigurationsoptionen finden Sie unter:

- [Valley-Cache-Konfiguration mit Symfony Cache](valkey-pg-cache.md)
