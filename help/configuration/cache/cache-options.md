---
title: Cache-Backend-Optionen und Speicherreferenz
description: Erfahren Sie mehr über die Cache-Backend-Optionen in Adobe Commerce, einschließlich Dateisystem, Redis, Valkey und Datenbankspeicher. Entdecken Sie alte und moderne Ansätze.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 309
ht-degree: 0%

---

# Cache-Backend-Optionen und Speicherreferenz

{{cloud-cache-config}}

Die Commerce-Anwendung verwendet ein Cache-Frontend und ein Backend auf niedriger Ebene, um Zugriff auf den Cache-Speicher zu gewähren. Commerce unterstützt verschiedene Caching-Backends und -Strategien, die jeweils für verschiedene Anwendungsfälle geeignet sind. Auf dieser Seite werden die verfügbaren Backends und deren Unterschiede beschrieben.

## Backend-Cache-Optionen

In der folgenden Tabelle sind die verfügbaren Backend-Caches zusammengefasst:

| Backend | Beschreibung | Konfigurationshandbuch |
| ------- | ----------- | ------------------- |
| Dateisystem | Standard. Speichert Cache-Daten in Dateien unter `var/cache/`. Keine Konfiguration erforderlich. | Nicht zutreffend |
| [Redis](config-redis.md) | In-Memory-Datenspeicher für leistungsstarkes Caching. | [Redis für Standard-Cache verwenden](redis-pg-cache.md) |
| [Valkey](config-valkey.md) | Open-Source, Redis-kompatible Alternative. | [Valkey für Standardcache verwenden](valkey-pg-cache.md) |
| [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Datenbankgestütztes Caching. | [Erstellen benutzerdefinierter Cache-Engines](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (Entwicklerdokumentation für Adobe) |

>[!NOTE]
>
>[Varnish](config-varnish.md) verarbeitet das Caching ganzer Seiten auf HTTP-Ebene und verwendet nicht das Cache-Backend auf niedriger Ebene.

## Implementierungsansätze

Commerce unterstützt zwei Backend-Implementierungsansätze. Der von Ihnen gewählte Ansatz hängt von Ihrer Commerce-Version ab:

>[!BEGINTABS]

>[!TAB Legacy-Zend-basierter Cache (2.4.8 und früher)]

Verwendet vollständige Klassennamen für die Backend-Konfiguration:

| Backend | Klassenname |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Tal | `Magento\Framework\Cache\Backend\Valkey` |

Diese sind mit der `Zend_Cache_Backend` kompatibel.

**Beispielkonfiguration:**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB Moderner Symfony-Cache (2.4.9 und höher, empfohlen)]

>[!TIP]
>
>Die moderne Symfony Cache-Implementierung bietet eine bessere Leistung durch PSR-6-Compliance, Igbinary-Serialisierung, Gzip-Komprimierung, Lua-Skripte und persistente Verbindungen.

Verwendet vereinfachte Namen von Backend-Typen:

| Backend | Name eingeben |
| ------- | --------- |
| Redis | `redis` |
| Tal | `valkey` |
| Dateisystem | `file` |

**Beispielkonfiguration:**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

Die vollständigen Konfigurationsoptionen finden Sie unter:

- [Redis für Standard-Cache verwenden](redis-pg-cache.md)
- [Valley für Standard-Cache verwenden](valkey-pg-cache.md)
- [L2-Cache-Konfiguration](level-two-cache.md)

Siehe die [Laminas-Dokumentation](https://docs.laminas.dev/) für ältere Zend-basierte Optionen.
