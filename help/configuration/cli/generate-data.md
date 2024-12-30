---
title: Generieren von Daten für Leistungstests
description: Erfahren Sie, wie Sie eine große Datenmenge generieren, die für Leistungstests verwendet werden kann.
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 9%

---

# Leistungstestdaten

## Profile

Sie können die von Ihnen erstellte Datenmenge mithilfe von _Profilen_ anpassen (klein, mittel, groß und extra groß). Profile befinden sich im `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>`.

Beispiel: `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

Die folgende Abbildung zeigt, wie ein Produkt in der Storefront mithilfe des Profils _klein_ angezeigt wird:

![Beispiel-Storefront mit generierten Daten](../../assets/configuration/generate-data.png)

Die folgende Tabelle enthält Details zu den Datengeneratorprofilen: klein, mittel, groß und extra groß.

| Parameter | Kleines Profil | Medium-Profil | Medium-Profil für mehrere Sites | Großes Profil | Extra großes Profil |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24.000 | 4.000 | 300.000 | 600.000 |
| `configurable_products` | 16 mit 24 Optionen | 640 mit 24 Optionen | 800 mit 24 Optionen und 79 mit 200 Optionen | 8.000 mit 24 Optionen | 16.000 mit 24 Optionen |
| `product_images` | 100 Bilder / 3 Bilder pro Produkt | 1000 Bilder / 3 Bilder pro Produkt | 1000 Bilder / 3 Bilder pro Produkt | 2000 Bilder / 3 Bilder pro Produkt | 2000 Bilder / 3 Bilder pro Produkt |
| `categories` | 30 | 300 | 100 | 3.000 | 6.000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2.000 | 2.000 | 5.000 | 10.000 |
| `tax rates` | 130 | 40.000 | 40.000 | 40.000 | 40.000 |
| `orders` | 80 | 50.000 | 50.000 | 100.000 | 150.000 |

### Ausführen des Datengenerators

{{file-system-owner}}

>[!WARNING]
>
>Deaktivieren Sie vor dem Ausführen des Datengenerators alle auf dem Server ausgeführten Cron-Aufträge. Durch Deaktivieren von Cron-Aufträgen wird verhindert, dass der Datengenerator Aktionen ausführt, die mit aktiven Cron-Aufträgen in Konflikt stehen, und unnötige Fehler werden vermieden.
>
>Wenn Sie beim Testen der Leistung das Eventing mit [!DNL Adobe I/O Events for Adobe Commerce] implementieren möchten, führen Sie diesen Befehl aus, bevor Sie [Ereignisse](https://developer.adobe.com/commerce/extensibility/events/) abonnieren. Das Abonnieren von Ereignissen kann zu Fehlern führen.

Führen Sie den Befehl wie in diesem Abschnitt beschrieben aus. Nach Ausführung des Befehls müssen Sie [alle Indexer neu indizieren](../cli/manage-indexers.md).

Befehlsoptionen:

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

Dabei gibt `<path-to-profile>` den absoluten Dateisystempfad zu einem Profil und dessen Namen an.

Beispiel:

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

Beispielausgabe für das kleine Profil:

```
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## Leistungsmerkmale

### Admin-Benutzer

Erzeugt Admin-Benutzer. XML-Profilknoten:

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### Attributsätze

Erzeugt Attributsätze mit festgelegter Konfiguration. XML-Profilknoten:

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### Produkte im Paket

Erzeugt Bundle-Produkte. Generierte Bundle-Auswahlen werden nicht einzeln im Katalog angezeigt. Die Produkte werden einheitlich nach Kategorien und Websites verteilt. Wenn `assign_entities_to_all_websites` aus dem Profil auf `1` gesetzt ist. Produkte werden allen Websites zugewiesen.

XML-Profilknoten:

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### Warenkorb-Preisregeln

Erstellt Regeln für den Warenkorbpreis. XML-Profilknoten:

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### Katalogpreisregeln

Erzeugt Katalogpreisregeln. XML-Profilknoten:

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### Kategorien

Erzeugt Kategorien. Wenn `assign_entities_to_all_websites` auf `0` gesetzt ist, werden alle Kategorien gleichmäßig nach Stammkategorien verteilt. Andernfalls werden alle Kategorien einer Stammkategorie zugewiesen.

XML-Profilknoten:

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### Konfigurationen

Legt Werte für Konfigurationsfelder fest. XML-Profilknoten:

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### Konfigurierbare Produkte

