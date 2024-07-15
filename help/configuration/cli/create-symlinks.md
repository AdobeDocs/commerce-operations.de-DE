---
title: Symlinks zu LESS-Dateien erstellen
description: Erfahren Sie, wie Sie Symlinks zu LESS-Dateien erstellen.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Symlinks zu LESS-Dateien erstellen

{{file-system-owner}}

So erstellen Sie Symlinks zu LESS-Dateien:

Befehlsoptionen:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Während der Entwicklung erstellt dieser Befehl Symlinks für LESS-Dateien in den Ordnern `var/view_preprocessed` und `pub/static`. Dieser Prozess kompiliert keine LESS-Dateien in CSS-Dateien.

In der folgenden Tabelle werden die Parameter und Werte dieses Befehls erläutert.

| Parameter | Wert | Erforderlich? |
| --------- | ----- | --------- |
| `--type` | Typ der Quelldateien: [less] (Standard: &quot;less&quot;)<br>Derzeit ist LESS der einzige unterstützte Dateityp. | Nein |
| `--locale` | Gebietsschema-Code.<br>Geben Sie `bin/magento info:language:list` ein, um die Liste der Gebietsschemas anzuzeigen. | Nein |
| `--area` | Bereich (`adminhtml` für den Verwaltungsbereich, `frontend` für die Storefront). | Nein |
| `--theme` | Designname im Format `<VendorName>/<theme-name>` . Beispiel: `Magento/blank` oder `Magento/backend`. | Nein |
| `<file>` | Eine durch Leerzeichen getrennte Liste von CSS-Dateien, die ohne die CSS-Erweiterung in LESS konvertiert werden sollen. (Der Standardwert ist `css/styles-m css/styles-l`, für den Administratortyp `css/styles css/styles-old`) | Nein |

Um beispielsweise mithilfe einer CSS-Datei mit dem Namen `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css` LESS-Dateien für das Frontend-Design mit dem Namen `VendorName/themeName` im Gebietsschema `en_US` zu erstellen, geben Sie den folgenden Befehl ein:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Die folgenden Meldungen werden angezeigt, um den Erfolg zu bestätigen:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

So erstellen Sie LESS-Dateien für den Administrator:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
