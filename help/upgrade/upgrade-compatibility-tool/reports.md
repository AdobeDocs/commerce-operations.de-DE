---
title: '[!DNL Upgrade Compatibility Tool] reports'
description: Führen Sie diese Schritte aus, um den  [!DNL Upgrade Compatibility Tool] für Ihr Adobe Commerce-Projekt auszuführen.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Berichte

{{commerce-only}}

Als Ergebnis der Analyse kann der [!DNL Upgrade Compatibility Tool] einen Bericht exportieren, der eine Liste von Problemen für jede Datei enthält und deren Schweregrad, Fehlercode und Fehlerbeschreibung angibt. Der [!DNL Upgrade Compatibility Tool] exportiert den Bericht in zwei verschiedene Formate:

- Eine [JSON-Datei](reports.md#json-file).
- Ein [HTML-Bericht](reports.md#html-report).

Siehe folgendes Beispiel für die Befehlszeilenschnittstelle eines Berichts:

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Weitere Informationen zu den verschiedenen Fehlern, die dieser Bericht erzeugen kann, finden Sie im Thema [Fehlermeldungsreferenz](../upgrade-compatibility-tool/error-messages.md) .

Dieser Bericht enthält auch eine detaillierte Zusammenfassung, die Folgendes zeigt:

- *Aktuelle Version*: die derzeit installierte Version.
- *Target-Version*: die Version, auf die Sie aktualisieren möchten.
- *Ausführungszeit*: Die Zeit, die die Analyse für die Erstellung des Berichts benötigt hat (mm:ss).
- *Module, die eine Aktualisierung erfordern*: der Prozentsatz der Module, die Kompatibilitätsprobleme enthalten und aktualisiert werden müssen.
- *Dateien, die aktualisiert werden müssen*: der Prozentsatz der Dateien, die Kompatibilitätsprobleme enthalten und aktualisiert werden müssen.
- *Gesamtzahl kritischer Fehler*: die Anzahl der gefundenen kritischen Fehler.
- *Fehler insgesamt*: die Anzahl der gefundenen Fehler.
- *Gesamte Warnungen*: die Anzahl der gefundenen Warnungen.
- *Speicherspitzenauslastung*: Die maximale Speicherkapazität, die [!DNL Upgrade Compatibility Tool] während der Ausführung erreicht hat.

Siehe folgendes Beispiel für die Befehlszeilenschnittstelle:

```
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## JSON-Datei

Sie können die JSON-Dateiausgabe abrufen, während Sie [!DNL Upgrade Compatibility Tool] auf einer Befehlszeilenschnittstelle ausführen. Die Datei `JSON` enthält genau dieselben Informationen, die auf der Ausgabe [!DNL Upgrade Compatibility Tool] angezeigt werden:

- Eine Liste der festgestellten Probleme.
- Eine Zusammenfassung der Analyse.

Für jedes aufgetretene Problem enthält der Bericht detaillierte Informationen wie den Schweregrad und die Beschreibung des Problems.

So exportieren Sie diese `JSON` -Datei in einen anderen Ausgabeordner:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Pfad-Verzeichnis zum Exportieren der `JSON` Ausgabedatei.

>[!NOTE]
>
> Der Standardpfad für den Ausgabeordner ist `var/output/[TIME]-results.json`.

## HTML-Bericht

Sie können den HTML-Bericht abrufen, während Sie das Tool auf einer Befehlszeilenschnittstelle oder über die [!DNL Site-Wide Analysis Tool] ausführen. Der HTML-Bericht enthält außerdem:

- Eine Liste der festgestellten Probleme.
- Eine Zusammenfassung der Analyse.

![HTML-Bericht - Zusammenfassung](../../assets/upgrade-guide/uct-html-summary.png)

Sie können während der [!DNL Upgrade Compatibility Tool]-Analyse einfach durch die identifizierten Probleme navigieren.

Sie können die im Bericht angezeigten Probleme nach der minimalen Problemstufe filtern (der Standardwert ist `WARNING`).

Oben rechts befindet sich ein Dropdown-Menü, in dem Sie eine andere Ebene auswählen können. Die Liste der identifizierten Probleme wird entsprechend gefiltert.

![HTML-Bericht - Verwendung von Dropdown-Listen](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Die Probleme mit einer niedrigeren Problemstufe werden entfernt, Sie erhalten jedoch eine Benachrichtigung, damit Sie die identifizierten Probleme pro Modul immer kennen.

Der HTML-Bericht enthält außerdem vier verschiedene Diagramme:

- **Module nach Schweregrad des Problems**: Zeigt die Schweregrad-Verteilung nach Modulen an.
- **Dateien nach Schweregrad des Problems**: Zeigt die Schweregrad-Verteilung nach Dateien an.
- **Nach Gesamtanzahl der Probleme sortierte Module**: Zeigt die 10 am stärksten gefährdeten Module unter Berücksichtigung von Warnungen, Fehlern und kritischen Fehlern an.
- **Module mit relativen Größen und Problemen**: Je mehr Dateien ein Modul enthält, desto größer ist sein Kreis. Je mehr Probleme ein Modul hat, desto roter erscheint sein Kreis.

In diesen Diagrammen können Sie ermitteln, welche Module am stärksten gefährdet sind und welche die Durchführung eines Upgrades erfordern.

Bericht ![HTML - Diagramme](../../assets/upgrade-guide/uct-html-diagrams.png)

Die HTML-Berichtsdiagramme werden ebenfalls entsprechend aktualisiert, mit Ausnahme der `Modules with relative sizes and issues`, die mit dem ursprünglich eingerichteten `min-issue-level` generiert wird.

Wenn Sie für das Diagramm `Modules with relative sizes and issues` unterschiedliche Ergebnisse anzeigen möchten, müssen Sie den Befehl erneut ausführen und einen anderen Wert für die Option `--min-issue-level` angeben.

![HTML-Bericht - Punktdiagramm](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

So exportieren Sie diesen HTML-Bericht in einen anderen Ausgabeordner:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=HTML-OUTPUT-PATH]`: Pfad-Verzeichnis zum Exportieren der `.html` Ausgabedatei.

>[!NOTE]
>
> Der Standardpfad für den Ausgabeordner ist `var/output/[TIME]-results.html`.
