---
source-git-commit: ff21c497db7dd2aab90ded90fb3bba853e3c20f6
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 1%

---
# Bin/Cut

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**Version**: 3.0.24

Diese Referenz enthält 9 Befehle, die über das `bin/uct` Befehlszeilen-Tool verfügbar sind.
Die anfängliche Liste wird automatisch mit dem `bin/uct list`-Befehl in Adobe Commerce generiert.

## Allgemein

Weitere Informationen zum Tool finden Sie unter [Übersicht](/help/upgrade/upgrade-compatibility-tool/overview.md).

Diese Referenzdokumentation wird aus dem Programm-Quell-Code generiert. Um die Dokumentation zu ändern, sollten Sie eine Pull-Anfrage für den entsprechenden Befehl im entsprechenden [Codebase“-](https://github.com/magento) öffnen. Weitere Informationen [ Sie unter ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)Code-Beiträge“.

### Globale Optionen

#### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für den Listenbefehl angezeigt

- Standard: `false`
- Akzeptiert keinen Wert

#### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

#### `--no-ansi`

Negieren Sie die Option &quot;—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Interner Befehl zur Bereitstellung von Shell-Fertigstellungsvorschlägen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--shell`, `-s`

Der Schalentyp („bash“, „fish“, „zsh„)

- Erfordert einen Wert

#### `--input`, `-i`

Ein Array von Eingabe-Token (z. B. COMP_WORDS oder argv)

- Standard: `[]`
- Erfordert einen Wert

#### `--current`, `-c`

Der Index des „Eingabe“-Arrays, in dem sich der Cursor befindet (z. B. COMP_CWORD)

- Erfordert einen Wert

#### `--api-version`, `-a`

Die API-Version des Abschlussskripts

- Erfordert einen Wert

#### `--symfony`, `-S`

Veraltet

- Erfordert einen Wert


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Dump des Shell-Fertigstellungsskripts

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### Argumente

#### `shell`

Der Shell-Typ (z. B. „bash„), der Wert der &quot;$SHELL“-Env-Var wird verwendet, wenn diese nicht angegeben wird

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--debug`

Verfolgen Sie den Abschluss des Debug-Protokolls

- Standard: `false`
- Akzeptiert keinen Wert


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Anzeigen der Hilfe für einen Befehl

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumente

#### `command_name`

Der Befehlsname

- Standard: `help`

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

#### `--raw`

So geben Sie die Raw-Befehlshilfe aus

- Standard: `false`
- Akzeptiert keinen Wert


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Befehle auflisten

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### Argumente

#### `namespace`

Der Namespace-Name

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--raw`

Ausgabe der unbearbeiteten Befehlsliste

- Standard: `false`
- Akzeptiert keinen Wert

#### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

#### `--short`

So überspringen Sie die Beschreibung der Befehlsargumente

- Standard: `false`
- Akzeptiert keinen Wert


## `refactor`

```bash
bin/uct refactor <path>
```

Behebt die Probleme, die automatisch behoben werden können. Der Code im angegebenen Pfad wird aktualisiert.

### Argumente

#### `path`

Pfad zum Beheben von Problemen in .

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

Das Upgrade-Kompatibilitäts-Tool ist ein Befehlszeilen-Tool, das eine Adobe Commerce-Instanz mit einer bestimmten Version vergleicht, indem es alle darin installierten Nicht-Adobe Commerce-Module analysiert. Gibt eine Liste mit Fehlern und Warnungen zurück, die vor dem Upgrade auf eine neue Version von Adobe Commerce-Code behoben werden müssen.

### Argumente

#### `dir`

Adobe Commerce-Installationsverzeichnis.

- Erforderlich


#### `vanilla-dir`

Adobe Commerce Vanilla-Installationsverzeichnis.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Pfad der Datei, in die die Ausgabe exportiert wird (JSON-Format)

- Akzeptiert einen Wert


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Auflisten der Adobe Commerce DB-Schemaunterschiede zwischen zwei ausgewählten Versionen zulassen. Verfügbare Versionen: 2.3.0 | 2,3,1 | 2,3,2 | 2.3.2-p2 | 2,3,3 | 2.3.3-P1 | 2,3,4 | 2.3.4-p1 | 2.3.4-p2 | 2,3,5 | 2.3.5-p1 | 2.3.5-p2 | 2,3,6 | 2.3.6-p1 | 2,3,7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2,4,0 | 2.4.0-P1 | 2,4,1 | 2.4.1-p1 | 2,4,2 | 2.4.2-p1 | 2.4.2-p2 | 2,4,3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2,4,4 | 2.4.4-p1 | 2,4,5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2,4,6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-Beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-Beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-Beta3 | 2,4,7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-P10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-P11 | 2.4.5-P10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-Beta1 | 2.4.4-P12 | 2.4.5-P11 | 2.4.6-p9 | 2.4.7-p4 | 2.4.8-beta2 | 2.4.4-P13 | 2.4.5-P12 | 2.4.6-P10 | 2.4.7-p5 | 2,4,8 | 2.4.9-Alpha2 | 2.4.8-p2 | 2.4.7-p7 | 2.4.6-P12 | 2.4.5-P14 | 2.4.4-p15 | 2.4.9-Alpha1 | 2.4.8-p1 | 2.4.7-p6 | 2.4.6-P11 | 2.4.5-P13 | 2.4.4-P14

### Argumente

#### `current-version`

Aktuelle Version (z. B. 2.3.2).

- Erforderlich


#### `target-version`

Zielversion (z. B. 2.4.5).

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL-Schemakompatibilitätsüberprüfung

### Argumente

#### `schema1`

Endpunkt-URL, die auf das erste GraphQL-Schema verweist.

- Erforderlich


#### `schema2`

Endpunkt-URL, die auf das zweite GraphQL-Schema verweist.

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Pfad der Datei, in die die Ausgabe exportiert wird (JSON-Format)

- Akzeptiert einen Wert


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

Das Upgrade-Kompatibilitäts-Tool ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz mit einer bestimmten Version vergleicht, indem alle darin installierten Module analysiert werden. Gibt eine Liste mit Fehlern und Warnungen zurück, die behoben werden müssen, bevor ein Upgrade auf die neueste Version von Adobe Commerce durchgeführt wird.

### Argumente

#### `dir`

Adobe Commerce-Installationsverzeichnis.

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--current-version`, `-a`

Aktuelle Adobe Commerce-Version, Version der Adobe Commerce-Installation wird verwendet, wenn sie weggelassen wird.

- Akzeptiert einen Wert

#### `--coming-version`, `-c`

Adobe Commerce-Zielversion. Die neueste veröffentlichte stabile Version von Adobe Commerce wird verwendet, wenn sie weggelassen wird. Verfügbare Adobe Commerce-Versionen: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-P1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-P2 \| 2.3.5 \| 2.3.5-P1 \| 2.3.5-P2 \| 2.3.6 \| 2.3.6-P1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-P2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-P1 \| 2.4.1 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-P1 \| 2.4.3-P2 \| 2.4.3-P3 \| 2.4.4 \| 2.4.4-P1 \| 2.4.4-P2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-P7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-P10 \| 2.4.4-P11 \| 2.4.4-P12 \| 2.4.4-P13 \| 2.4.4-P14 \| 2.4.4-P15 \| 2.4.5 \| 2.4.5-P1 \| 2.4.5-P2 \| 2.4.5-P3 \| 2.4.5-P4 \| 2.4.5-p5 \| 2.4.5-P6 \| 2.4.5-P7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-P10 \| 2.4.5-P11 \| 2.4.5-P12 \| 2.4.5-P13 \| 2.4.5-P14 \| 2.4.6 \| 2.4.6-P1 \| 2.4.6-P2 \| 2.4.6-p3 \| 2.4.6-P4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-P7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-P10 \| 2.4.6-P11 \| 2.4.6-P12 \| 2.4.7-Beta1 \| 2.4.7-Beta2 \| 2.4.7-Beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-P2 \| 2.4.7-p3 \| 2.4.7-p4 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-P7 \| 2.4.8-Beta1 \| 2.4.8-Beta2 \| 2.4.8 \| 2.4.8-P1 \| 2.4.8-P2 \| 2.4.9-Alpha1 \| 2.4.9-Alpha2

- Akzeptiert einen Wert

#### `--json-output-path`

Pfad der Datei, aus der die Ausgabe im JSON-Format exportiert wird

- Akzeptiert einen Wert

#### `--html-output-path`

Pfad der Datei, in die die Ausgabe im HTML-Format exportiert wird

- Akzeptiert einen Wert

#### `--min-issue-level`

Minimale Problemstufe, die im Bericht angezeigt werden soll (Warnung, Fehler oder kritisch).

- Standard: `warning`
- Akzeptiert einen Wert

#### `--ignore-current-version-compatibility-issues`, `-i`

Häufige Probleme für aktuelle und kommende Version ignorieren

- Standard: `false`
- Akzeptiert keinen Wert

#### `--context`

Ausführungskontext Diese Option dient zu Integrationszwecken und hat keinen Einfluss auf das Ausführungsergebnis.

- Erfordert einen Wert

