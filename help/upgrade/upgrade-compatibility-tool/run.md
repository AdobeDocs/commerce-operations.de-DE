---
title: Führen Sie die [!DNL Upgrade Compatibility Tool]
description: Führen Sie die folgenden Schritte aus, um [!DNL Upgrade Compatibility Tool] in Ihrem Adobe Commerce-Projekt.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 0%

---


# Führen Sie die [!DNL Upgrade Compatibility Tool]

Die [!DNL Upgrade Compatibility Tool] ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

Die [!DNL Upgrade Compatibility Tool] identifiziert potenzielle Probleme, die in Ihrem Code behoben werden müssen, bevor versucht wird, ein Upgrade auf eine neuere Version von Adobe Commerce durchzuführen.

## Verwenden Sie die `upgrade:check` command

Die `upgrade:check` -Befehl ist der Hauptbefehl zum Ausführen des Tools:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>Die `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Die `upgrade:check` -Befehl führt die [!DNL Upgrade Compatibility Tool] und überprüft eine benutzerdefinierte Adobe Commerce-Instanz auf eine bestimmte Version, indem alle darin installierten Module analysiert werden. Es wird eine Liste mit kritischen Problemen, Fehlern und Warnungen zurückgegeben, die behoben werden müssen, bevor ein Upgrade auf die neueste Version Ihres Adobe Commerce durchgeführt werden kann.

>[!WARNING]
>
>Führen Sie die Ausführung nur aus, wenn der Ordner des Projektstamms (oder des Hauptordners) angegeben ist.

Mit diesem Befehl werden Änderungen am Kerncode für diese bestimmte Adobe Commerce-Instanz sowie alle darin installierten Änderungen an benutzerdefiniertem Code überprüft.

Sie können die `core:code:changes` -Befehl, um nur Änderungen am Kerncode für diese bestimmte Adobe Commerce-Instanz zu analysieren. Siehe [Core-Code-Änderungen](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) Abschnitt.

Während Sie die `graphql:compare` verwenden, um zwei GraphQL-Schemas zu vergleichen, um nach etwaigen Änderungen zwischen ihnen zu suchen. Siehe [Überprüfung der Kompatibilität mit GraphQL-Schemas](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) Abschnitt.

### Recommendations zur Verwendung der `upgrade:check` command

- Die [!DNL Upgrade Compatibility Tool] erfordert mindestens 2 GB RAM für die Ausführung. Diese Einstellung wird empfohlen, um Probleme aufgrund einer geringen Speicherbegrenzung zu vermeiden. Die [!DNL Upgrade Compatibility Tool] zeigt eine Frage an, wenn Sie die `upgrade:check` -Befehl mit einer niedrigen `memory_limit` -Einstellung.
- Geben Sie die `-m` -Option, um das Tool für ein bestimmtes Modul auszuführen:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=MODULE-PATH]`: Spezifisches Modulpfadverzeichnis.

### Verwenden Sie die `--help` option

So zeigen Sie die [!DNL Upgrade Compatibility Tool] allgemeine Optionen und Hilfe, ausführen:

```bash
bin/uct --help
```

Es ist jedoch möglich, `--help` als Option beim Ausführen eines bestimmten Befehls, z. B. `bin/uct upgrade:check`. Gibt spezifische `--help` Optionen für diesen Befehl:

```bash
bin/uct upgrade:check --help
```

Verfügbar `--help` Optionen für `upgrade:check` command:

- `-m, --module-path[=MODULE-PATH]`: Pfad der zu analysierenden Module
- `-a, --current-version[=CURRENT-VERSION]`: Aktuelle Adobe Commerce-Version, Version der Adobe Commerce-Installation wird verwendet, wenn sie weggelassen wird.
- `-c, --coming-version[=COMING-VERSION]`: Target Adobe Commerce-Version, Version der Adobe Commerce-Installation wird verwendet, wenn sie weggelassen wird.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Pfad der Datei, in die die Ausgabe im JSON-Format exportiert wird.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Pfad der Datei, in die die Ausgabe im HTML-Format exportiert wird.
- `--min-issue-level`: Minimale Problemstufe, die im Bericht angezeigt wird. Der Standardwert ist [WARNUNG].
- `--ignore-current-version-compatibility-issues`: Verwenden Sie diese Option, wenn Sie bekannte kritische Probleme, Fehler und Warnungen nicht in Ihre [!DNL Upgrade Compatibility Tool] Bericht.
- `--context=CONTEXT`: Ausführungskontext. Diese Option dient Integrationszwecken und hat keine Auswirkungen auf das Ausführungsergebnis.
- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: Anwendungsversion anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

### Ausgabe

