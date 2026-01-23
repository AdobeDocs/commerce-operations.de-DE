---
title: env.php-Referenz
description: Erfahren Sie mehr über die Konfigurationswerte und -abschnitte der Datei env.php in Adobe Commerce. Erkunden Sie Umgebungseinstellungen und Konfigurationsoptionen.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---

# env.php-Referenz

Die `env.php`-Datei enthält die folgenden Abschnitte:

| -Name | Beschreibung |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Einstellungen für den Admin-Bereich |
| `cache` | Konfigurieren der Redix-Seite und des Standard-Caches |
| `cache_types` | Cache-Speichereinstellungen |
| `consumers_wait_for_messages` | Konfigurieren, wie Verbraucher Nachrichten aus der Nachrichtenwarteschlange verarbeiten |
| `cron` | Aktivieren oder Deaktivieren der Cron-Aufträge |
| `crypt` | Der Verschlüsselungsschlüssel für kryptografische Funktionen |
| `db` | Einstellungen für die Datenbankverbindung |
| `default_connection` | Standardverbindung für Nachrichtenwarteschlangen |
| `directories` | Zuordnungseinstellungen für Commerce-Ordner |
| `downloadable_domains` | Liste der herunterladbaren Domains |
| `install` | Das Installationsdatum |
| `lock` | Provider-Einstellungen sperren |
| `MAGE_MODE` | Der [Anwendungsmodus](../bootstrap/application-modes.md) |
| `queue` | Einstellungen [Nachrichtenwarteschlangen](../queues/manage-message-queues.md) |
| `resource` | Zuordnung des Ressourcennamens zu einer Verbindung |
| `session` | Sitzungsspeicherdaten |
| `system` | Deaktiviert das Feld für die Bearbeitung im Admin-Bereich |
| `x-frame-options` | Einstellung für [x-frame-options](../security/xframe-options.md) |

## Backend

Konfigurieren Sie **frontName** für die Commerce Admin-URL unter Verwendung des `backend` Knotens in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## Cache

Konfigurieren Sie die Redis-Seite und das Standard-Caching mithilfe `cache` Knotens in der `env.php`.

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

Alle Konfigurationen der Cache-Typen sind über diesen Knoten verfügbar.

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

Weitere Informationen zu den verschiedenen [Cache-Typen](../cli/manage-cache.md).

## consumers_wait_for_messages

Geben Sie an, ob Verbraucher weiterhin Nachrichten abfragen sollen, wenn die Anzahl der verarbeiteten Nachrichten kleiner als der `max_messages` ist. Der Standardwert ist `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Die folgenden Optionen sind verfügbar:

- `1` - Verbraucher verarbeiten weiterhin Nachrichten aus der Nachrichtenwarteschlange, bis der in der `max_messages` angegebene `env.php` erreicht ist, bevor sie die TCP-Verbindung schließen und den Verbraucherprozess beenden. Wenn die Warteschlange geleert wird, bevor der `max_messages` erreicht wird, wartet der Verbraucher, bis weitere Nachrichten eingehen.

  Wir empfehlen diese Einstellung für große Händler, da ein konstanter Nachrichtenfluss erwartet wird und Verzögerungen bei der Verarbeitung unerwünscht sind.

- `0` - Verbraucher verarbeiten verfügbare Nachrichten in der Warteschlange, schließen die TCP-Verbindung und beenden sie. Verbraucher warten nicht auf den Eintritt zusätzlicher Nachrichten in die Warteschlange, selbst wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als der in der `max_messages` angegebene `env.php`. Dadurch können Probleme mit Cron-Aufträgen vermieden werden, die durch lange Verzögerungen bei der Verarbeitung der Nachrichtenwarteschlange verursacht werden.

  Wir empfehlen diese Einstellung kleineren Händlern, die keinen konstanten Nachrichtenfluss erwarten und lieber Computing-Ressourcen sparen möchten, im Gegenzug für kleinere Verarbeitungsverzögerungen, wenn tagelang keine Nachrichten verfügbar sein könnten.

## Cron

Aktivieren oder Deaktivieren von Cron-Aufträgen für das Commerce-Programm. Standardmäßig sind Cron-Aufträge aktiviert. Um sie zu deaktivieren, fügen Sie die `cron`-Konfiguration zur `env.php` hinzu und setzen den Wert auf `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Seien Sie vorsichtig, wenn Sie Cron-Aufträge deaktivieren. Wenn sie deaktiviert sind, werden wesentliche Prozesse, die für das Commerce-Programm erforderlich sind, nicht ausgeführt.

