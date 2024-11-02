---
title: env.php-Referenz
description: Sehen Sie sich eine Liste der Werte für die Datei env.php an.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# env.php-Referenz

Die Datei `env.php` enthält die folgenden Abschnitte:

| Name | Beschreibung |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Einstellungen für den Administratorbereich |
| `cache` | Umleitungsseite und Standardcache konfigurieren |
| `cache_types` | Cachespeichereinstellungen |
| `consumers_wait_for_messages` | Konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten |
| `cron` | Cron-Aufträge aktivieren oder deaktivieren |
| `crypt` | Der Verschlüsselungsschlüssel für kryptografische Funktionen |
| `db` | Einstellungen für die Datenbankverbindung |
| `default_connection` | Standardverbindung für Nachrichtenwarteschlangen |
| `directories` | Zuordnungseinstellungen für Commerce-Ordner |
| `downloadable_domains` | Liste der herunterladbaren Domains |
| `install` | Installationsdatum |
| `lock` | Provider-Einstellungen sperren |
| `MAGE_MODE` | Der [Anwendungsmodus](../bootstrap/application-modes.md) |
| `queue` | [Einstellungen für Nachrichtenwarteschlangen](../queues/manage-message-queues.md) |
| `resource` | Zuordnung des Ressourcennamens zu einer Verbindung |
| `session` | Sitzungsspeicherdaten |
| `system` | Deaktiviert das Feld zur Bearbeitung im Admin |
| `x-frame-options` | Einstellung für [x-frame-options][x-frame-options] |

## Backend

Konfigurieren Sie den **frontName** für die Commerce-Admin-URL mithilfe des Knotens `backend` in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Konfigurieren Sie die Seite &quot;Umkehren&quot;und die standardmäßige Zwischenspeicherung mithilfe des Knotens &quot;`cache`&quot;in der Datei &quot;`env.php`&quot;.

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

Erfahren Sie mehr über verschiedene [Cache-Typen](../cli/manage-cache.md).

## consumer_wait_for_messages

Geben Sie an, ob der Abruf von Nachrichten durch den Verbraucher fortgesetzt werden soll, wenn die Anzahl der verarbeiteten Nachrichten unter dem Wert `max_messages` liegt. Der Standardwert ist `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Die folgenden Optionen sind verfügbar:

- `1`—Verbraucher verarbeiten weiterhin Nachrichten aus der Nachrichtenwarteschlange, bis sie den in der Datei `env.php` angegebenen `max_messages` -Wert erreichen, bevor sie die TCP-Verbindung schließen und den Verbraucherprozess beenden. Wenn die Warteschlange leer ist, bevor der `max_messages` -Wert erreicht wird, wartet der Verbraucher, bis weitere Nachrichten eintreffen.

  Wir empfehlen diese Einstellung für große Händler, da ein konstanter Nachrichtenfluss erwartet wird und Verzögerungen bei der Verarbeitung unerwünscht sind.

- `0` - Die Verbraucher verarbeiten verfügbare Nachrichten in der Warteschlange, schließen die TCP-Verbindung und beenden sie. Die Verbraucher warten nicht darauf, dass zusätzliche Nachrichten in die Warteschlange gelangen, selbst wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als der in der Datei `env.php` angegebene Wert `max_messages` . Dies kann dazu beitragen, Probleme mit Cron-Aufträgen zu verhindern, die durch lange Verzögerungen bei der Verarbeitung von Nachrichtenwarteschlangen verursacht werden.

  Wir empfehlen diese Einstellung für kleinere Händler, die keinen konstanten Nachrichtenfluss erwarten und im Gegenzug für geringfügige Verarbeitungsverzögerungen Rechenressourcen sparen möchten, wenn es für Tage keine Nachrichten geben könnte.

## cron

Aktivieren oder deaktivieren Sie Cron-Aufträge für die Commerce-Anwendung. Standardmäßig sind Cron-Aufträge aktiviert. Um sie zu deaktivieren, fügen Sie die Konfiguration `cron` zur Datei `env.php` hinzu und setzen Sie den Wert auf `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Seien Sie vorsichtig, wenn Sie Cron-Aufträge deaktivieren. Wenn sie deaktiviert sind, werden die für die Commerce-Anwendung erforderlichen wesentlichen Prozesse nicht ausgeführt.

Erfahren Sie mehr über [Crons](../cli/configure-cron-jobs.md).

## crypt

Commerce verwendet einen Verschlüsselungsschlüssel, um Kennwörter und andere vertrauliche Daten zu schützen. Dieser Schlüssel wird während des Installationsprozesses generiert.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Weitere Informationen zu [Verschlüsselungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) finden Sie im _Commerce-Benutzerhandbuch_.

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

Definiert die Standardverbindung für Nachrichtenwarteschlangen. Der Wert kann `db`, `amqp` oder ein benutzerdefiniertes Warteschlangensystem wie `redismq` sein. Wenn Sie einen anderen Wert als `db` angeben, muss die Nachrichtenwarteschlangensoftware zuerst installiert und konfiguriert werden. Andernfalls werden Nachrichten nicht korrekt verarbeitet.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Wenn in der System-Datei `env.php` der Wert `queue/default_connection` angegeben ist, wird diese Verbindung für alle Nachrichtenwarteschlangen über das System verwendet, es sei denn, eine bestimmte Verbindung ist in einer Datei `queue_topology.xml`, `queue_publisher.xml` oder `queue_consumer.xml` definiert.
Wenn beispielsweise `queue/default_connection` in `env.php` den Wert `amqp` hat, aber in den XML-Dateien der Warteschlangenkonfiguration eines Moduls eine Verbindung mit dem Wert `db` angegeben ist, verwendet das Modul MySQL als Nachrichtenbroker.

## Verzeichnisse

Optionale Ordnerzuordnungsoptionen, die festgelegt werden müssen, wenn der Webserver für die Bereitstellung der Commerce-App im Ordner &quot;`/pub`&quot;konfiguriert ist, um [verbesserte Sicherheit](../../installation/tutorials/docroot.md) zu gewährleisten.

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

Erfahren Sie mehr über [herunterladbare Domänen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## install

Das Installationsdatum der Commerce-Anwendung.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## lock

Die Einstellungen des Sperranbieters werden mit dem Knoten `lock` konfiguriert.

Erfahren Sie mehr über die [Konfiguration des Sperranbieters](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

Der Bereitstellungsmodus kann in diesem Knoten konfiguriert werden.

```conf
'MAGE_MODE' => 'developer'
```

Erfahren Sie mehr über [Anwendungsmodi](../cli/set-mode.md).

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

Erfahren Sie mehr über [Nachrichtenwarteschlange][message-queue].

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

Sitzungskonfigurationen werden im Knoten `session` gespeichert.

```conf
'session' => [
  'save' => 'files'
],
```

Erfahren Sie mehr über [Sitzung](../storage/sessions.md).

## x-frame-options

Die Kopfzeile für X-Frame-Optionen kann mithilfe dieses Knotens konfiguriert werden.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Erfahren Sie mehr über [x-frame-options](../security/xframe-options.md).

## System

Unter Verwendung dieses Knotens sperrt Commerce die Konfigurationswerte in der Datei `env.php` und deaktiviert dann das Feld im Admin.

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

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
