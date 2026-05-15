---
title: Cache-Frontends konfigurieren
description: Erfahren Sie, wie Sie Cache-Frontends definieren und sie mit Cache-Typen in Adobe Commerce verknüpfen. Erfahren Sie mehr über die Konfigurationssyntax für env.php und di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Cache-Frontends konfigurieren

Ein Cache-Frontend ist eine Schnittstelle zwischen Commerce und dem Cache-Speicher-Backend. Sie können mehrere Frontends mit jeweils unterschiedlichen Backend-Einstellungen definieren und dann jedem Frontend [Cache-Typen](../cli/manage-cache.md#clean-and-flush-cache-types) zuweisen.

Dies ist nützlich, wenn Sie verschiedene Cache-Backends oder Konfigurationen für verschiedene Arten von zwischengespeicherten Daten verwenden möchten. Beispielsweise können Sie `full_page` Zwischenspeicherung in einer dedizierten Redis-Datenbank verwenden, während Sie eine separate Datenbank für die `default` Zwischenspeicherung verwenden.

## Standard-Frontend verwenden

Commerce bietet ein `default` Cache-Frontend, das für alle Cache-Typen funktioniert. Er erweitert [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) durch die Implementierung des [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)-Frontend-Cache.

In den meisten Fällen müssen Sie das Frontend nicht anpassen. Sie müssen nur das Backend konfigurieren. Siehe [Cache-Backend-Optionen](cache-options.md).

## Definieren eines benutzerdefinierten Cache-Frontends

In den folgenden Schritten wird beschrieben, wie Sie ein Cache-Frontend einem Cache-Typ zuordnen.

### Schritt 1: Definieren eines Cache-Frontends und Zuweisen von Cache-Typen

Um ein benutzerdefiniertes Cache-Frontend zu definieren, fügen Sie die -Konfiguration zu `app/etc/env.php` hinzu (wodurch `di.xml` überschrieben wird):

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Dabei gilt:

- `<unique frontend id>` - Ein eindeutiger Name zur Identifizierung des Frontends (z. B. `default`, `page_cache`, `stale_cache_enabled`)
- `<cache options>` - Backend-Typ und Optionen für dieses Frontend (siehe [Cache-Optionen](cache-options.md))
- `<cache type>` - Ein Commerce-Cache-Typ, der diesem Frontend zugewiesen werden soll (z. B. `config`, `layout`, `block_html`, `full_page`)

>[!TIP]
>
>**Moderne Symfony-Cache-Implementierung (2.4.9+):** Ab Commerce 2.4.9 können Sie mit der modernen Symfony-Cache-Implementierung vereinfachte Backend-Typen wie `redis`, `valkey` oder `file` verwenden. Siehe [Verwenden von Redis für ](redis-pg-cache.md)-Cache und [Verwenden von Valkey für ](valkey-pg-cache.md)-Cache) für Details.

### Schritt 2: Konfigurieren der Frontend- und Backend-Optionen

Sie können die Konfigurationsoptionen für Frontend- und Backend-Cache in `env.php` oder `di.xml` angeben. Diese Aufgabe ist optional. Wenn Sie keine Optionen angeben, verwendet Commerce die standardmäßigen Frontend- und Backend-Einstellungen.

`env.php`:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

Dabei gilt:

- `<frontend_type>` - Der Frontend-Cache-Typ auf niedriger Ebene. Geben Sie einen Klassennamen an, der mit `Zend\Cache\Core` kompatibel ist.
Wenn ausgelassen, wird [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) verwendet.

- `<frontend_option>`, `<frontend_option_value>` - Name und Wert der Optionen, die das Commerce-Framework bei der Erstellung als assoziatives Array an den Frontend-Cache übergibt.

- `<backend_type>` - Der Backend-Cache-Typ auf niedriger Ebene. Sie können Folgendes angeben:
   - **Modern Symfony Cache (2.4.9+, empfohlen)**: Vereinfachte Namen wie `redis`, `valkey` oder `file`
   - **Legacy (Zend-basiert)** Vollständiger Klassenname kompatibel mit `Zend_Cache_Backend`, die `Zend_Cache_Backend_Interface` implementiert

- `<backend_option>`, `<backend_option_value>` - Name und Wert der Optionen, die das Commerce-Framework bei der Erstellung als assoziatives Array an den Backend-Cache übergibt.

>[!NOTE]
>
>**Legacy-Implementierung vs. moderne Implementierung:**
>
>- **Legacy (Zend-basiert)**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **Modern (Symfony Cache)**: `'backend' => 'redis'` (empfohlen für Commerce 2.4.9+)
>
>Die moderne Symfony Cache-Implementierung bietet eine bessere Leistung durch PSR-6-Compliance, Igbinary-Serialisierung, Gzip-Komprimierung, Lua-Skripte und persistente Verbindungen.

Siehe die [Laminas-](https://docs.laminas.dev/)) für Zend-basierte Optionen oder die modernen Symfony Cache-Handbücher für [Redis](redis-pg-cache.md) und [Valkey](valkey-pg-cache.md).
