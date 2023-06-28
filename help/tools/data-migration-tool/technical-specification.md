---
title: '''[!DNL Data Migration Tool] technische Spezifikation"'
description: Erfahren Sie mehr über die Implementierungsdetails der [!DNL Data Migration Tool] und wie bei der Datenübertragung zwischen Magento 1 und Magento 2 erweitert werden kann.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2079'
ht-degree: 0%

---

# [!DNL Data Migration Tool] technische Spezifikation

In diesem Abschnitt werden [!DNL Data Migration Tool] Implementierungsdetails und wie die Funktionalität erweitert werden kann.

## Repositorys

So greifen Sie auf die [!DNL Data Migration Tool] Quellcode, siehe GitHub [Repository](https://github.com/magento/data-migration-tool).

## Systemanforderungen

Die [Systemanforderungen](../../installation/system-requirements.md) für [!DNL Data Migration Tool] sind mit Magento 2 identisch.

## Interne Struktur

### Verzeichnisstruktur

Das folgende Diagramm stellt die Verzeichnisstruktur von [!DNL Data Migration Tool]:

```terminal
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

Das Schema für die Konfiguration `config.xsd` befindet sich im `etc/` Verzeichnis. Die Standardkonfigurationsdatei (`config.xml.dist`) für jede Version von Magento 1.x erstellt. Sie befindet sich in einem separaten Ordner unter `etc/`.

Die Standardkonfigurationsdatei kann durch eine benutzerdefinierte ersetzt werden (siehe [Befehlssyntax](migrate-data/overview.md#command-syntax)).

Die Konfigurationsdatei hat die folgende Struktur:

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

* Schritte - beschreibt alle Schritte, die während der Migration verarbeitet werden

* source - Konfiguration für die Datenquelle. Verfügbare Quelltypen: Datenbank

* Ziel - Konfiguration für das Datenziel. Verfügbare Zieltypen: Datenbank

* options - Liste der Parameter. Enthält sowohl obligatorische (map_file, settings_map_file, bulk_size) als auch optionale (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file) Parameter

Ändern Sie die Präfixoption, falls Magento mit Präfix in Datenbanktabellen installiert wurde. Sie kann für Magento 1- und Magento 2-Datenbanken festgelegt werden. Verwenden Sie die Konfigurationsoptionen &quot;source_prefix&quot;und &quot;dest_prefix&quot;.

Auf Konfigurationsdaten kann über die `\Migration\Config` -Klasse.

## Schritte für verfügbare Vorgänge

| Dokument | Feld |
|---|---|
| `step` | Knoten der zweiten Ebene innerhalb des Knotens &quot;Schritte&quot;. Die Beschreibung des entsprechenden Schritts muss im `title` -Attribut. |
| `integrity` | Gibt die für die Integritätsprüfung verantwortliche PHP-Klasse an. Vergleicht die Tabellenfeldnamen, -typen und andere Informationen, um die Kompatibilität zwischen den Datenstrukturen von Magento 1 und 2 zu überprüfen. |
| `data` | Gibt die für die Datenüberprüfung verantwortliche PHP-Klasse an. Überträgt die Daten Tabelle für Tabelle von Magento 1 in Magento 2. |
| `volume` | Gibt die PHP-Klasse an, die für die Lautstärkeprüfung verantwortlich ist. Vergleicht die Anzahl der Datensätze zwischen Tabellen, um sicherzustellen, dass die Übertragung erfolgreich war. |
| `delta` | Gibt die für die Delta-Prüfung verantwortliche PHP-Klasse an. Sendet das Delta nach der vollständigen Datenmigration von Magento 1 auf Magento 2. |

## Attribute der Quelldatenbankinformationen

| Dokument | Feld | Erforderlich? |
|---|---|---|
| `name` | Datenbankname des Magento 1-Servers. | yes |
| `host` | Host-IP-Adresse des Magento 1-Servers. | yes |
| `port` | Anschlussnummer des Magento 1-Servers. | no |
| `user` | Benutzername des Magento 1-Datenbankservers. | yes |
| `password` | Kennwort des Magento 1-Datenbankservers. | yes |
| `ssl_ca` | Pfad zur Datei der SSL-Zertifizierungsstelle. | no |
| `ssl_cert` | Pfad zur SSL-Zertifikatdatei. | no |
| `ssl_key` | Pfad zur SSL-Schlüsseldatei. | no |

## Attribute der Zieldatenbank-Informationen

| Dokument | Feld | Erforderlich? |
|---|---|---|
| `name` | Datenbankname des Magento 2-Servers. | yes |
| `host` | Host-IP-Adresse des Magento 2-Servers. | yes |
| `port` | Anschlussnummer des Magento 2-Servers. | no |
| `user` | Benutzername des Magento 2-Datenbankservers. | yes |
| `password` | Kennwort des Magento 2-Datenbankservers. | yes |
| `ssl_ca` | Pfad zur Datei der SSL-Zertifizierungsstelle. | no |
| `ssl_cert` | Pfad zur SSL-Zertifikatdatei. | no |
| `ssl_key` | Pfad zur SSL-Schlüsseldatei. | no |

## Verbindung mit dem TLS-Protokoll herstellen

Sie können auch über das TLS-Protokoll (d. h. mithilfe öffentlicher/privater kryptografischer Schlüssel) eine Verbindung zu einer Datenbank herstellen. Fügen Sie die folgenden optionalen Attribute zum `database` element:

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

## Schrittinternals

Der Migrationsprozess besteht aus Schritten.

Step ist eine Einheit, die Funktionen bietet, die für die Migration einiger separater Daten erforderlich sind. Schritt kann aus einer oder mehreren Phasen bestehen (Integritätsprüfung, Daten, Volumenprüfung und Delta).

Standardmäßig gibt es mehrere Schritte ([Zuordnung](#map-step), [EAV](#eav), [URL-Neuschreibungen](#url-rewrite-step)usw.). Optional können Sie auch eigene Schritte hinzufügen.

Klassen für Schritte sind im Verzeichnis src/migration/Step enthalten.

Um eine Step-Klasse auszuführen, muss die Klasse in der Datei config.xml definiert sein.

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

Wenn die Datenphase das Rollback unterstützt, sollte sie die `RollbackInterface` -Schnittstelle.

Die Visualisierung des laufenden Schritts wird von der Fortschrittsleistenkomponente von Symfony bereitgestellt (siehe [Fortschrittsleiste](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Greifen Sie in einem Schritt als LogLevelProcessor auf diese Komponente zu.

Die wichtigsten Anwendungsmethoden sind:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Schrittschritte

### Integritätsprüfung

Jeder Schritt muss prüfen, ob die Datenquellenstruktur (standardmäßig Magento 1) und die Datenzielstruktur (Magento 2) kompatibel sind. Wenn nicht, wird ein Fehler mit nicht kompatiblen Entitäten angezeigt. Wenn Felder unterschiedliche Datentypen haben (dasselbe Feld hat Dezimaldatentyp in Magento 1 und Integer in Magento 2), wird eine Warnmeldung angezeigt (es sei denn, es wurde in der Map-Datei behandelt).

### Datenübertragung

Im Falle einer Integritätsprüfung wird die Datenübertragung durchgeführt. Wenn Fehler auftreten, wird der Rollback ausgeführt, um zum vorherigen Status von Magento 2 zurückzukehren. Wenn eine Schrittklasse die `RollbackInterface` -Schnittstelle verwenden, wird die Rollback-Methode ausgeführt, wenn ein Fehler auftritt.

### Volumenprüfung

Nachdem die Daten migriert wurden, bietet die Volumenüberprüfung zusätzliche Möglichkeiten, um zu überprüfen, ob alle Daten korrekt übertragen wurden.

### Delta-Versand

Die Delta-Funktion ist für die Bereitstellung der restlichen Daten verantwortlich, die nach der Hauptmigration hinzugefügt wurden.

## Ausführungsmodi

Das Tool sollte in drei verschiedenen Modi ausgeführt werden, insbesondere in der Reihenfolge:

1. Einstellungen - Migration der Systemeinstellungen
1. data - Hauptmigration von Daten
1. delta - Migration der übrigen Daten, die nach der Hauptmigration hinzugefügt wurden

Jeder Modus verfügt über eine eigene Liste von auszuführenden Schritten. Siehe config.xml

### Migrationsmodus für Einstellungen

Der Konfigurationsmigrationsmodus dieses Tools wird verwendet, um die folgenden Entitäten zu übertragen:

1. Websites, Stores, Ansichten speichern.
1. Speicherkonfiguration (hauptsächlich Geschäfte->Konfiguration in M2 oder System->Konfiguration in M1)

Bei jeder Speicherkonfiguration werden die Daten in der Datentabelle core_config_data in der Datenbank gespeichert. Die Datei settings.xml enthält Regeln für diese Tabelle, die während des Migrationsprozesses angewendet werden. In dieser Datei werden Einstellungen beschrieben, die ignoriert, umbenannt oder deren Werte geändert werden sollen. Die Datei &quot;settings.xml&quot;weist die folgende Struktur auf:

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

Unter dem Knoten `<key>` Es gibt Regeln, die mit der Spalte &quot;path&quot;in der `core_config_data` Tabelle. `<ignore>` -Regeln verhindern, dass das Tool einige Einstellungen übertragen kann. In diesem Knoten können Platzhalter verwendet werden. Alle anderen Einstellungen werden nicht in der `<ignore>` -Knoten migriert werden. Wenn sich der Pfad zu einer Einstellung in Magento 2 geändert hat, sollte er zu `//key/rename` -Knoten, wobei der alte Pfad in `//key/rename/path` Knoten und neuer Pfad zeigt in `//key/rename/to` Knoten.

Unter dem Knoten `<value>`, gibt es Regeln, die mit der Spalte &quot;Wert&quot;im `core_config_data` Tabelle. Diese Regeln zielen darauf ab, den Wert der Einstellungen durch Handler (Klassen, die implementieren `Migration\Handler\HandlerInterface`) und passen Sie sie für Magento 2 an.

### Datenmigrationsmodus

In diesem Modus werden die meisten Daten migriert. Vor der Datenmigration werden die Integritätsprüfungen für jeden Schritt ausgeführt. Wenn die Integritätsprüfung erfolgreich ist, wird die [!DNL Data Migration Tool] installiert Deltalog-Tabellen (mit Präfix `m2_cl_*`) und den entsprechenden Triggern zur Magento 1-Datenbank hinzugefügt und führt die Datenmigrationsphase von Schritten durch. Wenn die Migration ohne Fehler abgeschlossen ist, überprüft die Volumenüberprüfung die Datenkonsistenz. Wenn Sie den Live Store migrieren, wird möglicherweise eine Warnmeldung angezeigt. Diese inkrementellen Daten werden durch die Delta-Migration berücksichtigt. Die wertvollsten Migrationsschritte sind Map, URL Rewrite und EAV.

#### Map Step

Der Zuordnungsschritt ist für die Übertragung der meisten Daten von Magento 1 auf Magento 2 verantwortlich. Dieser Schritt liest Anweisungen aus der Datei &quot;map.xml&quot;(im `etc/` Verzeichnis). In der Datei werden die Unterschiede zwischen den Datenstrukturen der Quelle (Magento 1) und des Ziels (Magento 2) beschrieben. Wenn Magento 1 Tabellen oder Felder enthält, die zu einer Erweiterung gehören, die in Magento 2 nicht vorhanden ist, können diese Entitäten hier platziert werden, um sie durch &quot;Map Step&quot;zu ignorieren. Andernfalls wird eine Fehlermeldung angezeigt.

Die Zuordnungsdatei hat das folgende Format:

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

Gebiete:

* *source* - enthält Regeln der Quelldatenbank

* *Ziel* - Regeln für die Zieldatenbank enthält

Optionen:

* *ignore* - Mit dieser Option markiertes Dokument, Feld oder Datentyp wird ignoriert.

* *umbenennen* - beschreibt Namensrelationen zwischen Dokumenten mit einem anderen Namen. Wenn der Zieldokumentname nicht mit dem Quelldokument identisch ist, können Sie die Option &quot;Umbenennen&quot;verwenden, um den Quelldokumentnamen ähnlich dem Zieltabellennamen festzulegen.

* *Verschieben* - legt eine Regel fest, um das angegebene Feld vom Quelldokument zum Zieldokument zu verschieben. HINWEIS: Der Zieldokumentname sollte mit dem Namen des Quelldokuments identisch sein. Wenn sich die Namen der Quell- und Zieldokumente unterscheiden, müssen Sie die Umbenennungsoption für Dokumente verwenden, die verschobene Felder enthalten

* *transformieren* - ist eine Option, mit der Benutzer Felder gemäß dem in Handlern beschriebenen Verhalten migrieren können.

* *handler* - beschreibt das Umwandlungsverhalten für Felder. Um den Handler aufzurufen, müssen Sie einen Handler-Klassennamen in einer `<handler>` -Tag. Verwenden Sie die `<param>` Tag mit den Parameternamen- und Wertdaten, die an den Handler übergeben werden sollen

**Quelle** verfügbare Vorgänge:

| Dokument | Feld |
|--- |--- |
| ignore rename | Verschieben ignorieren Transformation |

**Ziel** verfügbare Vorgänge:

| Dokument | Feld |
|--- |--- |
| ignore | ignore transform |

#### Platzhalter

So ignorieren Sie Dokumente mit ähnlichen Teilen (`document_name_1`, `document_name_2`), können Sie die Platzhalterfunktion verwenden. Put `*` Symbol anstelle eines sich wiederholenden Teils (`document_name_*`) und diese Maske alle Quell- oder Zieldokumente abdeckt, die dieser Maske entsprechen.

#### Schritt zum Neuschreiben der URL

Dieser Schritt ist komplex, da in Magento 1 viele verschiedene Algorithmen entwickelt wurden, die nicht mit Magento 2 kompatibel sind. Für verschiedene Versionen von Magento 1 kann es verschiedene Algorithmen geben. Daher gibt es im Ordner &quot;Step/UrlRewrite&quot;Klassen, die für einige bestimmte Versionen von Magento und Migration\Step\UrlRewrite\Version191to2000 is one of them entwickelt wurden. Es kann URL-Umschreibungen von Daten aus Magento 1.9.1 in Magento 2 übertragen.

#### EAV-Schritt

In diesem Schritt werden alle Attribute (Produkt, Kunde, RMA) von Magento 1 auf Magento 2 übertragen. Für bestimmte Fälle von Verarbeitungsdaten wird die Datei map-eav.xml verwendet, die ähnliche Regeln wie die in der Datei map.xml enthaltenen enthält.

Einige der Tabellen, die in diesem Schritt verarbeitet werden:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Delta-Migrationsmodus

Nach der Hauptmigration hätten der Datenbank von Magento 1 zusätzliche Daten hinzugefügt werden können (z. B. von Kunden, die sich auf eine Storefront befinden). Um diese Daten zu verfolgen, richtet das Tool die Datenbank-Trigger für Tabellen zu Beginn des Migrationsprozesses ein. Weitere Informationen finden Sie unter [Migrieren von Daten, die von Drittanbietererweiterungen erstellt wurden](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Datenquellen

Um zu den Datenquellen von Magento 1 und Magento 2 zu gelangen und mit den Daten (Auswählen, Aktualisieren, Einfügen, Löschen) zu arbeiten, gibt es viele Klassen im Ordner Ressource . Migration\ResourceModel\Source und Migration\ResourceModel\Destination sind Hauptklassen. Alle Migrationsschritte verwenden sie für den Betrieb mit Daten. Diese Daten sind in Klassen wie Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure usw. enthalten.

Im Folgenden finden Sie ein Klassendiagramm dieser Klassen:

![Datenstruktur des Migrationstools](../../assets/data-migration/MmigrationToolDataStructure.png)

## Protokollierung

Um die Ausgabe des Migrationsprozesses zu implementieren und alle möglichen Ebenen zu steuern, wird der in Magento verwendete PSR-Logger angewendet. `\Migration\Logger\Logger` -Klasse implementiert wurde, um Protokollierungsfunktionen bereitzustellen. Um den Logger zu verwenden, sollten Sie ihn über eine Injektion der Abhängigkeit des Konstruktors injizieren.

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

Danach können Sie diese Klasse zur Protokollierung einiger Ereignisse verwenden:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Es gibt eine Möglichkeit, anzupassen, wo Protokollinformationen geschrieben werden sollen. Dazu können Sie einen Handler zur Protokollfunktion hinzufügen, indem Sie die Methode pushHandler() der Protokollfunktion verwenden. Jeder Handler sollte `\Monolog\Handler\HandlerInterface` -Schnittstelle. Derzeit gibt es zwei Handler:

* ConsoleHandler: schreibt Meldungen in die Konsole

* FileHandler: schreibt Meldungen in eine Protokolldatei, die in der Konfigurationsoption &quot;log_file&quot;festgelegt wurde

Es ist auch möglich, jeden zusätzlichen Handler zu implementieren. Im Magento-Framework gibt es eine Reihe von Handlern. Beispiel für das Hinzufügen von Handlern zur Protokollfunktion:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Um zusätzliche Daten für Logger (aktueller Modus, Tabellenname) festzulegen, können Sie Logger-Prozessoren verwenden. Es gibt einen vorhandenen Prozessor (MessageProcessor). Es wird erstellt, um &quot;zusätzliche&quot;Daten für die Protokollierung von Meldungen hinzuzufügen, und wird jedes Mal aufgerufen, wenn die Protokollmethode ausgeführt wird. MessageProcessor hat $extra var geschützt, die leere Werte für &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; und &#39;table&#39; enthalten. Zusätzliche Daten können als zweiter Parameter (Kontext) für die Protokollmethode an den Prozessor übergeben werden. Derzeit werden zusätzliche Datensätze zum Prozessor in der Methode AbstractStep->runStage (Übergeben des aktuellen Modus, der Phase und des Schritts an den Prozessor) und Datenklassen verwendet, in denen logger->debug -Methode verwendet wird (Übergeben Sie den migrierenden Tabellennamen). Beispiel für das Hinzufügen von Prozessoren zur Protokollfunktion:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Es besteht die Möglichkeit, den Grad der Ausführlichkeit festzulegen. Derzeit gibt es drei Ebenen:

* `ERROR` (schreibt nur Fehler in das Protokoll)
* `INFO` (Nur wichtige Informationen werden in das Protokoll geschrieben, Standardwert)
* `DEBUG` (alles ist geschrieben)

Die Verbosity-Protokollebene kann für jeden Handler separat festgelegt werden, indem `setLevel()` -Methode. Wenn Sie die Ausführlichkeitsstufe über den Befehlszeilenparameter festlegen möchten, sollten Sie die Option &quot;ausführlich&quot;beim Start der Anwendung ändern.

Sie können Protokollmeldungen mit dem Monolog-Formatierer formatieren. Damit die Formatierungs-Funktion funktioniert, müssen Sie den Protokollhandler mithilfe der `setFormatter()` -Methode. Derzeit gibt es eine Formatierungs-Klasse (`MessageFormatter`), das während der Nachrichtenverarbeitung (über die `format()` -Methode, die vom -Handler ausgeführt wird).

Die Bearbeitung des Loggers (Hinzufügen von Handlern und Prozessoren) und die Verarbeitung im ausführlichen Modus erfolgt im `process()` -Methode `Migration\Logger\Manager` -Klasse. Die -Methode wird beim Starten der Anwendung aufgerufen.

## Automatische Tests

Es gibt drei Arten von Tests in der [!DNL Data Migration Tool]:

* Statisch
* Einheit
* Integration

Sie befinden sich im `tests/` Verzeichnis, das mit dem Testtyp identisch ist (Komponententests befinden sich im `tests/unit` Verzeichnis). Um den Test zu starten, sollte phpunit installiert sein. Ändern Sie das aktuelle Verzeichnis in das Testverzeichnis und starten Sie phpunit. Beispiel:

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
