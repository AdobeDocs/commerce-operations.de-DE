---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Adobe Commerce-Highlights (v2.4.10)

## Highlights in v2.4.10-alpha1

Die folgenden Highlights gelten für die Adobe Commerce-Version 2.4.10-alpha1.

### Braintree

#### Hebebühne

Fastlane von PayPal-Unterstützung für ein schnelleres und sichereres Gast-Checkout-Erlebnis hinzugefügt.
Kunden können sich dafür entscheiden, ihre Zahlungs- und Versanddetails für schnellere zukünftige Käufe zu speichern.
Rückkehrende Fastlane-Kunden können sich mit einem einmaligen Code authentifizieren und ihre gespeicherten Informationen abrufen.
Kunden können ihre gespeicherten Karten und Versandadressen auch während des Checkouts hinzufügen oder ändern.
FastLane-Stil- und Konfigurationsoptionen werden ebenfalls unterstützt.

_BUNDLE-3521_

#### Braintree Insights

Einführung von Braintree Insights, um Händlern zentralisierte Berichte zur Zahlungsleistung in Magento Admin zu bieten.
Bietet Einblick in Transaktions-, Abwicklungs-, Ablehnungs-, Gateway- und Zahlungsmethodendaten.
Unterstützt das Filtern nach Website, Datumsbereich und täglichen, wöchentlichen oder monatlichen Intervallen.
Ermöglicht Händlern den Import von bis zu 13 Monaten historischer Transaktionsdaten für das Reporting.
Umfasst Datenaufbewahrung und automatisierte Bereinigung, um Transaktionsdaten von bis zu drei Jahren aufzubewahren.

_BUNDLE-3522_

#### SWISH - Lokale Zahlungsmethode

Einführung von Swish als neue schwedische Lokalzahlungsmethode in der Braintree Magento-Erweiterung.
Swish ist verfügbar, wenn die erforderlichen schwedischen Händler-, Länder-, Währungs- und Zahlungskonfigurationen erfüllt sind.
Kunden mit einer schwedischen Versand- oder Rechnungsadresse können Zahlungen mit Swish während des Checkouts abschließen.
Unterstützung für erfolgreiche, stornierte und fehlgeschlagene Swish-Zahlungsflüsse mit entsprechenden Checkout-Antworten wurde hinzugefügt.
Swish wird nur angezeigt, wenn alle erforderlichen Konfigurationsbedingungen erfüllt sind.

_BUNDLE-3523_

#### Aktualisierung auf Version 4.9.0

Das Braintree-Modul wurde von v4.8.0 auf v4.9.0 aktualisiert.
Das Upgrade umfasst die neuesten Änderungen und Verbesserungen am Braintree-Modul.
Überprüft, ob der Braintree-Checkout und die Zahlungsverarbeitung nach dem Upgrade weiterhin wie erwartet funktionieren.
Bestehende Kunden-Checkout- und Bestellerstellungsabläufe bleiben mit dem aktualisierten Modul funktionsfähig.
Es wurden grundlegende Regressionstests durchgeführt, um sicherzustellen, dass beim Upgrade keine Probleme auftraten

_BUNDLE-3530_

### Framework

#### [2.4.10-alpha1] Plattformkomponenten-Upgrade

Adobe Commerce 2.4.10-alpha1 enthält eine Reihe von Plattformabhängigkeits-Upgrades, Kompatibilitätsverbesserungen, Frontend-Bibliotheks-Updates und Stabilitätskorrekturen. Die folgenden abgeschlossenen Änderungen sind in dieser Version enthalten:

