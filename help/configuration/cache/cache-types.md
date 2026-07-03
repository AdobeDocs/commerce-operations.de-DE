---
title: Konfigurieren von Cache-Frontends und -Typen
description: Erfahren Sie, wie Sie Cache-Frontends definieren und sie mit Cache-Typen in Adobe Commerce verknüpfen. Erfahren Sie mehr über die Konfigurationssyntax für env.php und di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 507
ht-degree: 1%

---

# Konfigurieren von Cache-Frontends und -Typen

Ein Cache-Frontend ist eine Schnittstelle zwischen Commerce-Cache-Typen und dem Cache-Speicher-Backend. Sie können mehrere Frontends mit jeweils unterschiedlichen Backend-Einstellungen definieren und dann jedem Frontend [Cache-Typen](../cli/manage-cache.md#clean-and-flush-cache-types) zuweisen.

Verwenden Sie diese Beziehung, um zu entscheiden, wo jeder Cache-Typ Daten speichert:

`cache type` -> `cache frontend` -> `cache backend`

Dies ist nützlich, wenn Sie verschiedene Cache-Backends oder Konfigurationen für verschiedene Arten von zwischengespeicherten Daten verwenden möchten. Beispielsweise können Sie den Cache-Typ `full_page` einem `page_cache`-Frontend zuweisen, das eine dedizierte Valkey-Datenbank verwendet, während andere Cache-Typen das `default`-Frontend verwenden.

{{cloud-cache-config}}

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
>Adobe Commerce 2.4.9 und höher verwenden vereinfachte Backend-Typnamen wie `valkey` oder `file` mit der Symfony Cache-Implementierung. Unter [Cache-Backend](cache-options.md)Optionen) finden Sie Backend-Beispiele und versionsspezifische Anleitungen.


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

- `<frontend_type>` - Der Frontend-Cache-Typ auf niedriger Ebene. Geben Sie einen Klassennamen an, der mit `Zend\Cache\Core` kompatibel ist.Wenn ausgelassen, wird [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) verwendet.

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
>- **Modern (Symfony Cache)**: `'backend' => 'valkey'` für Commerce-Versionen 2.4.9+ und aktuelle Patch-Versionen für die Release-Zeilen 2.4.5 bis 2.4.8, wobei Valkey das unterstützte Cache-Backend ist.
>
>Die moderne Symfony Cache-Implementierung bietet eine bessere Leistung durch PSR-6-Compliance, Igbinary-Serialisierung, Gzip-Komprimierung, Lua-Skripte und persistente Verbindungen.

Siehe die [Laminas-Dokumentation](https://docs.laminas.dev/) für Zend-basierte Optionen. Informationen zur Konfiguration des Symfony-Caches finden Sie in den [Redis](redis-pg-cache.md) und [Valkey](valkey-pg-cache.md) Artikeln in dieser Dokumentation.
