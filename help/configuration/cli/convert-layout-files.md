---
title: Layout-Dateien konvertieren
description: Konvertieren Sie XML-Layoutdateien.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# XML-Layoutdateien konvertieren

{{file-system-owner}}

Verwenden Sie diesen Befehl, um Ihre XML-Dateien zu aktualisieren, wenn Sie das entsprechende XSLT-Stylesheet (Extensible Stylesheet Language Transformations) aktualisieren.

- [Layout-Anweisungen](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Layout-Dateitypen](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Befehlsoptionen:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dabei gilt:

- `{xml file}`—ist der vollständige Pfad und Dateiname einer XML-Datei für das Layout, die konvertiert werden soll (erforderlich)
- `{xslt stylesheet}`—ist der vollständige Pfad und Dateiname einer XSLT-Stylesheet-Datei, die für die Konvertierung verwendet werden soll (erforderlich)
- `-o|--overwrite`—include this option to overwrite the existing XML file
