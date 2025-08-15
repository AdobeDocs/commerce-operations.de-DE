---
title: Übersetzungswörterbücher und Sprachpakete
description: Erfahren Sie, wie Sie Übersetzungswörterbücher erstellen und Sprachpakete erstellen.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# Lokalisierung

{{file-system-owner}}

Mit Commerce Translations können Sie Ihren Store für mehrere Regionen und Märkte anpassen und lokalisieren, indem Sie Folgendes generieren:

- **Übersetzungswörterbücher** die eine praktische Möglichkeit darstellen, _einige) Wörter und Ausdrücke_ übersetzen, z. B. für ein benutzerdefiniertes Modul oder Design.
- **Sprachpakete** mit denen Sie (_oder alle) Wörter und_ in der Commerce-Anwendung übersetzen können.

Siehe [Übersetzungen - Übersicht].

## Erstellen eines Übersetzungswörterbuchs

Sie können ein [Übersetzungswörterbuch] erstellen, um vorhandene Zeichenfolgen anzupassen, Wörter und Phrasen in einem benutzerdefinierten Modul zu übersetzen, ein Design zu lokalisieren oder Sprachpakete zu erstellen.

Um mit der Übersetzung zu beginnen, verwenden Sie den Befehl , um eine CSV-Wörterbuchdatei mit einer Liste aller vorhandenen Sätze und Wörter zu erstellen.

So erstellen Sie das Wörterbuch und beginnen mit der Übersetzung:

1. Extrahieren Sie übersetzbare Wörter und Ausdrücke aus aktivierten Komponenten mithilfe des Befehls für die Übersetzungserfassung. Der Inhalt wird in eine CSV-Datei extrahiert.
1. Übersetzen Sie die vorhandenen Wörter und Ausdrücke. Sie können bei Bedarf weitere benutzerdefinierte Begriffe hinzufügen.

   Es stehen Optionen zur Verwendung des übersetzten Wörterbuchs zur Verfügung:

1. Sie können die Übersetzungswörterbücher in ein Sprachpaket packen und dieses dem Commerce Store-Administrator bereitstellen.

1. In der Admin Store-Verwaltung [konfiguriert die Übersetzungen].

Befehlsoptionen:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

In der folgenden Tabelle werden Parameter und Werte erläutert:

| Parameter | Wert | Erforderlich? |
|--- |--- |--- |
| `<path to directory to translate>` | Pfad zu einem Verzeichnis mit übersetzbarem Code, d. h. PHP-, PHTML- oder XML-Dateien mit zu übersetzenden Ausdrücken.<br><br>Das Tool beginnt mit der Suche unter dem eingegebenen Pfad und durchsucht alle darin enthaltenen Dateien und Unterverzeichnisse.<br><br>Verwenden Sie diesen Parameter nicht, wenn Sie `-m --magento` verwenden. | Ja (Wörterbücher), nein (Pakete). |
| `-m --magento` | Wird benötigt, um ein Sprachpaket aus diesem Übersetzungswörterbuch zu erstellen. Durchsucht ggf. die Ordner, die bin/magento enthalten. Mit dieser Option werden jeder Zeile im Wörterbuch Designs oder Module hinzugefügt.<br><br>Es folgt ein Beispiel:<br><br>„Keine Elemente gefunden“,„Keine Elemente gefunden“,module,Magento_wishlist | Nein |
| `-o --output="<path>"` | Gibt den absoluten Dateisystempfad und Dateinamen der zu erstellenden CSV-Datei des Übersetzungswörterbuchs an. Bei dem eingegebenen Wert wird zwischen Groß- und Kleinschreibung unterschieden. Der Name der CSV-Datei muss genau mit dem Gebietsschema-Namen übereinstimmen, einschließlich der Groß-/Kleinschreibung der Zeichen.<br><br>Wenn Sie diesen Parameter weglassen, wird die Ausgabe an stdout weitergeleitet. | Nein |

>[!INFO]
>
>Um ein Sprachpaket aus einem Übersetzungswörterbuch zu erstellen, _müssen_ Sie die Option `-m|--magento` verwenden.

### Übersetzungsrichtlinien

Befolgen Sie bei der Übersetzung von Wörtern und Formulierungen die folgenden Richtlinien:

- Ändern Sie nur den Inhalt der zweiten Spalte. Übersetzen Sie die Sätze aus dem Englischen (`US`) in die gewünschte Sprache.
- Verwenden Sie beim Erstellen von Wörterbüchern für Gebietsschemata die standardmäßigen Commerce-Zeichenfolgen.
- Achten Sie beim Übersetzen auf Platzhalter: `%1`, `%2`

Commerce verwendet die Platzhalter zum Einfügen von Kontextwerten. Sie werden _nicht_ für Übersetzungen verwendet. Beispiel:

```text
Product '%1' has been added to shopping cart.
```

Befüllt mit einem Wert:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

