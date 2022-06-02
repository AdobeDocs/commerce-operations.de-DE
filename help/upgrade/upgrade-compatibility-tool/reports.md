---
title: '"[!DNL Upgrade Compatibility Tool] reports"'
description: Führen Sie die folgenden Schritte aus, um [!DNL Upgrade Compatibility Tool] in Ihrem Adobe Commerce-Projekt.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Berichte

{{commerce-only}

Die Analyse hat ergeben, dass die [!DNL Upgrade Compatibility Tool] exportiert einen Bericht mit einer Liste von Problemen für jede Datei, in dem der Schweregrad, der Fehlercode und die Fehlerbeschreibung angegeben sind.

Siehe folgendes Beispiel:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Überprüfen Sie die [Fehlermeldungsreferenz](../upgrade-compatibility-tool/error-messages.md) für weitere Informationen.

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

## JSON-Datei

Die JSON-Datei enthält genau die gleichen Informationen, die in der Ausgabe angezeigt werden:

- Liste der identifizierten Probleme.
- Zusammenfassung der Analyse.

Für jedes aufgetretene Problem enthält der Bericht detaillierte Informationen wie den Schweregrad und die Beschreibung des Problems.

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

## HTML-Bericht

Die HTML-Datei enthält auch die Analysezusammenfassung und die Liste der identifizierten Probleme. Sie können den HTML-Bericht abrufen, während Sie das Tool auf einer Befehlszeilenschnittstelle oder über die [!DNL Site-Wide Analysis Tool].

![HTML-Bericht - Zusammenfassung](../../assets/upgrade-guide/uct-html-summary.png)

Sie können einfach durch die identifizierten Probleme navigieren während der [!DNL Upgrade Compatibility Tool] Analyse:

![HTML-Bericht - Details](../../assets/upgrade-guide/uct-html-details.png)

Der HTML-Bericht enthält außerdem vier verschiedene Diagramme:

- **Schweregrad von Modulen nach Problem**: Zeigt die Schweregrad-Verteilung nach Modulen an.
- **Schweregrad der Dateien nach Problem**: Zeigt die Schweregrad-Verteilung nach Dateien an.
- **Nach Gesamtanzahl der Probleme sortierte Module**: Zeigt die 10 am stärksten kompromittierten Module unter Berücksichtigung von Warnungen, Fehlern und kritischen Fehlern an.
- **Module mit relativen Größen und Problemen**: Je mehr Dateien ein Modul enthält, desto größer ist sein Kreis. Je mehr Probleme ein Modul hat, desto roter erscheint sein Kreis.

Diese Diagramme ermöglichen es Ihnen, (auf einen Blick) die am stärksten betroffenen Teile und diejenigen zu identifizieren, die mehr Arbeit für eine Aktualisierung benötigen.

![HTML-Bericht - Diagramme](../../assets/upgrade-guide/uct-html-diagrams.png)

Sie können die im Bericht angezeigten Probleme nach der minimalen Problemstufe filtern. Der Standardwert ist `WARNING`.

Oben rechts befindet sich ein Dropdown-Menü, in dem Sie je nach Bedarf eine andere Auswahl treffen können. Die Liste der identifizierten Probleme wird entsprechend gefiltert.

![HTML-Bericht - Verwendung von Dropdown-Listen](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

Beachten Sie, dass die Probleme mit einer niedrigeren Problemstufe entfernt werden. Sie erhalten jedoch eine Benachrichtigung, damit Sie die ermittelten Probleme pro Modul immer kennen.

Die Diagramme werden ebenfalls entsprechend aktualisiert, mit Ausnahme der `Modules with relative sizes and issues`, der mit der `min-issue-level` ursprünglich eingerichtet wurde.

Wenn Sie unterschiedliche Ergebnisse anzeigen möchten, müssen Sie den Befehl erneut ausführen und einen anderen Wert für die `--min-issue-level` -Option.

![HTML-Bericht - Punktdiagramm](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

So exportieren Sie diesen Bericht in einen anderen Ausgabeordner:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: {{site.data.var.ee}} Installationsordner.
- `[=HTML-OUTPUT-PATH]`: Pfad-Verzeichnis zum Exportieren `.html` Ausgabedatei.

>[!NOTE]
>
> Der Standardpfad für den Ausgabeordner ist `var/output/[TIME]-results.html`.
