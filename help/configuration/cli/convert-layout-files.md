---
title: Layout-Dateien konvertieren
description: Konvertieren von XML-Layout-Dateien.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Konvertieren von XML-Layout-Dateien

{{file-system-owner}}

Verwenden Sie diesen Befehl, um Ihre Layout-XML-Dateien zu aktualisieren, wenn Sie die entsprechende Extensible Stylesheet Language Transformations (XSLT)-Stylesheet aktualisieren.

- [Layoutanweisungen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Layout-Dateitypen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Befehlsoptionen:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dabei gilt:

- `{xml file}` - ist der vollständige Pfad und Dateiname einer zu konvertierenden XML-Layout-Datei (erforderlich)
- `{xslt stylesheet}` - ist der vollständige Pfad und Dateiname einer für die Konvertierung zu verwendenden XSLT-Stylesheet-Datei (erforderlich)
- `-o|--overwrite` - Schließen Sie diese Option zum Überschreiben der vorhandenen XML-Datei mit ein
