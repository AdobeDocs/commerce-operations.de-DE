---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# Magento-Cloud (Adobe Commerce über Cloud-Infrastruktur)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 1,38,1 <!-- app.version -->

Diese Referenz enthält 127 Befehle, die über das `magento-cloud` Befehlszeilen-Tool.
Die anfängliche Liste wird automatisch mit der Variablen `magento-cloud list` -Befehl an der Edition.

>[!NOTE]
>
>Diese Referenz wird aus der Anwendungs-Codebase generiert. Um den Inhalt zu ändern, können Sie den Quellcode für die entsprechende Befehlsimplementierung im [codebase](https://github.com/magento) Repository erstellen und Ihre Änderungen zur Überprüfung einreichen. Eine andere Möglichkeit besteht darin, _Feedback geben_ (finden Sie den Link oben rechts). Beitragsrichtlinien finden Sie unter [Codebeiträge](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BASH-Fertigungshaken.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



Generieren Sie einen BASH-Code, der die Fertigstellung für diese Anwendung einrichtet.
- Standard: `false`
- Akzeptiert keinen Wert



### `--program`, `-p`



Programmname, der zum Abschluss des Triggers verwendet werden soll &lt;comment>(standardmäßig der absolute Anwendungspfad)&lt;/comment>.
- Erfordert einen Wert



### `--multiple`, `-m`



Generierter Erweiterungspunkt kann für mehrere Anwendungen verwendet werden.
- Standard: `false`
- Akzeptiert keinen Wert


### `--shell-type`

Legen Sie den Shell-Typ (zsh oder bash) fest. Andernfalls wird dies automatisch bestimmt.
- Akzeptiert einen Wert <!-- options --> <!-- options.size -->

## `bot`

Magento Cloud Bot

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--party`


- Standard: `false`
- Akzeptiert keinen Wert


### `--parrot`


- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `clear-cache`

Löschen des CLI-Cache

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `decode`

Dekodieren einer kodierten Zeichenfolge wie MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

Der zu dekodierende Variablenwert
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die Eigenschaft, die in der -Variablen angezeigt werden soll
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `docs`

Öffnen Sie die Online-Dokumentation

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

Suchbegriff(e)

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

Der zum Öffnen der URL zu verwendende Browser. Legen Sie 0 für keine fest.
- Erfordert einen Wert


### `--pipe`

Geben Sie die URL für stdout aus.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `help`

Zeigt Hilfe für einen Befehl an

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

Der Befehlsname
- Standard: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

Das Ausgabeformat (txt, xml, json oder md)
- Standard: `txt`
- Erfordert einen Wert


### `--raw`

Ausgabe der Rohbefehl-Hilfe
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `legacy-migrate`

Aus der alten Dateistruktur migrieren

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

Erstellen Sie keine Sicherung des Projekts.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `list`

Listet Befehle auf

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

Der Namespace-Name
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

So geben Sie die unformatierte Befehlsliste aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (txt, xml, json oder md)
- Standard: `txt`
- Erfordert einen Wert <!-- options --> <!-- options.size -->

## `multi`

Ausführen eines Befehls für mehrere Projekte

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Der auszuführende Befehl
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



Eine Liste der Projekt-IDs, durch Kommas und/oder Leerzeichen getrennt
- Erfordert einen Wert


### `--continue`

Fahren Sie mit der Ausführung von Befehlen fort, selbst wenn eine Ausnahme aufgetreten ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--sort`

Eine Eigenschaft zum Sortieren der Liste der Projektoptionen
- Standard: `title`
- Erfordert einen Wert


### `--reverse`

Reihenfolge der Projektoptionen umkehren
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `web`

Öffnen Sie die Web-Benutzeroberfläche

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

Der zum Öffnen der URL zu verwendende Browser. Legen Sie 0 für keine fest.
- Erfordert einen Wert


### `--pipe`

Geben Sie die URL für stdout aus.
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `welcome`

Willkommen bei Magento Cloud

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `activity:cancel`

Aktivität abbrechen

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die Aktivitäts-ID. Die Standardeinstellung ist die neueste stornierbare Aktivität.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtern nach Typ (bei Auswahl einer Standardaktivität)
- Erfordert einen Wert



### `--all`, `-a`



Prüfung der letzten Aktivitäten in allen Umgebungen (bei Auswahl einer Standardaktivität)
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `activity:get`

Detaillierte Informationen zu einer einzelnen Aktivität anzeigen

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die Aktivitäts-ID. Die Standardeinstellung ist die neueste Aktivität.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Eigenschaft
- Erfordert einen Wert


### `--type`

Filtern nach Typ (bei Auswahl einer Standardaktivität)
- Erfordert einen Wert


### `--state`

Filtern nach Status (bei Auswahl einer Standardaktivität): in_progress, ausstehend, vollständig oder abgebrochen
- Standard: `[]`
- Erfordert einen Wert


### `--result`

Filtern nach Ergebnis (bei Auswahl einer Standardaktivität): Erfolg oder Misserfolg
- Erfordert einen Wert



### `--incomplete`, `-i`



Schließen Sie nur unvollständige Aktivitäten ein (bei Auswahl einer Standardaktivität). Dies ist eine Kurzanleitung für &lt;info>—state=in_progress,pending&lt;/info>
- Standard: `false`
- Akzeptiert keinen Wert



### `--all`, `-a`



Prüfung der letzten Aktivitäten in allen Umgebungen (bei Auswahl einer Standardaktivität)
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `activity:list`

Liste der Aktivitäten für eine Umgebung oder ein Projekt abrufen

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Aktivitäten nach Typ filtern
- Erfordert einen Wert


### `--limit`

Anzahl der angezeigten Ergebnisse begrenzen
- Standard: `10`
- Erfordert einen Wert


### `--start`

Es werden nur Aktivitäten aufgelistet, die vor diesem Datum erstellt wurden
- Erfordert einen Wert


### `--state`

Filtern von Aktivitäten nach Status: in_progress, ausstehend, vollständig oder abgebrochen
- Standard: `[]`
- Erfordert einen Wert


### `--result`

Filtern von Aktivitäten nach Ergebnis: Erfolg oder Misserfolg
- Erfordert einen Wert



### `--incomplete`, `-i`



Nur unvollständige Aktivitäten auflisten
- Standard: `false`
- Akzeptiert keinen Wert



### `--all`, `-a`



Aktivitäten in allen Umgebungen auflisten
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `activity:log`

Protokoll für eine Aktivität anzeigen

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die Aktivitäts-ID. Die Standardeinstellung ist die neueste Aktivität.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Intervall für die Aktivitätsaktualisierung (Sekunden). Auf 0 setzen, um die Aktualisierung zu deaktivieren.
- Standard: `3`
- Erfordert einen Wert



### `--timestamps`, `-t`



Zeitstempel neben jeder Nachricht anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--type`

Filtern nach Typ (bei Auswahl einer Standardaktivität)
- Erfordert einen Wert


### `--state`

Filtern nach Status (bei Auswahl einer Standardaktivität): in_progress, ausstehend, vollständig oder abgebrochen
- Standard: `[]`
- Erfordert einen Wert


### `--result`

Filtern nach Ergebnis (bei Auswahl einer Standardaktivität): Erfolg oder Misserfolg
- Erfordert einen Wert



### `--incomplete`, `-i`



Schließen Sie nur unvollständige Aktivitäten ein (bei Auswahl einer Standardaktivität). Dies ist eine Kurzanleitung für &lt;info>—state=in_progress,pending&lt;/info>
- Standard: `false`
- Akzeptiert keinen Wert



### `--all`, `-a`



Prüfung der letzten Aktivitäten in allen Umgebungen (bei Auswahl einer Standardaktivität)
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `api:curl`

Ausführen einer authentifizierten cURL-Anfrage für die Magento Cloud-API

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Der API-Pfad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



Die zu verwendende Anforderungsmethode
- Erfordert einen Wert



### `--data`, `-d`



Zu sendende Daten
- Erfordert einen Wert



### `--include`, `-i`



Kopfzeilen in die Ausgabe einschließen
- Standard: `false`
- Akzeptiert keinen Wert



### `--head`, `-I`



Nur Header abrufen
- Standard: `false`
- Akzeptiert keinen Wert


### `--disable-compression`

Verwenden Sie nicht das Flag curl —compression .
- Standard: `false`
- Akzeptiert keinen Wert


### `--enable-glob`

Aktivieren Sie curl globbing (entfernen Sie die Markierung —globoff )
- Standard: `false`
- Akzeptiert keinen Wert



### `--header`, `-H`



Zusätzliche Header
- Standard: `[]`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `app:config-get`

Konfiguration einer App anzeigen

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Konfigurationseigenschaft
- Erfordert einen Wert


### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--identity-file`, `-i`



[Veraltete Option, nicht mehr verwendet]
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `app:list`

Auflisten von Apps im Projekt

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `auth:api-token-login`

Bei der Magento Cloud über ein API-Token anmelden

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `auth:browser-login`

Über einen Browser bei Magento Cloud anmelden

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Melden Sie sich erneut an, auch wenn Sie bereits angemeldet sind
- Standard: `false`
- Akzeptiert keinen Wert


### `--browser`

Der zum Öffnen der URL zu verwendende Browser. Legen Sie 0 für keine fest.
- Erfordert einen Wert


### `--pipe`

Geben Sie die URL für stdout aus.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `auth:info`

Kontoinformationen anzeigen

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

Die anzuzeigende Kontoeigenschaft
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Kontoeigenschaft (alternative Syntax)
- Erfordert einen Wert


### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `auth:logout`

Aus der Magento Cloud abmelden

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Abmelden von allen lokalen Sitzungen
- Standard: `false`
- Akzeptiert keinen Wert


### `--other`

Abmelden von anderen lokalen Sitzungen
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Melden Sie sich mit einem Benutzernamen und einem Kennwort bei Magento Cloud an

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `auth:token`

Abrufen eines OAuth 2-Zugriffs-Tokens für Anfragen an Magento Cloud-APIs

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `blackfire:setup`

Einrichten der Blackfire.io-Integration für das Projekt

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

Server-ID
- Erfordert einen Wert


### `--server_token`

Server-Token
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `certificate:add`

Hinzufügen eines SSL-Zertifikats zum Projekt

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

Der Pfad zur Zertifikatdatei
- Erfordert einen Wert


### `--key`

Der Pfad zur Datei mit dem privaten Zertifikatschlüssel
- Erfordert einen Wert


### `--chain`

Der Pfad zur Zertifikatskettendatei
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `certificate:delete`

Zertifikat aus dem Projekt löschen

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die Zertifikatkennung (oder der Anfang)
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `certificate:get`

Zertifikat anzeigen

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die Zertifikatkennung (oder der Anfang)
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Zertifikateigenschaft
- Erfordert einen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `certificate:list`

Projektzertifikate auflisten

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

Filtern nach Domain-Namen (Suche ohne Unterscheidung zwischen Groß- und Kleinschreibung)
- Erfordert einen Wert


### `--exclude-domain`

Zertifikate ausschließen, die mit dem Domänennamen übereinstimmen (Suche ohne Unterscheidung zwischen Groß- und Kleinschreibung)
- Erfordert einen Wert


### `--issuer`

Nach Emittenten filtern
- Erfordert einen Wert


### `--only-auto`

Nur automatisch bereitgestellte Zertifikate anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-auto`

Nur manuell hinzugefügte Zertifikate anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ignore-expiry`

Sowohl abgelaufene als auch nicht abgelaufene Zertifikate anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--only-expired`

Nur abgelaufene Zertifikate anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-expired`

Nur nicht abgelaufene Zertifikate anzeigen (Standard)
- Standard: `false`
- Akzeptiert keinen Wert


### `--pipe-domains`

Nur eine Liste der Domänennamen zurückgeben, die von den Zertifikaten abgedeckt sind
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `commit:get`

Commit-Details anzeigen

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

Der Commit SHA. Dies kann auch Suffixe vom Typ &quot;HEAD&quot;und Caret (^) oder Tilde (~) für übergeordnete Commits akzeptieren.
- Standard: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Commit-Eigenschaft.
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert


### `--format`

VERALTET
- Erfordert einen Wert


### `--columns`

VERALTET
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

VERALTET
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `commit:list`

Auflisten von Commits

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

Das Git-Commit-SHA für den Start. Dies kann auch Suffixe vom Typ &quot;HEAD&quot;und Caret (^) oder Tilde (~) für übergeordnete Commits akzeptieren.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

Die Anzahl der anzuzeigenden Commits.
- Standard: `10`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `db:dump`

Lokalen Dump der Remote-Datenbank erstellen

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

Das Schema, das abgelegt werden soll. Option zur Verwendung des Standardschemas (normalerweise &quot;main&quot;).
- Erfordert einen Wert



### `--file`, `-f`



Ein benutzerdefinierter Dateiname für die Ablage
- Erfordert einen Wert



### `--directory`, `-d`



Ein benutzerdefiniertes Verzeichnis für den Dump
- Erfordert einen Wert



### `--gzip`, `-z`



Komprimieren Sie die Ablage mit gzip
- Standard: `false`
- Akzeptiert keinen Wert



### `--timestamp`, `-t`



Fügen Sie einen Zeitstempel zum Dateinamen der Dump-Datei hinzu.
- Standard: `false`
- Akzeptiert keinen Wert



### `--stdout`, `-o`



Ausgabe in STDOUT anstelle einer Datei
- Standard: `false`
- Akzeptiert keinen Wert


### `--table`

Zu berücksichtigende Tabelle(n)
- Standard: `[]`
- Erfordert einen Wert


### `--exclude-table`

Auszuschließende Tabelle(n)
- Standard: `[]`
- Erfordert einen Wert


### `--schema-only`

Nur Schemas ablegen, keine Daten
- Standard: `false`
- Akzeptiert keinen Wert


### `--charset`

Die Zeichensatzkodierung für die Dump
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `db:size`

Schätzen der Festplattenauslastung einer Datenbank

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Zeigt Größen in Byte an.
- Standard: `false`
- Akzeptiert keinen Wert



### `--cleanup`, `-C`



Überprüfen Sie, ob Tabellen bereinigt werden können, und zeigen Sie mir Empfehlungen an (nur InnoDb).
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `db:sql`

SQL auf der Remote-Datenbank ausführen

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

Eine auszuführende SQL-Anweisung
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Rohe, nicht tabellarische Ausgabe erzeugen
- Standard: `false`
- Akzeptiert keinen Wert


### `--schema`

Das zu verwendende Schema. Option zur Verwendung des Standardschemas (normalerweise &quot;main&quot;). Übergeben Sie eine leere Zeichenfolge, um kein Schema zu verwenden.
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `domain:add`

Hinzufügen einer neuen Domäne zum Projekt

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Domänenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Der Pfad zur Zertifikatdatei für diese Domäne
- Erfordert einen Wert


### `--key`

Der Pfad zur privaten Schlüsseldatei für das angegebene Zertifikat.
- Erfordert einen Wert


### `--chain`

Der Pfad zur Zertifikatskettendatei bzw. zu den Dateien für das bereitgestellte Zertifikat
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `domain:delete`

Eine Domäne aus dem Projekt löschen

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Domänenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `domain:get`

Detaillierte Informationen für eine Domäne anzeigen

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Domänenname
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Domäneneigenschaft
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `domain:list`

Liste aller Domänen abrufen

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `domain:update`

Domain aktualisieren

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Domänenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Der Pfad zur Zertifikatdatei für diese Domäne
- Erfordert einen Wert


### `--key`

Der Pfad zur privaten Schlüsseldatei für das angegebene Zertifikat.
- Erfordert einen Wert


### `--chain`

Der Pfad zur Zertifikatskettendatei bzw. zu den Dateien für das bereitgestellte Zertifikat
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:activate`

Aktivieren einer Umgebung

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Die zu aktivierenden Umgebungen

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

Festlegen einer neuen übergeordneten Umgebung vor der Aktivierung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:branch`

Verzweigung einer Umgebung

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die ID (Zweigname) der neuen Umgebung
<!-- argument -->

### `parent`

Das übergeordnete Element der neuen Umgebung
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

Der Titel der neuen Umgebung
- Erfordert einen Wert


### `--force`

Erstellen Sie die neue Umgebung, auch wenn der Zweig nicht lokal ausgecheckt werden kann.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-clone-parent`

Die Daten der übergeordneten Verzweigung nicht klonen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:checkout`

Auschecken einer Umgebung

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die ID der Umgebung, die ausgecheckt werden soll. Beispiel: &quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:delete`

Löschen einer Umgebung

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Zu löschende Umgebung(n)

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

Löschen Sie auch die Remote-Git-Verzweigungen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-delete-branch`

Löschen Sie die Remote-Git-Verzweigungen nicht.
- Standard: `false`
- Akzeptiert keinen Wert


### `--inactive`

Alle inaktiven Umgebungen löschen
- Standard: `false`
- Akzeptiert keinen Wert


### `--merged`

Alle zusammengeführten Umgebungen löschen
- Standard: `false`
- Akzeptiert keinen Wert


### `--exclude`

Umgebungen, die nicht gelöscht werden sollen
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:http-access`

Aktualisieren von HTTP-Zugriffseinstellungen für eine Umgebung

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

Zugriffsbeschränkungen im Format &quot;permission:address&quot;. Verwenden Sie 0, um alle Adressen zu löschen.
- Standard: `[]`
- Erfordert einen Wert


### `--auth`

HTTP Basic auth credentials im Format &quot;username:password&quot;. Verwenden Sie 0, um alle Berechtigungen zu löschen.
- Standard: `[]`
- Erfordert einen Wert


### `--enabled`

Ob die Zugriffskontrolle aktiviert werden soll: 1 zum Aktivieren, 0 zum Deaktivieren
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:info`

Eigenschaften für eine Umgebung lesen oder festlegen

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

Der Name der Eigenschaft
<!-- argument -->

### `value`

Neuen Wert für die Eigenschaft festlegen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:init`

Initialisieren einer Umgebung aus einem öffentlichen Git-Repository

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Eine URL zum Git-Repository
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

Der Name des Profils
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:list`

Liste der Umgebungen abrufen

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



Inaktive Umgebungen nicht anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--pipe`

Geben Sie eine einfache Liste von Umgebungs-IDs aus.
- Standard: `false`
- Akzeptiert keinen Wert


### `--refresh`

Gibt an, ob die Liste aktualisiert werden soll.
- Standard: `1`
- Erfordert einen Wert


### `--sort`

Eine Eigenschaft, nach der sortiert werden soll
- Standard: `title`
- Erfordert einen Wert


### `--reverse`

Sortieren in umgekehrter (absteigender) Reihenfolge
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:logs`

Protokolle einer Umgebung lesen

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

Der Protokolltyp, z. B. &quot;access&quot;oder &quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

Die Anzahl der anzuzeigenden Zeilen
- Standard: `100`
- Erfordert einen Wert


### `--tail`

Kontinuierliches Verfolgen des Protokolls
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:merge`

Zusammenführen einer Umgebung

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Die zusammenzuführende Umgebung
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:push`

Push-Code in eine Umgebung

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

Die Quell-Referenz: einen Zweignamen oder Commit-Hash
- Standard: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

Der Name der Zielverzweigung
- Erfordert einen Wert



### `--force`, `-f`



Nicht-schnelle Aktualisierungen zulassen
- Standard: `false`
- Akzeptiert keinen Wert


### `--force-with-lease`

Nicht-schnelle Aktualisierungen zulassen, wenn die Remote-Tracking-Verzweigung auf dem neuesten Stand ist
- Standard: `false`
- Akzeptiert keinen Wert



### `--set-upstream`, `-u`



Legen Sie die Zielumgebung als Upstream für den Quellzweig fest.
- Standard: `false`
- Akzeptiert keinen Wert


### `--activate`

Aktivieren der Umgebung vor dem Pushen
- Standard: `false`
- Akzeptiert keinen Wert


### `--branch`

VERALTET: alias of —activate
- Standard: `false`
- Akzeptiert keinen Wert


### `--parent`

Festlegen einer neuen übergeordneten Umgebung (nur mit —activate oder —branch verwendet)
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:redeploy`

Bereitstellung einer Umgebung

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:relationships`

Anzeigen der Beziehungen einer Umgebung

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Umwelt
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Beziehungseigenschaft
- Erfordert einen Wert


### `--refresh`

Ob die Beziehungen aktualisiert werden sollen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:scp`

Kopieren von Dateien in und aus der aktuellen Umgebung mithilfe von scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

Zu kopierende Dateien. Verwenden Sie die Remote-Verbindung: -Präfix, um Remote-Standorte zu definieren.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



rekursiv ganze Verzeichnisse kopieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:set-remote`

Remote-Umgebung für die Zuordnung zu einem Zweig festlegen

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Der Umgebungsmaschinenname. Auf 0 setzen, um die Zuordnung für eine Verzweigung zu entfernen
- Erforderlich

   <!-- argument -->

### `branch`

Die zuzuordnende Git-Verzweigung (standardmäßig der aktuelle Zweig)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:ssh`

SSH in die aktuelle Umgebung

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Ein Befehl, der in der Umgebung ausgeführt werden soll.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Geben Sie nur die SSH-URL aus.
- Standard: `false`
- Akzeptiert keinen Wert


### `--all`

Geben Sie alle SSH-URLs (für jede App) aus.
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:synchronize`

Synchronisieren des Codes und/oder der Daten einer Umgebung von der übergeordneten Umgebung

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

Was soll synchronisiert werden? &quot;code&quot;, &quot;data&quot;oder beides

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

Synchronisieren Sie den Code durch Rebasing anstelle der Zusammenführung.
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:url`

Abrufen der öffentlichen URLs einer Umgebung

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



Gibt nur die URL für die primäre Route zurück
- Standard: `false`
- Akzeptiert keinen Wert


### `--browser`

Der zum Öffnen der URL zu verwendende Browser. Legen Sie 0 für keine fest.
- Erfordert einen Wert


### `--pipe`

Geben Sie die URL für stdout aus.
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `environment:xdebug`

Öffnen Sie einen Tunnel zu Xdebug in der Umgebung

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

Der lokale Port
- Standard: `9000`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:activity:get`

Detaillierte Informationen zu einer einzelnen Integrationsaktivität anzeigen

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Eine Integrations-ID. Leer lassen, um aus einer Liste auszuwählen.
<!-- argument -->

### `activity`

Die Aktivitäts-ID. Die Standardeinstellung ist die neueste Integrationsaktivität.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Eigenschaft
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



[Veraltete Option, nicht verwendet]
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:activity:list`

Liste der Aktivitäten für eine Integration abrufen

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

Eine Integrations-ID. Leer lassen, um aus einer Liste auszuwählen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Aktivitäten nach Typ filtern
- Erfordert einen Wert


### `--limit`

Anzahl der angezeigten Ergebnisse begrenzen
- Standard: `10`
- Erfordert einen Wert


### `--start`

Es werden nur Aktivitäten aufgelistet, die vor diesem Datum erstellt wurden
- Erfordert einen Wert


### `--state`

Aktivitäten nach Status filtern
- Standard: `[]`
- Erfordert einen Wert


### `--result`

Aktivitäten nach Ergebnis filtern
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



[Veraltete Option, nicht verwendet]
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:activity:log`

Protokoll für eine Integrationsaktivität anzeigen

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Eine Integrations-ID. Leer lassen, um aus einer Liste auszuwählen.
<!-- argument -->

### `activity`

Die Aktivitäts-ID. Die Standardeinstellung ist die neueste Integrationsaktivität.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



Zeitstempel neben jeder Nachricht anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



[Veraltete Option, nicht verwendet]
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:add`

Hinzufügen einer Integration zum Projekt

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Der Integrationstyp (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pageruty&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)
- Erfordert einen Wert


### `--base-url`

Die Basis-URL der Serverinstallation
- Erfordert einen Wert


### `--username`

Der Benutzername des Bitbucket-Servers
- Erfordert einen Wert


### `--token`

Ein Zugriffstoken für die Integration
- Erfordert einen Wert


### `--key`

Ein Bitbucket OAuth-Verbraucherschlüssel
- Erfordert einen Wert


### `--secret`

Ein Bitbucket OAuth-Kundengeheimnis
- Erfordert einen Wert


### `--server-project`

Das Projekt (z. B. &#39;namespace/repo&#39;)
- Erfordert einen Wert


### `--repository`

Das Repository, das verfolgt werden soll (z. B. &#39;owner/repository&#39;)
- Erfordert einen Wert


### `--build-merge-requests`

GitLab: Erstellen von Zusammenführungsanfragen als Umgebungen
- Standard: `true`
- Erfordert einen Wert


### `--build-pull-requests`

Erstellen jeder Pull-Anforderung als Umgebung
- Standard: `true`
- Erfordert einen Wert


### `--build-draft-pull-requests`

Erstellen von Entwurfs-Pull-Anforderungen
- Standard: `true`
- Erfordert einen Wert


### `--build-pull-requests-post-merge`

Pull-Anforderungen basierend auf ihrem Postzusammenführungsstatus erstellen
- Standard: `false`
- Erfordert einen Wert


### `--build-wip-merge-requests`

GitLab: WIP-Zusammenführungsanfragen erstellen
- Standard: `true`
- Erfordert einen Wert


### `--merge-requests-clone-parent-data`

GitLab: Daten für Zusammenführungsanfragen klonen
- Standard: `true`
- Erfordert einen Wert


### `--pull-requests-clone-parent-data`

Daten der übergeordneten Umgebung für Pull-Anforderungen klonen
- Standard: `true`
- Erfordert einen Wert


### `--resync-pull-requests`

Synchronisieren von Umgebungsdaten für Pull-Anforderungen bei jedem Build
- Standard: `false`
- Erfordert einen Wert


### `--fetch-branches`

Abrufen aller Zweige aus der Remote-Umgebung (als inaktive Umgebungen)
- Standard: `true`
- Erfordert einen Wert


### `--prune-branches`

Löschen von Zweigen, die nicht auf der Remote-Site vorhanden sind
- Standard: `true`
- Erfordert einen Wert


### `--room`

HipChat-Raum-ID
- Erfordert einen Wert


### `--url`

Webhook: eine URL zum Empfangen von JSON-Daten
- Erfordert einen Wert


### `--shared-key`

Webhook: den gemeinsamen JWS-geheimen Schlüssel
- Erfordert einen Wert


### `--file`

Der Name einer lokalen Datei, die das hochzuladende Skript enthält
- Erfordert einen Wert


### `--events`

Eine Liste der Ereignisse, auf die reagiert werden soll, z. B. environment.push
- Standard: `*`
- Erfordert einen Wert


### `--states`

Eine Liste der Status, auf die reagiert werden soll, z. B. ausstehend, in_progress, complete
- Standard: `complete`
- Erfordert einen Wert


### `--environments`

Die einzuschließenden Umgebungs-IDs
- Standard: `*`
- Erfordert einen Wert


### `--excluded-environments`

Die auszuschließenden Umgebungs-IDs
- Standard: `[]`
- Erfordert einen Wert


### `--from-address`

[Optional] Benutzerdefinierte Absenderadresse für Warnhinweis-E-Mails
- Erfordert einen Wert


### `--recipients`

Die E-Mail-Adresse(n) des Empfängers
- Standard: `[]`
- Erfordert einen Wert


### `--channel`

Der Slack-Kanal
- Erfordert einen Wert


### `--routing-key`

Der PagerDuty-Routing-Schlüssel
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:delete`

Integration aus einem Projekt löschen

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die Integrations-ID. Leer lassen, um aus einer Liste auszuwählen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:get`

Details einer Integration anzeigen

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Eine Integrations-ID. Leer lassen, um aus einer Liste auszuwählen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Integrationseigenschaft
- Akzeptiert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:list`

Liste der Projektintegration(n) anzeigen

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:update`

Integration aktualisieren

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die ID der zu aktualisierenden Integration
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Der Integrationstyp (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pageruty&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)
- Erfordert einen Wert


### `--base-url`

Die Basis-URL der Serverinstallation
- Erfordert einen Wert


### `--username`

Der Benutzername des Bitbucket-Servers
- Erfordert einen Wert


### `--token`

Ein Zugriffstoken für die Integration
- Erfordert einen Wert


### `--key`

Ein Bitbucket OAuth-Verbraucherschlüssel
- Erfordert einen Wert


### `--secret`

Ein Bitbucket OAuth-Kundengeheimnis
- Erfordert einen Wert


### `--server-project`

Das Projekt (z. B. &#39;namespace/repo&#39;)
- Erfordert einen Wert


### `--repository`

Das Repository, das verfolgt werden soll (z. B. &#39;owner/repository&#39;)
- Erfordert einen Wert


### `--build-merge-requests`

GitLab: Erstellen von Zusammenführungsanfragen als Umgebungen
- Standard: `true`
- Erfordert einen Wert


### `--build-pull-requests`

Erstellen jeder Pull-Anforderung als Umgebung
- Standard: `true`
- Erfordert einen Wert


### `--build-draft-pull-requests`

Erstellen von Entwurfs-Pull-Anforderungen
- Standard: `true`
- Erfordert einen Wert


### `--build-pull-requests-post-merge`

Pull-Anforderungen basierend auf ihrem Postzusammenführungsstatus erstellen
- Standard: `false`
- Erfordert einen Wert


### `--build-wip-merge-requests`

GitLab: WIP-Zusammenführungsanfragen erstellen
- Standard: `true`
- Erfordert einen Wert


### `--merge-requests-clone-parent-data`

GitLab: Daten für Zusammenführungsanfragen klonen
- Standard: `true`
- Erfordert einen Wert


### `--pull-requests-clone-parent-data`

Daten der übergeordneten Umgebung für Pull-Anforderungen klonen
- Standard: `true`
- Erfordert einen Wert


### `--resync-pull-requests`

Synchronisieren von Umgebungsdaten für Pull-Anforderungen bei jedem Build
- Standard: `false`
- Erfordert einen Wert


### `--fetch-branches`

Abrufen aller Zweige aus der Remote-Umgebung (als inaktive Umgebungen)
- Standard: `true`
- Erfordert einen Wert


### `--prune-branches`

Löschen von Zweigen, die nicht auf der Remote-Site vorhanden sind
- Standard: `true`
- Erfordert einen Wert


### `--room`

HipChat-Raum-ID
- Erfordert einen Wert


### `--url`

Webhook: eine URL zum Empfangen von JSON-Daten
- Erfordert einen Wert


### `--shared-key`

Webhook: den gemeinsamen JWS-geheimen Schlüssel
- Erfordert einen Wert


### `--file`

Der Name einer lokalen Datei, die das hochzuladende Skript enthält
- Erfordert einen Wert


### `--events`

Eine Liste der Ereignisse, auf die reagiert werden soll, z. B. environment.push
- Standard: `*`
- Erfordert einen Wert


### `--states`

Eine Liste der Status, auf die reagiert werden soll, z. B. ausstehend, in_progress, complete
- Standard: `complete`
- Erfordert einen Wert


### `--environments`

Die einzuschließenden Umgebungs-IDs
- Standard: `*`
- Erfordert einen Wert


### `--excluded-environments`

Die auszuschließenden Umgebungs-IDs
- Standard: `[]`
- Erfordert einen Wert


### `--from-address`

[Optional] Benutzerdefinierte Absenderadresse für Warnhinweis-E-Mails
- Erfordert einen Wert


### `--recipients`

Die E-Mail-Adresse(n) des Empfängers
- Standard: `[]`
- Erfordert einen Wert


### `--channel`

Der Slack-Kanal
- Erfordert einen Wert


### `--routing-key`

Der PagerDuty-Routing-Schlüssel
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `integration:validate`

Bestehende Integration validieren

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Eine Integrations-ID. Leer lassen, um aus einer Liste auszuwählen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `local:build`

Aktuelles Projekt lokal erstellen

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

Zu erstellende Anwendung(en) angeben

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



Absolute Links verwenden
- Standard: `false`
- Akzeptiert keinen Wert



### `--source`, `-s`



Das Quellverzeichnis. Die Standardeinstellung ist der aktuelle Projektstamm.
- Erfordert einen Wert



### `--destination`, `-d`



Das Ziel, mit dem der Webstamm jeder App symverknüpft wird. Standard: _www
- Erfordert einen Wert



### `--copy`, `-c`



Kopieren Sie in ein Build-Verzeichnis, anstatt symlinks aus der Quelle zu verknüpfen.
- Standard: `false`
- Akzeptiert keinen Wert


### `--clone`

Verwenden Sie Git, um die aktuelle HEAD in den Build-Ordner zu klonen.
- Standard: `false`
- Akzeptiert keinen Wert


### `--run-deploy-hooks`

Ausführen von &quot;deploy&quot;und/oder &quot;post_deploy&quot;
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-clean`

Alte Builds nicht entfernen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-archive`

Erstellen oder Verwenden Sie kein Build-Archiv
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-backup`

vorherigen Build nicht sichern
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-cache`

Zwischenspeicherung deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-build-hooks`

Führen Sie keine Post-Build-Hooks aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-deps`

Build-Abhängigkeiten nicht lokal installieren
- Standard: `false`
- Akzeptiert keinen Wert


### `--working-copy`

Entfernen: Verwenden Sie Git, um ein Repository jedes Drupal-Moduls zu klonen, anstatt einfach eine Version herunterzuladen.
- Standard: `false`
- Akzeptiert keinen Wert


### `--concurrency`

Entfernen: Legen Sie die Anzahl gleichzeitiger Projekte fest, die gleichzeitig verarbeitet werden.
- Standard: `4`
- Erfordert einen Wert


### `--lock`

Entfernen: eine Sperrdatei erstellen oder aktualisieren (nur verfügbar mit der Drush-Version 7+)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `local:clean`

Alte Projekt-Builds entfernen

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

Die maximale Anzahl an Builds, die beibehalten werden sollen
- Standard: `5`
- Erfordert einen Wert


### `--max-age`

Das maximale Alter der Builds in Sekunden. Wird ignoriert, wenn nicht festgelegt.
- Erfordert einen Wert


### `--include-active`

Löschen aktiver Builds auch
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `local:dir`

Lokalen Projektstamm suchen

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

Das zu suchende Unterverzeichnis (&#39;local&#39;, &#39;web&#39; oder &#39;shared&#39;)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `mount:download`

Herunterladen von Dateien von einem Rich-Rich-Rsync-Server

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Download von allen Reittieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--mount`, `-m`



Die -Bereitstellung (als App-relativer Pfad)
- Erfordert einen Wert


### `--target`

Das Verzeichnis, in das die Dateien heruntergeladen werden. Wenn —all verwendet wird, wird der Bereitstellungspfad angehängt
- Erfordert einen Wert


### `--source-path`

Verwenden Sie den Quellpfad des Mount (anstelle des Bereitstellungspfads) als Unterverzeichnis des Ziels, wenn —all verwendet wird.
- Standard: `false`
- Akzeptiert keinen Wert


### `--delete`

Ob irrelevante Dateien im Zielverzeichnis gelöscht werden
- Standard: `false`
- Akzeptiert keinen Wert


### `--exclude`

Vom Download auszuschließende Datei(en) (Muster)
- Standard: `[]`
- Erfordert einen Wert


### `--include`

Datei(en), die in den Download aufgenommen werden soll (Muster)
- Standard: `[]`
- Erfordert einen Wert


### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `mount:list`

Liste der Reittiere abrufen

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

Nur die Bereitstellungspfade ausgeben (1 pro Zeile)
- Standard: `false`
- Akzeptiert keinen Wert


### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `mount:size`

Überprüfen Sie die Festplattenauslastung der Bereitstellungen.

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Größen in Byte anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--refresh`

Cache aktualisieren
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `mount:upload`

Hochladen von Dateien in eine -Bereitstellung mithilfe von Rsync

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

Ein Verzeichnis mit hochzuladenden Dateien
- Erfordert einen Wert



### `--mount`, `-m`



Die -Bereitstellung (als App-relativer Pfad)
- Erfordert einen Wert


### `--delete`

Ob irrelevante Dateien im Bereitstellungsfenster gelöscht werden
- Standard: `false`
- Akzeptiert keinen Wert


### `--exclude`

Vom Hochladen auszuschließende Datei(en) (Muster)
- Standard: `[]`
- Erfordert einen Wert


### `--include`

In den Upload einzuschließende Datei(en) (Muster)
- Standard: `[]`
- Erfordert einen Wert


### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--worker`

Arbeitername
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

Löschen des Build-Cache eines Projekts

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:curl`

Ausführen einer authentifizierten cURL-Anfrage für die API eines Projekts

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Der API-Pfad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



Die zu verwendende Anforderungsmethode
- Erfordert einen Wert



### `--data`, `-d`



Zu sendende Daten
- Erfordert einen Wert



### `--include`, `-i`



Kopfzeilen in die Ausgabe einschließen
- Standard: `false`
- Akzeptiert keinen Wert



### `--head`, `-I`



Nur Header abrufen
- Standard: `false`
- Akzeptiert keinen Wert


### `--disable-compression`

Verwenden Sie nicht das Flag curl —compression .
- Standard: `false`
- Akzeptiert keinen Wert


### `--enable-glob`

Aktivieren Sie curl globbing (entfernen Sie die Markierung —globoff )
- Standard: `false`
- Akzeptiert keinen Wert



### `--header`, `-H`



Zusätzliche Header
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:get`

Lokales Klonen eines Projekts

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

Die Projekt-ID
<!-- argument -->

### `directory`

Das Verzeichnis, in das geklont werden soll. Die Standardeinstellung ist der Projekttitel
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



Die zu klonende Umgebungs-ID. Die Standardeinstellung ist die Projektnummer oder die erste verfügbare Umgebung.
- Erfordert einen Wert


### `--depth`

Erstellen Sie einen flachen Klon: die Anzahl der Commits im Verlauf begrenzen
- Erfordert einen Wert


### `--build`

Erstellen des Projekts nach dem Klonen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:info`

Eigenschaften für ein Projekt lesen oder festlegen

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

Der Name der Eigenschaft
<!-- argument -->

### `value`

Neuen Wert für die Eigenschaft festlegen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:list`

Liste aller aktiven Projekte abrufen

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

Einfache Liste von Projekt-IDs ausgeben
- Standard: `false`
- Akzeptiert keinen Wert


### `--host`

Nach Region-Hostname filtern (genaue Übereinstimmung)
- Erfordert einen Wert


### `--title`

Nach Titel filtern (Suche ohne Unterscheidung zwischen Groß- und Kleinschreibung)
- Erfordert einen Wert


### `--my`

Nur die Projekte anzeigen, deren Inhaber Sie sind
- Standard: `false`
- Akzeptiert keinen Wert


### `--refresh`

Ob die Liste aktualisiert werden soll
- Standard: `1`
- Erfordert einen Wert


### `--sort`

Eine Eigenschaft, nach der sortiert werden soll
- Standard: `title`
- Erfordert einen Wert


### `--reverse`

Sortieren in umgekehrter (absteigender) Reihenfolge
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:set-remote`

Remote-Projekt für das aktuelle Git-Repository festlegen

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

Die Projekt-ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Variable aus einem Projekt löschen

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Variablenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Anzeigen von Variablen für ein Projekt

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Name der Variablen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Nur den vollständigen Variablenwert ausgeben (ein &quot;Name&quot;muss angegeben werden)
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Variable für ein Projekt festlegen

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Variablenname
- Erforderlich

   <!-- argument -->

### `value`

Der Variablenwert
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Den Wert als JSON markieren
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-visible-build`

Diese Variable nicht zur Build-Zeit verfügbar machen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-visible-runtime`

Diese Variable nicht zur Laufzeit verfügbar machen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `repo:cat`

Datei im Projekt-Repository lesen

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Der Pfad zur Datei
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



Der Commit SHA. Dies kann auch Suffixe vom Typ &quot;HEAD&quot;und Caret (^) oder Tilde (~) für übergeordnete Commits akzeptieren.
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `repo:ls`

Auflisten von Dateien im Projekt-Repository

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Der Pfad zu einem Unterverzeichnis
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



Nur Ordner anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--files`, `-f`



Nur Dateien anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--git-style`

Stilausgabe ähnlich &quot;git ls-tree&quot;
- Standard: `false`
- Akzeptiert keinen Wert



### `--commit`, `-c`



Der Commit SHA. Dies kann auch Suffixe vom Typ &quot;HEAD&quot;und Caret (^) oder Tilde (~) für übergeordnete Commits akzeptieren.
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `route:get`

Detaillierte Informationen zu einer Route anzeigen

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

Die ursprüngliche URL der Route
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

Eine Route-ID zur Auswahl
- Erfordert einen Wert



### `--primary`, `-1`



Primäre Route auswählen
- Standard: `false`
- Akzeptiert keinen Wert



### `--property`, `-P`



Die anzuzeigende Eigenschaft
- Erfordert einen Wert


### `--refresh`

Den Zwischenspeicher von Routen umgehen
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



[Veraltete Option, nicht mehr verwendet]
- Erfordert einen Wert



### `--identity-file`, `-i`



[Veraltete Option, nicht mehr verwendet]
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `route:list`

Alle Routen für eine Umgebung auflisten

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Die Umgebungs-ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Den Zwischenspeicher von Routen umgehen
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `self:install`

Installieren oder Aktualisieren von CLI-Konfigurationsdateien

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

Der Shell-Typ für die automatische Vervollständigung (bash oder zsh)
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `self:stats`

Statistiken zu GitHub-Paketdownloads anzeigen

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



Seitenzahl
- Standard: `1`
- Erfordert einen Wert



### `--count`, `-c`



Ergebnisse pro Seite (max.: 100)
- Standard: `20`
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `self:update`

CLI auf die neueste Version aktualisieren

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

Nur Aktualisierung zwischen kleineren oder Patch-Versionen
- Standard: `false`
- Akzeptiert keinen Wert


### `--unstable`

Aktualisierung auf eine neue instabile Version, falls verfügbar
- Standard: `false`
- Akzeptiert keinen Wert


### `--manifest`

Speicherort der Manifestdatei überschreiben
- Erfordert einen Wert


### `--current-version`

Aktuelle Version überschreiben
- Erfordert einen Wert


### `--timeout`

Eine Zeitüberschreitung für die Versionsüberprüfung
- Standard: `30`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `service:list`

Auflisten von Diensten im Projekt

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `service:mongo:dump`

Erstellen eines binären Archivierungs-Dump von Daten aus MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



Die Sammlung, die abgelegt werden soll
- Erfordert einen Wert



### `--gzip`, `-z`



Komprimieren Sie die Ablage mit gzip
- Standard: `false`
- Akzeptiert keinen Wert



### `--stdout`, `-o`



Ausgabe in STDOUT anstelle einer Datei
- Standard: `false`
- Akzeptiert keinen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `service:mongo:export`

Daten aus MongoDB exportieren

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



Zu exportierende Kollektion
- Erfordert einen Wert


### `--jsonArray`

Daten als einzelnes JSON-Array exportieren
- Standard: `false`
- Akzeptiert keinen Wert


### `--type`

Der Exporttyp, z. B. &quot;csv&quot;
- Erfordert einen Wert



### `--fields`, `-f`



Zu exportierende Felder
- Standard: `[]`
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `service:mongo:restore`

Wiederherstellen eines binären Archivierungs-Dump von Daten in MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



Die wiederherzustellende Sammlung
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `service:mongo:shell`

MongoDB-Shell verwenden

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

Übergeben eines JavaScript-Fragments an die Shell
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `service:redis-cli`

Zugriff auf die Redis-CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Argumente, die zum Befehl &quot;Redis&quot;hinzugefügt werden sollen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Zwischen Sitzungen wechseln

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die neue Sitzungs-ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `snapshot:create`

Schnappschuss einer Umgebung erstellen

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Umwelt
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

Live Backup: stoppen Sie nicht die Umgebung. Wenn diese Einstellung festgelegt ist, bleibt die Umgebung aktiv und während der Sicherung für Verbindungen geöffnet. Dadurch werden Ausfallzeiten reduziert, wodurch das Risiko besteht, Daten in einem inkonsistenten Zustand zu sichern.
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `snapshot:list`

Verfügbare Momentaufnahmen einer Umgebung auflisten

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

Anzahl der aufzulistenden Momentaufnahmen begrenzen
- Standard: `10`
- Erfordert einen Wert


### `--start`

Es werden nur Momentaufnahmen aufgelistet, die vor diesem Datum erstellt wurden
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `snapshot:restore`

Wiederherstellen eines Umgebungs-Snapshots

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

Der Name der Momentaufnahme. Die Standardeinstellung ist die neueste
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

Die wiederherzustellende Umgebung. Die Standardeinstellung ist die aktuelle Umgebung des Snapshots.
- Erfordert einen Wert


### `--branch-from`

Wenn das —target noch nicht vorhanden ist, gibt dies das übergeordnete Element der neuen Umgebung an
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Quellvorgang ausführen

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

Der Vorgangsname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

Variable, die während des Vorgangs im Format &lt;info>type:name=value&lt;/info>
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `ssh-cert:info`

Anzeigen von Informationen zum aktuellen SSH-Zertifikat

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

Aktualisieren Sie das Zertifikat nicht, wenn es ungültig ist.
- Standard: `false`
- Akzeptiert keinen Wert



### `--property`, `-P`



Die anzuzeigende Zertifikateigenschaft
- Erfordert einen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `ssh-cert:load`

Erstellen eines SSH-Zertifikats

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

Aktualisieren Sie das Zertifikat nur bei Bedarf (schreiben Sie keine SSH-Konfiguration).
- Standard: `false`
- Akzeptiert keinen Wert


### `--new`

Aktualisieren des Zertifikats erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--new-key`

[Veraltet] Verwenden Sie stattdessen —new .
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `ssh-key:add`

Hinzufügen eines neuen SSH-Schlüssels

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Der Pfad zu einem vorhandenen öffentlichen SSH-Schlüssel
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

Ein Name zur Identifizierung des Schlüssels
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `ssh-key:delete`

SSH-Schlüssel löschen

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Die ID des zu löschenden SSH-Schlüssels
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `ssh-key:list`

Abrufen einer Liste von SSH-Schlüsseln in Ihrem Konto

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `subscription:info`

Abonnementeigenschaften lesen und ändern

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

Der Name der Eigenschaft
<!-- argument -->

### `value`

Neuen Wert für die Eigenschaft festlegen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



Die Abonnement-ID
- Erfordert einen Wert


### `--date-fmt`

Das Datumsformat (als PHP-Datumsformat-Zeichenfolge)
- Standard: `c`
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `tunnel:close`

SSH-Tunnel schließen

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Schließen aller Tunnel
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `tunnel:info`

Anzeigen von Beziehungsinformationen für SSH-Tunnel

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



Die anzuzeigende Beziehungseigenschaft
- Erfordert einen Wert



### `--encode`, `-c`



Ausgabe als base64-kodierte JSON
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `tunnel:list`

SSH-Tunnel auflisten

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Alle Tunnel anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `tunnel:open`

SSH-Tunnel für die Beziehungen einer App öffnen

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



Remote-Hosts erlauben, eine Verbindung zu lokalen weitergeleiteten Ports herzustellen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `tunnel:single`

Öffnen eines einzelnen SSH-Tunnels für eine App-Beziehung

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

Der lokale Port
- Erfordert einen Wert



### `--gateway-ports`, `-g`



Remote-Hosts erlauben, eine Verbindung zu lokalen weitergeleiteten Ports herzustellen
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--app`, `-A`



Der Name der Remote-Anwendung
- Erfordert einen Wert



### `--relationship`, `-r`



Die zu verwendende Dienstbeziehung
- Erfordert einen Wert



### `--identity-file`, `-i`



Eine SSH-Identität (privater Schlüssel) zur Verwendung
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `user:add`

Einen Benutzer zum Projekt hinzufügen

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

Die E-Mail-Adresse des Benutzers
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



Die Projektrolle des Benutzers (&#39;admin&#39; oder &#39;viewer&#39;) oder umgebungsspezifische Rolle (z. B. &quot;Übergeordnet:contributor&quot;oder &quot;stage:viewer&quot;). Das Zeichen % kann als Platzhalter in der Umgebungs-ID verwendet werden, z. B. &#39;%:viewer&#39;. Die Rolle kann abgekürzt werden, z. B. &quot;Übergeordnet:c&quot;.
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `user:delete`

Benutzer aus dem Projekt löschen

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

Die E-Mail-Adresse des Benutzers
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `user:get`

Benutzerrollen anzeigen

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

Die E-Mail-Adresse des Benutzers
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Die Rollenebene (&quot;Projekt&quot;oder &quot;Umgebung&quot;)
- Erfordert einen Wert


### `--pipe`

Ausgabe der zu stdout zu sendenden Rolle (nach Durchführung von Änderungen)
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--role`, `-r`



[Veraltet: Verwenden Sie user:update , um die Benutzerrolle(en) zu ändern]
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `user:list`

Projektbenutzer auflisten

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `user:update`

Benutzerrollen in einem Projekt aktualisieren

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

Die E-Mail-Adresse des Benutzers
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



Die Projektrolle des Benutzers (&#39;admin&#39; oder &#39;viewer&#39;) oder umgebungsspezifische Rolle (z. B. &quot;Übergeordnet:contributor&quot;oder &quot;stage:viewer&quot;). Das Zeichen % kann als Platzhalter in der Umgebungs-ID verwendet werden, z. B. &#39;%:viewer&#39;. Die Rolle kann abgekürzt werden, z. B. &quot;Übergeordnet:c&quot;.
- Standard: `[]`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:create`

Variable erstellen

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Variablenname
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Die Ebene, auf der die Variable festgelegt werden soll (&quot;Projekt&quot;oder &quot;Umgebung&quot;)
- Erfordert einen Wert


### `--name`

Der Variablenname
- Erfordert einen Wert


### `--value`

Der Wert der Variablen
- Erfordert einen Wert


### `--json`

Ob die Variable JSON-formatiert ist
- Standard: `false`
- Erfordert einen Wert


### `--sensitive`

Ob die Variable empfindlich ist
- Standard: `false`
- Erfordert einen Wert


### `--prefix`

Das Präfix des Variablennamens (z. B. &#39;none&#39; oder &#39;env:&#39;)
- Standard: `none`
- Erfordert einen Wert


### `--enabled`

Ob die Variable aktiviert werden soll
- Standard: `true`
- Erfordert einen Wert


### `--inheritable`

Ob die Variable von untergeordneten Umgebungen vererbt werden kann
- Standard: `true`
- Erfordert einen Wert


### `--visible-build`

Ob die Variable zur Build-Zeit sichtbar sein soll
- Standard: `true`
- Erfordert einen Wert


### `--visible-runtime`

Ob die Variable zur Laufzeit sichtbar sein soll
- Standard: `true`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:delete`

Variable löschen

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Variablenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Die Variablenebene (&quot;Projekt&quot;, &quot;Umgebung&quot;, &quot;p&quot;oder &quot;e&quot;)
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Eine aktivierte Umgebungsvariable deaktivieren

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Name der Variablen
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Aktiviert eine deaktivierte Variable auf Umgebungsebene

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Name der Variablen
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:get`

Anzeigen von Variablen

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Name der Variablen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Anzeigen einer einzelnen Variableneigenschaft
- Erfordert einen Wert



### `--level`, `-l`



Die Variablenebene (&quot;Projekt&quot;, &quot;Umgebung&quot;, &quot;p&quot;oder &quot;e&quot;)
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--pipe`

[Veraltete Option] Nur Variablenwert ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:list`

Listenvariablen

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



Die Variablenebene (&quot;Projekt&quot;, &quot;Umgebung&quot;, &quot;p&quot;oder &quot;e&quot;)
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VERALTET ]&lt;/> Variable für eine Umgebung festlegen

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Variablenname
- Erforderlich

   <!-- argument -->

### `value`

Der Variablenwert
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Den Wert als JSON markieren
- Standard: `false`
- Akzeptiert keinen Wert


### `--disabled`

Kennzeichnen der Variablen als deaktiviert
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `variable:update`

Variable aktualisieren

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Der Variablenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Die Variablenebene (&quot;Projekt&quot;, &quot;Umgebung&quot;, &quot;p&quot;oder &quot;e&quot;)
- Erfordert einen Wert


### `--value`

Der Wert der Variablen
- Erfordert einen Wert


### `--json`

Ob die Variable JSON-formatiert ist
- Standard: `false`
- Erfordert einen Wert


### `--sensitive`

Ob die Variable empfindlich ist
- Standard: `false`
- Erfordert einen Wert


### `--enabled`

Ob die Variable aktiviert werden soll
- Standard: `true`
- Erfordert einen Wert


### `--inheritable`

Ob die Variable von untergeordneten Umgebungen vererbt werden kann
- Standard: `true`
- Erfordert einen Wert


### `--visible-build`

Ob die Variable zur Build-Zeit sichtbar sein soll
- Standard: `true`
- Erfordert einen Wert


### `--visible-runtime`

Ob die Variable zur Laufzeit sichtbar sein soll
- Standard: `true`
- Erfordert einen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert



### `--no-wait`, `-W`



Warten Sie nicht, bis der Vorgang abgeschlossen ist.
- Standard: `false`
- Akzeptiert keinen Wert


### `--wait`

Warten Sie, bis der Vorgang abgeschlossen ist (Standard)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `worker:list`

Liste aller entsandten Arbeitskräfte abrufen

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Ob der Cache aktualisiert werden soll
- Standard: `false`
- Akzeptiert keinen Wert



### `--project`, `-p`



Die Projekt-ID oder URL
- Erfordert einen Wert


### `--host`

Der API-Hostname des Projekts
- Erfordert einen Wert



### `--environment`, `-e`



Die Umgebungs-ID
- Erfordert einen Wert


### `--format`

Das Ausgabeformat (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot;oder &quot;plain&quot;)
- Standard: `table`
- Erfordert einen Wert


### `--columns`

Anzuzeigende Spalten (kommagetrennte Liste oder mehrere Werte)
- Standard: `[]`
- Erfordert einen Wert


### `--no-header`

Geben Sie die Tabellenüberschrift nicht aus
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Die Ausführlichkeit von Nachrichten erhöhen
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--yes`, `-y`



Antworten Sie auf alle Ja-/Nein-Fragen mit &quot;Ja&quot;; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert



### `--no`, `-n`



Antwort &quot;nein&quot; auf alle Ja/Nein-Fragen; Deaktivieren der Interaktion
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->