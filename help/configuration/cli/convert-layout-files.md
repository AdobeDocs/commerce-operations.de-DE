---
title: Layout-Dateien konvertieren
description: Konvertieren Sie XML-Layoutdateien.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# XML-Layoutdateien konvertieren

{{file-system-owner}}

Verwenden Sie diesen Befehl, um Ihre XML-Dateien zu aktualisieren, wenn Sie das entsprechende XSLT-Stylesheet (Extensible Stylesheet Language Transformations) aktualisieren.

- [Layout-Anweisungen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Layout-Dateitypen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Befehlsoptionen:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dabei gilt:

- `{xml file}`—ist der vollständige Pfad und Dateiname einer XML-Datei für das Layout, die konvertiert werden soll (erforderlich)
- `{xslt stylesheet}`—ist der vollständige Pfad und Dateiname einer XSLT-Stylesheet-Datei, die für die Konvertierung verwendet werden soll (erforderlich)
- `-o|--overwrite`—include this option to overwrite the existing XML file
