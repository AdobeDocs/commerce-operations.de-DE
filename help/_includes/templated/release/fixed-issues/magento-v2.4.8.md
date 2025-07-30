---
source-git-commit: 1f377ab6e4dcdd2d350366f3889b8befd233474b
workflow-type: tm+mt
source-wordcount: '25720'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.8)

## Highlights

Die folgenden 31 Highlights gelten für die Version 2.4.8 von Magento Open Source.

### Framework

#### Aktualisieren des League/Flysystem Composer-Abhängigkeiten auf die neueste Version

Aktualisieren Sie die Abhängigkeiten von 2.x League/Flysystem Composer auf die neueste Version 3.x.

_AC-10721 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/91cb4d46>)_

#### Untersuchen Sie die neuesten Versionen von php-amqplib/php-amqplib

Die neueste Version php-amqplib/php-amqplib :^3.x wurde aktualisiert

_AC-11673 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### jQuery/FileUploader-CSS-Bereinigung nach der Migration zur Uploy-Bibliothek

jQuery/fileUploader-Bibliothek wurde entfernt, da sie in die Uppy-Bibliothek migriert wurde.

_AC-11911 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/7cabfb46>)_

#### Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für Magento CE

_AC-11995 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Bereinigung des ExtJs-Ordners nach der Migration zur jsTree-Bibliothek

Der extJs-Ordner wurde entfernt, da die zugehörige Funktion zu jsTree migriert wurde.

_AC-12015 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/7cabfb46>)_

#### Upgrade der Monolog-/Monolog-Systemabhängigkeit auf die neueste Hauptversion

Das System wurde aktualisiert, um die neueste Hauptversion der Bibliothek „monolog/monolog:^3.x“ zu verwenden, wodurch Kompatibilität und verbesserte Leistung gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek „monolog/monolog“, was zu potenziellen Problemen und Einschränkungen hätte führen können.

_AC-12022 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### Aktualisieren Sie die Abhängigkeit wikimedia/less.php auf die neueste Hauptversion

Das System wurde aktualisiert, um die neueste Hauptversion 5.x der Bibliothek &quot;wikimedia/less.php&quot; zu verwenden, wodurch Kompatibilität und aktuelle Funktionen gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek, was zu Sicherheitsproblemen hätte führen können.

_AC-12023 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### Upgrade von jQuery/Validate Library Dependency auf die neueste Nebenversion

Upgrade von jQuery/Validate Library Dependency auf die neueste Nebenversion 1.20.0

_AC-12024 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### Aktualisieren der Systemabhängigkeit von moment.js auf die neueste Nebenversion

Aktualisieren der Systemabhängigkeit von moment.js auf die neueste Nebenversion 2.30.1

_AC-12025 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für EE

_AC-12032 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für B2B

_AC-12034 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für Bundle-Erweiterungen

_AC-12074 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Kompatibilität mit MariaDB 11.4 LTS für CE hinzufügen

MariaDB 11.4-Unterstützung mit Adobe Commerce und -Erweiterungen hinzugefügt

_AC-12085 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Abonnentenoptimierung - PhpUnit10

_AC-12165 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/90e25b6b>)_

#### Unterstützen Sie weitere Verbindungsversuche für Redis-Sitzung und kompatibel mit colinmollenhour/php-redis-session-abstract v2.0.0

Aktualisierte neueste Version von colinmollenhour/php-redis-session-abstract v2.0.0, kompatibel mit Adobe Commerce

_AC-12267 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Untersuchung der Fehler bei Automatisierungstests mit MySQL 8.4 LTS

_AC-12576 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Kompatibilität mit MariaDB 11.4 LTS for EE hinzufügen

MariaDB 11.4-Unterstützung mit Adobe Commerce und -Erweiterungen hinzugefügt

_AC-12595 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Aktualisieren der Laminas Composer-Abhängigkeiten auf die neueste Version

Das System unterstützt jetzt die neuesten Versionen von Laminas Composer-Abhängigkeiten:
laminas/laminas-serviceManager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
Gewährleistung der Kompatibilität und aktuellen Funktionalität. Zuvor konnte eine Aktualisierung auf die neuesten Versionen dieser Abhängigkeiten zu Problemen mit der Abwärtskompatibilität und Testfehlern führen.

_AC-12715 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Untersuchen des Modultest-Fehlers aufgrund einer Aktualisierung des phpUnit-Patches während des Komponenten-Upgrades

_AC-12823 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### [Teil 1] - Aktualisieren aller js-Bibliothek und npm-Abhängigkeiten mit der neuesten verfügbaren Version

Die Unterstützung der Composer-Version beschränkte sich auf die Composer-Version 2.2.x. Jetzt wurde die Unterstützung auch auf Version 2.4.x erweitert.

_AC-13076 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/19844aa0>)_

### Reihenfolge

#### [Funktionsanfrage] Der Kunde schlägt vor, dass die Schaltfläche „Kommentar einreichen“ auf der Seite „Bestelldetails“ verwirrend ist und in etwas Anderes geändert werden sollte

Um die Verwirrung zu minimieren, wurde die Beschriftung der Schaltfläche „Kommentar übermitteln“ auf der Seite mit den Bestelldetails in „Aktualisieren“ geändert.

_ACP2E-2709 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/488c1034>)_

### Sonstige

#### Wenn eine neue Version von Adobe Commerce installiert wird, werden festgelegte Indexer im Status Bereit angezeigt

Nach der Installation von Magento muss der Indexerstatus standardmäßig im Status *Bereit* stehen.

_AC-11420 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/71432aeb>)_

#### Legen Sie in der bestehenden Magento-Installation bei der Installation des Indexermoduls eines Drittanbieters Indexer standardmäßig in der Zeitplanung für die Aktualisierung fest.

Alle neuen Indexer befinden sich standardmäßig im Modus [Nach Zeitplan aktualisieren]. Zuvor war der Standardmodus &quot;[ beim Speichern]. Dasselbe gilt auch für benutzerdefinierte Indexer.

_AC-11421 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/71432aeb>)_

#### Die Optionen für Elasticsearch 7 und 8 sollten in der Admin-Konfiguration als veraltet gekennzeichnet sein.

Die Option Elasticsearch 8 in der Admin Config-Option wird mit veraltetem Text angezeigt, um Benutzende darüber zu informieren, dass Elasticsearch 8 nicht mehr als Option empfohlen wird.

_AC-12480 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/0611e750>)_

#### Textnotiz hinzufügen, wenn die Option &quot;Elasticsearch&quot; in der Admin-Konfiguration ausgewählt ist

Es wurde ein Texthinweis hinzugefügt, der Adobe Commerce-Admin-Benutzern mitteilt, dass Elasticsearch von Adobe nicht mehr unterstützt wird und nicht mehr unterstützt wird.

_AC-12481 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/0611e750>)_

#### Patch zur Leistungsverbesserung bei Tierpreisvorgängen in 2.4.8 bereitstellen

Das System ermöglicht jetzt effizientere Massenaktualisierungen der Stufenpreise, ohne dass bei Verwendung des REST-API-Endpunkts &quot;/V1/products/tier-prices“ Leistungsprobleme oder Reaktionsstörungen der Site auftreten. Zuvor konnte die Aktualisierung einer großen Anzahl von Preisen mithilfe dieses Endpunkts zu Leistungsproblemen und mangelnder Reaktionsfähigkeit der Site führen.

_AC-13448 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/082d981c>)_

#### Entfernen Sie alle vertraulichen Adobe-Copyright-Hinweise aus den Magento Open Source-Repositorys

Alle Adobe-Hinweise zum vertraulichen Urheberrecht wurden aus den Open-Source-Repositorys entfernt, sodass nur die reduzierte Form des Adobe-Urheberrechts verwendet wird. Zuvor enthielten einige Dateien in den öffentlichen Repositorys Adobe-Hinweise auf vertrauliche Urheberrechte, die zu Eskalationen in der Community führten.

