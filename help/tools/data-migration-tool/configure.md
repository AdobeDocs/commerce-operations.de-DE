---
title: Konfigurieren Sie die [!DNL Data Migration Tool]
description: Erfahren Sie mehr über die beiden Methoden zum Konfigurieren der [!DNL Data Migration Tool] zur Übertragung von Daten zwischen Magento 1 und Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Konfigurieren Sie die [!DNL Data Migration Tool]

Nach der Installation [!DNL Data Migration Tool], enthält der folgende Ordner Zuordnungs- und Konfigurationsdateien:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Konfiguration und Skripte für die Migration von Magento Open Source 1 zu Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Konfiguration und Skripte für die Migration von Magento Open Source 1 zu Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Konfiguration und Skripte für die Migration von Adobe Commerce 1 zu Adobe Commerce 2

Die vorherigen Ordner enthalten Unterverzeichnisse für jede unterstützte Version.

## Konfigurieren der Migration

Es gibt zwei Möglichkeiten, die [!DNL Data Migration Tool]:

* Konfigurieren Sie die [!DNL Data Migration Tool] in einem separaten Modul (empfohlen)
* Ändern Sie die [!DNL Data Migration Tool] Konfiguration in der `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` Verzeichnis.

Um die Migrationskonfiguration mithilfe der Quellcodeverwaltung zu verwalten und für die Bereitstellung zu verwenden, müssen Sie ein separates Modul erstellen.
Wenn Sie die [!DNL Data Migration Tool] Nur lokal können Sie Dateien im `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` -Verzeichnis.

### Konfigurieren der Migration in einem separaten Modul

Bevor Sie Daten migrieren, müssen Sie ein Magento 2-Modul erstellen.

1. Erstellen Sie ein Magento 2-Modul.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Kopieren Sie die `config.xml.dist` Konfigurationsdatei aus dem entsprechenden Verzeichnis der [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) in die `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` -Datei.

   Wenn Sie beispielsweise `Magento 1.9.3.6 Community Edition` nach `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. Im `config.xml` -Datei, müssen Sie die Zugriffsdetails für die M1- und M2-Datenbanken und den Verschlüsselungsschlüssel festlegen.

1. Wenn Ihr M1-Store benutzerdefinierte Änderungen aufweist, sollten Sie den Rest Ihrer Konfigurationsdateien Ihren Magento 1-Store-Anpassungen zuordnen. Siehe [Arbeiten mit Konfigurations- und Zuordnungsdateien](#migration-config).

### Konfigurieren der Migration in `vendor` Ordner

Bevor Sie Daten migrieren, müssen Sie eine `config.xml` Konfigurationsdatei aus dem bereitgestellten Beispiel.

So konfigurieren Sie die [!DNL Data Migration Tool] für die Migration:

1. Melden Sie sich bei Ihrem Anwendungsserver als an oder wechseln Sie zu der [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).

1. Wechseln Sie in den folgenden Ordner:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Geben Sie den folgenden Befehl ein, um eine `config.xml` aus der mitgelieferten Probe:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Öffnen `config.xml` in einem Texteditor.

1. Die Datei &quot;config.xml&quot;muss mindestens Zugriffsdetails zu den Datenbanken von M1 und M2 sowie Verschlüsselungsschlüssel enthalten.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   Die &lt;crypt_key> -Tag muss einen Wert enthalten. Sie finden sie im `<key>` -Tag, das sich in der Datei app/etc/local.xml auf Ihrer Magento 1-Instanz befindet.

   Optionale Parameter:

   * Datenbankbenutzerkennwort: `password=<password>`
   * Benutzerdefinierter Datenbankport: `port=<port>`
   * Tabellenpräfix: `<source_prefix>`, `<dest_prefix>`

   Wenn der Benutzername Ihres Datenbankinhabers beispielsweise `root` mit Kennwort `pass` und Sie verwenden das Präfix `magento1` Verwenden Sie in Ihrer Magento 1-Datenbank Folgendes in `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

Speichern Sie abschließend Ihre Änderungen in `config.xml` und beenden Sie den Texteditor.

### Verbindung mit dem TLS-Protokoll herstellen

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

## Arbeiten mit Konfigurations- und Zuordnungsdateien