- Predis: Upgrade von `predis/predis` von 2.x auf 3.x, Verbesserung der Kompatibilität mit Redis- und Valkey-Umgebungen und Ausrichtung des Redis-Clients auf die neuesten unterstützten Abhängigkeitsversionen.
- Magento Composer-Installationsprogramm: Es wurde ein Problem behoben, bei dem `magento-composer-installer` ohne Abschluss des Installationsprozesses im Hintergrund fortfahren konnten, wodurch die Zuverlässigkeit von Installationen mit Composer verbessert wurde.
- Knockout.js: Knockout.js wurde von 3.5.1 auf 3.5.3 aktualisiert, zusammen mit den erforderlichen Validierungs- und Kompatibilitätsaktualisierungen.
- Chart.js: Aktualisierung von Chart.js von 4.5.0 auf 4.5.1, einschließlich der erforderlichen Validierungs- und Kompatibilitätsaktualisierungen.
- Less.js: Aktualisierung von Less.js von 4.2.2 auf 4.6.4 mit entsprechenden Validierungs- und Kompatibilitätsaktualisierungen.
- Uppy: Upgrade von Uppy von 5.0.0 auf 5.2.0, einschließlich der erforderlichen Validierungs- und Kompatibilitätsänderungen.
- jQuery-Benutzeroberfläche: Aktualisierung der jQuery-Benutzeroberfläche von 1.14.1 auf 1.14.2 mit den zugehörigen Validierungs- und Kompatibilitätsaktualisierungen.
- PHP 8.5-Kompatibilität: Behebung eines Problems mit der PHP 8.5-Verwerfung im Zusammenhang mit `chr()`, um sicherzustellen, dass die Funktion mit gültigen Byte-Werten bereitgestellt wird, und um die Kompatibilität mit PHP 8.5 zu verbessern.
- Katalogsuche: Es wurde ein Problem behoben, bei dem `catalogsearch_fulltext` Neuindizierung während der Verarbeitung angehalten werden konnte, wodurch die Zuverlässigkeit der Katalogsuchindizierung verbessert wurde.
- js-cookie: Aktualisierung von js-cookie von 3.0.5 auf 3.0.7 oder die entsprechende unterstützte Version, um Abhängigkeits- und Kompatibilitätsanforderungen zu berücksichtigen.

_AC-17061_

#### Gewährleistung der Kompatibilität von B2B 1.5.3-p1/1.5.4-alpha1 mit 2.4.10-alpha1, 2.4.9-p1, 2.4.8-p6, 2.4.7-p11 und 2.4.6-p16

B2B 1.5.4-alpha1 ist mit den folgenden Adobe Commerce-Versionen kompatibel: 2.4.9, 2.4.8, 2.4.7 und 2.4.6.

_AC-17100_

#### Upgrade und Modernisierung von NPM-Abhängigkeiten

Die folgenden npm-Abhängigkeiten wurden auf die neuesten sicheren Versionen aktualisiert, um bekannte Sicherheitslücken zu beheben:

- unterstreichen
- imagemin-svgo
- Kugel
- serve-static
- grunzen
- weniger
- uglify-js
- merklich
- clean-css
- Minimist
- trim-newlines
- Terser
- css-select
- n-te Prüfung
- Semver-Regex
- http-cache-semantics
- js-yaml
- package-json

Diese Abhängigkeitsaktualisierungen mindern die identifizierten Sicherheitslücken und erhalten gleichzeitig die vorhandene Anwendungsfunktionalität aufrecht.

_AC-17372_

#### Upgrade der NPM-Abhängigkeit: underscore.js (1.13.7 → 1.13.8)

Die Datei „underscore.js“ wurde von 1.13.7 auf 1.13.8 aktualisiert, um die neuesten Upstream-Fehlerbehebungen und Stabilitätsverbesserungen aufzunehmen.

_AC-17486 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Upgrade der NPM-Abhängigkeit: imagemin-svgo (9.0.0 → 12.0.0)

ImageMin-svgo wurde von 9.0.0 auf 12.0.0 aktualisiert und enthält jetzt die neuesten Upstream-Fehlerbehebungen, Sicherheitsaktualisierungen und SVG-Optimierungsverbesserungen.

_AC-17657 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Upgrade der NPM-Abhängigkeit: eslint-formatter-junit (8.40.0 → 9.0.1)

Aktualisierung von eslint-formatter-junit von 8.40.0 auf 9.0.1 mit den neuesten Upstream-Fehlerbehebungen und Kompatibilitätsverbesserungen für ESLint-Berichte.

_AC-17659 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Upgrade der NPM-Abhängigkeit: glob (11.0.0 → 13.0.0)

Globus wurde von 11.0.0 auf 13.0.0 aktualisiert und enthält jetzt die neuesten Upstream-Fehlerbehebungen, Leistungsverbesserungen und Kompatibilitätsverbesserungen.

_AC-17660 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Upgrade der NPM-Abhängigkeit: grunt-eslint (25.0.0 → 26.0.0)

Aktualisierung von grunt-eslint von 25.0.0 auf 26.0.0, um die neuesten Upstream-Fehlerbehebungen und Kompatibilitätsverbesserungen aufzunehmen.

_AC-17661 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Upgrade der NPM-Abhängigkeit: serve-static (1.16.2 → 2.2.1)

Serve-static wurde von 1.16.2 auf 2.2.1 aktualisiert und enthält jetzt die neuesten Upstream-Fehlerbehebungen, Sicherheitsaktualisierungen und Kompatibilitätsverbesserungen.

_AC-17662 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Aktualisieren der neuesten NPM-Abhängigkeiten für „grunt“ und „less“

Grunt und Less wurden auf die neuesten unterstützten Versionen aktualisiert, was die Stabilität und Kompatibilität des Frontend-Builds verbessert.

