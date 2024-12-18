---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Übersicht

Dieses Projekt umfasst mehrere RAKE-Aufgaben zur Automatisierung verschiedener Aspekte des Workflows, z. B. das Generieren von Daten für Nachrichten-Auszüge, das Rendern von Vorlagendateien, das Optimieren von Bildern und das Generieren von Karten. Nachstehend finden Sie die Beschreibungen und Nutzungsrichtlinien für jede Rake-Aufgabe, die in der Rake-Datei definiert ist.

## Aufgaben ausführen

### `render`

Rendert die Vorlagendateien im `_jekyll/templates` mit Daten aus `_jekyll/_data/`. Das Ergebnis befindet sich im `help/includes/templated`.

**Nutzung:**

```sh
rake render
```

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
