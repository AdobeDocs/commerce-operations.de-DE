---
title: Aktivieren der Profilerstellung
description: Erfahren Sie mehr darüber, wie Sie mit Ihren Analysetools den MAGE Profiler verwenden können.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Aktivieren der Profilerstellung

Mit Commerce Profiling können Sie:

- Aktivieren Sie einen integrierten Profiler.

  Sie können einen integrierten Profiler mit Commerce verwenden, um Aufgaben wie die Leistungsanalyse durchzuführen. Die Art der Profilerstellung hängt von den von Ihnen verwendeten Analysetools ab. Wir unterstützen mehrere Formate, einschließlich HTML. Wenn Sie den Profiler aktivieren, wird eine `var/profiler.flag` -Datei generiert, die angibt, dass der Profiler aktiviert ist und Konfigurationen vorgenommen wurden. Wenn diese Option deaktiviert ist, wird diese Datei gelöscht.

- Zeigen Sie Abhängigkeitsdiagramme auf einer Commerce-Seite an.

  Ein _Abhängigkeitsdiagramm_ ist eine Liste von Objektabhängigkeiten und all ihren Abhängigkeiten, allen Abhängigkeiten für diese Abhängigkeiten usw.

  Sie sollten besonders an der Liste der nicht verwendeten Abhängigkeiten von _1} interessiert sein, bei denen es sich um Objekte handelt, die erstellt wurden, weil sie in einem Konstruktor angefordert wurden, aber nie verwendet wurden (d. h. keine ihrer Methoden aufgerufen wurde)._ Dadurch werden Prozessorzeit und Arbeitsspeicher verschwendet, die für die Erstellung dieser Abhängigkeiten erforderlich sind.

Commerce bietet die Basisfunktionalität in [`Magento\Framework\Profiler`][profiler].

Sie können den Profiler mit einer MAGE_PROFILER -Variablen oder der Befehlszeile aktivieren und konfigurieren.

## MAGE_PROFILER festlegen

Sie können den Wert von `MAGE_PROFILER` auf eine der unter [Wert der Bootstrap-Parameter festlegen](../bootstrap/set-parameters.md) beschriebenen Arten festlegen.

`MAGE_PROFILER` unterstützt die folgenden Werte:

- `1` , um die Ausgabe eines bestimmten Profilers zu aktivieren.

  Sie können einen der folgenden Werte verwenden, um einen bestimmten Profiler zu aktivieren:

   - `csvfile` , der [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile] verwendet
   - Jeder andere Wert (außer `2`), einschließlich eines leeren Werts, der [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html] verwendet

- `2` , um Abhängigkeitsdiagramme zu aktivieren.

  Abhängigkeitsdiagramme werden normalerweise unten auf einer Seite angezeigt. Die folgende Abbildung zeigt einen Teil der Ausgabe:

  ![Abhängigkeitsdiagramme](../../assets/configuration/depend-graphs.png)

## CLI-Befehle

Sie können den Profiler mithilfe der CLI-Befehle aktivieren oder deaktivieren:

- `dev:profiler:enable <type>` aktiviert den Profiler mit `type` von `html` (Standard) oder `csvfile`. Wenn diese Option aktiviert ist, wird eine Flagfile `var/profiler.flag` erstellt.
- `dev:profiler:disable` deaktiviert den Profiler. Wenn diese Option deaktiviert ist, wird die Flagfile `var/profiler.flag` entfernt.

Verwenden Sie die Variablenoption, um Abhängigkeitsdiagramme zu aktivieren.

**So aktivieren oder deaktivieren Sie den Profiler**:

1. Melden Sie sich bei Ihrem Commerce-Server an.
1. Wechseln Sie zum Installationsverzeichnis von Commerce.
1. Als Eigentümer des Dateisystems aktivieren Sie den Profiler:

   So aktivieren Sie den Profiler mit dem Typ `html` und erstellen eine Flagfile:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   So aktivieren Sie den Profiler mit dem Typ `csvfile` und erstellen eine Flagfile:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   Die Ausgabe wird in `<project-root>/var/log/profiler.csv` gespeichert. Der `profiler.csv` wird bei jeder Seitenaktualisierung überschrieben.

   So deaktivieren Sie den Profiler und entfernen die Flagfile:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
