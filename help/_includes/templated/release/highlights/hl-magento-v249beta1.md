---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Magento Open Source-Highlights (v2.4.9-beta1)

## Highlights in v2.4.9-beta1

Die folgenden Highlights gelten für die Magento Open Source-Version 2.4.9-beta1.

### APIs

#### Hinzufügen der Möglichkeit, die Vererbung der Produktgalerie in der REST-API beizubehalten, wenn ein Produkt auf Store-Ansichtsebene aktualisiert wird

Die Aktualisierung eines Produkts über die REST-API in einem Store-Bereich führt nicht mehr dazu, dass Produktbilder und Videos Änderungen vom globalen Bereich übernehmen, wenn media_gallery_entries in der Payload weggelassen oder auf NULL gesetzt wird, um Änderungen in der Produktgalerie in diesem Bereich zu verhindern. Darüber hinaus ist es jetzt möglich, die Bereichsvererbung für Produktbilder und Videos über die REST-API wiederherzustellen, indem das entsprechende Feld auf NULL festgelegt wird

_ACP2E-4358 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Framework

#### Untersuchen der neuesten Hauptversion des Web-Token/JWT-Frameworks

Im Rahmen der kontinuierlichen Sicherheitsüberprüfung haben wir die neueste Hauptversion des JWT-Frameworks evaluiert, um die zukünftige Kompatibilität sicherzustellen und starke Sicherheitsstandards aufrechtzuerhalten. In dieser Version gibt es keine Auswirkungen auf die vorhandene Funktionalität.

_AC-13209 - [GitHub-Code-](https://github.com/magento/magento2/commit/2bac8114) - [GitHub-Code-](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/33b81f28)_

#### Ersetzen Sie Carlos-mg89/oauth durch PHP Native Funktionen

Die Drittanbieter-Bibliothek „carlos-mg89/oauth“ wurde durch native PHP-OAuth-Funktionen ersetzt, um die Sicherheit zu verbessern, externe Abhängigkeiten zu reduzieren und die Plattformstabilität zu verbessern.

_AC-14075 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7b8064f7)_

#### Untersuchen der neuesten Version von chart.js

Die Diagrammbibliothek Chart.js von JavaScript wurde auf die neueste Version 4.4.8 aktualisiert, um die Leistung des Diagrammrenderings zu verbessern, die visuellen Funktionen zu verbessern und Sicherheitslücken im Admin-Dashboard und in den Reporting-Modulen zu beheben.

_AC-14304 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/768b4442)_

#### Untersuchen Sie die neueste Version von jQuery/Uppy und Uppy

Die Uppy-Datei-Upload-Bibliothek wurde auf Version 4.13.4 aktualisiert, um die Dateiupload-Funktionen zu verbessern, das Benutzererlebnis zu verbessern und Sicherheitslücken bei der Dateiverarbeitung in der Admin-Oberfläche und den Frontend-Komponenten von Adobe Commerce zu beheben.

_AC-14307 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/eb491c05)_

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

#### Aktualisieren Sie allure-framework/allure-phpunit Version auf 3 und entfernen Sie die native Abhängigkeit in 2.4.9-alpha1

In Adobe Commerce 2.4.9 wurde die Abhängigkeit von allure-framework/allure-phpunit auf Hauptversion 3 aktualisiert, was die Unterstützung von PHP 8.4 und PHP 8.5 hinzufügt und unseren Allure-basierten Test-Reporting-Stack modernisiert. Die native Abhängigkeit, die zuvor von älteren Allure PHPUnit-Versionen benötigt wurde, wurde entfernt, wo zutreffend, wodurch die Einrichtung und Wartung vereinfacht wurde.

_AC-14548 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/87b8b34e)_

#### Aktualisieren der chart.js-Abhängigkeit auf die neueste Version

Die Chart.js-Abhängigkeit wird auf die neueste Version 4.5.0 aktualisiert

_AC-15133 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/657f983e)_

#### Offizielle Unterstützung für Symfony 7.4 LTS und PHP 8.5 in Adobe Commerce 2.4.9 hinzugefügt

Im Rahmen der Adobe Commerce 2.4.9 Plattformaktualisierungen wurden alle Symfony-Abhängigkeiten, die vom magento/composer-Paket verwendet werden, auf die neuesten Symfony LTS 7.4 Versionen aktualisiert. Dadurch wird das Composer-Tool von Commerce an der aktuellen Symfony LTS-Linie ausgerichtet und frühere Abhängigkeitsbeschränkungen für ältere Symfony-Versionen werden aufgehoben. Darüber hinaus haben alle benutzerdefinierten Klassen, die Symfony-Kernklassen erweitern, Typdeklarationen und Methodensignaturen aktualisiert, die mit den neuesten Symfony-Anforderungen abgestimmt sind, bevor sie auf Adobe Commerce 2.4.9 aktualisiert werden. Dadurch werden Kompatibilitätsprobleme vermieden und ein reibungsloser Übergang zu den aktualisierten Framework-Komponenten sichergestellt.

_AC-15170 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c127d10b)_

### Sonstige

#### Captcha / reCaptha funktioniert nicht für API / GraphQL

Wenn in Adobe Commerce 2.4.9 CAPTCHA (oder reCAPTCHA) für das Formular Konto erstellen aktiviert ist, wird jetzt dieselbe CAPTCHA-Validierung für die Erstellung von Kundenkonten über REST- und GraphQL-APIs erzwungen.

_AC-16245 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd7f30ee)_

### Sicherheit

#### Leistung bei asynchronen/Massenanfragen verbessern

Behebung der Leistungsbeeinträchtigung bei asynchronen Massenwebendpunkten, die nach dem APSB25-08-Sicherheits-Patch eingeführt wurden, was zu verlängerten Ausführungszeiten führte.

_AC-14078 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9a7352b7)_

#### Pro Benutzer muss nur ein aktivierter 2FA-Provider konfiguriert werden

Administratorbenutzer müssen jetzt nur noch einen der aktivierten 2FA-Provider des Händlers (z. B. Google Authenticator oder U2F) konfigurieren, um auf das Admin-Bedienfeld zuzugreifen. Zusätzliche aktivierte Anbieter können bei Bedarf später konfiguriert werden. Wenn zuvor mehrere 2FA-Anbieter aktiviert waren (z. B. Google Authenticator und U2F), musste jeder Admin-Benutzer alle aktivierten Anbieter konfigurieren, bevor er sich anmelden konnte. Dies führte zu Spannungen für Benutzer, die nicht auf alle Faktoren Zugriff hatten (wie z. B. einen Hardware-Schlüssel für U2F).

_AC-8253 - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/71e7936b)_

### Staging und Vorschau

#### [Funktionsanfrage] Vorschau der Inhalts-Staging-Umgebung in der Ansicht für Mobilgeräte

Die Staging-Vorschaufunktion im Admin-Bedienfeld ermöglicht jetzt die genaue Darstellung der Browser-simulierten Mobile-Device-Vorschauen und bietet eine visuelle Darstellung, wie die Staging-Aktualisierung auf einem mobilen Gerät angezeigt wird.

_ACP2E-3397 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_
