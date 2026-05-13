---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Magento Open Source-Highlights (v2.4.9)

## Highlights in Version 2.4.9

Die folgenden Highlights gelten für die Version 2.4.9 von Magento Open Source.

### APIs

#### Hinzufügen der Möglichkeit, die Vererbung der Produktgalerie in der REST-API beizubehalten, wenn ein Produkt auf Store-Ansichtsebene aktualisiert wird

Die Aktualisierung eines Produkts über die REST-API in einem Store-Bereich führt nicht mehr dazu, dass Produktbilder und Videos Änderungen vom globalen Bereich übernehmen, wenn media_gallery_entries in der Payload weggelassen oder auf NULL gesetzt wird, um Änderungen in der Produktgalerie in diesem Bereich zu verhindern. Darüber hinaus ist es jetzt möglich, die Bereichsvererbung für Produktbilder und Videos über die REST-API wiederherzustellen, indem das entsprechende Feld auf NULL festgelegt wird.

_ACP2E-4358 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### Vaulting Google Pay über den Kontobereich

In Adobe Commerce 2.4.9 können Kundinnen und Kunden ihre Google Pay Cards jetzt über den Kontobereich tresoren, wenn Google Pay Vault in Braintree aktiviert ist. Tresorkarten erscheinen unter gespeicherten Zahlungsmethoden, können für zukünftige Käufe an der Kasse verwendet werden und können vom Kunden gelöscht werden. Dies erweitert die Vaulting-Unterstützung über Cards und PayPal hinaus auf Google Pay.

_BUNDLE-3459_

#### Real-Time Account Updater (RTAU)

Die Funktion Real-Time Account Updater (RTAU) in Adobe Commerce 2.4.9 für Braintree stellt sicher, dass die Details der Visa-, MasterCard- und Discover-Karten mit Vault automatisch aktualisiert werden, wenn Karten ablaufen oder ersetzt werden. Dadurch werden fehlgeschlagene Zahlungen minimiert, Magento Vault wird aktuell gehalten und nicht unterstützte Typen (Prepaid, Apple Pay, Google Pay) werden fehlerfrei übersprungen.

_BUNDLE-3462_

#### Unterstützung des ELO-Kartentyps für Braintree-Kartenzahlungen

In Adobe Commerce 2.4.9 wurde die Unterstützung für den ELO-Kartentyp zu Braintree Payments hinzugefügt. Administratoren können jetzt ELO in der Kreditkartenkonfiguration aktivieren, und Kunden können erfolgreich Bestellungen mit ELO-Karten an der Kasse aufgeben, wodurch nahtlose Transaktionen über Braintree sichergestellt werden.

_BUNDLE-3464_

#### Zahlung auf Rechnung

Für Adobe Commerce 2.4.9 (Braintree-Erweiterung) wurde für deutsche Käufer eine neue lokale Zahlungsmethode „Pay Upon Invoice“ hinzugefügt. Pay Upon Invoice ist eine Pay Now, Pay Later (BNPL) Option von PayPal + Ratepay („Rechnungskauf mit Ratepay„), die es Kunden ermöglicht, zuerst Waren zu erhalten und die Rechnung innerhalb von 30 Tagen zu bezahlen, ohne ein PayPal-Konto zu benötigen. Da es sich nicht um eine sofortige Zahlung handelt, wird die Auftragsabwicklung durch einen Server-seitigen Webhook von PayPal gesteuert.

_BUNDLE-3475_

#### Hinzufügen von Angeboten zum Google Pay Express-Zahlungsblatt

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 unterstützt die Google Pay Express Pay Sheet jetzt Promo-/Angebotscodes. Kundinnen und Kunden können Magento-Warenkorbaktionen direkt auf dem Google-Zahlungsbogen beantragen, anzeigen und entfernen, sodass Kundinnen und Kunden mit einem Express-Checkout die gleichen Rabatte und Anreize erhalten wie normale Checkout-Abläufe.

