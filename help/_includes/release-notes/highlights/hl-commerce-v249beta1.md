---
source-git-commit: adda02b9d05b66ab066f110e877584bc1c77515d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Adobe Commerce-Highlights (v2.4.9-beta1)

## Highlights in v2.4.9-beta1

Die folgenden Highlights gelten für die Adobe Commerce-Version 2.4.9-beta1.

### APIs

#### Vererbungskontrolle der REST-API-Produktgalerie auf Store-Ansichtsebene

Wenn ein Produkt über die REST-API in einem Store-Bereich aktualisiert wird, erben Produktbilder und Videos keine Änderungen mehr vom globalen Umfang, wenn `media_gallery_entries` in der Payload weggelassen oder auf `NULL` gesetzt wird. Es ist jetzt auch möglich, die Bereichsvererbung für Produktbilder und Videos über die REST-API wiederherzustellen, indem das entsprechende Feld auf `NULL` festgelegt wird.

_ACP2E-4358 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Admin-Benutzeroberfläche

#### Aktionsmenü für das Katalogpreisregeln-Raster

Das Raster Katalogpreisregeln in Commerce Admin enthält jetzt ein Aktionsmenü, über das Händler mehrere Katalogpreisregeln gleichzeitig aktivieren, deaktivieren oder löschen können. Dadurch wird die Verwaltung der Katalogpreisregeln an die vorhandenen Massenaktionen angepasst, die für Warenkorbpreisregeln verfügbar sind, wodurch der Zeitaufwand für die Verwaltung großer Regelsätze erheblich reduziert wird.

_AC-13916_

#### Mobile-Vorschau für Inhalts-Staging

Die Staging-Vorschaufunktion in Admin ermöglicht jetzt die genaue Darstellung der Browser-simulierten Mobile-Device-Vorschauen und bietet eine visuelle Darstellung, wie eine Staging-Aktualisierung auf einem mobilen Gerät aussieht.

_ACP2E-3397 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### Express-Checkout

- **Werbeangebote im Google Pay Express-Lohnbogen**

  Die Google Pay Express Pay Sheet unterstützt jetzt Promo- und Angebotscodes. Kundinnen und Kunden können Commerce-Warenkorbaktionen direkt auf dem Google-Zahlungsbogen beantragen, anzeigen und entfernen, sodass Kundinnen und Kunden mit einem Express-Checkout die gleichen Rabatte und Anreize erhalten wie normale Checkout-Abläufe.

  _BUNDLE-3476_

- **Werbeangebote im Apple Pay Express-Lohnbogen**

  Die Apple Pay Express Pay Sheet unterstützt jetzt Promo- und Angebotscodes. Kundinnen und Kunden können einen Gutschein direkt in der Apple-Zahlungsanzeige beantragen, sodass Benutzer, die einen Express-Checkout durchführen, von denselben Rabatten und Kampagnen profitieren wie normale Checkout-Abläufe.

  _BUNDLE-3477_

- **Apple Pay für Chrome und Firefox**

  Apple Pay kann jetzt auf Chrome und Firefox verwendet werden, nicht nur in Safari. Wenn Apple Pay Express aktiviert ist, sind die Pay-Buttons von Apple in allen unterstützten Storefront-Standorten verfügbar, und Kundinnen und Kunden schließen die Zahlung ab, indem sie einen Code mit ihrer iPhone scannen.

  _BUNDLE-3478_

- **Server-seitiger Versandrückruf für PayPal Express**

  Der Versandrückruf PayPal Express wurde von Client- auf Server-Seite verschoben. Dies bietet dynamische Versandmethoden, Echtzeit-Kostenberechnungen und genaue Details auf Warenkorbebene direkt im PayPal-Modal, wodurch die Zuverlässigkeit verbessert wird und die Grundlage für zukünftige Funktionen wie die Unterstützung von Kontaktmodulen, App-Switch-Flüsse und Venmo Express gelegt wird.

  _BUNDLE-3479_

