---
title: Anpassen des  [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die  [!DNL Data Migration Tool] , um von Erweiterungen erstellte Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Konfigurieren des [!DNL Data Migration Tool]

Manchmal unterscheiden sich das Datenformat und die Struktur, die von [Erweiterungen](https://marketplace.magento.com/extensions.html) oder benutzerdefiniertem Code erstellt wurden, zwischen Magento 1 und Magento 2. Verwenden Sie Erweiterungspunkte innerhalb der [!DNL Data Migration Tool], um diese Daten zu migrieren. Wenn das Datenformat und die Datenstruktur identisch sind, kann das Tool die Daten automatisch ohne Benutzereingriff migrieren.

Während der Migration scannt [Map Step](technical-specification.md#map-step) und vergleicht alle Magento 1- und Magento 2-Tabellen, einschließlich der von Extensions erstellten Tabellen. Wenn die Tabellen identisch sind, migriert das Tool die Daten automatisch. Wenn die Tabellen unterschiedlich sind, wird das Tool beendet und der Benutzer wird benachrichtigt.

>[!NOTE]
>
>Lesen Sie die [Technische Spezifikation](technical-specification.md), bevor Sie versuchen, die [!DNL Data Migration Tool] zu erweitern. Lesen Sie auch das [Migrationshandbuch](../overview.md), um allgemeine Informationen zur Verwendung des Migrations-Tools zu erhalten.


## Geringfügige Änderungen des Datenformats und der Struktur

In den meisten Fällen löst [Zuordnungsschritt](technical-specification.md#map-step) geringfügige Änderungen des Datenformats und der Struktur mithilfe der folgenden Methoden in der `map.xml`-Datei ausreichend auf:

- Ändern von Tabellen- oder Feldnamen mit Zuordnungsregeln
- Umwandeln von Datenformaten mit vorhandenen Handlern oder einem benutzerdefinierten Handler

Im Folgenden finden Sie ein Beispiel für die Verwendung sowohl von Zuordnungsregeln als auch eines -Handlers. In diesem Beispiel wird eine hypothetische Magento 1-Erweiterung namens „GreatBlog“ verwendet, die für Magento 2 verbessert wurde.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- Migrieren Sie keine unnötigen Daten aus der `great_blog_index`.
- Die Tabelle `great_blog_publication` wurde in Magento 2 in `great_blog_post` umbenannt, sodass Daten in die neue Tabelle migriert werden.
   - Das `summary` wurde in `title` umbenannt, sodass Daten in das neue Feld migriert werden.
   - Das `priority` wurde entfernt und existiert nicht mehr in Magento 2.
   - Die Daten im Feld `body` haben das Format geändert und sollten vom benutzerdefinierten Handler verarbeitet werden: `\Migration\Handler\GreatBlog\NewFormat`.
- Für die Erweiterung „GreatBlog“ in Magento 2 wurde eine neue Bewertungsfunktion entwickelt.
   - Eine neue `great_blog_rating` wurde erstellt.
   - Ein neues `great_blog_post.rating` wurde erstellt.

### Erweitern der Zuordnung in anderen Schritten

Andere Schritte unterstützen die Zuordnung, z. B. [ Schritt „EAV](technical-specification.md#eav-step) und der Schritt „Kundenattribute“. Mit diesen Schritten wird eine vordefinierte Liste von Magento-Tabellen migriert. Angenommen, die Erweiterung „GreatBlog“ enthält ein zusätzliches Feld in der `eav_attribute` und der Name wurde in Magento 2 geändert. Da die Tabelle vom [EAV-Schritt](technical-specification.md#eav-step) verarbeitet wird, sollten Zuordnungsregeln für die `map-eav.xml` geschrieben werden. Die `map.xml`- und `map-eav.xml` verwenden dasselbe `map.xsd`, sodass die Zuordnungsregeln gleich bleiben.

## Wesentliche Änderungen des Datenformats und der Datenstruktur

Zusätzlich zum Schritt Zuordnung gibt es weitere Schritte in der `config.xml`, mit denen Daten mit wichtigen Format- und Strukturänderungen migriert werden, darunter:

- [URL-Neuschreibungsschritt](technical-specification.md#url-rewrite-step)
- Schritt „Raster bestellen“
- [EAV-Schritt](technical-specification.md#eav-step)

Im Gegensatz zum [Map-](technical-specification.md#map-step) scannen diese Schritte anstelle aller Tabellen eine vordefinierte Liste von Tabellen.

Erstellen Sie für wichtige Änderungen am Datenformat und an der Struktur einen benutzerdefinierten Schritt.

### Erstellen eines benutzerdefinierten Schritts

Nehmen wir an, dass die Erweiterung unter Verwendung des gleichen „GreatBlog“-Beispiels in Magento 1 über eine Tabelle verfügt, aber neu entworfen wurde, um zwei Tabellen in Magento 2 zu haben.

In Magento 1 gab es nur eine `greatblog_post`:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

In Magento 2 wurde eine neue Tabelle für Tags `greatblog_post_tags` eingeführt:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post` sieht nun wie folgt aus:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Um alle Daten aus der alten Tabellenstruktur in eine neue zu migrieren, können Sie einen benutzerdefinierten Schritt in der `config.xml`-Datei erstellen. Beispiel:

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

Das Tool führt die Schritte entsprechend ihrer Position in der `config.xml` von oben nach unten aus. In unserem Beispiel wird die `GreatBlog Step` zuletzt ausgeführt.

Die Schritte können vier Arten von Klassen umfassen:

- Integritätsprüfung
- Datenbereitstellung
- Lautstärkeprüfung
- Delta-Bereitstellung

>[!NOTE]
>
>Weitere Informationen finden [ unter ](technical-specification.md#configuration), [Schrittinterne](technical-specification.md#step-internals), [](technical-specification.md#step-stages) und [Ausführungsmodi](technical-specification.md#running-modes).


Innerhalb dieser Klassen können komplexe SQL-Abfragen zusammengestellt werden, um Daten abzurufen und zu migrieren. Außerdem sollten diese Tabellen im [Map-Schritt“ „ignoriert“ werden](technical-specification.md#map-step) da alle vorhandenen Tabellen gescannt werden und versucht wird, die Daten zu migrieren, sofern sie sich nicht im `<ignore>`-Tag der `map.xml`-Datei befinden.

Für die Integritätsprüfung definieren Sie eine zusätzliche Zuordnungsdatei in der `config.xml`, um zu überprüfen, ob die Tabellenstruktur erwartungsgemäß ist.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

Zuordnungsdatei `map-greatblog.xml`:

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

Die Integritätsprüfung-Klasse `Vendor\Migration\Step\GreatBlog\Integrity` erweitert `Migration\App\Step\AbstractIntegrity` und enthält die `perform` Methode , bei der die Tabellenstruktur überprüft wird:

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

Als Nächstes müssen Sie eine Klasse für die Verarbeitung und Speicherung von Daten in der Magento 2-`Vendor\Migration\Step\GreatBlog\Data` erstellen:

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

In einer Volume-`Vendor\Migration\Step\GreatBlog\Volume` überprüfen wir, ob die Daten vollständig migriert wurden:

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

Um die Delta-Migrationsfunktion hinzuzufügen, fügen Sie eine neue Gruppe zur `deltalog.xml` hinzu. Geben Sie in `group` den Namen der Tabellen an, die auf Änderungen überprüft werden müssen:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Erstellen Sie dann die `Delta`-`Vendor\Migration\Step\GreatBlog\Delta`, die `Migration\App\Step\AbstractDelta` erweitert:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

Nach der in den Beispielen angegebenen benutzerdefinierten Schrittimplementierung nimmt das System Daten aus der einzelnen Magento 1-Tabelle,
Verarbeiten Sie sie mit `Vendor\Migration\Step\GreatBlog\Data` Klasse und speichern Sie die Daten in zwei Magento 2-Tabellen. Neue und geänderte Datensätze werden bei der Delta-Migration mithilfe der `Vendor\Migration\Step\GreatBlog\Delta`-Klasse bereitgestellt.

## Verbotene Erweiterungsmethoden

Da sich die [!DNL Data Migration Tool] und Magento 2 ständig weiterentwickeln, können sich bestehende Schritte und Handler ändern. Es wird dringend empfohlen, das Verhalten von Schritten wie [Map-Schritt](technical-specification.md#map-step), [URL-Rewrite-Schritt](technical-specification.md#url-rewrite-step) und Handlern nicht durch Erweitern ihrer Klassen zu überschreiben.

Einige Schritte unterstützen keine Zuordnung und können nicht geändert werden, ohne den Code zu ändern. Sie können entweder einen zusätzlichen Schritt schreiben, der die Daten am Ende der Migration ändert, oder ein [GitHub-Problem](https://github.com/magento/data-migration-tool/issues) erstellen und einen neuen Erweiterungspunkt für den vorhandenen Schritt anfordern.
