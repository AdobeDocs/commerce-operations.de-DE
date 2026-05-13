---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Adobe Commerce-Highlights (v2.4.9)

## Highlights in Version 2.4.9

Die folgenden Highlights gelten für die Version 2.4.9 von Adobe Commerce.

### REST-API-Änderungen

#### Vererbungskontrolle der REST-API-Produktgalerie auf Store-Ansichtsebene

Wenn ein Produkt über die REST-API in einem Store-Bereich aktualisiert wird, erben Produktbilder und Videos keine Änderungen mehr vom globalen Umfang, wenn `media_gallery_entries` in der Payload weggelassen oder auf `NULL` gesetzt wird. Es ist jetzt auch möglich, die Bereichsvererbung für Produktbilder und Videos über die REST-API wiederherzustellen, indem das entsprechende Feld auf `NULL` festgelegt wird.

Beim Aktualisieren von Produkten über die REST-API auf Store-Ansichtsebene:

- Wenn Sie `media_gallery_entries` auslassen oder auf NULL festlegen, wird jetzt die Vererbung aus dem standardmäßigen/globalen Katalog beibehalten.
- Um die Vererbung für bestimmte Galerieattribute (z. B. `label`, `position`, `disabled`, `video_title`, `video_description`) wiederherzustellen, legen Sie diese Felder im `media_gallery_entries`-Array auf NULL fest.

Diese Änderung stellt sicher, dass Store-Ansichten die standardmäßigen Galeriewerte einfach beibehalten oder wiederherstellen können, um die Verwirrung zu reduzieren und die Galerie-Verwaltung konsistenter zu gestalten.

_ACP2E-4358 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### GraphQL-API-Änderungen

#### `clearCart` GraphQL-Mutation ist jetzt in Magento Open Source verfügbar

Die [clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/)-GraphQL-Mutation ist jetzt für alle Magento Open Source-Benutzer verfügbar. Zuvor war diese Mutation nur in Adobe Commerce zugänglich.

_AC-16683 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4449d914)_

#### Beschreibendere Fehler aufgrund der `applyGiftCardToCart` GraphQL-Mutation

Verbesserte Fehlerbehandlung für die `applyGiftCardToCart`. Die Mutation gibt jetzt bestimmte Fehlermeldungen für Fälle wie abgelaufene oder Null-Saldo-Geschenkkarten zurück, was das Käufererlebnis verbessert. Darüber hinaus verhindert das Backend, dass zusätzliche Geschenkkarten auf Bestellungen angewendet werden, die bereits kostenlos sind.

_LYNX-787_

#### Die neue `clearWishlist` GraphQL-Mutation entfernt alle Elemente der Wunschliste auf einmal

Es wurde eine `clearWishlist` Mutation hinzugefügt, die in einem einzigen Aufruf alle Elemente aus einer Wunschliste entfernt.

_LYNX-790_

#### Neue `exchangeExternalCustomerToken` GraphQL-Mutation für integrationsbasierte Authentifizierung

Es wurde eine neue `exchangeExternalCustomerToken` GraphQL-Mutation eingeführt, die Benutzende über ein Integrations-Token authentifiziert und sowohl das Kunden-Token als auch die zugehörigen Kundendaten zurückgibt.

_LYNX-815_


#### Neue GraphQL-Abfragen geben angewendete Kundengruppen-, Segment- und Warenkorbregel-IDs zurück

Neue GraphQL-Abfragen geben die kodierte `uid` der angewendeten Kundengruppe, Kundensegmente und Warenkorbregeln zurück.

_LYNX-867_

#### Geschenkoptionen werden automatisch gelöscht, wenn der Warenkorb geleert wird

Es wurde ein Problem behoben, bei dem Geschenkoptionen auf einem leeren Warenkorb beibehalten wurden, nachdem alle Artikel entfernt wurden. Geschenk-Optionen werden jetzt automatisch gelöscht, wenn der Warenkorb geleert wird, was dem vorhandenen Verhalten für Coupons entspricht.

_LYNX-786_

#### Geschenkoptionen werden bei der Kombination von Gast- und Kundenwagen konsistent zusammengeführt

Verbesserte Handhabung von Geschenkoptionen bei Zusammenführungen des Warenkorbs, um ein konsistenteres Benutzererlebnis zu gewährleisten. Geschenkoptionen folgen jetzt einer priorisierten Zusammenführungslogik, um unbeabsichtigte Überschreibungen zu verhindern, wenn sich ein Gastbenutzer anmeldet und sein Warenkorb mit einem vorhandenen Kundenwarenkorb zusammengeführt wird.

