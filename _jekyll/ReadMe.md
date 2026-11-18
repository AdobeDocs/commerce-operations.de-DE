---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%
---

# Überblick

Dieses Projekt verwendet RAKE-Aufgaben zur Automatisierung von Teilen des Dokumentations-Workflows. Die meisten Aufgaben werden über die Repositorys der ExL Commerce-Dokumente hinweg gemeinsam ausgeführt und stammen aus dem [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks) Gem. Einige der folgenden Aufgaben sind spezifisch für dieses Repository.

**Informationen zu häufigen Aufgaben (Rendering-Vorlagen, Verwalten von Includes, Optimieren/Überprüfen von Bildern, Generieren des neuen Digest) finden Sie unter [adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md).**

> Alle `bundle exec rake` folgenden Befehle müssen aus dem `_jekyll/` Verzeichnis heraus ausgeführt werden, da dort die Gemfile- und Rakefile-Datei vorhanden sind.

## Repo-spezifische Rake-Aufgaben

### `whatsnew_bp`

Erzeugt Daten für einen News-Digest unter Best Practices. Der Standardzeitrahmen ist seit der letzten Aktualisierung. Mit dem `since` Argument können Sie einen anderen Zeitraum angeben.

**Nutzung:**

```sh
bundle exec rake whatsnew_bp
```

**Mit `since` Argument:**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `whatsnew_consolidated`

Fasst veröffentlichte Neue Tabellen aus den konfigurierten Commerce-Dokumentationsprojekten in `help/_includes/automated/whatsnew/consolidated.md` zusammen.

```sh
bundle exec rake whatsnew_consolidated
```

