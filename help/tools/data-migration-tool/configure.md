---
title: Konfigurieren des  [!DNL Data Migration Tool]
description: Erfahren Sie mehr über die beiden Methoden zum Konfigurieren von  [!DNL Data Migration Tool] , um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# Konfigurieren des [!DNL Data Migration Tool]

Nach der Installation des [!DNL Data Migration Tool] enthält das folgende Verzeichnis Zuordnungs- und Konfigurationsdateien:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Konfiguration und Skripte für die Migration von Magento Open Source 1 zu Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Konfiguration und Skripte für die Migration von Magento Open Source 1 zu Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Konfiguration und Skripte für die Migration von Adobe Commerce 1 zu Adobe Commerce 2

Die vorherigen Verzeichnisse enthalten Unterverzeichnisse für jede unterstützte Version.

## Konfigurieren der Migration

Es gibt zwei Möglichkeiten, die [!DNL Data Migration Tool] zu konfigurieren:

* Konfigurieren des [!DNL Data Migration Tool] in einem separaten Modul (empfohlen)
* Ändern Sie die [!DNL Data Migration Tool] im `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/`.

Um die Quellcodeverwaltung für die Verwaltung der Migrationskonfiguration und die Bereitstellung zu verwenden, müssen Sie ein separates Modul erstellen.
Wenn Sie die [!DNL Data Migration Tool] nur lokal ausführen möchten, können Sie Dateien im `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` direkt bearbeiten.

### Konfigurieren der Migration in einem separaten Modul

Bevor Sie Daten migrieren, müssen Sie ein Magento 2 -Modul erstellen.

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

1. Kopieren Sie die `config.xml.dist` Konfigurationsdatei aus dem entsprechenden Verzeichnis der [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) in die `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml`.

   Wenn Sie beispielsweise `Magento 1.9.3.6 Community Edition` nach `Magento 2 Open Source` migrieren:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. In der `config.xml` müssen Sie die Zugriffsdetails auf M1- und M2-Datenbanken und den Verschlüsselungsschlüssel festlegen.

1. Wenn Ihr M1-Store benutzerdefinierte Änderungen enthält, sollten Sie den Rest Ihrer Konfigurationsdateien Ihren Magento 1-Store-Anpassungen zuordnen. Siehe [Arbeiten mit Konfigurations- und &#x200B;](#migration-config).

### Konfigurieren der Migration in `vendor` Ordner

Bevor Sie Daten migrieren, müssen Sie eine `config.xml` Konfigurationsdatei aus dem bereitgestellten Beispiel erstellen.

So konfigurieren Sie die [!DNL Data Migration Tool] für die Migration:

1. Melden Sie sich bei Ihrem Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).

1. Wechseln Sie in das folgende Verzeichnis:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Geben Sie den folgenden Befehl ein, um einen `config.xml` aus dem bereitgestellten Beispiel zu erstellen:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Öffnen Sie `config.xml` in einem Texteditor.

1. Die Datei config.xml muss mindestens Zugriffsdetails für M1- und M2-Datenbanken und Verschlüsselungsschlüssel enthalten.

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

   Das Tag &lt;crypt_key> muss einen Wert enthalten. Sie finden es im `<key>`-Tag, das sich in der Datei app/etc/local.xml auf Ihrer Magento 1-Instanz befindet.

   Optionale Parameter:

   * Kennwort des Datenbankbenutzers: `password=<password>`
   * Benutzerdefinierter Datenbank-Port: `port=<port>`
   * Tabellenpräfix: `<source_prefix>`, `<dest_prefix>`

   Wenn beispielsweise der Benutzername Ihres Datenbankbesitzers mit dem Kennwort `root` `pass` ist und Sie das Präfix `magento1` in Ihrer Magento 1-Datenbank verwenden, verwenden Sie Folgendes in `config.xml`:

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

Wenn Sie fertig sind, speichern Sie Ihre Änderungen in `config.xml` und beenden Sie den Texteditor.

### Verbinden mit dem TLS-Protokoll

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

## Arbeiten mit Konfigurations- und Zuordnungsdateien

Der [!DNL Data Migration Tool] verwendet *Zuordnungsdateien*, um Ihnen eine benutzerdefinierte Datenbankzuordnung zwischen Ihren Magento 1- und Magento 2-Datenbanken zu ermöglichen, einschließlich:

