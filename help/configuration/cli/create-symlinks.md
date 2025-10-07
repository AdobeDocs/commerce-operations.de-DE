---
title: Erstellen von Symlinks zu LESS-Dateien
description: Erfahren Sie, wie Sie für die Adobe Commerce-Entwicklung Symlinks zu LESS-Dateien erstellen. Entdecken Sie die Verknüpfung von Stylesheets und die Optimierung von Entwicklungs-Workflows.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Erstellen von Symlinks zu LESS-Dateien

{{file-system-owner}}

So erstellen Sie Symlinks zu LESS-Dateien:

Befehlsoptionen:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Während der Entwicklung erstellt dieser Befehl Symlinks für LESS-Dateien in den Ordnern `var/view_preprocessed` und `pub/static`. Dieser Prozess kompiliert LESS-Dateien nicht in CSS-Dateien.

In der folgenden Tabelle werden die Parameter und Werte dieses Befehls erläutert.

| Parameter | Wert | Erforderlich? |
| --------- | ----- | --------- |
| `--type` | Typ der Quelldateien: [less] (Standard: „less„)<br>Derzeit ist LESS der einzige unterstützte Dateityp. | Nein |
| `--locale` | Gebietsschema-Code.<br>Um die Liste der Gebietsschema-Codes anzuzeigen, geben Sie `bin/magento info:language:list` ein | Nein |
| `--area` | Fläche (`adminhtml` für den administrativen Bereich, `frontend` für die Storefront). | Nein |
| `--theme` | Name des Designs im `<VendorName>/<theme-name>`. Beispiel: `Magento/blank` oder `Magento/backend`. | Nein |
| `<file>` | Eine durch Leerzeichen getrennte Liste von CSS-Dateien, die ohne CSS-Erweiterung in LESS konvertiert werden sollen. (Die Standardeinstellung ist `css/styles-m css/styles-l`, für den adminhtml-Typ `css/styles css/styles-old`) | Nein |

Um beispielsweise LESS-Dateien für das Frontend-Design mit dem Namen `VendorName/themeName` im `en_US` Gebietsschema mithilfe einer CSS-Datei mit dem Namen `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css` zu erstellen, geben Sie den folgenden Befehl ein:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Die folgenden Meldungen werden angezeigt, um den Erfolg zu bestätigen:

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

So erstellen Sie LESS-Dateien für das Admin-HTML:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