_AC-13550 - [GitHub-Problem](https://github.com/magento/magento2/issues/39493) - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/4bca5dfe>)_

### UI-Framework

#### [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7

TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu werden. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete

_AC-12726 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7 Page Builder

TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu werden. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete

_AC-12825 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7 - Magento2-infra - Banned Words

TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu werden. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete

_AC-12844 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### Erfordert ein Upgrade von.js auf die neueste Version 2.3.7 (Sicherheitslücke CVE-2024-38999)

Require.js wurde auf die neueste Version 2.3.7 aktualisiert. In der vorherigen Version meldete Sicherheitslücke

_AC-12901 - [GitHub-Code-Beitrag](<https://github.com/magento/magento2/commit/b34c0a75>)_

## Behobene Probleme in Version 2.4.8

Es wurden 497 Probleme im Magento Open Source 2.4.8-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

#### /V1/Transactions REST API gibt einen Fehler zurück, wenn parent_txn_id = txn_id ist

Das System verarbeitet jetzt die Transaktionen des übergeordneten und des untergeordneten Konzepts korrekt, bei denen die übergeordnete Transaktions-ID mit der Transaktions-ID identisch ist, sodass beim Abfragen des /V1/transaction-REST-API-Endpunkts keine Endlosschleife entsteht. Zuvor führte dieses Szenario aufgrund der Überschreitung der maximalen Ausführungszeit zu einem schwerwiegenden Fehler.

_AC-10042 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_

#### [GraphQL] Typproblem in 2.4.7

Das System verarbeitet jetzt Ganzzahlwerte in der GetCustomSelectedOptionAttributes-Funktion beim Ausführen einer GraphQL-Abfrage korrekt, sodass typbezogene Fehler vermieden werden. Zuvor führte das Starten einer GraphQL-Abfrage, die GetCustomSelectedOptionAttributes mit einem ganzzahligen Argument verwendet hat, zu einem Typfehler.

_AC-11878 - [GitHub-Problem](https://github.com/magento/magento2/issues/38662) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38663)_

#### Sonderzeichen in Kategorie url_key (bei Erstellung über REST-API)

Früher In category_url_key ist nach der Fehlerbehebung kein Sonderzeichen vorhanden, sondern es wird ein Sonderzeichen in category_url_key angezeigt.

_AC-3223 - [GitHub-Problem](https://github.com/magento/magento2/issues/35577) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c699c206)_

#### Problem mit der REST-API nach der Aktivierung von 2FA Duo

2FA mit Duo Sicherheitsoption generiert jetzt die richtige Signatur für die Rest-API

_ACP2E-2755 - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/412fa642)_

#### [REST API]: „Standardwert in Store-Ansicht verwenden“ bleibt nach dem Hinzufügen von Konfigurationen für ein konfigurierbares Produkt nicht aktiviert

Das Problem wurde behoben, indem sichergestellt wurde, dass die Datenbankeinträge für die anpassbaren Optionen eines nicht standardmäßigen Speichers korrekt sind. Das Kontrollkästchen für den benutzerdefinierten Store im Abschnitt „Admin > Katalog > Produktbearbeitung > Anpassbare Optionen“ war zuvor aufgrund ungenauer Datenbankeinträge deaktiviert, auch wenn der Optionstitel für den benutzerdefinierten Store genauso geblieben ist wie der Standardstore.

_ACP2E-2927 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3056e9cb)_

#### REST-API kann bei Verwendung von Oauth1 keine Anfragen mit Schrägstrich (/) in der SKU stellen

Vor der Fehlerbehebung waren Sie nicht in der Lage, einen erfolgreichen API-Aufruf für ein Produkt durchzuführen, das &quot;/&quot; in der SKU hatte. Jetzt können Sie eine erfolgreiche API-GET-Anfrage für Produktdetails ausführen, obwohl ihre SKU einen Schrägstrich enthält.

_ACP2E-2969 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_

#### Aktualisierung der Kundenadresse schlägt fehl bei Aktualisierung über REST API, wenn „validateDefaultAddress“ aktiviert ist

Der API-Endpunkt funktioniert jetzt wie beabsichtigt, nachdem das Problem mit dem in der API-Payload fehlenden ID-Schlüssel behoben wurde.

_ACP2E-3079 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_

#### [Cloud] Erstellen der doppelten Website-Preisgruppe in der Preisstufen-API.

Die Preis-Rest-API der Stufe erlaubt es jetzt nicht mehr, die Kundengruppe „Duplizierte Website-Preisgruppe“ zu erstellen.
Zuvor war es möglich, die Kundengruppe „Duplizierte Website-Preisgruppe“ in der Stufen-Preis-API zu erstellen, die die Validierung in Admin während der Produktspeicherung nicht bestehen konnte.

_ACP2E-3091 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_

#### Bestellkommentar mit Status kann nicht über die REST-API hinzugefügt werden

Das Problem wurde behoben, indem die Änderung des Bestellstatus zugelassen wurde, wenn sie nur aus dem aktuellen Status stammt. Zuvor wurde der Bestellstatus nicht berücksichtigt und Änderungen in einem Bestellstatus verhindert, selbst wenn er aus demselben Status stammte.

_ACP2E-3130 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_

#### Asynchroner Vorgang schlägt fehl, wenn die SKU in der Payload fehlt

Asynchrone und Synchronisierungsvorgänge sind zuvor aufgrund von Fehlern bei der Produktspeicherung fehlgeschlagen, wenn die SKU in der Payload fehlt. Nach der Behebung schlagen die Vorgänge der asynchronen und synchronisierten Produkt-REST-API mit der entsprechenden Ausnahmemeldung fehl.

_ACP2E-3236 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

#### [CLOUD] Die Basispreise können nicht mit der REST-API aktualisiert werden (der Wert von „value_id“ in „catalog_product_entity_decimal“ wird nicht korrekt inkrementiert).

Vor dieser Fehlerbehebung wurde beim Aufruf der REST-API /rest/default/V1/products/base-prices die Inkrement-ID fälschlicherweise erhöht, sodass eine Lücke zwischen den Werten entstand. Nach der Fehlerbehebung wird die Inkrement-ID wie erwartet inkrementell erhöht. Außerdem wurde der Wertebereich des Feldes vergrößert.

_ACP2E-3376 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Bestellartikel sind in E-Mails mit Gutschriften für die API POST V1/order/:orderId/fund nicht sichtbar

Vor dieser Fehlerbehebung enthält eine Kundin oder ein Kunde, wenn sie bzw. er eine Gutschrift aus einer API-Anfrage erstellt, die send_email benachrichtigt, bisher kein Produktdetailraster. Nachdem diese Fehlerbehebung angewendet wurde, sendet der Kunde eine Anfrage zur Gutschrift-API und findet die Produktdetails in der E-Mail.

_ACP2E-3460 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_

#### Für Datums- und Uhrzeitattribute mit der Produkt-Rest-API werden keine Standardwerte festgelegt

Standardwerte legen jetzt für Datums- und Datums- und Uhrzeitattribute über die Rest-API korrekt fest

_ACP2E-3486 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

### APIs, Warenkorb und Checkout

#### Kritischer 500-Fehler: Magento\Framework\Webapi\Exception im Zusammenhang mit dem Accept-HTTP-Header

Nach der Behebung besteht kein Problem mit der Angabe des „Accept“-Headers.

_ACP2E-3343 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

### Konto

#### Das Formular „Kundenadresse“ ermöglicht zufälligen Code in den Namensfeldern.

Das System validiert jetzt die Eingabe in den Feldern Vorname und Nachname im Formular der Kundenadresse, wodurch die Verwendung von zufälligem Code verhindert wird. Zuvor ermöglichte das System die Verwendung von zufälligem Code in diesen Feldern ohne einen Fehler auszulösen.

_AC-10782 - [GitHub-Problem](https://github.com/magento/magento2/issues/38331) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38345)_

#### Aktualisierung des Administratorkennworts.

_AC-10886 - [GitHub-Problem](https://github.com/magento/magento2/issues/38352) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4bca5dfe)_

#### Mein Konto Hinzufügen der Adresse stürzt beim Speichern ab

Das System speichert Kundenadressen jetzt korrekt, selbst wenn das Feld Region nicht angezeigt wird, was einen Absturz während des Speichervorgangs verhindert. Zuvor führte der Versuch, eine Adresse ohne angezeigtes Bereichsfeld hinzuzufügen oder zu bearbeiten, zu einem Ausnahmefehler.

_AC-10990 - [GitHub-Problem](https://github.com/magento/magento2/issues/38406) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38407)_

#### Umleitungsschleife bei URLs in Großbuchstaben

Das System konvertiert nun in URLs Großbuchstaben automatisch in Kleinbuchstaben, wodurch eine Umleitungsschleife beim Zugriff auf die Homepage verhindert wird. Zuvor führte die Verwendung von Großbuchstaben in der Secure Base-URL beim Zugriff auf die Homepage zu einer kontinuierlichen Umleitungsschleife.

_AC-11718 - [GitHub-Problem](https://github.com/magento/magento2/issues/38538) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38539)_

#### Mittelname(n) nicht für Gastkonten gespeichert

Das System speichert nun den zweiten Vornamen für Gastkonten beim Checkout korrekt, sodass er in der E-Mail-Vorlage verfügbar ist. Zuvor wurde der zweite Vorname nicht in der Angebotstabelle gespeichert und war in der E-Mail-Vorlage für Gastkonten nicht zugänglich.

_AC-11755 - [GitHub-Problem](https://github.com/magento/magento2/issues/38593) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39067)_

#### Admin: Schaltflächen für Seitenaktionen, die links statt rechts eingeblendet werden

Das System richtet nun die Schaltflächen für die Seitenaktionen korrekt auf der rechten Seite der Sticky-Kopfzeile im Admin-Bedienfeld aus, wodurch das professionelle Look-and-Feel verbessert wird. Zuvor waren diese Schaltflächen fälschlicherweise auf der linken Seite der Sticky-Kopfzeile unverankert.

_AC-11919 - [GitHub-Problem](https://github.com/magento/magento2/issues/38701) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44cef3a9)_

#### `dev:di:info` in Magento 2.4.7

Das System zeigt jetzt beim Ausführen des `dev:di:info`-Befehls die Konstruktorparameter korrekt an, sodass keine Fehler auftreten. Zuvor führte die Ausführung dieses Befehls zu einem Fehler aufgrund eines Typkonflikts im -Argument.

_AC-11999 - [GitHub-Problem](https://github.com/magento/magento2/issues/38740) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Als Kunden-Opt-in anmelden Checkbox nicht übersetzbar

Das System ermöglicht jetzt, dass die Felder „Als Kunden-Opt-in anmelden“ und „Als Kunden-Checkbox-Tooltip anmelden“ im Bereich „Store-Ansicht“ festgelegt werden, was Übersetzungen für verschiedene Store-Ansichten ermöglicht. Zuvor wurden diese Felder nur im Umfang der „Website“ festgelegt, wodurch Übersetzungen für einzelne Store-Ansichten verhindert wurden.

_AC-13000 - [GitHub-Problem](https://github.com/magento/magento2/issues/32329) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32359)_

#### Kunde ist angemeldet, zeigt aber 404-Fehler in Frontend an.

Die Kunden-Dashboard-Seite der Storefront wird jetzt wie erwartet geladen, wenn sich ein Kunde anmeldet. Zuvor konnten sich Kunden zwar anmelden, auf dieser Seite wurde jedoch ein 404-Fehler angezeigt. [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [GitHub-Problem](https://github.com/magento/magento2/issues/35838) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36263)_

#### Kundenattributinformationen können nicht im Abschnitt „Admin-Kundenbearbeitung“ gespeichert werden.

Die Store-ID des Kunden wird jetzt ordnungsgemäß pro Website-Umfang für das Admin-Kundenbearbeitungsformular implementiert.

_ACP2E-2791 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/488c1034)_

#### Nach der Anmeldung sind die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.

Produkte, die vor der Anmeldung als Kunde zur Produktvergleichsliste hinzugefügt wurden, bleiben jetzt nach der Anmeldung erhalten.
Zuvor waren nach der Anmeldung die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.

_ACP2E-3329 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### Die Konfiguration „Länder zulassen“ verursacht Probleme in den Konfigurationen für Kundenadressen

Die Auswahl der Konfiguration „Länder zulassen“ hat jetzt keinen Einfluss auf Länder, die außerhalb des angegebenen Bereichs angezeigt werden. Zuvor durch die Konfiguration „Länder zulassen“ beeinflusste Kundenadressattribute außerhalb des angegebenen Bereichs.

_ACP2E-3433 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### VAPT: Business Logic-Fehler - künftiges Datum als Geburtsdatum des Kunden

Das Geburtsdatum des Kunden kann nicht nach heute festgelegt werden

_ACP2E-3501 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

### Konto, APIs, GraphQL

#### Kunden-API - Zahl der Anmeldefehler, die nach erfolgreicher Anmeldung nicht auf 0 zurückgesetzt werden kann

Jetzt wird die Fehlernummer in der Kundenentitätstabelle nach erfolgreicher Anmeldung des Kunden über API-Endpunkte auf null zurückgesetzt.

_ACP2E-3246 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### Konto, Admin-Benutzeroberfläche, B2B

#### Benutzende mit eingeschränktem Administratorzugriff können benutzerdefinierte freigegebene Kataloge nicht immer sehen

Benutzende mit eingeschränkten Administratorrechten können jetzt Kundinnen und Kunden sowie alle freigegebenen Kataloge, denen die Produkte zugewiesen sind, konsistent anzeigen und verwalten, sofern sie Zugriff auf den jeweiligen Shop haben. Zuvor konnte ein Admin-Benutzer mit eingeschränktem Zugriff auf einen bestimmten Store nicht immer alle freigegebenen Kataloge sehen, denen die Produkte zugewiesen waren, oder er konnte Kunden sehen, die nicht speichern konnten, was zu Inkonsistenzen im System führte.

_ACP2E-3038 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

### Konto, Warenkorb und Checkout

#### Benutzerdefiniertes Kundenadressenattribut „Auswählen“ wird nicht für neue Kundenadresse gerendert

_AC-2341 - [GitHub-Problem](https://github.com/magento/magento2/issues/34950)_

### Admin-Benutzeroberfläche

#### [Problem] Hinzufügen einer Berechtigungsprüfung für die Datenschaltfläche „Daten neu laden“

Das System umfasst jetzt eine Berechtigungsprüfung für die Schaltfläche „Daten neu laden“, um sicherzustellen, dass sie nur Benutzern mit den entsprechenden Berechtigungen angezeigt und zugänglich sind. Zuvor war die Schaltfläche „Daten neu laden“ für alle Benutzer sichtbar und klickbar, was zu einer „nicht zulässigen“ Seite führte, wenn Benutzer ohne die erforderlichen Berechtigungen darauf klickten.

_AC-10705 - [GitHub-Problem](https://github.com/magento/magento2/issues/38283) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38279)_

#### [Problem] Inkonsistente Beschriftungen für Attribute in Marketing-Regeln

Das System füllt nun die Beschriftungen für Kategorie- und Attributoptionen in der Warenkorb-Preisregel korrekt aus

_AC-11427 - [GitHub-Problem](https://github.com/magento/magento2/issues/31232) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31231)_

#### Die Datenvalidierung ist erfolgreich und die Schaltfläche Importieren ist beim Importieren von Produkten mit dem Verhalten „Ersetzen“ vorhanden

Das System validiert jetzt die Daten korrekt und blendet die Schaltfläche „Importieren“ während des Produktimports mit „Ersetzen“-Verhalten aus, um einen unbeabsichtigten Datenaustausch zu verhindern. Zuvor hat das System die Daten falsch validiert und die Schaltfläche „Importieren“ angezeigt, was zu potenziellen Dateninkonsistenzen führte.

_AC-11588 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

#### [Bug] Magento 2.4.7 lässt keine Produktfotos mit der Dateierweiterung „Großbuchstaben“ zu.

Das System akzeptiert jetzt Produkt-Image-Uploads mit Großbuchstaben-Dateierweiterungen, was einen reibungslosen Produkterstellungsprozess gewährleistet. Zuvor wurden Bild-Uploads mit Großbuchstaben-Dateierweiterungen abgelehnt, was Benutzer zwang, die Dateierweiterung in Kleinbuchstaben zu ändern.

_AC-12167 - [GitHub-Problem](https://github.com/magento/magento2/issues/38831) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_

#### Ausgeblendetes Dropdown-Menü in Rastern mit Auswahl-Aktion (z. B. Inhalt > Elemente > Seiten)

Jetzt wurde das System für alle ähnlichen Dropdown-Listen für alle Raster korrigiert.

_AC-12319 - [GitHub-Problem](https://github.com/magento/magento2/issues/38891) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39371)_

#### [Problem] Warnung beheben: Nicht definierter Array-Schlüssel „filter“

Das System verarbeitet jetzt Szenarien, in denen ein neuer Benutzer noch nicht mit Lesezeichen interagiert hat, sodass keine Warnung bezüglich eines nicht definierten Array-Schlüssels „Filter“ protokolliert wird. Zuvor wurde diese Warnung protokolliert, wenn ein neuer Benutzer nicht mit Lesezeichen interagiert hatte.

_AC-13131 - [GitHub-Problem](https://github.com/magento/magento2/issues/39013) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38996)_

#### CSV-Datei des Produktimports mit Sonderzeichen schlägt aufgrund von Code-Änderungen in der Datei Validate.php fehl

Das System validiert und importiert jetzt Produkt-CSV-Dateien, die Sonderzeichen enthalten, korrekt, was eine erfolgreiche Datenübertragung ermöglicht. Zuvor führte der Versuch, eine Produkt-CSV-Datei mit Sonderzeichen zu importieren, zu einem Fehler, der den Importvorgang verhinderte.

_AC-13529 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Für das Feld Obligatorische Telefonnummer ist kein rotes Sternchen vorhanden.

Frühere rote Sternchen wurden nicht für Telefonnummer angezeigt, aber  Telefonnummer war obligatorisch. Was nun ein festes rotes Sternchen ist, kann auf der Telefonnummer als Pflichtfeld gesehen werden.

_AC-13850 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c699c206)_

#### [Problem] Standardindexermodus auf „schedule“ festlegen

Alle neuen Indexer befinden sich standardmäßig im **[!UICONTROL Update by Schedule]**.  Zuvor war der Standardmodus **[!UICONTROL Update on Save]**. Bestehende Indexer sind davon nicht betroffen. [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [GitHub-Problem](https://github.com/magento/magento2/issues/36419) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0b410856)_

#### [Problem] Löschen von Indexeränderungsprotokolltabellen bei der Abmeldung von der mview

Das System entfernt jetzt automatisch nicht verwendete Änderungsprotokolltabellen, wenn ein Index von „Aktualisierung im Zeitplan“ zu „Aktualisierung beim Speichern“ wechselt. Der Index wird als ungültig markiert, um sicherzustellen, dass keine Einträge übersehen werden. Zuvor würde ein Wechsel eines Index zu „Aktualisierung beim Speichern“ nicht verwendete Änderungsprotokolltabellen im System belassen und alle geänderten Indizes als „gültig“ markieren.

_AC-7700 - [GitHub-Problem](https://github.com/magento/magento2/issues/29789) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/25859)_

#### Kein Link zum Versand bei Zahlungen an der Kasse in der Mobiltelefonansicht

Das System stellt jetzt sicher, dass die Checkout-Titel/Links „Versand“ und „Überprüfung und Zahlungen“ immer oben auf der Seite in der mobilen Ansicht sichtbar sind, sodass Benutzende einfach zwischen Schritten navigieren und notwendige Korrekturen vornehmen können. Zuvor waren diese Titel/Links in der mobilen Ansicht ausgeblendet, sodass es für Benutzende schwierig ist, ihren aktuellen Schritt zu kennen oder zu vorherigen Schritten zurückzukehren.

_AC-7962 - [GitHub-Problem](https://github.com/magento/magento2/issues/36856) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36982)_

#### Die Abfrage „Kundenaufträge - Lieferkommentare“ von created_at wird in der Zeitzone +0 zurückgegeben, die nicht in der konfigurierten Zeitzone des Geschäfts ist

Das System zeigt jetzt bei Verwendung der Abfrage „Kundenbestellungen“ das Feld „created_at“ aus den Versandkommentaren in der konfigurierten Zeitzone des Kunden korrekt an. Zuvor wurde das Feld „created_at“ in der Zeitzone +0 angezeigt, unabhängig von der konfigurierten Zeitzone des Kunden.

_AC-8109 - [GitHub-Problem](https://github.com/magento/magento2/issues/36947) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases beeinträchtigt die Integrität der Übersetzungen

Der Befehl `bin/magento i18n:collect-phrases -o` erfasst und fügt nun neue Ausdrücke aus JavaScript- und PHTML-Dateien hinzu, um sicherzustellen, dass die Übersetzungen korrekt in der Übersetzungsdatei wiedergegeben werden. Zuvor konnte das System nicht mehrzeilige Übersetzungsausdrücke aus JavaScript-Dateien und Ausdrücke aus .phtml-Dateien in die Übersetzungsdatei einbeziehen, was zu unvollständigen oder falschen Übersetzungen führte.

_AC-9843 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Apostroph im Namen der Store-Ansicht wird durch &quot;&#039;“ ersetzt

Die Store-View-Filter des Rasters zeigen jetzt korrekt Apostrophe an

_ACP2E-2787 - [GitHub-Problem](https://github.com/magento/magento2/issues/38395) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_

#### Der Favicon-Upload kann .ico-Dateien nicht validieren

Der Fehler bei der Dateivalidierung wurde in „Dateivalidierung fehlgeschlagen“ aktualisiert. Überprüfen Sie die Bildverarbeitungseinstellungen in der Store-Konfiguration.“ Zuvor hieß es einfach „Dateivalidierung fehlgeschlagen“.

_ACP2E-2847 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_

#### Galerie in PageBuilder zeigt die alte Miniaturansicht anstelle des neu hochgeladenen Bildes an

Regenerieren Sie Bildvorschauen für Bilder, die gelöscht und mit demselben Namen über die Mediensammlung in Page Builder-Inhalten erneut hochgeladen wurden.

_ACP2E-2957 - [GitHub-Code-](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/001e5188)_

#### Durch das Speichern des Produkts durch einen Administrator mit einem anderen Rollenbereich werden vorhandene zugehörige Produktinformationen im Produkt überschrieben/gelöscht

Vor der Fehlerbehebung wurden die zugehörigen Produkte zurückgesetzt und leer, wenn der sekundäre Administrator auf die Schaltfläche Speichern geklickt hat, ohne das zugehörige Produkt zu ändern. Nach dieser Fehlerbehebung klickt der sekundäre Admin-Benutzer auf die Schaltfläche Speichern , das Produkt wird nicht zurückgesetzt und erfolgreich gespeichert.

_ACP2E-2978 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3056e9cb)_

#### Export von mehr als 200 Bestellungen nicht möglich

Die Server-Beschränkungen für die Anfragegröße zuvor gesendeter ausgewählter IDs wurden vernachlässigt, indem die HTTP-Anfrage von GET in POST geändert wurde, um das Problem zu beheben. Aufgrund der Serverbeschränkungen für die GET-Anfragengröße trat zuvor das Problem auf.

_ACP2E-3033 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_

#### Validierungsmeldung für Checkout-Seite falsch.

Wenn ein erforderliches Feld leer gelassen wird, z. B. „Adresse“, zeigt die Server-seitige Validierung die Nachricht nicht an. Die Client-seitige Validierung stellt sicher, dass die Fehlerbenachrichtigung für das erforderliche Feld angezeigt wird, in der steht: „Dies ist ein erforderliches Feld.“ Zuvor wurde zusätzlich zur Client-seitigen Validierungsmeldung die Meldung „Adresse ist erforderlich“ angezeigt, wenn ein erforderliches Feld leer gelassen wurde.

_ACP2E-3037 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_

#### Problem mit der Vorlage zum Zurücksetzen des Kennworts bei Admin-Benutzer

Das Problem wurde durch Verwendung des richtigen Schlüssels behoben, der jetzt den Admin-Benutzernamen in die E-Mail-Vorlage enthält und den Betreff ordnungsgemäß ausfüllt. Zuvor bestand das Problem aus einem veralteten Schlüssel, der verwendet wurde.

_ACP2E-3125 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_

#### Doppelte Schrägstriche in der Kundensegment-URL

Doppelte Schrägstriche werden in der URL nicht angezeigt, wenn im Raster auf „Filter zurücksetzen“ geklickt wird.

_ACP2E-3149 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_

#### Für bestimmte zulässige Länder ist kein Kabeljau verfügbar

Jetzt ist Cash-on-Delivery für bestimmte zulässige Länder verfügbar, wann immer es erforderlich ist, und   AC-3216 funktioniert erwartungsgemäß.

_ACP2E-3171 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_

#### Status der benutzerdefinierten erstellten Bestellung kann nicht aktualisiert werden

&#39;Wir können jetzt den Status der benutzerdefinierten Bestellung aktualisieren, während der Status zuvor nur geändert werden konnte, wenn der aktuelle Status entweder „Verarbeitung läuft“ oder „Betrug“ war.&#39;

_ACP2E-3178 - [GitHub-Problem](https://github.com/magento/magento2/issues/38659) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_

#### Der Status der Versandadresse wird nicht automatisch aktualisiert

Vor der Fehlerbehebung war die Region der Versandadresse (oder die Regions-ID) nicht mit den Rechnungsinformationen für die Adresse synchronisiert. Jetzt werden sowohl die Versandadressenregion als auch die Regions-ID ordnungsgemäß aktualisiert, wenn die Informationen zur Rechnungsadresse geändert werden.

_ACP2E-3294 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

#### Die Schaltfläche „Zurücksetzen“ funktioniert nicht beim Hinzufügen/Bearbeiten von Admin-Benutzern

Zuvor funktionierte die Schaltfläche „Zurücksetzen“ nicht auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“. Jetzt funktioniert die Schaltfläche „Zurücksetzen“ im Admin-Bedienfeld unter „System“ > „Berechtigungen“ > „Alle Benutzer“ auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“ ordnungsgemäß.

_ACP2E-3364 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_

#### Falsche Erkennung und CORS-Fehler beim Routing der Magento-Admin-URL

Wenn nach der Fehlerbehebung die benutzerdefinierte Admin-Domain eine Subdomain der Hauptdomäne ist, kann auf den Admin nur über die konfigurierte Subdomain zugegriffen werden.

_ACP2E-3373 - [GitHub-Problem](https://github.com/magento/magento2/issues/37663) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_

#### Fehlerhafte Validierung für „Maximal zulässige Menge im Warenkorb“

Zuvor gab es bei leerem `Maximum Qty Allowed in Shopping Cart` keine Ausnahme, obwohl hier kein leerer Wert akzeptiert wird. Wenn diese Fehlerbehebung angewendet wird, werden beim Einfügen einer leeren Zeichenfolge Ausnahmen ausgelöst, sodass das Produkt nicht gespeichert werden kann.

_ACP2E-3392 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Problem mit der PageBuilder]Vorschau-Benutzeroberfläche: Die Schaltflächen in der Spalte „Page Builder“ werden nicht korrekt ausgerichtet

Die Schaltflächen in den Page Builder-Spalten sind jetzt korrekt ausgerichtet. Zuvor waren sie in den Page Builder-Spalten falsch ausgerichtet.

_ACP2E-3408 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### Bericht zu bestellten Produkten wird nicht exportiert. 404-Fehler.

Der Export von bestellten Produkten in CSV und XML funktioniert jetzt erwartungsgemäß

_ACP2E-3431 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_

#### TinyMCE JS Error in der Konsole nach JS-Minimierung aktivieren mit Produktionsmodus

Zuvor wurden durch die Aktivierung der JavaScript-Minimierung im Produktionsmodus im Admin-Bedienfeld JavaScript-Fehler im Zusammenhang mit TinyMCE 6 in der Browser-Konsole angezeigt, was sich auf die Funktionalität und das Benutzererlebnis auswirkte. Dieses Problem wurde nun behoben, sodass TinyMCE 6 reibungslos funktioniert und keine Fehler erzeugt werden, auch wenn die JS-Minimierung aktiviert ist.

_ACP2E-3457 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/56463d5e)_

#### Antrag auf zusätzliche Änderungen, um die Fehlerbehebung ACP2E-3375 vollständig abzuschließen

&#39;-

_ACP2E-3459 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Automatische Aktivierung neuer ACL-Berechtigungen

Neue Berechtigungen, die benutzerdefinierten Modulen hinzugefügt wurden, gewähren nicht mehr automatisch Zugriff auf alle vorhandenen Benutzerrollen, es sei denn, sie sind explizit konfiguriert.

_ACP2E-3503 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_

#### Der Benutzerbericht für das Admin-Aktionsprotokoll enthält keine Details für adminhtml_user_delete

Adminhtml_user_delete protokolliert jetzt wichtige Details korrekt. Zuvor wurden keine Protokolle für das Löschen von Benutzern generiert.

_ACP2E-3509 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4de008a9)_

#### Warenkorbregel, für die beim Aufgeben einer Bestellung vom Administrator keine Versandbedingung angewendet wird

Wenn die Warenkorb-Preisregel mit dem Coupon einen Rabatt für die Versandmethode aufweist, kann sie zuvor nicht über die Admin-Benutzeroberfläche angewendet werden. Nachdem diese Fehlerbehebung angewendet wurde, wird der Rabatt auf den Warenkorbpreis mit einem Coupon für eine bestimmte Versandmethode erfolgreich von der Admin-Benutzeroberfläche aus angewendet.

_ACP2E-3536 - [GitHub-Code-](https://github.com/magento/magento2/commit/a52ff98f) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/11ce816b)_

#### [FRESH] HEX-Code wird in SWATCH nicht korrekt aktualisiert

HEX-Code, der vom Benutzer manuell in die Farbauswahl des visuellen Farb-/Bildmusters eingegeben wird, wird vom System nicht mehr geändert. Zuvor wurden bei bestimmten HEX-Codes aufgrund von Konversionsfehlern zwischen Farbmodellen leichte Anpassungen vorgenommen.

_ACP2E-3559 - [GitHub-Code-](https://github.com/magento/magento2/commit/344fce23) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/1ef984c0)_

### Admin-Benutzeroberfläche, B2B

#### B2B-Anmeldung als Kunden-Header hat weiterhin das Magento-Branding

Zuvor wurde in der Kopfzeile der Storefront „You are now connected as &lt;customer name> on &lt;store name>&quot; (Sie sind jetzt als &lt;customer name> verbunden) mit Magento-Branding angezeigt. Was jetzt behoben ist und die Kopfzeile mit ADOBE-Branding angezeigt wird.

_AC-13628 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/96dec499)_

### Admin-Benutzeroberfläche, Zahlungs-/Zahlungsmethoden, Bestellung

#### Transaktionsautorisierung wird nach der Bestellung des PayPal-Smart-Buttons nicht auf der Registerkarte Transaktion angezeigt

Das System zeigt nun die Transaktionsautorisierung auf der Registerkarte Transaktion korrekt an, nachdem eine Bestellung über den PayPal Smart Button aufgegeben wurde. Zuvor wurde die Autorisierungstransaktion nicht auf der Registerkarte Transaktion angezeigt, nachdem auf die Schaltfläche „Autorisieren“ geklickt wurde, und es wurde keine neue Transaktion vom Typ „Autorisierung“ erstellt.

_AC-13520 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Admin-Benutzeroberfläche, Leistung

#### Nach der Aktualisierung auf 2.4.5-p8 treten beim Erstellen der Bestellung vom Administrator 500 Fehler auf

Zuvor konnte bei Aktivierung der HTML-Minimierung keine Bestellung vom Administrator aufgegeben werden. Nachdem die HTML-Minimierung aktiviert wurde, kann die Bestellung vom Administrator aufgegeben werden.

_ACP2E-3169 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_

### Admin-Benutzeroberfläche, Versand

#### Die Anzahl der Couponcodes wird in der   Die Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“, wenn eine Bestellung mit Mehrfachversand aufgegeben wird.

Zuvor wurde bei einer Bestellung mit mehreren Versandvorgängen die Anzahl der Gutscheincodes nicht in der Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“ aktualisiert. Jetzt wird die richtige Anzahl sowohl in der „Verwendeten Zeit“ angezeigt, die die gewünschten Werte bei Multi-Versand widerspiegelt.

_ACP2E-2519 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4745100c)_

### Admin-Benutzeroberfläche, Staging und Vorschau

#### [Cloud] Wenn Sie eine Vorlage mit fehlenden Bildern entfernen, wird Pub/Media gelöscht

Zuvor wurde der Ordner „pub/media“ gelöscht, wenn der Name des Vorschaubilds für eine PageBuilder-Vorlage fehlte. Nach der Korrektur wird nur die Vorlage gelöscht und das Vorschaubild gefunden, falls vorhanden.

_ACP2E-3424 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/Reporting

#### Google Analytics CSP-Fehler https://region1.analytics.google.com

Das System lässt jetzt bei aktiviertem Google Analytics korrekt Verbindungen zu &quot;https://region1.analytics.google.com&#39;&quot; zu, wodurch CSP-Fehler (Content Security Policy) verhindert werden. Zuvor führte die Aktivierung von Google Analytics und die Anzeige der Website aus der EU zu CSP-Konsolenfehlern aufgrund einer Weigerung, eine Verbindung zu &quot;https://region1.analytics.google.com&#39;&quot; herzustellen.

_AC-9922 - [GitHub-Problem](https://github.com/magento/magento2/issues/37750) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38991)_

#### Fortschrittsbericht funktioniert nicht

Das System unterstützt jetzt die Generierung von erweiterten Reporting-Datendateien für extragroße Datensätze, indem Berichte in Stapeln von 10.000 geladen und geschrieben werden. Zuvor konnte das Modul für erweiterte Berichterstellung keine Datendateien für besonders große Datensätze generieren, was zu Fehlern von „MySQL Server ist verschwunden“ während der Ausführung des Cron-Auftrags analytics_collect_data führte.

_ACP2E-2570 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a12063bd)_

#### Problem mit der Sichtbarkeit des Datumsbereichs des vom Administrator bestellten Produktberichts.

Der Benutzer kann ein beliebiges Datum aus dem Bericht Bestellte Produkte auswählen. Zuvor wird nach einer Tabellenaktualisierung durch die Auswahl von „Von“ das „Bis“-Datum zurückgesetzt.

_ACP2E-3080 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_

#### Falsche cURL-Kopfzeilen, sodass `newrelic:create:deploy-marker` nicht funktioniert

Das System formatiert jetzt die cURL-Kopfzeilen korrekt, sodass der `newrelic:create:deploy-marker`-Befehl erfolgreich eine Bereitstellungsmarkierung in New Relic erstellen kann. Zuvor verhinderten falsche cURL-Kopfzeilen die Erstellung einer Bereitstellungsmarkierung in New Relic.

_ACP2E-3096 - [GitHub-Problem](https://github.com/magento/magento2/issues/37641) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_

#### Die InlineJS-Skriptüberwachung von NewRelic verursacht CSP-Fehler

NewRelic-Browser-Überwachungsskripte werden jetzt von der Anwendung anstelle des APM-Agenten eingefügt, um die Einhaltung von CSP (Content Security Policy) zu gewährleisten. Zuvor waren die vom APM-Agent injizierten NewRelic-Browser-Überwachungsskripte nicht konform mit CSP und haben dazu geführt, dass die Skripte nicht ausgeführt wurden.

_ACP2E-3183 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

#### Abfragen in die Tabelle sales_bestsellers_aggregated_daily einfügen werden bei einem Projekt mit großem Auftragsvolumen langsam

Zuvor dauerte es sehr lange, bis der aggregierte Tagesbericht für die Bestseller für ein großes Volumen an aufgegebenen Bestellungen erstellt wurde. Jetzt wird der Bericht rechtzeitig erstellt.

_ACP2E-3189 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

#### Berichte mit falschem Währungssymbol bestellen

Das Währungssymbol für Bestellbeträge im Bestellbericht wurde fälschlicherweise aus Währung/Optionen/Basis übernommen. Es wurde jetzt korrigiert, um Währung/Optionen/Standard für ein genaues Reporting zu verwenden.

_ACP2E-3276 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] Falsche Berechnungen im Bericht zur Couponnutzung

Die Umsatzsumme im Berichtsraster „Coupons“ wird jetzt genau berechnet, indem sowohl der „Rabattsteuerausgleichsbetrag“ als auch der „Versandrabatt-Steuerausgleichsbetrag“ einbezogen werden. Zuvor fehlten diese Beträge in der Berechnung, was zu Diskrepanzen zwischen der Verkaufssumme und den Auftragsdaten führte.

_ACP2E-3302 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_

#### Probleme mit freigegebenen &quot;&lt;project_id>/var/tmp“

Temporäre Analytics-Datenexport-Dateien verwenden das sysTmp-Verzeichnis, das für häufigen Zugriff und Änderungen besser geeignet ist. Um Konflikte zu vermeiden, falls mehrere Instanzen auf demselben Server ausgeführt werden, wurde der tmp-Pfad aktualisiert, sodass er die eindeutige ID einer Instanz verwendet

_ACP2E-3339 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/Reporting, B2B

#### B2B - Sitemap enthält Produkte/Kategorien, die nicht dem freigegebenen Katalog zugewiesen sind

Beschränken Sie die von der Sitemap generierten Kategorien und Produkte auf die Kategorien und Produkte, die nur dem öffentlichen freigegebenen Katalog und/oder der Einrichtung der Katalogkategorie zugewiesen sind.

_ACP2E-2300 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/Reporting, Cloud

#### Magento verwirft die meisten New Relic Cron-Transaktionen #34108

AC meldet korrekt Cron-auftragsbezogene Transaktionen an NewRelic. Zuvor wurden einige Cron-Job-bezogene Transaktionen als „OtherTransaction/Action/Unknown“ in NR angezeigt

_ACP2E-3067 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/35b1b1da)_

#### Kennzahl in NR könnte für Hintergrundtransaktionen irreführend sein - Follow-up von ACP2E-3067

Hintergrundtransaktionen (Cron) verwenden den in den Konfigurationseinstellungen definierten App-Namen von New Relic

_ACP2E-3187 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### Produkte, die einem freigegebenen Katalog zugewiesen sind, werden bei der Ausführung eines partiellen Index nicht am Frontend angezeigt

Produkte, die über die REST-API einem freigegebenen Katalog zugewiesen wurden, sind jetzt nach Abschluss der partiellen Indizierung sofort in der Storefront sichtbar. Zuvor waren Produkte nur nach einer vollständigen Neuindizierung sichtbar.

_ACP2E-2139 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

#### Unnötige Ränder im Abschnitt Meine Bestellungen

Zuvor wurde ein zusätzlicher Container (Auftragsreferenzen) erstellt, der zusätzliche CSS-Klassen anwandte, was dazu führte, dass unnötige Rahmenlinien unter der Auftragsnummer im Abschnitt Meine Bestellungen angezeigt wurden, der jetzt nicht sichtbar ist.

_ACP2E-3044 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quotes cron löscht Angebote von bis zu noch genehmigten Bestellungen

Angebote, die jetzt in Bestellungen verwendet werden, werden von Sales_clean_quotes Cron-Auftrag nicht gelöscht.

_ACP2E-3247 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

### B2B, Framework

#### Filtern des Unternehmensrasters und anschließender Versuch des CSV-Exports des Rasters schlägt fehl und löst eine Ausnahme aus

Das System ermöglicht jetzt einen erfolgreichen CSV-Export der Rasterdaten des Unternehmens im Admin-Bedienfeld, auch wenn Filter wie „Ausstehender Saldo“ und „Unternehmenstyp“ angewendet werden. Zuvor führte das Anwenden bestimmter Filter und der Versuch, die Rasterdaten zu exportieren, zu einem Fehler und einer Ausnahme.

_AC-9607 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44cef3a9)_

### Bündel

#### Fehlermeldung bei der Überprüfung des Storefront-Bundles mit Checkbox-Überprüfung mehr als 1

Das System zeigt jetzt nur noch eine Validierungsfehlermeldung an, wenn die Schaltfläche „Zum Warenkorb hinzufügen“ angeklickt wird, ohne dass Kontrollkästchen-Optionen für ein gebündeltes Produkt ausgewählt werden. Zuvor zeigte das System mehrere Validierungsfehlermeldungen für jedes nicht ausgewählte Kontrollkästchen an.

_AC-10826 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ea26621)_

### Warenkorb und Checkout

#### Ausnahme wird beim Hinzufügen eines Produkts zum Warenkorb auf der Seite „Produkt vergleichen“ nicht ordnungsgemäß verarbeitet

Das System verarbeitet jetzt Ausnahmen ordnungsgemäß, wenn ein Produkt von der Seite Produkt vergleichen zum Warenkorb hinzugefügt wird und eine Meldung des Nachrichten-Managers im Controller angezeigt wird. Zuvor führte eine Ausnahme dazu, dass eine JSON-codierte Seite zurückgegeben wurde, anstatt ordnungsgemäß erfasst und verarbeitet zu werden.

_AC-10660 - [GitHub-Problem](https://github.com/magento/magento2/issues/38200) - [GitHub-Code-](https://github.com/magento/magento2/pull/38257) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_

#### GTag sendet keine Transaktionspreise und -summen.

Das System sendet jetzt die Transaktionspreise und -summen korrekt an das Google-Tag, wenn das GT-Tag aktiviert ist, was eine genaue Verfolgung der E-Commerce-Daten gewährleistet. Zuvor wurde die Währung fälschlicherweise als Teil der „All“-Bestellungen gesendet, anstatt mit der einzelnen Bestellung verknüpft zu werden.

_AC-10698 - [GitHub-Problem](https://github.com/magento/magento2/issues/37348) - [GitHub-Code-](https://github.com/magento/magento2/pull/37504) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37349)_

#### [Problem] [Checkout] Abhängigkeitsanweisungen in der E-Mail-Vorlage für fehlgeschlagene Zahlungen aktualisiert

Das System lässt nun bei virtuellen Produkten die Lieferadresse und Versandmethode in der Vorlage für fehlgeschlagene Zahlungen korrekt aus, sodass die E-Mail nur relevante Informationen enthält. Zuvor enthielt die fehlgeschlagene Zahlungs-E-Mail für virtuelle Produkte fälschlicherweise die Versandadresse und die Versandmethode.

_AC-11641 - [GitHub-Problem](https://github.com/magento/magento2/issues/32781) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32511)_

#### Magento 2-Anmeldung beim Checkout mit vorhandenem Kunden geben Konsolenfehler im Firefox-Browser

Das System ermöglicht es Benutzern jetzt, sich während des Checkout-Prozesses anzumelden, ohne dass im Firefox-Browser Konsolenfehler auftreten. Zuvor führte der Versuch, sich während des Checkouts als bestehender Kunde anzumelden, zu einem Konsolenfehler in Firefox.

_AC-11717 - [GitHub-Problem](https://github.com/magento/magento2/issues/38557) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39509)_

#### [Problem] Regression der Verkaufsregeln in 2.4.7

Das System validiert nun die Verkaufsregeln korrekt und verhindert die Anwendung eines Gutscheincodes auf einen Warenkorb, wenn die Produktbedingung mit keinem Produktnamen übereinstimmt. Zuvor konnte eine Verkaufsregel angewendet und ein Rabatt auf den Versandbetrag gewährt werden, selbst wenn die Produktbedingung mit keinem Produktnamen übereinstimmte.

_AC-11876 - [GitHub-Problem](https://github.com/magento/magento2/issues/38671) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

#### [Problem] Verkaufsregel WarenkorbFeste Berechnung : Falscher Rabattbetrag

Das System berechnet nun den Rabattbetrag für Verkaufsregeln mit festen Warenkorbbeträgen korrekt und stellt sicher, dass genaue Rabatte unabhängig von Änderungen an den Warenkorbartikeln angewendet werden. Zuvor konnte der Rabattbetrag falsch variieren, wenn Artikel im Warenkorb geändert wurden, was manchmal zu erheblich größeren Rabatten als erwartet führte.

_AC-11914 - [GitHub-Problem](https://github.com/magento/magento2/issues/38694) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

#### [Problem] Der Lader blockiert die Versandmethoden, nachdem die Postleitzahl geändert wurde. Validierungsregeln für Versandraten

Das System verarbeitet jetzt benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten korrekt, sodass der Lader die Versandmethoden nicht blockiert, nachdem die Postleitzahl während des Checkouts in der Versandadresse geändert wurde. Zuvor führte eine Änderung der Postleitzahl in der Versandadresse während des Checkouts dazu, dass der Lader die Versandmethoden blockiert und nicht verschwindet, wenn benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten verwendet wurden.

_AC-11993 - [GitHub-Problem](https://github.com/magento/magento2/issues/38742) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_

#### Die Gutscheincode-Funktion funktioniert auf der Kaufbestätigungsseite in Magento 2.4.7 nicht ordnungsgemäß

Das System aktiviert jetzt das Eingabefeld für Rabattcode/Coupon auf der Checkout-Seite für virtuelle und herunterladbare Produkte, sodass Benutzer Rabattcodes wie erwartet anwenden können. Zuvor war die Eingabe des Rabattcodes/Coupons deaktiviert und der Text des Schaltflächentitels wurde als „Coupon abbrechen“ angezeigt, was Benutzer daran hinderte, Rabattcodes anzuwenden.

_AC-12170 - [GitHub-Problem](https://github.com/magento/magento2/issues/38826) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_

#### Das Kontrollkästchen „Allgemeine Geschäftsbedingungen“ lässt HTML in der Storefront nicht zu

Das System unterstützt jetzt die Formatierung von HTML im Checkbox „Geschäftsbedingungen“ auf der Storefront, was eine bessere Anpassung und Lesbarkeit ermöglicht. Zuvor wurde der Checkbox-Text im Nur-Text-Format angezeigt, wobei alle verwendeten HTML-Tags ignoriert wurden.

_AC-12479 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Die für einen angemeldeten Benutzer erstellte Warenkorbpreisregel wird fälschlicherweise für einen nicht angemeldeten Benutzer angewendet

Das System entfernt jetzt die Warenkorb-Preisregel für angemeldete Benutzer korrekt, wenn sie aufgrund des Cookie-Ablaufs automatisch abgemeldet werden, sodass der Rabatt nicht auf nicht angemeldete Benutzer angewendet wird. Zuvor wurde die Regel zum Warenkorbpreis auch dann angewendet, wenn sich der Benutzer abgemeldet hatte, was dazu führte, dass auf nicht angemeldete Benutzer ein falscher Rabatt angewendet wurde.

_AC-12541 - [GitHub-Problem](https://github.com/magento/magento2/issues/38944) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problem] [FUNKTION] Leistungsoptimierung großer Warenkörbe durch…

Das System optimiert jetzt die Leistung für große Warenkörbe, indem doppelte getActions-Aufrufe verhindert werden, was die Geschwindigkeit und Effizienz von Warenkorbvorgängen erhöht. Zuvor wurde bei einem Warenkorb mit mehreren Artikeln die getActions-Funktion mehrmals aufgerufen, was die Systemleistung verlangsamte.

_AC-13302 - [GitHub-Problem](https://github.com/magento/magento2/issues/39292) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39290)_

#### MwSt.-Übersetzungsauftrag im Adressrechner

Das System ermöglicht nun die Übersetzung des Textes „VAT“, „T“, „F“ in den Adressrenderern, sodass die Benutzer diese Begriffe in die spezifische Sprache des Ladens übersetzen können. Zuvor waren diese Begriffe nicht übersetzbar, was die Benutzer dazu zwang, eine Problemumgehung anzuwenden.

_AC-8103 - [GitHub-Problem](https://github.com/magento/magento2/issues/36942) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36943)_

#### Doppelte Bestellungen mit derselben Angebots-ID zur gleichen Zeit mit wenig Zeitunterschied

Es wurde ein Problem behoben, bei dem Adobe Commerce-Kunden auf doppelte Bestellungen stießen, die mit derselben QuoteID aufgegeben wurden

_ACP2E-2055 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

#### Beständiger Warenkorb beim Checkout gelöscht

Nach der Behebung wird die persistente Sitzung nicht beendet, wenn Sie die Zahlungsmethode während des Checkouts auswählen, während Sie nicht angemeldet sind.

_ACP2E-2470 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

#### Neu bestellen fügt nicht zugewiesenes Produkt zum Warenkorb hinzu

Zuvor konnten für die verschiedenen Stores Produkte vom anderen Store nachbestellt werden. Nachdem diese Fehlerbehebung nur auf denselben Store angewendet wurde, kann dasselbe Produktumfang neu bestellt werden, wenn die Kundenkontofreigabe aktiviert ist

_ACP2E-2518 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

#### In Admin wird der „Warenkorb“ auf der linken Seite nicht aktualisiert, wenn die Artikel ausgewählt werden und „Zum Warenkorb wechseln“ auf der rechten Seite

Der „Warenkorb“ auf der linken Seite wird aktualisiert, wenn Sie die Artikel auswählen und „Zum Warenkorb wechseln“ auf der rechten Seite in der Admin-Seite. Zuvor funktionierte diese Funktion nicht, da die umgewandelten Warenkorbelemente nicht aus der Sitzung leer wurden.

_ACP2E-2620 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_

#### [Cloud] Verkaufsregel nicht auf die erste Bestellung von Multi-Shipping angewendet

Nach der Fehlerbehebung wird der Rabatt für jede Bestellung desselben Multi-Shipping-Angebots korrekt angezeigt.

_ACP2E-2646 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

#### [Cloud] Produktionsanfragen zum Hinzufügen desselben Produkts zum Warenkorb führen zu zwei separaten Elementen in der Warenkorb-REST-API

Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte das parallele Anfordern desselben Produkts über die REST-API zum Warenkorb, zu mehreren Zeileneinträgen für dieselbe SKU.

_ACP2E-2664 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

#### Das Cookie kann nicht gesendet werden. Größe von „image-messages“ beim Versuch, eine Neuanordnung vorzunehmen

Der Neuanordnungsprozess erzeugt jetzt keine eigenen Fehler. Dies beruht auf der Auflistung der in den Warenkorb integrierten Artikelprüfungen.

_ACP2E-2704 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_

#### Die Standard-Versandadresse ist beim Checkout nicht ausgewählt

Die standardmäßige Versandadresse wird jetzt im Kontext der aktivierten Adresssuche für das Ereignis ausgewählt.

_ACP2E-2798 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD] GraphQL addProductsToCart API-Problem mit benutzerdefinierter Option

GraphQL fügt dasselbe Produkt mit verschiedenen benutzerdefinierten Optionen korrekt in den Warenkorb

_ACP2E-2897 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_

#### Mehrere Adressen wurden dem Konto beim Checkout als neuer Kunde hinzugefügt

Das System speichert jetzt eine neue Kundenadresse nur einmal, wenn die Bestellung nicht erstellt werden konnte, wodurch die Erstellung mehrerer identischer Adressen im Falle von Fehlern bei der Bestellplatzierung verhindert wird. Zuvor speicherte das System jedes Mal eine neue Adresse, wenn ein Bestellplatzierungsversuch unternommen wurde, unabhängig davon, ob der Auftrag erfolgreich erstellt wurde oder nicht.

_ACP2E-2923 - [GitHub-Code-](https://github.com/magento/magento2/commit/001e5188) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/2ebcef39)_

#### Die Neuanordnung einer Kundenbestellung über ein Gastbestellungsformular führt zu einem leeren Warenkorb

Zuvor wurde der Kunde bei der Neubestellung über die Seite Bestellungen und Rücksendungen zur Anmeldeseite weitergeleitet. Nachdem diese Fehlerbehebung angewendet wurde, wird der registrierte Kunde bei der Neubestellung korrekt zur Seite Warenkorb anzeigen weitergeleitet. Der Fluss funktioniert genauso wie bei Gastkunden.

_ACP2E-3004 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_

#### Admin-Benutzer mit eingeschränkten Rollenressourcen kann den Warenkorb nicht anzeigen

Zuvor konnte der Administrator mit Zugriffsbeschränkung den abgebrochenen Warenkorb im Admin-Bedienfeld für eine zugehörige Website nicht sehen. Nachdem diese Fehlerbehebung angewendet wurde, kann der eingeschränkte Administrator den Transaktionsabbruch im Admin-Bedienfeld einsehen.

_ACP2E-3025 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d1f7dc95)_

#### [Cloud]-Schnellbestellung: Große SKU-Leistung

Die Checkout-Leistung wurde verbessert, wenn in den Warenkorbpreisregeln verwendete Attribute nicht für alle Produkte vorhanden sind und die MAP-Funktion (Minimum Advertised Price) aktiviert ist.

_ACP2E-3176 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

#### Duplizierte Artikel im Warenkorb

Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte die parallele Anforderung, dasselbe Produkt zum Warenkorb in der Storefront hinzuzufügen, zu mehreren Zeileneinträgen für dieselbe SKU.

_ACP2E-3211 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

#### Die E-Mail-Bestätigung der Kaufbestätigung wird an die in Vor-/Nachname eingegebenen E-Mails gesendet.

Die E-Mail-Bestätigung für die Kaufbestätigung, die zuvor gesendet wurde, als ein E-Mail-ähnliches Muster in die Felder Vor- und Nachname eingegeben wurde, wird nicht mehr gesendet.

_ACP2E-3296 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_

#### Checkout Versandadresse Formular mit falscher Adresse aktualisieren

shippingAddressFromData wird jetzt pro Website im lokalen Speicher gespeichert. Zuvor konnte eine Adresse von der falschen Website während des Checkouts automatisch in das Versandadressenformular eingefügt werden, wenn ein Store-Code in der URL verwendet wurde und der Checkout von mehreren Websites während derselben Gastsitzung initiiert wurde.

_ACP2E-3402 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### Geschenkkartenprodukt | Beim Zusammenführen des Warenkorbs werden Geschenkkarten zusammengeführt

Geschenkkartenprodukte wurden jetzt korrekt im Warenkorb zusammengeführt

_ACP2E-3407 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_

#### Warenkorb-Persistenz wird beim Abmelden nicht berücksichtigt

Es wurde eine Funktion hinzugefügt, mit der ich mich von der Kundenanmeldung zum Authentifizierungs-Popup und zur Checkout-Anmeldung erinnere.

_ACP2E-3415 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/344fce23)_

#### Vorhandene Anführungszeichen werden nicht aktualisiert/nicht angezeigt. Stattdessen einen neuen Anführungszeichen erstellen, wenn Trigger_recollect = 1

Die Artikel im Warenkorb des Kunden verschwinden nicht mehr, weil ein Produkt gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde.

_ACP2E-3488 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

#### [CLOUD] Funktion „Schaltfläche neu anordnen“

Wenn Sie eine Bestellung im Administratorbereich neu bestellen, werden jetzt Produkte mit Lager zum Angebot hinzugefügt, auch wenn es einige Produkte in der ursprünglichen Bestellung gibt, die nicht mehr vorrätig sind. Vor der Fehlerbehebung wurden keine Produkte zum neuen Angebot hinzugefügt, wenn Produkte ohne Lager in der ursprünglichen Bestellung waren.

_ACP2E-3618 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a52ff98f)_

#### Suchvorgänge funktionieren nicht nach Postleitzahl

Die Suche nach Abholorten per Postleitzahl funktionierte bei niederländischen Lokalisierungen nicht ordnungsgemäß. Nach der Fehlerbehebung liefert die Suche nach dem Abholort Ergebnisse basierend auf der Postleitzahl.

_ACP2E-3622 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/344fce23)_

### Warenkorb &amp; Checkout, Checkout/ Eine Seite Checkout

#### [Zufällige Fehler] Das Feld „E-Mail“ wird nicht gerendert oder benötigt viel Zeit, um auf der Kaufbestätigungs-, Versand- oder Zahlungsseite anzuzeigen.

Commerce rendert jetzt das **[!UICONTROL Email]** auf den Seiten Checkout-Versand und Zahlung wie erwartet. Zuvor war dieses Feld entweder nicht vorhanden oder wurde langsam gerendert.

_AC-9386 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e1babcfd)_

### Warenkorb und Checkout, Bestellung

#### Datumsauswahl für ein Produkt mit mehreren anpassbaren Optionen, bei denen Datumsfelder bei der Bestellung vom Administrator nicht funktionieren

Das System zeigt jetzt bei der Konfiguration eines Produkts mit mehreren anpassbaren Datumsoptionen im Prozess zur Erstellung von Admin-Aufträgen die Datumsauswahl für alle Datumsfelder korrekt an. Zuvor wurde die Datumsauswahl nur für das erste Datumsfeld angezeigt, sodass die verbleibenden Felder keine Datumsauswahl aufweisen.

_ACP2E-3097 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_

### Warenkorb und Checkout, Versand

#### Sofortiger Kauf „Günstigster Versand“ für konfigurierbare Produkte defekt

Die Funktion Instant Purchase wählte fälschlicherweise die teurere In-Store-Lieferoption für konfigurierbare Produkte anstelle der günstigsten Pauschalmethode aus. Durch diese Fehlerbehebung wird sichergestellt, dass die richtige Versandmethode auf der Grundlage des tatsächlichen Preises ausgewählt wird.“

_AC-12119 - [GitHub-Problem](https://github.com/magento/magento2/issues/38811) - [GitHub-Code-](https://github.com/magento/magento2/pull/38819) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/29fe9097)_

### Katalog

#### Die Bereinigung der Datenbanktabelle cron_schedule bereinigt keine nicht vorhandenen Aufträge

Das System bereinigt jetzt automatisch die Datenbanktabelle cron_schedule und entfernt Einträge für Aufträge, die nicht mehr im System vorhanden sind. Dadurch wird eine optimale Leistung gewährleistet, indem eine minimale Anzahl von Zeilen in der Tabelle beibehalten wird. Zuvor wurden Einträge für Aufträge von inaktiven oder entfernten Modulen nicht bereinigt, was zu einer unnötigen Datenakkumulation in der cron_schedule-Tabelle führte.

_AC-10910 - [GitHub-Problem](https://github.com/magento/magento2/issues/38217) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38693)_

#### Stufe Preis wird nicht aus konfigurierbarem Produkt gelöscht

Das System entfernt nun den Stufenpreis eines Produkts korrekt, wenn es von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wird, wodurch eine genaue Preisanzeige im Frontend gewährleistet ist. Zuvor wurde der Stufenpreis eines konfigurierbaren Produkts nicht gelöscht, wenn ein Produkt von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wurde, was zu einer Diskrepanz beim angezeigten Preis führte.

_AC-10953 - [GitHub-Problem](https://github.com/magento/magento2/issues/38390) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38427)_

#### Kategoriebeschreibung WYSIWYG ist in nicht standardmäßiger Storeview leer

Das System speichert jetzt die Kategoriebeschreibung korrekt im WYSIWYG-Editor und zeigt sie an, wenn eine Kategorie auf der Store-Ansichtsebene bearbeitet wird. Zuvor war der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer.

_AC-11804 - [GitHub-Problem](https://github.com/magento/magento2/issues/38622) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38623)_

#### Es ist nicht möglich, konfigurierbare Produkte neu anzuordnen, wenn ein Kontrollkästchen für eine benutzerdefinierte Option aktiviert ist

Das System verarbeitet jetzt die Neuanordnung von konfigurierbaren Produkten mit einer einzigen ausgewählten benutzerdefinierten Checkbox-Option korrekt, was eine erfolgreiche Warenkorberstellung ermöglicht. Zuvor führte der Versuch, solche Produkte neu zu bestellen, zu einem Fehler und verhinderte, dass Artikel zum Warenkorb hinzugefügt wurden.

_AC-11970 - [GitHub-Problem](https://github.com/magento/magento2/issues/38736) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1d144bce)_

#### [Problem] Wortlaut des Filterelements in der mehrschichtigen Navigation korrigieren

Das System verwendet jetzt korrekt die Wörter „Element“ und „Elemente“ im Filterelement für die mehrschichtige Navigation, wodurch die Klarheit und Genauigkeit der Filterbeschreibungen verbessert wird. Zuvor wurden diese Wörter falsch verwendet, was zu Verwirrung bei Benutzenden führen kann, die in den Filteroptionen navigieren.

_AC-12076 - [GitHub-Problem](https://github.com/magento/magento2/issues/38789) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37852)_

#### Datums- und Uhrzeitformat für benutzerdefinierte Option funktioniert nicht

Das System wendet das konfigurierte Datumsformat jetzt korrekt auf benutzerdefinierte Produktoptionen des Typs Datum an, um sicherzustellen, dass das Datumsformat im Frontend korrekt angezeigt wird. Zuvor spiegelten Änderungen an der Datumsformatkonfiguration das Frontend für benutzerdefinierte Optionen des Typs Datum nicht wider.

_AC-12164 - [GitHub-Problem](https://github.com/magento/magento2/issues/32990) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38925)_

#### Dropdown-Optionen fehlen

Das System zeigt jetzt alle Werte in der Dropdown-Liste korrekt an, wenn ein neues Attribut mit mehr als 20 Werten erstellt wird. Zuvor wurden nur die ersten 20 Werte oder andere ausgewählte Seitenwerte angezeigt, wodurch die verbleibenden Werte fehlten.

_AC-13068 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problem] Aktuelle Sore-ID für Laufzeitcache der Kategorie verwenden

Das System verwendet jetzt die aktuelle Speicher-ID für den Laufzeitcache der Kategorie korrekt, um zu verhindern, dass Daten überschrieben werden, wenn die Emulation verwendet wird oder benutzerdefinierter Code die Kategorie in verschiedenen Stores speichert. Zuvor stammte das in der Laufzeit gespeicherte Objekt möglicherweise aus dem falschen Speicher, was zu einer Datenüberschreibungen führte.

_AC-13296 - [GitHub-Problem](https://github.com/magento/magento2/issues/39310) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampleData:deploy —no-update löst eine Ausnahme aus

Das System akzeptiert jetzt bei Verwendung der Option —no-update im Beispieldaten:deploy-Befehl einen booleschen Wert korrekt, wodurch Fehler bei der Bereitstellung von Beispieldaten vermieden werden. Zuvor wurde bei der Verwendung dieses Befehls ein Fehler ausgelöst, da das System fälschlicherweise einen ganzzahligen Wert erwartet hatte.

_AC-13324 - [GitHub-Problem](https://github.com/magento/magento2/issues/39344) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39345)_

#### [Problem] Behebung der Verwendung des EAV-Cache-Typs

Das System verwendet jetzt den EAV-Cache-Typ an allen relevanten Stellen korrekt, um ein konsistentes und effizientes Daten-Caching sicherzustellen. Zuvor wurde der EAV-Cache-Typ nicht konsistent verwendet, was zu potenziellen Ineffizienzen und Inkonsistenzen bei der Datenzwischenspeicherung führte.

_AC-13355 - [GitHub-Problem](https://github.com/magento/magento2/issues/32322) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31264)_

#### Die erweiterte Katalogsuche mit leeren Daten wird in die Verzweigung für Suchergebnisse [.2.4.dev verschoben]

Das System speichert Benutzer jetzt korrekt auf der Seite Erweiterte Suche und zeigt eine Fehlermeldung an, wenn sie versuchen, eine Suche durchzuführen, ohne Daten einzugeben. Zuvor wurden Benutzer bei einer leeren Suche zur Seite für die erweiterte Katalogsuche weitergeleitet, wobei eine Meldung angezeigt wurde, die sie aufforderte, ihre Suche zu ändern.

_AC-13596 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### [Problem] Produkt-Layout basierend auf attribute_set

Das System ermöglicht jetzt die Anpassung des Produkt-Layouts auf der Grundlage des Attributsatzes und bietet so eine praktischere und effizientere Möglichkeit, die Produktanzeige im Frontend-Store zu verwalten. Zuvor konnte das Layout nur nach SKU oder Produktarten angepasst werden, was für viele Produkte oder bestimmte Artikel nicht immer praktisch war.

_AC-13622 - [GitHub-Problem](https://github.com/magento/magento2/issues/38790) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36244)_

#### Fehlender eindeutiger Schlüssel in der Tabelle eav_attribute_option_value

Das System enthält jetzt einen eindeutigen Schlüssel in den Spalten „option_id“ und „store_id“ in der Tabelle „eav_attribute_option_value“, was verhindert, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hat. Zuvor konnte ein fehlerhafter Code dazu führen, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hatte, was Probleme bei der Bearbeitung von Produkten oder Attributen verursachte.

_AC-6738 - [GitHub-Problem](https://github.com/magento/magento2/issues/24718) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/28796)_

#### [Problem] Verwenden Sie die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte.

Das System verwendet jetzt die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte, was die Modularität verbessert. Zuvor wurden im Produkt-Indexer der Kategorie hartcodierte Werte verwendet, was die Flexibilität und Anpassungsfähigkeit einschränkte.

_AC-8297 - [GitHub-Problem](https://github.com/magento/magento2/issues/37200) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37199)_

#### Währungs-Code ändert sich nicht im Widget „Neues Produkt“

Das System aktualisiert jetzt den Währungs-Code im Widget Neues Produkt korrekt, wenn die Währung im Frontend geändert wird, und stellt so die Konsistenz der Währungsanzeige auf der Website sicher. Zuvor hatte das Ändern der Währung im Frontend keine Auswirkungen auf den Währungs-Code, der im Widget Neues Produkt angezeigt wird.

_AC-9375 - [GitHub-Problem](https://github.com/magento/magento2/issues/37898) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37899)_

#### Regulärer Preis wird nicht auf PLP für konfigurierbares Produkt angezeigt

Der reguläre Preis wird jetzt auf den Produktlistenseiten für konfigurierbare Produkte angezeigt, die untergeordnete Produkte mit Sonderpreis enthalten.

_ACP2E-2224 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

#### Stock-Informationen werden im visuellen Merchandising-Raster nicht richtig angezeigt

Der Lagerbestand wird jetzt entsprechend dem ausgewählten Geschäft angezeigt.

_ACP2E-2478 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/bdbf97ea)_

#### Widget-Inhalt wird auf CMS-Seite nicht aktualisiert

Das System aktualisiert jetzt den Widget-Inhalt auf einer CMS-Seite, wenn ein Produkt als neu festgelegt und gespeichert wird, und stellt sicher, dass die Seite die aktualisierte Produktsammlung anzeigt. Zuvor wurde die Seite aufgrund der falschen Cache-Identitäten, die für das Widget im Cache verwendet wurden, nicht aktualisiert, um das neue Produkt anzuzeigen.

_ACP2E-2621 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

#### Probleme beim Speichern von erweiterten Preisen für Bundle-Produkte

Leistungsverbesserung durch Einsparung von Produkten im Paket

_ACP2E-2630 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### [On-Premise] Der Neuindizierungsprozess ist beim Erstellen von Katalogpreisregeln ineffizient

Durch das Speichern der Katalogpreisregel werden Indexer nicht ungültig, sondern nur die betroffenen Produkte neu indiziert

_ACP2E-2652 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

#### Aktualisieren der Uhrzeit von Produktattributen vom Typ Datum und Uhrzeit über den CSV-Import

Jetzt verfügen Datums-/Uhrzeitattribute über einen Zeitanteil in den exportierten Daten. Es ist auch möglich, die Zeit für solche Attribute mithilfe des Imports zu aktualisieren. Auch wenn „Einschließungsfelder“ aktiviert ist, werden Attributwerte in der Spalte „additional_attributes“ in doppelte Anführungszeichen gesetzt.

_ACP2E-2679 - [GitHub-Problem](https://github.com/magento/magento2/issues/38306) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Keine passende Fehlermeldung, wenn die Website-ID in der Anfrage falsch ist

Jetzt wurde die entsprechende Fehlermeldung hinzugefügt, die angezeigt wird, wenn die Website-ID in der Anfrage falsch ist. Zuvor gab es keine Validierung, wenn die Website-ID in der Anfrage falsch war.

_ACP2E-2689 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_

#### Das Produktbild geht verloren, nachdem eine vorhandene geplante Aktualisierung gelöscht wurde, die sich nicht auf das Bild auswirkt

Produktbilder werden beim Löschen der Staging-Aktualisierung nicht entfernt.

_ACP2E-2785 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_

#### [Cloud] Falscher Bundle-Produktpreis bei Verwendung mit Stufenpreisen

Zuvor wurden bei der Berechnung bestimmter prozentualer Rabatte, gerundet auf 2 Dezimalpunkte, unterschiedliche Endpreise für die Warenkorb- und Produktlistenseite/Produktdetailseite ermittelt. Nachdem diese Fehlerbehebung angewendet wurde, ist der Endpreis für das Bundle-Produkt derselbe wie auf der Produktdetailseite, der Produktlistenseite und der Mini-Warenkorbseite.

_ACP2E-2799 - [GitHub-Problem](https://github.com/magento/magento2/issues/38091) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### Regel für Katalog-Promotions funktioniert nicht mit dem Attribut quantity_and_stock_status

Das Attribut quantity_and_stock_status wird jetzt von der Regel für die Katalogbeförderung berücksichtigt, die zuvor beim Generieren eines neuen Produkts von der Admin-Seite aus nicht berücksichtigt wurde.

_ACP2E-2805 - [GitHub-Problem](https://github.com/magento/magento2/issues/35627) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/cf34971d)_

#### Produktentität aktualisiert_at Spaltenwerte werden beim Aktualisieren des Preises über die REST-API nicht aktualisiert

Die Spalte „Zuletzt aktualisiert am“ des Produkts vom Administrator wird zum richtigen Zeitpunkt aktualisiert, während die vorhandenen Produkte über die REST-API aktualisiert werden. Zuvor wurde die Spalte „Zuletzt aktualisiert um“ nicht ordnungsgemäß aktualisiert.

_ACP2E-2837 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_

#### Sie können nicht eindeutige Werte über den Produktimport festlegen

Das System erzwingt jetzt beim Produktimport korrekt die Beschränkung des eindeutigen Werts für eindeutige Produktattribute, sodass für dieses Attribut keine doppelten Werte vorhanden sind. Zuvor war es möglich, nicht eindeutige Werte für Produktattribute festzulegen, die über den Produktimport für eindeutige Werte konfiguriert wurden.

_ACP2E-2840 - [GitHub-Problem](https://github.com/magento/magento2/issues/38445) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_

#### Produkte im Frontend verwenden speicherspezifische Daten, wenn der Einzelspeichermodus aktiviert ist

Wenn wir zuvor den Einzelspeichermodus für die standardmäßige Store-Ansicht aktiviert haben, wurden die Änderungen nicht in den Umfang auf Website-Ebene migriert. Wenn wir nach dieser Fehlerbehebung den Einzelspeichermodus aktivieren, werden die standardmäßigen speicheransichtsspezifischen Daten mit Website-spezifischen Daten synchronisiert und die möglichen Konflikte für Produkte und Kategorien werden aufgelöst.

_ACP2E-2843 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_

#### „Standardsortierung nach“ kann in einer Kategorie nicht mit der REST-API festgelegt werden

Aktualisieren Sie default_sort_by korrekt für eine Kategorie über eine REST-/SOAP-API-Anfrage

_ACP2E-2857 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] Der Händler hat Probleme mit der Anzahl der Wunschlisten

Das Hinzufügen eines Produkts zur Wunschliste in einem Geschäft erhöht nicht mehr die Anzahl der Wunschlisten in anderen Geschäften, die im selben Browser geöffnet sind. Wenn beide Stores im selben Browser geladen wurden, stieg die Anzahl der Wunschlisten auch im anderen Store.

_ACP2E-2871 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Kategorieseite im Frontend zeigt leere Slots bei Verwendung des Produktpakets an

Bundle-Produkte, die im aktuellen Store-Kontext nicht verfügbar sind, werden nicht mehr indiziert.

_ACP2E-2874 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/bc37ec76)_

#### [Cloud] Problem mit Zitaten in der Architektur mit mehreren Websites

Zuvor konnten in einer Multi-Website-Architektur mit unterschiedlichen Währungen und Kundengruppen keine Rabatte korrekt auf den Store angewendet werden. Nachdem diese Fehlerbehebung implementiert wurde, wird die Multi-Website-Architektur mit unterschiedlichen Preisnachlässen für Kundengruppen erfolgreich auf verschiedene Stores angewendet.

_ACP2E-2905 - [GitHub-Problem](https://github.com/magento/magento2/issues/38506) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js:658 Nicht erfasster TypFehler: dataRecord.slice beim Bearbeiten von Bundle-Produkten

In der Browser-Konsole tritt beim Löschen der Option aus dem Produktpaket kein JavaScript-Fehler auf.

_ACP2E-2909 - [GitHub-Problem](https://github.com/magento/magento2/issues/38505) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_

#### [Cloud] Bundle Falsche Produktpreise in Bestellbestätigung

Der korrekte Betrag wird für Bundle-Optionen in der Reihenfolge auf der Storefront angezeigt, wenn eine andere Währung als die Basiswährung verwendet wurde.

_ACP2E-2950 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

#### Fehler beim Hinzufügen von YouTube-Videos

Produktbilder und Videos werden im globalen Umfang konfiguriert. Da ein Produktvideo nicht in einem Umfang und nicht in einem anderen enthalten sein kann, wurde die Einstellung für den YouTube-API-Schlüssel auf den globalen Umfang festgelegt.

_ACP2E-2956 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Cloud] URL-Aktualisierung nur für store_id=0

Der „URL-Pfad“ wird jetzt mit der richtigen Store-ID gespeichert. Zuvor war die Store-ID falsch, was dazu führte, dass beim Verschieben von Kategorien falsche URL-Pfade in der Datenbank verbleiben.

_ACP2E-2964 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all ausgeführt und ein Fehler erstellt.

Falsche Produktverknüpfungsdaten in REST-API-Aufrufen verursachen keine kritischen Fehler mehr.

_ACP2E-3009 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Cloud] Problem Nur für Mobilgeräte kann das PDP-Bild nicht gequetscht werden

Das System unterstützt jetzt die Pinch-to-Zoom-Funktion auf Produktdetailseitenbildern in der mobilen Ansicht auf Chrome, wodurch das mobile Benutzererlebnis verbessert wird. Zuvor wurde das Bild in der mobilen Ansicht auf Chrome beim Doppeltippen nicht wie erwartet vergrößert.

_ACP2E-3029 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_

#### Fehlende Beschriftung in LayeredNavigation mit Optionsname 0

Das Problem wurde behoben, indem eine leere Werteprüfung für den Attributwert 0 übersprungen wurde. Zuvor wurde es als leer betrachtet und verursachte das Problem.

_ACP2E-3058 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Kunden sehen Preise von anderen Kundengruppen

Es wurde ein Problem behoben, bei dem Informationen zu Kundengruppen aufgrund des alten Werts der Anfrage „X-Magento-Vary“ in einem falschen Segment gespeichert wurden

_ACP2E-3069 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Fehler beim Löschen von Bundle-Optionen

Das System löscht jetzt die Bundle-Optionen korrekt, ohne einen Fehler auszulösen oder die Seite nicht mehr reagieren zu lassen. Zuvor führte der Versuch, Bundle-Optionen zu löschen, zu einem Fehler „Seite reagiert nicht“ und verhindert, dass das Produkt gespeichert wird.

_ACP2E-3076 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud] Bilddatei ist im New Relic-Fehlerprotokoll nicht vorhanden

Das System synchronisiert jetzt benutzerdefinierte Platzhalterbilder mit dem lokalen Speicher, um sicherzustellen, dass sie bei der Verwendung von Remote-Speicher wie AWS S3 korrekt gerendert werden. Zuvor konnten benutzerdefinierte Platzhalterbilder bei der Verwendung des Remote-Speichers nicht gerendert werden, was zu einer fehlerhaften Bildanzeige und zu Fehlerprotokollen führte.

_ACP2E-3100 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d1f7dc95)_

#### RSS-Feed für neue Produkte wird aufgrund des Cache nicht mit neuen Produkten aktualisiert

Der RSS-Feed für neue Produkte wird jetzt aktualisiert, wenn ein Produkt als neu festgelegt und gespeichert wird

_ACP2E-3103 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_

#### [Cloud] Die GQL-Antwort der Produktmediensammlung ist nicht nach Bildposition sortiert

Das System sortiert jetzt die Elemente in der Mediensammlung korrekt nach der Position in der GraphQL-Antwort, um eine genaue Anzeigereihenfolge zu gewährleisten. Zuvor wurden Elemente in der Mediensammlung nicht nach Position sortiert, was zu einer falschen Anzeigereihenfolge führte.

_ACP2E-3126 - [GitHub-Problem](https://github.com/magento/magento2/issues/37671) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_

#### [Cloud] Unterkategorieelemente werden nicht in den Widgets angezeigt, die im Admin-Backend bearbeitet werden

Die Kategoriestruktur auf der neuen Widget-Seite sollte keine Probleme mehr beim Laden von Kategorien der Stufe 5+ aufweisen. Zuvor fehlten beim Laden des Baums über die Kategorie der Ebene 5 hinaus einige Kategorien.

_ACP2E-3136 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_

#### [cloud] Problem beim Zoomen und Verschieben mit zwei Fingern auf dem echten Mobilgerät

Das System stellt nun auf mobilen Geräten eine konsistente Bildzoom-Funktionalität sicher und sorgt so für ein reibungsloses und vorhersehbares Benutzererlebnis. Zuvor war die Bildzoom-Funktion inkonsistent und zoomte bei der Ansicht auf einem Mobilgerät nach einem bestimmten Punkt plötzlich heraus.

_ACP2E-3198 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

#### Wenn wir die Zuweisung von Produkten zum freigegebenen Katalog aufheben, werden die Produkte auf der Wunschliste nicht gelöscht

Jetzt sind keine Elemente in der Wunschliste sichtbar, wenn ein Produkt nicht im freigegebenen Katalog verfügbar ist. Zuvor wurde auf der Seite mit der Wunschliste fälschlicherweise die Anzahl „1 Artikel“ angezeigt, auch wenn keine Artikel in der Wunschliste verfügbar waren.

_ACP2E-3282 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_

#### Auswahl für alle verwandten Produkte/Aufheben der Auswahl für alle Probleme

Zuvor funktionierten die Schaltflächen „Alle auswählen“/„Alle deaktivieren“ für zugehörige Produkte nicht richtig, wenn ein Produkt manuell ausgewählt wurde. Nach der Fehlerbehebung funktionieren diese Schaltflächen nun auch nach der manuellen Auswahl konsistent und stellen sicher, dass alle Produkte richtig ausgewählt oder deaktiviert sind.

_ACP2E-3286 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] Übersetzen von Warnhinweis-E-Mails in die falsche Sprache

Wenn Stock-/Preis-Warnhinweise für eine Website mit mehreren Store-Ansichten in verschiedenen Sprachen gesendet werden, wird die Sprache für die Store-Ansicht, in der der Warnhinweis erstellt wurde, in der E-Mail verwendet.

_ACP2E-3336 - [GitHub-Code-](https://github.com/magento/magento2/commit/a4cf5e62) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/9f3e63d1)_

#### Die Namen von deaktivierten Kategorien sind in der Kategoriestruktur nicht mehr ausgegraut

Zuvor waren deaktivierte Kategorien in der Kategoriestruktur nicht ausgegraut. Jetzt werden sie mit einem Graustufeneffekt angezeigt.

_ACP2E-3350 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_

#### Konfigurierbares Formular zum Bearbeiten von Produkten verursacht Zeitüberschreitung und Speichererschöpfung

Vor der Fehlerbehebung wurden konfigurierbare Produktvarianten basierend auf allen möglichen Attributoptionskombinationen erstellt. In Fällen, in denen Attribute viele Optionen hatten, führte dies zu einem langwierigen und ressourcenintensiven Vorgang. Jetzt werden konfigurierbare Produktvarianten basierend auf vorhandenen untergeordneten Produktattributen erstellt. Dies führt zu deutlich weniger Berechnungen - und damit zu einer verbesserten Nutzung von Ressourcen.

_ACP2E-3410 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### Das Video wird bei Verwendung von Farbfeldern nicht korrekt geladen und die Option ist über die URL vorausgewählt

Produktvideos werden jetzt auf der konfigurierbaren Produktdetailseite korrekt gerendert, wenn die URL ausgewählte Optionen enthält.

_ACP2E-3454 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### Das Karussell-Widget von PageBuilder zeigt Produkte an, die nicht den Bedingungen entsprechen

Die in Widgets verwendete Produktliste berücksichtigt jetzt die Kategoriebedingung

_ACP2E-3461 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### Validierungsfehler, der für alle Produkte in der Gruppe ausgelöst wird, wenn eine ungültige Menge aufweist

Jetzt wird der Validierungsfehler korrekt für alle Produkte in der Gruppe ausgelöst, wenn ein Produkt eine ungültige Menge hat, was zuvor nicht passiert ist.

_ACP2E-3469 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/56463d5e)_

#### [CLOUD] Sonderpreis wird nicht im konfigurierbaren Produkt angezeigt

Nach der Korrektur wirkt sich die Änderung des Werts „Wird in der Produktliste verwendet“ für das Sonderpreisattribut nicht auf die Anzeige des Sonderpreises für konfigurierbare Produkte aus.

_ACP2E-3513 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

#### Indexer Temporäre Tabellen werden nicht bereinigt, wenn der Prozess beendet wird

Die temporären Tabellen des CatalogRule-Indexers werden jetzt bereinigt, wenn der Indexerprozess beendet wird

_ACP2E-3516 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

#### [QUANS] Fehler bei Kernkomponententests in 2.4.7-p3

Versionshinweise für diesen Test sind nicht erforderlich, da es sich um eine Verbesserung bei Modultests handelt.

_ACP2E-3520 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

#### Leistungsproblem beim Abrufen der Lagermenge für gruppierte Produkte mit mehreren Quellen

Die gruppierte Seite zur Bearbeitung von Produkten und Bundles wurde jetzt optimiert, wenn zugewiesene Produkte über eine große Anzahl von Inventarquellen verfügen.

_ACP2E-3533 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/0208e433)_

#### Präfix ACP2e-3389

Verbesserte Leistung der Admin-Kategorieseite bei einer großen Anzahl von Anker-Kategorien

_ACP2E-3641 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Katalog, Inhalt

#### [Cloud]-Cache wird nicht ungültig gemacht.

Beim Speichern einer CMS-Seite mit einem aktualisierten Design-Layout wurde diese zuvor nicht ordnungsgemäß am Frontend dargestellt. Nachdem diese Fehlerbehebung angewendet wurde, wird das entsprechende Design-Layout am Frontend angezeigt, wenn wir das Design-Layout ändern und die CMS-Seite speichern.

_ACP2E-3063 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

#### [Cloud] Anker-/Nicht-Anker-Kategorien im Inhalts-Widget umgekehrt

Wenn wir zuvor „Anzeigen auf“ > „Ankerkategorien“ ausgewählt haben, wurden alle Kategorien angezeigt, die nicht die hierarchische Beziehung zwischen Anker und Nicht-Anker widerspiegeln. Nachdem diese Fehlerbehebung angewendet wurde, zeigt „Anzeigen ein“ > „Ankerkategorien“ nur Ankerkategorien (auswählbar) an und „Anzeigen ein“ > „Nicht-Ankerkategorien“ zeigt „Nicht-Ankerkategorien“ (auswählbar) an

_ACP2E-3131 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

#### Kategorien funktionieren nicht mit Widgets

Wenn wir den CMS-Block zuvor für verschiedene Anker-/Nicht-Anker-Kategorien gespeichert haben, funktionierte er nicht für die untergeordneten Kategorien, als er am Frontend angezeigt wurde. Nach Anwendung dieser Fehlerbehebung wird der Block an der Vorderseite für verschiedene Kategorien angezeigt.

_ACP2E-3152 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_

### Katalog, Framework

#### Bestellabruf (Sendungen|Creditmemos|Rechnung)Sammlung - Sammlung darf nicht geladen werden

Das System stellt jetzt sicher, dass die Sammlungen für Sendungen und Gutschriften beim Abrufen aus einer Bestellung nicht vorgeladen werden, sodass zusätzliche Filter oder Bestellungen auf diese Sammlungen angewendet werden können. Zuvor wurden diese Sammlungen automatisch geladen, was weitere Änderungen verhinderte.

_AC-9111 - [GitHub-Problem](https://github.com/magento/magento2/issues/37561) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37562)_

#### [Cloud]Follow-up: Beim Datenvergleich bei der Überprüfung, ob die Daten Änderungen aufweisen, stimmen die Werte nicht überein

Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Außerdem werden die von der Zeichenfolge gekapselten Gleitkommazahlen nicht geprüft. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, und führt eine strikte Typübereinstimmung durch

_ACP2E-2949 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_

### Catalog, GraphQL

#### Umgang mit Kategoriefiltern in GraphQL: includeDirectChildrenOnly und category_uid

Beim Filtern nach category_uid werden nur die direkt untergeordneten Kategorien abgerufen.

_ACP2E-3090 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_

#### [Cloud] GraphQL-Produktsortierung funktioniert nicht

Die GraphQL-Produktsortierung nach mehreren Feldern, wenn die Felder in Variablen übergeben werden, funktioniert jetzt erwartungsgemäß.

_ACP2E-3166 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_

#### Stufenpreise geben in GraphQL-Produkten einen falschen Wert zurück (im Vergleich zu Storefront)

Nach der Fehlerbehebung haben die für GraphQL-Anfragen zurückgegebenen Produktstufenpreise den Preis pro einem Element.

_ACP2E-3312 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

### Katalog, Preise, Staging und Vorschau

#### [Cloud] API-Endpunkt für Sonderpreise gibt einen Fehler zurück, wenn eine große Anzahl von Produkten gleichzeitig aktualisiert wird

Jetzt erstellt die Special Price Bulk Update API für jeden Datumsbereich eine einzelne Kampagne anstelle mehrerer geplanter Aktualisierungen für jedes Produkt und jeden Datumsbereich. Außerdem unterstützt es gleichzeitige API-Anfragen für eine schnellere Verarbeitung einer großen Anzahl von SKUs.

_ACP2E-2672 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

### Katalog, Produkt

#### Die Kategorieauswahlstruktur im bearbeiteten Produkt hat nicht die gleiche Reihenfolge wie im Katalog->Kategorien

Das System zeigt nun die Kategorieauswahl im Produktbearbeitungsbereich in der gleichen Reihenfolge wie unter Katalog->Kategorien an, was die Produktverwaltung in großen Katalogen erleichtert. Zuvor wurde die Kategoriestruktur im Produktbearbeitungsabschnitt in der Reihenfolge der Kategorienerstellung angezeigt, unabhängig von der Anzeigereihenfolge, die unter Katalog->Kategorien festgelegt wurde.

_AC-7050 - [GitHub-Problem](https://github.com/magento/magento2/issues/36101) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36104)_

### Katalog, SEO

#### Falsche kanonische URL für Kategorie bei Seite > 1

Zuvor funktionierte die kanonische URL für mehrseitige Inhalte nicht ordnungsgemäß, sodass die Basis-URL durchgängig angezeigt wurde. Nachdem die Fehlerbehebung implementiert wurde, zeigt die kanonische URL für mehrseitige Inhalte jetzt jedoch korrekt die URL mit der Seiten-ID an.

_ACP2E-3653 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Katalog, Suche

#### Produkte werden nicht in der Kategorie und Suche angezeigt, aber direkte Links funktionieren

Zuvor funktionierte das benutzerdefinierte Attribut „Ja/Nein“ mit dem _* „Preis/Attribut_Code“ nicht mit der Indizierung. Nach dieser Korrektur funktioniert das benutzerdefinierte Attribut Ja/Nein erwartungsgemäß.

_ACP2E-2757 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_

#### [Cloud] Elastischer Suchfehler auf bestimmten Kategorieseiten

Zuvor wurde mit dem erwähnten Konfigurations-Ticket, wenn wir den Preis 0 für mehrere Produkte setzen, eine Ausnahme auf der Frontend-Kategorieseite ausgelöst. Nachdem diese Fehlerbehebung angewendet wurde, wenn mehrere Produktpreise 0 sind und wir die Kategorieseite im Frontend laden, wird keine Ausnahme ausgelöst und die Kategorieseite wird erfolgreich geladen.

_ACP2E-3053 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_

#### Beim Erstellen des Objekts ist ein Typfehler aufgetreten: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Ausnahme

Nach der Fehlerbehebung kann eine Instanz der Klasse Magento\CatalogSearch\Model\Indexer\Fulltext erstellt werden, ohne $data anzugeben.

_ACP2E-3345 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] Problem mit Produkten ist nach dem Speichern in Magento Admin nicht in Frontend sichtbar

Nach der Fehlerbehebung werden konfigurierbare Produkte, die untergeordnete Produkte mit langen Namen haben, in der Storefront nicht übersehen.

_ACP2E-3521 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

### Cloud

#### [Cloud] PHPSESSID ändert jede POST-Anfrage

PHPSESSID wird bei POST-Anfragen im Frontend-Bereich für einen angemeldeten Kunden nicht mehr neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde vom Backend aktualisiert wurde

_ACP2E-3010 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_

#### Sitemap-Erzeugungswarnungen

Nach der Fehlerbehebung wird die Sitemap im System-TMP-Verzeichnis generiert und in das endgültige Ziel kopiert.

_ACP2E-3532 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

### Inhalt

#### [Problem] Problem mit der Preisanzeige im Widget „Kürzlich angezeigt“

Das System zeigt jetzt den Preis nicht vorrätiger einfacher Produkte im Widget „Kürzlich angezeigtes Produkt“ korrekt an, wodurch die Konsistenz über alle Widgets und Produktlistenseiten hinweg sichergestellt wird. Zuvor wurde der Preis für nicht vorrätige einfache Produkte aufgrund einer Bedingung in den Preisladevorlagen nicht im Widget „Kürzlich angezeigtes Produkt“ angezeigt.

_AC-10539 - [GitHub-Problem](https://github.com/magento/magento2/issues/38167) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38159)_

#### [Problem] Korrigieren Sie Tippfehler und Grammatik in der Datei acl.xsd

Das System korrigiert jetzt einen Tippfehler und Grammatikfehler in der Datei acl.xsd, wodurch die Klarheit und Genauigkeit der Dokumentation verbessert wird. Zuvor enthielt die Datei acl.xsd einen Tippfehler und eine falsche Grammatik, was möglicherweise zu Verwirrung führen konnte.

_AC-10596 - [GitHub-Problem](https://github.com/magento/magento2/issues/38061) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38046)_

#### PageBuilder-Bannerbild nicht in Galerie sichtbar

Das System zeigt jetzt korrekt Bannerbilder an, die in neu erstellte Ordner in der PageBuilder-Galerie hochgeladen wurden, sodass frühere Konsolenfehler vermieden werden. Vor dieser Fehlerbehebung waren Bannerbilder in der Galerie nicht sichtbar, wenn sie in einen neuen Ordner hochgeladen wurden, was einen Konsolenfehler verursachte.

_AC-10845 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_

#### „Ortsvorwahl nicht festgelegt“ nach Aktualisierung auf 2.4.5-p8

Das System schließt nun den statischen Prozess der Inhaltsbereitstellung erfolgreich ab, wenn das Magento_CSP-Modul aktiviert ist und „dev/js/translate_strategy“ auf „embedded“ gesetzt ist, ohne den Fehler „Area Code Not Set“ auszulösen. Zuvor schlug der statische Prozess der Inhaltsbereitstellung unter diesen Bedingungen mit dem Fehler „Area Code Not Set“ fehl.

_AC-12283 - [GitHub-Problem](https://github.com/magento/magento2/issues/38845) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38922)_

#### Die Widget-Kategoriestruktur wird nicht korrekt gerendert

_AC-12692 - [GitHub-Problem](https://github.com/magento/magento2/issues/39008) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/58e40ceb)_

#### Die Meldung „Standardwert wird verwendet“ wird beim Ändern des Designs auf der Design-Konfigurationsseite nicht angezeigt

Das System enthält jetzt eine separate Spalte, in der die Meldung „Standardwert verwenden“ je nach ausgewähltem Design auf der Design-Konfigurationsseite angezeigt wird. Dadurch wird Klarheit und Sichtbarkeit des Standardwertstatus sichergestellt. Zuvor wurde die Meldung „Standardwert verwenden“ nicht angezeigt, was zu Verwirrung über den Status des ausgewählten Designs führte.

_AC-13054 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problem] Stellt die Abwärtskompatibilität mit TinyMCE-Plug-ins wieder her (nach dem…

Das System stellt jetzt die Abwärtskompatibilität mit TinyMCE-Plug-ins wieder her, sodass Funktionen, die innerhalb des Plug-ins definiert sind, aufgerufen werden können, wenn das Widget von einem anderen Ort verwendet wird. Zuvor gab es aufgrund einer Änderung in der TinyMCE-Version die Plug-ins die Widgets nicht als -Objekt zurück, was zu einem Fehler beim Versuch führte, bestimmte Funktionen auf der Widget-Instanz aufzurufen.

_AC-13569 - [GitHub-Problem](https://github.com/magento/magento2/issues/39262) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39258)_

#### [Problem] Problem beim Hochladen einer Datei im WYSIWYG-Editor auf der Produktseite

Das System zeigt nun die Ordnerstruktur korrekt an und ermöglicht das Hochladen von Bildern im WYSIWYG-Editor auf der Produktseite, auch nachdem zuerst die Registerkarte „Bild und Videos“ erweitert wurde. Zuvor führte das Erweitern der Registerkarte „Bild und Videos“ zunächst dazu, dass die Ordnerstruktur nicht angezeigt wurde und eine Fehlermeldung angezeigt wurde, wenn versucht wurde, ein Bild im WYSIWYG-Editor hochzuladen.

_AC-9638 - [GitHub-Problem](https://github.com/magento/magento2/issues/38026) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38025)_

#### [On-Premise] Problem mit dynamischen Blöcken

Widgets werden jetzt innerhalb dynamischer Blöcke ordnungsgemäß gerendert.

_ACP2E-2392 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a12063bd)_

#### [Cloud] Frontend wird aufgrund eines Problems in der Newsletter-Vorlage nicht geladen

Das Hinzufügen von Blöcken über den CMS-Seiteninhaltsabschnitt führt nicht mehr zu einer Ausnahme

_ACP2E-2693 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836: [Cloud] Investigate-Ausnahme im Protokoll gefunden: InvalidArgumentException: Klasse ist in vendor/magento/module-rule/Model/ConditionFactory.php nicht vorhanden

Wenn Sie eine Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten entfernen, wird keine Ausnahme mehr in den Protokolldateien aufgezeichnet. Zuvor führte das Entfernen einer Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten dazu, dass eine kritische Ausnahme in den Protokollen aufgezeichnet wurde, obwohl dies keine Probleme im Frontend verursachte.

_ACP2E-2836 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### Wechseln zum Einzelspeichermodus - Globale Inhalte werden nicht mehr angezeigt

Das System synchronisiert jetzt Design-Konfigurationen für Store-Ansichten mit Website-Design-Konfigurationen, wenn es den Einzelspeichermodus aktiviert, um sicherzustellen, dass Inhaltsaktualisierungen im Frontend sichtbar sind. Zuvor wurde durch den Wechsel zum Einzelspeichermodus verhindert, dass Inhaltsaktualisierungen in der Storefront widergespiegelt werden.

_ACP2E-2842 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_

#### Page Builder ersetzt ein Bild, wenn versucht wird, einen Link und andere Nutzungsfehler hinzuzufügen.

Wenn Sie jetzt auf ein Bild klicken, werden Links im WYSIWYG-Editor im Textelement von Page Builder geladen. Dadurch werden die richtigen Daten in das Dialogfeld Bild- und Link-Konfiguration geladen. Auch das Hinzufügen eines Links zu einem Bild im Editor funktioniert jetzt ordnungsgemäß. Zuvor wurde das Bild durch einen Link ersetzt.

_ACP2E-2903 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### Die alte Mediensammlung kann Bilder nicht rendern, wenn ein 0-Byte-Bild im Verzeichnis platziert wird

Das System verarbeitet jetzt 0-Byte-Bilder in der Mediensammlung, ohne dass die Funktionalität beeinträchtigt wird, sodass andere Bilder im Verzeichnis wie erwartet angezeigt und ausgewählt werden können. Zuvor verhinderte das Vorhandensein eines 0-Byte-Bildes in der Mediensammlung, dass alle Bilder im Verzeichnis angezeigt oder ausgewählt wurden.

_ACP2E-2970 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/35b1b1da)_

#### Fehler in Page Builder beim Bearbeiten des CMS-Blocks

Das System speichert jetzt mit Page Builder korrekt die im Administratorbereich vorgenommenen Änderungen, ohne den Fehler „Page Builder wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben“ auszulösen. In der Browser-Konsole. Zuvor trat dieser Fehler beim Versuch auf, Änderungen zu speichern, wodurch die erfolgreiche Aktualisierung des Inhalts verhindert wurde.

_ACP2E-3064 - [GitHub-Code-](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [CLOUD] Keine Schaltflächen von Checkout oder Warenkorb bearbeiten im Warenkorbabschnitt

Das Bundle-Produkt wird jetzt fehlerfrei über Widgets zum Warenkorb hinzugefügt.

_ACP2E-3092 - [GitHub-Code-](https://github.com/magento/magento2/commit/b21e5d91) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### [CLOUD] Schaltfläche Bild hochladen funktioniert nicht

Bevor die Schaltfläche Bild hochladen für Banner und Regler von PageBuilder nicht erwartungsgemäß funktionierte, wird durch Drücken von nun der lokale Datei-Manager geöffnet, um das gewünschte Bild zum Hochladen auszuwählen.

_ACP2E-3122 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imageCreateTrueColor(): Der #2 ($height) muss größer als 0 sein. Bestimmtes Bild kann nicht hochgeladen werden

Es wurde das Problem behoben, das beim Hochladen von Bildern mit einer Höhe von 0 über die Mediensammlung zu Fehlern in der Administratorrolle führte und die Assets mit dem Befehl Synchronisieren erfolgreich synchronisierte. Zuvor kann das Bild nicht über die Mediensammlung hochladen, und der Synchronisierungsbefehl schlägt auch fehl, wenn sich ein bestimmtes Bild in der Galerie befindet.

_ACP2E-3127 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_

#### Prototype.js Array.from steht im Konflikt mit der Google Maps-API

Google Maps werden im PageBuilder-Editor jetzt korrekt gerendert. Zuvor verhinderte ein JavaScript-Fehler, dass Google Maps korrekt gerendert wurden.

_ACP2E-3154 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_

#### [Cloud] - CMS-Schieberegler spiegelt nicht die neuesten Änderungen wider

Das Problem wurde behoben, indem sichergestellt wurde, dass die Schiebereglerliste aktualisiert wird, während das Speicherereignis auf dem Bildschirm Folie bearbeiten ausgelöst wird. Zuvor wurde das Problem ausgelöst und verursacht.

_ACP2E-3275 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Auf der CSM-Seite tritt ein Fehler auf, wenn CMS-Blöcke mithilfe des Seiten-Builders in einer bestimmten Reihenfolge eingefügt werden

Zuvor wäre bei einigen Versionen von PHP und OS (Linux) das Rendern von Blöcken, die über PageBuilder auf andere CMS-Blöcke verwiesen haben, mit dem Fehler „Ein unbekannter Fehler ist aufgetreten. Bitte erneut versuchen.“ Jetzt wird der Inhalt der CMS-Blöcke innerhalb eines von PageBuilder gesteuerten Inhalts korrekt wiedergegeben.

_ACP2E-3326 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Vorlagenvorschau-Fehler von PageBuilder bei großen Inhalten

Große Inhalte führten dazu, dass das Canvas-Element über die Beschränkungen des Browsers hinausreichte und einen falschen Wert zurückgab, wodurch der Backend-Code beschädigt wurde (das Bild kann nicht ordnungsgemäß decodiert werden). Es wurde ein Problem behoben, indem die Arbeitsfläche auf die Grenze des universellen Browsers beschränkt wurde.

_ACP2E-3428 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### Neueste Sicherheitsupdates mit TinyMCE 7 fehlender Schriftgröße

Die Auswahl der Schriftgröße und Schriftfamilie ist jetzt im WYSIWYG-Editor verfügbar. Vor dieser Fehlerbehebung waren diese bei TinyMCE 7 nicht in der Editor-Oberfläche verfügbar.

_ACP2E-3430 - [GitHub-Code-](https://github.com/magento/magento2/commit/d50f6b5d) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### TinyMCE 7 Editor Schriftgröße in der Admin in PT und nicht PX Bitte klären

Vor der Korrektur konnten Sie die Schriftgröße in px in WYSIWYG-Bereichen nicht angeben. Jetzt können Sie die Schriftgröße in px statt pt einstellen.

_ACP2E-3483 - [GitHub-Code-](https://github.com/magento/magento2/commit/3f12d152) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### Der Produktinhaltstyp in Page Builder wird ohne korrekte Meldungen reduziert

Vor der Korrektur wurde die HTML-Vorschau nicht richtig generiert, wenn es keine Produkte im Widget gab. Jetzt wird die leere Antwort ordnungsgemäß generiert und das Produkt-Widget wird in der Vorschau korrekt angezeigt.

_ACP2E-3490 - [GitHub-Code-](https://github.com/magento/magento2/commit/3f12d152) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [Page Builder]Hinzufügen der Produktliste zum Blockieren führt zu Fehlern

Das Hinzufügen der Bundle-Produktliste zum -Block über den Seiten-Builder führt jetzt nicht mehr zu Fehlern

_ACP2E-3534 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/344fce23)_

### Kunde/Kunden

#### Frontend - Die Validierung des Geburtsdatums schlägt auf der Seite zur Kundenerstellung fehl

Stellen Sie sicher, dass die gesamte Validierung nach dem Upgrade von moment.js Systemabhängigkeit auf die neueste Nebenversion funktioniert

_AC-12162 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Das Textfeld Region wird nicht zurückgesetzt, wenn die Dropdown-Liste „Land“ geändert wird

Das Textfeld Region wird jetzt zurückgesetzt, wenn das Land im Dropdown-Menü geändert wird. Dadurch wird sichergestellt, dass die vorherigen Werte nicht beibehalten werden. Beim Ändern des Landes aus der Dropdown-Liste wurde das Feld Region zuvor nicht zurückgesetzt, sodass der zuletzt gespeicherte Wert beibehalten wurde.

_AC-8499 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ea26621)_

#### Beim Löschen eines Kunden werden nicht alle Browser-Sitzungsdaten in der Storefront für angemeldete und gelöschte Kunden gelöscht

Durch das Löschen eines Kunden werden jetzt alle Browser-Sitzungsdaten aus der Storefront für angemeldete und gelöschte Kunden wie erwartet bereinigt. Der Käufer kann weiterhin einkaufen, und sein Browser behandelt seine Sitzung als Gastsitzung. Wenn das Kundenkonto eines angemeldeten Käufers aus dem Admin gelöscht wurde, gab es zuvor im Browser des Käufers JavaScript-Fehler.

_AC-9240 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_

### Framework

#### [Question]Unused Type configuration in `app/code/Magento/Translation/etc/di.xml`

Das System entfernt jetzt nicht verwendete Abhängigkeiten in der Konfiguration, was die Code-Sauberkeit und -Effizienz insgesamt verbessert. Zuvor gab es in der Konfiguration nicht verwendete Abhängigkeiten, die zu keiner Funktion beitrugen.

_AC-10037 - [GitHub-Problem](https://github.com/magento/magento2/issues/38030) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38064)_

#### Frage/Problem des Endpunkts V1/customers/password

Das System hält sich jetzt bei der Verarbeitung von Passwortänderungsanfragen über die API an die in der Verwaltungs-Benutzeroberfläche festgelegten Einschränkungen, um einen potenziellen Missbrauch der Passwortrücksetzfunktion zu verhindern. Zuvor konnte die API Passwortänderungsanfragen außerhalb der in der Verwaltungs-Benutzeroberfläche definierten Regeln verarbeiten, was möglicherweise einen konstanten Stream von Zurücksetzungs-E-Mails ermöglichte, wenn gültige E-Mails bekannt waren.

_AC-10654 - [GitHub-Problem](https://github.com/magento/magento2/issues/38238) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Lackkonfiguration schließt nicht alle Marketing-Parameter aus

Das System schließt jetzt alle gängigen Marketing-Parameter in der Lackkonfiguration korrekt aus, um eine genaue Verfolgung und Analyse zu gewährleisten. Zuvor wurden bestimmte Marketing-Parameter wie „gad_source“, „srsltid“ und „msclpid“ nicht ausgeschlossen, was zu möglichen Ungenauigkeiten bei der Datenerfassung führen kann.

_AC-10738 - [GitHub-Problem](https://github.com/magento/magento2/issues/38298) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39188)_

#### Indizierungsprozess für Katalogsuchindex-Fehler

Das System führt nun den Befehl zur Neuindizierung erfolgreich aus, ohne dass Fehler auftreten, unabhängig von der mit PHP kompilierten libxml-Version. Zuvor führte die Ausführung des Befehls re-index zu einem Fehler „Catalog Search index process error during indexation process“, wenn PHP mit bestimmten Versionen von libxml kompiliert wurde.

_AC-10838 - [GitHub-Problem](https://github.com/magento/magento2/issues/38254) - [GitHub-Code-](https://github.com/magento/magento2/pull/38553) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

#### Filter CREATED_AT, STATUS und GRAND_TOTAL zur Abfrage von Kundenaufträgen hinzugefügt und Fehler bei mehreren Filtern behoben

Das System unterstützt jetzt die Verwendung der Filter CREATED_AT, STATUS und GRAND_TOTAL in Kundenauftragsabfragen und hat ein Problem behoben, bei dem mehrere Filter nicht korrekt angewendet wurden. Zuvor hat das System diese Filter nicht unterstützt und würde nicht alle Filter anwenden, wenn mehr als einer in einer Abfrage verwendet wurde.

_AC-10941 - [GitHub-Problem](https://github.com/magento/magento2/issues/38392) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36949)_

#### Zufällige Flut von Abfragen aus verwandten / Upsell / Crosssell-Blöcken und Preisindizierung

Das System optimiert jetzt Abfragen aus verwandten, Upsell- und Crosssell-Blöcken, verbessert die Leistung und verhindert, dass die Site aufgrund übermäßiger Abfragen abstürzt. Zuvor konnte das System mit Abfragen aus diesen Blöcken überlastet werden, was zu erheblichen Verzögerungen führte und möglicherweise die Site lahmlegte.

_AC-10991 - [GitHub-Problem](https://github.com/magento/magento2/issues/36667) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38050)_

#### Ausnahme: Warnung: Versuch, auf Array-Offset in zuzugreifen… -> Calendar.php seit Upgrade auf ICU 74.1 (PHP Intl)

Commerce protokolliert die folgende Ausnahme nicht mehr in der Datei „Exception.log“, wenn ein Käufer oder Händler die Storefront oder den Administrator besucht: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [GitHub-Problem](https://github.com/magento/magento2/issues/38214) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38364)_

#### [Problem] Beheben von Problemen mit Kundendaten, wenn das Formular ein Element mit dem Namen `method` enthält

Das System identifiziert nun das Attribut „method“ in Formularübermittlungen korrekt, auch wenn ein Element namens „method“ im Formular vorhanden ist. Dadurch wird eine präzise Verarbeitung der Kundendaten gewährleistet. Wenn ein Formularelement zuvor „Methode“ genannt wurde, würde dies die Identifizierung des Attributs „Methode“ bei Formularübermittlungen beeinträchtigen, was zu potenziellen Problemen bei der Verarbeitung von Kundendaten führen würde.

_AC-11476 - [GitHub-Problem](https://github.com/magento/magento2/issues/38484) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38449)_

#### [Problem] Beheben von PHPDocs für \Magento\Framework\Data\Collection::getItemById

Die PHPDocs für die Methode \Magento\Framework\Data\Collection::getItemById wurden aktualisiert, um null als möglichen Rückgabetyp einzuschließen und Probleme mit statischen Analyse-Tools zu beheben. Zuvor wurde in den PHPDocs der Methode nicht null als möglicher Rückgabetyp angegeben, was zu Warnungen oder Fehlern bei der statischen Analyse führte, wenn die Methode in bedingten Anweisungen verwendet wurde.

_AC-11489 - [GitHub-Problem](https://github.com/magento/magento2/issues/38485) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38439)_

#### [Problem] Nur gültige Voreinstellungen während der `setup:di:compile` zulassen

Das System gibt jetzt während des `setup:di:compile`-Befehls einen Fehler aus, wenn eine Voreinstellung für eine Klasse erstellt wird, die nicht vorhanden ist oder speziell ausgeschlossen wurde, sodass nur gültige Voreinstellungen zulässig sind. Zuvor schlugen diese Szenarien im Hintergrund fehl und machten möglicherweise alle Plug-ins, die mit den ursprünglichen Klassen verknüpft sind, unbrauchbar.

_AC-11592 - [GitHub-Problem](https://github.com/magento/magento2/issues/38517) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33161)_

#### Magento versucht, die schreibgeschützte Eigenschaft in der __wakeup-Methode von LoggerProxy zu ändern

Das System ermöglicht jetzt die Änderung von zuvor schreibgeschützten Eigenschaften in der __wakeup-Methode von LoggerProxy, um einen reibungslosen Betrieb zu gewährleisten, ohne die Benutzer zu zwingen, eine Problemumgehung zu verwenden. Zuvor hatte der Versuch, den Wert einer schreibgeschützten Eigenschaft in der WakeUp-Methode __ LoggerProxy neu zuzuweisen, Probleme verursacht.

_AC-11651 - [GitHub-Problem](https://github.com/magento/magento2/issues/38526) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_

#### [Problem] AC-2039 AC-1667 Upgrade TinyMCE-Referenzen

Die tinymce-neueste Version wurde in composer.json aktualisiert.

_AC-11681 - [GitHub-Problem](https://github.com/magento/magento2/issues/38533) - [GitHub-Code-](https://github.com/magento/magento2/pull/36543) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker funktioniert nicht in mehreren Threads

Das System unterstützt jetzt Process Fork für die MView-Indizierung, wodurch Fehler während der Indexerausführung bei der Ausführung auf mehreren Threads verhindert werden. Zuvor führte das Ausführen von ChangelogBatchWalker auf mehreren Threads zum Löschen von Tabellen, die von anderen Threads verwendet wurden, was einen Fehler während der Indexerausführung verursachte.

_AC-11696 - [GitHub-Problem](https://github.com/magento/magento2/issues/38246) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38248)_

#### [Problem] Umbenennen einer falsch benannten Variablen

Das System benennt nun die Variable korrekt, die den Betrag an Geld enthält, der noch zurückerstattet werden kann, um Verwirrung beim Debugging zu vermeiden. Zuvor wurde diese Variable fälschlicherweise als totalRefund bezeichnet, was zu Missverständnissen für Entwickler führen konnte.

_AC-11781 - [GitHub-Problem](https://github.com/magento/magento2/issues/38609) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36205)_

#### [Problem] Übergeben von benutzerdefinierten Attributen an den aktuellen Link über XML

Das System ermöglicht jetzt die Übergabe benutzerdefinierter Attribute über XML an den aktuellen Link, um sicherzustellen, dass diese Attribute korrekt angezeigt werden, auch wenn der Link die aktuelle Seite ist. Zuvor wurden keine benutzerdefinierten Attribute für den aktuellen Seitenlink angezeigt, da die Methode getAttributesHtml() für den aktuellen Link nicht verwendet wurde.

_AC-11809 - [GitHub-Problem](https://github.com/magento/magento2/issues/38500) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30070)_

#### Der integrierte FPC-Cache ist in Version 2.4.7 für einige Konfigurationen fehlerhaft

Das System speichert Seiten jetzt korrekt zwischen, wenn der Parameter MAGE_RUN_CODE festgelegt ist, was eine optimale Leistung gewährleistet. Zuvor wurden Seiten unter diesen Bedingungen nicht zwischengespeichert, was zu potenziellen Leistungsproblemen führte.

_AC-11819 - [GitHub-Problem](https://github.com/magento/magento2/issues/38626) - [GitHub-Code-](https://github.com/magento/magento2/pull/38646) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [Problem] Behebung von Inkonsistenzen bei der Ausnahmebehandlung zwischen Entwickler- und Produktionsmodus

Das System verarbeitet jetzt Ausnahmen konsistent zwischen dem Entwickler- und dem Produktionsmodus, wodurch eine unerwartete Weiterleitung zur Anmeldeseite verhindert wird, wenn eine Ausnahme ausgelöst wird. Zuvor konnte eine Inkonsistenz bei der Ausnahmebehandlung zu einer Umleitung zur Anmeldeseite im Produktionsmodus führen, anstatt die Ausnahmemeldung anzuzeigen.

_AC-11829 - [GitHub-Problem](https://github.com/magento/magento2/issues/38639) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37712)_

#### Übersetzung &#39;PayPal-Konto&#39; in token_list.phtml ersetzen

Das System kennzeichnet den Abschnitt für Token-fähige Konto-Zahlungsmethoden auf der Seite „Gespeicherte Zahlungsmethoden“ nun als „Konto“ anstelle von „PayPal-Konto“, wodurch er seine Funktion besser darstellt. Zuvor wurde dieser Abschnitt speziell als „PayPal-Konto“ gekennzeichnet, was irreführend war, wenn andere Token-fähige Konto-Zahlungsmethoden hinzugefügt wurden.

_AC-11852 - [GitHub-Problem](https://github.com/magento/magento2/issues/35622) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37959)_

#### Die Abwärtskompatibilität wurde für die Klasse Magento\Catalog\Model\ProductRepository nicht mehr unterstützt

Die ProductRepository-Klasse erhält jetzt die Abwärtskompatibilität aufrecht, indem sie die Initialisierungs-Hilfsklasse als zweiten Parameter wiederherstellt und sicherstellt, dass Module, die von dieser Klasse erweitert werden, erwartungsgemäß funktionieren. Zuvor führte das Entfernen des Initialization Helper aus dem Konstruktor in der ProductRepository-Klasse zu einem Verlust der Abwärtskompatibilität, was Benutzer zwang, eine Problemumgehung zu verwenden.

_AC-11874 - [GitHub-Problem](https://github.com/magento/magento2/issues/38669)_

#### [Problem] Statische Inhaltsbereitstellung - Typfehler

Das System verarbeitet jetzt leere LESS-Dateien während der Bereitstellung statischer Inhalte korrekt und zeigt die Fehlermeldung „LESS-Datei ist leer“ an. Zuvor wurde ein Fehler vom Typ „Falsch“ ausgelöst, wenn während der Bereitstellung eine leere LESS-Datei auftrat.

_AC-11905 - [GitHub-Problem](https://github.com/magento/magento2/issues/38682) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38683)_

#### [Problem] [Anzeigen] Zusätzliches Leerzeichen im Link- und Skript-Tag entfernt

Das System stellt jetzt sicher, dass es keine zusätzlichen Leerzeichen in den Link- und Skript-Tags gibt, was einen saubereren und effizienteren Code bietet. Zuvor konnten zwischen Attributen in den Link- und Skript-Tags doppelte Leerzeichen gefunden werden.

_AC-12002 - [GitHub-Problem](https://github.com/magento/magento2/issues/32920) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32919)_

#### [Problem] Vermeiden Sie eine Fehlkonfiguration in der Endlosschleife.

Das System vermeidet jetzt eine Endlosschleife, indem es in virtuellen Typkonfigurationen die selbstreferenzielle Zuordnung verhindert. Dadurch wird sichergestellt, dass die Anwendung beim Versuch, einen selbstverweisenden Knoten zu dereferenzieren, nicht in einer Endlosschleife hängt. Wenn eine Konfiguration eines virtuellen Typs zuvor selbstverweisend war, würde dies dazu führen, dass sich die Anwendung unbegrenzt dreht.

_AC-12127 - [GitHub-Problem](https://github.com/magento/magento2/issues/38822) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38794)_

#### Object Manager wird nicht für Magento\Csp\Model\Mode\Data\ModeConfigured verwendet

Das System verwendet nun den Objekt-Manager beim Erstellen des ModeConfiged-Objekts korrekt, sodass Plug-ins für dieses Objekt verwendet werden können. Zuvor wurde der Objekt-Manager nicht verwendet, was verhinderte, dass Plug-ins auf das ModeConfiged-Objekt angewendet wurden.

_AC-12299 - [GitHub-Problem](https://github.com/magento/magento2/issues/38875) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38886)_

#### Falsche Blockkommentare in Produkt- und Preiswarnhinweisen

Der Blockkommentar für die Methode deleteCustomer in den Warnhinweisen für Warenbestand und Preise wurde korrigiert, um genau widerzuspiegeln, dass die Methode alle Warenbestand- oder Preiswarnhinweise löscht, die mit einer bestimmten Kundin oder einem bestimmten Kunden und einer bestimmten Website verbunden sind, nicht mit dem Kunden von der Website. Zuvor wurde in dem Kommentar fälschlicherweise angegeben, dass die Methode zum Löschen eines Kunden von der Website war.

_AC-12540 - [GitHub-Problem](https://github.com/magento/magento2/issues/38939) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39001)_

#### [Problem] Verwenden Sie die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration.

Das System verwendet jetzt die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration, wodurch die Netzwerkübertragung und der Overhead von Daten, der von einer bestimmten Code-Version abhängt, reduziert werden. Diese Änderung verhindert das Überschreiben des Caches in freigegebenen Instanzen beim Austausch von Containern, was zu verbesserter Stabilität und reduzierten Ausfallzeiten führt. Zuvor verwendeten bestimmte Kernklassen gemeinsame Konfigurationstypen, was aufgrund von Unterschieden in den Codeversionen über mehrere Server hinweg zu Cache-Überschreibungen oder Anwendungsausfällen führen konnte.

_AC-12594 - [GitHub-Problem](https://github.com/magento/magento2/issues/38785) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29954)_

#### [Problem] Verweise auf Dateien aus ExtJS entfernen, die aus e1ccdb entfernt wurden…

Das System entfernt jetzt Verweise auf Dateien aus ExtJS, die zuvor entfernt wurden, wodurch Fehler in der Browser-Konsole und der Systemprotokolldatei vermieden werden. Zuvor verursachten diese Verweise Fehler, da die referenzierten Dateien nicht vorhanden waren.

_AC-12597 - [GitHub-Problem](https://github.com/magento/magento2/issues/38960) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38951)_

#### [Problem] Kleinere Bereinigung: Fehlerhafte Verwendung von sprintf wurde behoben, es werden nur 2 Platzhalter verwendet…

Das System verwendet nun die Sprintf-Funktion korrekt mit der entsprechenden Anzahl von Platzhaltern, was die Code-Sauberkeit und -Konsistenz verbessert. Zuvor wurde die Sprint-Funktion fälschlicherweise mit einem zusätzlichen Argument verwendet, was zwar keine größeren Probleme verursachte, aber nicht die richtige Verwendung war.

_AC-12778 - [GitHub-Problem](https://github.com/magento/magento2/issues/39062) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38628)_

#### PHP 8.2.15 entfernte FTP-Erweiterung

Das System enthält jetzt die FTP-Erweiterung als Abhängigkeit in der Datei composer.json, wodurch die erfolgreiche Konfiguration von CSV-Importen über FTP sichergestellt wird. Zuvor wurde beim Versuch, CSV-Importe über FTP zu konfigurieren, ein Fehler ausgelöst, da die FTP-Erweiterung im PHP-Paket fehlt.

_AC-12857 - [GitHub-Problem](https://github.com/magento/magento2/issues/39083) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problem] Behebt den Verweis falscher Klassen in Magento-Modulen.

Das System verweist jetzt korrekt auf Klassen in -Modulen, um einen reibungsloseren Betrieb zu gewährleisten und Abstürze aufgrund nicht vorhandener Klassen zu verhindern. Dazu gehören eine Fehlerbehebung im Indexer- und Creditmemo-Modul sowie die Implementierung der HttpGetActionInterface-Klasse in der PrintAction-Klasse. Zuvor führten falsche Klassenverweise zu Fehlern und potenziellen Systemabstürzen, und bestimmte Funktionen, wie der Dateiname für CreditMemo-PDF-Dateien und die Neuindizierung von Aktien, funktionierten nicht wie erwartet.

_AC-12869 - [GitHub-Problem](https://github.com/magento/magento2/issues/39126) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37784)_

#### Möglichkeit, Bereich für `dev:di:info` CLI-Befehl zu definieren

Das System ermöglicht es Entwicklerinnen und Entwicklern jetzt, einen Bereich für den `dev:di:info` CLI-Befehl zu definieren, wodurch der Entwicklungs- und Debugging-Prozess verbessert wird. Zuvor konnte dieser Befehl nur Informationen für den Bereich GLOBAL anzeigen.

_AC-12964 - [GitHub-Problem](https://github.com/magento/magento2/issues/38758) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38759)_

#### [Problem] Fügen Sie die Eigenschaft isMultipleFiles zur Vorlage des Formularelements hinzu

Diese Fehlerbehebung verhindert, dass die Schaltfläche „Nach Bild suchen oder Bild hierher ziehen“ ausgeblendet wird, wenn ein Bild in einem Bildelement mit mehreren Dateien hinzugefügt wird.

_AC-13149 - [GitHub-Problem](https://github.com/magento/magento2/issues/39219) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36325)_

#### [Problem] Entfernen Sie alle Marketing-GET-Parameter, um den Cache zu minimieren

Das System entfernt jetzt alle Marketing-GET-Parameter, um die Cache-Nutzung zu optimieren, und spiegelt die Logik wider, die bei der Verwendung von Varnish verwendet wird. Zuvor konnten diese Parameter zu einer Aufblähung des Cache und einer verringerten Leistung führen.

_AC-13279 - [GitHub-Problem](https://github.com/magento/magento2/issues/39266) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39099)_

#### [Problem] [PHPDOC] Fehlerbehebung für fehlerhafte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries()

Das PHPDoc für die Methode AllowedCountries::getAllowedCountries() wurde korrigiert, um genaue Informationen bereitzustellen und so die Klarheit und Nützlichkeit der Dokumentation zu verbessern. Bisher enthielt das PHPDoc für diese Methode falsche Informationen, was zu Verwirrung oder Missbrauch der Methode führen konnte.

_AC-13345 - [GitHub-Problem](https://github.com/magento/magento2/issues/39246) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39241)_

#### [Problem] Entfernt Code für PHP-Versionen, die wir nicht mehr unterstützen.

Entfernen von Code für PHP-Versionen, die in Magento nicht mehr unterstützt werden

_AC-13348 - [GitHub-Problem](https://github.com/magento/magento2/issues/39361) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39202)_

#### [Problem] ImageMagick-Adapter mit PHP8 kompatibel machen (implizite Konvertierung von float zu int)

Das System stellt nun die Kompatibilität mit PHP8 sicher, indem es bei der Berechnung der Bildabmessungen die Gleitkommazahlen korrekt verarbeitet und Fehler durch implizite Konvertierung von float in int verhindert. Zuvor konnte die Berechnung der Bildabmessungen zu Gleitkommazahlen führen, die bei impliziter Rundung einen Fehler verursachen würden.

_AC-13417 - [GitHub-Problem](https://github.com/magento/magento2/issues/39402) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37362)_

#### [Problem] [PHPDOC] Schlechtes phpdoc beheben Magento\Framework\App\Config\ScopeConfigInterface

Durch diese Aktualisierung werden die PHPDoc-Anmerkungen in Magento\Framework\App\Config\ScopeConfigInterface korrigiert, damit sie den Typ des $scopeCode-Arguments für die Methoden getValue und isSetFlag genau widerspiegeln.

_AC-13537 - [GitHub-Problem](https://github.com/magento/magento2/issues/39492) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http hängt von der Ursachenformel ab OK

Die Prüfung der „OK“-Phrase wurde aus Magento\Framework\Filesystem\Driver\Http::isExists entfernt.

_AC-13725 - [GitHub-Problem](https://github.com/magento/magento2/issues/39546) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39558)_

#### Der Rasterindizierer des Kunden funktioniert im Zeitplanmodus nicht ordnungsgemäß

Frühere Kundenraster wurden sofort aktualisiert, aber nach der Fehlerbehebung wird das Kundenraster nach der Cron-Ausführung aktualisiert, es wird jedoch nicht sofort wiedergegeben.

_AC-13810 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1da9ba6f)_

#### Tippfehler in einer JS-Datei.

Das System verwendet nun den Begriff „Abonnenten“ in der JavaScript-Datei korrekt, um eine ordnungsgemäße Funktionalität der zugehörigen Funktionen sicherzustellen. Zuvor führte ein typografischer Fehler in der JavaScript-Datei zur falschen Verwendung des Begriffs „Abonnenten“.

_AC-6754 - [GitHub-Problem](https://github.com/magento/magento2/issues/36163) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36171)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich jetzt an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.

_AC-8353 - [GitHub-Problem](https://github.com/magento/magento2/issues/37253) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37003)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Customer` (Teil 2)

Das System hält sich jetzt an den Kodierungsstandard, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.

_AC-8356 - [GitHub-Problem](https://github.com/magento/magento2/issues/37250) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37000)_

#### Durch Leerzeichen in der EditorConfig-Syntax wird die Regel für `[&lbrace;composer,auth&rbrace;.json]` unterbrochen.

Nach der Behebung eines Syntaxfehlers in editorconfig wendet das System jetzt einen Einzug mit vier Leerzeichen korrekt auf die Dateien composer und auth.json an. Aufgrund eines Leerzeichens in der EditorConfig-Syntax wurden diese Dateien zuvor falsch mit einem Einzug aus zwei Leerzeichen formatiert.

_AC-8659 - [GitHub-Problem](https://github.com/magento/magento2/issues/37394) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37395)_

#### [Problem] Verbesserung der Cron-Fehlerprotokollierung

Das System erfasst und protokolliert jetzt sowohl STDERR als auch STDOUT für Cron-Prozesse und liefert wertvolle Diagnoseinformationen in Szenarien, in denen Cron-Prozesse fehlschlagen. Zuvor wurden Fehlermeldungen innerhalb von Cron-Prozessen nicht aufgezeichnet, und STDERR und STDOUT für Cron-Gruppen, die in separaten Prozessen ausgeführt werden, gingen verloren.

_AC-8662 - [GitHub-Problem](https://github.com/magento/magento2/issues/37453) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32690)_

#### [Problem] Fügt der Ausgabe bestimmter Setup-Befehlszeilenbefehle einige weitere Farben hinzu

Das System fügt jetzt der Ausgabe bestimmter Befehle der Befehlszeilenschnittstelle (Command Line Interface, CLI) mehr Farben hinzu, was die Lesbarkeit und das Benutzererlebnis verbessert. Bisher war die Ausgabe dieser Befehle aufgrund fehlender Farbdifferenzierung schwieriger zu lesen.

_AC-8984 - [GitHub-Problem](https://github.com/magento/magento2/issues/29335) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29298)_

#### Beim Upgrade von Magento wird „general/region/state_required“ zurückgesetzt, wenn ein neues Land mit dem erforderlichen Bundesland bzw. der erforderlichen Region hinzugefügt wird.

Das System fügt das geänderte Land jetzt nur noch dann zur Konfiguration „general/region/state_required“ hinzu, wenn ein neues Land mit den erforderlichen Status hinzugefügt wird. Dadurch wird jede Unterbrechung des benutzerdefinierten Codes vermieden, bei der davon ausgegangen wird, dass die Region deaktiviert ist. Zuvor würde das Hinzufügen eines neuen Landes mit erforderlichen Status die Konfiguration „general/region/state_required“ auf Standardländer mit einem erforderlichen Status zurücksetzen und möglicherweise den Shop zerstören.

_AC-9630 - [GitHub-Problem](https://github.com/magento/magento2/issues/37796) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38076)_

#### Unterschied in weniger Kompilierung zwischen PHP &amp; NodeJS Library (grunt) mit komplizierten `calc` Ausdrücken

Behebung des Unterschieds in weniger Kompilierung zwischen PHP &amp; NodeJS Library (grunt) nach dem Update wikimedia/less.php:^5.x

_AC-9712 - [GitHub-Problem](https://github.com/magento/magento2/issues/37841) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b34c0a75)_

#### Bei der Ausführung einer partiellen Indizierung tritt der Fehler „Basistabelle oder Ansicht nicht gefunden“ auf

Die teilweise Neuindizierung funktioniert jetzt mit einem großen Änderungsprotokoll im Falle einer sekundären DB-Verbindung korrekt

_ACP2E-2692 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_

#### Probleme nach dem Upgrade von MariaDB auf 10.5.1 oder höher

Es wurde ein Problem behoben, bei dem Datums-/Uhrzeitwerte in einer DB nach dem MySQL-Upgrade in 0000-00-00 00:00:00 konvertiert wurden

_ACP2E-2844 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a12063bd)_

#### Nicht übereinstimmender Typ beim Datenvergleich bei der Überprüfung, ob die Daten Änderungen aufweisen

Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, führt eine strikte Typübereinstimmung durch.

_ACP2E-2855 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud]-Import kann nicht mit Verzeichnis-Var verwendet werden

Produkt kann unabhängig vom Dateinamen erfolgreich importiert werden.

_ACP2E-2959 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Auf dem iPad mini werden das Menü und die Kopfzeile als Mobilgerät geladen. Stattdessen sollten sie als Desktop geladen werden.

Das System behandelt Geräte mit einer Breite von 768 Pixel jetzt als Desktop, um sicherzustellen, dass das Menü und die Kopfzeile korrekt geladen werden. Zuvor wurden Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobilansicht geladen wurden.

_ACP2E-2966 - [GitHub-Code-](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### Die Änderung der Spaltenlänge über db_schema.xml funktioniert nicht bei Fremdschlüsseln

Das Ändern der Spalte mit dem Fremdschlüssel über das deklarative Schema verursacht jetzt keine Fehler mehr bei MariaDB

_ACP2E-3230 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

#### Einige der Beziehungsdatensätze werden beim Speichern des Bestelldatensatzes in der DB gespeichert

Vor der Behebung wurden unnötige UPDATE-Abfragen ausgelöst, die die Leistung beeinträchtigen können. Nach der Fehlerbehebung wurden die unnötigen UPDATE-Abfragen entfernt.

_ACP2E-3361 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] In Admin gibt es viele JavaScript-Fehler in der Konsole

Zuvor gab es im Admin-Bedienfeld viele JavaScript-Fehler in der Konsole. Im Admin-Bedienfeld gibt es nun keine JavaScript-Fehler mehr in der Konsole, und alle standardmäßigen JavaScript-Funktionen werden problemlos ausgeführt.

_ACP2E-3375 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_

#### [Cloud] Magento: Warteschlangennachricht wurde gelöscht

Warteschlangennachrichten werden jetzt ordnungsgemäß gelöscht. Vor der Fehlerbehebung hätten, da das SQL-Warteschlangensystem verwendet wurde, neue Nachrichten gelöscht werden können, wenn die Bereinigungswarteschlangennachricht gleichzeitig ausgeführt wurde.

_ACP2E-3387 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Entsprechende Cache-Schlüsseleinträge sind in Cache-Tags nicht verfügbar, daher funktioniert die Cache-Bereinigung nicht ordnungsgemäß

Der LUA-Modus ist jetzt standardmäßig für den Redis-Cache-Garbage Collector aktiviert, um Race-Bedingungen zu verhindern

_ACP2E-3537 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a52ff98f)_

#### MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK-Wert wird ignoriert

Nach der Fehlerbehebung wird eine auf „false“ gesetzte ENV-Variable als bool/false und nicht als String „false“ behandelt.

_ACP2E-3681 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

#### [Problem] Einführung der Unterstützung benutzerdefinierter Skalartypen für das GraphQL-Schema

Das System unterstützt jetzt benutzerdefinierte Skalartypen für GraphQL-Schemata, sodass Entwickelnde benutzerdefinierte Skalartypen und Implementierungen definieren können. Diese Funktion kann besonders nützlich sein, um Werte auszudrücken, die möglicherweise einer Validierung bedürfen, z. B. HTML, E-Mails, URLs, Daten usw., und für komplexere Fälle wie EAV-Attribute. Zuvor unterstützte das System nicht die Verarbeitung von benutzerdefinierten Skalartypen in GraphQL.

_AC-7976 - [GitHub-Problem](https://github.com/magento/magento2/issues/36877) - [GitHub-Code-](https://github.com/magento/magento2/pull/34651) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

### Framework, UI-Framework

#### Möglichkeit, den Konfigurationswert zu überschreiben, selbst wenn er gesperrt ist

Zuvor konnte die Design-Konfiguration nicht über den Befehl bin/magento config:set festgelegt werden und gesperrte Werte konnten durch Manipulation des Formulars, das sie anzeigte, geändert werden. Nach dem Fix können gesperrte Werte, die von cli mit —lock-env oder —lock-conf gesetzt wurden, nicht mehr aktualisiert werden.

_ACP2E-3324 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQL führt die Verarbeitung von Headern auch dann aus, wenn der Header-Wert die Validierung nicht besteht

Das System stellt jetzt sicher, dass die Header-Verarbeitung nur einmal und nur dann ausgeführt wird, wenn der Header-Wert die Validierung besteht, was die Sicherheit erhöht und potenzielle Sicherheitslücken verhindert. Zuvor wurde die Header-Verarbeitung auch dann ausgeführt, wenn der Header-Wert die Validierung nicht bestanden hat, was zu potenziellen Sicherheitslücken und unerwartetem Verhalten aufgrund der doppelten Verarbeitung von Header-Werten führte.

_AC-11729 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_

#### Die physischen Geschenkkartenoptionen haben nicht die richtige Sortierreihenfolge

Das System sortiert jetzt bei der Abfrage über GraphQL die Optionen physischer Geschenkkartenprodukte korrekt, wodurch eine konsistente Darstellung mit dem Luma-Design gewährleistet ist. Zuvor war die Sortierreihenfolge gemäß dem Luma-Design falsch, was zu einer falschen Anzeige und Sortierung von Optionen wie Absendername, Empfängername und Betrag führte.

_AC-8951 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_

#### [GraphQL] Resolver-Cache wird beim Erstellen/Bearbeiten/Verschieben/Löschen einer Staging-Aktualisierung ungültig

Das System stellt jetzt sicher, dass der Resolver-Cache nicht beim Erstellen, Bearbeiten, Verschieben oder Löschen eines Staging-Updates ungültig gemacht wird, sondern nur, wenn das Staging-Update auf die Entität angewendet wird. Zuvor wurde der Resolver-Cache vorzeitig invalidiert, noch bevor die Staging-Aktualisierung angewendet wurde, was zu unnötigen Cache-Invalidierungen führte.

_AC-9157 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Fastly-Cache für die Aktualisierung des Inhalts-Staging nicht gelöscht

Jetzt wird der Antwort-Cache für GraphQL mit PageBuilder-Inhalt ungültig, wenn die Entitäten für den PageBuilder-Inhalt aktualisiert werden.

_ACP2E-2642 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_

#### Deaktivieren der mehrschichtigen Navigation : Die Aggregation wird nicht aus GraphQL entfernt

Das Problem wurde behoben, nachdem die Prüfung bei der Anforderung einer Produktsuche mit Kategorieaggregationen über eine GraphQL-Abfrage in der Admin-Konfigurationseinstellung von „Katalog > Mehrschichtige Navigation > Kategoriefilter anzeigen“ angewendet wurde.

_ACP2E-2653 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/12e071c3)_

#### GraphQL-Produktanruf, der den Preisfilter enthält `&lbrace;from:&quot;0&quot;&rbrace;` kein Ergebnis zurückgibt

Zuvor gab GraphQL-Produkte, die mit dem Filter nach Nullpreisen suchten, aufgrund einer ausgelösten Ausnahme überhaupt keine Ergebnisse zurück. Jetzt gibt die Suche die erwarteten Ergebnisse zurück.

_ACP2E-2928 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_

#### Übersetzungen für Kundenrückgabeattribute werden für die jeweilige StoreView nicht in der GraphQL-API angezeigt

Übersetzungen für Kundenrückgabeattribute werden in der GraphQL-API für die jeweilige StoreView angezeigt.
Zuvor wurden Kundenrückgabeattribute für die jeweilige StoreView nicht in der GraphQL-API angezeigt.

_ACP2E-2974 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] Beschädigter GraphQL-Aufruf für getPurchaseOrder mit Knotenangebot

Der GraphQL-Aufruf für die Bestellung kann die Aufgabe ausführen, ohne dass interne Server-Fehler auftreten.

_ACP2E-3128 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_

#### [Cloud] Konfigurierbare Produkte werden auf der Produktions-Site nicht angezeigt, wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist.

Das System zeigt jetzt konfigurierbare Produkte auf der Website korrekt an, auch wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist, sondern in bestimmten Store-Ansichtsbereichen.
Wenn ein Produkt zuvor in „Alle Store-Ansichten“ deaktiviert und nur in bestimmten Store-Ansichtsbereichen aktiviert wurde, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, was dazu führt, dass das Produkt nicht richtig angezeigt wird.

_ACP2E-3184 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/3f300077)_

#### [Cloud] GraphQL-Produkte mit Fehler, wenn dasselbe einfache Produkt mehreren konfigurierbaren Produkten zugewiesen wurde

Zuvor gab GraphQL bei separaten konfigurierbaren Produkten mit demselben einfachen Produkt einen Fehler zurück. Nachdem diese Fehlerbehebung angewendet wurde, gibt GraphQL ohne Fehler Ergebnisse für verschiedene konfigurierbare Produkte mit demselben einfachen Produkt zurück.

_ACP2E-3190 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_

#### [Cloud] Problem mit Benutzerauthentifizierung und Site-übergreifendem Token-Zugriff bei der Einrichtung mehrerer Websites

GraphQL-Kundeninformationen und Warenkorbabfragen bei der Einrichtung mehrerer Websites überprüfen, ob der Kunde auf einer nicht standardmäßigen Website vorhanden ist.
Zuvor funktionierte die Abfrage, ohne sicherzustellen, dass der Kunde bei der Einrichtung mehrerer Sites auf einer nicht standardmäßigen Website vorhanden ist.

_ACP2E-3215 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

#### GraphQL-Artikel im WarenkorbV2-Paginierung funktioniert nicht ordnungsgemäß

Das Problem wurde behoben, indem der richtige Wert für das aktuelle Seitenargument in der Sammlungsabfrage übergeben wurde. Zuvor wurde der falsche Wert übergeben, um die aktuelle Seite festzulegen, was das Problem verursachte.

_ACP2E-3253 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_

#### [GRAPHQL]-Modellwert sollte beim Abrufen von customerCart angegeben werden

Die GraphQL-Abfrage „customerCart“ kann jetzt einen leeren Warenkorb erstellen, selbst wenn das Angebot nicht in der Datenbank verfügbar ist. Zuvor schlug dieser Vorgang aufgrund von Problemen mit der Ländervalidierung beim Erstellen des leeren Warenkorbs fehl.

_ACP2E-3255 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [GraphQL] Wunschlistenelemente sind über GraphQL sichtbar, aber nicht in der Storefront

Wunschzettel-Produkte, die nicht ordnungsgemäß aufgeführt werden, wenn sie über GraphQL angefragt werden. Jetzt werden Produkte auf der Wunschliste basierend auf dem bereitgestellten Store-Kontext gefiltert.

_ACP2E-3380 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL] E-Mail-Inkonsistenz des Kennworts zwischen Inhalt und Betreff/Link zurücksetzen

Das Problem wurde behoben, indem der richtige Speicher simuliert wurde, in dem das Konto des Kunden beim Senden der Anforderung zum Zurücksetzen des Kennworts registriert ist, unabhängig vom Website-Speicher.

_ACP2E-3404 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_

#### [Cloud]-Produkte GraphQL-Abfrage gibt verwandte Produkte zurück, die der aktuellen Website nicht zugewiesen sind

Zuvor wurden für GraphQL-Abfragen Produkte, die mit mehreren Stores verbunden sind, für die Produktabfrage nicht richtig angezeigt. Nachdem diese Fehlerbehebung angewendet wurde, werden für Produkte in der GraphQL-Abfrage Multistore-bezogene Produkte entsprechend angezeigt.

_ACP2E-3419 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### Die Verwendung der falschen Store-ID in der GraphQL-Kopfzeile verursacht einen schwerwiegenden Speicherfehler

Das Senden von falschem Speicher-Code in einer GraphQL-Anfrage führt nicht mehr zu übermäßigem Speicherverbrauch.

_ACP2E-3447 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Cloud] 500-Antwort auf leere GraphQL-Antwort auf 2.4.7

Nach der Behebung werden ungültige GraphQL-Anfragen nicht mehr in der Datei Exception.log protokolliert.

_ACP2E-3467 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

#### [Cloud] Probleme mit der GraphQL-API

Vor der Fehlerbehebung mithilfe des GraphQL-Anwendungsservers hat die Kundenadressanfrage nicht die neuesten Daten zurückgegeben.

_ACP2E-3492 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_

#### Deaktiviertes Produkt wird weiterhin in verwandten, Upsell- und Crosssell-Elementen in der GraphQL-Abfrage angezeigt

GraphQL bietet jetzt eine korrekte Antwort für deaktivierte verwandte Produkte, Upsell- und Crosssell-Produkte

_ACP2E-3505 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

#### [CLOUD]: GraphQL-Fehler Interner Server-Fehler placeOrder-Mutation

Die „placeOrder“-Mutation mit Coupon-Code-Informationen in der Anfrage löst keine interne Fehlerausnahme mehr aus, die Bestellung wurde erfolgreich platziert. Zuvor schlug er mit „Interner Server-Fehler“ fehl.

_ACP2E-3647 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

#### Der Rabatt_Prozentsatz wird nicht für Bundle-Produkte mit dynamischem Preis berechnet

Korrektur hinzugefügt für „DISCOUNT_PERCENTAGE“ von „product.price_details“, bei der für Bundle-Produkte mit aktiviertem dynamischen Preis und angewendetem Rabattcoupon der richtige Wert angezeigt wird.

_LYNX-426_

#### Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist

Es wurde das Problem behoben, dass Paketprodukte weiterhin „IN_STOCK“ zeigten, auch wenn eines ihrer Paketprodukte nicht vorrätig war.

_LYNX-485_

#### NOT_AVAILABLE_MESSAGE und ONLY_X_LEFT_IN_STOCK zeigen nicht denselben verfügbaren Bestand

Es wurde das Problem behoben, bei dem die Nachrichten not_available_message und only_x_left_in_stock inkonsistente Lagerverfügbarkeit zeigten

_LYNX-486_

#### original_row_total Feld gibt falschen Wert zurück

Das Problem mit dem Feld original_row_total wurde behoben, das falsche Werte zurückgab, wenn benutzerdefinierte Optionen ausgewählt wurden

_LYNX-488_

#### Die Miniaturansicht des gruppierten Produkts sollte gemäß der Konfiguration angezeigt werden     .

Das Problem wurde behoben, um sicherzustellen, dass die gruppierte Produktminiatur gemäß den Konfigurationseinstellungen angezeigt wird

_LYNX-503_

#### original_item_price beinhaltet keine Rabatte

Original_item_price wurde aktualisiert und enthält jetzt Rabatte.

_LYNX-512_

#### Meldung „Nicht verfügbar“ zeigt nicht die verfügbare Lagermenge an

Die Fehlermeldung und der Fehlercode für die AddProductsToCart-Mutation wurden behoben, sodass sie mit der Nachrichtenkonfiguration „nicht verfügbar“ übereinstimmen.

_LYNX-530_

#### „OUT_OF_STOCK“-Status gibt auf Einfach mit benutzerdefinierten Optionen Produkte mit Mehrfachauswahl-Optionen zurück

Der StockStatusProvider-Resolver im Inventar-Package wurde aktualisiert, um den stock_status für einfache Produkte mit benutzerdefinierten Optionen zu korrigieren.

_LYNX-532_

#### Fehler (GQL): cart.itemsV2.items.product.custom_attributesV2 gibt einen Server-Fehler zurück

Der Server-Fehler, der auftrat, wenn eine Warenkorbabfrage die benutzerdefinierten Attribute eines Produkts enthielt, wurde behoben, indem ein Produkt ohne benutzerdefinierte Attribute hinzugefügt wurde.

_LYNX-533_

#### order/date_of_first_order gibt immer null zurück

Es wurde das Problem behoben, bei dem „orders“ > „date_of_first_order“ immer null zurückgab.

_LYNX-536_

#### Der Kunde darf eine teilweise versendete Bestellung nicht stornieren können

Die Validierung wurde hinzugefügt, um zu verhindern, dass Kunden eine teilweise versendete Bestellung stornieren.

_LYNX-544_

#### Fehlercodes für die Stornierung von Aufträgen basierend auf der Fehlermeldung

Die Fehler-Codes für die Stornierung von Bestellungen basieren nun auf der spezifischen Fehlermeldung.

_LYNX-548_

#### Zurückverschieben von Cookie-bezogenen Eigenschaften von „privat“ nach „geschützt“

Setzt die Sichtbarkeit der Eigenschaften des Klassenkonstruktors Magento\Framework\App\PageCache\Version von privat auf geschützt zurück

_LYNX-581_

#### Erhöhung der maximalen standardmäßigen GraphQL-Abfragekomplexität auf 1.000

Die standardmäßige maximale GraphQL-Abfragekomplexität wurde von 300 auf 1.000 erhöht.

_LYNX-600_

#### GQL - itemsV2 > Ursprüngliche Zeilensumme, Preisspanne Preise wird als $0.00 für herunterladbare Produkte mit Dateioptionen zurückgegeben, die separate Preise haben.

Es wurde ein Problem behoben, bei dem herunterladbare Produkte mit aktivierten Kaufoptionen für separate Links 0 $ für itemsV2 > Ursprüngliche Zeilensumme und Preisspanne als 0,00 $ für Produkte mit Dateioptionen mit separaten Preisen zurückgaben.

_LYNX-620_

#### GraphQL-Kompatibilität für PHP-8.4 Version

Es wurden GraphQL-Kompatibilitätsprobleme mit PHP 8.4 auf mehreren Resolvern behoben, wodurch eine reibungslose Funktionalität sichergestellt wurde. Betroffene Dateien in den Modulen CatalogRule, Customer, GiftMessage, GiftCard und GiftWrapping wurden aktualisiert.

_LYNX-772_

### GraphQL, Inventar/MSI

#### Die MergeCart-Mutation löst eine Ausnahme aus, wenn Quell- und Zielkarten dieselben Bundle-Elemente enthalten

&#39;-

_ACP2E-2607 - [GitHub-Code-](https://github.com/magento/magento2/commit/c971859e) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, Inventar/MSI, Leistung

#### Site nach dem Upgrade nicht verfügbar

Die Leistung beim Abrufen von Bundle-Produkten über GraphQL wurde verbessert.

_ACP2E-1716 - [GitHub-Code-](https://github.com/magento/magento2/commit/ba25af8a) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Leistung

#### [GraphQL-Resolver] Kundenresolverdaten werden nicht im Import ungültig gemacht

Der Cache des GraphQL-Kundenauflösers wird jetzt erwartungsgemäß invalidiert, wenn ein Kunde durch Importe bearbeitet oder gelöscht wird. Zuvor wurde der Cache nicht ungültig gemacht, und Kundendaten konnten während des Imports bearbeitet oder gelöscht werden.

_AC-9569 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Suche

#### Die Sortierung einer GraphQL-Produktliste nach mehreren Parametern funktioniert nicht

Die Sortierung von Produkten nach mehreren Feldern in GraphQL funktioniert jetzt, wie in der Dokumentation beschrieben

_ACP2E-2809 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_

#### GraphQL-Abfrage zur Produktliste beschränkt auf total_count 10.000 Produkte

Nach der Fehlerbehebung ist das Suchergebnis nicht auf 10000 Produkte beschränkt, sondern es können alle Produkte abgerufen werden, die den Suchkriterien entsprechen, selbst wenn die Anzahl mehr als 10000 beträgt.

_ACP2E-948 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, Test-Framework

#### Magento\GraphQl\App\GraphQlCustomerMutationsTest.php Integrationstest fehlgeschlagen

&#39;-

_ACP2E-3363 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### Import/Export

#### Problem beim Produktimport bei Bereitstellung mit benutzerdefiniertem Optionstyp: Datei (Erstelltes Produkt enthält keinen Preis für benutzerdefinierte Option und zeigt nur die erste angegebene Dateityperweiterung an)

Das System importiert jetzt Produktdaten mit benutzerdefinierten Optionen vom Typ „Datei“ korrekt, um sicherzustellen, dass alle bereitgestellten Dateierweiterungen angezeigt werden und der Preis für die benutzerdefinierte Option enthalten ist. Wenn beim Produktimport zuvor eine benutzerdefinierte Option des Typs „Datei“ mit mehr als einer Dateierweiterung bereitgestellt wurde, wurde nur die erste Erweiterung angezeigt und der Preis für die benutzerdefinierte Option fehlte.

_AC-12172 - [GitHub-Problem](https://github.com/magento/magento2/issues/38805) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38926)_

#### Falsche Ausführungszeit für Importvorgang im Importverlaufsraster

Die Ausführungszeit des Importberichts ist korrekt unabhängig vom Admin-Gebietsschema.

_ACP2E-2710 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Doppelte Kundinnen und Kunden mit derselben E-Mail-Adresse beim Import erstellen

Wenn der Kunde importiert wird, während die Kontofreigabe auf „Global“ eingestellt ist, wird der importierte Kunde, der im System vorhanden ist, aktualisiert.
Zuvor importierter Kunde wurde dupliziert.

_ACP2E-2737 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_

#### Hinzufügen/Aktualisieren von Importprodukten beim Duplizieren anpassbarer Optionen

Das Problem wurde behoben, indem den Produktoptionen beim CSV-Import der richtige Store zugewiesen wurde.
Zuvor dem Admin-Store anstelle des entsprechenden Stores zugewiesen.

_ACP2E-2902 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Kundendatum „created_at“ wird beim Export nicht in die Speicherzeitzone konvertiert

Ein Datumswert der Spalte „created_at“ wird basierend auf der Zeitzone des Speichers im CSV-Abschnitt für den Kundenexport in das richtige Datumsformat konvertiert.

_ACP2E-2990 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3056e9cb)_

#### [Cloud] Beim Überprüfen der Daten in Importdaten mithilfe von CSV wird ein Fehler angezeigt.

Beim Überprüfen der Daten während des CSV-Imports tritt kein Fehler auf. Zuvor war die angezeigte Fehlermeldung: „Wir können keinen Kunden finden, der diese E-Mail- und Website-Code in Zeile(n): 1 abgleicht“, wenn die Daten im Importabschnitt mithilfe von CSV von der Administratorin bzw. dem Administrator überprüft werden.

_ACP2E-3165 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_

#### Importschaltfläche fehlt

Beheben Sie das Problem fehlender Importschaltfläche nach Datenprüfungen mit richtigen und falschen Datensätzen in der CSV. Zuvor wird die Schaltfläche Importieren nicht angezeigt, nachdem Daten mit richtigen und falschen Datensätzen in der CSV-Datei geprüft wurden.

_ACP2E-3172 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1819fe73)_

#### Exportierte Kundenadresse kann nicht importiert werden

Der Import der Kundenadresse wird erwartungsgemäß fortgesetzt. Zuvor verlief die Validierung einer Kundenadressenimportdatei nicht, wenn Kundenkonten freigeben = global gilt, und es gibt zwei Websites, auf denen die Standardwebsite eine eingeschränkte Länderliste hat und die importierte Adresse für eine andere Website gilt, auf der die zulässigen Länder unterschiedlich sind

_ACP2E-3382 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] Falsche Menge in CSV-Datei gab keinen Fehler zurück

Beim Import von Lagerquellen wird nun ein Validierungsfehler für nicht numerische Werte in der Spalte Menge angezeigt. Zuvor führte der Import von Lagerbeständen mit nicht numerischem Wert in der Spalte „Menge“ dazu, dass die Menge auf 0 gesetzt wurde.

_ACP2E-3448 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5b21b7af)_

#### Die Fehlermeldung für den duplizierten URL-Schlüssel, die beim Importieren eines Produkts generiert wird, ist nicht korrekt, wenn der URL-Schlüssel bereits zu einer Kategorie gehört

Beim Überprüfen des Produktimports wird die richtige Fehlermeldung angezeigt, wenn ein Kunde versucht hat, ein Produkt zu importieren, obwohl der URL-Schlüssel des Produkts bereits zu einer Kategorie gehört.

_ACP2E-3455 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

#### Produktexport verursacht OOM auch bei 4G-Speicherbegrenzung

Vor dieser Fehlerbehebung schlug der Produktexport fehl, wenn Produktattribute Tausende von Optionswerten hatten, selbst mit verfügbarem 4G-Speicher. Nach dieser Fehlerbehebung sollte der Produktexport den Export der CSV-Datei abschließen.

_ACP2E-3475 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

#### [Cloud] Importprozesse, die sich gegenseitig beeinflussen

Es werden korrekte Meldungen angezeigt, wenn derselbe Admin-Benutzer zwei oder mehr Importvorgänge mit derselben Benutzersitzung durchführt.

_ACP2E-3527 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

### Import/Export, Leistung

#### [Cloud] Die Produktimportzeit wurde erheblich verlängert

Vor der Fehlerbehebung wies der Katalogproduktimport mit über 10.000 Einträgen eine erhebliche Zeitbeeinträchtigung auf. Nach der Fehlerbehebung wird der Import des Katalogprodukts zeitnah ausgeführt.

_ACP2E-3476 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/87d012e5)_

### Installieren und Verwalten

#### Magento-Upgrade schlägt auf MariaDB 11.4 + 2.4.8-beta1 fehl

Das Upgrade sollte fehlerfrei durchgeführt werden.

_AC-13242 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7b336d0a)_

#### Schaltfläche „VCL für Lack 7 exportieren“ im Admin-Bedienfeld

Die Schaltfläche „VCL für Lack 7 exportieren“ wurde dem Admin-Bedienfeld hinzugefügt.

_ACP2E-2102 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventar/MSI

#### Inventar-Update des konfigurierbaren Produkts schlägt fehl, wenn die Datenbank Präfixe verwendet

Das System aktualisiert jetzt das Inventar der konfigurierbaren Produkte korrekt, wenn die Datenbank Präfixe verwendet, wodurch Fehlermeldungen verhindert und sichergestellt wird, dass die richtige Menge gespeichert wird. Zuvor trat ein Fehler auf, wenn versucht wurde, die Lagermenge für einfache Produkte innerhalb eines konfigurierbaren Produkts zu speichern, wenn die Datenbank Präfixe verwendete.

_AC-10750 - [GitHub-Problem](https://github.com/magento/magento2/issues/38045)_

#### Google-Google-API-Schlüssel funktioniert nicht beim Hinzufügen von Zuordnungen mit Attributen

Das System unterstützt jetzt die neueste Google Maps-API-Version 3.56, sodass Benutzende erfolgreich einen Map-Inhaltsbaustein aus dem PageBuilder-Menü zum Staging hinzufügen können, ohne auf Fehler zu stoßen. Zuvor konnten Benutzende aufgrund von Kompatibilitätsproblemen mit der Google Maps API-Version keinen Zuordnungs-Inhaltsblock hinzufügen, was zu einer Fehlermeldung führte, dass etwas schiefgelaufen ist.

_AC-11593 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

#### Sendung für Auftragselement mit mehreren Quellen und beschädigter SKU kann nicht erstellt werden

Früher, als Leerzeichen versehentlich in der SKU über die Datenbank hinzugefügt wurden, führt zu einem Fehler auf der Sendungsseite, der jetzt behoben ist, und das automatische Zuschneiden gilt als benutzerfreundlicher Fehler und es wurde keine Auswirkung gefunden. Daher wurde die Sendung erfolgreich erstellt.

_AC-13922 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [Testen] Bundle-Produkte mit 0 Inventar, das auf der Storefront angezeigt wird

Das Bundle-Produkt wird nicht auf den zusätzlichen Websites angezeigt, die zusätzliche Lager verwenden.

_ACP2E-1411_

#### [Cloud] Kritisches Problem bei der Produktliste mit leeren Platzierungen

Das System zeigt jetzt Produktlisten korrekt ohne Leerzeichen an, wenn Produkte auf „Nicht vorrätig“ eingestellt sind, was eine konsistente und genaue Anzeige der verfügbaren Produkte gewährleistet. Zuvor führte das Festlegen eines Produkts auf „Nicht vorrätig“ dazu, dass ein leerer Bereich in der Produktliste angezeigt wurde, was das Layout störte und Kunden möglicherweise verwirrte.

_ACP2E-2794 - [GitHub-Code-](https://github.com/magento/magento2/commit/ea79f7dd) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/b59e48ca)_

#### Bestellung kann nicht versendet werden, wenn MSI Pick Up Store aktiviert ist

Verbesserte Inventarleistung der Versanderstellung bei vielen Quellen durch Abholung im Geschäft

_ACP2E-3335 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/9f3e63d1)_

#### Cron-Neuindizierung kann die Produktverfügbarkeit im Frontend nicht aktualisieren

Zuvor waren Produkte im Frontend nicht vorrätig, nachdem der Auftragsstatus über die REST-API aktualisiert wurde. Nach der Aktualisierung des Auftragsstatus über die REST-API werden die Produkte nun als vorrätig angezeigt.

_ACP2E-3355 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### Das Hinzufügen von Bildern zum konfigurierbaren Modus funktioniert nicht, wenn MSI aktiviert ist.

Der Bild-Upload für ein konfigurierbares Produkt funktioniert jetzt wie erwartet, wenn das Inventar-Modul verwendet wird. Zuvor funktionierte der Bild-Upload nicht

_ACP2E-3357 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/fdf409aa)_

#### Problem mit Bundle Product + MSI in Clean M2.4.7-p3

Zuvor konnte bei Inventar-Bundle-Produkten nach der Duplizierung mit demselben einfachen Produkt das einfache Produkt nicht gespeichert werden. Nachdem diese Fehlerbehebung angewendet wurde, kann das einfache Produkt ohne Ausnahmen erfolgreich gespeichert werden.

_ACP2E-3470 - [GitHub-Problem](https://github.com/magento/magento2/issues/39358) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/0208e433)_

### Inventar/MSI, Suche

#### Alle Produkte werden mit [is_out_of_stock] = 1 indiziert, wenn die SKU nicht als durchsuchbares Attribut festgelegt ist

Nach der Fehlerbehebung ist „is_out_of_stock“ im Katalogsuchindex korrekt, auch wenn die SKU nicht durchsuchbar ist.

_ACP2E-3413 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5b21b7af)_

### Reihenfolge

#### Bildschirm „Auftragsübersicht Backend“: Auf Bestellartikelebene ist keine Auftragsmenge sichtbar

Das System zeigt jetzt die Anzahl der nachbestellten Artikel in der Spalte Menge auf dem Bildschirm „Auftragsübersicht“ des Backends an. Dadurch wird sichergestellt, dass Benutzende den Status aller Artikel in einer Bestellung genau verfolgen können. Zuvor wurde in der Spalte „Menge“ nur die Anzahl der bestellten, fakturierten und versandten Artikel angezeigt, nicht jedoch die Anzahl der nachbestellten Artikel.

_AC-10828 - [GitHub-Problem](https://github.com/magento/magento2/issues/38252) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38320)_

#### [Problem] Falsche Store-ID im Renderer für die Bestelladresse verwendet

Das System verwendet nun bei der Darstellung der Bestelladresse die einer Bestellung zugeordnete Speicher-ID korrekt, um sicherzustellen, dass die Adressen entsprechend ihrer jeweiligen Speicher-ID korrekt formatiert sind. Zuvor verwendete das System fälschlicherweise die aktuelle Store-ID, was zu einer falschen Adressformatierung führen konnte, wenn mehrere E-Mails zu Bestellungen aus verschiedenen Stores gesendet werden mussten.

_AC-10994 - [GitHub-Problem](https://github.com/magento/magento2/issues/38412) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37932)_

#### Problem mit der Prozessorzwischenspeicherung

Das System wendet nun den JoinProcessor für jede Iteration korrekt an, auch bei aufeinander folgenden Aufrufen, was einen präzisen Datenabruf gewährleistet. Zuvor wurde der JoinProcessor fälschlicherweise bereits in aufeinander folgenden Iterationen als angewendet markiert, was zu Fehlern beim Datenabruf führte.

_AC-11690 - [GitHub-Problem](https://github.com/magento/magento2/issues/27504) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37550)_

#### [Problem] Versandpreis wird in gedruckter PDF-Datei anders angezeigt

Das System zeigt nun die Versandkosten in gedruckten PDFs entsprechend den Einstellungen für die Steuerkonfiguration korrekt an, sodass die Konsistenz zwischen der Seite mit der Rechnung für Kundenaufträge und der gedruckten Rechnung gewährleistet ist. Zuvor war der im gedruckten PDF angezeigte Versandpreis ohne Steuer, unabhängig von den Steuerkonfigurationseinstellungen.

_AC-11798 - [GitHub-Problem](https://github.com/magento/magento2/issues/38608) - [GitHub-Code-](https://github.com/magento/magento2/pull/38595) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_

#### Neu anordnen mit einem gelöschten übergeordneten konfigurierbaren Produkt

Beim Neuanordnen mit dem gelöschten Produkt zeigt das System jetzt nicht die Schaltfläche zum Neuanordnen an

_AC-13839 - [GitHub-Problem](https://github.com/magento/magento2/issues/39568) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39601)_

#### [Problem] Falsches \Magento\Sales\Model\Order\Email\Container\Template::$id-Eigenschaft beheben

Dies behebt die fehlerhafte phpdoc für \Magento\Sales\Model\Order\Email\Container\Template::$id, eigentlich ist $id type int, aber in Wirklichkeit ist string.

_AC-13924 - [GitHub-Problem](https://github.com/magento/magento2/issues/39151) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39150)_

#### Änderungen an der Telefonnummer können nicht in den Bestelldetails gespeichert werden

Jetzt kann der Benutzer das internationale Präfix 00 im Telefonfeld der Bestelladresse hinzufügen

_ACP2E-2622 - [GitHub-Problem](https://github.com/magento/magento2/issues/38201) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/12e071c3)_

#### E-Mails können nicht gesendet werden

Das System enthält jetzt die Konfigurationsoption async_sending_attempts , mit der vor dem Anhalten eine E-Mail gesendet werden soll, und die Handhabung von fehlgeschlagenen E-Mail-Sendungen verbessert, wenn „Asynchrones Senden“ aktiviert ist. Zuvor versuchte das System, eine E-Mail nicht zu senden, und versuchte kontinuierlich, sie erneut zu senden, was zu einer endlosen Schleife von Fehlermeldungen im Systemprotokoll führte.

_ACP2E-2734 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### [Cloud] Auftragsstatus wurde in „Abgeschlossen“ geändert, wenn eine teilweise Rückerstattung einer teilweise versendeten Bestellung erfolgt

Beim Ausstellen einer Gutschrift wird der Bestellstatus nicht mehr in „Abgeschlossen“ geändert, wenn es Artikel gibt, die noch nicht versandt wurden.

_ACP2E-2756 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD] kann das Senden von E-Mails über die Admin-Benutzeroberfläche nicht deaktivieren, wie in den Entwicklungsdokumenten angezeigt wird

Das System verhindert jetzt korrekt, dass Verkaufs-E-Mails gesendet werden, wenn die E-Mail-Kommunikation deaktiviert ist. Diese E-Mails werden nicht mehr gesendet, wenn die E-Mail-Kommunikation wieder aktiviert wird. Zuvor wurden Verkaufs-E-Mails, die initiiert wurden, während die E-Mail-Kommunikation deaktiviert war, weiterhin gesendet, sobald die E-Mail-Kommunikation wieder aktiviert wurde.

_ACP2E-3002 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_

#### Bestellung ohne vollständige Rückerstattung geschlossen

Das System behält nun den Bestellstatus als „Verarbeitung läuft“ und den Rechnungsstatus als „Ausstehend“ korrekt bei, wenn eine Bestellung mit einer nicht erfassten Zahlung erstellt wurde. Dadurch wird sichergestellt, dass Bestellungen erst nach vollständiger Rückerstattung als „Geschlossen“ gekennzeichnet werden. Zuvor wurde der Bestellstatus bei der Erstellung einer Lieferung für einen Auftrag mit ausstehender Rechnung fälschlicherweise in „Geschlossen“ geändert.

_ACP2E-3045 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud] In Admin kann keine Bestellung in einem Geschäft erstellt werden, wenn nur die Standard-Rechnungsadresse nicht eingerichtet wurde.

Jetzt relevante Fehlermeldung „Ein Kunde mit derselben E-Mail-Adresse existiert bereits auf einer zugehörigen Website.“ wird angezeigt, wenn ein Kunde keine Standard-Rechnungsadresse hat und versucht, eine Bestellung in einem anderen Shop zu erstellen.

_ACP2E-3311 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_

#### Admin hat doppelte Bestellanfragen gesendet

Zuvor konnte die Schaltfläche „Bestellung abschicken“ im Admin-Panel mehrmals angeklickt oder durch wiederholtes Drücken der Eingabetaste aktiviert werden, was zu doppelten oder fehlerhaften Bestellübermittlungen führte. Vermeiden Sie jetzt zusätzliche Aktionen, bis die Bestellung vollständig verarbeitet ist, sodass nur eine Bestellung gesendet wird.

_ACP2E-3416 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_

#### Der Administrator kann auch ohne Zahlungsmethode eine Bestellung aufgeben

Zuvor ausgewählte Zahlungsmethode wird jetzt beibehalten, wenn die Zahlungsmethode in der Liste der verfügbaren Zahlungen erneut angezeigt wird.

_ACP2E-3425 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_

### Bestellung, Zahlungen

#### Der Administrator kann auch ohne Zahlungsmethode eine Bestellung aufgeben

Zuvor konnte der Händler Bestellungen über das Admin-Panel aufgeben, ohne eine Zahlungsmethode auszuwählen. Jetzt wird der Händler eine Zahlungsmethode benötigt, um mit der Bestellung fortzufahren.

_ACP2E-3233 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_

### Reihenfolge, Rückgabe

#### Rückerstattungsergebnisse in doppelter Gutschrift bestellen

Wenn bei der Rückerstattung über die REST-API zwei identische Anfragen gleichzeitig ausgeführt wurden, werden keine doppelten Gutschriften mehr erstellt.

_ACP2E-2982 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

### Bestellung, Steuer

#### [CLOUD] Falsche base_row_total in der RESTFUL-Auftrags-API bei der Aktivierung grenzüberschreitender Transaktionen und der Anwendung von Couponrabatten

Jetzt wird der korrekte base_row_total von der RESTFUL-Auftrags-API zurückgegeben, wenn die grenzüberschreitende Transaktion aktiviert ist und ein Couponrabatt angewendet wird.

_ACP2E-3003 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_

### Sonstige

#### private_content_version-Cookie, das in GQL-Abfragen zurückgegeben wird

Es wurde ein Problem behoben, bei dem das Cookie „private_content_version“ in GraphQL-Abfragen zurückgegeben wurde, selbst wenn das Sitzungs-Cookie deaktiviert war. Das Cookie ist nicht mehr in den GraphQL-Antworten enthalten, wenn die Sitzung erwartungsgemäß deaktiviert wird.

_LYNX-339_

#### Das Attribut is_available in CartItemInterface gibt für konfigurierbare Produkte immer „false“ zurück.

Es wurde ein Problem behoben, bei dem das Attribut is_available in CartItemInterface für auf Lager konfigurierbare Produkte immer „false“ zurückgab. Jetzt spiegelt sie die Verfügbarkeit korrekt wider, sofern zutreffend.

_LYNX-380_

#### is_available-Attribut in CartItemInterface gibt „true“ zurück, auch wenn der verkaufbare Bestand kleiner als die Menge des Produkts ist

Es wurde ein Problem behoben, bei dem das Attribut is_available in der CartItemInterface fälschlicherweise „true“ zurückgegeben wurde, selbst wenn die Menge des Warenkorbeartikels den verkäuflichen Lagerbestand überschritt.

_LYNX-382_

#### Platzhalter-Miniaturansicht gibt zurück, wenn ein einfaches Produkt innerhalb eines gruppierten Produkts zum Warenkorb hinzugefügt wird

Es wurde ein Problem behoben, bei dem beim Hinzufügen eines einfachen Produkts (Teil eines gruppierten Produkts) zum Warenkorb ein Platzhalter-Miniaturbild zurückgegeben wurde, selbst wenn dem Produkt ein Bild zugewiesen war.
Fehlerbehebungsdetails:
- Die Produktminiatur zeigt nun das zugewiesene Bild, sofern verfügbar, korrekt an.
- Die Auswahl der Miniaturen berücksichtigt die Admin-Konfiguration unter:
Stores > Konfiguration > Verkauf > Checkout > Warenkorb > Gruppiertes Produktbild.
Dadurch wird ein konsistentes Verhalten von Miniaturansichten für gruppierte Produkte basierend auf Store-Einstellungen sichergestellt.

_LYNX-399_

#### Benutzerdefinierte Optionsattribute des Kunden funktionieren nicht mit Ganzzahlwerten

Es wurde ein Problem behoben, bei dem die benutzerdefinierten Optionsattribute des Kunden nicht funktionierten, wenn der zurückgegebene Wert eine Ganzzahl war. Benutzerdefinierte Optionen verarbeiten und geben jetzt ganzzahlige Werte korrekt wie erwartet zurück.

_LYNX-400_

#### Interner Server-Fehler beim Abrufen von Preisdetails für Bundle-Produkte mit dynamischem Preis

Es wurde ein Problem behoben, bei dem die Abfrage von Preisdetails für Bundle-Produkte mit dynamischer Preisgestaltung über GraphQL zu einem internen Server-Fehler führte. Diese Verbesserung gewährleistet stabile Warenkorbabfragen bei der Arbeit mit Bundle-Produkten, die mit dynamischen Preisen konfiguriert sind.

_LYNX-402_

#### only_x_left_in_stock gibt für konfigurierbare Produkte immer 0 zurück

Es wurde ein Problem behoben, bei dem das Attribut only_x_left_in_stock bei Verwendung der übergeordneten SKU mit Optionen immer 0 für konfigurierbare Produkte zurückgab.
Fehlerbehebungsdetails:
- Der Wert only_x_left_in_stock spiegelt nun genau den Bestand der ausgewählten untergeordneten Variante statt der übergeordneten SKU wider.
- Dadurch wird sichergestellt, dass die Lagerbestände für konfigurierbare Produktvarianten auf den Warenkorb- und Produktseiten korrekt angezeigt werden.

_LYNX-403_

#### GraphQL-Abfrage gibt nicht den richtigen berechneten regulären Preis für anpassbare Produkte zurück

Es wurde ein Problem behoben, bei dem GraphQL für anpassbare Produkte nicht den richtigen berechneten regulären Preis zurückgab. Die Abfrage enthält jetzt korrekt den berechneten regulären Preis mit anpassbaren Werten (z. B. 125 USD) in der Preiseigenschaft, die sowohl den Grundpreis als auch etwaige zusätzliche Anpassungskosten widerspiegeln.

_LYNX-411_

#### Angewendete Steuern über EstimatedTotals bleiben mit aktualisierten Mutationen erhalten

Es wurde ein Problem mit der Mutation EstimatedTotals behoben, bei dem angewendete Steuern auch nach dem Aktualisieren der Region oder Postleitzahl auf einem Warenkorb beibehalten wurden. Die Mutation aktualisiert nun die angewendeten Steuern korrekt, wenn zwischen Regions- und Postcodewerten gewechselt wird, um sicherzustellen, dass nur die richtige Steuerregel auf der Grundlage der aktuellen Warenkorbdaten angewendet wird.

_LYNX-412_

#### is_available-Attribut in CartItemInterface gibt „true“ zurück, auch wenn der verkaufbare Bestand kleiner als die Menge des Produkts ist

Es wurde ein Problem behoben, bei dem das Attribut is_available in CartItemInterface fälschlicherweise „true“ zurückgegeben wurde, selbst wenn der verkaufbare Bestand kleiner als die angeforderte Produktmenge war. Das Feld is_available gibt jetzt korrekt „false“ zurück, wenn die Produktmenge den verfügbaren Bestand überschreitet.

_LYNX-420_

#### Regulärer Produktpreis mit 12 Dezimalstellen und falschem Wert

Es wurde ein Problem behoben, bei dem der Wert „Regular_Price“ im GraphQL-Pfad „product.price_range.maximum_price“ und „minimum_price“ nicht mit dem Katalogpreis übereinstimmte, wenn mehrere Steuersätze angewendet wurden. Der reguläre Preis spiegelt nun den Katalogpreis über alle Steuerkonfigurationen hinweg konsistent wider und gewährleistet eine genaue Einzelpreisfindung, Berechnungen der GesamtZeilenkosten und Rabattprüfungen in der Warenkorbzusammenfassung.

_LYNX-425_

#### GraphQL-Serverfehler im Warenkorb mit nicht vorrätigem gebündeltem Produkt

Es wurde ein Problem behoben, bei dem GraphQL beim Abrufen eines Warenkorbs mit einem gebündelten Produkt mit einem nicht vorrätigen Element einen internen Server-Fehler zurückgab, insbesondere wenn die Abfrage die itemsV2-Eigenschaft enthielt. GraphQL gibt jetzt wie erwartet korrekt eine Liste von Elementen mit relevanten Fehlermeldungen zurück, die an den Produkteintrag im Paket angehängt sind.

_LYNX-430_

#### Eine Adresse mit benutzerdefinierten Attributen kann nicht erstellt werden

Es wurde ein Problem mit der createCustomerAddress-Mutation behoben, das die Erstellung von Adressen mit erforderlichen benutzerdefinierten Attributen verhinderte. Die Mutation verarbeitet jetzt benutzerdefinierte Adressattribute korrekt, wenn die entsprechende Payload bereitgestellt wird.

_LYNX-441_

#### GraphQL-Server-Fehler im Warenkorb mit only_x_left_in_stock für gebündeltes Produkt

Es wurde ein Problem behoben, bei dem das Abrufen eines Warenkorbs, der ein gebündeltes Produkt mit dem Feld only_x_left_in_stock in der GraphQL-Abfrage enthält, zu einem internen Server-Fehler führte. GraphQL gibt jetzt für das Feld only_x_left_in_stock korrekt einen Float oder null zurück, ohne Fehler zu verursachen.

_LYNX-447_

#### GraphQL-Fehler beim Entfernen anderer Produkte mit unzureichendem konfigurierbarem Produkt im Warenkorb

Es wurde ein Problem behoben, bei dem der Versuch, vorrätige Produkte aus dem Warenkorb zu entfernen, zu dem GraphQL-Fehler „Die angeforderte Menge ist nicht verfügbar“ führte, wenn der Warenkorb auch konfigurierbare Produkte mit unzureichendem Bestand enthielt. Die Entfernung funktioniert nun erwartungsgemäß, ohne dass Fehler ausgelöst werden.

_LYNX-464_

#### Es können keine Produkte hinzugefügt werden, da bei der SKU-Mutation die Groß-/Kleinschreibung beachtet wird

Es wurde ein Problem behoben, bei dem die addProductsToCart-Mutation bei Verwendung von SKUs mit unterschiedlicher Groß-/Kleinschreibung den Fehler „PRODUCT_NOT_FOUND“ zurückgab. Die Mutation verarbeitet SKUs nun ohne Unterscheidung der Groß-/Kleinschreibung und stellt so die Konsistenz mit Abfragen des Katalog-Service und dem PDP-Verhalten sicher.

_LYNX-469_

#### Produktattribut > Marken-Kurzform &trade; wird als &trade; zurückgegeben

Es wurde ein Zeichenkodierungsproblem mit dem Produktnamen für die GraphQL-API behoben

_LYNX-603_

#### updateCustomerEmail-Mutationsproblem

Es wurde ein Problem mit der updateCustomerEmail-Mutation behoben, bei dem Kunden ohne erforderliche benutzerdefinierte Attribute (die nach der Kontoerstellung hinzugefügt wurden) ihre E-Mail nicht aktualisieren konnten.

_LYNX-619_

#### Die Mutation setShippingAddressesOnCart gibt einen Fehler aus, wenn pickup_location_code verwendet wird

Es wurde ein Problem behoben, bei dem die setShippingAddressesOnCart-Mutation bei Verwendung von pickup_location_code ohne Angabe von customer_address_id oder -adresse einen Fehler zurückgab. Die Mutation ermöglicht es nun, eine Versandadresse nur mit dem PICKUP_LOCATION_CODE zu setzen.

_LYNX-626_

#### Storefront-Kompatibilität - Aktualisieren der Logik, um den Tabellennamen mit Präfix und anderen geringfügigen Verbesserungen zu erhalten

Die Logik zum Abrufen des Tabellennamen mit dem Präfix (im Zusammenhang mit SCP-Änderungen) wurde aktualisiert.

_LYNX-637_

#### Das Speichern im Adressbuch funktioniert nicht, wenn das Feld „same_as_shipping“ von setBillingAddressOnCart GQL verwendet wird

Fehlerkorrektur - Die Lieferadresse wird nicht im Adressbuch des Kunden gespeichert, wenn die GraphQL-Mutation setBillingAddressOnCart verwendet wird und das Feld same_as_shipping auf true gesetzt ist. Jetzt wird die Lieferadresse korrekt wie erwartet gespeichert.

_LYNX-643_

#### Standardisieren von order_id in Mutationen

Die Eingabe von order_id in Mutationen wurde standardisiert und die E-Mail-Vorlage für die Auftragsabbruchsbestätigung wurde aktualisiert, um die Inkrement-ID anstelle der Auftrags-ID anzuzeigen.

_LYNX-650_

#### CustomerOrder zeigt die Bestellkommentare nicht an

Es wurde ein Problem mit CustomerOrder behoben, um Bestellkommentare in GraphQL-Abfragen für Gast- und Kundenaufträge einzuschließen.

_LYNX-651_

#### original_item_price darf keinen Rabatt enthalten

Die Logik für original_item_price in GraphQL-Warenkorbartikelpreisen wurde aktualisiert, um Rabatte auszuschließen.

_LYNX-652_

#### Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist

Es wurde ein Problem behoben, bei dem product.stock_status für Bundle-Produkte weiterhin „IN_STOCK“ zeigte, selbst wenn eines der gebündelten Elemente nicht vorrätig war.

_LYNX-681_

#### Kundenabfrage gibt internen Server-Fehler zurück, wenn ein Wert für das gelöschte benutzerdefinierte Attribut für einen Kunden vorhanden ist

Es wurde ein Problem behoben, bei dem die Kundenabfrage einen internen Server-Fehler zurückgab, wenn ein gelöschtes benutzerdefiniertes Attribut noch einen gespeicherten Wert hatte. Jetzt wird eine korrekte Fehlermeldung zurückgegeben, wenn ein nicht vorhandenes Attribut angefordert wird. Erforderlicher Cache wird beim Löschen des benutzerdefinierten Kundenattributs ungültig.

_LYNX-686_

#### Aktionsparameter für Bestätigungs-Links für Rücksendung und Abbruch

Aktionsparameter für Links zu E-Mails mit Rückgabe- und Abbruchsbestätigung hinzugefügt

_LYNX-687_

#### Die Bestätigungs-URL des Gastbenutzers wird zur Bestellstatus-Seite umgeleitet, da darin „orderRef“ fehlt.

Der Parameter orderRef wurde zum Link in der Bestätigungs-E-Mail zur Stornierung einer Gastbestellung hinzugefügt

_LYNX-689_

#### Für das Feld „TaxItem.title“, das keine NULL-Werte zulässt, kann in placeOrder GQL nicht null zurückgegeben werden.

Fehlerkorrektur - Die placeOrder-Mutation ist jetzt aufgrund eines Nullwerts für das Feld TaxItem.title, in dem keine NULL-Werte zulässig sind, mit einem internen Server-Fehler fehlgeschlagen. Jetzt gibt das Feld immer einen gültigen Wert zurück, um eine erfolgreiche Auftragserteilung sicherzustellen.

_LYNX-699_

#### Geschätzte Gesamtwerte: Rabatte sind null für virtuelle Produktarten

Es wurde das Problem behoben, bei dem die Mutation estimatedTotals für Rabatte null zurückgab, wenn ein Rabattcode auf einen Warenkorb mit virtuellen Produkten angewendet wird.

_LYNX-702_

#### Das Paketprodukt gibt nicht den richtigen Rabattprozentsatz und Betrag zurück.

Für Katalogartikelpreise wurden die neuen Eigenschaften „CATALOG_DISCOUNT“ und „ROW_CATALOG_DISCOUNT“ eingeführt, um die richtigen Rabattbeträge und -prozentsätze sowohl auf Zeilen- als auch Einzelartikelebene anzuzeigen.

_LYNX-703_

#### Konfiguration von Geschenknachrichten auf Produktebene

Es wurde ein Problem behoben, bei dem Geschenknachrichten nicht auf Produktebene angewendet wurden, wenn sie global deaktiviert waren. Wenn jetzt Geschenknachrichten für ein bestimmtes Produkt aktiviert sind, können sie mit der UpdateCartItems-Mutation erfolgreich hinzugefügt werden und werden korrekt gespeichert und angezeigt.

_LYNX-714_

#### cart.rules-Abfrage gibt einen Fehler anstelle eines leeren Arrays zurück, wenn keine aktiven Warenkorbregeln angewendet werden

Die Abfrage „cart.rules“ wurde korrigiert, sodass ein leeres Array anstelle eines Fehlers zurückgegeben wird, wenn keine aktiven Warenkorbregeln angewendet werden.

_LYNX-757_

#### GraphQL-Aufrufe mit der OPTIONS-Methode geben den 500-Antwort-Code zurück, wenn das Adobe-Commerce/Storefront-Kompatibilitätspaket installiert ist

Es wurde ein Problem behoben, bei dem GraphQL-Aufrufe mit der OPTIONS-Methode bei der Installation des Pakets „adobe-commerce/storefront-compatibility“ einen internen Server-Fehler 500 zurückgaben. Der Endpunkt gibt jetzt korrekt eine 200/204-Antwort wie erwartet zurück.

_LYNX-778_

### Andere Entwickler-Tools

#### [Problem] Behebung eines HTML-Syntaxfehlers in visual.phtml

Das System schließt jetzt das Start-Tag in der Datei „visual.phtml“ korrekt, um eine ordnungsgemäße HTML-Syntax sicherzustellen. Zuvor wurde das Start-Tag nicht ordnungsgemäß geschlossen, was zu einem HTML-Syntaxfehler führte.

_AC-10658 - [GitHub-Problem](https://github.com/magento/magento2/issues/38247) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37457)_

#### [Problem] Im Wartungsbefehl bin/Magento wurde „aktiv“ in „aktiviert“ :status.

Das System bietet jetzt genauere Statusmeldungen für den Wartungsmodusbefehl, wobei der Status von „aktiv“ in „aktiviert“ und von „nicht aktiv“ in „deaktiviert“ geändert wird. Zuvor wurde die Statusmeldung für den Wartungsmodusbefehl als „aktiv“ oder „nicht aktiv“ angezeigt, was zu Verwirrung führen konnte.

_AC-11474 - [GitHub-Problem](https://github.com/magento/magento2/issues/38486) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38410)_

#### Die Navigation in der Kategoriestruktur führt zu Fehlern in Redis: „Redis-Sitzung hat gleichzeitige Verbindungen überschritten“

_AC-12571 - [GitHub-Problem](https://github.com/magento/magento2/issues/38851) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0611e750)_

#### CSP-Probleme in Kombination mit dev/css/use_css_critical_path

Das System lädt CSS-Dateien nun korrekt asynchron auf Auscheckseiten, selbst wenn die Einstellung „dev/css/use_css_critical_path“ aktiviert ist, um sicherzustellen, dass diese Seiten mit den richtigen CSS-Stilen gerendert werden. Zuvor verhinderte eine eingeschränkte Content Security Policy (CSP) die Ausführung von Inline-JavaScript, was dazu führte, dass CSS-Dateien nicht wie erwartet geladen wurden.

_AC-12731 - [GitHub-Problem](https://github.com/magento/magento2/issues/39020) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39040)_

#### Bei Verwendung des virtuellen Typs zum Konfigurieren des Plug-ins kann die Interceptor-Methode im `setup:di:compile`-Befehl nicht korrekt generiert werden

Das System generiert jetzt korrekt Interceptor-Methoden, wenn ein virtueller Typ zum Konfigurieren eines Plug-ins verwendet wird, um konsistente Ergebnisse sicherzustellen, unabhängig davon, ob vorkompiliert oder zur Laufzeit kompiliert. Zuvor generiert das System beim Vorkompilieren falsche Ergebnisse im Vergleich zur Laufzeitkompilierung.

_AC-13398 - [GitHub-Problem](https://github.com/magento/magento2/issues/33980) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38141)_

#### Adobe Commerce 2.4.7-P3-Modultests schlagen fehl

Es sind keine Versionshinweise erforderlich.

_ACP2E-3631 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Zahlungs-/Zahlungsmethoden, Bestellung

#### Papal Payflow Kreditkartendetails, die für die spätere Verwendung gespeichert wurden, werden nicht auf der Seite der gespeicherten Zahlungsmethode angezeigt

Frühere Papal Payflow Kreditkartendetails, die für die spätere Verwendung gespeichert wurden, wurden nicht auf der Seite der gespeicherten Zahlungsmethode angezeigt, die jetzt feste Kreditkartendetails sind auf der Seite der gespeicherten Zahlungsmethode sichtbar.

_AC-13699 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/96dec499)_

### Zahlungen

#### Zahlung mit Kreditkarte (Payflow-Link) funktioniert nicht

Früher erhalten Fehler (Zahlung wurde abgelehnt) beim Platzieren der Bestellung mit Kreditkarte, nachdem die Bestellung erfolgreich platziert wurde.

_AC-13414 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a68324bc)_

#### Der Payflow erstellt jedes Mal eine neue Transaktion, wenn wir auf dem Bildschirm Transaktion anzeigen auf die Schaltfläche Abrufen klicken

Das System ruft jetzt bei jedem Klicken auf die Schaltfläche „Abrufen“ im Bildschirm „Transaktion anzeigen“ Transaktionsinformationen korrekt ab, ohne eine neue Zahlungstransaktion zu erstellen. Zuvor wurde durch Klicken auf die Schaltfläche „Abrufen“ fälschlicherweise eine neue Zahlungstransaktion für eine bereits bezahlte Bestellung erstellt.

_ACP2E-2841 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### PayLater-Nachricht für kanadisches PayPal-Händlerkonto wird nicht in PDP angezeigt

Das System zeigt nun auf der Produktdetailseite (PDP) korrekt die PayLater-Nachricht für kanadische PayPal-Händlerkonten an, wenn das Land des Käufers anhand der Rechnungsadresse oder der Lieferung des Kontos ermittelt werden kann. Zuvor wurde die PayLater-Nachricht aufgrund eines fehlenden Parameters nicht angezeigt, was zu einem Fehler in der Browser-Konsole führte.

_ACP2E-3028 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_

#### Rückerstattung bei PayPal-Bestellung führt zu einer doppelten Gutschrift

Fehlerkorrektur - Parallelitätsprobleme bei IPN-erstellten Gutschriften für den PayPal-Zahlungsdienst wurden behoben.

_ACP2E-3143 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_

#### Warenkorb-Preisregel funktioniert nicht für Paypal

Der korrekte Betrag wird auf der PayPal-Seite angezeigt, wenn der Rabatt nach Zahlungsmethode angewendet wird

_ACP2E-3163 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

#### [Cloud] Benutzer mit einer bestimmten Rolle können sich nicht anmelden

Admin-Benutzer mit einer Rolle, die nur PayPal-Abschnittszugriff enthält, können sich jetzt fehlerfrei anmelden

_ACP2E-3208 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

### Leistung

#### Problem mit den Standardattributeinstellungen

Das System ermöglicht es Benutzenden jetzt, die Auswahl einer Standardoption für ein Produktattribut aufzuheben, sodass das Attribut nicht immer über einen Standardsatz verfügt. Nachdem ein Standard für ein Produktattribut festgelegt wurde, gab es bisher keine Möglichkeit, die Auswahl aufzuheben, sodass für das Attribut immer ein Standardwert festgelegt war.

_AC-11932 - [GitHub-Problem](https://github.com/magento/magento2/issues/38703) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problem] Code-Bereinigung und Hinzufügen eines neuen kritischen Head-Blocks und Verschieben von kritischem CSS vor Assets

Das System umfasst jetzt einen neuen kritischen Hauptblock und verschiebt wichtiges CSS vor Assets, was eine bessere Anpassung und Leistungsoptimierung im Frontend ermöglicht. Zuvor wurde das kritische CSS nicht vor den Assets positioniert, was die Anpassungs- und Optimierungsmöglichkeiten einschränkte.

_AC-12000 - [GitHub-Problem](https://github.com/magento/magento2/issues/38748) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35580)_

#### Die Design-Kompilierung funktioniert nicht mehr, wenn der MySQL-Host Port-Informationen enthält

Das System verarbeitet jetzt die MySQL-Host-Konfiguration, die Port-Informationen enthält, korrekt, um eine erfolgreiche Design-Kompilierung sicherzustellen. Zuvor schlug die Design-Kompilierung fehl, wenn die MySQL-Host-Konfiguration in der Datenbankverbindung Port-Informationen enthielt.

_AC-12176 - [GitHub-Problem](https://github.com/magento/magento2/issues/38799) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38842)_

#### Unterstützung für die CommandLoaderInterface von Symfony in Magento CLI

Durch diese Änderung wird die Initialisierungszeit der Magento-CLI-App reduziert, da Befehle erst dann initialisiert werden können, wenn sie benötigt werden.

_AC-13471 - [GitHub-Problem](https://github.com/magento/magento2/issues/29266) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29355)_

#### Leistungsproblem beim Laden von Produktattributen in Warenkorbregeln

Verbesserte Abfrageleistung für Vertriebsregeln - von rund 150 ms bis zu einstelligen ms.

_ACP2E-2494 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_

#### Preis partielle Indizierungsleistung

Die Leistung bei der partiellen Indizierung wurde durch die Optimierung einiger Löschabfragen, die im Indizierungsprozess verwendet werden, verbessert.

_ACP2E-2673 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_

#### Bestellung wird bei Multi-Store-Einrichtung bei Verwendung der asynchronen Auftragsverarbeitung abgelehnt + Nutzungsbedingungen

Die Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden jetzt verarbeitet.
Bevor sie automatisch abgelehnt wurden.

_ACP2E-2850 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_

#### Die Ausführung des Aufruf der Order Rest-API dauert sehr lange

Das System führt nun den Aufruf der Auftrags-REST-API innerhalb eines angemessenen Zeitraums aus, was die Leistung beim Abrufen einer großen Anzahl von Aufträgen verbessert. Zuvor dauerte die Ausführung des Order Rest-API-Aufrufs lange, was zu Verzögerungen beim Abrufen einer großen Anzahl von Bestellungen führte.

_ACP2E-2910 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/001e5188)_

### Preisgestaltung

#### Magento2.4.6-p4 Bestellung API Einfache Artikel fehlender Preis

Das System zeigt jetzt den Preis einfacher Produkte korrekt an, wenn sie über die Auftrags-API abgefragt werden, wodurch eine genaue Datendarstellung gewährleistet ist. Zuvor wurde der Preis für einfache Produkte in der API-Antwort fälschlicherweise als null angezeigt.

_AC-11810 - [GitHub-Problem](https://github.com/magento/magento2/issues/38603)_

#### Penny-Rundungsfehler in Katalogregel

_AC-13855 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/276e0acd)_

### Produkt

#### Sonderzeichen im konfigurierbaren zugehörigen Produktnamen werden in HTML-Entitäten konvertiert.

Das System behält jetzt Sonderzeichen in den Namen der zugehörigen Produkte beim Bearbeiten eines konfigurierbaren Produkts korrekt bei, was verhindert, dass sie in HTML-Entitäten konvertiert werden. Zuvor wurden Sonderzeichen in zugehörigen Produktnamen beim Bearbeiten des konfigurierbaren Produkts in HTML-Entitäten konvertiert.

_AC-10535 - [GitHub-Problem](https://github.com/magento/magento2/issues/38146) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38447)_

#### Die ProductRepository-Funktion GetById erstellt nicht den richtigen Cache-Schlüssel

Das System erstellt nun korrekt einen Cache-Schlüssel in der GetById-Funktion des ProductRepositorys, unabhängig davon, ob die Speicher-ID als Zeichenfolge oder Ganzzahl übergeben wird. Dadurch wird sichergestellt, dass das Produkt bei nachfolgenden Aufrufen aus dem Speicher abgerufen wird, was die Leistung verbessert. Zuvor konnte das System das Produkt jedes Mal aus der Datenbank abrufen, wenn die Funktion aufgerufen wurde, auch mit denselben Parametern, da ein falscher Cache-Schlüssel erstellt wurde.

_AC-10947 - [GitHub-Problem](https://github.com/magento/magento2/issues/38384) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38433)_

#### [Problem] [MFTF] AdminClickAddOptionForBundleItemsActionGroup hinzugefügt

Das System enthält jetzt die AdminClickAddOptionForBundleItemsActionGroup, wodurch die Funktionalität des Admin-Bedienfelds erweitert wird. Zuvor war diese Aktionsgruppe nicht verfügbar.

_AC-11992 - [GitHub-Problem](https://github.com/magento/magento2/issues/30857) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30838)_

#### [Problem] Beheben von Tippfehlern im PHPDoc-Block

Das System entfernt jetzt korrekt eine unbekannte referenzierte Variable in PHPDoc für die $helper-Variablendeklaration, was die Code-Klarheit und -Genauigkeit verbessert. Zuvor verursachte diese unbekannte referenzierte Variable in PHPDoc Verwirrung und potenzielle Ungenauigkeiten im Code.

_AC-13173 - [GitHub-Problem](https://github.com/magento/magento2/issues/38961) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38940)_

#### [Problem] Fehlerkorrektur: Layout von fehlerhaften Bundles und herunterladbaren Produktseiten in Magento >= 2.4.7 behoben

Das Layout für Paket- und herunterladbare Produktseiten wurde korrigiert, um eine konsistente und korrekte Anzeige auf allen Geräten sicherzustellen. Zuvor traten auf diesen Seiten Layout-Probleme aufgrund einer Neuanordnung des Produktinfo-Medienblocks auf.

_AC-13423 - [GitHub-Problem](https://github.com/magento/magento2/issues/39403) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor - #2 ($storeId) muss vom Typ int sein, angegebene Zeichenfolge

Das System erstellt nun einen korrekten Trigger der E-Mail-Benachrichtigung mit dem Produkt, indem sichergestellt wird, dass die Kennung des Stores vom richtigen Datentyp ist. Zuvor wurden keine E-Mails zu Produktwarnungen gesendet, da der Typ in der Store-Kennung nicht übereinstimmt.

_AC-5969 - [GitHub-Problem](https://github.com/magento/magento2/issues/35602) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

#### [Cloud] Funktion addFilterToMap funktioniert für bestimmte Spalten nicht

Jetzt kann das benutzerdefinierte Modul im Bestellraster verwendet werden. Bei der Verwendung eines benutzerdefinierten Moduls sind zuvor Fehler aufgetreten.

_ACP2E-2944 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_

### Promotion

#### Kundenattribut beim Erstellen eines Kontos aus einer Einladung nicht sichtbar

Kundenattribute sind beim Erstellen eines Kontos über eine Einladung verfügbar.

_ACP2E-2602 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_

#### Couponcode mit „Benutzer pro Coupon“-Limit wird nicht für Zahlung freigegeben, die mit der Stornierung der Bestellung fehlgeschlagen ist.

Das System aktualisiert jetzt sofort die Couponnutzung, wenn eine Bestellung erstellt oder storniert wird, und fügt einer Warteschlange Regelverwendungen hinzu, um potenzielle Deadlocks zu verhindern. Dadurch wird sichergestellt, dass ein Gutscheincode mit einem Limit „Nutzungen pro Gutschein“ freigegeben wird und wiederverwendet werden kann, wenn eine Bestellung aufgrund einer fehlgeschlagenen Zahlung storniert wird. Zuvor gab das System den Couponcode nicht zur Wiederverwendung frei, was zu einer Fehlermeldung führte, die besagt, dass der Couponcode nicht gültig war.

_ACP2E-2627 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud] Neuindizierung Katalogregel Produkt-Indexer gibt SQLSTATE[HY000] aus: Allgemeiner Fehler: Der MySQL-Server 2006 ist verschwunden.

Das System verarbeitet jetzt den benutzerdefinierten Wert „batchCount“ in der Datei „di.xml“ für &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot; korrekt, wodurch SQL-Fehler wie „Allgemeiner Fehler: 2006 MySQL Server ist verschwunden“ während der Neuindizierung des Catalog Rule Product Indexers aufgrund der falschen Batch-Größe bei großen Katalogen verhindert werden

_ACP2E-2811 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### Verkaufsregel mit dem Attribut „Rabattmengenschritt (X kaufen)“ bewirkt, dass andere Regeln nicht angewendet werden

Die Warenkorb-Preisregel hebt zuvor angewendete Regeln nicht auf, wenn die Menge des Produkts im Warenkorb nicht ausreicht, um die Regel anzuwenden.

_ACP2E-3139 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_

#### Anfrageverkaufsregeln mit Festbetragsrabatt und „Maximaler Mengenrabatt wird angewendet auf“

Es wurde ein Problem mit dem Rabatt auf Warenkorbregeln behoben, wenn der Rabatt auf einen festen Betrag so konfiguriert ist, dass er auf eine begrenzte Anzahl von Produkten angewendet wird, wenn der Warenkorb der Warenkorb ist. Zuvor wurde der Wert „Maximaler Mengenrabatt wird auf angewendet“ verwendet, um den Preis des aktuellen Artikels im Warenkorb zu berechnen, nicht nur für die Berechnung des Rabatts der Regel.

_ACP2E-3332 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

#### Warenkorbregeln „Fester Rabatt auf den gesamten Warenkorb“  Aktion wendet Rabatte falsch an

Couponcodes werden bei Verwendung der Auftragserstellung im Admin-Bereich unabhängig von Groß- oder Kleinschreibung ordnungsgemäß validiert. Zuvor wurde der Couponcode nicht validiert, wenn er nicht mit der exakten Groß-/Kleinschreibung des konfigurierten Warenkorb-Regel-Codes übereinstimmte.

_ACP2E-3349 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_

#### Speichern Sie im Backend Standardwerte für Produktattribute (anstelle der erwarteten Administratorwerte).

Im Backend werden jetzt Admin-Werte anstelle der standardmäßigen Store-Werte für Produktattribute verwendet.

_ACP2E-3374 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_

#### Die Aktion „Fester Rabatt für den gesamten Warenkorb“ wendet Rabatte beim Hinzufügen von Bundle-Produkten falsch an

Regeln zum Warenkorb mit festem Betrag wurden für Bundle-Produkte nicht ordnungsgemäß angewendet. Jetzt werden bei der Berechnung des gesamten Rabattbetrags untergeordnete Bundle-Produkte berücksichtigt, was zu einer korrekten Rabattberechnung führt.

_ACP2E-3377 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

#### Warenkorbpreisregeln berechnen den Rabatt falsch

Festbetragsrabatte werden jetzt ordnungsgemäß berechnet. Vor der Fehlerbehebung wurden die Festbetragsrabatte für Bundle-Produkte nicht korrekt summiert.

_ACP2E-3403 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0b488dd1)_

#### Verschachtelte Kategorien in Regelbedingungen werden nicht angezeigt

Es wurde ein Problem behoben, bei dem verschachtelte Kategorien unter der Kategorie der Ebene 3 in Marketing-Regeln für die Kategoriebedingung nicht angezeigt wurden

_ACP2E-3406 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_

#### usage_limit und uses_per_customer werden in der Tabelle „salesrule_coupon“ nicht aktualisiert

Die Aktualisierung der Preisregel Benutzer pro Coupon und Benutzer pro Kunde im Warenkorb wirkt sich jetzt auf bestehende automatisch generierte Coupons aus. Zuvor waren von den neuen Werten nur neue Coupons betroffen

_ACP2E-3432 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_

#### Die Warenkorbpreisregel berücksichtigt keine übergeordnete Kategorie, wenn sie die Bedingung „gleich oder größer als“ verwendet.

Warenkorbpreisregeln berücksichtigen jetzt die übergeordnete Kategorie korrekt, wenn sie in erweiterten Bedingungen verwendet wird

_ACP2E-3456 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93359343)_

#### Ungültige Rabattberechnung mit Priorität

Im Falle eines festen Betrags, der für den gesamten Warenkorb-Rabatttyp angewendet wurde, wurde der Betrag für Warenkorbartikel, die bereits durch eine frühere Promotion diskontiert wurden, nicht ordnungsgemäß berechnet. Jetzt sind die Rabatte richtig zusammengefasst.

_ACP2E-3463 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

#### [CLOUD] Die Versandberechnung berücksichtigt nicht die Warenkorbregel

Vor der Fehlerbehebung wurde eine Warenkorb-Regel mit der Bedingung Region nicht konsistent angewendet. Nach der Fehlerbehebung werden Warenkorbregeln mit Regionsbedingungen ordnungsgemäß angewendet.

_ACP2E-3472 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

#### Warenkorbregel-SKU-Bedingung schlägt für Rechnung fehl.

Rabatt auf Bundle-Produkt mit dynamischem Preis wird jetzt korrekt in der Rechnung angezeigt. Zuvor wurde der Rabatt nicht in der Rechnung berücksichtigt.

_ACP2E-3491 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_

#### Falscher Rabattwert, wenn mehrere Warenkorbpreisregeln gleichzeitig mit Produkten mit Rabatt/Sonderpreis angewendet werden

Vor der Festsetzung wurde der Festbetrag für Regeln für den gesamten Warenkorb nicht ordnungsgemäß angewendet, wenn mehr als eine angewendet wurde. Jetzt werden die Regeln für den Rabatt auf feste Beträge ordnungsgemäß angewendet.

_ACP2E-3498 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

### SEO

#### Das Hinzufügen von URL-Neuschreibungen mit einem Akzent verursacht unendliche Ladevorgänge

Das System erstellt jetzt erfolgreich URL-Funktionen und schreibt sie mit Akzenten um, wodurch das unendliche Laden während des Speichervorgangs verhindert wird. Zuvor führte das Hinzufügen einer URL-Umschreibung mit einem Akzent zu einem unendlichen Ladeproblem.

_AC-11907 - [GitHub-Problem](https://github.com/magento/magento2/issues/38692) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44cef3a9)_

#### Multi-Store-URL-Rewrite für Kategorie der falschen Kategorie auf dritter Ebene

Generieren korrekter URL-Neuschreibungen für untergeordnete Elemente mit einem übergeordneten Element mit benutzerdefiniertem URL-Schlüssel

_ACP2E-2641 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Doppelbyte-Zeichen (Sonderzeichen) im Feld Produktname blockieren die Produkterstellung im Backend

Es wurde eine neue Einstellung hinzugefügt, mit der Sie die Transliteration auf die Produkt-URL anwenden können oder nicht. Einstellung ist hier verfügbar: Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung: „Transliteration für Produkt-URL anwenden“

_ACP2E-2770 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### Falsche Erstellung von url_rewrite Einträgen mit mehreren Stores in einer Store-Gruppe

Vor der Fehlerbehebung konnten Sie beim Bearbeiten eines Produkts nur URL-Neuschreibungen auf Website-Ebene generieren. Mit der Fehlerbehebung wurde eine neue Einstellung eingeführt (Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung, „Produkt-URL-Neuschreibungsbereich“ mit Optionen „Store-Ansicht“, „Website„), mit der Sie URL-Neuschreibungen auf Store-Ansicht- oder Website-Ebene generieren können.

_ACP2E-3383 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2d627301)_

### Suche

#### Erhalten von „Geben Sie einen Suchbegriff ein und versuchen Sie es erneut.“ Fehler auf der Seite für die erweiterte Suche in der Storefront in 2.4.8-Beta1

Das System zeigt jetzt die Suchergebnisse auf der Seite Erweiterte Suche korrekt an, wenn ein Produktattribut auf „Nein“ gesetzt ist. Wenn Sie ein Produktattribut zuvor auf „Nein“ festgelegt und eine Suche durchgeführt haben, wird die Fehlermeldung „Geben Sie einen Suchbegriff ein und versuchen Sie es erneut.“

_AC-13053 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ea26621)_

#### Magento/module-open-search ist von einer nicht vorhandenen OpenSearch-PHP-Verzweigung abhängig

_AC-13721 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/05dc0bbf)_

#### Die Tabelle search_query hat bei großer Größe große Auswirkungen auf die Ladezeit des Frontends

Die Ladezeit der Suchauflistungsseite wurde verbessert. Vor der Fehlerbehebung wurde die Suchauflistungsseite aufgrund einer nicht optimierten Abfrage verzögert.

_ACP2E-3362 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

### Sicherheit

#### [Problem] Fehlendes PayLater-Popup für Schriftart-CSP

Das System erlaubt jetzt das Laden der Schriftart &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;, ohne gegen die Content Security Policy Direktive zu verstoßen, um die korrekte Anzeige des Paylater Popup sicherzustellen. Zuvor wurde das Laden der Schriftart aufgrund eines Verstoßes gegen die Content Security Policy-Direktive abgelehnt, was zu Anzeigeproblemen mit dem Paylater-Popup führte.

_AC-11855 - [GitHub-Problem](https://github.com/magento/magento2/issues/38624) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37401)_

#### [Problem] Aktualisieren des js.js-DOM-Texts, neu interpretiert als HTML

Durch die Verwendung von innerText wird das Risiko einer HTML-Injektion vermieden, da diese Eigenschaften automatisch alle HTML-Sonderzeichen im bereitgestellten Text mit Escape-Zeichen versehen. Diese Fehlerbehebung hilft, Sicherheitslücken beim Cross-Site-Scripting (XSS) zu vermeiden, indem die Eingabe als reiner Text behandelt wird, anstatt als HTML interpretiert zu werden.

_AC-12035 - [GitHub-Problem](https://github.com/magento/magento2/issues/38767)_

#### ReCaptcha V2 wird an der Kasse für die deutsche Sprache falsch angezeigt

Zuvor erscheint das reCAPTCHA von unter der E-Mail-Adresse von der Kasse für Sprachen mit langen Wörtern wie Deutsch ungestylt. Danach sieht das reCAPTCHA genauso aus wie alle reCAPTCHA-Elemente aus dem Rest der Bereiche.

_ACP2E-3273 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

#### Captcha erfordert bei der Administratoranmeldung für einige Benutzer keine Interaktion

ReCaptcha für die Admin-Anmeldung wird erwartungsgemäß validiert

_ACP2E-3300 - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/8f64ab3c)_

### Lieferung

#### [Problem] Tippfehler in tracking.phtml behoben - JS-Funktionen in „currier“ in „carrier“ umbenannt

Das System verwendet nun in den in der Bestellverfolgungsvorlage verwendeten JavaScript-Handler-Funktionen korrekt den Begriff „Carrier“ anstelle des falsch geschriebenen „Currier“, um eine ordnungsgemäße Funktionsbenennung und Code-Klarheit zu gewährleisten. Zuvor wurde der falsch geschriebene Begriff „Currier“ verwendet, was zu Verwirrung und Inkonsistenz in der Codebasis führen konnte.

_AC-10757 - [GitHub-Problem](https://github.com/magento/magento2/issues/34523) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33414)_

#### UPS REST „Eine Sendung darf keine KGS/IN- oder LBS/CM- oder OZS/CM-Einheit als Maßeinheit haben“

Stellen Sie sicher, dass UPS-Tarife an der Kasse und im Warenkorb sichtbar sind.

_AC-11938 - [GitHub-Problem](https://github.com/magento/magento2/issues/38618) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/493e01f5)_

#### [Problem] Korrigieren der Schreibweise von Variablen für die Kundenadresse

Das System schreibt nun Variablen für Kundenadressen korrekt und gewährleistet so eine genaue Anzeige im Kontobereich des Frontends. Zuvor konnte eine falsche Schreibweise dieser Variablen zu Fehlern bei der Überprüfung des lokalen Codes führen.

_AC-13172 - [GitHub-Problem](https://github.com/magento/magento2/issues/32817) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32815)_

#### Tracking-Fenster mit dem falschen erwarteten Versanddatum

Zeigt das richtige Lieferdatum für den Fedex-Provider an.

_ACP2E-2738 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_

#### Abrechnungssätze werden weiterhin angezeigt, obwohl kostenloser Versand angewendet wird

Die Versandmethode Tabelle Tarif wird jetzt angezeigt, auch wenn der kostenlose Versand nach Anwendung des Coupons verfügbar wird

_ACP2E-2763 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_

#### MFTF-Test AdminCreatingShippingLabelTest schlägt fehl aufgrund von Anmeldeinformationen, die nicht in der Jenkins-Umgebung hinzugefügt wurden

MFTF-Testkorrektur

_ACP2E-2765 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

#### FedEx-Tracking-API funktioniert nicht mit REST-Anmeldeinformationen

Zuvor waren für die FedEx-Integration keine zusätzlichen API-Schlüssel für die Tracking-API erforderlich. Jetzt wurde eine neue Konfiguration hinzugefügt, um Tracking-API-Schlüssel zu unterstützen.

_ACP2E-3340 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] Ausgehandelte FedEx-Raten nicht auf REST zurückgegeben

Vor der Fehlerbehebung wurden FedEx-kontospezifische Raten in der Antwort nicht gesendet, auch wenn sie laut FedEx-Dokumentation hätten gesendet werden müssen. Nach der Fehlerbehebung werden die kontospezifischen Tarife für die Antwort gesendet, indem die Anfrage von unserer Seite geändert wird.

_ACP2E-3354 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

### Staging und Vorschau

#### Geplantes Update kann bei Verwendung eines eindeutigen benutzerdefinierten Kategorieattributs nicht aktualisiert werden

Es wurde ein Problem behoben, bei dem das Aktualisieren einer geplanten Aktualisierung für eine Kategorie nicht möglich war, wenn die Kategorie ein eindeutiges Attribut hatte

_ACP2E-3453 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

### Targeting

#### [Problem] Verwendung von CIDR-Bereichen in der Wartungs-Zulassungsliste zulassen

Das System unterstützt jetzt die Verwendung von CIDR-Bereichen in der Zulassungsliste des Wartungsmodus, sodass ein Bereich von IP-Adressen den Wartungsmodus umgehen kann. Zuvor erlaubte der Wartungsmodus, dass die IP-Liste nur einzelne IP-Adressen den Wartungsmodus umgeht.

_AC-9432 - [GitHub-Problem](https://github.com/magento/magento2/issues/37943) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30699)_

### Steuer

#### [Problem] Feature/php8.1 Konstruktor Eigenschaftsförderung wee Graph ql

Ersetzen Sie fast alle Eigenschaften mit dem Konstruktor-Eigenschaftsförderungsmodul in der Graph-SQL:

_AC-13295 - [GitHub-Problem](https://github.com/magento/magento2/issues/39309) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36975)_

#### Feste Produktsteuer (FPT) funktioniert nicht mit konfigurierbaren Produkten

FPT für konfigurierbare Produktvarianten, die ordnungsgemäß funktionieren.

_ACP2E-3193 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### Test-Framework

#### Integrationstest schlägt fehl testDbSchemaUpToDate aufgrund von JSON-Spaltentyp

Das System erkennt jetzt JSON-Spaltentypen im Datenbankschema während der Integrationstests korrekt, um Testfehler aufgrund einer Diskrepanz zwischen dem Datenbankschema und dem deklarativen Schema zu verhindern. Zuvor hat das System JSON-Spaltentypen in MariaDB fälschlicherweise als LONGTEXT identifiziert, wodurch Integrationstests fehlschlugen.

_AC-11654 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [Problem] Rechtschreibung für PHPDoc-Korrektur

Das System erkennt nun veraltete Methoden in IDEs aufgrund einer Rechtschreibkorrektur im PHPDoc korrekt. Zuvor führte ein Rechtschreibfehler im PHPDoc dazu, dass IDEs bestimmte Methoden nicht als veraltet erkannten.

_AC-13362 - [GitHub-Problem](https://github.com/magento/magento2/issues/31399) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118: Überprüfen des Verhaltens beim persistenten Warenkorb nach Ablauf der Sitzung

_AC-13478 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_

#### Beheben von statischen Tests, um die Verwendung durch Erweiterungen von 3D-Anbietern zu ermöglichen

_AC-13848 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9e383b4d)_

#### [Intern] Fehler bei der Anwendung der Vorrichtung wird während der Ausführung oder in Protokollen nicht angezeigt

&#39;-

_ACP2E-3334 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest

Feste MFTFs

_ACP2E-3458 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

### UI-Framework

#### Behebung von Sicherheitslücken in Prototype.js CVE-2020-27511

Das System wurde aktualisiert, um die Sicherheitslücke CVE-2020-27511 in Prototype.js 1.7.3 zu beheben und so die allgemeine Sicherheit des Systems zu verbessern. Vor diesem Update war das System anfällig für einen regulären Ausdrucks-Denial-of-Service (ReDOS) durch Strippen von erstellten HTML-Tags.

_AC-12128 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Grunt Less verwendet Pub/Präfix für Quellenkarten

Das System generiert jetzt bei Verwendung von grunt LESS/css-Quellzuordnungen ohne das Präfix /pub für Pfade, sodass keine Problemumgehung in der Webserver-Konfiguration erforderlich ist. Zuvor war für die Verwendung des Präfixes /pub in Quellzuordnungspfaden eine bestimmte Konfiguration im Webserver erforderlich, damit es ordnungsgemäß funktioniert.

_AC-12189 - [GitHub-Problem](https://github.com/magento/magento2/issues/38837) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38840)_

#### Feld für UI-Komponentendatei

Das System validiert das Dateifeld in einem Benutzeroberflächen-Komponentenformular jetzt korrekt, sodass das Formular ohne Fehler gesendet werden kann, wenn eine Datei ausgewählt wird. Zuvor schlug die Validierung auch dann fehl, wenn eine Datei ausgewählt wurde, was verhinderte, dass das Formular gesendet wurde.

_AC-12432 - [GitHub-Problem](https://github.com/magento/magento2/issues/38908) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39004)_

#### [Problem] Verbessertes Datumsformat in der js-Konsole: von 12 auf 24 Stunden wechseln…

Verbessertes Datumsformat in der JS-Konsole: Wechsel von 12 auf 24 Stunden

_AC-12645 - [GitHub-Problem](https://github.com/magento/magento2/issues/38983) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38972)_

#### [Problem] SourceMap-Generierung für weniger Dateien im Entwicklermodus hinzufügen

Das System generiert jetzt Quellzuordnungen für weniger Dateien, wenn sie sich im Entwicklermodus befinden, wodurch die Identifizierung der Quelle eines Stils erleichtert wird. Zuvor war es schwierig, die Quelle eines Stils zu identifizieren, wenn das System im Entwicklermodus ohne Server-seitige Kompilierung ausgeführt wurde.

_AC-12650 - [GitHub-Problem](https://github.com/magento/magento2/issues/38982) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38977)_

#### Statischer Inhalt wird für deaktivierte Module bereitgestellt

Das System schließt jetzt CSS für deaktivierte Module aus den endgültigen CSS-Ausgabedateien aus, um sicherzustellen, dass unnötige Stile nicht geladen werden. Zuvor wurde CSS für deaktivierte Module in die endgültigen CSS-Ausgabedateien eingefügt, was dazu führte, dass zusätzliche, unnötige Stile geladen wurden.

_AC-1306 - [GitHub-Problem](https://github.com/magento/magento2/issues/24666) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32922)_

#### Inkonsistentes Verhalten bei der Sortierung „Nicht vorrätig“ mit Mindestbestand-Schwellenwert

Das System sortiert jetzt Produkte im Katalog korrekt anhand der Lagerbestände, hält sich dabei an die festgelegte Mindestbestandsschwelle und verschiebt nicht vorrätige Artikel konsequent an das Ende der Liste. Zuvor war das Sortierverhalten inkonsistent, da Elemente basierend auf ihren Lagerbeständen nicht immer in der richtigen Reihenfolge angezeigt wurden und Änderungen bei der Sortierung nach dem Speichern, Aktualisieren oder Ändern der Kategoriehierarchie unvorhersehbar auftreten konnten.

_AC-13459 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_

#### Vorschlag für eine verbesserte Fehlerberichterstattung bei Problemen beim Laden von Require.js

Diese PR verbessert die Fehlermeldung, wenn eine Komponente bei Bedarf nicht geladen werden kann.

_AC-13472 - [GitHub-Problem](https://github.com/magento/magento2/issues/36761) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38971)_

#### PHP 8.4 Veraltungsfehler, die Build-Fehler in 2.4-develop verursachen

_AC-14004 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [Problem] Laden Sie den Backend-Blockkontext nicht in Frontend

Das System stellt jetzt sicher, dass der Backend-Block-Kontext nicht in das Frontend geladen wird, wodurch die Erstellung unnötiger Backend-Sitzungen und potenzieller Sitzungssperren verhindert wird. Zuvor hat das System fälschlicherweise den Backend-Blockkontext im Frontend geladen, was zur Erstellung von Backend-Sitzungen und potenziellen Sitzungssperren geführt hat.

_AC-9007 - [GitHub-Problem](https://github.com/magento/magento2/issues/37617) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36368)_

#### [Problem] Entfernen unnötiger Skripte - Überprüfungszusammenfassung

Das System optimiert jetzt die Seitenladezeit, indem unnötige JavaScript-Skripte aus dem Bewertungsabschnitt entfernt werden, anstatt Inline-CSS-Stile zu verwenden, um Code effizienter und lesbarer zu gestalten. Zuvor konnte die Verwendung von JavaScript-Skripten für den Bewertungsabschnitt die Seitenladezeit möglicherweise verlangsamen.

_AC-9168 - [GitHub-Problem](https://github.com/magento/magento2/issues/37776) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/34643)_

#### Ausnahme beim Überprüfen des Guthabens einer Geschenkkarte, wenn reCAPTCHA aktiviert ist

Benutzer können den Guthaben der Geschenkkarte auf dem Bildschirm zum Anzeigen und Bearbeiten des Warenkorbs abrufen. Zuvor wurden diese Details nicht angezeigt, während reCAPTCHA aktiviert war.

_ACP2E-2529 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [CLARIFICATION] Einhaltung der Funktionsanfrage-ADA

Das System stellt jetzt die ADA-Konformität sicher, indem es nicht unterstützte CSS-Eigenschaften entfernt und sie durch unterstützte in der Datei „print.css“ ersetzt. Zuvor führte die Verwendung nicht unterstützter CSS-Eigenschaften zu Problemen mit der Browser-Kompatibilität.

_ACP2E-2729 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] Confusion-Bibliothekscode in effect-drop.js von AC 2.4.4-p8

Das System implementiert nun die Bibliothek „effect-drop.js“ korrekt, um die ordnungsgemäße Funktion der jQuery-UI-Effekte sicherzustellen. Zuvor wurde die Bibliothek „effect-drop.js“ versehentlich mit der Bibliothek „effect-clip.js“ überschrieben, was zu Problemen mit jQuery-UI-Effekten führen konnte.

_ACP2E-3061 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/35b1b1da)_

#### Website-Kopfzeile | Sonderzeichen im Abschnitt „Kundenempfehlung“

Nach der Fehlerbehebung werden Sonderzeichen im Begrüßungsabschnitt des Kunden korrekt angezeigt.

_ACP2E-3367 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

#### Die Kundensegmentbearbeitung schlägt mit daterange fehl

Es ist möglich, ein Kundensegment mit der Bedingung „Datumsbereich“ zu speichern, wenn nur eines der Daten bearbeitet wurde.

_ACP2E-3561 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a52ff98f)_
