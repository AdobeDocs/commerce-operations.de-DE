---
title: env.php-Referenz
description: Sehen Sie sich eine Liste der Werte für die Datei env.php an.
source-git-commit: 7ecd54b40690ec046e9a3d46a6ef9ad44ffaf4ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# env.php-Referenz

Die `env.php` -Datei enthält die folgenden Abschnitte:

| Name | Beschreibung |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Einstellungen für den Admin-Bereich |
| `cache` | Umleitungsseite und Standardcache konfigurieren |
| `cache_types` | Cachespeichereinstellungen |
| `consumers_wait_for_messages` | Konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten |
| `cron` | Aktivieren oder Deaktivieren von Cron-Aufträgen |
| `crypt` | Der Verschlüsselungsschlüssel für kryptografische Funktionen |
| `db` | Einstellungen für die Datenbankverbindung |
| `default_connection` | Standardverbindung für Nachrichtenwarteschlangen |
| `directories` | Zuordnungseinstellungen für Commerce-Ordner |
| `downloadable_domains` | Liste der herunterladbaren Domains |
| `install` | Installationsdatum |
| `lock` | Provider-Einstellungen sperren |
| `MAGE_MODE` | Die [Anwendungsmodus](../bootstrap/application-modes.md) |
| `queue` | [Nachrichtenwarteschlangen](../queues/manage-message-queues.md) settings |
| `resource` | Zuordnung des Ressourcennamens zu einer Verbindung |
| `session` | Sitzungsspeicherdaten |
| `system` | Deaktiviert das Feld zur Bearbeitung im Admin |
| `x-frame-options` | Einstellung für [x-frame-options][x-frame-options] |

## Backend

Konfigurieren Sie die **frontName** für die Commerce-Admin-URL mit der `backend` Knoten in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Umleitungsseite und Standard-Zwischenspeicherung mithilfe von konfigurieren `cache` Knoten in `env.php` -Datei.

```conf
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
]
```

Weitere Informationen finden Sie unter [Redis-Konfiguration](../cache/redis-pg-cache.md).

## cache_types

Alle Konfigurationen der Cache-Typen sind in diesem Knoten verfügbar.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

Weitere Informationen zu verschiedenen [Cachetypen](../cli/manage-cache.md).

## consumer_wait_for_messages

Geben Sie an, ob Verbraucher die Abfrage von Nachrichten fortsetzen sollen, wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als die `max_messages` -Wert. Der Standardwert ist `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Die folgenden Optionen sind verfügbar:

- `1`—Verbraucher verarbeiten weiterhin Nachrichten aus der Nachrichtenwarteschlange, bis sie die `max_messages` Wert, der in der Variablen `env.php` -Datei vor dem Schließen der TCP-Verbindung und dem Beenden des Verbraucherprozesses. Wenn die Warteschlange vor dem Erreichen der `max_messages` -Wert, wartet der Verbraucher auf mehr Nachrichten.

   Wir empfehlen diese Einstellung für große Händler, da ein konstanter Nachrichtenfluss erwartet wird und Verzögerungen bei der Verarbeitung unerwünscht sind.

- `0`—Verbraucher verarbeiten verfügbare Nachrichten in der Warteschlange, schließen die TCP-Verbindung und beenden sie. Die Verbraucher warten nicht darauf, dass zusätzliche Nachrichten in die Warteschlange gelangen, selbst wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als die Anzahl der `max_messages` Wert, der in der Variablen `env.php` -Datei. Dies kann dazu beitragen, Probleme mit Cron-Aufträgen zu verhindern, die durch lange Verzögerungen bei der Verarbeitung von Nachrichtenwarteschlangen verursacht werden.

   Wir empfehlen diese Einstellung für kleinere Händler, die keinen konstanten Nachrichtenfluss erwarten und im Gegenzug für geringfügige Verarbeitungsverzögerungen Rechenressourcen sparen möchten, wenn es für Tage keine Nachrichten geben könnte.

## cron

Aktivieren oder deaktivieren Sie Cron-Aufträge für die Commerce-Anwendung. Standardmäßig sind Cron-Aufträge aktiviert. Um sie zu deaktivieren, fügen Sie die `cron` -Konfiguration `env.php` und setzen Sie den Wert auf `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Seien Sie vorsichtig, wenn Sie Cron-Aufträge deaktivieren. Wenn sie deaktiviert sind, werden die für die Commerce-Anwendung erforderlichen wesentlichen Prozesse nicht ausgeführt.

