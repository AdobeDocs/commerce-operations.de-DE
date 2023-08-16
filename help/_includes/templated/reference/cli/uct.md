---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 3.0.3

Diese Referenz enthält 9 Befehle, die über die `bin/uct` Befehlszeilen-Tool.
Die anfängliche Liste wird automatisch mit der Variablen `bin/uct list` -Befehl in Adobe Commerce.

Weitere Informationen zum Tool finden Sie unter [Übersicht](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Diese Referenz wird aus der Anwendungs-Codebase generiert. Um den Inhalt zu ändern, können Sie den Quellcode für die entsprechende Befehlsimplementierung im [codebase](https://github.com/magento) Repository erstellen und Ihre Änderungen zur Überprüfung einreichen. Eine andere Möglichkeit ist, _Feedback geben_ (finden Sie den Link oben rechts). Beitragsrichtlinien finden Sie unter [Codebeiträge](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Interner Befehl zum Bereitstellen von Vorschlägen zur Shell-Fertigstellung

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

Der Shell-Typ (&quot;bash&quot;)

- Erfordert einen Wert

### `--input`, `-i`

Ein Array von Eingabe-Token (z. B. COMP_WORDS oder argv)

- Standard: `[]`
- Erfordert einen Wert

### `--current`, `-c`

Der Index des &quot;input&quot;-Arrays, in dem sich der Cursor befindet (z. B. COMP_CWORD)

- Erfordert einen Wert

### `--symfony`, `-S`

Die Version des Fertigstellungsskripts

- Erfordert einen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `completion`

Dump des Shell-Fertigstellungsskripts

```bash
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

Der Shell-Typ (z. B. &quot;bash&quot;), der Wert der env var &quot;$SHELL&quot; wird verwendet, wenn dies nicht angegeben wird.


### `--debug`

Fertigstellungs-Debug-Protokoll verfolgen

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `help`

Hilfe für einen Befehl anzeigen

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Der Befehlsname

- Standard: `help`


### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

### `--raw`

Ausgabe der Rohbefehl-Hilfe

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `list`

Listen-Befehle

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

Der Namespace-Name


### `--raw`

So geben Sie die unformatierte Befehlsliste aus

- Standard: `false`
- Akzeptiert keinen Wert

### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

### `--short`

Überspringen der Beschreibung der Befehlsargumente

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `refactor`

Behebt Probleme, die automatisch behoben werden können. Der Code im angegebenen Pfad wird aktualisiert.

```bash
bin/uct refactor <path>
```


### `path`

Pfad zum Beheben von Problemen in.

- Erforderlich

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `core:code:changes`

Das Upgrade-Kompatibilitätstool ist ein Befehlszeilenwerkzeug, das eine Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Nicht-Adobe Commerce-Module analysiert werden. Gibt eine Liste mit Fehlern und Warnungen zurück, die Sie vor der Aktualisierung auf eine neue Version des Adobe Commerce-Codes beheben müssen.

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

Installationsordner von Adobe Commerce.

- Erforderlich

### `vanilla-dir`

Adobe Commerce-Vanilla-Installationsordner.


### `--output`, `-o`

Pfad der Datei, in die die Ausgabe exportiert wird (JSON-Format)

- Akzeptiert einen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dbschema:diff`

Zulassen der Auflistung von Adobe Commerce DB-Schemaunterschieden zwischen zwei ausgewählten Versionen.
Verfügbare Versionen: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.5-p2 | 2.4.6

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

aktuelle Version (z. B. 2.3.2).

- Erforderlich

### `target-version`

Zielversion (z. B. 2.4.5).

- Erforderlich

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `graphql:compare`

Überprüfung der Kompatibilität mit GraphQL-Schemas

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

Endpunkt-URL, die auf das erste GraphQL-Schema verweist.

- Erforderlich

### `schema2`

Endpunkt-URL, die auf das zweite GraphQL-Schema verweist.

- Erforderlich

### `--output`, `-o`

Pfad der Datei, in die die Ausgabe exportiert wird (JSON-Format)

- Akzeptiert einen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `upgrade:check`

Das Upgrade-Kompatibilitätstool ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Gibt eine Liste mit Fehlern und Warnungen zurück, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

Installationsordner von Adobe Commerce.

- Erforderlich

### `--current-version`, `-a`

Die aktuelle Adobe Commerce-Version und die Version der Adobe Commerce-Installation werden verwendet, wenn sie weggelassen werden.

- Akzeptiert einen Wert

### `--coming-version`, `-c`

Target Adobe Commerce-Version, wird die neueste veröffentlichte Version von Adobe Commerce verwendet, wenn sie weggelassen wird. Verfügbare Adobe Commerce-Versionen: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.5 \| 2.4-p2 \| 2.4.5-p1 \| 2.4.4-p3 \| 2.4.5-p2 \| 2.4.6

- Akzeptiert einen Wert

### `--json-output-path`

Pfad der Datei, in die die Ausgabe im JSON-Format exportiert wird

- Akzeptiert einen Wert

### `--html-output-path`

Pfad der Datei, in die die Ausgabe im HTML-Format exportiert wird

- Akzeptiert einen Wert

### `--min-issue-level`

Minimale Problemebene, die im Bericht angezeigt werden soll (Warnung, Fehler oder kritisch).

- Standard: `warning`
- Akzeptiert einen Wert

### `--ignore-current-version-compatibility-issues`, `-i`

Ignorieren häufiger Probleme bei aktueller und bevorstehender Version

- Standard: `false`
- Akzeptiert keinen Wert

### `--context`

Ausführungskontext. Diese Option dient Integrationszwecken und hat keine Auswirkungen auf das Ausführungsergebnis.

- Erfordert einen Wert

### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl erhält, wird die Hilfe zur Anzeige des \&lt;info>list\&lt;/info> command

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert

