---
title: Übersetzungswörterbücher und Sprachpakete
description: Erfahren Sie, wie Sie Übersetzungswörterbücher erstellen und Sprachpakete erstellen.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# Lokalisierung

{{file-system-owner}}

Mit Commerce-Übersetzungen können Sie Ihren Store für mehrere Regionen und Märkte anpassen und lokalisieren, indem Sie Folgendes generieren:

- **Übersetzungswörterbücher**, die eine praktische Methode zur Anpassung oder Übersetzung darstellen _some_ Wörter und Ausdrücke, z. B. für ein benutzerdefiniertes Modul oder Design.
- **Sprachpakete** , mit denen Sie übersetzen können _alle_ Wörter und Ausdrücke in der Commerce-Anwendung.

Siehe [Übersetzungen - Übersicht].

## Übersetzungswörterbuch erstellen

Sie können eine [Übersetzungswörterbuch] um vorhandene Zeichenfolgen anzupassen, Wörter und Ausdrücke in einem benutzerdefinierten Modul zu übersetzen, ein Design zu lokalisieren oder zu erstellen [Sprachpakete](https://glossary.magento.com/language-package).

Um mit der Übersetzung zu beginnen, verwenden Sie einen Befehl, um eine Wörterbuch-CSV-Datei mit einer Liste aller vorhandenen Ausdrücke und Wörter zu generieren.

So generieren Sie das Wörterbuch und beginnen die Übersetzung:

1. Extrahieren Sie übersetzbare Wörter und Ausdrücke aus aktivierten Komponenten mithilfe des Befehls zur Übersetzungserfassung. Inhalte werden in eine CSV-Datei extrahiert.
1. Übersetzen Sie die vorhandenen Wörter und Ausdrücke. Sie können bei Bedarf weitere benutzerdefinierte Begriffe hinzufügen.

   Sie haben Optionen für die Verwendung des übersetzten Wörterbuchs:

1. Sie können die Übersetzungswörterbücher in ein Sprachpaket verpacken und das Paket dem Commerce Store-Administrator bereitstellen.

1. Der Store-Administrator im Admin [Konfiguration der Übersetzungen].

Befehlsoptionen:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

In der folgenden Tabelle werden Parameter und Werte erläutert:

| Parameter | Wert | Erforderlich? |
|--- |--- |--- |
| `<path to directory to translate>` | Pfad zu einem Verzeichnis mit übersetzbarem Code; d. h. PHP-, PHTML- oder XML-Dateien mit zu übersetzenden Ausdrücken.<br><br>Das Tool beginnt mit der Suche nach dem Pfad, den Sie eingeben, und durchsucht alle darin enthaltenen Dateien und Unterverzeichnisse.<br><br>Verwenden Sie diesen Parameter nicht, wenn Sie `-m --magento`. | Ja (Wörterbücher), nein (Pakete). |
| `-m --magento` | Erforderlich zum Erstellen eines Sprachpakets aus diesem Übersetzungswörterbuch. Durchsucht bei Verwendung die Verzeichnisse, die bin/magento enthalten. Mit dieser Option werden Designs oder Module zu jeder Zeile im Wörterbuch hinzugefügt.<br><br>Beispiel:<br><br>&quot;Keine Elemente gefunden&quot;, &quot;Keine Elemente gefunden&quot;, Modul, Magento_Wishlist | Nein |
| `-o --output="<path>"` | Gibt den absoluten Dateisystempfad und Dateinamen der zu erstellenden CSV-Datei des Übersetzungswörterbuchs an. Beim eingegebenen Wert wird zwischen Groß- und Kleinschreibung unterschieden. Der Name der CSV-Datei muss genau mit dem Gebietsschema-Namen übereinstimmen, einschließlich der Groß-/Kleinschreibung der Zeichen.<br><br>Wenn Sie diesen Parameter weglassen, wird die Ausgabe zum &quot;stdout&quot;weitergeleitet. | Nein |

>[!INFO]
>
>Um ein Sprachpaket aus einem Übersetzungswörterbuch zu erstellen, müssen Sie _must_ die `-m|--magento` -Option.

### Übersetzungsrichtlinien

Beachten Sie beim Übersetzen von Wörtern und Ausdrücken die folgenden Richtlinien:

- Ändern Sie nur den Inhalt der zweiten Spalte. Übersetzen Sie die Ausdrücke aus dem Englischen (`US`) in die gewünschte Sprache.
- Verwenden Sie beim Erstellen von Wörterbüchern für Gebietsschemata die standardmäßigen Commerce-Zeichenfolgen.
- Achten Sie beim Übersetzen auf Platzhalter: `%1`, `%2`

Commerce verwendet die Platzhalter zum Einfügen von Kontextwerten. , _not_ wird für Übersetzungen verwendet. Beispiel:

```text
Product '%1' has been added to shopping cart.
```

Füllt mit einem Wert:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

Der resultierende Satz muss mindestens einen von jedem Platzhalter enthalten. Angenommen, es gibt Platzhalter von `%1` nach `%3` im ursprünglichen Satz. Die Übersetzung kann beliebig viele dieser Platzhalter enthalten, es muss jedoch mindestens ein Vorkommen von `%1`, `%2`und `%3`. Die Übersetzung darf keine Platzhalterwerte enthalten, die nicht im ursprünglichen Wert vorhanden sind (z. B. `%4`, `%5`usw.).

Beispiel für die Übersetzung einer Wortgruppe:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Sprachpaket erstellen

Im Gegensatz zu einem Übersetzungswörterbuch können Sie beliebige oder alle Wörter und Ausdrücke in der Commerce-Anwendung mithilfe eines Sprachpakets übersetzen. Sie können eine bestimmte Komponente - wie ein Modul oder ein Design - mithilfe eines Übersetzungswörterbuchs übersetzen. [Weitere Informationen zu Sprachpaketen].

In diesem Abschnitt wird beschrieben, wie Sie ein Sprachpaket erstellen, das CSV-Dateien in Module und Designs schreibt. Um ein Sprachpaket zu erstellen, müssen Sie die in den folgenden Abschnitten beschriebenen Aufgaben ausführen:

1. [Wörter und Ausdrücke sammeln und übersetzen](#generate-a-translation-dictionary). (Die `--magento` -Parameter erforderlich ist.)
1. [Ausführen des Sprachpakets, Befehl](#run-the-language-package-command).
1. [Erstellen von Ordnern und Dateien](#create-directories-and-files).
1. (Optional.) [Mehrere Pakete für eine Sprache konfigurieren](#configure-multiple-packages-for-a-language).

### Ausführen des Sprachpakets, Befehl

Befehlsverwendung:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

In der folgenden Tabelle werden die Parameter und Werte für den Sprachpaket-Befehl erläutert:

| Parameter | Wert | Erforderlich? |
|--- |--- |--- |
| `<source>` | Absoluter Dateisystempfad und Dateiname einer CSV-Datei, die das kombinierte Übersetzungswörterbuch und die für die Aufschlüsselung in ein Sprachpaket erforderlichen Metainformationen enthält.<br><br>Verwendung [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) , um die CSV-Datei zu erstellen, und erstellen Sie dann das Sprachpaket, wie hier beschrieben: [Erstellen von Ordnern und Dateien](#m2devgde-xlate-files). | Ja |
| `<locale>` | [ISO 639-1] (Sprache) und [ISO 3166] (country) Die Kennung der Sprache, die als Dateiname für alle resultierenden CSV-Dateien verwendet wird. Beispiele: `de_DE`, `pt_PT`, `pt_BR`. | Ja |
| `-m --mode` | Wenn eine Zieldatei vorhanden ist, gibt an, ob das vorhandene Sprachpaket ersetzt oder mit dem neuen Sprachpaket zusammengeführt werden soll. Die Zusammenführung überschreibt alle vorhandenen Ausdrücke und fügt neue hinzu.<br><br>Werte: Zusammenführen oder Ersetzen (Standard). | Nein |
| `-d --allow-duplicates` | Fügen Sie diese Option hinzu, um Duplikate im Sprachpaket zuzulassen. Andernfalls schlägt der Befehl mit einem Fehler fehl, wenn in mehreren Einträgen mit unterschiedlichen Übersetzungen dieselbe Wortgruppe vorkommt. | Nein |

### Erstellen von Ordnern und Dateien

Sprachpakete befinden sich in einem Verzeichnis unter `app/i18n/<VendorName>` im Commerce-Dateisystem mit folgendem Inhalt:

- Erforderliche Lizenzdateien
- `composer.json`
- `registration.php` dass [Register] Sprachpaket
- [`language.xml`](#language-package-languagexml) Meta-Informationsdatei

>[!INFO]
>
>Sie müssen den gesamten Pfad in Kleinbuchstaben schreiben. Siehe beispielsweise [`de_de`].

So erstellen Sie diese Dateien:

1. Erstellen eines Ordners unter `app/i18n`.

   Beispielsweise befinden sich Commerce-Sprachpakete unter `app/i18n/magento`

1. Fügen Sie erforderliche Lizenzdateien hinzu.
1. Hinzufügen [`composer.json`] , der Abhängigkeiten für Ihr Sprachpaket angibt.
1. Registrieren Sie das Sprachpaket mit [`registration.php`]
1. Hinzufügen `language.xml` Metainformationsdatei, wie im nächsten Abschnitt beschrieben.

#### Sprachpaket language.xml

Beim Deklarieren eines Sprachpakets im `language.xml` Konfigurationsdatei, müssen Sie die Reihenfolge der Sprachvererbung für dieses Paket angeben.

Durch die Sprachvererbung können Sie eine Übersetzung erstellen, die als _child_ basierend auf einer vorhandenen Übersetzung, die als _parent_. Die untergeordneten Übersetzungen überschreiben die übergeordnete. Wenn die untergeordnete Übersetzung jedoch nicht hochgeladen oder angezeigt werden kann oder eine Wortgruppe oder ein Wort fehlt, verwendet Commerce die übergeordnete [locale](https://glossary.magento.com/locale). [Beispiele für die Vererbung von Sprachpaketen](#example-of-language-inheritance).

Geben Sie die folgenden Informationen an, um ein Package zu deklarieren:

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

- `code`—Gebietsschema des Sprachpakets (erforderlich)
- `vendor`—Name des Anbieters des Moduls (erforderlich)
- `package`—Name des Sprachpakets (erforderlich)
- `sort_order`—Priorität beim Hochladen eines Pakets, wenn mehrere Sprachpakete für einen Store verfügbar sind
- `use`—Übergeordnetes Sprachpaket-Gebietsschema, aus dem Wörterbücher geerbt werden sollen

Bei Bedarf können Sie mehrere übergeordnete Pakete angeben. Die übergeordneten Pakete werden auf der ersten aufgelisteten, zuerst verwendeten Basis angewendet.

#### Beispiel einer Sprachvererbung

Angenommen, ein Sprachpaket erbt von zwei anderen Paketen, und diese Pakete haben auch übergeordnete und &quot;übergeordnete&quot;Pakete.

Wenn ein Sprachpaket von zwei Paketen erbt, wird es `language.xml` könnte wie folgt aussehen:

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

Im obigen Beispiel:

- `language_package_one` von `en_au_package` und `en_au_package` von `en_ie_package`
- `language_package_two` von `en_ca_package` und `en_ca_package` von `en_us_package`

Wenn die Commerce-Anwendung das Wort oder die Wortgruppe nicht im `en_GB` -Paket, sieht es in anderen Paketen in der folgenden Sequenz aus:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Das Angeben aller Vererbungen zwischen den Sprachpaketen kann zur Erstellung zirkulärer Vererbungsketten führen. Verwendung [Magento\Test\Integrity\App\Language\CircularDependencyTest] testen, um solche Ketten zu finden und zu beheben.

### Mehrere Pakete für eine Sprache konfigurieren

Um Ihren Speicher flexibler zu gestalten, können Sie mehrere Sprachpakete für dieselbe Sprache in Ihren Speicher hochladen. So können Sie verschiedene benutzerdefinierte Pakete für verschiedene Teile Ihres Geschäfts verwenden, da das System ein einzelnes Paket aus allen Paketen zusammenstellt, die für eine Sprache verfügbar sind.

Um ein zusätzliches Paket für eine vorhandene Sprache zu aktivieren, geben Sie dem neuen Paket einen beliebigen Namen außer einem vorhandenen Sprachcode-Namen (um Verwirrung zu vermeiden). Festlegen von Konfigurationen eines Pakets im Sprachpaket `language.xml` Metainformationsdatei, wie im nächsten Abschnitt beschrieben.

## Beispiele für die Verwendung von Übersetzungsbefehlen

Die folgenden Abschnitte enthalten durchgängige Beispiele für die Verwendung der in diesem Thema beschriebenen Befehle zum Erstellen von Übersetzungswörterbüchern und Übersetzungspaketen:

### Beispiel: Erstellen eines Übersetzungswörterbuchs für ein Modul oder Design

So fügen Sie eine deutsche Übersetzung zu einem Modul oder Thema hinzu, das Sie an andere Händler verteilen möchten:

1. Sammeln Sie Ausdrücke aus Ihrem Modul:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Der CSV-Dateiname muss _exakte Übereinstimmung_ das Gebietsschema, einschließlich der Groß-/Kleinschreibung der Zeichen.

1. Übersetzen Sie die Wörter und Ausdrücke mithilfe von [diese Leitlinien](#translation-guidelines).
1. Falls erforderlich, kopieren Sie `xx_YY.csv` nach `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` oder in das Designverzeichnis des Moduls (je nachdem, ob das Übersetzungswörterbuch für ein Modul oder ein Design gilt).

### Beispiel: Sprachpaket erstellen

Generieren Sie wie im vorherigen Beispiel eine CSV-Datei, geben Sie jedoch anstatt eines Modul- oder Designverzeichnisses den gesamten Stammordner der Commerce-Anwendung an. Die resultierende CSV-Datei enthält alle Ausdrücke, die der Befehl im Code finden könnte.

1. Sammeln Sie Ausdrücke aus Ihrem Modul:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Der CSV-Dateiname muss _exakte Übereinstimmung_ das Gebietsschema, einschließlich der Groß-/Kleinschreibung der Zeichen.

1. Übersetzen Sie die Wörter und Ausdrücke mithilfe von [diese Leitlinien](#translation-guidelines).
1. Erstellen Sie das Sprachpaket.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Erstellen Sie ein Verzeichnis für das Sprachpaket.

   Beispiel: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Fügen Sie in diesem Verzeichnis die folgenden Elemente hinzu:

   - Eine Lizenz, falls erforderlich
   - `composer.json` (Beispiel:
   - `registration.php` (Beispiel:
   - `language.xml` (Beispiel:

   **Beispiel`composer.json`**:

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

   **Beispiel`registration.php`**:

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Beispiel`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Translate theme strings]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/translate_theory.html
[Übersetzungen - Übersicht]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html
[Community Engineering contributions]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#translations-project
[Übersetzungswörterbuch]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-dictionaries
[Konfiguration der Übersetzungen]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[Weitere Informationen zu Sprachpaketen]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-languagepack
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[Register]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[&quot;de_de&quot;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&quot;composer.json&quot;]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html
[&quot;registration.php&quot;]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
