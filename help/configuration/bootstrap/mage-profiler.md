---
title: Profiling aktivieren
description: Erfahren Sie mehr darüber, wie Sie mit Ihren Analysetools den MAGE Profiler verwenden können.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Profiling aktivieren

Mit Commerce-Profiling können Sie:

- Aktivieren Sie einen integrierten Profiler.

   Sie können einen integrierten Profiler mit Commerce verwenden, um Aufgaben wie die Leistungsanalyse durchzuführen. Die Art der Profilerstellung hängt von den von Ihnen verwendeten Analysetools ab. Wir unterstützen mehrere Formate, einschließlich HTML. Wenn Sie den Profiler aktivieren, wird eine `var/profiler.flag` -Datei generiert, die angibt, dass der Profiler aktiviert ist, und Konfigurationen. Wenn diese Option deaktiviert ist, wird diese Datei gelöscht.

- Anzeigen von Abhängigkeitsdiagrammen auf einer Commerce-Seite.

   A _Abhängigkeitsdiagramm_ ist eine Liste von Objektabhängigkeiten und all ihren Abhängigkeiten, allen Abhängigkeiten für diese Abhängigkeiten usw.

   Die Liste der _nicht verwendete Abhängigkeiten_: Objekte, die erstellt wurden, weil sie in einem Konstruktor angefordert wurden, aber nie verwendet wurden (d. h. keine ihrer Methoden aufgerufen wurde). Dadurch werden Prozessorzeit und Arbeitsspeicher verschwendet, die für die Erstellung dieser Abhängigkeiten erforderlich sind.

Commerce bietet die Basisfunktionalität in [`Magento\Framework\Profiler`][profiler].

Sie können den Profiler mit einer MAGE_PROFILER -Variablen oder der Befehlszeile aktivieren und konfigurieren.

## MAGE_PROFILER festlegen

Sie können den Wert von `MAGE_PROFILER` in einer der in [Wert der Bootstrap-Parameter festlegen](../bootstrap/set-parameters.md).

`MAGE_PROFILER` unterstützt die folgenden Werte:

- `1` , um die Ausgabe eines bestimmten Profilers zu aktivieren.

   Sie können einen der folgenden Werte verwenden, um einen bestimmten Profiler zu aktivieren:

   - `csvfile` , die [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Beliebiger anderer Wert (außer `2`), einschließlich eines leeren Werts, der [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` um Abhängigkeitsdiagramme zu aktivieren.

   Abhängigkeitsdiagramme werden normalerweise unten auf einer Seite angezeigt. Die folgende Abbildung zeigt einen Teil der Ausgabe:

   ![Abhängigkeitsdiagramme](../../assets/configuration/depend-graphs.png)

## CLI-Befehle

Sie können den Profiler mithilfe der CLI-Befehle aktivieren oder deaktivieren:

- `dev:profiler:enable <type>` aktiviert den Profiler mit `type` von `html` (Standard) oder `csvfile`. Wenn diese Option aktiviert ist, wird eine Flagfile `var/profiler.flag` erstellt.
- `dev:profiler:disable` Deaktiviert den Profiler. Wenn diese Option deaktiviert ist, wird die Flags-Datei `var/profiler.flag` entfernt.

Verwenden Sie die Variablenoption, um Abhängigkeitsdiagramme zu aktivieren.

**So aktivieren oder deaktivieren Sie den Profiler**:

1. Melden Sie sich bei Ihrem Commerce-Server an.
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Als Eigentümer des Dateisystems aktivieren Sie den Profiler:

   So aktivieren Sie den Profiler mit dem Typ `html` und erstellen Sie eine Flagfile:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   So aktivieren Sie den Profiler mit dem Typ `csvfile` und erstellen Sie eine Flagfile:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   Die Ausgabe wird in `<project-root>/var/log/profiler.csv`. Die `profiler.csv` wird bei jeder Seitenaktualisierung überschrieben.

   So deaktivieren Sie den Profiler und entfernen die Flagfile:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