_LYNX-788_

#### Neues `grand_total_excl_tax` in der GraphQL-`OrderTotal`

Der GraphQL-Bestellantwort wurde das neue Feld `OrderTotal.grand_total_excl_tax` hinzugefügt. Dieses Feld gibt den Gesamtbetrag ohne Steuern an, was den direkten Zugriff auf die Gesamtsumme ohne Steuern über die API erleichtert.

Vorteile:

- Einfaches Abrufen der Gesamtsumme ohne MwSt. für jede Bestellung über GraphQL.
- Vereinfacht die Integration mit externen Systemen, für die steuerliche Gesamtwerte erforderlich sind.
- Verringert den Bedarf an benutzerdefinierten Berechnungen auf der Client-Seite.

_LYNX-892_

#### Historische Bestellungen zeigen Details zu Produkten an, die jetzt nicht mehr vorrätig sind

Historische Bestellungen zeigen jetzt vollständige Produktdetails für Zeileneinträge an, selbst wenn das Produkt nicht mehr vorrätig ist, sodass Kunden und Händler einen vollständigen Datensatz darüber behalten, was gekauft wurde.

_LYNX-913_

#### Die reCAPTCHA-Validierung wurde zu `updateCustomer`-, `updateCustomerV2`- und `contactUs` GraphQL-Mutationen hinzugefügt.

Wenn reCAPTCHA für die entsprechenden Storefront-Formulare aktiviert ist, erzwingen die `updateCustomer`-, `updateCustomerV2`- und `contactUs` GraphQL-Mutationen jetzt dieselbe Validierung, um einen automatisierten Missbrauch über die API zu verhindern.

_LYNX-941_

#### Die reCAPTCHA-Validierung wurde zur `applyCouponsToCart` GraphQL-Mutation hinzugefügt.

Wenn reCAPTCHA für das Couponformular aktiviert ist, erzwingt die `applyCouponsToCart` GraphQL-Mutation jetzt dieselbe Validierung, wodurch die Auflistung des Couponcodes über die API verhindert wird.

_LYNX-942_

#### Das Feld für die B2B-GraphQL-API-`customer_id` wurde wiederhergestellt und wird vollständig unterstützt

Das `customer_id` in der B2B-GraphQL-API wird wiederhergestellt und gibt jetzt den richtigen Wert in Abfragen und Mutationen des Unternehmensmanagements zurück. Zuvor wurde das Feld veraltet und `null` zurückgegeben, was seine Nützlichkeit für B2B-Integrationen einschränkte.

_LYNX-955_

### Admin-Benutzeroberfläche

#### Aktionsmenü für das Katalogpreisregeln-Raster

Das **Katalogpreisregeln** im Commerce Admin enthält jetzt ein Menü **Aktionen**, über das Händler mehrere Regeln gleichzeitig aktivieren, deaktivieren oder löschen können. Dadurch wird die Verwaltung der Katalogpreisregeln mit den vorhandenen Massenaktionen in Einklang gebracht, die für **Warenkorbpreisregeln** verfügbar sind, wodurch der Zeitaufwand für die Verwaltung großer Regelsätze erheblich reduziert wird.

_AC-13916_

#### Mobile-Vorschau für Inhalts-Staging

Die Staging-Vorschau in Admin rendert jetzt die Browser-simulierten Vorschauen für mobile Geräte genau, sodass Händler sehen können, wie ein gestaffeltes Update auf einem mobilen Gerät angezeigt wird, bevor es live geschaltet wird.

_ACP2E-3397 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Die neue Admin-Konfiguration steuert das Zusammenführungsverhalten von Gast und Warenkorb beim Anmelden

Händler können jetzt auswählen, wie die Artikel im Warenkorb zusammengeführt werden, wenn sich ein Gast anmeldet und bereits über einen Warenkorb verfügt:

- **Gastpriorität** - Verwenden Sie die Menge des Gästekorbs.
- **Kundenpriorität** - Verwenden Sie die Menge des Kundenwagens.
- **Mengen zusammenführen** (Standard) - Beide Mengen addieren.

Konfigurieren Sie dieses Verhalten unter **Stores** > **Configuration** > **Sales** > **Checkout** unter **Warenkorb-Zusammenführungsvoreinstellung**. Die Einstellung gilt für alle Produkttypen, sodass Händler die volle Kontrolle darüber haben, wie Gäste- und Kundenwagen bei der Anmeldung kombiniert werden.