Konfigurieren Sie Projekte unter `whatsnew_consolidated.projects` in [`_config.yml`](_config.yml). Jeder Eintrag erfordert einen Repository-Namen, einen Projekttitel und eine absolute HTTP(S)-Website-URL:

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/en/docs/commerce
```

Einträge in geänderte Abschnittsreihenfolge verschieben. Sie können Projekte von beiden Plattformen frei miteinander verzahnen. Repository-Namen, die mit enden`.en` verwenden den ExL-Quellpfad `help/_includes/templated/whats-new.md`. Alle anderen Repositorys verwenden `src/pages/_includes/templated/whats-new.md` den Quellpfad der DevSite.

Die Aufgabe ruft öffentliche `main` aus der `AdobeDocs` GitHub-Organisation ab. Er zeigt jeden Projekttitel als Textüberschrift an und führt jede Tabelle mit einem Satz ein, der den Projekttitel mit der Dokumentations-Startseite verknüpft, die in `website` als Quelle für die neuen Aktualisierungen konfiguriert ist. Durchgehend werden `Description | Type | Date/source` Tabellenüberschriften verwendet. Nur für DevSite-Projekte werden mit Escape-Zeichen versehene `\<br/\>`-Tags `<br/>`. Andernfalls bleiben Textzeilen, Duplikate, Links und die Reihenfolge der Quellzeilen unverändert. Jede Quelle definiert ihren eigenen Zeitraum.

Projekte mit einer erkannten Meldung, dass keine Aktualisierungen erfolgen, werden weggelassen. Wenn jedes Projekt keine Einträge hat, enthält die Einschließende eine allgemeine Nachricht, dass keine Aktualisierungen vorgenommen werden. Fehler beim Konfigurieren, Abrufen, Analysieren oder Schreiben schlagen bei der Aufgabe fehl, ohne dass ein vorhandenes Include ersetzt wird.

Die Aufgabe plant keine Generierung oder Aktualisierung verbrauchender Seiten.

Die fokussierte Test-Suite enthält Rake-Einstiegspunkttests, die die `_jekyll` Rakefile laden und durch den Bundler laufen. Installieren Sie zunächst Bundler und das `_jekyll`:

```sh
cd _jekyll && bundle install
```

Führen Sie dann die Tests aus dem Repository-Stamm aus:

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

Erstellt `help/_includes/automated/whatsnew/consolidated-feedback.md` durch Filtern der vorhandenen lokalen `help/_includes/automated/whatsnew/consolidated.md`.

```sh
bundle exec rake whatsnew_feedback
```

Die Aufgabe stimmt `Feedback` als vollständiger, durch Kommas getrennter Typwert überein, wobei Groß- und Kleinschreibung und das umgebende Leerzeichen ignoriert werden. Kombinierte Typen wie `Feedback, technical` sind enthalten. Erwähnungen in Beschreibungen, Quelllinks oder Namen partieller Typen sind nicht qualifiziert.

Übereinstimmende Zeilen, Duplikate, Projektüberschriften im Klartext, Quellsätze (falls vorhanden) und Projekt- und Zeilenreihenfolge bleiben unverändert. Projekte ohne übereinstimmende Einträge werden weggelassen. Wenn nichts übereinstimmt, enthält die Ausgabe insgesamt eine Nicht-Feedback-Nachricht.

Die Eingabe muss bereits vorhanden sein. Führen Sie `bundle exec rake whatsnew_consolidated` separat aus, wenn Sie es aktualisieren möchten. Die Feedback-Aufgabe ruft keine Remote-Inhalte ab, liest die Projektkonfiguration und generiert keine Eingabe.

Fehlende oder falsch formatierte Eingaben führen dazu, dass die Aufgabe fehlschlägt, ohne ein vorhandenes gefiltertes Include zu ersetzen. Die Eingabedatei wird nie geändert, und die gefilterte Ausgabe wird automatisch veröffentlicht.

### `get_released_versions`

Ruft die letzten 10 veröffentlichten Versionen aus dem `magento/magento2`-Repository ab. Erfordert [&#x200B; Installation und Authentifizierung von &#x200B;](https://cli.github.com/)GitHub CLI“.

**Nutzung:**

```sh
bundle exec rake get_released_versions
```

**Ausgabe:** Erzeugt `tmp/core-release.txt` mit Namen und Daten von Release-Tags.

### `first_merge_date`

Ruft das Datum der ersten Zusammenführung mit einer angegebenen Verzweigung ab. Erfordert [&#x200B; Installation und Authentifizierung von &#x200B;](https://cli.github.com/)GitHub CLI“.

**Nutzung:**

```sh
bundle exec rake first_merge_date base=develop
```

**Argumente:**

- `base` (erforderlich): Der Name der Zielverzweigung, auf die Zusammenführungen geprüft werden soll.

## Auflisten der verfügbaren Aufgaben

Um alle verfügbaren RAKE-Aufgaben mit ihren Beschreibungen anzuzeigen, verwenden Sie:

```sh
bundle exec rake --tasks
```

Detaillierte Informationen zu einer bestimmten Aufgabe finden Sie unter:

```sh
bundle exec rake -T [task_name]
```

## Dateiformat für Beziehungen einschließen

Die `include-relationships.yml` verfolgt die Beziehungen zwischen Hauptinhaltsdateien und ihren enthaltenen Dateien. Diese Datei wird automatisch von der `includes:maintain_relationships`-Aufgabe gepflegt (siehe [adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) zur Aufgabennutzung). Diese erkennt Beziehungen, indem sie vorhandene Include-Dateien liest und Hauptdateien findet, die darauf verweisen.

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
- Erforderliche Edelsteine, die in der Gemfile angegeben sind (allgemeine Aufgaben werden von `adobe-comdox-exl-rake-tasks` bereitgestellt; die `whatsnew` Aufgabe erfordert zusätzlich `whatsup_github`).
- [GitHub-CLI](https://cli.github.com/) für die `get_released_versions` und `first_merge_date` Aufgaben.

## Setup

Installieren Sie die erforderlichen Gems:

```sh
bundle install
```
