---
title: URN-Highlighter
description: Erfahren Sie, wie Sie URN-Hervorhebung in Ihrer IDE einrichten.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Überblick über URN-Highlighter

{{file-system-owner}}

Commerce-Code verweist auf alle XSD[Schemata (Uniform Resource Names (URNs)](https://www.ietf.org/rfc/rfc2141.txt). Wenn Sie Code entwickeln und auf XSDs verweisen müssen, konfiguriert dieser Befehl Ihre integrierte Entwicklungsumgebung (IDE), um URNs zu erkennen und hervorzuheben. Dies erleichtert die Entwicklung.

Standardmäßig ist eine IDE wie PhpStorm nicht so konfiguriert, dass sie URNs erkennt. Daher werden sie wie folgt in rotem Text angezeigt:

![PhpStorm ist nicht so konfiguriert, dass URN erkannt wird](../../assets/configuration/urn-before.png)

Mit dem Befehl `bin/magento dev:urn-catalog:generate` kann Ihre IDE (derzeit nur PhpStorm und Visual Studio Code) URNs wie die folgenden erkennen und hervorheben:

![IDE aktivieren, um URN zu erkennen](../../assets/configuration/urn-after.png)

Insbesondere erstellt dieser Befehl die folgende PhpStorm-Konfiguration:

![Beispiel für eine PhpStorm-Konfiguration](../../assets/configuration/urn-settings.png)

## Konfigurieren der IDE

Derzeit werden nur PhpStorm und Visual Studio Code unterstützt.

Befehlssyntax:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Dabei `<path>` der Pfad zur `misc.xml`-Datei Ihres PhpStorm, die relativ zu Ihrem Projektstamm gespeichert ist. Normalerweise ist `<path>` `.idea/misc.xml`.

>[!INFO]
>
>Um Ihre „Schemata und DTDs“ auf dem neuesten Stand zu halten, führen Sie den `dev:urn-catalog:generate` Befehl jedes Mal aus, wenn Sie Commerce 2-Module mit `*.xsd`-Dateien hinzufügen, ändern oder entfernen.
