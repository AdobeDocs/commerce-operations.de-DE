---
title: '[!DNL Data Migration Tool] technische Spezifikation'
description: Erfahren Sie mehr über die Implementierungsdetails von  [!DNL Data Migration Tool]  und wie Sie sie bei der Übertragung von Daten zwischen Magento 1 und Magento 2 erweitern können.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool] technische Spezifikation

In diesem Abschnitt werden [!DNL Data Migration Tool] Implementierungsdetails und die Erweiterung ihrer Funktionalität beschrieben.

## Repositorys

Informationen zum Zugriff auf den [!DNL Data Migration Tool]-Quell-Code finden Sie unter GitHub [Repository](https://github.com/magento/data-migration-tool).

## Systemanforderungen

Die [Systemanforderungen](../../installation/system-requirements.md) für die [!DNL Data Migration Tool] entsprechen denen für Magento 2.

## Interne Struktur

### Verzeichnisstruktur

Das folgende Diagramm zeigt die Verzeichnisstruktur von [!DNL Data Migration Tool]:

```
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## Einstiegspunkt

Das Skript, das den Migrationsprozess ausführt, befindet sich unter: `magento-root/bin/magento`.

## Konfiguration

Das Schema für die `config.xsd` befindet sich im `etc/`. Die Standardkonfigurationsdatei (`config.xml.dist`) wird für jede Version von Magento 1.x erstellt. Er befindet sich in einem separaten Verzeichnis unter `etc/`.

Die standardmäßige Konfigurationsdatei kann durch eine benutzerdefinierte Datei ersetzt werden (siehe [Befehlssyntax](migrate-data/overview.md#command-syntax)).

Die Konfigurationsdatei weist die folgende Struktur auf:

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* Schritte : Beschreibt alle Schritte, die während der Migration verarbeitet werden

* Quelle - Konfiguration für die Datenquelle. Verfügbare Quelltypen: Datenbank

* Ziel - Konfiguration für das Datenziel. Verfügbare Zieltypen: Datenbank

* options - Liste der Parameter. Enthält sowohl obligatorische (map_file, settings_map_file, bulk_size) als auch optionale (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file) Parameter

Option „Präfix ändern“, falls Magento mit Präfix in Datenbanktabellen installiert wurde Sie kann für Magento 1- und Magento 2-Datenbanken festgelegt werden. Verwenden Sie die Konfigurationsoptionen „source_prefix“ und „dest_prefix“ entsprechend.

Auf die Konfigurationsdaten kann mit der `\Migration\Config`-Klasse zugegriffen werden.

## Verfügbare Schritte

| Dokument | Feld |
|---|---|
| `step` | Knoten der zweiten Ebene im Knoten Schritte . Die Beschreibung des relevanten Schritts muss im Attribut `title` angegeben werden. |
| `integrity` | Gibt die PHP-Klasse an, die für die Integritätsprüfung verantwortlich ist. Vergleicht die Namen, Typen und anderen Informationen der Tabellenfelder, um die Kompatibilität zwischen Magento 1- und 2-Datenstrukturen zu überprüfen. |
| `data` | Gibt die PHP-Klasse an, die für die Datenüberprüfung verantwortlich ist. Überträgt die Daten tabellarisch von Magento 1 nach Magento 2. |
| `volume` | Gibt die PHP-Klasse an, die für die Lautstärkeprüfung verantwortlich ist. Vergleicht die Anzahl der Datensätze zwischen Tabellen, um zu überprüfen, ob die Übertragung erfolgreich war. |
| `delta` | Gibt die PHP-Klasse an, die für die Delta-Prüfung verantwortlich ist. Überträgt das Delta von Magento 1 nach der vollständigen Datenmigration an Magento 2. |

## Source-Datenbankinformationsattribute

| Dokument | Feld | Erforderlich? |
|---|---|---|
| `name` | Datenbankname des Magento 1-Servers. | Ja |
| `host` | Host-IP-Adresse des Magento 1-Servers | Ja |
| `port` | Port-Nummer des Magento 1-Servers. | Nein |
| `user` | Benutzername des Magento 1-Datenbankservers. | Ja |
| `password` | Kennwort für den Magento 1-Datenbankserver. | Ja |
| `ssl_ca` | Pfad zur Datei der SSL-Zertifizierungsstelle. | Nein |
| `ssl_cert` | Pfad zur SSL-Zertifikatdatei. | Nein |
| `ssl_key` | Pfad zur SSL-Schlüsseldatei. | Nein |

## Informationsattribute zur Zieldatenbank

| Dokument | Feld | Erforderlich? |
|---|---|---|
| `name` | Datenbankname des Magento 2-Servers. | Ja |
| `host` | Host-IP-Adresse des Magento 2-Servers | Ja |
| `port` | Port-Nummer des Magento 2-Servers | Nein |
| `user` | Benutzername des Magento 2-Datenbankservers. | Ja |
| `password` | Kennwort für den Magento 2-Datenbankserver. | Ja |
| `ssl_ca` | Pfad zur Datei der SSL-Zertifizierungsstelle. | Nein |
| `ssl_cert` | Pfad zur SSL-Zertifikatdatei. | Nein |
| `ssl_key` | Pfad zur SSL-Schlüsseldatei. | Nein |

## Verbinden mit dem TLS-Protokoll

Sie können auch über das TLS-Protokoll eine Verbindung zu einer Datenbank herstellen (d. h. mithilfe öffentlicher/privater kryptografischer Schlüssel). Fügen Sie dem `database`-Element die folgenden optionalen Attribute hinzu:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Beispiel:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Schrittinterne

Der Migrationsprozess besteht aus Schritten.

Der Schritt ist eine Einheit, die die für die Migration einiger separierter Daten erforderlichen Funktionen bereitstellt. Ein Schritt kann aus einem oder mehreren Schritten bestehen (Integritätsprüfung, Daten-, Volume- und Delta-Prüfung).

Standardmäßig gibt es mehrere Schritte ([Map](#map-step), [EAV](#eav), [URL-](#url-rewrite-step) usw.). Sie können optional auch eigene Schritte hinzufügen.

Die mit Schritten zusammenhängenden Klassen befinden sich im Verzeichnis „src/migration/step“.

Um eine Step-Klasse auszuführen, muss die Klasse in der Datei config.xml definiert werden.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

Jede Staging-Klasse muss StageInterface implementieren.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

Wenn das Datenstadium Rollback unterstützt, sollte die `RollbackInterface` implementiert werden.

Die Visualisierung des laufenden Schritts wird durch die ProgressBar-Komponente von Symfony bereitgestellt (siehe [Fortschrittsleiste](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Greifen Sie in einem Schritt als LogLevelProcessor auf diese Komponente zu.

Die wichtigsten Methoden sind:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Schrittphasen

### Integritätsprüfung

In jedem Schritt muss überprüft werden, ob die Struktur der Datenquelle (standardmäßig Magento 1) und die Struktur des Datenziels (Magento 2) kompatibel sind. Andernfalls wird ein Fehler mit Entitäten angezeigt, die nicht kompatibel sind. Wenn Felder unterschiedliche Datentypen haben (dasselbe Feld hat den Dezimaldatentyp in Magento 1 und eine Ganzzahl in Magento 2), wird eine Warnmeldung angezeigt (sofern sie nicht in der Zuordnungsdatei behandelt wurde).

### Datenübertragung

Im Falle einer bestandenen Integritätsprüfung wird die Datenübertragung ausgeführt. Wenn Fehler auftreten, wird das Rollback ausgeführt, um zum vorherigen Status von Magento 2 zurückzukehren. Wenn eine Schrittklasse die `RollbackInterface` implementiert, wird die Rollback-Methode bei einem Fehler ausgeführt.

### Lautstärkeprüfung

Nach der Migration von Daten stellt die Volume-Prüfung eine zusätzliche Überprüfung bereit, um sicherzustellen, dass alle Daten korrekt übertragen wurden.

### Delta-Versand

Die Delta-Funktion ist für die Bereitstellung der restlichen Daten verantwortlich, die nach der Hauptmigration hinzugefügt wurden.

## Ausführungsmodi

Das Tool sollte in drei verschiedenen Modi in einer bestimmten Reihenfolge ausgeführt werden:

1. Einstellungen - Migration von Systemeinstellungen
1. Daten - Hauptmigration von Daten
1. Delta - Migration der übrigen Daten, die nach der Hauptmigration hinzugefügt wurden

Jeder Modus verfügt über eine eigene Liste von auszuführenden Schritten. Siehe config.xml

### Migrationseinstellungen

Der Einstellungsmigrationsmodus dieses Tools wird verwendet, um die folgenden Entitäten zu übertragen:

1. Websites, Stores, Store-Ansichten.
1. Speicherkonfiguration (hauptsächlich Speicher->Konfiguration in M2 oder System->Konfiguration in M1)

Alle Speicherkonfigurationen behalten ihre Daten in der Tabelle core_config_data der Datenbank bei. Die Datei settings.xml enthält Regeln für diese Tabelle, die während des Migrationsprozesses angewendet werden. In dieser Datei werden Einstellungen beschrieben, die ignoriert, umbenannt oder in ihren Werten geändert werden sollten. Die Datei settings.xml weist die folgende Struktur auf:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

Unter dem Knoten `<key>` gibt es Regeln, die mit der Spalte „Pfad“ in der `core_config_data`-Tabelle funktionieren. `<ignore>` Regeln verhindern, dass das Tool einige Einstellungen überträgt. In diesem Knoten können Platzhalter verwendet werden. Alle anderen Einstellungen, die nicht im Knoten `<ignore>` aufgeführt sind, werden migriert. Wenn sich der Pfad zu einer Einstellung in Magento 2 geändert hat, sollte er `//key/rename` Knoten hinzugefügt werden, wobei der alte Pfad im Knoten und `//key/rename/path` neue Pfad im Knoten `//key/rename/to`.

Unter dem Knoten `<value>` gibt es Regeln, die mit der Spalte „Wert“ in der `core_config_data`-Tabelle funktionieren. Diese Regeln zielen darauf ab, den Wert von Einstellungen durch Handler (Klassen, die `Migration\Handler\HandlerInterface` implementieren) umzuwandeln und für Magento 2 anzupassen.

### Datenmigrationsmodus

In diesem Modus werden die meisten Daten migriert. Vor der Datenmigration werden für jeden Schritt die Schritte zur Integritätsprüfung ausgeführt. Wenn die Integritätsprüfung erfolgreich war, installiert die [!DNL Data Migration Tool] Deltalogtabellen (mit Präfix `m2_cl_*`) und entsprechende Trigger in der Magento 1-Datenbank und führt die Datenmigrationsphase der folgenden Schritte aus. Wenn die Migration fehlerfrei abgeschlossen wird, prüft das Volume die Datenkonsistenz. Wenn Sie den Live Store migrieren, kann eine Warnmeldung angezeigt werden. Keine Sorge, die Delta-Migration übernimmt diese inkrementellen Daten. Die wertvollsten Migrationsschritte sind Zuordnung, URL-Umschreibung und EAV.

#### Schritt zuordnen

Map step ist für die Übertragung der meisten Daten von Magento 1 zu Magento 2 verantwortlich. In diesem Schritt werden Anweisungen aus der Datei map.xml (im Verzeichnis `etc/`) gelesen. Die Datei beschreibt die Unterschiede zwischen den Datenstrukturen von Quelle (Magento 1) und Ziel (Magento 2). Falls Magento 1 Tabellen oder Felder enthält, die zu einer Erweiterung gehören, die in Magento 2 nicht vorhanden ist, können diese Entitäten hier platziert werden, um sie durch Zuordnungsschritt zu ignorieren. Andernfalls wird eine Fehlermeldung angezeigt.

Map-Datei hat das nächste Format:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

Bereiche:

* *source* - enthält Regeln der Quelldatenbank

* *Ziel* - enthält Regeln der Zieldatenbank

Optionen:

* *Ignorieren* - Dokument, Feld oder Datentyp, die mit dieser Option markiert sind, wird ignoriert

* *Umbenennen* - Beschreibt die Namensbeziehungen zwischen Dokumenten mit unterschiedlichen Namen. Wenn der Name des Zieldokuments nicht mit dem Quelldokument identisch ist, können Sie die Option „Umbenennen“ verwenden, um den Namen des Quelldokuments ähnlich dem Namen der Zieltabelle festzulegen

* *Verschieben* - Legt die Regel fest, um das angegebene Feld vom Quelldokument zum Zieldokument zu verschieben. HINWEIS: Der Name des Zieldokuments sollte mit dem Namen des Quelldokuments übereinstimmen. Wenn Quell- und Zieldokumentnamen unterschiedlich sind, müssen Sie die Option „Umbenennen“ für Dokumente verwenden, die verschobene Felder enthalten

* *Transform* - ist eine Option, mit der Benutzende Felder entsprechend dem in Handlern beschriebenen Verhalten migrieren können

* *handler* - Beschreibt das Umwandlungsverhalten für Felder. Um den Handler aufzurufen, müssen Sie einen Handler-Klassennamen in einem `<handler>`-Tag angeben. Verwenden Sie das `<param>`-Tag mit dem Parameternamen und den Wertdaten, um es an den Handler zu übergeben.

**Source** Verfügbare Vorgänge:

| Dokument | Feld |
|--- |--- |
| Umbenennen ignorieren | Transformation ignorieren |

**Ziel** verfügbare Vorgänge:

| Dokument | Feld |
|--- |--- |
| Ignorieren | Transformation ignorieren |

#### Platzhalter

Um Dokumente mit ähnlichen Teilen (`document_name_1`, `document_name_2`) zu ignorieren, können Sie die Platzhalterfunktion verwenden. Platzieren Sie `*` Symbol anstelle eines sich wiederholenden Teils (`document_name_*`), und diese Maske deckt alle Quell- oder Zieldokumente ab, die diese Maske erfüllen.

#### URL-Neuschreibungsschritt

Dieser Schritt ist komplex, da in Magento 1 viele verschiedene Algorithmen entwickelt wurden, die nicht mit Magento 2 kompatibel sind. Für verschiedene Versionen von Magento 1 kann es verschiedene Algorithmen geben. Daher gibt es unter dem Ordner Step/UrlRewrite Klassen, die für einige bestimmte Versionen von Magento entwickelt wurden, und Migration\Step\UrlRewrite\Version191to2000 ist eine davon. Es kann URL-Umschreibungsdaten von Magento 1.9.1 an Magento 2 übertragen.

#### EAV-Schritt

Dieser Schritt überträgt alle Attribute (Produkt, Kunde, RMA) von Magento 1 auf Magento 2. Sie verwendet die Datei map-eav.xml , die Regeln ähnlich denen in der Datei map.xml für bestimmte Fälle der Datenverarbeitung enthält.

Einige der Tabellen, die im Schritt verarbeitet werden:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Delta-Migrationsmodus

Nach der Hauptmigration konnten zusätzliche Daten zur Magento 1-Datenbank hinzugefügt werden (z. B. von Kunden in der Storefront). Um diese Daten zu verfolgen, richtet das Tool die Datenbanktabellen für Trigger zu Beginn des Migrationsprozesses ein. Weitere Informationen finden Sie unter [Migrieren von Daten, die von Erweiterungen von Drittanbietern erstellt wurden](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Datenquellen

Um zu den Datenquellen von Magento 1 und Magento 2 zu gelangen und mit den zugehörigen Daten (Auswählen, Aktualisieren, Einfügen, Löschen) zu arbeiten, gibt es viele -Klassen im Ressourcenordner. Migration\ResourceModel\Source und Migration\ResourceModel\Destination sind Hauptklassen. In allen Migrationsschritten wird sie zum Arbeiten mit Daten verwendet. Diese Daten sind in Klassen wie Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure usw. enthalten.

Im Folgenden finden Sie ein Klassendiagramm für diese Klassen:

![Datenstruktur des Migrations-Tools](../../assets/data-migration/MmigrationToolDataStructure.png)

## Protokollierung

Um die Ausgabe des Migrationsprozesses zu implementieren und alle möglichen Ebenen zu steuern, wird PSR-Logger angewendet, der in Magento verwendet wird. `\Migration\Logger\Logger` Klasse wurde implementiert, um Protokollierungsfunktionen bereitzustellen. Um den Logger zu verwenden, sollten Sie ihn über die Injektion der Konstruktorabhängigkeit einfügen.

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

Danach können Sie diese Klasse für die Protokollierung einiger Ereignisse verwenden:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Es besteht die Möglichkeit, anzupassen, wo Protokollinformationen geschrieben werden sollen. Dazu können Sie dem Logger mithilfe der Methode pushHandler() des Loggers einen Handler hinzufügen. Jeder Handler sollte `\Monolog\Handler\HandlerInterface` Schnittstelle implementieren. Derzeit gibt es zwei Handler:

* ConsoleHandler: schreibt Meldungen in die Konsole

* FileHandler: schreibt Meldungen in eine Protokolldatei, die in der Konfigurationsoption „log_file“ festgelegt wurde

Außerdem ist es möglich, jeden zusätzlichen Handler zu implementieren. Im Magento-Framework gibt es eine Reihe von Handlern. Beispiel für das Hinzufügen von Handlern zu einer Protokollierung:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Zum Festlegen zusätzlicher Daten für Logger (aktueller Modus, Tabellenname) können Sie Logger-Prozessoren verwenden. Es gibt einen vorhandenen Prozessor (MessageProcessor). Sie wird erstellt, um „zusätzliche“ Daten für Protokollmeldungen hinzuzufügen, und werden jedes Mal aufgerufen, wenn die Protokollmethode ausgeführt wird. MessageProcessor hat $extra var geschützt, die leere Werte für „mode“, „stage“, „step“ und „table“ enthalten. Zusätzliche Daten können als zweiter Parameter (Kontext) für die Protokollmethode an den Prozessor übergeben werden. Derzeit zusätzliche Datensätze an den Prozessor in der AbstractStep->runStage-Methode (Übergeben des aktuellen Modus, der Phase und des Schritts an den Prozessor) und Datenklassen, in denen die Logger->Debug-Methode (Übergeben des migrierenden Tabellennamen) verwendet wird. Beispiel für das Hinzufügen von Prozessoren zum Logger:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Es besteht die Möglichkeit, die Ausführlichkeitsstufe festzulegen. Derzeit gibt es drei Ebenen:

* `ERROR` (schreibt nur Fehler in das Protokoll)
* `INFO` (nur wichtige Informationen werden in das Protokoll geschrieben, Standardwert)
* `DEBUG` (alles ist geschrieben)

Die Protokollebene für die Ausführlichkeit kann für jeden Handler separat festgelegt werden, indem `setLevel()` Methode aufgerufen wird. Wenn Sie die Ausführlichkeitsstufe über einen Befehlszeilenparameter festlegen möchten, sollten Sie beim Start der Anwendung die Option „Verbose“ ändern.

Sie können Protokollmeldungen mit dem Monolog-Formatierer formatieren. Damit die Formatierungsfunktion funktioniert, müssen Sie den Protokoll-Handler mithilfe der `setFormatter()`-Methode angeben. Derzeit verfügen wir über eine Formatierungsklasse (`MessageFormatter`), die während der Nachrichtenverarbeitung (über die vom Handler ausgeführte `format()`-Methode) ein bestimmtes Format festlegt (abhängig vom Ausführlichkeitsgrad).

Die Bearbeitung des Loggers (Hinzufügen von Handlern und Prozessoren) und die Verarbeitung im Verbose-Modus werden in der `process()`-Methode der `Migration\Logger\Manager`-Klasse durchgeführt. Die Methode wird beim Starten der Anwendung aufgerufen.

## Automatische Tests

Es gibt drei Arten von Tests in der [!DNL Data Migration Tool]:

* Statisch
* Einheit
* Integration

Sie befinden sich im `tests/`-Verzeichnis des Tools, das mit dem Typ des Tests identisch ist (Modultests befinden sich im `tests/unit`-Verzeichnis). Um den Test zu starten, sollte phpunit installiert sein. Ändert das aktuelle Verzeichnis in das Testverzeichnis und startet phpunit. Beispiel:

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