_BUNDLE-3476_

#### Hinzufügen von Angeboten zur Apple Pay Express-Zahlungsliste

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 unterstützt die Apple Pay Express Pay Sheet jetzt Promo-/Angebotscodes. Kundinnen und Kunden können einen Gutschein direkt in der Apple-Zahlungsanzeige beantragen, sodass Benutzer, die einen Express-Checkout durchführen, von denselben Rabatten und Kampagnen profitieren wie normale Checkout-Abläufe.

_BUNDLE-3477_

#### Bezahlen mit Apple Pay auf Chrome und Firefox

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 kann Apple Pay jetzt auf Chrome und Firefox verwendet werden, nicht nur in Safari. Wenn Apple Pay Express aktiviert ist, sind die Pay-Buttons von Apple in allen unterstützten Storefront-Standorten verfügbar, und Kundinnen und Kunden schließen die Zahlung ab, indem sie einen Code mit ihrer iPhone scannen.

_BUNDLE-3478_

#### Server-seitiger Versandrückruf

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 wurde der PayPal Express-Versand-Callback von Client- auf Serverseite verschoben. Dies bietet dynamische Versandmethoden, Echtzeit-Kostenberechnungen und genaue Details auf Warenkorbebene direkt im PayPal-Modal, wodurch die Zuverlässigkeit verbessert wird und die Grundlage für zukünftige Funktionen wie die Unterstützung von Kontaktmodulen, App-Switch-Flüsse und Venmo Express gelegt wird.

_BUNDLE-3479_

#### PayPal-Kontaktmodul

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 wird ein neues PayPal-Kontaktmodul für US-Händler eingeführt. Wenn diese Option aktiviert ist, können Käufer, die PayPal Express verwenden, die E-Mail-Adresse und Telefonnummer, die mit dem Händler geteilt wurde, direkt innerhalb des PayPal-Modals während der Express-Flüsse (PDP, Mini-Warenkorb, Warenkorb, Checkout-Express) anzeigen und aktualisieren. Die ausgewählten Kontaktdaten werden dann in der Adobe Commerce-Bestellung gespeichert.

_BUNDLE-3480_

#### BLIK (Lokale Zahlungsmethode)

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 wurde BLIK als neue lokale Zahlungsmethode für polnische Käufer hinzugefügt. Dies ermöglicht sichere, bankbasierte BLIK-Zahlungen innerhalb des bestehenden Flusses der Braintree Local Payment Methods (LPM) und verbessert den Checkout-Komfort und die Konversion für Kunden in Polen.

_BUNDLE-3481_

#### Kardinale Integrationsaktualisierung - CSP-Richtlinie

Für die Braintree-Erweiterung in Adobe Commerce 2.4.9 wurde die Content Security Policy (CSP) aktualisiert, um die neuesten Anforderungen an die Integration von Cardinal (3-D Secure) zu unterstützen. Dadurch wird sichergestellt, dass alle Kardinal-gehosteten Skripte, iFrames und zugehörigen Ressourcen, die während sicherer 3D-Flüsse verwendet werden, vom CSP des Browsers zugelassen werden, um blockierte Anfragen und fehlerhafte Challenge-/Verifizierungserlebnisse zu verhindern.

_BUNDLE-3485_

### Framework

#### Web-Token-/JWT-Framework-Bibliothek wurde auf die neueste Hauptversion aktualisiert.

Im Rahmen der kontinuierlichen Sicherheitsüberprüfung haben wir die neueste Hauptversion des JWT-Frameworks evaluiert, um die zukünftige Kompatibilität sicherzustellen und starke Sicherheitsstandards aufrechtzuerhalten. In dieser Version gibt es keine Auswirkungen auf die vorhandene Funktionalität.

