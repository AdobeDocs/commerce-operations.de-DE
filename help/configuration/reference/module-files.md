---
title: Modulkonfigurationsdateien
description: Erfahren Sie, wie Sie ein Modul mithilfe von Konfigurationstypen anpassen.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---

# Überblick über die Modulkonfigurationsdateien

Die Zuständigkeiten der `config.xml` Die Konfigurationsdatei, die in früheren Versionen von Commerce verwendet wird, ist jetzt zwischen mehreren Dateien unterteilt, die sich in verschiedenen Modulverzeichnissen befinden. Die verschiedenen Konfigurationsdateien von Commerce werden nur bei Bedarf geladen, wenn ein Modul einen bestimmten Konfigurationstyp anfordert.

Sie können diese Dateien verwenden, die auch als _Konfigurationstypen_—um bestimmte Aspekte des Verhaltens Ihres Moduls anzupassen.

Mehrere Module können Konfigurationsdateien deklarieren, die denselben Konfigurationstyp betreffen (z. B. Ereignisse), und diese verschiedenen Konfigurationsdateien werden zusammengeführt.

In diesem Thema werden häufig Begriffe verwendet:

- **Konfigurationsobjekt**—Die Commerce-Bibliothek oder -Klasse, die für die Definition und Validierung des Konfigurationstyps zuständig ist. Beispielsweise das Konfigurationsobjekt für `config.xml` is [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Konfigurationsphase**—Phasen sind definiert als _primary_, _global_, und _area_. Jede Phase bestimmt, wann der Konfigurationstyp geladen und mit denselben benannten Konfigurationstypen zusammengeführt wird. Beispiel: `module.xml` Dateien mit anderen zusammengeführt werden `module.xml` -Dateien.

- **Konfigurationsbereich**—Ergänzend zu den Konfigurationsphasen definiert ein Perimeter das Konfigurationstypmodell. Beispiel: `adminhtml` ist ein Bereichsbereich, der im Moment mit anderen Modulen geladen wird. `adminhtml` -Konfigurationen. Weitere Informationen finden Sie unter [Module und Bereiche](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Laden und Zusammenführen von Konfigurationen

In diesem Abschnitt wird erläutert, wie Konfigurationsdateien geladen und zusammengeführt werden.

### Wie Commerce Konfigurationsdateien lädt

Commerce lädt Konfigurationsdateien in der folgenden Reihenfolge (alle Pfade beziehen sich auf Ihr Commerce-Installationsverzeichnis):

- Primäre Konfiguration ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Diese Datei wird zum Bootstrapping von Commerce verwendet.
- Globale Konfigurationen von Modulen (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Erfasst bestimmte Konfigurationsdateien aus allen Modulen und führt sie zusammen.
- Gebietsspezifische Konfiguration von Modulen (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Erfasst Konfigurationsdateien aus allen Modulen und führt sie in der globalen Konfiguration zusammen. Einige gebietsspezifische Konfigurationen können die globale Konfiguration überschreiben oder erweitern.

where

- `<your component base dir>` ist das Basisverzeichnis, in dem sich Ihre Komponente befindet. Typische Werte sind `app/code` oder `vendor` relativ zum Installationsordner von Commerce.
- `<vendorname>` ist der Name des Anbieters der Komponente. Der Name des Anbieters in Commerce lautet beispielsweise `magento`.
- `<component-type>` ist einer der folgenden Werte:

   - `module-`: Eine Erweiterung oder ein Modul.
   - `theme-`: Design.
   - `language-`: Sprachpaket.

>[!INFO]
>
>Derzeit befinden sich die Designs unter `<magento_root>/app/design/frontend` oder `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Name der Komponente, wie definiert in [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Zusammenführen von Konfigurationsdateien

Knoten in Konfigurationsdateien werden basierend auf ihren vollständig qualifizierten XPaths zusammengeführt, wobei ein spezielles Attribut definiert ist in `$idAttributes` -Array, das als Kennung deklariert ist. Diese Kennung muss für alle Knoten eindeutig sein, die unter demselben übergeordneten Knoten verschachtelt sind.

Commerce-Anwendungszusammenführungsalgorithmus:

- Wenn Knotenkennungen gleich sind (oder keine Kennung definiert ist), wird der gesamte zugrunde liegende Inhalt im Knoten (Attribute, untergeordnete Knoten und skalare Inhalte) überschrieben.
- Wenn Knotenkennungen nicht gleich sind, ist der Knoten ein neues untergeordnetes Element des übergeordneten Knotens.
- Wenn das Originaldokument mehrere Knoten mit derselben Kennung enthält, wird ein Fehler ausgelöst, da die Kennungen nicht identifiziert werden können.

Nachdem die Konfigurationsdateien zusammengeführt wurden, enthält das resultierende Dokument alle Knoten aus den Originaldateien.

>[!INFO]
>
>Sie können [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) -Klasse zum Debuggen und Verständnis der Logik hinter [Ladeprogramm für Konfigurationsdateien](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) und [Zusammenführungskonfigurationen](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) -Prozess.

## Konfigurationstypen, -objekte und -schnittstellen

Die folgenden Abschnitte enthalten Informationen zu Konfigurationstypen, den zugehörigen Konfigurationsobjekten und Schnittstellen, die Sie zum Arbeiten mit den Objekten verwenden können:

### Konfigurationstypen und -objekte

In der folgenden Tabelle sind alle Konfigurationstypen und das Commerce-Konfigurationsobjekt aufgeführt, auf das sie sich beziehen.

| Konfigurationsdatei | Beschreibung | Staging | Konfigurationsobjekt |
| --- | --- | --- | --- |
| `address_formats.xml` | Adressenformatdeklaration | primary, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Zugriffssteuerungsliste](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Erweiterte Berichterstellung](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | primary, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Cache-Typdeklaration | primary, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Konfiguration von Katalogattributen | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` und `env.php` | [Bereitstellungskonfiguration](../reference/deployment-files.md) | Diese Dateien sind vom internen Konfigurationsprozessor lesbar/beschreibbar. | Hat kein Objekt, kann nicht angepasst werden |
| `config.xml` | Systemkonfiguration | primary, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Definiert Aspekte des Nachrichtenwarteschlangensystems](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Konfigurationen von Cron-Gruppen](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Gibt Cron-Gruppenoptionen an](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Deklaratives Schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Injektion der Abhängigkeit](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) Konfiguration | primary, global, area | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Konfiguration von EAV-Attributen | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Konfiguration von E-Mail-Vorlagen | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Konfiguration der Gebietsschema-Stoppwörter der Suchmaschine](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Ereignis-/Beobachter-Konfiguration | global, area | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Konfiguration der Exportentität | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Erweiterungsattribute](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Definiert Feldsätze | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Deklariert Indexer](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Deklariert Importentitäten | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Definiert Menüelemente für den Administrator | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Definiert Modulkonfigurationsdaten und weiche Abhängigkeit | primary, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView-Konfiguration](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | primary, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Konfiguration des Zahlungsmoduls | primary, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) Konfigurationsdatei | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF-Einstellungen | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Konfiguration von Produktoptionen | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Definiert den Produkttyp | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Definiert die Beziehung zwischen einer vorhandenen Warteschlange und ihrem Verbraucher](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Definiert den Austausch, bei dem ein Thema veröffentlicht wird.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Definiert die Routing-Regeln für Nachrichten, deklariert Warteschlangen und Austausche](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Erweiterte Berichte](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Definiert die Modulressource | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Route](https://developer.adobe.com/commerce/php/development/components/routing/) Konfiguration | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Definiert die Konfiguration der Verkaufssumme | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Suchmaschinenkonfiguration | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Definiert die Konfiguration der Katalogsuche | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Definiert Aktionen, bei denen die Invalidierung des Triggers-Cache für private Inhaltsbausteine durchgeführt wird | frontend | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Definiert Optionen für die Systemkonfigurationsseite | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Konfigurationsdatei für Modulvalidierung | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Definiert Konfigurationswerte der Ansicht &quot;Vendor_Module&quot; | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Web-API konfigurieren](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Definiert benutzerdefinierte REST-Routen](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Definiert Widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Definiert das Postleitzahlformat für jedes Land | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Konfigurationsoberflächen

Sie können mit Konfigurationsdateien über Schnittstellen unter interagieren [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Sie können diese Schnittstellen verwenden, wenn Sie [Konfigurationstyp erstellen](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` stellt die folgenden Schnittstellen bereit:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), wodurch die XML in eine speicherinterne Array-Darstellung der Konfigurationen konvertiert wird.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), der die Konfigurationsdaten in einem bestimmten Umfang abruft.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), der den Speicherort der Dateien angibt, die von gelesen werden sollen [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), der die Konfigurationsdaten aus dem Speicher liest und den Speicher auswählt, von dem aus sie gelesen werden.

Das heißt, das Dateisystem, die Datenbank und der andere Speicher führen die Konfigurationsdateien gemäß den Zusammenführungsregeln zusammen und validieren die Konfigurationsdateien mit den Validierungsschemas.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), das das XSD-Schema lokalisiert.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), der eine Liste von Bereichen zurückgibt.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), der den Validierungsstatus abruft.