Die [!DNL Data Migration Tool] uses *Zuordnungsdateien* , damit Sie eine benutzerdefinierte Datenbankzuordnung zwischen Ihren Magento 1- und Magento 2-Datenbanken durchführen können, einschließlich:

* Ändern von Tabellennamen

* Ändern von Feldnamen

* Ignorieren von Tabellen oder Feldern

* Anpassen der Übertragung von Daten eines Felds in das Magento 2-Format

Zuordnungsdateien für unterstützte Magento-Versionen befinden sich in Unterverzeichnissen von `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

So verwenden Sie die Zuordnungsdateien:

1. Kopieren Sie sie aus `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` nach `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` und entfernen Sie die `.dist` [Erweiterung](https://glossary.magento.com/extension).

1. Aktualisieren Sie den Pfad zur neu kopierten Datei im `<options>` Knoten von `config.xml`. Der aktualisierte Pfad sollte einer der folgenden sein:

   1. Absoluter Dateipfad, z. B. g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool-Modul relativer Dateipfad: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento-Stammverzeichnis-relativer Dateipfad: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

Die `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` und `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` -Verzeichnisse enthalten die folgenden Konfigurationsdateien:

Auch wenn Sie mit der `map.xml.dist` meistens werden in der folgenden Tabelle alle Mapping- und anderen Dateien erläutert.

| Dateinamen zuordnen | Beschreibung |
| --- | --- |
| `class-map.xml.dist` | Wörterbuch der Klassenzuordnungen zwischen Magento 1 und Magento 2 |
| `config.xml.dist` | Hauptkonfigurationsdatei, die die Datenbankkonfigurationen für Magento 1 und Magento 2, die Schrittkonfiguration und die Links zu Zuordnungsdateien angibt |
| *Nur Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Liste der Tabellen, die im Schritt für benutzerdefinierte Kundenattribute verwendet werden. |
| *Nur Adobe Commerce*. `customer-attr-map.xml.dist` | Zuordnungsdatei, die im Schritt &quot;Benutzerdefinierte Kundenattribute&quot;verwendet wird. |
| `deltalog.xml.dist` | Enthält die Liste der Tabellen, die für die Einrichtung von Datenbankroutinen erforderlich sind. |
| `eav-attribute-groups.xml.dist` | Enthält eine Liste der Attribute, die in jedem Schritt verwendet werden. |
| `eav-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die in jedem Schritt verwendet werden. |
| `log-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die im Protokollschritt verwendet werden. |
| `map-eav.xml.dist` | Zuordnungsdatei, die im EAV-Schritt verwendet wird. |
| `map-log.xml.dist` | Protokollzuordnungsdatei. |
| *Nur Adobe Commerce*. `map-sales.xml.dist` | Zuordnungsdatei, die im SalesOrder-Schritt verwendet wird. |
| `map.xml.dist` | Zuordnungsdatei, die für den Schritt &quot;Zuordnung&quot;erforderlich ist. |
| `settings.xml.dist` | Festlegen der Konfigurationsdatei für die Migration, die die für die Migration der `core_config_data` Tabelle. |
| `customer-attribute-groups.xml.dist` | Enthält eine Liste der Attribute, die im Schritt &quot;Kundenattribute&quot;verwendet werden. |
| `customer-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die im Schritt &quot;Kundenattribute&quot;verwendet werden. |
| `map-customer.xml.dist` | Zuordnungsdatei, die im Schritt &quot;Kundenattribute&quot;verwendet wird. |
| `order-grids-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die im Schritt &quot;OrderGrids&quot;verwendet werden. |
| `map-document-groups.xml.dist` | Definiert, welche Felder aktualisiert werden, wenn beim Einfügen von Daten Duplikate auftreten |
| `map-stores.xml.dist` | Zuordnungsdatei, die im Store-Schritt verwendet wird. |
| `map-tier-price.xml.dist` | Zuordnungsdatei, die im Schritt &quot;Level Price&quot;verwendet wird. |
| *Nur Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Zuordnungsdatei, die im VisualMerchandiser-Schritt verwendet wird. |
| *Nur Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Enthält eine Liste der Attribute, die im VisualMerchandiser-Schritt verwendet werden. |
| *Nur Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Enthält eine Liste der Tabellen, die im VisualMerchandiser-Schritt verwendet werden. |

Weitere Informationen finden Sie unter [[!DNL Data Migration Tool] Technische Spezifikation](technical-specification.md) für weitere Details.