Erzeugt konfigurierbare Produkte. Generierte konfigurierbare Optionen werden nicht einzeln im Katalog angezeigt. Die Produkte werden einheitlich nach Kategorien und Websites verteilt. Wenn `assign_entities_to_all_websites` auf `1` gesetzt ist, werden die Produkte allen Websites zugewiesen.

Die folgenden XML-Knotenformate werden unterstützt:

- Verteilung nach Standard- und vordefinierten Attributsätzen:

  ```xml
  <!-- Number of configurable products -->
  <configurable_products>{int}</configurable_products>
  ```

- Generieren von Produkten basierend auf einem vorhandenen Attributsatz:

  ```xml
  <configurable_products>
  
      <config>
              <!-- Existing attribute set name -->
              <attributeSet>{string}</attributeSet>
  
              <!-- Configurable sku pattern with %s -->
              <sku>{string}</sku>
  
              <!-- Number of configurable products -->
              <products>{int}</products>
  
              <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
              <category>[{string}]</category>
  
              <!-- Type of Swatch attribute e.g. color|image -->
              <swatches>{string}</swatches>
      </config>
  
  <!-- ... more entries ... -->
  </configurable_products>
  ```

- Generieren von Produkten basierend auf einem dynamisch erstellten Attributsatz mit einer bestimmten Anzahl von Attributen und Optionen:

  ```xml
  <configurable_products>
  
      <config>
          <!-- Number of attributes in configurable product -->
          <attributes>{int}</attributes>
  
          <!-- Number of options per attribute -->
          <options>{int}</options>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
          <category>[{string}]</category>
  
          <!-- Type of Swatch attribute e.g. color|image -->
          <swatches>{string}</swatches>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

- Generieren von Produkten basierend auf einem dynamisch erstellten Attributsatz mit einer für jedes Attribut angegebenen Konfiguration:

  ```xml
  <configurable_products>
  
      <config>
          <attributes>
              <!-- Configuration for a first attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
  
                  <!-- Type of Swatch attribute -->
                  <swatches>{string}</swatches>
              </attribute>
  
              <!-- Configuration for a second attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
              </attribute>
          </attributes>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
          <category>[{string}]</category>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

### Kunden

Erzeugt Kunden. Kunden haben eine Standardverteilung auf allen verfügbaren Websites. Jeder Kunde hat dieselben Daten außer Kunden-E-Mail, Kundengruppe und Kundenadressen.

XML-Profilknoten:

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

Sie können die folgende XML verwenden, um die Kundenkonfiguration zu ändern:

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### Produktbilder

Erzeugt Produktbilder. Die Generierung umfasst nicht die Größenanpassung.

XML-Profilknoten:

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### Indexerstatus

Aktualisiert den Status der Indexer. XML-Profilknoten:

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### Bestellungen

Erzeugt Bestellungen mit einer konfigurierbaren Anzahl unterschiedlicher Bestellartikeltypen. Generiert optional inaktive Anführungszeichen für generierte Bestellungen.

XML-Profilknoten:

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### Einfache Produkte

Erzeugt einfache Produkte. Produkte werden standardmäßig und nach vordefinierten Attributsätzen verteilt. Wenn im Profil zusätzliche Attributsätze wie `<product_attribute_sets>{int}</product_attribute_sets>` angegeben sind, werden die Produkte auch pro zusätzlichen Attributsätzen verteilt.

Die Produkte werden einheitlich nach Kategorien und Websites verteilt. Wenn `assign_entities_to_all_websites` auf `1` gesetzt ist, werden die Produkte allen Websites zugewiesen.

XML-Profilknoten:

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### Websites

Erzeugt Websites. XML-Profilknoten:

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### Speichergruppen

Erstellt Speichergruppen (in der Administratorgruppe als &quot;_&quot;_). Speichergruppen werden normalerweise auf Websites verteilt.

XML-Profilknoten:

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### Ansichten speichern

Erzeugt Ansichten des Stores. Store-Ansichten werden normalerweise unter Store-Gruppen verteilt. XML-Profilknoten:

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### Steuersätze

Erstellt Steuersätze. XML-Profilknoten:

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## Zusätzliche Konfigurationsinformationen:

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` - Standard-Attributsätze

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` - Kundenkonfiguration

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` - Konfiguration der vollständigen Produktbeschreibung

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` - Konfiguration der Produktkurzbeschreibung

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` - Konfiguration für kurze und vollständige Produktbeschreibungen. Diese ältere Implementierung dient der Abwärtskompatibilität.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` - Kleine Anzahl von Suchbegriffen, die kurz und vollständig beschrieben werden sollen

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` - Größere Anzahl von Suchbegriffen, die in einer kurzen und vollständigen Beschreibung verwendet werden sollen.
