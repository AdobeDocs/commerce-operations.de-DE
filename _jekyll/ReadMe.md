---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
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