- **PayPal-Kontaktmodul für U.S. Händler-Express-Checkout**

  Für US-Händler wird ein neues PayPal-Kontaktmodul eingeführt. Wenn diese Option aktiviert ist, können Käufer, die PayPal Express verwenden, die E-Mail-Adresse und Telefonnummer, die mit dem Händler geteilt wurde, direkt innerhalb des PayPal-Modals während der Express-Flüsse (PDP, Mini-Warenkorb, Warenkorb, Checkout-Express) anzeigen und aktualisieren. Die ausgewählten Kontaktdaten werden dann in der Commerce-Bestellung gespeichert.

  _BUNDLE-3480_

#### Zahlungsmethoden

- **ELO-Kartenunterstützung für Braintree-Zahlungen**

  Unterstützung für den ELO-Kartentyp wurde zu Braintree Payments hinzugefügt. Administratoren können jetzt ELO in der Kreditkartenkonfiguration aktivieren, und Kunden können erfolgreich Bestellungen mit ELO-Karten an der Kasse aufgeben, wodurch nahtlose Transaktionen über Braintree sichergestellt werden.

  _BUNDLE-3464_

- **BLIK-Lokalzahlungsmethode für polnische Käufer**

  BLIK wurde als neue lokale Zahlungsmethode für polnische Käufer hinzugefügt. Dies ermöglicht sichere, bankbasierte BLIK-Zahlungen innerhalb des bestehenden Flusses der Braintree Local Payment Methods (LPM) und verbessert den Checkout-Komfort und die Konversion für Kunden in Polen.

  _BUNDLE-3481_

- **Zahlung auf Rechnung — neue BNPL-Zahlungsmethode für Deutschland**

  Es wurde eine neue lokale Zahlungsmethode hinzugefügt, Bezahlung auf Rechnung für deutsche Käufer. Pay Upon Invoice ist eine Pay Now, Pay Later (BNPL) Option von PayPal und Ratepay („Rechnungskauf mit Ratepay„), die es Kunden ermöglicht, Waren zuerst zu erhalten und die Rechnung innerhalb von 30 Tagen zu bezahlen, ohne ein PayPal-Konto zu benötigen. Da es sich nicht um eine sofortige Zahlung handelt, wird der Abschluss von Bestellungen durch einen Server-seitigen Webhook von PayPal gesteuert.

  _BUNDLE-3475_

#### Kartengewölbe

- **Vaulting Google Pay über den Kontobereich**

  Kunden können jetzt ihre Google Pay Cards über den Kontobereich tresoren, wenn Google Pay Vault in Braintree aktiviert ist. Tresorkarten erscheinen unter gespeicherten Zahlungsmethoden, können für zukünftige Käufe an der Kasse verwendet werden und können vom Kunden gelöscht werden. Dies erweitert die Vaulting-Unterstützung über Cards und PayPal hinaus auf Google Pay.

  _BUNDLE-3459_

- **Echtzeit-Kontoaktualisierer (RTAU) für Braintree-Tresorkarten**

  Die Braintree hinzugefügte Funktion Real-Time Account Updater (RTAU) stellt sicher, dass die Kartendetails von Vault Visa, MasterCard und Discover automatisch aktualisiert werden, wenn Karten ablaufen oder ersetzt werden. Dadurch werden fehlgeschlagene Zahlungen minimiert, der Commerce Vault wird aktuell gehalten und nicht unterstützte Typen (Prepaid, Apple Pay, Google Pay) werden fehlerfrei übersprungen.

  _BUNDLE-3462_

#### Admin-Tools

- **Verknüpfen der Commerce-Bestellung mit dem Braintree-Portal**

  Im Commerce-Admin wird nun ein Braintree Portal-Link zu den Bestelldetails hinzugefügt. Wenn Sie auf den Link klicken, wird die zugehörige Transaktion im Braintree-Portal (auf einer neuen Registerkarte) unter Verwendung der Händler-ID und der Transaktions-ID aus der Commerce-Bestellung geöffnet. Dies ermöglicht einen direkten Querverweis, ohne sich separat bei beiden Systemen anzumelden.

  _BUNDLE-3461_

#### Sicherheit und Kompatibilität

