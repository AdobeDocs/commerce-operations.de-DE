---
title: Cache-Typen
description: Zuordnen von Cache-Frontends zu Cache-Typen.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Cache-Typen

In den folgenden Schritten wird beschrieben, wie Sie das Cache-Frontend einem Cache-Typ zuordnen.

## Schritt 1: Cache-Frontend definieren

Das Commerce-Programm verfügt über ein `default` Cache-Frontend, das Sie für jeden [Cache-Typ“ ](../cli/manage-cache.md#clean-and-flush-cache-types) können. In diesem Abschnitt wird beschrieben, wie Sie optional ein Cache-Frontend mit einem anderen Namen definieren. Dies ist vorzuziehen, wenn Sie Ihr Frontend anpassen möchten.

>[!INFO]
>
>Um den `default` Cache-Typ zu verwenden, müssen Sie `env.php` überhaupt nicht ändern. Sie ändern die globale `di.xml` von Commerce. Siehe [Cache-Optionen auf niedriger Ebene](cache-options.md).

Sie müssen ein benutzerdefiniertes Cache-Frontend entweder `app/etc/env.php` oder die globale `app/etc/di.xml` von Commerce angeben.

Das folgende Beispiel zeigt, wie Sie sie in der `env.php` definieren, wodurch die `di.xml` überschrieben wird:

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

Dabei sind `<unique frontend id>` ein eindeutiger Name zur Identifizierung Ihres Frontends und `<cache options>` Optionen, die in den für die einzelnen Arten von Caching spezifischen Themen (Datenbank, Redis usw.) erläutert werden.

## Schritt 2: Konfigurieren des Cache

Sie können die Konfigurationsoptionen für Frontend- und Backend-Cache in `env.php` oder `di.xml` angeben. Diese Aufgabe ist optional.

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

Hierbei gilt

- `<frontend_type>` ist der Frontend-Cache-Typ auf niedriger Ebene. Geben Sie den Namen einer mit `Zend\Cache\Core` kompatiblen Klasse an.
Wenn Sie `<frontend_type>` auslassen, wird [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) verwendet.

- `<frontend_option>` sind `<frontend_option_value>` der Name und der Wert von Optionen, die das Commerce-Framework bei seiner Erstellung als assoziatives Array an den Frontend-Cache übergibt.
- `<backend_type>` ist der Backend-Cache-Typ auf niedriger Ebene. Geben Sie den Namen einer Klasse an, die mit `Zend_Cache_Backend` kompatibel ist und `Zend_Cache_Backend_Interface` implementiert.
- `<backend_option>` und `<backend_option_value>` sind der Name und der Wert von Optionen, die das Commerce-Framework bei seiner Erstellung als assoziatives Array an den Backend-Cache übergibt.

Die neuesten [ Informationen finden Sie in ](https://docs.laminas.dev/)Laminas-Dokumentation).
