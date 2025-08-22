---
source-git-commit: 926ca67d3878de14cf7ee6940e4226ac29a76919
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---
# Bibliotheksdateien mitnehmen

Dieses Verzeichnis enthält Aufgabendefinitionen für die Aufgabe nach Funktionen. Rake lädt automatisch alle `.rake` Dateien in diesem Verzeichnis.

## Dateiorganisation

### `includes.rake`

Enthält alle Include-bezogenen RAKE-Aufgaben unter dem `:includes`-Namespace:

- `includes:maintain_relationships` - Erkennen und Verwalten von Include-Beziehungen
- `includes:maintain_timestamps` - Hinzufügen/Aktualisieren von Zeitstempeln basierend auf eingeschlossenen Dateiänderungen
- `includes:maintain_all` - Führen Sie beide Vorgänge nacheinander aus.

## Funktionsweise

Rake erkennt und lädt automatisch alle `.rake` Dateien in das `rakelib/`. Dies ermöglicht Folgendes:

1. **Aufgaben nach Funktion organisieren** - Gruppieren verwandter Aufgaben
2. **Keep the main Rakefile clean** - Fokus auf zentrale Projektaufgaben
3. **Einfaches Hinzufügen neuer Aufgabengruppen** - Einfach neue `.rake` erstellen
4. **Trennung von Belangen beibehalten** - Jede Datei verarbeitet eine bestimmte Domain

## Hinzufügen neuer Aufgabengruppen

So fügen Sie eine neue Gruppe verwandter Aufgaben hinzu:

1. Erstellen Sie eine neue `.rake` in diesem Verzeichnis
2. Verwenden eines beschreibenden Namespace (z. B. `namespace :images` für bildbezogene Aufgaben)
3. Aufgaben im Namespace definieren
4. Rake lädt sie automatisch

## Beispielstruktur

```ruby
namespace :your_namespace do
  desc 'Description of what this task does'
  task :task_name do
    # Task implementation
  end
end
```

## Nutzung

Aufgaben sind sofort nach der Erstellung verfügbar:

```bash
rake your_namespace:task_name
```

## Vorteile

- **Modularität**: Jede Datei konzentriert sich auf einen bestimmten Bereich
- **Wartbarkeit**: Einfacheres Suchen und Ändern bestimmter Aufgabengruppen
- **Skalierbarkeit**: Kann viele Aufgabengruppen hinzufügen, ohne die Haupt-Rakefile zu überladen
- **Team-Entwicklung**: Verschiedene Entwickler können mit verschiedenen Aufgabengruppen arbeiten
