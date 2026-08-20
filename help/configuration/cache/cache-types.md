---
title: Konfigurieren von Cache-Frontends und -Typen
description: Erfahren Sie, wie Sie Cache-Frontends definieren und sie mit Cache-Typen in Adobe Commerce verknüpfen. Erkunden Sie die Konfigurationssyntax für env.php.
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
source-git-commit: 3652976a8db3d0bb19ff9cd06adb3a7736c89539
workflow-type: tm+mt
source-wordcount: 398
ht-degree: 0%

---

# Konfigurieren von Cache-Frontends und -Typen

Ein Cache-Frontend verbindet Commerce-Cache-Typen mit dem Cache-Speicher. Sie können mehrere Frontends definieren und jedem Frontend spezifische Cache-Typen zuweisen.

>[!BEGINSHADEBOX]

Verwenden Sie die folgende Beziehung, um zu bestimmen, wo ein Cache-Typ seine Daten speichert:

Cache-Typ → Cache-Frontend → Cache-Backend

>[!ENDSHADEBOX]

Einen Überblick über die Commerce-Caching-Architektur finden Sie unter [Übersicht über Caching und Konfigurationsoptionen](caching-overview.md).

>[!NOTE]
>
>Verwenden Sie für Adobe Commerce in der Cloud[Infrastruktur die Cloud-Bereitstellungskonfiguration &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml) im Cloud-Handbuch beschrieben. `app/etc/env.php` nicht direkt bearbeiten. Bereitstellungs-Tools generieren diese Datei und können manuelle Änderungen überschreiben.

## Standard-Frontend verwenden

Commerce bietet ein standardmäßiges Frontend, das von allen Cache-Typen verwendet werden kann.

In den meisten Fällen ist es nicht erforderlich, ein benutzerdefiniertes Frontend zu definieren. Wenn alle Cache-Typen dieselben Backend- und Backend-Optionen verwenden können, verwenden Sie das Standard-Frontend und konfigurieren Sie sein Backend. Siehe [Cache-Backend](cache-options.md)Optionen) für die Backend-spezifische Konfiguration.

Für Adobe Commerce-Versionen vor 2.4.9 verwendet das Standard-Frontend die veraltete Zend-basierte Cache-Implementierung. Das `Magento\Framework\Cache\Core` Frontend erweitert `Zend_Cache_Core`. Adobe Commerce 2.4.9 und höher verwenden die moderne Symfony-Implementierung. Eine versionsspezifische Anleitung finden [&#x200B; unter &#x200B;](cache-options.md)Cache-Backend-Optionen“.

## Definieren eines benutzerdefinierten Frontends

Verwenden Sie ein benutzerdefiniertes Cache-Frontend, wenn ein oder mehrere Cache-Typen Backend-Einstellungen benötigen, die sich von denen des Standard-Frontends unterscheiden.

Definieren Sie für On-Premise-Bereitstellungen das Frontend in `app/etc/env.php`. Weisen Sie ihm dann einen oder mehrere Cache-Typen zu:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

Dabei gilt:

- `<frontend-id>` ist die eindeutige Kennung für das Frontend, z. B. `default` oder `page_cache`.
- `<backend-type>` identifiziert das vom Frontend verwendete Backend. Der unterstützte Wert hängt von der Adobe Commerce-Version und dem ausgewählten Backend ab.
- `backend_options` enthält Optionen für das ausgewählte Backend.
- `<cache-type-id>` ist ein Commerce-Cache-Typ, z. B. `config`, `layout`, `block_html` oder `full_page`.


Backend-Typen, unterstützte Optionen und versionsspezifische Konfigurationsbeispiele finden Sie unter [Cache-Backend-Optionen](cache-options.md).

## Zuweisen eines Cache-Typs zu einem Frontend

Die `type`-Konfiguration ordnet einen Cache-Typ einem Frontend zu:

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

In diesem Beispiel weist Commerce dem `page_cache`-Frontend den Cache-Typ `full_page` zu. Das Frontend bestimmt, welche Backend-Konfiguration diesen Cache-Typ speichert.

>[!NOTE]
>
>Der `full_page` stellt einen Cache-Typ einer Commerce-Anwendung dar. Das Caching ganzer Seiten über Varnish oder Fastly ist eine separate Caching-Ebene. Siehe [Übersicht über Caching und Konfigurationsoptionen](caching-overview.md).

>[!MORELIKETHIS]
>
>- [L2-Cache-Konfiguration zur Leistungsoptimierung](level-two-cache.md)
>- [Cache verwalten](../cli/manage-cache.md)