- **Aktualisierung der Kardinalintegration für die Inhaltssicherheitsrichtlinie für 3-D Secure**

  Die Content Security Policy (CSP) wurde aktualisiert und unterstützt nun die neuesten Anforderungen an die Integration von Cardinal (3-D Secure). Dadurch wird sichergestellt, dass alle Kardinal-gehosteten Skripte, iFrames und zugehörigen Ressourcen, die während sicherer 3D-Flüsse verwendet werden, vom CSP des Browsers zugelassen werden, um blockierte Anfragen und fehlerhafte Challenge- oder Verifizierungserlebnisse zu verhindern.

  _BUNDLE-3485_

- Kompatibilität der **Braintree-Zahlungserweiterung mit PHP 8.5**

  Die Braintree-Zahlungserweiterung wurde aktualisiert, um die PHP 8.5-Laufzeitumgebung zu unterstützen und gleichzeitig die Kompatibilität mit PHP 8.4 zu gewährleisten.

  _BUNDLE-3493_

### Plattform und Infrastruktur

#### OpenSearch 3.x-Unterstützung

Adobe Commerce 2.4.9-beta1 ist vollständig kompatibel mit OpenSearch 3.x. Dieses Update ermöglicht es Händlern, von verbesserter Leistung, Sicherheit und langfristigem Support zu profitieren und gleichzeitig die Abwärtskompatibilität mit OpenSearch 2.x zu wahren.

_AC-11846_

#### Vollständige Unterstützung von Valkey 8.x

Adobe Commerce 2.4.9-beta1 bietet umfassende Unterstützung für Valkey 8.x als Redis-kompatibles Cache-Backend, einschließlich vollständiger CLI-Befehlsparität mit Redis. Die Admin- und Cloud-Konfigurationsoptionen wurden für eine nahtlose Einrichtung von Valley aktualisiert. Diese Unterstützung basiert auf dem Ende der Unterstützung und den Lizenzänderungen für Redis 7.2 und bietet Händlern eine zuverlässige, vollständig unterstützte Alternative zu Redis in den Commerce-Release-Zeilen 2.4.5 bis 2.4.9-beta1.

_AC-14103, AC-14604_

#### Die Apache ActiveMQ Artemis-Unterstützung ersetzt RabbitMQ

Es wurde Unterstützung für Apache ActiveMQ Artemis als strategische Alternative zu RabbitMQ hinzugefügt, die durch Support-End-Risiken im Zusammenhang mit RabbitMQ 4 bedingt ist. ActiveMQ Artemis wird jetzt in den Commerce-Release-Zeilen 2.4.6 bis 2.4.9-beta1 vollständig unterstützt, einschließlich Adobe Commerce Cloud mit AWS ActiveMQ für Cloud-native Bereitstellungen, und unterstützt die STOMP-Konfiguration für Warteschlangennutzer und -herausgeber. Bestehende RabbitMQ 4-Installationen bleiben für Händler kompatibel, die weiterhin ihren aktuellen Nachrichtenwarteschlangendienst nutzen möchten.

_AC-14558_

### PHP und Composer

#### PHP 8.5-Kompatibilität

Ab Adobe Commerce 2.4.9-beta1 ist die Plattform vollständig mit PHP 8.5 kompatibel, wobei PHP 8.4 weiterhin unterstützt wird und PHP 8.3 für reine Upgrade-Szenarien möglich ist. Diese Arbeit modernisiert den Kern-Code, die Abhängigkeiten und die Tools, damit Händler vor dem Ende der Unterstützung von PHP 8.4 sicher zu neueren PHP-Versionen wechseln können, um die PCI-Konformität und den langfristigen Zustand der Plattform aufrechtzuerhalten.

_AC-15615_

#### PHP 8.2-Unterstützung entfernt

Ab Adobe Commerce 2.4.9-beta1 wird PHP 8.2 nicht mehr unterstützt. Die Plattform zielt nun auf PHP 8.3 und höher ab, mit Kern-Code, Abhängigkeiten und Tools, die aktualisiert wurden, um sauber und zuverlässig auf PHP 8.4 und 8.5 laufen zu können.

_AC-15758_

#### Kompatibilität mit Composer 2.9 überprüft