_AC-13209 - [GitHub-Code-](https://github.com/magento/magento2/commit/2bac8114) - [GitHub-Code-](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/33b81f28)_

#### [Teil 2] - Aktualisieren aller js-Bibliothek und npm-Abhängigkeiten mit der neuesten verfügbaren Version

Die Unterstützung der Composer-Version beschränkte sich auf die Composer-Version 2.2.x. Jetzt wurde die Unterstützung auch auf Version 2.4.x erweitert.

_AC-13792 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/19844aa0)_

#### Ersetzen Sie Carlos-mg89/oauth durch PHP Native Funktionen

Die Drittanbieter-Bibliothek „carlos-mg89/oauth“ wurde durch native PHP-OAuth-Funktionen ersetzt, um die Sicherheit zu verbessern, externe Abhängigkeiten zu reduzieren und die Plattformstabilität zu verbessern.

_AC-14075 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7b8064f7)_

#### Upgrade von jQuery/Uppy und Uppy-Bibliotheken auf die neueste Version

Die Uppy-Datei-Upload-Bibliothek wurde auf Version 4.13.4 aktualisiert, um die Dateiupload-Funktionen zu verbessern, das Benutzererlebnis zu verbessern und Sicherheitslücken bei der Dateiverarbeitung in der Admin-Oberfläche und den Frontend-Komponenten von Adobe Commerce zu beheben.

_AC-14307 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/eb491c05)_

#### jQuery-Validate-Bibliothek auf die neueste Version aktualisieren

Die jQuery Validate-Bibliothek wurde auf Version 1.21.0 aktualisiert, um die Formularvalidierungsfunktionen zu verbessern, das Benutzererlebnis zu verbessern und eine moderne Browserkompatibilität für alle Adobe Commerce-Formulare sowohl in der Admin- als auch in der Frontend-Benutzeroberfläche sicherzustellen.

_AC-14403 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### jQuery-UI-Bibliothek auf die neueste Version aktualisieren

Die jQuery UI-Bibliothek wurde auf Version 1.14.1 aktualisiert, um Benutzeroberflächen-Widgets zu verbessern, die Barrierefreiheit zu verbessern und eine moderne Browserkompatibilität für alle Adobe Commerce Admin- und Frontend-Schnittstellenkomponenten sicherzustellen.

_AC-14417 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/77c589a6)_

#### Aktualisieren der less.js-Bibliothek auf die neueste Version

Der CSS-Präprozessor von Less.js wurde auf Version 4.2.2 aktualisiert, um die CSS-Kompilierungsleistung zu verbessern, die Syntaxunterstützung zu verbessern und den Design-Build-Prozess für alle Adobe Commerce-Frontend- und Admin-Designs zu modernisieren.

_AC-14418 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Aktualisieren Sie die Bibliothek „moment-timezone-with-data.js“ auf die neueste Version

Die Zeitzonenbibliothek von Moment wurde auf Version 0.5.43 aktualisiert, um die Zeitzonenhandhabungsfunktionen zu verbessern, Zeitzonendaten mit den neuesten Änderungen der IANA-Zeitzonendatenbank zu aktualisieren und die Genauigkeit der Datums-/Zeitverarbeitung in allen internationalen und Multi-Zeitzonenvorgängen von Adobe Commerce zu verbessern.

_AC-14419 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Aktualisieren der Bibliothek „underscore.js“ auf die neueste Version

Die Unterstrich.js-Dienstprogrammbibliothek wurde auf Version 1.13.7 aktualisiert, um die JavaScript-Funktionsprogrammierfunktionen zu verbessern, die Datenmanipulationsleistung zu verbessern und eine moderne Browserkompatibilität für alle Frontend- und Admin-Schnittstellenkomponenten von Adobe Commerce sicherzustellen.

_AC-14420 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Aktualisieren Sie allure-framework/allure-phpunit Version auf 3 und entfernen Sie die native Abhängigkeit in 2.4.9-alpha1

