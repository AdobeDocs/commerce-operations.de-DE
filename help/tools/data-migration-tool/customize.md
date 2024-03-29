---
title: Anpassen der [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die [!DNL Data Migration Tool] , um durch Erweiterungen erstellte Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Konfigurieren Sie die [!DNL Data Migration Tool]

Manchmal werden das Datenformat und die Struktur von [Erweiterungen](https://marketplace.magento.com/extensions.html) oder benutzerdefinierter Code unterscheidet sich zwischen Magento 1 und Magento 2. Verwenden Sie Erweiterungspunkte innerhalb der [!DNL Data Migration Tool] um diese Daten zu migrieren. Wenn das Datenformat und die Datenstruktur identisch sind, kann das Tool die Daten automatisch ohne Benutzereingriff migrieren.

Während der Migration wird die Variable [Map Step](technical-specification.md#map-step) scannt und vergleicht alle Magento 1- und Magento 2-Tabellen, einschließlich der durch Erweiterungen erstellten Tabellen. Wenn die Tabellen identisch sind, migriert das Tool die Daten automatisch. Wenn die Tabellen unterschiedlich sind, wird das Tool beendet und der Benutzer wird benachrichtigt.

>[!NOTE]
>
>Lesen Sie die [Technische Spezifikation](technical-specification.md) vor dem Versuch, die [!DNL Data Migration Tool]. Lesen Sie auch den Abschnitt [Migrationshandbuch](../overview.md) allgemeine Informationen zur Verwendung des Migrationswerkzeugs.


## Geringfügige Datenformat- und Strukturänderungen

In den meisten Fällen wird die [Map Step](technical-specification.md#map-step) hinreichend löst kleinere Datenformat- und Strukturänderungen mithilfe der folgenden Methoden im `map.xml` Datei:

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

- Migrieren Sie keine unnötigen Daten aus dem `great_blog_index` Indextabelle.
- Die Tabelle `great_blog_publication` wurde in `great_blog_post` in Magento 2, sodass Daten in die neue Tabelle migriert werden.
   - Die `summary` wurde in umbenannt. `title`, sodass Daten in das neue Feld migriert werden.
   - Die `priority` wurde entfernt und ist in Magento 2 nicht mehr vorhanden.
   - Die Daten im `body` hat das Format geändert und sollte vom benutzerdefinierten Handler verarbeitet werden: `\Migration\Handler\GreatBlog\NewFormat`.
- Für die Erweiterung &quot;GreatBlog&quot;wurde in Magento 2 eine neue Bewertungsfunktion entwickelt.
   - Eine neue `great_blog_rating` wurde erstellt.
   - Eine neue `great_blog_post.rating` wurde erstellt.

### Erweitern der Zuordnung in anderen Schritten

Andere Schritte unterstützen das Mapping, z. B. die [EAV-Schritt](technical-specification.md#eav-step) und im Schritt Kundenattribute . Diese Schritte migrieren eine vordefinierte Liste von Magento-Tabellen. Angenommen, die Erweiterung &quot;GreatBlog&quot;enthält ein zusätzliches Feld im `eav_attribute` -Tabelle und der Name wurde in Magento 2 geändert. Da die Tabelle von der [EAV-Schritt](technical-specification.md#eav-step), sollten Zuordnungsregeln für die `map-eav.xml` -Datei. Die `map.xml` und `map-eav.xml` -Dateien verwenden dasselbe `map.xsd` -Schema verwenden, sodass die Zuordnungsregeln unverändert bleiben.

## Größere Datenformat- und Strukturänderungen

Zusätzlich zum Schritt &quot;Zuordnung&quot;gibt es weitere Schritte im `config.xml` -Datei, die Daten mit wesentlichen Format- und Strukturänderungen migriert, darunter:

- [URL-Neuschreibungsschritt](technical-specification.md#url-rewrite-step)
- OrderGrids-Schritt
- [EAV-Schritt](technical-specification.md#eav-step)

Im Gegensatz zu [Map Step](technical-specification.md#map-step)enthalten ist, wird mit diesen Schritten eine vordefinierte Liste von Tabellen anstelle aller Tabellen gescannt.

Erstellen Sie für umfangreiche Datenformat- und Strukturänderungen einen benutzerdefinierten Schritt.

### Erstellen eines benutzerdefinierten Schritts

Angenommen, die Erweiterung enthält eine Tabelle in Magento 1, wurde aber neu gestaltet, um zwei Tabellen in Magento 2 zu haben.

In Magento 1 gab es eine einzige `greatblog_post` table:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

In Magento 2 eine neue Tabelle für Tags `greatblog_post_tags` eingeführt wurde:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO 2 `greatblog_post` -Tabelle sieht nun wie folgt aus:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Um alle Daten aus der alten Tabellenstruktur in eine neue zu migrieren, können Sie einen benutzerdefinierten Schritt im `config.xml` -Datei. Beispiel:

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

Das Tool führt die Schritte entsprechend ihrer Position im `config.xml` -Datei; von oben nach unten. In unserem Beispiel wird die `GreatBlog Step` wird zuletzt ausgeführt.

Schritte können vier Arten von Klassen umfassen:

- Integritätsprüfung
- Datenbereitstellung
- Lautstärkeregelung
- Delta-Bereitstellung

>[!NOTE]
>
>Siehe Abschnitt [Konfiguration](technical-specification.md#configuration), [Schrittinternals](technical-specification.md#step-internals), [Phasen](technical-specification.md#step-stages), und [Ausführungsmodi](technical-specification.md#running-modes) für weitere Informationen.


Innerhalb dieser Klassen können komplexe SQL-Abfragen zusammengestellt werden, um Daten abzurufen und zu migrieren. Außerdem sollten diese Tabellen im [Map Step](technical-specification.md#map-step) weil es alle vorhandenen Tabellen scannt und versucht, die Daten zu migrieren, es sei denn, sie befinden sich im `<ignore>` -Tag `map.xml` -Datei.

Definieren Sie zur Integritätsprüfung eine zusätzliche Zuordnungsdatei im `config.xml` -Datei, um zu überprüfen, ob die Tabellenstruktur erwartungsgemäß ist.

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

Integrationsprüfungsklasse `Vendor\Migration\Step\GreatBlog\Integrity` erweitert `Migration\App\Step\AbstractIntegrity` und enthält die `perform` Methode zur Überprüfung der Tabellenstruktur:

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

Als Nächstes müssen Sie eine Klasse für die Verarbeitung und Speicherung von Daten in der Magento 2-Datenbank erstellen `Vendor\Migration\Step\GreatBlog\Data`:

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

In einer Volume-Klasse `Vendor\Migration\Step\GreatBlog\Volume`überprüfen wir, ob die Daten vollständig migriert wurden:

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

Um die Delta-Migrationsfunktion hinzuzufügen, fügen Sie dem `deltalog.xml` -Datei. In `group`Geben Sie den Namen der Tabellen an, die auf Änderungen überprüft werden müssen:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Erstellen Sie dann die `Delta` class `Vendor\Migration\Step\GreatBlog\Delta` , die `Migration\App\Step\AbstractDelta`:

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

Nach der in den Beispielen angegebenen Implementierung eines benutzerdefinierten Schritts nimmt das System Daten aus der einzelnen Magento 1-Tabelle auf und verarbeitet sie mithilfe von `Vendor\Migration\Step\GreatBlog\Data` -Klasse und speichern Sie die Daten in zwei Magento 2-Tabellen. Neue und geänderte Datensätze werden bei der Delta-Migration mithilfe der Variablen `Vendor\Migration\Step\GreatBlog\Delta` -Klasse.

## Verbotene Erweiterungsmethoden

Seit [!DNL Data Migration Tool] und Magento 2 entwickeln sich ständig weiter, bestehende Schritte und Handler können sich ändern. Es wird dringend empfohlen, das Verhalten von Schritten wie dem [Map Step](technical-specification.md#map-step), [URL-Neuschreibungsschritt](technical-specification.md#url-rewrite-step), und Handler durch Erweitern ihrer Klassen.

Einige Schritte unterstützen keine Zuordnung und können nicht geändert werden, ohne den Code zu ändern. Sie können entweder einen zusätzlichen Schritt schreiben, der Daten nach der Migration ändert, oder eine [GitHub-Problem](https://github.com/magento/data-migration-tool/issues) und fordern Sie einen neuen Erweiterungspunkt für den vorhandenen Schritt an.
