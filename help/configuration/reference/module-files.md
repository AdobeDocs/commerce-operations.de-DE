---
title: Modulkonfigurationsdateien
description: Erfahren Sie, wie Sie ein Modul mithilfe von Konfigurationstypen anpassen können.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# Überblick über die Modulkonfigurationsdateien

Die Zuständigkeiten der `config.xml` Konfigurationsdatei, die in früheren Versionen von Commerce verwendet wurde, sind jetzt auf mehrere Dateien aufgeteilt, die sich in verschiedenen Modulverzeichnissen befinden. Die verschiedenen Konfigurationsdateien von Commerce werden nur bei Bedarf geladen, wenn ein Modul einen bestimmten Konfigurationstyp anfordert.

Sie können diese Dateien - auch als &quot;_&quot; bezeichnet_ verwenden, um bestimmte Aspekte des Verhaltens Ihres Moduls anzupassen.

Mehrere Module können Konfigurationsdateien deklarieren, die denselben Konfigurationstyp betreffen (z. B. Ereignisse), und diese mehreren Konfigurationsdateien werden zusammengeführt.

In diesem Thema werden häufig folgende Begriffe verwendet:

- **Konfigurationsobjekt** - Die Commerce-Bibliothek oder -Klasse, die für die Definition und Validierung des Konfigurationstyps verantwortlich ist. Das Konfigurationsobjekt für `config.xml` ist beispielsweise [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Konfigurationsphase** - Phasen werden als _primär_, _global_ und _area_ definiert. Jede Phase bestimmt, wann der Konfigurationstyp geladen und mit gleichnamigen Konfigurationstypen zusammengeführt wird. Beispielsweise werden `module.xml` Dateien mit anderen `module.xml` zusammengeführt.

- **Konfigurationsbereich** - Ergänzend zu den Konfigurationsphasen definiert ein Bereich das Konfigurationstypmodell. `adminhtml` ist beispielsweise ein Bereichsbereich, der zu einem späteren Zeitpunkt mit den `adminhtml`-Konfigurationen anderer Module geladen wird. Weitere Informationen finden Sie unter [Module und Bereiche](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Laden und Zusammenführen von Konfigurationen

In diesem Abschnitt wird beschrieben, wie Konfigurationsdateien geladen und zusammengeführt werden.

### So lädt Commerce Konfigurationsdateien

Commerce lädt Konfigurationsdateien in der folgenden Reihenfolge (alle Pfade beziehen sich auf Ihr Commerce-Installationsverzeichnis):

- Primäre Konfiguration ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)) Diese Datei wird zum Bootstrapping von Commerce verwendet.
- Globale Konfigurationen aus Modulen (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Sammelt bestimmte Konfigurationsdateien aus allen Modulen und führt sie zusammen.
- Bereichsspezifische Konfiguration aus Modulen (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Sammelt Konfigurationsdateien aus allen Modulen und führt sie in der globalen Konfiguration zusammen. Einige bereichsspezifische Konfigurationen können die globale Konfiguration überschreiben oder erweitern.

Hierbei gilt

- `<your component base dir>` ist der Basisordner, in dem sich die Komponente befindet. Typische Werte sind `app/code` oder `vendor` relativ zum Commerce-Installationsverzeichnis.
- `<vendorname>` ist der Anbietername der Komponente; beispielsweise ist der Anbietername von Commerce `magento`.
- `<component-type>` ist eine der folgenden:

   - `module-`: Eine Erweiterung oder ein Modul.
   - `theme-`: Design.
   - `language-`: Sprachpaket.

>[!INFO]
>
>Derzeit befinden sich Designs unter `<magento_root>/app/design/frontend` oder `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Name der Komponente wie in [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json) definiert.

### Zusammenführen von Konfigurationsdateien

Knoten in Konfigurationsdateien werden auf der Grundlage ihrer vollqualifizierten XPaths zusammengeführt, für die ein spezielles -Attribut in `$idAttributes` als Kennung deklarierten Array definiert ist. Diese Kennung muss für alle Knoten eindeutig sein, die unter demselben übergeordneten Knoten verschachtelt sind.

Zusammenführungsalgorithmus der Commerce-Anwendung:

- Wenn Knotenkennungen gleich sind (oder keine Kennung definiert ist), wird der gesamte zugrunde liegende Inhalt im Knoten (Attribute, untergeordnete Knoten und skalare Inhalte) überschrieben.
- Wenn die Knotenkennungen nicht gleich sind, ist der Knoten ein neues untergeordnetes Element des übergeordneten Knotens.
- Wenn das Originaldokument mehrere Knoten mit derselben Kennung enthält, wird ein Fehler ausgelöst, da die Kennungen nicht unterschieden werden können.

Nach dem Zusammenführen der Konfigurationsdateien enthält das resultierende Dokument alle Knoten aus den Originaldateien.

>[!INFO]
>
>Sie können die [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php)-Klasse zum Debuggen und zum Verstehen der Logik hinter dem [Konfigurationsdateien-Ladeprogramm](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) und [Zusammenführungskonfigurationen](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144)-Prozess verwenden.

## Konfigurationstypen, Objekte und Schnittstellen

Die folgenden Abschnitte enthalten Informationen zu Konfigurationstypen, den entsprechenden Konfigurationsobjekten und Schnittstellen, die Sie für die Arbeit mit den Objekten verwenden können:

### Konfigurationstypen und Objekte

In der folgenden Tabelle sind die einzelnen Konfigurationstypen und das Commerce-Konfigurationsobjekt aufgeführt, auf das sie sich beziehen.

| Konfigurationsdatei | Beschreibung | Etappe | Konfigurationsobjekt |
| --- | --- | --- | --- |
| `address_formats.xml` | Deklaration des Adressformats | primär, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Zugriffssteuerungsliste](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Erweiterte Berichte]https://developer.adobe.com/commerce/php/development/advanced-reporting/data-collection/) | primär, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Cache-Typ-Deklaration | primär, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Konfiguration der Katalogattribute | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` und `env.php` | [Bereitstellungskonfiguration](../reference/deployment-files.md) | Diese Dateien können vom internen Konfigurationsprozessor gelesen/geschrieben werden. | Hat kein Objekt, kann nicht angepasst werden |
| `config.xml` | Systemkonfiguration | primär, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Definiert Aspekte des Meldungswarteschlangen-Systems](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Konfiguriert Cron-Gruppen](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Gibt die Optionen der Cron-Gruppe an](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Deklaratives Schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Dependency Injection](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) Konfiguration | primär, global, Bereich | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Stellt die EAV-Attributkonfiguration bereit | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Konfiguration von E-Mail-Vorlagen | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Konfiguration für Suchmaschinengebietsschema-Stoppwörter](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Ereignis-/Beobachterkonfiguration | global, area | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Entitätskonfiguration exportieren | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Erweiterungsattribute](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Definiert Feldsätze | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Deklariert Indexer](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Deklariert Importentitäten | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Definiert Menüelemente für den Administrator | adminHTML | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Definiert Modulkonfigurationsdaten und Soft-Abhängigkeiten | primär, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView-Konfiguration](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | primär, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Konfiguration des Zahlungsmoduls | primär, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | Konfigurationsdatei für [&#128279;](https://developer.adobe.com/commerce/php/module-reference/module-persistent/)Magento_Persistent | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF-Einstellungen | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Bietet eine Konfiguration der Produktoptionen | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Definiert den Produkttyp | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Definiert die Beziehung zwischen einer vorhandenen Warteschlange und ihrem Verbraucher](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Definiert den Austausch, in dem ein Thema veröffentlicht wird.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Definiert die Routing-Regeln für Nachrichten, deklariert Warteschlangen und Austausche](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Erweiterte Berichte](https://developer.adobe.com/commerce/php/development/advanced-reporting/report-xml/) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Definiert die Modulressource | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Route](https://developer.adobe.com/commerce/php/development/components/routing/)-Konfiguration | Bereich | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Definiert die Konfiguration des Gesamtverkaufs | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Stellt die Suchmaschinenkonfiguration bereit | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Definiert die Konfiguration der Katalogsuche | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Definiert Aktionen, die die Trigger-Cache-Invalidierung für private Inhaltsblöcke ermöglichen | Frontend | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Definiert Optionen für die Systemkonfigurationsseite | adminHTML | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Konfigurationsdatei für die Modulvalidierung | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Definiert Konfigurationswerte der Ansicht Vendor_Module . | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Konfiguriert eine Web-API](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Definiert benutzerdefinierte REST-Routen](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Definiert Widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Definiert das Postleitzahlformat für jedes Land | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Konfigurationsoberflächen

Sie können mit Konfigurationsdateien über Schnittstellen unter [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config) interagieren.

Sie können diese Schnittstellen verwenden, wenn Sie [einen Konfigurationstyp erstellen](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` bietet die folgenden Schnittstellen:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), das den XML-Code in eine speicherinterne Array-Darstellung der Konfigurationen konvertiert.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), das die Konfigurationsdaten in einem bestimmten Umfang abruft.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), das den Speicherort der Dateien angibt, die von [Magento\Framework\Config\ReaderInterface gelesen werden ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), das die Konfigurationsdaten aus dem Speicher liest und den Speicher auswählt, aus dem er liest.

Das heißt, das Dateisystem, die Datenbank und der andere Speicher führen die Konfigurationsdateien gemäß den Zusammenführungsregeln zusammen und validieren die Konfigurationsdateien mit den Validierungsschemata.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), das das XSD-Schema findet.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), das eine Liste von Bereichen zurückgibt.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), das den Validierungsstatus abruft.