_LYNX-889_

### Braintree

#### Express-Checkout

- **Werbeangebote im Google Pay Express-Lohnbogen**

  Das Google Pay Express-Zahlungsblatt unterstützt jetzt Promo- und Angebotscodes. Kundinnen und Kunden können Commerce-Warenkorbaktionen direkt in der Google-Zahlungsliste beantragen, anzeigen und entfernen, sodass Kundinnen und Kunden mit Express-Checkout die gleichen Rabatte und Anreize erhalten wie normale Checkout-Abläufe.

  _BUNDLE-3476_

- **Werbeangebote im Apple Pay Express-Lohnbogen**

  Das Apple Pay Express-Zahlungsblatt unterstützt jetzt Promo- und Angebotscodes. Kundinnen und Kunden können einen Gutschein direkt in der Apple-Zahlungsanzeige beantragen, sodass Benutzer, die einen Express-Checkout durchführen, von denselben Rabatten und Kampagnen profitieren wie normale Checkout-Abläufe.

  _BUNDLE-3477_

- **Apple Pay für Chrome und Firefox**

  Apple Pay kann jetzt auf Chrome und Firefox verwendet werden, nicht nur in Safari. Wenn Apple Pay Express aktiviert ist, sind die Pay-Buttons von Apple auf den Seiten „PDP“, „Mini-Warenkorb“, „Warenkorb“ und „Checkout“ verfügbar, und Kunden können die Zahlung abschließen, indem sie einen Code mit ihrer iPhone scannen.

  _BUNDLE-3478_

- **Server-seitiger Versandrückruf für PayPal Express**

  Der Versandrückruf PayPal Express wurde von Client- auf Server-Seite verschoben. Dies bietet dynamische Versandmethoden, Echtzeit-Kostenberechnungen und genaue Details auf Warenkorbebene direkt im PayPal-Modal, wodurch die Zuverlässigkeit verbessert wird und die Grundlage für zukünftige Funktionen wie die Unterstützung von Kontaktmodulen, App-Switch-Flüsse und Venmo Express gelegt wird.

  _BUNDLE-3479_

- **PayPal-Kontaktmodul für U.S. Händler-Express-Checkout**

  Für US-Händler wird ein neues PayPal-Kontaktmodul eingeführt. Wenn diese Option aktiviert ist, können Käufer, die PayPal Express verwenden, die E-Mail-Adresse und Telefonnummer, die mit dem Händler geteilt wurde, direkt innerhalb des PayPal-Modals während der Express-Flüsse (PDP, Mini-Warenkorb, Warenkorb, Checkout-Express) anzeigen und aktualisieren. Die ausgewählten Kontaktdaten werden dann in der Commerce-Bestellung gespeichert.

  _BUNDLE-3480_

#### Zahlungsmethoden

- **ELO-Kartenunterstützung für Braintree-Zahlungen**

  Unterstützung für den ELO-Kartentyp in Braintree Payments wurde hinzugefügt. Administratoren können ELO in der Kreditkartenkonfiguration aktivieren, und Kunden können an der Kasse mit ELO-Karten bezahlen.

  _BUNDLE-3464_

- **BLIK-Lokalzahlungsmethode für polnische Käufer**

  BLIK wurde als neue lokale Zahlungsmethode für polnische Käufer hinzugefügt. Dies ermöglicht sichere, bankbasierte BLIK-Zahlungen innerhalb des bestehenden Flusses der Braintree Local Payment Methods (LPM) und verbessert den Checkout-Komfort und die Konversion für Kunden in Polen.

  _BUNDLE-3481_

- **Zahlung auf Rechnung — neue BNPL-Zahlungsmethode für Deutschland**

  [!DNL Pay Upon Invoice] als neue lokale Zahlungsmethode für deutsche Käufer hinzugefügt. [!DNL Pay Upon Invoice] ist eine Option „Jetzt kaufen, später bezahlen“ (BNPL) von PayPal und Ratepay („Rechnungskauf mit Ratepay„), mit der Kunden Waren zuerst erhalten und die Rechnung innerhalb von 30 Tagen bezahlen können, ohne ein PayPal-Konto zu benötigen. Da es sich nicht um eine sofortige Zahlung handelt, wird der Abschluss von Bestellungen durch einen Server-seitigen Webhook von PayPal gesteuert.

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