Adobe Commerce 2.4.9-beta1 ist vollständig kompatibel mit Composer 2.x, einschließlich Composer 2.9. Diese Ausrichtung bewahrt die Abwärtskompatibilität und sorgt für ein stabiles Build- und Bereitstellungserlebnis für Händler und Entwickler, die die neuesten Composer-Versionen verwenden.

_AC-14481_

### Framework

#### Aktualisierung der Sicherheit und Kompatibilität des JWT-Frameworks

Im Rahmen der kontinuierlichen Sicherheitsüberprüfung der Plattform wurde die Abhängigkeit vom Web-Token-JWT-Framework evaluiert und auf die neueste Hauptversion aktualisiert, um für die Zukunft Kompatibilität und strenge Sicherheitsstandards für die Token-basierte Authentifizierung über Commerce-Integrationen hinweg sicherzustellen. Vorhandene Funktionen bleiben vollständig erhalten.

_AC-13209 - [GitHub-Code-](https://github.com/magento/magento2/commit/2bac8114) - [GitHub-Code-](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce Functional Testing Framework aktualisiert auf Symfony LTS-Abhängigkeiten

Das Adobe Commerce Functional Testing Framework (MFTF) wurde aktualisiert, um die neuesten Symfony LTS-Abhängigkeiten, einschließlich symfony/config, zu verwenden, wie es für die Aktualisierung des Web-Token-/JWT-Frameworks erforderlich ist. Dies löst frühere Abhängigkeitskonflikte und stellt einen stabilen, unterstützten Stack für Funktionstests sicher.

_AC-13244_

#### Native PHP OAuth-Funktionen ersetzen die Drittanbieter-Bibliothek

Die `carlos-mg89/oauth`-Bibliothek von Drittanbietern wurde durch native PHP-OAuth-Funktionen ersetzt, wodurch die Sicherheit verbessert, externe Abhängigkeiten reduziert und die Plattformstabilität verbessert wurden.

_AC-14075 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7b8064f7)_

#### Die Komponente Symfony Cache ersetzt Zend_Cache

Ab Adobe Commerce 2.4.9-beta1 wurde die veraltete Zend_Cache-Komponente durch die Symfony Cache-Komponente ersetzt. Diese Aktualisierung verbessert die Cache-Leistung und die Wartbarkeit und stellt eine langfristige Kompatibilität mit PHP 8.x und zukünftigen Plattformaktualisierungen sicher. Vorhandene Cache-Backends und Cache-Management-Befehle werden weiterhin vollständig unterstützt, ohne dass Änderungen für aktuelle Integrationen erforderlich sind.

_AC-15823_

#### WYSIWYG Editor von TinyMCE zu HugeRTE migriert

Aufgrund des Auslaufens der Unterstützung für TinyMCE 5 und 6 und der Lizenzierungsinkompatibilitäten mit TinyMCE 7 wurde der Adobe Commerce WYSIWYG Editor in den Open-Source-Editor [HugeRTE](https://hugerte.org/) migriert. Diese Migration stellt sicher, dass Adobe Commerce weiterhin mit der Open-Source-Lizenzierung konform ist, bekannte TinyMCE 6-Schwachstellen vermeidet und Händlern und Entwicklern ein modernes, unterstütztes Bearbeitungserlebnis bietet.

_AC-14568_

#### Native MVC-Implementierung ersetzt Laminas MVC

Adobe Commerce hat eine native MVC-Implementierung eingeführt, die das alte Laminas-MVC ersetzt, um die langfristige Kompatibilität und Stabilität über PHP 8.5 hinaus sicherzustellen. Diese Änderung stärkt die Leistung, reduziert externe Abhängigkeiten und bietet eine zukunftsfähigere Grundlage für Commerce.

_AC-15160_

#### Offizielle Symfony 7.4 LTS-Unterstützung

Im Rahmen der Adobe Commerce 2.4.9-beta1 Plattformaktualisierungen wurden alle Symfony-Abhängigkeiten auf die neueste Version Symfony LTS 7.4 aktualisiert. Alle benutzerdefinierten Klassen, die Symfony-Kernklassen erweitern, verfügen über aktualisierte Typdeklarationen und Methodensignaturen, die mit den neuesten Symfony-Anforderungen abgestimmt sind. So werden Kompatibilitätsprobleme vermieden und ein reibungsloser Übergang zu den aktualisierten Framework-Komponenten gewährleistet.

_AC-15170 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c127d10b)_