Weitere Informationen zu [Crons](../cli/configure-cron-jobs.md).

## Krypta

Commerce verwendet einen Verschlüsselungsschlüssel zum Schutz von Kennwörtern und anderen vertraulichen Daten. Dieser Schlüssel wird während des Installationsprozesses generiert.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Weitere Informationen zu [Verschlüsselungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) finden Sie im _Commerce-Benutzerhandbuch_.

## dB

In diesem Knoten sind alle Datenbankkonfigurationen verfügbar.

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

Definiert die Standardverbindung für Nachrichtenwarteschlangen. Der Wert kann `db`, `amqp`, `stomp` oder ein benutzerdefiniertes Warteschlangensystem wie `redismq` sein. Wenn Sie einen anderen Wert als `db` angeben, muss zuerst die Message Queue-Software installiert und konfiguriert werden. Andernfalls werden die Nachrichten nicht korrekt verarbeitet.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Für STOMP (ActiveMQ Artemis):

```conf
'queue' => [
    'default_connection' => 'stomp'
]
```

Wenn `queue/default_connection` in der `env.php` angegeben ist, wird diese Verbindung für alle Meldungswarteschlangen im System verwendet, es sei denn, eine bestimmte Verbindung ist in einer `queue_topology.xml`-, `queue_publisher.xml`- oder `queue_consumer.xml` definiert.
Wenn `queue/default_connection` beispielsweise in `amqp` `env.php` ist, aber in den XML-Dateien der Warteschlangenkonfiguration eines Moduls eine `db` angegeben ist, verwendet das Modul MySQL als Nachrichtenbroker.

## Verzeichnisse