Weitere Informationen [Krone](../cli/configure-cron-jobs.md).

## crypt

Commerce verwendet einen Verschlüsselungsschlüssel, um Passwörter und andere vertrauliche Daten zu schützen. Dieser Schlüssel wird während des Installationsprozesses generiert.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Weitere Informationen [Verschlüsselungsschlüssel](https://docs.magento.com/user-guide/system/encryption-key.html) im _Commerce-Benutzerhandbuch_.

## db

Alle Datenbankkonfigurationen sind in diesem Knoten verfügbar.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Definiert die Standardverbindung für Nachrichtenwarteschlangen. Der Wert kann `db`, `amqp`oder ein benutzerdefiniertes Warteschlangensystem wie `redismq`. Wenn Sie einen anderen Wert als `db`muss die Nachrichtenwarteschlangensoftware zuerst installiert und konfiguriert werden. Andernfalls werden Nachrichten nicht korrekt verarbeitet.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Wenn `queue/default_connection` im System angegeben ist `env.php` -Datei, wird diese Verbindung für alle Nachrichtenwarteschlangen über das System verwendet, es sei denn, eine bestimmte Verbindung ist in einer `queue_topology.xml`, `queue_publisher.xml` oder `queue_consumer.xml` -Datei.
Wenn beispielsweise `queue/default_connection` is `amqp` in `env.php` aber ein `db` -Verbindung wird in den XML-Dateien der Warteschlangenkonfiguration eines Moduls angegeben. Das Modul verwendet MySQL als Nachrichtenbroker.

## Verzeichnisse

Optionale Ordnerzuordnungsoptionen, die festgelegt werden müssen, wenn der Webserver für die Bereitstellung der Commerce-App über die `/pub` Verzeichnis für [verbesserte Sicherheit][change-docroot-to-pub].

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

Eine Liste der herunterladbaren Domains, die in diesem Knoten verfügbar sind. Zusätzliche Domänen können mithilfe von CLI-Befehlen hinzugefügt, entfernt oder aufgelistet werden.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Weitere Informationen [Herunterladbare Domänen](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## install

Das Installationsdatum der Commerce-Anwendung.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## lock

Die Einstellungen des Sperranbieters werden mithilfe der Variablen `lock` Knoten.

Weitere Informationen [Anbieterkonfiguration sperren][lock-provider-config].

## MAGE_MODE

Der Bereitstellungsmodus kann in diesem Knoten konfiguriert werden.

```conf
'MAGE_MODE' => 'developer'
```

Weitere Informationen [Anwendungsmodi](../cli/set-mode.md).

## queue

Die Konfigurationen der Nachrichtenwarteschlange sind in diesem Knoten verfügbar.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

Weitere Informationen [Nachrichtenwarteschlange][message-queue].

## resource

Die Einstellungen für die Ressourcenkonfiguration sind in diesem Knoten verfügbar.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

Sitzungskonfigurationen werden im `session` Knoten.

```conf
'session' => [
  'save' => 'files'
],
```

Weitere Informationen [Sitzung](../storage/sessions.md).

## x-frame-options

Die Kopfzeile für X-Frame-Optionen kann mithilfe dieses Knotens konfiguriert werden.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Weitere Informationen [x-frame-options](../security/xframe-options.md).

## System

Unter Verwendung dieses Knotens sperrt Commerce die Konfigurationswerte im `env.php` und deaktiviert dann das Feld im Admin.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

Weitere Informationen finden Sie unter [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[change-docroot-to-pub]: https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html
[encryption-key]: https://docs.magento.com/user-guide/system/encryption-key.html
[lock-provider-config]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-lock.html
[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