* Ändern von Tabellennamen

* Ändern von Feldnamen

* Tabellen oder Felder werden ignoriert

* Anpassen der Übertragung von Daten eines Felds in das Magento 2-Format

Zuordnungsdateien für unterstützte Magento-Versionen befinden sich in Unterverzeichnissen von `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

So verwenden Sie die Zuordnungsdateien:

1. Kopieren Sie sie von `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` nach `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` und entfernen Sie die `.dist`.

1. Aktualisieren Sie den Pfad zur neu kopierten Datei im `<options>` Knoten von `config.xml`. Der aktualisierte Pfad sollte einer der folgenden sein:

   1. Absoluter Dateipfad, z. B. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento/data-migration-tool-Modul Relativer Dateipfad: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Stammbezogener Dateipfad von Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

Die `<Magento 2 dir>/vendor/magento/data-migration-tool/etc`- und `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>`-Verzeichnisse enthalten die folgenden Konfigurationsdateien:

Obwohl Sie die meiste Zeit mit der `map.xml.dist`-Datei arbeiten, werden in der folgenden Tabelle die einzelnen Zuordnungsdateien und andere Dateien erläutert.

| Name der Zuordnungsdatei | Beschreibung |
| --- | --- |
| `class-map.xml.dist` | Wörterbuch der Klassenzuordnungen zwischen Magento 1 und Magento 2 |
| `config.xml.dist` | Hauptkonfigurationsdatei, die die Magento 1- und Magento 2-Datenbankkonfigurationen, die Schrittkonfiguration und Links zu Zuordnungsdateien angibt |
| *Nur Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Liste der im Schritt „Benutzerdefinierte Kundenattribute“ verwendeten Tabellen. |
| *Nur Adobe Commerce*. `customer-attr-map.xml.dist` | Zuordnungsdatei, die im Schritt Benutzerdefinierte Kundenattribute verwendet wird. |
| `deltalog.xml.dist` | Enthält die Liste der Tabellen, die für die Einrichtung von Datenbankroutinen erforderlich sind. |
| `eav-attribute-groups.xml.dist` | Enthält eine Liste der Attribute, die in EAV-Schritt verwendet werden. |
| `eav-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die in EAV-Schritt verwendet werden. |
| `log-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die im Protokollschritt verwendet werden. |
| `map-eav.xml.dist` | Zuordnungsdatei, die im EAV-Schritt verwendet wird. |
| `map-log.xml.dist` | Protokollzuordnungsdatei |
| *Nur Adobe Commerce*. `map-sales.xml.dist` | Zuordnungsdatei, die im SalesOrder-Schritt verwendet wird. |
| `map.xml.dist` | Zuordnungsdatei für den Zuordnungsschritt erforderlich. |
| `settings.xml.dist` | Festlegen einer Migrationskonfigurationsdatei, die die für die Migration der `core_config_data` erforderlichen Regeln angibt. |
| `customer-attribute-groups.xml.dist` | Enthält eine Liste der Attribute, die im Schritt Kundenattribute verwendet werden. |
| `customer-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die im Schritt Kundenattribute verwendet werden. |
| `map-customer.xml.dist` | Zuordnungsdatei, die im Schritt Kundenattribute verwendet wird. |
| `order-grids-document-groups.xml.dist` | Enthält eine Liste der Tabellen, die in OrderGrids Step verwendet werden. |
| `map-document-groups.xml.dist` | Definiert, welche Felder aktualisiert werden, wenn beim Einfügen von Daten Duplikate auftreten |
| `map-stores.xml.dist` | Zuordnungsdatei, die im Schritt „Stores“ verwendet wird. |
| `map-tier-price.xml.dist` | Zuordnungsdatei, die im Schritt „Preisstufe“ verwendet wird. |
| *Nur Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Zuordnungsdatei, die im Visual Merchandiser-Schritt verwendet wird. |
| *Nur Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Enthält eine Liste der Attribute, die in Visual Merchandiser Step verwendet werden. |
| *Nur Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Enthält eine Liste der Tabellen, die in Visual Merchandiser Step verwendet werden. |

Weitere Informationen finden Sie [[!DNL Data Migration Tool] Technische Spezifikation](technical-specification.md).