_AC-17663 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Upgrade von NPM Override-Abhängigkeiten auf die neuesten unterstützten Versionen

Mehrere NPM-Überschreibungsabhängigkeiten wurden auf die neuesten unterstützten Versionen aktualisiert, um die Sicherheit, Build-Stabilität und Kompatibilität zu verbessern.

_AC-17664 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c69ec9c5)_

#### [B2B] Bestellungen werden nicht automatisch in Kundenaufträge mit ActiveMQ konvertiert

Es wurde ein Problem behoben, bei dem Bestellungen, die über die Storefront mit aktivierter automatischer Genehmigung aufgegeben wurden, nicht automatisch in Kundenaufträge umgewandelt wurden, wenn ActiveMQ verwendet wurde und Verbraucher über Cron (bin/magento cron:run) laufen. Zuvor wurden Nachrichten zur ActiveMQ-Warteschlange hinzugefügt, aber nicht verarbeitet, es sei denn, der Benutzer wurde manuell über die CLI gestartet. Mit dieser Fehlerbehebung verarbeitet der -Verbraucher nun nach der Ausführung von Cron wie erwartet Nachrichten und gewährleistet so eine nahtlose Bestellkonvertierung für B2B-Händler, die ActiveMQ verwenden.

_AC-17679_

#### Symfony L2-Cache-Optimierung und alte Cache-Abwärtskompatibilität

Adobe Commerce 2.4.10 bietet jetzt optimierte Unterstützung für Symfony L2-Cache, wobei die bestehende Zend-basierte Cache-Implementierung als Standard beibehalten wird.

Händler, die Symfony Cache verwenden möchten, müssen ihn explizit aktivieren und die erforderliche Cache-Konfiguration für die Symfony L1/L2-Implementierung aktualisieren. Bestehende Händler, die weiterhin den Zend-basierten Cache verwenden, müssen keine Konfigurationsänderungen vornehmen.

Dieser Dual-Cache-Ansatz bietet Händlern die Flexibilität, Symfony-Cache basierend auf ihren Anforderungen zu verwenden und gleichzeitig die Abwärtskompatibilität mit vorhandenen Cache-Konfigurationen und -Bereitstellungen sicherzustellen.

_AC-17865_

### Sonstige

#### Verwaltung der Unterregionen der Länder (Bundesstaaten und Provinzen)

Händler können jetzt Unterregionen für Länder (wie Bundesstaaten und Provinzen) direkt über die Admin-Benutzeroberfläche verwalten. Diese neue Funktion ermöglicht Händlern Folgendes:

- Anzeigen, Hinzufügen, Bearbeiten, Deaktivieren oder Entfernen von Regionen für ein beliebiges Land.
- Stellen Sie neue Regionen sofort als Dropdown-Optionen an der Kasse, in Kundenadressformularen und bei der Erstellung von Admin-Aufträgen zur Verfügung - keine Code-Änderungen erforderlich.
- Anzeigenamen (einschließlich lokalisierter Namen) und ISO-Codes für die Bearbeitungsregion.
- Deaktivieren Sie Regionen, auf die von vorhandenen Bestellungen, Adressen oder Steuerregeln verwiesen wird (wobei sichergestellt wird, dass historische Daten korrekt bleiben), und verhindern Sie gleichzeitig das harte Löschen solcher Regionen.
- Alle vordefinierten Bereiche bleiben unverändert und sind jetzt in der neuen Benutzeroberfläche sichtbar und verwaltbar.

Diese Funktion ist vollständig abwärtskompatibel und stellt sicher, dass das Verhalten kundenorientierter und API-Adressen konsistent bleibt.

_AC-16192_

#### Aktualisieren von Predis/Predis von 2.x auf 3.x

Die Redis-Client-Bibliothek predis/predis wurde von Version 2.x auf 3.x aktualisiert. Dieses große Versions-Upgrade entspricht den neuesten Abhängigkeitsstandards, verbessert die Kompatibilität und sorgt für langfristige Wartbarkeit.

_AC-17101 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de7188da)_

#### Aktualisieren von knockout.js von Version 3.5.1 auf 3.5.3

Die Bibliothek knockout.js wurde von Version 3.5.1 auf 3.5.3 aktualisiert. Dieses Update bringt vorgelagerte Fehlerbehebungen und Stabilitätsverbesserungen für alle Benutzeroberflächenkomponenten, die Knock-out-Bindungen sowohl in der Storefront als auch in der Admin verwenden.

_AC-17366 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de7188da)_

#### Aktualisieren von Lack auf Version 9 für 2.4.10-alpha1

Adobe Commerce 2.4.10 ist kompatibel mit Lack Version 9.0.

_AC-17972_