Die resultierende Phrase muss mindestens einen von jedem Platzhalter enthalten. Angenommen, im ursprünglichen Satz gibt es Platzhalter von `%1` bis `%3`. Die Übersetzung kann beliebig viele dieser Platzhalter in beliebiger Reihenfolge enthalten. Es muss jedoch mindestens ein Vorkommen von `%1`, `%2` und `%3` vorhanden sein. Die Übersetzung darf keine Platzhalterwerte enthalten, die im ursprünglichen Wert nicht vorhanden sind (z. B. `%4`, `%5` usw.).

Beispiel für die Übersetzung eines Satzes:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Erstellen eines Sprachpakets

Im Gegensatz zu einem Übersetzungswörterbuch können Sie jedes oder alle Wörter und Sätze in der Commerce-Anwendung mithilfe eines Sprachpakets übersetzen. Sie können eine bestimmte Komponente - z. B. ein Modul oder ein Design - mithilfe eines Übersetzungswörterbuchs übersetzen. [Weitere Informationen zu Sprachpaketen].

In diesem Abschnitt wird beschrieben, wie Sie ein Sprachpaket erstellen, das CSV-Dateien in Module und Designs schreibt. Um ein Sprachpaket zu erstellen, müssen Sie die in den folgenden Abschnitten beschriebenen Aufgaben ausführen:

