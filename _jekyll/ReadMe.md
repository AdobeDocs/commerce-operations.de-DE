---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Übersicht

Dieses Projekt umfasst mehrere Rake-Aufgaben zur Automatisierung verschiedener Aspekte des Workflows, z. B. die Generierung von Daten für Nachrichtendigests, das Rendern von Vorlagendateien, die Optimierung von Bildern und das Generieren von Karten. Im Folgenden finden Sie die Beschreibungen und Nutzungsrichtlinien für jede Rake-Aufgabe, die in der Rakefile definiert ist.

## Aufgaben wiedergeben

### `render`

Rendert die Vorlagendateien im Verzeichnis `_jekyll/templates` mit Daten aus `_jekyll/_data/`. Das Ergebnis finden Sie im Verzeichnis &quot;`help/includes/templated`&quot;.

**Nutzung:**

```sh
rake render
```

### `image_optim`

Optimiert Bilder in modifizierten nicht gebundenen Dateien. Für andere Bilder verwenden Sie das `path`-Argument, um das Verzeichnis oder die Datei anzugeben.

**Nutzung:**

```sh
rake image_optim
```

**Mit `path` Argument:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Erstellt Daten für einen NewsDigest. Der standardmäßige Zeitraum ist seit der letzten Aktualisierung verstrichen. Mit dem `since` -Argument können Sie einen anderen Zeitraum angeben.

**Nutzung:**

```sh
rake whatsnew
```

**Mit `since` Argument:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Erstellt Daten für einen Newsdigest in Best Practices. Der standardmäßige Zeitraum ist seit der letzten Aktualisierung verstrichen. Mit dem `since` -Argument können Sie einen anderen Zeitraum angeben.

**Nutzung:**

```sh
rake whatsnew_bp
```

**Mit `since` Argument:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Generiert eine Azure-Regionen-Zuordnung. Die Eingabedatendatei sollte in `_jekyll/tmp/azure-regions.json` platziert werden. Das Ergebnis finden Sie in `_jekyll/tmp/azure-regions.svg`. Beachten Sie, dass Python, [PyGMT](https://www.pygmt.org/latest/install.html) und [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) installiert sein müssen.

**Nutzung:**

```sh
rake azure_regions
```

## Voraussetzungen

- Ruby und Bundler installiert.
- Erforderliche Werte, die in der Gemfile angegeben sind.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) und [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) für die Aufgabe `azure_regions`.

## Einrichtung

1. Installieren Sie die erforderlichen Edelsteine:

   ```sh
   bundle install
   ```

2. Stellen Sie sicher, dass Python, PyGMT und pdf2svg für die Aufgabe &quot;`azure_regions`&quot;installiert sind. Weitere Informationen zum Setup finden Sie in der Dokumentation in Kommentaren unter [_scripts/azure_regions.py](_scripts/azure_regions.py).