#### Schnelleres Laden von Seiten in Speichern mit mehreren Designs und mehreren Gebietsschemata nach SRI-Hash-Speicherrefaktor

Der SRI-Hash-Speicher generiert jetzt separate Dateien pro Bereich, Design und Gebietsschema anstelle einer einzigen großen `sri-hashes.json`. Durch diese Änderung wird sichergestellt, dass für jede Seite nur die relevante Hash-Datei geladen wird, was die Seitenladezeiten verbessert und die Speichernutzung in Stores mit mehreren Designs oder Gebietsschemata reduziert.

_AC-16113 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/bc83cd2c)_

#### Kompatibilität mit PHPUnit 12 hinzufügen

Die Adobe Commerce Composer-Abhängigkeit wird auf `phpunit/phpunit` 12.x aktualisiert. Alle Tests werden aktualisiert, um die Kompatibilität zu gewährleisten, die Sicherheit zu verbessern und die Anpassung an die neuesten PHPUnit-Funktionen zu verbessern. Dieses Upgrade hält Adobe Commerce für zukünftige PHP- und PHPUnit-Versionen bereit.

_AC-14808_

#### Hinzufügen der Kompatibilität mit RabbitMQ 4.2

RabbitMQ 4.2 ist jetzt ein unterstützter Nachrichtenbroker. Dieses Update ist ein kurzfristiger Kompatibilitätspfad, der es Händlern, die auf das AMQP-Protokoll angewiesen sind, ermöglicht, RabbitMQ vor dem Ende der Unterstützung für RabbitMQ 4.1 im Februar 2026 weiter zu verwenden, ohne sofort auf STOMP migrieren zu müssen. Verwenden Sie für langfristige Bereitstellungen Apache ActiveMQ Artemis als langfristigen Ersatz für RabbitMQ.

_AC-16117_

#### Apache ActiveMQ Artemis ist der langfristige Ersatz für RabbitMQ

Apache ActiveMQ Artemis ist der empfohlene Langzeit-Message-Broker für Adobe Commerce, basierend auf Support-End-Risiken im Zusammenhang mit RabbitMQ 4.1. ActiveMQ Artemis wird in allen Commerce-Versionen 2.4.6 bis 2.4.9 vollständig unterstützt. In Adobe Commerce Cloud wird es als AWS ActiveMQ für Cloud-native Bereitstellungen bereitgestellt. Sowohl Warteschlangenverbraucher als auch Herausgeber können für die Verwendung von STOMP konfiguriert werden.


Bestehende RabbitMQ 4-Installationen bleiben für Händler kompatibel, die ihren aktuellen Nachrichtenwarteschlangendienst kurzfristig weiterhin nutzen möchten - siehe [Hinzufügen der Kompatibilität mit RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42) oben. Planen Sie eine Migration zu ActiveMQ Artemis für eine langfristige Unterstützung.

_AC-14558_

#### Unterstützung für Valkey 9.x hinzufügen

Adobe Commerce 2.4.9 erweitert die Unterstützung für Valkey als Redis-kompatibles Cache-Backend:

- **Valkey 9.x** - Umfassende Unterstützung, die in Adobe Commerce 2.4.9 eingeführt wurde, einschließlich vollständiger CLI-Befehlsparität mit Redis und aktualisierter Admin- und Cloud-Konfigurationsoptionen für eine nahtlose Einrichtung. Diese Arbeit basiert auf dem Ende der Unterstützung und Lizenzänderungen für Redis 7.2 und bietet Händlern eine zuverlässige, vollständig unterstützte Alternative zu Redis.

_AC-14103, AC-14604, AC-16122_

#### Unterstützung für OpenSearch 3.x hinzufügen

Adobe Commerce 2.4.9 ist vollständig kompatibel mit OpenSearch 3.x, mit der neuesten Nebenversion jetzt die empfohlene Suchmaschine. Händler profitieren von einer verbesserten Leistung, Sicherheit und langfristigem Support, während die Abwärtskompatibilität mit OpenSearch 2.x beibehalten wird.

_AC-11846, AC-16403_

#### Unterstützung für MariaDB 11.8 und 12.x hinzufügen

MariaDB 11.8 und 12.x werden jetzt als Datenbankversionen unterstützt, sodass Händler die neuesten Versionen einsetzen können, um die SQL-Leistung und die langfristige Plattformstabilität zu verbessern.

_AC-16533_

### PHP und Composer

#### PHP 8.5-Kompatibilität

