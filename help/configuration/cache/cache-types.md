---
title: Cachetypen
description: Verknüpfen Sie Cache-Frontends mit Cache-Typen.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Cachetypen

Die folgenden Schritte zeigen, wie Sie das Cache-Frontend mit einem Cache-Typ verknüpfen.

## Schritt 1: Definieren eines Cache-Frontend

Die Commerce-Anwendung verfügt über ein Cache-Frontend mit dem Wert `default` , das Sie für jeden beliebigen Cache-Typ [2} verwenden können. ](../cli/manage-cache.md#clean-and-flush-cache-types) In diesem Abschnitt wird beschrieben, wie Sie optional ein Cache-Frontend mit einem anderen Namen definieren, was bei der erwarteten Anpassung Ihres Frontend vorzuziehen ist.

>[!INFO]
>
>Um den Cache-Typ `default` zu verwenden, müssen Sie `env.php` überhaupt nicht ändern. Sie ändern Commerces globale `di.xml`. Siehe [Optionen für den Cache auf niedriger Ebene](cache-options.md).

Sie müssen ein benutzerdefiniertes Cache-Frontend entweder `app/etc/env.php` oder das globale Commerce-Frontend `app/etc/di.xml` angeben.

Das folgende Beispiel zeigt, wie Sie es in der Datei `env.php` definieren, die die Datei `di.xml` überschreibt:

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

Dabei ist `<unique frontend id>` ein eindeutiger Name, der Ihr Frontend identifiziert, und `<cache options>` sind Optionen, die in den für jeden Caching-Typ (Datenbank, Redis usw.) spezifischen Themen besprochen werden.

## Schritt 2: Cache konfigurieren

Sie können die Konfigurationsoptionen für den Frontend- und Backend-Cache in `env.php` oder `di.xml` angeben. Diese Aufgabe ist optional.

Beispiel für `env.php`:

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

- `<frontend_type>` ist der Frontend-Cache-Typ der unteren Ebene. Geben Sie den Namen einer Klasse an, die mit `Zend\Cache\Core` kompatibel ist.
Wenn Sie `<frontend_type>` weglassen, wird [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) verwendet.

- `<frontend_option>`, `<frontend_option_value>` sind der Name und der Wert der Optionen, die das Commerce-Framework bei seiner Erstellung als assoziatives Array an den Frontend-Cache übergibt.
- `<backend_type>` ist der Backend-Cache-Typ der unteren Ebene. Geben Sie den Namen einer Klasse an, die mit `Zend_Cache_Backend` kompatibel ist und `Zend_Cache_Backend_Interface` implementiert.
- `<backend_option>` und `<backend_option_value>` sind der Name und der Wert der Optionen, die das Commerce-Framework bei seiner Erstellung als assoziatives Array an den Backend-Cache übergibt.

Aktuelle Informationen zu Zend finden Sie in der [Laminas-Dokumentation](https://docs.laminas.dev/) .