Die Analyse hat ergeben, dass die [!DNL Upgrade Compatibility Tool] exportiert einen Bericht mit einer Liste von Problemen für jede Datei, in dem der Schweregrad, der Fehlercode und die Fehlerbeschreibung angegeben sind.

Siehe folgendes Beispiel:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Überprüfen Sie die [Fehlermeldungsreferenz](error-messages.md) für weitere Informationen.

Der Bericht enthält auch eine detaillierte Zusammenfassung, die Folgendes zeigt:

- *Aktuelle Version*: die derzeit installierte Version.
- *Zielversion*: die Version, auf die Sie aktualisieren möchten.
- *Ausführungszeit*: die Zeit, die die Analyse für die Erstellung des Berichts benötigte (mm:ss).
- *Module, die aktualisiert werden müssen*: der Prozentsatz der Module, die Kompatibilitätsprobleme enthalten und aktualisiert werden müssen.
- *Dateien, die aktualisiert werden müssen*: den Prozentsatz der Dateien, die Kompatibilitätsprobleme enthalten und aktualisiert werden müssen.
- *Kritische Fehler insgesamt*: die Anzahl der gefundenen kritischen Fehler.
- *Fehler insgesamt*: die Anzahl der gefundenen Fehler.
- *Warnhinweise insgesamt*: die Anzahl der gefundenen Warnungen.

Siehe folgendes Beispiel:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Standardmäßig wird die [!DNL Upgrade Compatibility Tool] exportiert den Bericht in zwei verschiedene Formate: `json` und `html`.

#### JSON

Die JSON-Datei enthält genau die gleichen Informationen, die in der Ausgabe angezeigt werden:

- Liste der identifizierten Probleme.
- Zusammenfassung der Analyse.

Für jedes aufgetretene Problem enthält der Bericht detaillierte Informationen wie den Schweregrad und die Beschreibung des Problems.

>[!NOTE]
>
>Der Standardpfad für den Ausgabeordner ist `var/output/[TIME]-results.json`.

Um diesen Bericht in einen anderen Ausgabeordner zu exportieren, führen Sie Folgendes aus:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Pfad-Verzeichnis zum Exportieren `.json` Ausgabedatei.

>[!NOTE]
>
>Der Standardpfad für den Ausgabeordner ist `var/output/[TIME]-results.json`.

#### HTML

Die HTML-Datei enthält auch die Liste der identifizierten Probleme und die Analysezusammenfassung. Er umfasst außerdem vier verschiedene Diagramme:

- **Schweregrad von Modulen nach Problem**: Zeigt die Schweregrad-Verteilung nach Modulen an.
- **Schweregrad der Dateien nach Problem**: Zeigt die Schweregrad-Verteilung nach Dateien an.
- **Nach Gesamtanzahl der Probleme sortierte Module**: Zeigt die 10 am stärksten kompromittierten Module unter Berücksichtigung von Warnungen, Fehlern und kritischen Fehlern an.
- **Module mit relativen Größen und Problemen**: Je mehr Dateien ein Modul enthält, desto größer ist sein Kreis. Je mehr Probleme ein Modul hat, desto roter erscheint sein Kreis.

Diese Diagramme ermöglichen es Ihnen, (auf einen Blick) die am stärksten betroffenen Teile und diejenigen zu identifizieren, die mehr Arbeit für eine Aktualisierung benötigen.

![HTML-Bericht - Zusammenfassung](../../assets/upgrade-guide/uct-html-summary.png)

![HTML-Bericht - Details](../../assets/upgrade-guide/uct-html-details.png)

So exportieren Sie diesen Bericht in einen anderen Ausgabeordner:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: {{site.data.var.ee}} Installationsordner.
- `[=HTML-OUTPUT-PATH]`: Pfad-Verzeichnis zum Exportieren `.html` Ausgabedatei.

>[!NOTE]
>
>Der Standardpfad für den Ausgabeordner ist `var/output/[TIME]-results.html`.

### Verwenden Sie die `--ignore-current-version-compatibility-issues` option

Die [!DNL Upgrade Compatibility Tool] ermöglicht Ihnen, die `upgrade:check` -Befehl mit einer `--ignore-current-version-compatibility-issues` angezeigt, sodass nur neue oder unbekannte kritische Probleme, Fehler und Warnungen angezeigt werden. Verwenden Sie diese Option, wenn Sie bekannte kritische Probleme, Fehler und Warnungen nicht in Ihre [!DNL Upgrade Compatibility Tool] Bericht.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Dies gilt nur für PHP-API-Überprüfungen.

### Vanilla-Installation

A _Vanille_ Bei der Installation handelt es sich um eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