Adobe Commerce 2.4.9 unterstützt jetzt PHP 8.5 und PHP 8.4, sodass Sie Ihren Store mit den neuesten sicheren und konformen PHP-Versionen ausführen können. Alle Kernfunktionen, gebündelten Erweiterungen (einschließlich Page Builder, B2B, Braintree und mehr) und Adobe SaaS-Services sind mit PHP 8.5 kompatibel.

- PHP 8.5 und 8.4 werden vollständig unterstützt.
- PHP 8.3 ist nur für Upgrade-Zwecke erlaubt (nicht für die Produktion empfohlen).
- Gewährleistet PCI-Compliance und ist zukunftssicher für Ihre Adobe Commerce-Installation.

_AC-15615_

#### PHP 8.2-Unterstützung entfernt

Ab Adobe Commerce 2.4.9 wird PHP 8.2 nicht mehr unterstützt. Die Plattform zielt nun auf PHP 8.3 und höher ab, mit Kern-Code, Abhängigkeiten und Tools, die aktualisiert wurden, um sauber und zuverlässig auf PHP 8.4 und 8.5 laufen zu können.

_AC-15758_

#### Kompatibilität mit Composer 2.9 überprüft

Adobe Commerce 2.4.9 ist vollständig kompatibel mit Composer 2.x, einschließlich Composer 2.9. Die Abwärtskompatibilität mit früheren Composer 2.x-Versionen bleibt erhalten, sodass Händler und Entwickler, die die neuesten Composer-Versionen verwenden, ein stabiles Build- und Bereitstellungserlebnis haben.

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

Ab Adobe Commerce 2.4.9 wurde die veraltete Zend_Cache-Komponente durch die Symfony Cache-Komponente ersetzt. Diese Aktualisierung verbessert die Cache-Leistung und die Wartbarkeit und stellt eine langfristige Kompatibilität mit PHP 8.x und zukünftigen Plattformaktualisierungen sicher. Vorhandene Cache-Backends und Cache-Management-Befehle werden weiterhin vollständig unterstützt, ohne dass Änderungen für aktuelle Integrationen erforderlich sind.

_AC-15823_

#### WYSIWYG Editor von TinyMCE zu HugeRTE migriert

Aufgrund des Auslaufens der Unterstützung für TinyMCE 5 und 6 und der Lizenzierungsinkompatibilitäten mit TinyMCE 7 wurde der Adobe Commerce WYSIWYG Editor in den Open-Source-Editor [HugeRTE](https://hugerte.org/) migriert. Diese Migration stellt sicher, dass Adobe Commerce weiterhin mit der Open-Source-Lizenzierung konform ist, bekannte TinyMCE 6-Schwachstellen vermeidet und Händlern und Entwicklern ein modernes, unterstütztes Bearbeitungserlebnis bietet.

_AC-14568_

#### Native MVC-Implementierung ersetzt Laminas MVC

Adobe Commerce hat eine native MVC-Implementierung eingeführt, die das alte Laminas-MVC ersetzt, um die langfristige Kompatibilität und Stabilität über PHP 8.5 hinaus sicherzustellen. Diese Änderung stärkt die Leistung, reduziert externe Abhängigkeiten und bietet eine zukunftsfähigere Grundlage für Commerce.

_AC-15160_

#### Offizielle Symfony 7.4 LTS-Unterstützung

Im Rahmen der Plattformaktualisierungen von Adobe Commerce 2.4.9 wurden alle Abhängigkeiten von Symfony auf die neueste Version Symfony LTS 7.4 aktualisiert. Alle benutzerdefinierten Klassen, die Symfony-Kernklassen erweitern, verfügen über aktualisierte Typdeklarationen und Methodensignaturen, die mit den neuesten Symfony-Anforderungen abgestimmt sind. So werden Kompatibilitätsprobleme vermieden und ein reibungsloser Übergang zu den aktualisierten Framework-Komponenten gewährleistet.

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

Administratorbenutzer müssen jetzt nur noch einen der aktivierten 2FA-Provider des Händlers (z. B. Google Authenticator oder U2F) konfigurieren, um auf das Admin-Bedienfeld zuzugreifen. Zusätzliche aktivierte Anbieter können bei Bedarf später konfiguriert werden. Als zuvor mehrere 2FA-Provider aktiviert waren, musste jeder Admin-Benutzer alle konfigurieren, bevor er sich anmelden konnte, was zu Reibungen bei Benutzern führte, die nicht auf jeden Provider Zugriff hatten.

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
