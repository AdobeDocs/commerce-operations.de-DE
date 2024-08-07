---
title: Aktualisierungsumfang verstehen
description: Erfahren Sie mehr über abwärtskompatible Änderungen in einer Version, die sich auf benutzerdefinierte Adobe Commerce-Module oder Drittanbieter-Erweiterungen auswirken können.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# den Umfang der Aktualisierung verstehen

Lesen Sie die [Versionshinweise](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) , um den Umfang einer Version zu verstehen, einschließlich Verbesserungen, Fehlerbehebungen und bekannten Problemen, die sich auf Drittanbieter- und benutzerdefinierte Module auswirken könnten.

## Abwärtskompatible Änderungen

Adobe Commerce-Versionen können abwärtskompatible Änderungen enthalten. Lesen Sie unsere Dokumentation zu rückwärtsinkompatiblen Änderungen. Weitere Informationen finden Sie unter:

- **[Wichtige Änderungen - Highlights](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** - Änderungen, die erhebliche Auswirkungen haben und detaillierte Erläuterungen und spezielle Anweisungen erfordern, um sicherzustellen, dass Module von Drittanbietern weiterhin funktionieren.
- **[Geringfügige Änderungsreferenz](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** - Referenzdokumentation, die von der Codebasis generiert wurde und geringfügige Änderungen an Klassen, API-Mitgliedschaft, Datenbank, Abhängigkeitseinfügung, Schnittstellen, Layouts, System und XSD beschreibt.

## Drittanbietererweiterungen

Die neue Kompatibilitätsrichtlinie von Adobe Commerce Marketplace stellt sicher, dass _alle_ aufgelisteten Erweiterungen innerhalb von 30 Tagen nach dem GA-Datum mit der neuesten veröffentlichten Version kompatibel sind. Aus diesem Grund ist es wichtig, dass Sie Ihre Drittanbietererweiterungen, wann immer möglich, über den Marketplace abrufen.

## Benutzerdefinierte Module

Alle benutzerdefinierten Module sollten mit der Zielversion verglichen werden, auf die Sie ein Upgrade durchführen möchten. Dies ist der zeitintensivste und ressourcenintensivste Aktualisierungsprozess. Bei der Bewertung Ihrer benutzerdefinierten Module müssen Sie nach abwärtskompatiblen Änderungen suchen und sich über neue Vorgehensweisen, wie z. B. die Aufhebung der Controller-Zusammensetzung, informieren. Weitere Informationen hierzu finden Sie in den [Versionshinweisen](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Stellen Sie außerdem sicher, dass Sie die [Best Practices](https://developer.adobe.com/commerce/php/best-practices/extensions/) für die Modulentwicklung befolgen.

## [!DNL Upgrade Compatibility Tool]

Der [!DNL Upgrade Compatibility Tool] ist ein Befehlszeilen-Tool, das Ihre Instanz auf potenzielle Aktualisierungsprobleme hin analysiert. Es sucht nach Problemen zwischen der aktuellen Version, die Sie installiert haben, und der Version, auf die Sie ein Upgrade durchführen möchten.

Die Verwendung dieses Tools reduziert den Aufwand Ihres Teams, den Umfang und die Auswirkungen eines Upgrades zu verstehen. Dies hilft Ihnen, gängige Code-Probleme beim Aktualisieren zu vermeiden, und gibt eine klare Anleitung dazu, wie identifizierte Probleme gelöst werden. Darüber hinaus hilft es, die wichtigsten Probleme zu priorisieren, die für eine erfolgreiche Aktualisierung erforderlich sind. So sparen Sie Zeit und Kosten bei der Aktualisierung.

In den folgenden Abschnitten erhalten Sie Informationen zu den ersten Schritten mit dem [!DNL Upgrade Compatibility Tool]. Weitere technische Details und erweiterte Anwendungsfälle finden Sie im [!DNL Upgrade Compatibility Tool] [Handbuch](../upgrade-compatibility-tool/overview.md) .

### Tool herunterladen

Verwenden Sie Composer , um das Tool herunterzuladen. Es erfordert PHP 7.3 oder höher, mindestens 2 GB RAM, Node.js (wenn Sie die GraphQL-Kompatibilität überprüfen) und eine Adobe Commerce-Lizenz.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Tool ausführen

So analysieren Sie Ihre Instanz und suchen nach Fehlern, Warnungen und kritischen Problemen:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> Das `<dir>` -Argument ist der Ordner, in dem Ihre Codebasis gespeichert ist. Die Option `-c` vergleicht Ihre Codebasis mit der angegebenen Version.

So identifizieren Sie die wichtigsten Probleme, die Ihr Team lösen sollte:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Einige weitere Optionen, die mit diesem Befehl verwendet werden können:

- `--ignore-current-version-compatibility-issues` - Unterdrückt alle bekannten kritischen Probleme, Fehler und Warnungen gegenüber Ihrer aktuellen Version. Es werden nur Fehler gegenüber der Version bereitgestellt, die Sie aktualisieren möchten.

- `--min-issue-level` - Ermöglicht die Festlegung des minimalen Problemniveaus, damit nur die wichtigsten Probleme bei der Aktualisierung priorisiert werden. Die Optionen sind Warnung, Fehler und kritisch in aufsteigender Reihenfolge der Schwere.

- `-m | [=MODULE-PATH]` - Wenn Sie nur ein bestimmtes Anbieter, Modul oder Verzeichnis analysieren möchten, können Sie auch den Pfad als Option angeben.

- `--vanilla-dir` - Ermöglicht es Ihnen, den Kerncode auf eine nicht standardmäßige Implementierung von Funktionen oder Anpassungen zu überprüfen. Es ist wichtig, dass diese im Vorfeld bereinigt werden. Eine Vanilla-Instanz Ihrer Version wird automatisch zur Referenz heruntergeladen.

  >[!NOTE]
  >
  > Dies kann auch mit dem Befehl `core:code:changes` im Tool durchgeführt werden.

### Analyse der Ausgabe

Der [!DNL Upgrade Compatibility Tool] exportiert eine JSON-Datei, die den betroffenen Code oder die betroffenen Module, den Schweregrad und eine Beschreibung des Problems für jedes auftretende Problem enthält. Außerdem wird ein Zusammenfassungsbericht mit einem Komplexitätswert ausgegeben, der es Ihrem Team ermöglicht, ungefähr zu verstehen, was für die Aktualisierung auf die neueste Version erforderlich ist. Je niedriger der Komplexitätswert ist, desto einfacher ist es, das Upgrade durchzuführen.

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

### Tipps und Hinweise

Alle Probleme, die das identifizierte Tool hat, werden im Bericht mit spezifischen Fehlercodes aufgeführt. Verwenden Sie die [Fehlermeldungsreferenz](../upgrade-compatibility-tool/error-messages.md) , um weitere Details zu den einzelnen Problemen zu erhalten. Adobe bietet außerdem Vorschläge zur Behebung jedes Problems, damit Sie Ihre Behebungsschritte planen können.

Verwenden Sie den Bericht, um den Aufwand für die Aktualisierung Ihres Codes für die Aktualisierung zu schätzen. Basierend auf Ihren Erfahrungen können Sie den erforderlichen Aktualisierungsaufwand anhand der Gesamtzahl der festgestellten Probleme und der Schwere der Probleme schätzen. Da es sich um ein Befehlszeilen-Tool handelt, können Sie dieses in automatisierte Test- und Code-Check-Suites einbinden und die JSON-Ausgabe verwenden, um Ihre Berichte zu generieren.

Es wird empfohlen, die Ergebnisse jedes Aktualisierungsprojekts zu speichern, damit Sie zukünftige Upgrade-Ergebnisse mit früheren Ergebnissen vergleichen können. Wenn Sie dieses Tool weiterhin verwenden, entwickeln Sie ein gutes Gefühl dafür, wie aufwändig es ist, ein Upgrade auf die nächste Version durchzuführen, und zwar nur ausgehend vom Zusammenfassungsbericht, der vom Tool bereitgestellt wird.

Wir empfehlen Ihnen außerdem, das Tool regelmäßig während der Arbeit an der Aktualisierung auszuführen, um einen Überblick über Ihren Fortschritt zu erhalten. Die Anzahl der Probleme sollte mit der Korrektur verringert werden. Dies hilft Ihrem Team auch bei der Entscheidung über den besten Ansatz zur Verteilung der Arbeit.

Die [!DNL Upgrade Compatibility Tool] -Version wird weiterhin verbessert und künftige Versionen enthalten Funktionen wie Autofixes, mit denen Sie Probleme so schnell wie möglich beheben können. Die im Januar 2022 veröffentlichten neuesten Verbesserungen umfassen Kompatibilitätstests für PHP 8.1 und HTML-Visualisierungsfunktionen, mit denen Sie schnell Bereiche ermitteln können, die möglicherweise ein größeres Upgrade erfordern.
