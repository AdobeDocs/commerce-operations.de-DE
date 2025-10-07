---
title: Konfigurationstypen
description: Erfahren Sie, wie Sie Konfigurationstypen in Adobe Commerce erstellen und erweitern. Erfahren Sie mehr über die Konfiguration von Modulen und Anpassungstechniken.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Konfigurationstypen

## Erweitern von Konfigurationstypen

Um einen vorhandenen Konfigurationstyp zu erweitern, müssen Sie nur eine Konfigurationsdatei in Ihrem Modul erstellen.

Um beispielsweise einen Ereignisbeobachter hinzuzufügen, erstellen Sie `app/code/{VendorName}/{ModuleName}/etc/events.xml` und deklarieren Sie einen neuen Beobachter.

Da der Ereigniskonfigurationstyp in Commerce vorhanden ist, sind das Ladeprogramm und das `events.xsd` Validierungsschema bereits vorhanden und funktionsfähig.

Ihre neue `events.xml` wird automatisch aus Ihrem -Modul erfasst und mit anderen `events.xml`-Dateien für andere Module zusammengeführt.

## Konfigurationstypen erstellen

Um einen Konfigurationstyp zu erstellen, müssen Sie mindestens Folgendes hinzufügen:

- Ein Lader
- XSD-Validierungsschema
- XML-Konfigurationsdateien

Um beispielsweise einen Adapter für einen neuen Suchserver einzuführen, der Erweiterungen die Konfiguration der Indexierung seiner Entitäten in diesem Server ermöglicht, erstellen Sie:

- Ein Lader
- Eine XSD-Schemadatei
- Eine entsprechend benannte Konfigurationsdatei. Beispiel: `search.xml`. Diese Datei wird gelesen und anhand Ihres Schemas validiert.
- Alle anderen Klassen, die für Ihre Arbeit erforderlich sind.

>[!INFO]
>
>Wenn neue Module eine `search.xml`-Datei haben, werden sie beim Laden mit Ihrer -Datei zusammengeführt.

### Anwendungsbeispiele

So erstellen Sie einen Konfigurationstyp:

1. Erstellen Sie Ihre XSD-Datei.
1. Erstellen Sie Ihre XML-Datei.
1. Definieren Sie Ihr Konfigurationsobjekt in Ihrem `di.xml`.

   Das folgende Beispiel aus der Datei &quot;[.xml“ des Moduls &quot;Magento_Sales](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) veranschaulicht, wie ein Konfigurationsobjekt aussehen sollte.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - Der erste Typknoten legt den Dateinamen der Reader, die zugehörigen `Converter` und `SchemaLocator` fest.
   - Anschließend hängt der Knoten vom Typ „Virtueller `pdfConfigDataStorage`&quot; die Readerklasse an eine Instanz von [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php) an.
   - Und schließlich hängt der letzte Typknoten diesen virtuellen Konfigurationstyp an die Klasse [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) an, die zum tatsächlichen Einlesen von Werten aus diesen PDF[xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml)-Dateien verwendet wird.

1. Definieren Sie einen Reader, indem Sie die Klasse {0[Magento\Framework\Config\Reader\Filesystem} erweitern und die folgenden Parameter neu schreiben:](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php)

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Beispiel:**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>Wenn Sie Ihre eigene Version des Readers erstellen möchten, können Sie dies tun, indem Sie `\Magento\Framework\Config\ReaderInterface` implementieren. Siehe [Magento_Analytics-Konfigurationsleser](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Nachdem Sie Ihren Reader definiert haben, verwenden Sie ihn zum Erfassen, Zusammenführen, Validieren und Konvertieren der Konfigurationsdateien in eine interne Array-Darstellung.

## Validieren eines Konfigurationstyps

Jede Konfigurationsdatei wird anhand eines Schemas validiert, das für ihren Konfigurationstyp spezifisch ist. Beispiel: Ereignisse, die in früheren Commerce-Versionen in `config.xml` konfiguriert wurden, werden jetzt in `events.xml` konfiguriert.

Konfigurationsdateien können sowohl vor (optional) als auch nach dem Zusammenführen mehrerer Dateien, die denselben Konfigurationstyp betreffen, validiert werden. Sofern die Validierungsregeln für die einzelnen und die zusammengeführten Dateien nicht identisch sind, sollten Sie zwei Schemata zur Validierung der Konfigurationsdateien bereitstellen:

- Schema zur Validierung eines Kontakts
- Schema zur Validierung einer zusammengeführten Datei

Neue Konfigurationsdateien müssen von XSD-Validierungsschemata begleitet werden. Eine XML-Konfigurationsdatei und die zugehörige XSD-Validierungsdatei müssen denselben Namen haben.

Wenn Sie zwei XSD-Dateien für eine einzelne XML-Datei verwenden müssen, sollten die Namen der Schemata erkennbar und mit der XML-Datei verknüpft sein.
Wenn Sie eine `events.xml` und eine erste `events.xsd` haben, können die XSD-Dateien für die zusammengeführte `events.xml`-Datei `events_merged.xsd` benannt werden.
Um die Validierung einer XML-Datei anhand der entsprechenden XSD-Datei sicherzustellen, müssen Sie der XSD-Datei in der XML-Datei den Uniform Resource Name (URN) hinzufügen. Beispiel:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Ihre IDE kann Ihre Konfigurationsdateien sowohl zur Laufzeit als auch während der Entwicklung überprüfen.
