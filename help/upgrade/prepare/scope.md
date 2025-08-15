---
title: Upgrade-Umfang verstehen
description: Erfahren Sie mehr über abwärtsinkompatible Änderungen in einer Version, die sich auf benutzerdefinierte Adobe Commerce-Module oder Erweiterungen von Drittanbietern auswirken können.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 9eeb0e3a1c75b25cc70b092d23f02ebfe355d6bd
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Den Umfang der Aktualisierung verstehen

Lesen Sie [Versionshinweise](https://experienceleague.adobe.com/de/docs/commerce-operations/release/notes/overview) um den Umfang einer Version zu verstehen, einschließlich Verbesserungen, Fehlerbehebungen und bekannter Probleme, die sich auf Drittanbieter- und benutzerdefinierte Module auswirken können.

## Abwärtsinkompatible Änderungen

Adobe Commerce-Versionen können abwärtsinkompatible Änderungen enthalten. Weitere Informationen finden Sie in der Dokumentation zu abwärtsinkompatiblen Änderungen:

- **[Wichtige Änderungen](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)** - Änderungen, die erhebliche Auswirkungen haben und detaillierte Erläuterungen und spezielle Anweisungen erfordern, um sicherzustellen, dass Drittanbietermodule weiterhin funktionieren.
- **[Referenz für geringfügige Änderungen](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** - Referenzdokumentation, die aus der Code-Basis generiert wurde und geringfügige Änderungen an Klassen, API-Zugehörigkeit, Datenbank, Injektion von Abhängigkeiten, Schnittstellen, Layouts, System und XSD beschreibt.

## Erweiterungen von Drittanbietern

Die neue Kompatibilitätsrichtlinie von Adobe Commerce Marketplace stellt sicher, dass _alle_ aufgelisteten Erweiterungen innerhalb von 30 Tagen nach dem GA-Datum mit der neuesten veröffentlichten Version kompatibel sind. Aus diesem Grund ist es wichtig, Ihre Erweiterungen von Drittanbietern, wann immer möglich, über den Marketplace zu erhalten.

## Benutzerdefinierte Module

Alle benutzerdefinierten Module sollten mit der Zielversion abgeglichen werden, auf die Sie das Upgrade durchführen möchten. Dies ist der zeit- und ressourcenintensivste Prozess eines Upgrades. Bei der Bewertung Ihrer benutzerdefinierten Module müssen Sie nach abwärtsinkompatiblen Änderungen suchen und neue Praktiken beachten, wie z. B. die Zerlegung von Controllern. Weitere Informationen hierzu finden Sie in den [ zu ](https://experienceleague.adobe.com/de/docs/commerce-operations/release/notes/overview). Stellen Sie außerdem sicher, dass Sie die [Best Practices“ für ](https://developer.adobe.com/commerce/php/best-practices/extensions/) Modulentwicklung befolgen.

## [!DNL Upgrade Compatibility Tool]

Der [!DNL Upgrade Compatibility Tool] ist ein Befehlszeilen-Tool, das Ihre Instanz auf mögliche Upgrade-Probleme analysiert. Es sucht nach Problemen zwischen der aktuellen Version, die Sie installiert haben, und der Version, auf die Sie ein Upgrade durchführen möchten.

Die Verwendung dieses Tools reduziert den Aufwand, den Ihr Team betreiben muss, um den Umfang und die Auswirkungen eines Upgrades zu verstehen. Dies hilft Ihnen, gängige Code-Probleme beim Upgrade zu vermeiden, und bietet eine klare Anleitung zum Beheben identifizierter Probleme. Außerdem können Sie die wichtigsten Probleme priorisieren, die für ein erfolgreiches Upgrade erforderlich sind, sodass Sie beim Upgrade Zeit und Kosten sparen.

Erste Schritte mit der [!DNL Upgrade Compatibility Tool] finden Sie in den folgenden Abschnitten. Weitere technische Details und erweiterte Anwendungsfälle finden Sie [!DNL Upgrade Compatibility Tool] [Handbuch](../upgrade-compatibility-tool/overview.md) .

### Tool herunterladen

Verwenden Sie Composer, um das Tool herunterzuladen. Es erfordert PHP 7.3 oder höher, mindestens 2 GB RAM, Node.js (wenn Sie die GraphQL-Kompatibilität überprüfen) und eine Adobe Commerce-Lizenz.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Ausführen des Tools

So analysieren Sie Ihre Instanz und prüfen sie auf Fehler, Warnungen und kritische Probleme:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> Das `<dir>` ist der Ordner, in dem die Codebasis gespeichert wird. Die Option `-c` vergleicht Ihre Code-Basis mit der angegebenen Version.

So identifizieren Sie die wichtigsten Probleme, die Ihr Team beheben muss:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Einige weitere Optionen, die mit diesem Befehl verwendet werden können, sind:

- `--ignore-current-version-compatibility-issues` - Unterdrückt alle bekannten kritischen Probleme, Fehler und Warnungen für Ihre aktuelle Version. Es werden nur Fehler für die Version angezeigt, die Sie aktualisieren möchten.

- `--min-issue-level` - Ermöglicht es Ihnen, die Mindestproblemstufe festzulegen, um nur die wichtigsten Probleme bei Ihrem Upgrade zu priorisieren. Die Optionen sind „Warnung“, „Fehler“ und „Kritisch“ in aufsteigender Reihenfolge des Schweregrads.

- `-m | [=MODULE-PATH]` - Wenn Sie nur einen bestimmten Anbieter, ein bestimmtes Modul oder sogar ein bestimmtes Verzeichnis analysieren möchten, können Sie den Pfad ebenfalls als Option angeben.

- `--vanilla-dir` - Ermöglicht die Überprüfung des Kern-Codes auf nicht standardmäßige Implementierungen von Funktionen oder Anpassungen. Es ist wichtig, dass diese vorher bereinigt werden. Eine Vanilla-Instanz Ihrer Version wird automatisch als Referenz heruntergeladen.

  >[!NOTE]
  >
  > Dies kann auch mit dem Befehl `core:code:changes` im Tool erfolgen.

### Analysieren der Ausgabe

Der [!DNL Upgrade Compatibility Tool] exportiert eine JSON-Datei, die den betroffenen Code oder die betroffenen Module, den Schweregrad und eine Beschreibung des Problems für jedes auftretende Problem identifiziert. Es wird auch ein Zusammenfassungsbericht mit einem Komplexitätswert ausgegeben, der Ihrem Team zeigt, was für ein Upgrade auf die neueste Version erforderlich ist. Je niedriger der Komplexitätswert, desto einfacher ist das Upgrade durchzuführen.

Die folgende Ausgabe zeigt einen Beispielzusammenfassungsbericht:

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Tipps und Ratschläge

Alle vom Tool identifizierten Probleme werden im Bericht mit spezifischen Fehler-Codes aufgeführt. Verwenden Sie die [Fehlermeldungsreferenz](../upgrade-compatibility-tool/error-messages.md) um weitere Details zu den einzelnen Problemen zu erhalten. Adobe bietet außerdem Vorschläge zur Behebung jedes Problemtyps, damit Sie Ihre Korrekturschritte planen können.

Verwenden Sie den Bericht, um den Aufwand für die Aktualisierung Ihres Codes für das Upgrade zu schätzen. Basierend auf Ihren Erfahrungen können Sie den erforderlichen Aufwand für die Aktualisierung auf der Grundlage der Gesamtzahl der festgestellten Probleme und des Schweregrads der Probleme schätzen. Da es sich um ein Befehlszeilen-Tool handelt, können Sie es in automatisierte Test- und Code-Check-Suites integrieren und die JSON-Ausgabe zur Erstellung Ihrer Berichte verwenden.

Es wird empfohlen, die Ergebnisse jedes Upgrade-Projekts zu speichern, damit Sie zukünftige Upgrade-Ergebnisse mit vorherigen Ergebnissen vergleichen können. Bei fortgesetzter Verwendung können Sie bereits anhand des vom Tool bereitgestellten Zusammenfassungsberichts ein gutes Gespür für den Aufwand entwickeln, der für die Aktualisierung auf die nächste Version erforderlich ist.

Es wird außerdem empfohlen, das Tool regelmäßig auszuführen, während Sie an der Aktualisierung arbeiten, damit Sie Ihren Fortschritt einsehen können. Je mehr Probleme behoben werden, desto geringer sollte die Anzahl der Probleme sein. Dies hilft Ihrem Team auch bei der Entscheidung, wie die Arbeit am besten verteilt werden soll.

Die [!DNL Upgrade Compatibility Tool] wird weiter verbessert und zukünftige Versionen werden Funktionen wie Autokorrekturen enthalten, damit Sie Probleme so schnell wie möglich beheben können. Die neuesten Verbesserungen, die im Januar 2022 veröffentlicht wurden, umfassen PHP 8.1-Kompatibilitätstests und HTML-Visualisierungsfunktionen, mit denen Sie schnell Bereiche identifizieren können, in denen ein Upgrade möglicherweise aufwändiger ist.
