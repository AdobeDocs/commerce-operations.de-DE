---
title: Generieren von Daten für Leistungstests
description: Erfahren Sie, wie Sie eine große Datenmenge für Leistungstests generieren.
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: d4a6d5cd181c7c4426914bbe481f4d5d1e828b5e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 9%

---

# Leistungstestdaten

## Profile

Sie können die Menge der von Ihnen erstellten Daten anpassen, indem Sie _profiles_ (klein, mittel, groß und extra groß). Die Profile befinden sich im `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>` Verzeichnis.

Beispiel: `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

Die folgende Abbildung zeigt, wie ein Produkt in der Storefront mit der _klein_ profile:

![Beispiel-Storefront mit generierten Daten](../../assets/configuration/generate-data.png)

Die folgende Tabelle enthält Details zu den Profilen des Datengenerators: klein, mittel, groß und extra groß.

| Parameter | Wenig Profil | Mittleres Profil | Mittleres Profil für mehrere Sites | Großes Profil | Großes Profil |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24.000 | 4.000 | 300.000 | 600.000 |
| `configurable_products` | 16 mit 24 Optionen | 640 mit 24 Optionen | 800 mit 24 Optionen &amp; 79 mit 200 Optionen | 8.000 mit 24 Optionen | 16.000 mit 24 Optionen |
| `product_images` | 100 Bilder/3 Bilder pro Produkt | 1000 Bilder/3 Bilder pro Produkt | 1000 Bilder/3 Bilder pro Produkt | 2000 Bilder/3 Bilder pro Produkt | 2000 Bilder/3 Bilder pro Produkt |
| `categories` | 30 | 300 | 100 | 3.000 | 6.000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2.000 | 2.000 | 5.000 | 10.000 |
| `tax rates` | 130 | 40.000 | 40.000 | 40.000 | 40.000 |
| `orders` | 80 | 50.000 | 50.000 | 100.000 | 150.000 |

### Datengenerator ausführen

{{file-system-owner}}

>[!WARNING]
>
>Deaktivieren Sie vor dem Ausführen des Datengenerators alle auf dem Server ausgeführten Cron-Aufträge. Das Deaktivieren von Cron-Aufträgen verhindert, dass der Datengenerator Aktionen ausführt, die mit aktiven Cron-Aufträgen in Konflikt stehen, und vermeidet unnötige Fehler.
>
>Wenn Sie Eventing mit implementieren möchten [!DNL Adobe I/O Events for Adobe Commerce] Führen Sie während des Testens der Leistung diesen Befehl aus, bevor Sie sich anmelden [events](https://developer.adobe.com/commerce/extensibility/events/). Das Abonnieren von Ereignissen zuerst kann zu Fehlern führen.

Führen Sie den Befehl wie in diesem Abschnitt beschrieben aus. Nachdem der Befehl ausgeführt wurde, müssen Sie [Neuindizieren aller Indexer](../cli/manage-indexers.md).

Befehlsoptionen:

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

Wo `<path-to-profile>` gibt den absoluten Dateisystempfad und Namen eines Profils an.

Beispiel:

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

Beispielausgabe für ein kleines Profil:

```terminal
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

## Leistungsverbesserungen

### Admin Users

Erstellt Admin-Benutzer. XML-Profilknoten:

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### Attributsätze

Generiert Attributsätze mit der angegebenen Konfiguration. XML-Profilknoten:

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### Paketprodukte

Generiert Bundle-Produkte. Generierte Bundle-Auswahlen werden nicht einzeln im Katalog angezeigt. Produkte werden einheitlich nach Kategorien und Websites verteilt. Wenn  `assign_entities_to_all_websites` aus dem Profil auf `1`. Produkte werden allen Websites zugewiesen.

XML-Profilknoten:

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### Preisregeln für Warenkorb

Erstellt Regeln zum Warenkorbpreis. XML-Profilknoten:

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### Katalogpreisregeln

Erstellt Regeln zu Katalogpreisen. XML-Profilknoten:

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### Kategorien

Erzeugt Kategorien. Wenn `assign_entities_to_all_websites` auf `0`festgelegt ist, werden alle Kategorien gleichmäßig pro Stammkategorien verteilt. Andernfalls werden alle Kategorien einer Stammkategorie zugeordnet.

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

Erzeugt konfigurierbare Produkte. Generierte konfigurierbare Optionen werden nicht einzeln im Katalog angezeigt. Produkte werden einheitlich nach Kategorien und Websites verteilt. Wenn `assign_entities_to_all_websites` auf `1`, werden Produkte allen Websites zugewiesen.

Die folgenden XML-Knotenformate werden unterstützt:

- Verteilung nach Standard- und vordefinierten Attributsätzen:

  ```xml
  <!-- Number of configurable products -->
  <configurable_products>{int}</configurable_products>
  ```

- Generieren Sie Produkte basierend auf einem vorhandenen Attributsatz:

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

- Generieren Sie Produkte basierend auf einem dynamisch erstellten Attributsatz mit einer bestimmten Anzahl von Attributen und Optionen:

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

- Generieren Sie Produkte basierend auf einem dynamisch erstellten Attribut, das mit einer bestimmten Konfiguration für jedes Attribut festgelegt wurde:

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

Erzeugt Kunden. Kunden verfügen über eine normale Verteilung auf alle verfügbaren Websites. Jeder Kunde verfügt über die gleichen Daten, außer Kunden-E-Mail, Kundengruppe und Kundenadressen.

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

Generiert Produktbilder. Die Generierung umfasst keine Größenanpassung.

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

Erstellt Bestellungen mit einer konfigurierbaren Anzahl von verschiedenen Arten von Bestellelementen. Generiert optional inaktive Anführungszeichen für generierte Bestellungen.

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

Generiert einfache Produkte. Produkte werden nach standardmäßigen und vordefinierten Attributsätzen verteilt. Wenn im Profil zusätzliche Attributsätze wie folgt angegeben werden: `<product_attribute_sets>{int}</product_attribute_sets>`, werden Produkte auch pro zusätzlichen Attributsätzen verteilt.

Produkte werden einheitlich nach Kategorien und Websites verteilt. Wenn `assign_entities_to_all_websites` auf `1`, werden Produkte allen Websites zugewiesen.

XML-Profilknoten:

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### Websites

Erstellt Websites. XML-Profilknoten:

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### Store-Gruppen

Generiert Store-Gruppen (in Admin als _Stores_). Store-Gruppen werden normal auf Websites verteilt.

XML-Profilknoten:

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### Store-Ansichten

Generiert Store-Ansichten. Store-Ansichten werden normal zwischen Store-Gruppen verteilt. XML-Profilknoten:

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### Steuersätze

Erzeugt Steuersätze. XML-Profilknoten:

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## Zusätzliche Konfigurationsinformationen:

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml`—Standardmäßige Attributsätze

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml`—Kundenkonfiguration

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml`—Konfiguration der vollständigen Produktbeschreibung

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml`—Konfiguration der kurzen Produktbeschreibung

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml`—Konfiguration für kurze und vollständige Beschreibung des Produkts. Diese ältere Implementierung wird aus Gründen der Abwärtskompatibilität bereitgestellt.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml`—Kleine Anzahl von Suchbegriffen in kurze und vollständige Beschreibungen

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml`—Größere Anzahl von Suchbegriffen, die kurz und vollständig verwendet werden sollen.
