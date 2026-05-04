---
title: Layout-Dateien konvertieren
description: Erfahren Sie, wie Sie XML-Layout-Dateien mithilfe von Adobe Commerce-Befehlszeilen-Tools konvertieren können. Erfahren Sie mehr über XSLT-Stylesheet-Aktualisierungen und Dateikonvertierungsprozesse.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Konvertieren von XML-Layout-Dateien

{{file-system-owner}}

Verwenden Sie diesen Befehl, um Ihre Layout-XML-Dateien zu aktualisieren, wenn Sie die entsprechende Extensible Stylesheet Language Transformations (XSLT)-Stylesheet aktualisieren.

- [Layout-Anweisungen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [Layout-Dateitypen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

Befehlsoptionen:

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dabei gilt:

- `{xml file}` - ist der vollständige Pfad und Dateiname einer zu konvertierenden XML-Layout-Datei (erforderlich)
- `{xslt stylesheet}` - ist der vollständige Pfad und Dateiname einer für die Konvertierung zu verwendenden XSLT-Stylesheet-Datei (erforderlich)
- `-o|--overwrite` - Schließen Sie diese Option zum Überschreiben der vorhandenen XML-Datei mit ein
