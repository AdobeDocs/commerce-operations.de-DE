---
source-git-commit: 9994f486c38df4c0dc2ff477c48f3e8f3259aa9f
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---
# Überblick

Dieses Projekt umfasst mehrere RAKE-Aufgaben zur Automatisierung verschiedener Aspekte des Workflows, z. B. das Generieren von Daten für Nachrichten-Auszüge, das Rendern von Vorlagendateien, das Optimieren von Bildern und das Generieren von Karten. Nachstehend finden Sie die Beschreibungen und Nutzungsrichtlinien für jede Rake-Aufgabe, die in der Rake-Datei definiert ist.

## Aufgaben ausführen

### `render`

Rendert die Vorlagendateien im `_jekyll/templates` mit Daten aus `_jekyll/_data/`. Das Ergebnis befindet sich im `help/includes/templated`. Diese Aufgabe verwaltet nach dem Rendern automatisch Include-Beziehungen und Zeitstempel.

**Nutzung:**

```sh
rake render
```

**Funktion:**
- Führt das Render-Skript aus, um vorlagenbasierte Dateien zu generieren
- `includes:maintain_all` zur Aktualisierung von Include-Beziehungen und Zeitstempeln
- Stellt sicher, dass alle eingeschlossenen Metadaten nach dem Rendern aktuell sind

### `image_optim`

Optimiert Bilder in geänderten, nicht übergebenen Dateien. Verwenden Sie für andere Bilder das `path`-Argument, um das Verzeichnis oder die Datei anzugeben.

**Nutzung:**

```sh
rake image_optim
```

**Mit `path` Argument:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Erzeugt Daten für einen Newsauszug. Der Standardzeitrahmen ist seit der letzten Aktualisierung. Mit dem `since` Argument können Sie einen anderen Zeitraum angeben.

**Nutzung:**

```sh
rake whatsnew
```

**Mit `since` Argument:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Erzeugt Daten für einen News-Digest unter Best Practices. Der Standardzeitrahmen ist seit der letzten Aktualisierung. Mit dem `since` Argument können Sie einen anderen Zeitraum angeben.

**Nutzung:**

```sh
rake whatsnew_bp
```

**Mit `since` Argument:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Erstellt eine Azure-Regionszuordnung. Die Eingabedatendatei sollte in `_jekyll/tmp/azure-regions.json` platziert werden. Das Ergebnis befindet sich in `_jekyll/tmp/azure-regions.svg`. Beachten Sie, dass Python, [PyGMT](https://www.pygmt.org/latest/install.html) und [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) installiert sein müssen.

**Nutzung:**

```sh
rake azure_regions
```

### `includes:maintain_relationships`

Erkennt und aktualisiert die `include-relationships.yml`-Datei, indem alle Markdown-Dateien im `help`-Verzeichnis mithilfe des Muster-`{{$include /help/_includes/filename.md}}` auf Include-Anweisungen überprüft werden. Diese Aufgabe behält automatisch die Beziehungen zwischen Hauptinhaltsdateien und ihren enthaltenen Dateien bei.

**Nutzung:**

```sh
rake includes:maintain_relationships
```

**Funktion:**
- Liest die Liste der vorhandenen Include-Dateien aus dem `help/_includes`
- Durchsucht alle Haupt-Markdown-Dateien, um herauszufinden, welche jeweils auf verweisen.
- Verwendet das `{{$include /help/_includes/filename.md}}`, um Verweise zu identifizieren
- Aktualisiert die `include-relationships.yml` mit erkannten Beziehungen
- Bietet eine Zusammenfassung der vorgenommenen Änderungen und kennzeichnet nicht referenzierte Includes

### `includes:maintain_timestamps`

Behält eingeschlossene Zeitstempel bei, indem die neuesten eingeschlossenen Dateiänderungszeitstempel zu Hauptdateien hinzugefügt werden. Diese Aufgabe liest die `include-relationships.yml`-Datei, prüft den Git-Verlauf für jede Include-Datei und fügt Zeitstempel am Ende der Hauptdateien hinzu oder aktualisiert diese.

**Nutzung:**

```sh
rake includes:maintain_timestamps
```

**Funktion:**
- Lasten beinhalten Beziehungen aus `include-relationships.yml`
- Für jede Hauptdatei findet unter den eingeschlossenen Dateien das neueste Git-Commit-Datum
- Fügt HTML-Kommentare mit Zeitstempeln am Ende der Hauptdateien hinzu oder aktualisiert diese
- Verwendet das Format: `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Bietet eine detaillierte Ausgabe, die anzeigt, welche Include-Dateien überprüft wurden, und deren Zeitstempel

**Beispielausgabe:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

Eine praktische Aufgabe, die sowohl `includes:maintain_relationships` als auch `includes:maintain_timestamps` nacheinander ausgeführt wird. Dies ist die empfohlene Methode, um sowohl Include-Beziehungen als auch Zeitstempel zu pflegen.

**Nutzung:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Sucht Include-Dateien im `help/_includes`, auf die keine Markdown-Dateien verweisen. Auf diese Weise können verwaiste Include-Dateien identifiziert werden, die sicher entfernt werden können.

**Nutzung:**

```sh
rake unused_includes
```

## Auflisten der verfügbaren Aufgaben

Um alle verfügbaren RAKE-Aufgaben mit ihren Beschreibungen anzuzeigen, verwenden Sie:

```sh
rake --tasks
```

Detaillierte Informationen zu einer bestimmten Aufgabe finden Sie unter:

```sh
rake -T [task_name]
```

## Verwaltungsaufgaben einschließen

Alle mit Include zusammenhängenden Aufgaben sind zur besseren Organisation unter dem `includes`-Namespace organisiert:

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Dateiformat für Beziehungen einschließen

Die `include-relationships.yml` verfolgt die Beziehungen zwischen Hauptinhaltsdateien und ihren enthaltenen Dateien. Diese Datei wird automatisch von der Aufgabe &quot;`maintain_include_relationships` Rake“ verwaltet, die Beziehungen erkennt, indem sie vorhandene Include-Dateien liest und Hauptdateien findet, die auf sie verweisen.

**Dateistruktur:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Felder:**
- `metadata.last_updated`: Zeitstempel der letzten Aktualisierung
- `metadata.total_relationships`: Gesamtzahl der Hauptdateien mit Einschlüssen
- `metadata.auto_discovered`: Zeigt an, dass die Datei automatisch generiert wurde
- `metadata.discovery_date`: Datum, an dem Beziehungen zum ersten Mal erkannt wurden
- `relationships`: Zuordnung der Hauptdateien zu den zugehörigen Dateien

**Include-Anweisungsformat:**
Hauptinhaltsdateien verwenden die folgende Syntax, um andere Dateien einzuschließen:

```markdown
{{$include /help/_includes/filename.md}}
```

## Voraussetzungen

- Ruby und Bundler installiert.
- Erforderliche Edelsteine, die in der Gemfile angegeben sind.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) und [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) für die `azure_regions`.

## Setup

1. Installieren Sie die erforderlichen Gems:

   ```sh
   bundle install
   ```

2. Stellen Sie sicher, dass Python, PyGMT und pdf2svg für die `azure_regions` installiert sind. Weitere Informationen zum Setup finden Sie in der Dokumentation unter Kommentare unter [_scripts/azure_regions.py](_scripts/azure_regions.py).
