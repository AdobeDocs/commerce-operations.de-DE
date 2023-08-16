---
title: URN-Highlighter
description: Erfahren Sie, wie Sie die URN-Hervorhebung in Ihrer IDE einrichten.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Überblick über URN Highlighter

{{file-system-owner}}

Commerce-Code verweist auf alle XSD-Schemas [Uniform Resource Names (URNs)](https://www.ietf.org/rfc/rfc2141.txt). Wenn Sie Code entwickeln und auf XSDs verweisen müssen, konfiguriert dieser Befehl Ihre integrierte Entwicklungsumgebung (IDE), um URNs zu erkennen und hervorzuheben. Dies erleichtert die Entwicklung.

Standardmäßig ist eine IDE wie PhpStorm nicht so konfiguriert, dass sie URNs erkennt und daher wie folgt in rotem Text angezeigt wird:

![PhpStorm ist nicht zur Erkennung von URN konfiguriert](../../assets/configuration/urn-before.png)

Die `bin/magento dev:urn-catalog:generate` -Befehl aktiviert Ihre IDE (derzeit nur PhpStorm und Visual Studio Code), um URNs wie folgt zu erkennen und hervorzuheben:

![IDE aktivieren, um URN zu erkennen](../../assets/configuration/urn-after.png)

Dieser Befehl erstellt insbesondere die folgende PhpStorm-Konfiguration:

![Beispiel für eine PhpStorm-Konfiguration](../../assets/configuration/urn-settings.png)

## IDE konfigurieren

Derzeit werden nur PhpStorm und Visual Studio Code unterstützt.

Befehlssyntax:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Wo `<path>` ist der Pfad zu Ihrem PHPStorm `misc.xml` -Datei, die sich relativ zum Projektstamm befindet. In der Regel `<path>` is `.idea/misc.xml`.

>[!INFO]
>
>Um Ihre &quot;Schemas und DTDs&quot;auf dem neuesten Stand zu halten, führen Sie die `dev:urn-catalog:generate` jedes Mal, wenn Sie Commerce 2-Module, die `*.xsd` -Dateien.
