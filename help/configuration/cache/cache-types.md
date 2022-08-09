---
title: Cachetypen
description: Verknüpfen Sie Cache-Frontends mit Cache-Typen.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Cachetypen

Die folgenden Schritte zeigen, wie Sie das Cache-Frontend mit einem Cache-Typ verknüpfen.

## Schritt 1: Cache-Frontend definieren

Die Commerce-Anwendung verfügt über eine `default` Cache-Frontend, das Sie für beliebige [Cache-Typ](../cli/manage-cache.md#clean-and-flush-cache-types). In diesem Abschnitt wird beschrieben, wie Sie optional ein Cache-Frontend mit einem anderen Namen definieren, was bei der erwarteten Anpassung Ihres Frontend vorzuziehen ist.

>[!INFO]
>
>So verwenden Sie die `default` Cache-Typ, müssen Sie nicht ändern `env.php` überhaupt; Sie ändern die globale `di.xml`. Siehe [Optionen für den Cache auf niedriger Ebene](cache-options.md).

Sie müssen ein benutzerdefiniertes Cache-Frontend angeben, entweder `app/etc/env.php` oder die globale `app/etc/di.xml`.

Das folgende Beispiel zeigt, wie Sie ihn im `env.php` -Datei, die die `di.xml` Datei:

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
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Wo `<unique frontend id>` ist ein eindeutiger Name zur Identifizierung Ihres Frontend und `<cache options>` sind Optionen, die in den Themen besprochen werden, die für jeden Caching-Typ (Datenbank, Redis usw.) spezifisch sind.

## Schritt 2: Cache konfigurieren

Die Konfigurationsoptionen für den Frontend- und Backend-Cache können in `env.php` oder `di.xml`. Diese Aufgabe ist optional.

`env.php` Beispiel:

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

where

- `<frontend_type>` ist der Typ des Frontend-Cache auf niedriger Ebene. Geben Sie den Namen einer Klasse an, die mit `Zend\Cache\Core`.
Wenn Sie weglassen `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) verwendet.

- `<frontend_option>`, `<frontend_option_value>` sind der Name und der Wert der Optionen, die das Commerce-Framework bei seiner Erstellung als assoziatives Array an den Frontend-Cache übergibt.
- `<backend_type>` ist der Backend-Cache-Typ der unteren Ebene. Geben Sie den Namen einer Klasse an, die mit `Zend_Cache_Backend` und die `Zend_Cache_Backend_Interface`.
- `<backend_option>` und `<backend_option_value>` sind der Name und der Wert der Optionen, die das Commerce-Framework bei seiner Erstellung als assoziatives Array übergibt, um den Cache zu sichern.

Siehe [Laminatdokumentation](https://docs.laminas.dev/) für die neuesten Zend-Informationen.
