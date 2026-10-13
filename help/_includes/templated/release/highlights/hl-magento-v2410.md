---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Magento Open Source-Highlights (v2.4.10)

## Highlights in v2.4.10-alpha1

Die folgenden Highlights gelten für die Magento Open Source-Version 2.4.10-alpha1.

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

### Sonstige

#### Aktualisieren von Predis/Predis von 2.x auf 3.x

Die Redis-Client-Bibliothek predis/predis wurde von Version 2.x auf 3.x aktualisiert. Dieses große Versions-Upgrade entspricht den neuesten Abhängigkeitsstandards, verbessert die Kompatibilität und sorgt für langfristige Wartbarkeit.

_AC-17101 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de7188da)_

#### Aktualisieren von knockout.js von Version 3.5.1 auf 3.5.3

Die Bibliothek knockout.js wurde von Version 3.5.1 auf 3.5.3 aktualisiert. Dieses Update bringt vorgelagerte Fehlerbehebungen und Stabilitätsverbesserungen für alle Benutzeroberflächenkomponenten, die Knock-out-Bindungen sowohl in der Storefront als auch in der Admin verwenden.

_AC-17366 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de7188da)_