In Adobe Commerce 2.4.9 wurde die Abhängigkeit von allure-framework/allure-phpunit auf Hauptversion 3 aktualisiert, was die Unterstützung von PHP 8.4 und PHP 8.5 hinzufügt und unseren Allure-basierten Test-Reporting-Stack modernisiert. Die native Abhängigkeit, die zuvor von älteren Allure PHPUnit-Versionen benötigt wurde, wurde entfernt, wo zutreffend, wodurch die Einrichtung und Wartung vereinfacht wurde.

_AC-14548 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/87b8b34e)_

#### Aktualisieren der chart.js-Abhängigkeit auf die neueste Version

Die Chart.js-Abhängigkeit wird auf die neueste Version 4.5.0 aktualisiert.

_AC-15133 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/657f983e)_

#### Offizielle Unterstützung für Symfony 7.4 LTS und PHP 8.5 in Adobe Commerce 2.4.9 hinzugefügt

Im Rahmen der Adobe Commerce 2.4.9 Plattformaktualisierungen wurden alle Symfony-Abhängigkeiten, die vom magento/composer-Paket verwendet werden, auf die neuesten Symfony LTS 7.4 Versionen aktualisiert. Dadurch werden Commerce Composer-Tools an der aktuellen Symfony LTS-Linie ausgerichtet und frühere Abhängigkeitsbeschränkungen für ältere Symfony-Versionen entfernt. Darüber hinaus haben alle benutzerdefinierten Klassen, die Symfony-Kernklassen erweitern, Typdeklarationen und Methodensignaturen aktualisiert, die mit den neuesten Symfony-Anforderungen abgestimmt sind, bevor sie auf Adobe Commerce 2.4.9 aktualisiert werden. Dadurch werden Kompatibilitätsprobleme vermieden und ein reibungsloser Übergang zu den aktualisierten Framework-Komponenten sichergestellt.

_AC-15170 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Stellen Sie sicher, dass in Open Source eine ClearCart-GraphQL-Mutation verfügbar ist.

Mit Adobe Commerce 2.4.9 ist die clearCart-GraphQL-Mutation nun für alle Open Source-Anwender verfügbar. Zuvor war diese Mutation nur in Adobe Commerce verfügbar, ist jetzt jedoch auch Teil der standardmäßigen GraphQL-Warenkorbfunktion für Open Source.
Die Dokumentation für die Mutation wurde aktualisiert, um die Verfügbarkeit in Open Source für Version 2.4.9 widerzuspiegeln.
Siehe [ClearCart GraphQL-Mutationsdokumentation](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/).

_AC-16683 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9] Zusammenführen von Gast- und Kundencartlogik mithilfe der Admin-Konfiguration

Eine neue Admin-Konfigurationsoption wurde eingeführt, um zu steuern, wie Gast- und Kundenwagen zusammengeführt werden, wenn sich ein Käufer anmeldet. Diese Verbesserung bietet Ihnen Flexibilität bei der Definition des Warenkorb-Zusammenführungsverhaltens, das Ihren Geschäftsanforderungen am besten entspricht.

_LYNX-889_

#### [AC-2.4.9] Historische Bestellungen mit nicht vorrätigen Produkten abrufen

Historische Bestellungen zeigen jetzt Produktdetails an, auch wenn sie jetzt nicht mehr vorrätig sind.

_LYNX-913_

#### [AC-2.4.9] [CE] Implementieren von ReCaptcha für fehlende GraphQL-Mutationen

Die ReCaptcha-Validierung wird den Mutationen updateCustomer, updateCustomerV2 und contactUs hinzugefügt.

_LYNX-941_

### Sonstige

#### Captcha / reCAPTCHA funktioniert nicht für API / GraphQL

Wenn in Adobe Commerce 2.4.9 CAPTCHA (oder reCAPTCHA) für das Formular Konto erstellen aktiviert ist, wird jetzt dieselbe CAPTCHA-Validierung für die Erstellung von Kundenkonten über REST- und GraphQL-APIs erzwungen.