#### Abhängigkeit von Allure PHPUnit auf Version 3 aktualisiert

Die `allure-framework/allure-phpunit`-Abhängigkeit wurde auf Hauptversion 3 aktualisiert, welche die Unterstützung für PHP 8.4 und PHP 8.5 hinzufügt und den Allure-basierten Test-Reporting-Stack modernisiert. Die native Abhängigkeit, die zuvor von älteren Allure PHPUnit-Versionen benötigt wurde, wurde entfernt, wodurch die Einrichtung und Wartung vereinfacht wurde.

_AC-14548 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic-Reporting aktualisiert auf NerdGraph-API

Das Berichtsmodul von New Relic wurde aktualisiert, um die Änderungsverfolgungs-API von New Relic (NerdGraph, GraphQL) zu unterstützen und gleichzeitig die bestehende Integration der REST v2-Bereitstellungsmarkierung vollständig zu erhalten. Die Änderung bietet umfangreichere Bereitstellungsmetadaten, regionale Endpunktunterstützung (USA und EU) und Konfigurierbarkeit durch Admin-Einstellungen, ohne vorhandene Setups zu beschädigen.

_AC-15461_

#### JavaScript-Bibliotheksaktualisierungen

- **Chart.js aktualisiert auf Version 4.5.0**

  Die Diagrammbibliothek Chart.js JavaScript wurde auf Version 4.5.0 aktualisiert, um die Darstellung von Diagrammen zu verbessern, die visuellen Funktionen zu verbessern und Sicherheitslücken im Admin-Dashboard und in den Reporting-Modulen zu beheben.

  _AC-14304, AC-15133 - [GitHub-Code-](https://github.com/magento/magento2/commit/768b4442), [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/657f983e)_

- **Uppy-Datei-Upload-Bibliothek aktualisiert auf Version 4.13.4**

  Die Uppy-Datei-Upload-Bibliothek wurde auf Version 4.13.4 aktualisiert, um die Dateiupload-Funktionen zu verbessern, das Benutzererlebnis zu verbessern und Sicherheitslücken bei der Dateiverarbeitung in der Admin-Oberfläche und den Frontend-Komponenten von Adobe Commerce zu beheben.

  _AC-14307 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery Validate-Bibliothek auf Version 1.21.0 aktualisiert**

  Die jQuery Validate-Bibliothek wurde auf Version 1.21.0 aktualisiert, um die Formularvalidierungsfunktionen zu verbessern, das Benutzererlebnis zu verbessern und eine moderne Browserkompatibilität für alle Adobe Commerce-Formulare sowohl in der Admin- als auch in der Frontend-Benutzeroberfläche sicherzustellen.

  _AC-14403 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery UI-Bibliothek auf Version 1.14.1 aktualisiert**

  Die jQuery UI-Bibliothek wurde auf Version 1.14.1 aktualisiert, um Benutzeroberflächen-Widgets zu verbessern, die Barrierefreiheit zu verbessern und eine moderne Browserkompatibilität für alle Adobe Commerce Admin- und Frontend-Schnittstellenkomponenten sicherzustellen.

  _AC-14417 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/77c589a6)_

- **Less.js-CSS-Präprozessor aktualisiert auf Version 4.2.2**

  Der CSS-Präprozessor von Less.js wurde auf Version 4.2.2 aktualisiert, um die CSS-Kompilierungsleistung zu verbessern, die Syntaxunterstützung zu verbessern und den Design-Build-Prozess für alle Adobe Commerce-Frontend- und Admin-Designs zu modernisieren.

  _AC-14418 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

- **Time Timezone Library auf Version 0.5.43 aktualisiert**

  Die Zeitzonenbibliothek (`moment-timezone-with-data.js`) von Moment wurde auf Version 0.5.43 aktualisiert, um die Zeitzonenbehandlungsfunktionen zu verbessern, Zeitzonendaten mit den neuesten Änderungen der IANA-Zeitzonendatenbank zu aktualisieren und die Genauigkeit der Datums- und Zeitverarbeitung für alle internationalen und Multi-Zeitzonenvorgänge von Adobe Commerce zu verbessern.

  _AC-14419 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