1. [Sammeln und Übersetzen von Wörtern und Wortgruppen](#generate-a-translation-dictionary). (Der `--magento` ist erforderlich.)
1. [Führen Sie den Sprachpaketbefehl ](#run-the-language-package-command).
1. [Erstellen von Verzeichnissen und Dateien](#create-directories-and-files).
1. (Optional) [Konfigurieren mehrerer Pakete für eine Sprache](#configure-multiple-packages-for-a-language).

### Führen Sie den Sprachpaketbefehl aus

Befehlsverwendung:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

In der folgenden Tabelle werden die Parameter und Werte für den Sprachpaketbefehl erläutert:

| Parameter | Wert | Erforderlich? |
|--- |--- |--- |
| `<source>` | Absoluter Dateisystempfad und Dateiname einer CSV-Datei, die das kombinierte Wörterbuch und die Metadaten enthält, die für die Aufschlüsselung in ein Sprachpaket erforderlich sind.<br><br>Verwenden Sie [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict), um die CSV-Datei zu erstellen, und erstellen Sie dann das Sprachpaket, wie in [Erstellen von Verzeichnissen und Dateien](#m2devgde-xlate-files) beschrieben. | Ja |
| `<locale>` | [ISO 639-1] (Sprache) und [ISO 3166] (Land) Kennung der Sprache, die als Dateiname für alle resultierenden CSV-Dateien verwendet wird. Beispiele: `de_DE`, `pt_PT`, `pt_BR`. | Ja |
| `-m --mode` | Gibt an, ob bei Vorhandensein einer Zieldatei das vorhandene Sprachpaket ersetzt oder mit dem neuen Sprachpaket zusammengeführt werden soll. Beim Zusammenführen werden alle vorhandenen Sätze überschrieben und neue hinzugefügt.<br><br>Werte: zusammenführen oder ersetzen (Standard). | Nein |
| `-d --allow-duplicates` | Schließen Sie diese Option ein, um Duplikate im Sprachpaket zuzulassen. Andernfalls schlägt der Befehl mit einem Fehler fehl, wenn dieselbe Phrase in mehreren Einträgen mit unterschiedlichen Übersetzungen auftritt. | Nein |

### Erstellen von Verzeichnissen und Dateien

Sprachpakete befinden sich in einem Verzeichnis unter `app/i18n/<VendorName>` im Commerce-Dateisystem mit folgendem Inhalt:

- Erforderliche Lizenzdateien
- `composer.json`
- `registration.php`, [ das ] registriert
- [`language.xml`](#language-package-languagexml)-Metadatendatei

>[!INFO]
>
>Sie müssen den gesamten Pfad in Kleinbuchstaben eingeben. Siehe zum Beispiel [`de_de`].

So erstellen Sie diese Dateien:

1. Erstellen Sie ein Verzeichnis unter `app/i18n`.

   Beispielsweise befinden sich Commerce-Sprachpakete in `app/i18n/magento`

1. Erforderliche Lizenzdateien hinzufügen.
1. Fügen Sie [`composer.json`] hinzu, die Abhängigkeiten für Ihr Sprachpaket angeben.
1. Registrieren des Sprachpakets bei [`registration.php`]
1. Fügen Sie `language.xml` Metadatendatei hinzu, wie im nächsten Abschnitt beschrieben.

#### Sprachpaket language.xml

Beim Deklarieren eines Sprachpakets in der `language.xml`-Konfigurationsdatei müssen Sie die Reihenfolge der Sprachvererbung für dieses Paket angeben.

Mit der Sprachvererbung können Sie eine Übersetzung namens _untergeordnet“_ einer vorhandenen Übersetzung namens &quot;_&quot;_. Die untergeordneten Übersetzungen überschreiben das übergeordnete Element. Wenn die untergeordnete Übersetzung jedoch nicht hochgeladen oder angezeigt werden kann oder eine Wortgruppe oder ein Wort fehlt, verwendet Commerce das übergeordnete Gebietsschema. [Beispiele für die Sprachpaketvererbung](#example-of-language-inheritance).

Um ein Paket zu deklarieren, geben Sie die folgenden Informationen an:

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Dabei gilt:

- `code` - Sprachpaket-Gebietsschema (erforderlich)
- `vendor` - Herstellername des Moduls (erforderlich)
- `package` - Name des Sprachpakets (erforderlich)
- `sort_order` - Priorität beim Hochladen eines Pakets, wenn mehrere Sprachpakete für einen Store verfügbar sind
- `use` - Übergeordnetes Sprachpaket-Gebietsschema, von dem Wörterbücher übernommen werden sollen

Bei Bedarf können Sie mehrere übergeordnete Pakete angeben. Die übergeordneten Pakete werden auf der Basis der ersten aufgelisteten und verwendeten angewendet.

#### Beispiel für die Sprachvererbung

Angenommen, ein Sprachpaket erbt von zwei anderen Paketen und diese Pakete haben auch übergeordnete und „übergeordnete“ Pakete.

Wenn ein Sprachpaket von zwei Paketen erbt, kann sein `language.xml` wie folgt aussehen:

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

Im vorherigen Beispiel:

- `language_package_one` erbt von `en_au_package` und `en_au_package` erbt von `en_ie_package`
- `language_package_two` erbt von `en_ca_package` und `en_ca_package` erbt von `en_us_package`

Wenn die Commerce-Anwendung ein Wort oder eine Phrase im `en_GB` nicht finden kann, sucht sie in anderen Paketen in der folgenden Reihenfolge:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Die Angabe aller Vererbungen zwischen den Sprachpaketen kann zur Erstellung von zirkulären Vererbungsketten führen. Verwenden Sie [Magento\Test\Integrity\App\Language\CircularDependencyTest] Test, um solche Ketten zu finden und zu reparieren.

### Konfigurieren mehrerer Pakete für eine Sprache

Um Ihnen zu helfen, Ihren Store flexibler zu gestalten, können Sie mehrere Sprachpakete für dieselbe Sprache in Ihren Store hochladen. Daher können Sie verschiedene benutzerdefinierte Pakete für verschiedene Teile Ihres Stores verwenden, da das System ein einziges Paket aus allen Paketen kompiliert, die für eine Sprache verfügbar sind.

Um ein zusätzliches Paket für eine vorhandene Sprache zu aktivieren, benennen Sie das neue Paket mit einem beliebigen Namen außer einem vorhandenen Sprach-Code-Namen (um Verwirrung zu vermeiden). Geben Sie die Konfigurationen eines Pakets in der `language.xml`-Metadatendatei des Sprachpakets an, wie im nächsten Abschnitt erläutert.

## Beispiele für die Verwendung von Übersetzungsbefehlen

Die folgenden Abschnitte enthalten End-to-End-Beispiele für die Verwendung der in diesem Thema beschriebenen Befehle zum Erstellen von Übersetzungswörterbüchern und Übersetzungspaketen:

### Beispiel: Erstellen eines Übersetzungswörterbuchs für ein Modul oder Design

So fügen Sie eine deutsche Übersetzung zu einem Modul oder Thema hinzu, das Sie an andere Händler verteilen möchten:

1. Sammeln Sie Sätze aus Ihrem Modul:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Der CSV-Dateiname muss _genau mit dem_ übereinstimmen, einschließlich der Groß-/Kleinschreibung der Zeichen.

1. Übersetzen Sie die Wörter und Sätze mithilfe [dieser Richtlinien](#translation-guidelines).
1. Kopieren Sie bei Bedarf `xx_YY.csv` in `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` oder in das Design-Verzeichnis des Moduls (je nachdem, ob das Übersetzungs-Wörterbuch für ein Modul oder ein Design ist).

### Beispiel: Sprachpaket erstellen

Generieren Sie ähnlich wie im vorherigen Beispiel eine CSV-Datei, geben Sie jedoch anstelle eines Modul- oder Designverzeichnisses den gesamten Stammordner der Commerce-Anwendung an. Die resultierende CSV-Datei enthält alle Phrasen, die der Befehl im Code finden konnte.

1. Sammeln Sie Sätze aus Ihrem Modul:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Der CSV-Dateiname muss _genau mit dem_ übereinstimmen, einschließlich der Groß-/Kleinschreibung der Zeichen.

1. Übersetzen Sie die Wörter und Sätze mithilfe [dieser Richtlinien](#translation-guidelines).
1. Erstellen Sie das Sprachpaket.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Erstellen Sie ein Verzeichnis für das Sprachpaket.

   Beispiel: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Fügen Sie in diesem Verzeichnis Folgendes hinzu:

   - Eine Lizenz, falls erforderlich
   - `composer.json` (Beispiel unten)
   - `registration.php` (Beispiel unten)
   - `language.xml` (Beispiel unten)

   **`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **`registration.php`**:

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Übersetzungen - Übersicht]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[Übersetzungswörterbuch]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[Konfigurieren der Übersetzungen]: https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/store-localize
[Weitere Informationen zu Sprachpaketen]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[Register]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`composer.json`]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[`registration.php`]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