Optionale Verzeichniszuordnungsoptionen, die festgelegt werden müssen, wenn der Webserver so konfiguriert ist, dass er die Commerce-App aus dem `/pub` bereitstellt ([&#x200B; Sicherheit](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

Eine Liste der in diesem Knoten verfügbaren herunterladbaren Domains. Zusätzliche Domains können über CLI-Befehle hinzugefügt, entfernt oder aufgelistet werden.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Weitere Informationen zu &quot;[&#x200B; Domains](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## installieren

Das Installationsdatum der Commerce-Anwendung.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## Sperren

Die Einstellungen des Sperranbieters werden mithilfe des `lock`-Knotens konfiguriert.

Weitere Informationen über [Sperranbieter-Konfiguration](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

Der Bereitstellungsmodus kann in diesem Knoten konfiguriert werden.

```conf
'MAGE_MODE' => 'developer'
```

Weitere Informationen zu [Anwendungsmodi](../cli/set-mode.md).

## Warteschlange

In diesem Knoten sind Konfigurationen für die Nachrichtenwarteschlange verfügbar. Sie können RabbitMQ (AMQP) oder ActiveMQ Artemis (STOMP) als Nachrichtenbroker konfigurieren.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-broker"],
    'order.created' => [publisher="default-broker"],
  ]
]
```

Weitere Informationen über [Nachrichtenwarteschlange](https://developer.adobe.com/commerce/php/development/components/message-queues/).

## Ressource

Ressourcenkonfigurationseinstellungen sind in diesem Knoten verfügbar.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## Sitzung

Sitzungskonfigurationen werden im Knoten `session` gespeichert.

```conf
'session' => [
  'save' => 'files'
],
```

Weitere Informationen über [Sitzung](../storage/sessions.md).

## X-Frame-Options

Der X-Frame-Options-Header kann mit diesem Knoten konfiguriert werden.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Weitere Informationen zu [x-frame-options](../security/xframe-options.md).

## System

Mithilfe dieses Knotens sperrt Commerce die Konfigurationswerte in der `env.php` und deaktiviert dann das Feld in der Admin-Instanz.

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



## Variablen zur Dateikonfiguration hinzufügen

Sie können jede Konfigurationsoption (Variable mit Wert) mit Umgebungsvariablen auf Betriebssystemebene festlegen oder überschreiben.

Die `env.php` wird in einem Array mit verschachtelten Ebenen gespeichert. Um einen verschachtelten Array-Pfad in eine Zeichenfolge für OS-Umgebungsvariablen zu konvertieren, verketten Sie jeden Schlüssel im Pfad mit doppelten Unterstrichen `__`, großgeschrieben und mit dem Präfix `MAGENTO_DC_`.

Konvertieren wir beispielsweise den Sitzungsspeicher-Handler aus `env.php` Konfiguration in eine BS-Umgebungsvariable.

```conf
'session' => [
  'save' => 'files'
],
```

Verkettet mit `__` und Großbuchstaben wird `SESSION__SAVE`.

Anschließend stellen wir `MAGENTO_DC_` als Präfix voran, um den resultierenden Namen der Betriebssystemumgebungsvariablen `MAGENTO_DC_SESSION__SAVE`.

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

Als weiteres Beispiel konvertieren wir einen Optionspfad für die Skalarkonfiguration `env.php`.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>Während der Variablenname in Großbuchstaben geschrieben werden sollte, wird bei dem Wert zwischen Groß- und Kleinschreibung unterschieden und er sollte wie dokumentiert beibehalten werden.

Wir schreiben sie einfach in Großbuchstaben und setzen das Präfix `MAGENTO_DC_`, um den endgültigen `MAGENTO_DC_X-FRAME-OPTIONS` für den Betriebssystemumgebungsvariablen zu erhalten.

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>Beachten Sie, dass `env.php` Inhalt Vorrang vor den Umgebungsvariablen des Betriebssystems hat.

## Überschreiben der Dateikonfiguration mit Variablen

Um die vorhandenen `env.php`-Konfigurationsoptionen mit einer BS-Umgebungsvariablen zu überschreiben, muss das Array-Element der Konfiguration JSON-kodiert sein und als Wert der `MAGENTO_DC__OVERRIDE` OS-Variablen festgelegt sein.

Wenn `MAGENTO_DC__OVERRIDE` festgelegt ist, umgeht das Commerce-Framework die entsprechenden Werte in der `env.php` und liest die Konfiguration direkt aus der Umgebungsvariablen. Die Werte in der `env.php` bleiben unverändert, werden aber für die überschriebenen Konfigurationsabschnitte ignoriert.

>[!IMPORTANT]
>
>Die `MAGENTO_DC__OVERRIDE`-Variable umgeht die angegebenen Konfigurationsabschnitte in der `env.php`-Datei vollständig. Dieses Verhalten unterscheidet sich von einzelnen `MAGENTO_DC_`, die eine niedrigere Priorität als Werte in der `env.php` haben.

Wenn Sie mehrere Konfigurationsoptionen überschreiben müssen, stellen Sie sie alle in einem einzigen Array zusammen, bevor Sie JSON-Codierung verwenden.

Überschreiben wir beispielsweise die folgenden `env.php`:

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

Der JSON-codierte Text des obigen Arrays lautet wie folgt
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`.

Legen Sie ihn jetzt als Wert der `MAGENTO_DC__OVERRIDE`-Betriebssystemvariablen fest.

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>Stellen Sie sicher, dass das JSON-codierte Array ordnungsgemäß in Anführungszeichen gesetzt und/oder ggf. mit Escape-Zeichen versehen ist, um zu verhindern, dass das Betriebssystem die codierte Zeichenfolge beschädigt.