- **Die Dienstprogrammbibliothek Underscore.js wurde auf Version 1.13.7 aktualisiert**

  Die Unterstrich.js-Dienstprogrammbibliothek wurde auf Version 1.13.7 aktualisiert, um die JavaScript-Funktionsprogrammierfunktionen zu verbessern, die Datenmanipulationsleistung zu verbessern und eine moderne Browserkompatibilität für alle Frontend- und Admin-Schnittstellenkomponenten von Adobe Commerce sicherzustellen.

  _AC-14420 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98b2848a)_

### Sicherheit

#### CAPTCHA-Validierung jetzt für REST- und GraphQL-APIs erzwungen

Wenn CAPTCHA (oder reCAPTCHA) für das Formular Konto erstellen aktiviert ist, wird jetzt dieselbe CAPTCHA-Validierung für die Erstellung von Kundenkonten über REST- und GraphQL-APIs erzwungen.

_AC-16245_

#### Verbesserte Leistung bei asynchronen/Massenanfragen

Diese Fehlerbehebung behebt die Leistungseinbußen bei asynchronen Web-API-Massenendpunkten, die nach dem Sicherheits-Patch APSB25-08 eingeführt wurden, und stellt die erwarteten Ausführungszeiten wieder her.

_AC-14078 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9a7352b7)_

#### Vereinfachte Konfiguration der Zwei-Faktor-Authentifizierung

Administratorbenutzer müssen jetzt nur noch einen der aktivierten 2FA-Provider des Händlers (z. B. Google Authenticator oder U2F) konfigurieren, um auf das Admin-Bedienfeld zuzugreifen. Zusätzliche aktivierte Anbieter können bei Bedarf später konfiguriert werden. Wenn zuvor mehrere 2FA-Anbieter aktiviert waren, musste jeder Admin-Benutzer alle aktivierten Anbieter konfigurieren, bevor er sich anmelden konnte. Dies führte zu Reibungen bei Benutzern, die nicht auf alle Faktoren Zugriff hatten.

_AC-8253 - [GitHub-Code-Beitrag](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### Lieferung

#### Migrieren der USPS-Integration zu RESTful-USPS-APIs

Um der angekündigten Einstellung der älteren Web-Tools-APIs durch USPS nachzukommen, hat Adobe Commerce seine USPS-Integration auf die neuen RESTful-USPS-APIs umgestellt.

Wichtige Verbesserungen:

- Unterstützung von zwei APIs: Admin-Benutzer können jetzt über die Konfigurationseinstellungen zwischen der Legacy Web Tools-API und der neuen RESTful USPS-API wählen.
- Authentifizierungs-Upgrade: Verwendet OAuth 2.0 für sicheren API-Zugriff.
- Verbessertes Datenformat: Verwendet JSON anstelle von XML für eine sauberere, effizientere Kommunikation.
- Neue Administratorfelder:
   - Gateway-REST-URL (basierend auf Modus: Entwicklung oder Live)
   - Client-ID und Geheimnis
   - Kontotyp, Kontonummer
   - CRID, MID, Mailer-Identifizierungscode
   - AES/ITN für internationale Sendungen
   - REST-spezifische zulässige Versandmethoden

Diese Migration stellt sicher, dass Adobe Commerce weiterhin die USPS-Standards erfüllt, die Systemzuverlässigkeit verbessert und die Versandintegrationen für Händler zukunftssicher macht.

_AC-13257_

#### Migrieren der DHL-Integration zu MyDHL RESTful-APIs

Die integrierte DHL-Versandintegration unterstützt jetzt MyDHL RESTful-APIs, wobei die Kompatibilität mit der alten DHL Express XML-API erhalten bleibt. Händler können auswählen, welche DHL-API im Admin verwendet werden soll. Sie profitieren von modernen REST-Funktionen, ohne die bestehenden XML-basierten Setups zu beschädigen.

_AC-13258_
