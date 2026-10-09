---
title: Layout-Dateien konvertieren
description: Erfahren Sie, wie Sie XML-Layout-Dateien mithilfe von Adobe Commerce-Befehlszeilen-Tools konvertieren können. Erfahren Sie mehr über XSLT-Stylesheet-Aktualisierungen und Dateikonvertierungsprozesse.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
