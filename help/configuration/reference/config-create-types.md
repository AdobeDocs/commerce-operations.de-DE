---
title: Konfigurationstypen
description: Erstellen oder erweitern Sie Konfigurationstypen.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Konfigurationstypen

## Erweitern von Konfigurationstypen

Um einen vorhandenen Konfigurationstyp zu erweitern, müssen Sie nur eine Konfigurationsdatei in Ihrem -Modul erstellen.

Um beispielsweise einen Ereignisbeobachter hinzuzufügen, erstellen Sie `app/code/{VendorName}/{ModuleName}/etc/events.xml` und deklarieren einen neuen Beobachter.

Da der Ereignistyp in Commerce vorhanden ist, sind das Validierungsschema loader und `events.xsd` bereits vorhanden und funktionsfähig.

Ihr neuer `events.xml` wird automatisch aus Ihrem Modul erfasst und mit anderen `events.xml` -Dateien für andere Module zusammengeführt.

## Erstellen von Konfigurationstypen

Um einen Konfigurationstyp zu erstellen, müssen Sie mindestens Folgendes hinzufügen:

- Lader
- XSD-Validierungsschema
- XML-Konfigurationsdateien

Um beispielsweise einen Adapter für einen neuen Suchserver einzuführen, mit dem Erweiterungen konfigurieren können, wie seine Entitäten in diesem Server indiziert werden, erstellen Sie:

- Lader
- Eine XSD-Schemadatei
- Eine entsprechend benannte Konfigurationsdatei. Beispiel: `search.xml`. Diese Datei wird anhand Ihres Schemas gelesen und validiert.
- Alle anderen Klassen, die für Ihre Arbeit erforderlich sind.

>[!INFO]
>
>Wenn neue Module eine `search.xml` -Datei haben, werden sie beim Laden mit Ihrer Datei zusammengeführt.

### Anwendungsbeispiele

So erstellen Sie einen Konfigurationstyp:

1. Erstellen Sie Ihre XSD-Datei.
1. Erstellen Sie Ihre XML-Datei.
1. Definieren Sie Ihr Konfigurationsobjekt in Ihrem `di.xml`.

   Das folgende Beispiel aus dem [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) des Magento_Sales-Moduls zeigt, wie ein Konfigurationsobjekt aussehen sollte.

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

   - Der erste Knotentyp legt den Dateinamen des Readers fest, die zugehörigen `Converter` - und `SchemaLocator` -Klassen.
   - Anschließend hängt der virtuelle Knoten `pdfConfigDataStorage` die Leserklasse an eine Instanz von [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php) an.
   - Und schließlich hängt der Knoten des letzten Typs diesen virtuellen Konfigurationsdatentyp an die Klasse [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) an, die zum tatsächlichen Lesen von Werten in aus diesen [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) -Dateien verwendet wird.

1. Definieren Sie einen Leser, indem Sie die Klasse [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) erweitern und die folgenden Parameter neu schreiben:

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
>Wenn Sie lieber eine eigene Version des Readers erstellen möchten, können Sie dies durch Implementierung von `\Magento\Framework\Config\ReaderInterface` tun. Siehe [Magento_Analytics-Konfigurationsleser](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Nachdem Sie Ihren Leser definiert haben, verwenden Sie ihn zum Erfassen, Zusammenführen, Überprüfen und Konvertieren der Konfigurationsdateien in eine interne Array-Darstellung.

## Validieren eines Konfigurationstyps

Jede Konfigurationsdatei wird anhand eines für ihren Konfigurationstyp spezifischen Schemas validiert. Beispiel: Ereignisse, die in früheren Commerce-Versionen in `config.xml` konfiguriert wurden, werden jetzt in `events.xml` konfiguriert.

Konfigurationsdateien können sowohl vor (optional) als auch nach jeder Zusammenführung mehrerer Dateien überprüft werden, die sich auf denselben Konfigurationstyp auswirken. Sofern die Validierungsregeln für die einzelnen und die zusammengeführten Dateien nicht identisch sind, sollten Sie zwei Schemas zur Validierung der Konfigurationsdateien bereitstellen:

- Schema zur Validierung eines einzelnen
- Schema zur Validierung einer zusammengeführten Datei

Neue Konfigurationsdateien müssen von XSD-Validierungsschemas begleitet werden. Eine XML-Konfigurationsdatei und ihre XSD-Validierungsdatei müssen denselben Namen haben.

Wenn Sie zwei XSD-Dateien für eine einzelne XML-Datei verwenden müssen, sollten die Namen der Schemas erkannt und mit der XML-Datei verknüpft werden.
Wenn Sie eine `events.xml` -Datei und eine erste `events.xsd` -Datei haben, können die XSD-Dateien für die zusammengeführte `events.xml` -Datei den Namen `events_merged.xsd` haben.
Um die Validierung einer XML-Datei anhand der entsprechenden XSD-Datei sicherzustellen, müssen Sie die Uniform Resource Name (URN) zur XSD-Datei in der XML-Datei hinzufügen. Beispiel:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Ihre IDE kann Ihre Konfigurationsdateien sowohl zur Laufzeit als auch während der Entwicklung überprüfen.
