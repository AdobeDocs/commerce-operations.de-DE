---
title: Anpassen des [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die [!DNL Data Migration Tool] anpassen, um durch Erweiterungen erstellte Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Konfigurieren des [!DNL Data Migration Tool]

Manchmal unterscheiden sich das Datenformat und die Struktur, die von [extensions](https://marketplace.magento.com/extensions.html) oder benutzerdefiniertem Code erstellt werden, zwischen Magento 1 und Magento 2. Verwenden Sie Erweiterungspunkte innerhalb des [!DNL Data Migration Tool] , um diese Daten zu migrieren. Wenn das Datenformat und die Datenstruktur identisch sind, kann das Tool die Daten automatisch ohne Benutzereingriff migrieren.

Während der Migration scannt und vergleicht der [Zuordnungsschritt](technical-specification.md#map-step) alle Magento 1- und Magento 2-Tabellen, einschließlich der von Erweiterungen erstellten Tabellen. Wenn die Tabellen identisch sind, migriert das Tool die Daten automatisch. Wenn die Tabellen unterschiedlich sind, wird das Tool beendet und der Benutzer wird benachrichtigt.

>[!NOTE]
>
>Lesen Sie die [Technische Spezifikation](technical-specification.md) , bevor Sie versuchen, die [!DNL Data Migration Tool] zu erweitern. Allgemeine Informationen zur Verwendung des Migrationstools finden Sie im [Migrationshandbuch](../overview.md) .


## Geringfügige Datenformat- und Strukturänderungen

In den meisten Fällen löst der Schritt [Map Schritt](technical-specification.md#map-step) kleinere Datenformat- und Strukturänderungen mithilfe der folgenden Methoden in der Datei `map.xml` ausreichend auf:

- Ändern von Tabellen- oder Feldnamen mit Zuordnungsregeln
- Transformieren von Datenformaten mit vorhandenen Handlern oder einem benutzerdefinierten Handler

Im Folgenden finden Sie ein Beispiel für die Verwendung sowohl von Zuordnungsregeln als auch von Handlern. In diesem Beispiel wird eine hypothetische Magento 1-Erweiterung namens &quot;GreatBlog&quot;verwendet, die für Magento 2 verbessert wurde.

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

- Migrieren Sie keine unnötigen Daten aus der `great_blog_index` -Indextabelle.
- Die Tabelle `great_blog_publication` wurde in Magento 2 in `great_blog_post` umbenannt, sodass Daten in die neue Tabelle migriert werden.
   - Das Feld `summary` wurde in `title` umbenannt, sodass Daten in das neue Feld migriert werden.
   - Das Feld `priority` wurde entfernt und ist in Magento 2 nicht mehr vorhanden.
   - Die Daten im Feld `body` haben das Format geändert und sollten vom benutzerdefinierten Handler verarbeitet werden: `\Migration\Handler\GreatBlog\NewFormat`.
- Für die Erweiterung &quot;GreatBlog&quot;wurde in Magento 2 eine neue Bewertungsfunktion entwickelt.
   - Eine neue `great_blog_rating` -Tabelle wurde erstellt.
   - Ein neues `great_blog_post.rating` -Feld wurde erstellt.

### Erweitern der Zuordnung in anderen Schritten

Andere Schritte unterstützen die Zuordnung, z. B. der Schritt [EAV-Schritt](technical-specification.md#eav-step) und der Schritt &quot;Kundenattribute&quot;. Diese Schritte migrieren eine vordefinierte Liste von Magento-Tabellen. Angenommen, die Erweiterung &quot;GreatBlog&quot;enthält ein zusätzliches Feld in der Tabelle `eav_attribute` und der Name wurde in Magento 2 geändert. Da die Tabelle vom [EAV-Schritt](technical-specification.md#eav-step) verarbeitet wird, sollten Zuordnungsregeln für die Datei `map-eav.xml` geschrieben werden. Die Dateien `map.xml` und `map-eav.xml` verwenden dasselbe `map.xsd`-Schema, sodass die Zuordnungsregeln unverändert bleiben.

## Größere Datenformat- und Strukturänderungen

Zusätzlich zum Schritt &quot;Map&quot;gibt es weitere Schritte in der Datei &quot;`config.xml`&quot;, die Daten mit größeren Format- und Strukturänderungen migrieren, darunter:

- [URL-Neuschreibungsschritt](technical-specification.md#url-rewrite-step)
- OrderGrids-Schritt
- [EAV-Schritt](technical-specification.md#eav-step)

Im Gegensatz zum Schritt [Map Schritt](technical-specification.md#map-step) werden mit diesen Schritten eine vordefinierte Liste von Tabellen anstelle aller Tabellen gescannt.

Erstellen Sie für umfangreiche Datenformat- und Strukturänderungen einen benutzerdefinierten Schritt.

### Erstellen eines benutzerdefinierten Schritts

Angenommen, die Erweiterung enthält eine Tabelle in Magento 1, wurde aber neu gestaltet, um zwei Tabellen in Magento 2 zu haben.

In Magento 1 gab es eine einzige `greatblog_post` -Tabelle:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

In Magento 2 wurde eine neue Tabelle für die Tags `greatblog_post_tags` eingeführt:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Die Tabelle Magento 2 `greatblog_post` sieht nun wie folgt aus:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Um alle Daten aus der alten Tabellenstruktur in eine neue zu migrieren, können Sie einen benutzerdefinierten Schritt in der Datei `config.xml` erstellen. Beispiel:

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

Das Tool führt die Schritte entsprechend ihrer Position in der Datei `config.xml` aus; von oben nach unten. In unserem Beispiel wird `GreatBlog Step` zuletzt ausgeführt.

Schritte können vier Arten von Klassen umfassen:

- Integritätsprüfung
- Datenbereitstellung
- Lautstärkeregelung
- Delta-Bereitstellung

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfiguration](technical-specification.md#configuration), [Schrittinterne Schritte](technical-specification.md#step-internals), [Phasen](technical-specification.md#step-stages) und [Ausführungsmodi](technical-specification.md#running-modes) .


Innerhalb dieser Klassen können komplexe SQL-Abfragen zusammengestellt werden, um Daten abzurufen und zu migrieren. Außerdem sollten diese Tabellen im Schritt [Map - Schritt](technical-specification.md#map-step) &quot;ignoriert&quot;werden, da alle vorhandenen Tabellen gescannt werden und versucht wird, die Daten zu migrieren, es sei denn, sie befinden sich im Tag `<ignore>` der Datei `map.xml` .

Definieren Sie für die Integritätsprüfung eine zusätzliche Zuordnungsdatei in der Datei &quot;`config.xml`&quot;, um zu überprüfen, ob die Tabellenstruktur erwartungsgemäß ist.

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

Die Integritätsprüfklasse `Vendor\Migration\Step\GreatBlog\Integrity` erweitert `Migration\App\Step\AbstractIntegrity` und enthält die `perform` -Methode, bei der wir die Tabellenstruktur überprüfen:

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

Als Nächstes müssen Sie eine Klasse für die Verarbeitung und Speicherung von Daten in der Magento 2-Datenbank `Vendor\Migration\Step\GreatBlog\Data` erstellen:

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

In einer Volume-Klasse `Vendor\Migration\Step\GreatBlog\Volume` wird geprüft, ob die Daten vollständig migriert wurden:

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

Fügen Sie der Datei `deltalog.xml` eine neue Gruppe hinzu, um die Delta-Migrationsfunktion hinzuzufügen. Geben Sie in `group` den Namen der Tabellen an, die auf Änderungen überprüft werden müssen:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Erstellen Sie dann die `Delta` -Klasse `Vendor\Migration\Step\GreatBlog\Delta`, die `Migration\App\Step\AbstractDelta` erweitert:

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

Nach der in den Beispielen angegebenen Implementierung benutzerdefinierter Schritte nimmt das System Daten aus der einzelnen Magento 1-Tabelle,
verarbeitet sie mit der `Vendor\Migration\Step\GreatBlog\Data` -Klasse und speichert die Daten in zwei Magento 2-Tabellen. Neue und geänderte Datensätze werden bei der Delta-Migration mithilfe der `Vendor\Migration\Step\GreatBlog\Delta` -Klasse bereitgestellt.

## Verbotene Erweiterungsmethoden

Da sich die [!DNL Data Migration Tool] und die Magento 2 ständig weiterentwickeln, können sich bestehende Schritte und Handler ändern. Es wird dringend empfohlen, das Verhalten von Schritten wie dem [Zuordnungsschritt](technical-specification.md#map-step), dem [URL-Neuschreibungsschritt](technical-specification.md#url-rewrite-step) und den Handlern nicht zu überschreiben, indem deren Klassen erweitert werden.

Einige Schritte unterstützen keine Zuordnung und können nicht geändert werden, ohne den Code zu ändern. Sie können entweder einen zusätzlichen Schritt schreiben, der Daten am Ende der Migration ändert, oder ein [GitHub-Problem](https://github.com/magento/data-migration-tool/issues) erstellen und einen neuen Erweiterungspunkt für den vorhandenen Schritt anfordern.
