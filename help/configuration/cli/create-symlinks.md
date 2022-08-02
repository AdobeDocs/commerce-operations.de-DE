---
title: Symlinks zu LESS-Dateien erstellen
description: Erfahren Sie, wie Sie Symlinks zu LESS-Dateien erstellen.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
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
>Während der Entwicklung erstellt dieser Befehl Symlinks für LESS-Dateien in der `var/view_preprocessed` und `pub/static` Ordner. Dieser Prozess kompiliert keine LESS-Dateien in CSS-Dateien.

In der folgenden Tabelle werden die Parameter und Werte dieses Befehls erläutert.

| Parameter | Wert | Erforderlich? |
| --------- | ----- | --------- |
| `--type` | Typ der Quelldateien: [less] (Standard: &quot;less&quot;)<br>Derzeit ist LESS der einzige unterstützte Dateityp. | Nein |
| `--locale` | Gebietsschema-Code.<br>Um die Liste der Gebietsschemas anzuzeigen, geben Sie `bin/magento info:language:list` | Nein |
| `--area` | Bereich (`adminhtml` für den Verwaltungsbereich, `frontend` für die Storefront). | Nein |
| `--theme` | Designname in `<VendorName>/<theme-name>` Format. Beispiel: `Magento/blank` oder `Magento/backend`. | Nein |
| `<file>` | Eine durch Leerzeichen getrennte Liste von CSS-Dateien, die ohne die CSS-Erweiterung in LESS konvertiert werden sollen. (Der Standardwert ist `css/styles-m css/styles-l`, für den Administratortyp `css/styles css/styles-old`) | Nein |

So erstellen Sie beispielsweise LESS-Dateien für das Frontend-Design namens `VendorName/themeName` im `en_US` Gebietsschema mit einer CSS-Datei mit dem Namen `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`Geben Sie den folgenden Befehl ein:

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
