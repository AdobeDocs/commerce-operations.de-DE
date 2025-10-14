---
title: Profilerstellung aktivieren
description: Erfahren Sie mehr darüber, wie Sie den MAGE Profiler für Ihre Analyse-Tools aktivieren.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Profilerstellung aktivieren

Mit der Commerce-Profilerstellung können Sie:

- Aktivieren Sie einen integrierten Profiler.

  Sie können einen integrierten Profiler mit Commerce verwenden, um Aufgaben wie die Leistungsanalyse durchzuführen. Die Art der Profilerstellung hängt von den verwendeten Analysetools ab. Wir unterstützen verschiedene Formate, einschließlich HTML. Wenn Sie den Profiler aktivieren, wird eine `var/profiler.flag` generiert, die angibt, dass der Profiler aktiviert ist und Konfigurationen vorgenommen wurden. Wenn deaktiviert, wird diese Datei gelöscht.

- Anzeigen von Abhängigkeitsdiagrammen auf einer Commerce-Seite.

  Ein _Abhängigkeitsdiagramm_ ist eine Liste der Objektabhängigkeiten und all ihrer Abhängigkeiten sowie aller Abhängigkeiten für diese Abhängigkeiten usw.

  Sie sollten besonders an der Liste der _nicht verwendeten Abhängigkeiten_ interessiert sein. Dabei handelt es sich um Objekte, die erstellt wurden, weil sie in einem Konstruktor angefordert, aber nie verwendet wurden (d. h. keine ihrer Methoden wurde aufgerufen). Daher werden Prozessorzeit und Arbeitsspeicher, die für die Erstellung dieser Abhängigkeiten aufgewendet werden, verschwendet.

Commerce stellt die Basisfunktionen in [`Magento\Framework\Profiler`][profiler] bereit.

Sie können den Profiler mithilfe einer MAGE_PROFILER-Variablen oder der Befehlszeile aktivieren und konfigurieren.

## MAGE_PROFILER festlegen

Sie können den Wert von `MAGE_PROFILER` auf eine der unter „Festlegen des [&#x200B; von Bootstrap-Parametern“ beschriebenen Arten &#x200B;](../bootstrap/set-parameters.md).

`MAGE_PROFILER` unterstützt die folgenden Werte:

- `1` zur Aktivierung der Ausgabe eines bestimmten Profilers.

  Sie können einen der folgenden Werte verwenden, um einen bestimmten Profiler zu aktivieren:

   - `csvfile`, das [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile] verwendet
   - Alle anderen Werte (außer `2`), einschließlich eines leeren Werts, für den [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html] verwendet wird

- `2` zum Aktivieren von Abhängigkeitsdiagrammen.

  Abhängigkeitsdiagramme werden normalerweise am unteren Rand einer Seite angezeigt. Die folgende Abbildung zeigt einen Teil der Ausgabe:

  ![Abhängigkeitsdiagramme](../../assets/configuration/depend-graphs.png)

## CLI-Befehle

Sie können den Profiler mithilfe von CLI-Befehlen aktivieren oder deaktivieren:

- `dev:profiler:enable <type>` aktiviert den Profiler mit `type` von `html` (Standard) oder `csvfile`. Wenn diese Option aktiviert ist, wird ein `var/profiler.flag` erstellt.
- `dev:profiler:disable` deaktiviert den Profiler. Wenn diese Option deaktiviert ist, wird die `var/profiler.flag` entfernt.

Verwenden Sie die Variablenoption, um Abhängigkeitsdiagramme zu aktivieren.

**Aktivieren oder Deaktivieren des Profilers**:

1. Melden Sie sich beim Commerce-Server an.
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Aktivieren Sie als Verantwortlicher für das Dateisystem den Profiler:

   So aktivieren Sie den Profiler mit dem Typ `html` und erstellen eine Flagdatei:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   So aktivieren Sie den Profiler mit dem Typ `csvfile` und erstellen eine Flagdatei:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   Die Ausgabe wird in `<project-root>/var/log/profiler.csv` gespeichert. Die `profiler.csv` wird bei jeder Seitenaktualisierung überschrieben.

   So deaktivieren Sie den Profiler und entfernen die Flagdatei:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