Die `bin/uct core:code:changes` -Befehl prüft, ob sich in Ihrem System eine Vanilla-Instanz befindet. Wenn Sie zum ersten Mal eine Vanilla-Installation verwenden, werden Sie durch eine interaktive Befehlszeilenfrage aufgefordert, das Vanilla-Projekt von der [Adobe Commerce-Repository](https://repo.magento.com/).

Sie können eine [!DNL Upgrade Compatibility Tool] mit dem Befehl `--vanilla-dir` -Option, um den Installationsordner für Adobe Commerce Vanilla anzugeben.

Siehe [Vanilla-Instanz bereitstellen](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) für weitere Informationen.

## Verwenden Sie die `list` command

So geben Sie eine Liste der [!DNL Upgrade Compatibility Tool] verfügbare Befehle, ausführen:

```bash
bin/uct list
```

Die `list` gibt Folgendes zurück:

- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: App-Version anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

## Verwenden Sie die `core:code:changes` command

Sie können Ihre aktuelle Adobe Commerce-Installation mit einer sauberen Vanilla-Installation vergleichen, um festzustellen, ob im Kerncode Änderungen zur Implementierung einer neuen Funktion oder Anpassung vorgenommen wurden. Diese Validierung hilft bei der Schätzung des Aufwands, den das Upgrade basierend auf diesen Änderungen erfordert.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `<vanilla dir>`: Adobe Commerce-Vanilla-Installationsordner.

Beim Ausführen dieses Befehls gibt es einige Einschränkungen:

- Führen Sie die Ausführung nur aus, wenn der Ordner des Projektstamms (oder des Hauptordners) angegeben ist.
- Zeigt nur eine Liste der wichtigsten Änderungen an.

### Verwenden Sie die `core:code:changes` mit dem Befehl `--help` option

Verfügbar `--help` Optionen für `core:code:changes` command:

- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: App-Version anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

## Version

Sie können Ihre aktuelle Adobe Commerce-Installation mit Adobe Commerce-Versionen vergleichen `>=2.3`.

Sie müssen die Version als Parameter angeben, wenn Sie den Befehl ausführen:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Dabei gilt:

- `-c, --coming-version[=COMING-VERSION]`: Die Adobe Commerce-Zielversion.

Beim Ausführen des vorherigen Befehls gibt es einige Einschränkungen:

- Dieser Parameter bezieht sich auf alle Tags, die eine bestimmte Version von Adobe Commerce identifizieren.
- Es ist eine Pflicht, dies explizit anzugeben. Die Bereitstellung nur des Werts funktioniert nicht.
- Geben Sie die Tag-Version ohne Anführungszeichen an (weder Einzel- noch Doppelpunkt): ~~&quot;2.4.1-develop&quot;~~.
- Sie sollten KEINE älteren Versionen als die derzeit installierten bereitstellen und auch nicht ältere als 2.3, die derzeit die älteste Version ist, die unterstützt wird.

## Überprüfung der Kompatibilität mit GraphQL-Schemas

Die [!DNL Upgrade Compatibility Tool] bietet außerdem die Möglichkeit, zwei GraphQL-Endpunkte zu überprüfen und ihre Schemas zu vergleichen, um nach riskanten und gefährlichen Änderungen zwischen ihnen zu suchen:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Wenn die Argumente wie folgt lauten:

- `<schema1>`: Endpunkt-URL für die vorhandene Installation.
- `<schema2>`: Endpunkt-URL für die Vanilla-Installation.

Sie müssen `instance before` und `instance after` das Upgrade.

### GraphQL-Vergleich, Befehl `--help` options

Verfügbar `--help` Optionen für `graphql:compare` command:

- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: App-Version anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

### Beispiel mit einer Liste kritischer Probleme, Fehler und Warnungen für GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

Siehe [Entwicklerinformationen](../upgrade-compatibility-tool/developer.md) für weitere Informationen.

Sie können die [!DNL Upgrade Compatibility Tool] mit einer Ausführungskonfiguration über das PhpStorm-Plug-in. Siehe [[!DNL Upgrade Compatibility Tool] Konfiguration ausführen](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) für weitere Informationen.

## Fehlerbehebung

### Leere Ausgabe

>[!NOTE]
>
>Die `M2_VERSION` ist die Adobe Commerce-Zielversion, die Sie mit Ihrer Adobe Commerce-Instanz vergleichen möchten.

Wenn dieser Befehl nach der Ausführung ausgeführt wurde:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

Die einzige Ausgabe ist `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

Die wahrscheinliche Ursache ist eine PHP-Speicherbegrenzung.
Überschreiben Sie die Speicherbegrenzung durch Festlegen von `memory_limit` nach `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