_AC-16245 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd7f30ee)_

#### Braintree Branch sollte mit PHP 8.5-Unterstützung aktualisiert werden

Die Braintree-Zahlungserweiterung wurde aktualisiert, um die neueste PHP 8.5-Laufzeitumgebung zu unterstützen und gleichzeitig die Kompatibilität mit PHP 8.4 zu gewährleisten.

_BUNDLE-3493_

#### Löschung der Wunschliste hinzufügen

Es wurde eine neue ClearWishlist-Mutation hinzugefügt, die Massenvorgänge unterstützt, sodass alle Elemente in einer einzigen Aktion aus einer Wunschliste entfernt werden können.

_LYNX-790_

#### Einführung der exchangeExternalCustomerToken-Mutation

Die neue GraphQL-Mutation exchangeExternalCustomerToken wurde eingeführt, die Benutzende über ein Integrations-Token authentifiziert und sowohl das Kunden-Token als auch die zugehörigen Kundendaten zurückgibt

_LYNX-815_

#### [AC] Einführung von GraphQL-Abfragen, die angewendete Gruppen-, Segment- und Warenkorb-Regel-IDs zurückgeben

GraphQL-Abfragen werden bereitgestellt, um die codierte UID der angewendeten Kundengruppe, Kundensegmente und Warenkorbregeln abzurufen.

_LYNX-867_

#### [AC-2.4.9] Feld „OrderTotal.grand_total_excl_tax“ einführen

Ein neues Feld, OrderTotal.grand_total_excl_tax, wurde zur GraphQL-Bestellantwort hinzugefügt. Dieses Feld gibt den Gesamtbetrag ohne Steuern an, was den direkten Zugriff auf die Gesamtsumme ohne Steuern über die API erleichtert.

Vorteile:

- Einfaches Abrufen der Gesamtsumme ohne MwSt. für jede Bestellung über GraphQL.
- Vereinfacht die Integration mit externen Systemen, für die steuerliche Gesamtwerte erforderlich sind.
- Verringert den Bedarf an benutzerdefinierten Berechnungen auf der Client-Seite.

_LYNX-892_

### PCI, Sicherheit

#### Umgestalten von SRI-Speicher für mehr Performance-Effizienz

Der SRI-Hash-Speicher generiert jetzt separate Dateien pro Bereich, Design und Gebietsschema anstelle eines einzelnen großen sri-hashes.json. Durch diese Änderung wird sichergestellt, dass für jede Seite nur die relevante Hash-Datei geladen wird. Dies verbessert die Leistung und reduziert die Speichernutzung in Stores mit mehreren Designs oder Gebietsschemata.

_AC-16113 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/bc83cd2c)_

### Sicherheit

#### Leistung bei asynchronen/Massenanfragen verbessern

Behebung der Leistungsbeeinträchtigung bei asynchronen Massenwebendpunkten, die nach dem APSB25-08-Sicherheits-Patch eingeführt wurden, was zu verlängerten Ausführungszeiten führte.

_AC-14078 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9a7352b7)_

#### Pro Benutzer muss nur ein aktivierter 2FA-Provider konfiguriert werden

Administratorbenutzer müssen jetzt nur noch einen der aktivierten 2FA-Provider des Händlers (z. B. Google Authenticator oder U2F) konfigurieren, um auf das Admin-Bedienfeld zuzugreifen. Zusätzliche aktivierte Anbieter können bei Bedarf später konfiguriert werden. Wenn zuvor mehrere 2FA-Anbieter aktiviert waren (z. B. Google Authenticator und U2F), musste jeder Admin-Benutzer alle aktivierten Anbieter konfigurieren, bevor er sich anmelden konnte. Dies führte zu Spannungen für Benutzer, die nicht auf alle Faktoren Zugriff hatten (wie z. B. einen Hardware-Schlüssel für U2F).

_AC-8253 - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/71e7936b)_
