---
source-git-commit: 5b0229d73dc7b8ad53750102e99447bb15baa84d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.9-alpha2)

## Highlights in v2.4.9-alpha2

Die folgenden Highlights gelten für die Magento Open Source-Version 2.4.9-alpha2.

### Framework

#### Unterstützung für OpenSearch 3 hinzufügen

Adobe Commerce 2.4.9 ist jetzt vollständig mit OpenSearch 3.x kompatibel. Dieses Update ermöglicht es Händlern, von verbesserter Leistung, Sicherheit und langfristigem Support zu profitieren und gleichzeitig die Abwärtskompatibilität mit OpenSearch 2.x zu wahren.

_AC-11846_

#### Nginx-Version von 1.26 auf 1.28 aktualisieren

Die Nginx-Version, die in Entwicklungs- und Testumgebungen in allen derzeit unterstützten Versionen von Adobe Commerce verwendet wird, wurde von 1.26 auf 1.28 aktualisiert und entspricht der neuesten stabilen Nginx-Version, die verfügbar ist.
Tests auf PR-Ebene werden jetzt mit Nginx 1.28 ausgeführt und bestätigen die vollständige Kompatibilität und Unterstützung für alle Adobe Commerce-Versionen.

_AC-14104_

#### Untersuchen der neuesten Version von jQuery-validate

Die jQuery Validate-Bibliothek wurde auf Version 1.21.0 aktualisiert, um die Formularvalidierungsfunktionen zu verbessern, das Benutzererlebnis zu verbessern und eine moderne Browserkompatibilität für alle Adobe Commerce-Formulare sowohl in der Admin- als auch in der Frontend-Benutzeroberfläche sicherzustellen.

_AC-14403 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Untersuchen der neuesten Version von jQuery-ui

Die jQuery UI-Bibliothek wurde auf Version 1.14.1 aktualisiert, um Benutzeroberflächen-Widgets zu verbessern, die Barrierefreiheit zu verbessern und eine moderne Browserkompatibilität für alle Adobe Commerce Admin- und Frontend-Schnittstellenkomponenten sicherzustellen.

_AC-14417 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/77c589a6)_

#### Untersuchen der neuesten Version von less.js

Der CSS-Präprozessor von Less.js wurde auf Version 4.2.2 aktualisiert, um die CSS-Kompilierungsleistung zu verbessern, die Syntaxunterstützung zu verbessern und den Design-Build-Prozess für alle Adobe Commerce-Frontend- und Admin-Designs zu modernisieren.

_AC-14418 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Untersuchen Sie die neueste Version von moment-timezone-with-data.js

Die Zeitzonenbibliothek von Moment wurde auf Version 0.5.43 aktualisiert, um die Zeitzonenhandhabungsfunktionen zu verbessern, Zeitzonendaten mit den neuesten Änderungen der IANA-Zeitzonendatenbank zu aktualisieren und die Genauigkeit der Datums-/Zeitverarbeitung in allen internationalen und Multi-Zeitzonenvorgängen von Adobe Commerce zu verbessern.

_AC-14419 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Untersuchen der neuesten Version von underscore.js

Die Unterstrich.js-Dienstprogrammbibliothek wurde auf Version 1.13.7 aktualisiert, um die JavaScript-Funktionsprogrammierfunktionen zu verbessern, die Datenmanipulationsleistung zu verbessern und eine moderne Browserkompatibilität für alle Frontend- und Admin-Schnittstellenkomponenten von Adobe Commerce sicherzustellen.

_AC-14420 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Migration von TinyMCE zu Hugerte.org

Aufgrund des Auslaufens der Unterstützung für TinyMCE 5 und 6 und der Lizenzierungsinkompatibilitäten mit TinyMCE 7 wird die aktuelle Implementierung des Adobe Commerce WYSIWYG-Editors von TinyMCE in den Open-Source-HugeRTE-Editor (https://hugerte.org/) migriert.
Diese Migration stellt sicher, dass Adobe Commerce weiterhin mit der Open-Source-Lizenzierung konform ist, bekannte TinyMCE 6-Schwachstellen vermeidet und Händlern und Entwicklern ein modernes, unterstütztes Bearbeitungserlebnis bietet.

_AC-14568_

#### Vollständige Valkey 8.x-Unterstützung für 2.4.9-alpha2 hinzufügen

Adobe Commerce 2.4.9 verfügt über eine vollständige CLI-Befehlsunterstützung für Valkey, die die aktuelle Redis-Funktionalität widerspiegelt. Die Admin- und Cloud-Konfiguration wurde aktualisiert, um eine nahtlose Einrichtung von Valley zu ermöglichen.
Dieses Update stellt sicher, dass Adobe Commerce zukunftssicher und leistungsfähig bleibt, indem es Valkey 8.x unterstützt und Händlern und Entwicklern eine zuverlässige Alternative zu Redis bietet, wenn es sich dem Ende des Lebenszyklus nähert.

_AC-14604_

### Sonstige

#### Aktualisieren des AWS Valkey 8.x-Service für CNS Build and Test

Aktualisieren des AWS Valkey 8.x-Service für CNS Build

_AC-14470_

#### 2.4.9-alpha2 - Verbesserungen der Kernqualität im August

_AC-14700_

### Sicherheit

#### Sicherheitsverbesserungen für 2.4.9-alpha2

_AC-14610_

### Lieferung

#### Migrieren der USPS-Integration von veralteten Web-Tools-APIs zu neuen RESTful-USPS-APIs

Um die von USPS angekündigte Einstellung der veralteten Web-Tools-APIs bis zum 25. Januar 2026 einzuhalten, wird die Adobe Commerce USPS-Integration auf die neuen RESTful-USPS-APIs migriert.

Wichtige Verbesserungen:

* Unterstützung von zwei APIs: Admin-Benutzer können jetzt über die Konfigurationseinstellungen zwischen der Legacy Web Tools-API und der neuen RESTful USPS-API wählen.
* Authentifizierungs-Upgrade: OAuth 2.0 wurde für sicheren API-Zugriff implementiert.
* Verbessertes Datenformat: Übergang von XML zu JSON für sauberere, effizientere Kommunikation.
* Neue Administratorfelder:
   * Gateway-REST-URL (basierend auf Modus: Entwicklung oder Live)
   * Client-ID und Geheimnis
   * Kontotyp, Kontonummer
   * CRID, MID, Mailer-Identifizierungscode
   * AES/ITN für internationale Sendungen
   * REST-spezifische zulässige Versandmethoden

Diese Migration stellt sicher, dass Adobe Commerce weiterhin die USPS-Standards erfüllt, die Systemzuverlässigkeit verbessert und die Versandintegrationen für Händler zukunftssicher macht.

_AC-13257_
