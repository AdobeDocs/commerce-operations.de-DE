---
source-git-commit: c96f5620bbde1b15f6419c482c790517cc8de70c
workflow-type: tm+mt
source-wordcount: '26036'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.8)

## Highlights

Die folgenden 31 Highlights gelten für die Version 2.4.8 von Magento Open Source.

### Framework

* _AC-10721_: Aktualisieren der League/Flysystem Composer-Abhängigkeiten auf die neueste Version
   * _Fix Hinweis_: Aktualisieren Sie die Abhängigkeiten von 2.x League/Flysystem Composer auf die neueste Version 3.x
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11673_: Untersuchen Sie die neuesten Versionen von php-amqplib/php-amqplib
   * _Fehlerbehebung_: Die neueste Version php-amqplib/php-amqplib wurde aktualisiert:^3.x
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11911_: jQuery/fileuploader-CSS-Bereinigung nach der Migration zur Uppy-Bibliothek
   * _Fehlerbehebung_: jQuery/fileUploader-Bibliothek wurde entfernt, da sie in die Uppy-Bibliothek migriert wurde
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für Magento CE
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12015_: ExtJS-Ordnerbereinigung nach der Migration zur jsTree-Bibliothek
   * _Fehlerbehebung_: ExtJs-Ordner wurde entfernt, da die zugehörige Funktion zu jsTree migriert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: Aktualisieren der Monolog-/Monolog-Systemabhängigkeit auf die neueste Hauptversion
   * _Fehlerbehebung_: Das System wurde aktualisiert, um die neueste Hauptversion der Bibliothek „monolog/monolog:^3.x“ zu verwenden, wodurch Kompatibilität und verbesserte Leistung gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek „monolog/monolog“, was zu potenziellen Problemen und Einschränkungen hätte führen können.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: Aktualisieren Sie die Abhängigkeit von wikimedia/less.php auf die neueste Hauptversion
   * _Fehlerbehebung_: Das System wurde aktualisiert, um die neueste Hauptversion 5.x der Bibliothek &quot;wikimedia/less.php&quot; zu verwenden, wodurch Kompatibilität und aktuelle Funktionen gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek, was zu Sicherheitsproblemen hätte führen können.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: Aktualisieren von jquery/validate-Bibliotheksabhängigkeiten auf die neueste Nebenversion
   * _Fehlerbehebung_: Aktualisieren von jquery/validate library-Abhängigkeiten auf die neueste Nebenversion 1.20.0
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: Aktualisieren der Systemabhängigkeit von moment.js auf die neueste Nebenversion
   * _Hinweis:_ Sie die Systemabhängigkeit von moment.js auf die neueste Nebenversion 2.30.1 auf.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für EE
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für B2B
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für Bundle-Erweiterungen
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: Kompatibilität mit MariaDB 11.4 LTS für CE hinzufügen
   * _Fehlerbehebung_: MariaDB 11.4-Unterstützung für Adobe Commerce und -Erweiterungen hinzugefügt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: Abonnentenoptimierung - PhpUnit10
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: Unterstützt weitere Verbindungsversuche für Redis-Sitzung und kompatibel mit colinmollenhour/php-redis-session-abstract v2.0.0
   * _Fehlerbehebung_: Die neueste Version von colinmollenhour/php-redis-session-abstract v2.0.0 wurde aktualisiert und ist mit Adobe Commerce kompatibel
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12576_: Untersuchung der Fehler bei Automatisierungstests mit MySQL 8.4 LTS
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: Kompatibilität mit MariaDB 11.4 LTS for EE hinzufügen
   * _Fehlerbehebung_: MariaDB 11.4-Unterstützung für Adobe Commerce und -Erweiterungen hinzugefügt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12715_: Aktualisieren der Laminas Composer-Abhängigkeiten auf die neueste Version
   * _Fehlerbehebung_: Das System unterstützt jetzt die neuesten Versionen von Laminas Composer-Abhängigkeiten:
laminas/laminas-serviceManager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
Gewährleistung der Kompatibilität und aktuellen Funktionalität. Zuvor konnte eine Aktualisierung auf die neuesten Versionen dieser Abhängigkeiten zu Problemen mit der Abwärtskompatibilität und Testfehlern führen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12823_: Untersuchen Sie den Fehler beim Modultest aufgrund einer Aktualisierung des phpunit-Patches während des Komponenten-Upgrades.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-13076_: [Teil 1] - Aktualisieren aller js-Bibliotheks- und npm-Abhängigkeiten mit der neuesten verfügbaren Version
   * _Fehlerbehebung_: Composer-Versionsunterstützung galt nur für die Composer-Version 2.2.x. Jetzt wurde die Unterstützung auch auf Version 2.4.x erweitert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/19844aa0>

### Reihenfolge

* _ACP2E-2709_: [Funktionsanfrage] Kunde schlägt vor, dass die Schaltfläche „Kommentar senden“ auf der Seite „Bestelldetails“ verwirrend ist und in etwas Anderes geändert werden sollte
   * _Hinweis korrigieren_: Um die Verwirrung zu minimieren, wurde die Beschriftung der Schaltfläche „Kommentar übermitteln“ auf der Seite mit den Bestelldetails in „Aktualisieren“ geändert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/488c1034>

### Sonstige

* _AC-11420_: Setzen Sie Indexer auf den Status „Bereit“, wenn eine neue Version von Adobe Commerce installiert wird
   * _Fehlerbehebung_: Nach der Installation von Magento muss der Indexerstatus standardmäßig *Bereit* sein.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: Legen Sie in der bestehenden Magento-Installation bei der Installation des Indexermoduls eines Drittanbieters die Indexer standardmäßig in der geplanten Aktualisierung fest.
   * _Hinweis:_ neuen Indexer befinden sich standardmäßig im Modus [Nach Zeitplan aktualisieren]. Zuvor war der Standardmodus &quot;[ beim Speichern]. Dasselbe gilt auch für benutzerdefinierte Indexer.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: Die Optionen für Elasticsearch 7 und 8 sollten in der Admin-Konfiguration als veraltet gekennzeichnet sein.
   * _Fehlerbehebung_: Die Option Elasticsearch 8 in der Admin Config-Option wird mit veraltetem Text angezeigt, um Benutzende darüber zu informieren, dass Elasticsearch 8 nicht mehr empfohlen wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: Textnotiz hinzufügen, wenn die Option &quot;Elasticsearch&quot; in der Admin-Konfiguration ausgewählt ist
   * _Fehlerbehebung_: Es wurde ein Textkommentar hinzugefügt, um Adobe Commerce-Admin-Benutzern mitzuteilen, dass Elasticsearch nicht mehr von Adobe unterstützt wird und nicht mehr unterstützt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-13448_: Patch zur Verbesserung der Betriebsleistung zum Preis der Stufe in 2.4.8 bereitstellen
   * _Fehlerbehebung_: Das System ermöglicht jetzt eine effizientere Massenaktualisierung von Stufenpreisen, ohne bei Verwendung des REST-API-Endpunkts &quot;/V1/products/tier-prices“ Leistungsprobleme oder Reaktionsstörungen der Site zu verursachen. Zuvor konnte die Aktualisierung einer großen Anzahl von Preisen mithilfe dieses Endpunkts zu Leistungsproblemen und mangelnder Reaktionsfähigkeit der Site führen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_: Entfernen Sie alle vertraulichen Copyright-Hinweise von Adobe aus den Magento Open Source-Repositorys
   * _Fix Hinweis_: Alle vertraulichen Copyright-Hinweise von Adobe wurden aus den Open-Source-Repositorys entfernt, sodass nur die reduzierte Form des Adobe-Copyrights verwendet wird. Zuvor enthielten einige Dateien in den öffentlichen Repositorys Adobe-Hinweise auf vertrauliche Urheberrechte, die zu Eskalationen in der Community führten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39493>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/4bca5dfe>

### UI-Framework

* _AC-12726_: [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7
   * _Fehlerbehebung_: TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu sein. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7 Page Builder
   * _Fehlerbehebung_: TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu sein. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7 - Magento2-infra - Banned Words
   * _Fehlerbehebung_: TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu sein. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Require.js-Upgrade auf die neueste Version 2.3.7 (Sicherheitslücke CVE-2024-38999)
   * _Hinweis:_ Require.js wurde auf die neueste Version 2.3.7 aktualisiert. In der vorherigen Version meldete Sicherheitslücke
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>

## Behobene Probleme

Es wurden 497 Probleme im Magento Open Source 2.4.8-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

* _AC-10042_: /V1/Transactions REST API gibt einen Fehler zurück, wenn parent_txn_id = txn_id ist
   * _Fehlerbehebung_: Das System verarbeitet jetzt korrekt die übergeordneten und untergeordneten Concept-Transaktionen, bei denen die übergeordnete Transaktions-ID mit der Transaktions-ID identisch ist, sodass beim Abfragen des /V1/transaction-REST-API-Endpunkts keine Endlosschleife entsteht. Zuvor führte dieses Szenario aufgrund der Überschreitung der maximalen Ausführungszeit zu einem schwerwiegenden Fehler.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [GraphQL] Typproblem in 2.4.7
   * _Hinweis beheben_: Das System verarbeitet jetzt beim Ausführen einer GraphQL-Abfrage Ganzzahlwerte in der GetCustomSelectedOptionAttributes-Funktion korrekt, sodass typbezogene Fehler vermieden werden. Zuvor führte das Starten einer GraphQL-Abfrage, die GetCustomSelectedOptionAttributes mit einem ganzzahligen Argument verwendet hat, zu einem Typfehler.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: Sonderzeichen in der Kategorie url_key (bei Erstellung über die REST-API)
   * _Hinweis korrigieren_: Das Sonderzeichen „Früher in category_url_key“ ist nach der Fehlerbehebung nicht vorhanden, da es das Sonderzeichen in category_url_key anzeigt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35577>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2755_: Problem mit der Rest-API nach der Aktivierung von 2FA Duo
   * _Fehlerbehebung_: Die Sicherheitsoption 2FA mit Duo generiert jetzt die richtige Signatur für die Rest-API
   * _GitHub-Code-Beitrag_: <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_: [REST API]: „Standardwert in Store-Ansicht verwenden“ bleibt nach dem Hinzufügen von Konfigurationen für ein konfigurierbares Produkt nicht aktiviert
   * _Hinweis beheben_: Das Problem wurde behoben, indem sichergestellt wurde, dass die Datenbankeinträge für die anpassbaren Optionen eines nicht standardmäßigen Speichers korrekt sind. Das Kontrollkästchen für den benutzerdefinierten Store im Abschnitt „Admin > Katalog > Produktbearbeitung > Anpassbare Optionen“ war zuvor aufgrund ungenauer Datenbankeinträge deaktiviert, auch wenn der Optionstitel für den benutzerdefinierten Store genauso geblieben ist wie der Standardstore.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: REST-API kann bei Verwendung von Oauth1 keine Anfragen mit Schrägstrich (/) in der SKU stellen
   * _Fehlerbehebung_: Vor der Fehlerbehebung waren Sie nicht in der Lage, einen erfolgreichen API-Aufruf für ein Produkt durchzuführen, das &quot;/&quot; in der SKU hatte. Jetzt können Sie eine erfolgreiche API-GET-Anfrage für Produktdetails ausführen, obwohl ihre SKU einen Schrägstrich enthält.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: Aktualisierung der Kundenadresse schlägt fehl, wenn die Aktualisierung über die REST-API erfolgt, wenn „validateDefaultAddress“ aktiviert ist
   * _Hinweis:_ API-Endpunkt funktioniert jetzt wie beabsichtigt, nachdem das Problem mit dem fehlenden ID-Schlüssel in der API-Payload behoben wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Cloud] Erstellen der Kundengruppe „Doppelter Website-Gruppenpreis“ in der Stufen-Preis-API.
   * _Fehlerbehebung_: Die Tier Price Rest-API erlaubt es jetzt nicht, die Kundengruppe „Preis der doppelten Website-Gruppe“ zu erstellen.
Zuvor war es möglich, die Kundengruppe „Duplizierte Website-Preisgruppe“ in der Stufen-Preis-API zu erstellen, die die Validierung in Admin während der Produktspeicherung nicht bestehen konnte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: Befehl mit Status kann nicht über die REST-API hinzugefügt werden
   * _Hinweis:_ Problem wurde behoben, indem die Änderung des Bestellstatus zugelassen wurde, wenn sie nur aus dem aktuellen Status stammt. Zuvor wurde der Bestellstatus nicht berücksichtigt und Änderungen in einem Bestellstatus verhindert, selbst wenn er aus demselben Status stammte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_: Asynchroner Vorgang schlägt fehl, wenn die SKU in der Payload fehlt
   * _Hinweis_: Asynchrone und Synchronisierungsvorgänge sind zuvor aufgrund von Fehlern bei der Produktspeicherung fehlgeschlagen, wenn die SKU in der Payload fehlt. Nach der Behebung schlagen die Vorgänge der asynchronen und synchronisierten Produkt-REST-API mit der entsprechenden Ausnahmemeldung fehl.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Die Basispreise können nicht mit der REST-API aktualisiert werden (der Wert von „value_id“ in „catalog_product_entity_decimal“ wird nicht korrekt inkrementiert.)
   * _Fehlerbehebung_: Vor dieser Fehlerbehebung wurde beim Aufruf der rest-API /rest/default/V1/products/base-prices die Inkrement-ID fälschlicherweise erhöht, sodass eine Lücke zwischen den Werten entstand. Nach der Fehlerbehebung wird die Inkrement-ID wie erwartet inkrementell erhöht. Auch die value_id Feldreichweite wurde vergrößert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: Bestellartikel sind in E-Mails mit Gutschriften für die API POST V1/order/:orderId/fund nicht sichtbar
   * _Fehlerbehebung_: Vor dieser Fehlerbehebung enthält eine Kundin oder ein Kunde, die bzw. der eine Gutschrift aus einer API-Anfrage erstellt, die send_email benachrichtigt, nicht das Produktdetailraster. Nachdem diese Fehlerbehebung angewendet wurde, sendet der Kunde eine Anfrage zur Gutschrift-API und findet die Produktdetails in der E-Mail.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_: Standardwerte werden für Datums- und Uhrzeitattribute mit der Produkt-Rest-API nicht festgelegt
   * _Hinweis korrigieren_: Die Standardwerte werden jetzt für Datums- und Datums- sowie Uhrzeitattribute über die Rest-API korrekt festgelegt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### APIs, Warenkorb und Checkout

* _ACP2E-3343_: Kritischer 500-Fehler: Magento\Framework\Webapi\Exception im Zusammenhang mit dem Accept-HTTP-Header
   * _Fehlerbehebung_: Nach der Fehlerbehebung gibt es kein Problem mehr mit der Angabe der „Accept“-Kopfzeile.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>

### Konto

* _AC-10782_: Das Formular „Kundenadresse“ ermöglicht zufälligen Code in den Namensfeldern
   * _Fehlerbehebung_: Das System validiert jetzt die Eingabe in den Feldern Vorname und Nachname im Formular der Kundenadresse, wodurch die Verwendung von zufälligem Code verhindert wird. Zuvor ermöglichte das System die Verwendung von zufälligem Code in diesen Feldern ohne einen Fehler auszulösen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: Aktualisierung des Administratorkennworts.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: Adresse für mein Konto beim Speichern abstürzt
   * _Fehlerbehebung_: Das System speichert Kundenadressen jetzt korrekt, selbst wenn das Feld Region nicht angezeigt wird, wodurch ein Absturz während des Speichervorgangs verhindert wird. Zuvor führte der Versuch, eine Adresse ohne angezeigtes Bereichsfeld hinzuzufügen oder zu bearbeiten, zu einem Ausnahmefehler.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: Umleitungsschleife bei URLs in Großbuchstaben
   * _Fix Hinweis_: Das System wandelt nun Großbuchstaben in URLs automatisch in Kleinbuchstaben um, wodurch eine Umleitungsschleife beim Zugriff auf die Homepage verhindert wird. Zuvor führte die Verwendung von Großbuchstaben in der Secure Base-URL beim Zugriff auf die Homepage zu einer kontinuierlichen Umleitungsschleife.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: middlename(s) nicht für Gastkonten gespeichert
   * _Fehlerbehebung_: Das System speichert nun den zweiten Vornamen für Gastkonten beim Checkout korrekt, sodass er in der E-Mail-Vorlage verfügbar ist. Zuvor wurde der zweite Vorname nicht in der Angebotstabelle gespeichert und war in der E-Mail-Vorlage für Gastkonten nicht zugänglich.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38593>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Admin: Schaltflächen für Seitenaktionen unverankert links statt rechts
   * _Fehlerbehebung_: Die Schaltflächen für Seitenaktionen werden nun korrekt auf der rechten Seite der Sticky-Kopfzeile im Admin-Bedienfeld ausgerichtet, was das professionelle Look-and-Feel verbessert. Zuvor waren diese Schaltflächen fälschlicherweise auf der linken Seite der Sticky-Kopfzeile unverankert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: `dev:di:info` Fehler in Magento 2.4.7
   * _Hinweis beheben_: Das System zeigt jetzt beim Ausführen des `dev:di:info`-Befehls die Konstruktorparameter korrekt an, sodass keine Fehler mehr auftreten. Zuvor führte die Ausführung dieses Befehls zu einem Fehler aufgrund eines Typkonflikts im -Argument.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: Kontrollkästchen „Als Kunden-Opt-in anmelden“ nicht übersetzbar
   * _Fehlerbehebung_: Das System ermöglicht es jetzt, die Felder „Als Kunden-Opt-in anmelden“ und „Als Kunden-Checkbox-QuickInfo anmelden“ im Bereich „Store-Ansicht“ festzulegen, wodurch Übersetzungen für verschiedene Store-Ansichten ermöglicht werden. Zuvor wurden diese Felder nur im Umfang der „Website“ festgelegt, wodurch Übersetzungen für einzelne Store-Ansichten verhindert wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32359>
* _AC-6071_: Der Kunde ist angemeldet, zeigt jedoch einen 404-Fehler im Frontend an.
   * _Fehlerbehebung_: Die Kunden-Dashboard-Seite für die Storefront wird jetzt wie erwartet geladen, wenn sich ein Kunde anmeldet. Zuvor konnten sich Kunden zwar anmelden, auf dieser Seite wurde jedoch ein 404-Fehler angezeigt. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35838>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Kundenattributinformationen können nicht im Abschnitt „Kundenbearbeitung“ von Admin gespeichert werden;
   * _Fehlerbehebung_: Die Store-ID des Kunden wird jetzt ordnungsgemäß pro Website-Umfang für das Admin-Kundenbearbeitungs-Formular implementiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3329_: Nach der Anmeldung sind die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.
   * _Fehlerbehebung_: Produkte, die vor der Anmeldung als Kunde zur Produktvergleichsliste hinzugefügt wurden, bleiben jetzt nach der Anmeldung erhalten.
Zuvor waren nach der Anmeldung die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Die Konfiguration von Ländern zulassen verursacht Probleme in den Konfigurationen von Kundenadressen
   * _Fehlerbehebung_: Die Auswahl der Konfiguration „Länder zulassen“ wirkt sich jetzt nicht auf Länder aus, die außerhalb des angegebenen Bereichs angezeigt werden. Zuvor durch die Konfiguration „Länder zulassen“ beeinflusste Kundenadressattribute außerhalb des angegebenen Bereichs.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3501_: VAPT: Business Logic Error - zukünftiges Datum als Kundengeburtstag
   * _Hinweis_: Das Geburtsdatum des Kunden kann nicht später als heute festgelegt werden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>

### Konto, APIs, GraphQL

* _ACP2E-3246_: Kunden-API - Anzahl von Anmeldefehlern kann nach erfolgreicher Anmeldung nicht auf 0 zurückgesetzt werden
   * _Fehlerbehebung_: Jetzt wird die Fehlernummer in der Entitätstabelle des Kunden auf null zurückgesetzt, nachdem der Kunde sich über API-Endpunkte erfolgreich angemeldet hat.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Konto, Admin-Benutzeroberfläche, B2B

* _ACP2E-3038_: Benutzer mit eingeschränkten Administratorrechten können benutzerdefinierte freigegebene Kataloge nicht immer sehen
   * _Fehlerbehebung_: Benutzende mit eingeschränktem Administratorzugriff können jetzt Kundinnen und Kunden sowie alle freigegebenen Kataloge, denen die Produkte zugewiesen sind, konsistent anzeigen und verwalten, sofern sie Zugriff auf den jeweiligen Store haben. Zuvor konnte ein Admin-Benutzer mit eingeschränktem Zugriff auf einen bestimmten Store nicht immer alle freigegebenen Kataloge sehen, denen die Produkte zugewiesen waren, oder er konnte Kunden sehen, die nicht speichern konnten, was zu Inkonsistenzen im System führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>

### Konto, Warenkorb und Checkout

* _AC-2341_: Das benutzerdefinierte Adressattribut des Kunden „select“ wird für die neue Kundenadresse nicht gerendert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/34950>

### Admin-Benutzeroberfläche

* _AC-10705_: [Problem] Berechtigungsprüfung für die Schaltfläche „Daten neu laden“ hinzufügen
   * _Fehlerbehebung_: Das System enthält jetzt eine Berechtigungsprüfung für die Schaltfläche „Daten neu laden“, um sicherzustellen, dass sie nur Benutzern mit den entsprechenden Berechtigungen angezeigt und zugänglich sind. Zuvor war die Schaltfläche „Daten neu laden“ für alle Benutzer sichtbar und klickbar, was zu einer „nicht zulässigen“ Seite führte, wenn Benutzer ohne die erforderlichen Berechtigungen darauf klickten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38283>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38279>
* _AC-11427_: [Problem] Inkonsistente Beschriftungen für Attribute in Marketing-Regeln
   * _Fehlerbehebung_: Die Beschriftungen für Kategorie- und Attributoptionen in der Warenkorb-Preisregel werden jetzt korrekt ausgefüllt
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/31232>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: Die Datenvalidierung ist erfolgreich und die Schaltfläche „Importieren“ ist beim Importieren von Produkten mit dem Verhalten „Ersetzen“ vorhanden
   * _Fehlerbehebung_: Das System validiert jetzt die Daten korrekt und blendet die Schaltfläche „Importieren“ während des Produktimports mit dem Verhalten „Ersetzen“ aus, um einen unbeabsichtigten Datenaustausch zu verhindern. Zuvor hat das System die Daten falsch validiert und die Schaltfläche „Importieren“ angezeigt, was zu potenziellen Dateninkonsistenzen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] Magento 2.4.7 lässt keine Produktfotos mit der Dateierweiterung „Großbuchstaben“ zu.
   * _Fehlerbehebung_: Das System akzeptiert jetzt das Hochladen von Produktbildern mit Großbuchstaben-Dateierweiterungen, um einen reibungslosen Produkterstellungsprozess sicherzustellen. Zuvor wurden Bild-Uploads mit Großbuchstaben-Dateierweiterungen abgelehnt, was Benutzer zwang, die Dateierweiterung in Kleinbuchstaben zu ändern.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: Ausgeblendetes Dropdown-Menü in Rastern mit Auswahl-Aktion (z. B. Inhalt > Elemente > Seiten)
   * _Fehlerbehebung_: Jetzt wurde das System für alle ähnlichen Dropdown-Listen für alle Raster korrigiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38891>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39371>
* _AC-13131_: [Problem] Fehlerbehebung Warnung: Nicht definierter Array-Schlüssel „filter“
   * _Fehlerbehebung_: Das System verarbeitet jetzt Szenarien, in denen ein neuer Benutzer noch nicht mit Lesezeichen interagiert hat, sodass keine Warnung bezüglich eines nicht definierten Array-Schlüssels „Filter“ protokolliert wird. Zuvor wurde diese Warnung protokolliert, wenn ein neuer Benutzer nicht mit Lesezeichen interagiert hatte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: Die CSV-Datei des Produktimports mit Sonderzeichen schlägt aufgrund von Code-Änderungen in der Datei Validate.php fehl
   * _Fehlerbehebung_: Das System validiert und importiert jetzt Produkt-CSV-Dateien, die Sonderzeichen enthalten, korrekt, was eine erfolgreiche Datenübertragung ermöglicht. Zuvor führte der Versuch, eine Produkt-CSV-Datei mit Sonderzeichen zu importieren, zu einem Fehler, der den Importvorgang verhinderte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13850_: Für das Feld Obligatorische Telefonnummer ist kein rotes Sternchen vorhanden.
   * _Fehlerbehebung_: Früheres rotes Sternchen wurde für Telefonnummer nicht angezeigt, aber  Telefonnummer war obligatorisch. Was nun ein festes rotes Sternchen ist, kann auf der Telefonnummer als Pflichtfeld gesehen werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c699c206>
* _AC-6975_: [Problem] Standardindexermodus auf „schedule“ festlegen
   * _Fix Hinweis_: Alle neuen Indexer befinden sich standardmäßig im **[!UICONTROL Update by Schedule]**.  Zuvor war der Standardmodus **[!UICONTROL Update on Save]**. Bestehende Indexer sind davon nicht betroffen. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problem] Indexer-Änderungsprotokolltabellen bei mview abmelden
   * _Fehlerbehebung_: Das System entfernt jetzt automatisch nicht verwendete Änderungsprotokolltabellen, wenn ein Index von „Aktualisierung planmäßig“ in „Aktualisierung beim Speichern“ geändert wird. Der Index wird dadurch als ungültig markiert, um sicherzustellen, dass keine Einträge übersehen werden. Zuvor würde ein Wechsel eines Index zu „Aktualisierung beim Speichern“ nicht verwendete Änderungsprotokolltabellen im System belassen und alle geänderten Indizes als „gültig“ markieren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: Kein Link zum Versand bei Zahlungen an der Kasse in der Mobiltelefonansicht
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Checkout-Titel/Links „Versand“ und „Überprüfung und Zahlungen“ in der mobilen Ansicht immer oben auf der Seite sichtbar sind, sodass Benutzende einfach zwischen Schritten navigieren und notwendige Korrekturen vornehmen können. Zuvor waren diese Titel/Links in der mobilen Ansicht ausgeblendet, sodass es für Benutzende schwierig ist, ihren aktuellen Schritt zu kennen oder zu vorherigen Schritten zurückzukehren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: Die Abfrage von Versandkommentaren für Kundenbestellungen CREATED_AT wird in +0 Zeitzone zurückgegeben, die sich nicht in der konfigurierten Zeitzone des Geschäfts befindet
   * _Fehlerbehebung_: Das System zeigt jetzt korrekt das Feld „created_at“ aus Versandkommentaren in der konfigurierten Zeitzone des Kunden an, wenn die Abfrage „Kundenaufträge“ verwendet wird. Zuvor wurde das Feld „created_at“ in der Zeitzone +0 angezeigt, unabhängig von der konfigurierten Zeitzone des Kunden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-phrases bricht die Übersetzungsintegrität
   * _Fehlerbehebung_: Der Befehl `bin/magento i18n:collect-phrases -o` erfasst und fügt nun neue Ausdrücke aus JavaScript- und PHTML-Dateien hinzu, um sicherzustellen, dass Übersetzungen korrekt in der Übersetzungsdatei widergespiegelt werden. Zuvor konnte das System nicht mehrzeilige Übersetzungsausdrücke aus JavaScript-Dateien und Ausdrücke aus .phtml-Dateien in die Übersetzungsdatei einbeziehen, was zu unvollständigen oder falschen Übersetzungen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: Apostroph im Namen der Store-Ansicht wird durch &amp;#039; ersetzt.
   * _Hinweis korrigieren_: Die Filter für die Store-Ansicht des Rasters zeigen jetzt Apostrophe korrekt an
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Favicon-Upload kann .ico-Dateien nicht validieren
   * _Fix Hinweis_: Der Fehler bei der Dateivalidierung wurde in „Dateivalidierung fehlgeschlagen“ aktualisiert. Überprüfen Sie die Bildverarbeitungseinstellungen in der Store-Konfiguration.“ Zuvor hieß es einfach „Dateivalidierung fehlgeschlagen“.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: In der Galerie in PageBuilder wird eine alte Miniaturansicht anstelle eines neu hochgeladenen Bildes angezeigt
   * _Fehlerbehebung_: Generieren Sie Bildvorschauen für Bilder, die gelöscht und mit demselben Namen über die Mediensammlung im Page Builder-Inhalt erneut hochgeladen wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: Durch das Speichern von Produkten durch Admin-Benutzende mit anderem Rollenbereich werden vorhandene zugehörige Produktinformationen im Produkt überschrieben/gelöscht
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurden die zugehörigen Produkte zurückgesetzt und leer, wenn der sekundäre Admin-Benutzer auf die Schaltfläche Speichern klickte, ohne das zugehörige Produkt zu ändern. Nach dieser Fehlerbehebung klickt der sekundäre Admin-Benutzer auf die Schaltfläche Speichern , das Produkt wird nicht zurückgesetzt und erfolgreich gespeichert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Es können nicht mehr als 200 Bestellungen exportiert werden
   * _Fehlerbehebung_: Die Serverbeschränkungen für die Anfragengröße von zuvor gesendeten IDs wurden vernachlässigt, indem die HTTP-Anfrage von GET in POST geändert wurde, um das Problem zu beheben. Aufgrund der Serverbeschränkungen für die GET-Anfragengröße trat zuvor das Problem auf.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Meldung bei Validierung der Checkout-Seite falsch.
   * _Fehlerbehebung_: Wenn ein erforderliches Feld leer gelassen wird, z. B. „Adresse“, zeigt die Server-seitige Validierung die Nachricht nicht an. Die Client-seitige Validierung stellt sicher, dass die Fehlerbenachrichtigung für das erforderliche Feld angezeigt wird, in der steht: „Dies ist ein erforderliches Feld.“ Zuvor wurde zusätzlich zur Client-seitigen Validierungsmeldung die Meldung „Adresse ist erforderlich“ angezeigt, wenn ein erforderliches Feld leer gelassen wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Problem mit der Vorlage zum Zurücksetzen des Kennworts bei einem Admin-Benutzer
   * _Hinweis:_ Problem wurde durch Verwendung des richtigen Schlüssels behoben, der jetzt den Admin-Benutzernamen in die E-Mail-Vorlage enthält und den Betreff ordnungsgemäß ausfüllt. Zuvor bestand das Problem aus einem veralteten Schlüssel, der verwendet wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: Doppelte Schrägstriche in der Kundensegment-URL
   * _Hinweis korrigieren_: Doppelte Schrägstriche werden in der URL nicht angezeigt, wenn im Raster auf „Filter zurücksetzen“ geklickt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: Für bestimmte zugelassene Länder ist kein Kabeljau verfügbar
   * _Fehlerbehebung_: Jetzt ist Nachnahme für bestimmte Länder verfügbar, wenn sie benötigt wird, und   AC-3216 funktioniert erwartungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: Status der benutzerdefinierten erstellten Bestellung kann nicht aktualisiert werden
   * _Notiz korrigieren_: &#39;
Wir können jetzt den Status der benutzerdefinierten Bestellung aktualisieren, während der Status zuvor nur geändert werden konnte, wenn der aktuelle Status entweder „Verarbeitung läuft“ oder „Betrug“ war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38659>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: Der Status der Versandadresse wird nicht automatisch aktualisiert
   * _Fehlerbehebung_: Vor der Fehlerbehebung war die Region (oder Regions-ID) der Versandadresse nicht mit den Rechnungsinformationen der Adresse synchronisiert. Jetzt werden sowohl die Versandadressenregion als auch die Regions-ID ordnungsgemäß aktualisiert, wenn die Informationen zur Rechnungsadresse geändert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: Zurücksetzen-Schaltfläche funktioniert nicht bei Admin-Benutzer hinzufügen/bearbeiten
   * _Hinweis korrigieren_: Zuvor funktionierte die Schaltfläche „Zurücksetzen“ auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“ nicht. Jetzt funktioniert die Schaltfläche „Zurücksetzen“ im Admin-Bedienfeld unter „System“ > „Berechtigungen“ > „Alle Benutzer“ auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“ ordnungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: Fehlererkennung und CORS-Fehler beim Routing der Magento-Admin-URL
   * _Fehlerbehebung_: Wenn die benutzerdefinierte Admin-Domain nach der Fehlerbehebung eine Subdomain der Hauptdomain ist, kann auf den Admin nur über die konfigurierte Subdomain zugegriffen werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37663>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: Beschädigte Validierung für „Maximal zulässige Menge im Warenkorb“
   * _Fehlerbehebung_: Wenn wir `Maximum Qty Allowed in Shopping Cart` leer gelassen haben, hat es zuvor keine Ausnahme ausgelöst, obwohl hier kein leerer Wert akzeptiert wird. Wenn diese Fehlerbehebung angewendet wird, werden beim Einfügen einer leeren Zeichenfolge Ausnahmen ausgelöst, sodass das Produkt nicht gespeichert werden kann.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problem mit der PageBuilder-Vorschau] Die Schaltflächen in der Page Builder-Spalte werden nicht korrekt ausgerichtet
   * _Hinweis korrigieren_: Die Schaltflächen in den Spalten des Seiten-Builders sind jetzt korrekt ausgerichtet. Zuvor waren sie in den Page Builder-Spalten falsch ausgerichtet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: Bericht „Bestellte Produkte“ wird nicht exportiert. 404-Fehler.
   * _Fehlerbehebungshinweis_: Der Bericht &quot;Bestellte Produkte&quot; wird an CSV übergeben und XML funktioniert jetzt wie erwartet
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: TinyMCE JS-Fehler in der Konsole nach JS-Minimierung aktivieren mit Produktionsmodus
   * _Fehlerbehebung_: Zuvor wurden durch die Aktivierung der JavaScript-Minimierung im Produktionsmodus im Admin-Bedienfeld JavaScript-Fehler im Zusammenhang mit TinyMCE 6 in der Browser-Konsole angezeigt, was sich auf die Funktionalität und das Benutzererlebnis auswirkte. Dieses Problem wurde nun behoben, sodass TinyMCE 6 reibungslos funktioniert und keine Fehler erzeugt werden, auch wenn die JS-Minimierung aktiviert ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Antrag auf zusätzliche Änderungen, um die Fehlerbehebung ACP2E-3375 vollständig abzuschließen
   * _Korrekturhinweis_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: Automatisch Aktivierung neuer ACL-Berechtigungen
   * _Korrekturhinweis_: Neu Berechtigungen, die benutzerdefinierten Modulen hinzugefügt werden, gewähren nicht mehr automatisch Zugriff auf alle vorhandenen User-Rollen, es sei denn, sie werden explizit konfiguriert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: Benutzerbericht für Admin-Aktionsprotokoll zeigt keine Details für adminhtml_user_delete an
   * _Fix Hinweis_: Adminhtml_user_delete protokolliert jetzt wichtige Details korrekt. Zuvor wurden keine Protokolle für das Löschen von Benutzern generiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: Warenkorbregel mit Versandbedingung wird bei der Bestellung von Administrator nicht angewendet
   * _Fehlerbehebung_: Wenn die Warenkorbpreisregel bisher einen Rabatt für die Versandmethode mit dem Coupon hat, kann er nicht über die Admin-Benutzeroberfläche angewendet werden. Nachdem diese Fehlerbehebung angewendet wurde, wird der Rabatt auf den Warenkorbpreis mit einem Coupon für eine bestimmte Versandmethode erfolgreich von der Admin-Benutzeroberfläche aus angewendet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [FRESH] HEX-Code wird in SWATCH nicht korrekt aktualisiert
   * _Fehlerbehebung_: HEX-Code, der manuell vom Benutzer in der Farbauswahl „Visual Swatch“ eingegeben wird, wird vom System nicht mehr geändert. Zuvor wurden bei bestimmten HEX-Codes aufgrund von Konversionsfehlern zwischen Farbmodellen leichte Anpassungen vorgenommen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Admin-Benutzeroberfläche, B2B

* _AC-13628_: B2B-Anmeldung als Kunden-Header hat noch das Magento-Branding
   * _Fehlerbehebung_: Zuvor zeigt die Storefront-Kopfzeile mit dem Magento-Branding „Sie sind jetzt als &lt;Kundenname> in &lt;Storename> verbunden“. Was jetzt behoben ist und die Kopfzeile mit ADOBE-Branding angezeigt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/96dec499>

### Admin-Benutzeroberfläche, Zahlungs-/Zahlungsmethoden, Bestellung

* _AC-13520_: Transaktionsautorisierung wird nach der Bestellung des PayPal-Smart-Buttons nicht auf der Registerkarte Transaktion angezeigt
   * _Fix Hinweis_: Das System zeigt nun die Transaktionsautorisierung auf der Registerkarte Transaktion korrekt an, nachdem eine Bestellung mit dem PayPal Smart Button aufgegeben wurde. Zuvor wurde die Autorisierungstransaktion nicht auf der Registerkarte Transaktion angezeigt, nachdem auf die Schaltfläche „Autorisieren“ geklickt wurde, und es wurde keine neue Transaktion vom Typ „Autorisierung“ erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Admin-Benutzeroberfläche, Leistung

* _ACP2E-3169_: Nach der Aktualisierung auf 2.4.5-p8 treten 500 Fehler auf, wenn eine Bestellung vom Administrator erstellt wird
   * _Fehlerbehebung_: Beim Aktivieren der HTML-Minimierung konnte zuvor keine Bestellung vom Administrator aufgegeben werden. Nachdem die HTML-Minimierung aktiviert wurde, kann die Bestellung vom Administrator aufgegeben werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin-Benutzeroberfläche, Versand

* _ACP2E-2519_: Die Anzahl der Couponcodes wird in der   Die Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“, wenn eine Bestellung mit Mehrfachversand aufgegeben wird.
   * _Fehlerbehebung_: Wenn früher eine Bestellung mit mehreren Versandvorgängen aufgegeben wurde, wurde die Anzahl der Gutscheincodes nicht in der Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“ aktualisiert. Jetzt wird die richtige Anzahl sowohl in der „Verwendeten Zeit“ angezeigt, die die gewünschten Werte bei Multi-Versand widerspiegelt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/4745100c>

### Admin-Benutzeroberfläche, Staging und Vorschau

* _ACP2E-3424_: [Cloud] Wenn Sie eine Vorlage mit fehlenden Bildern entfernen, wird Pub/Media gelöscht
   * _Fehlerbehebung_: Zuvor wurde der Ordner „pub/media“ gelöscht, wenn der Vorschaubildname für eine PageBuilder-Vorlage fehlte. Nach der Korrektur wird nur die Vorlage gelöscht und das Vorschaubild gefunden, falls vorhanden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/Reporting

* _AC-9922_: Google Analytics CSP-Fehler https://region1.analytics.google.com
   * _Hinweis beheben_: Das System lässt jetzt bei aktiviertem Google Analytics korrekt Verbindungen zu &quot;https://region1.analytics.google.com&#39;&quot; zu, wodurch CSP-Fehler (Content Security Policy) vermieden werden. Zuvor führte die Aktivierung von Google Analytics und die Anzeige der Website aus der EU zu CSP-Konsolenfehlern aufgrund einer Weigerung, eine Verbindung zu &quot;https://region1.analytics.google.com&#39;&quot; herzustellen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: Fortschrittsbericht funktioniert nicht
   * _Fehlerbehebung_: Das System unterstützt jetzt die Generierung von Datendateien für erweiterte Berichte für extragroße Datensätze, indem Berichte in Stapeln von 10.000 geladen und geschrieben werden. Zuvor konnte das Modul für erweiterte Berichterstellung keine Datendateien für besonders große Datensätze generieren, was zu Fehlern von „MySQL Server ist verschwunden“ während der Ausführung des Cron-Auftrags analytics_collect_data führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Problem mit der Sichtbarkeit des Datumsbereichs für vom Administrator bestellte Produkte.
   * _Fehlerbehebung_: Der Benutzer kann ein beliebiges Datum aus dem Bericht Bestellte Produkte auswählen. Zuvor wird nach einer Tabellenaktualisierung durch die Auswahl von „Von“ das „Bis“-Datum zurückgesetzt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Falsche cURL-Kopfzeilen, die dazu führen, dass `newrelic:create:deploy-marker` nicht funktionieren
   * _Fehlerbehebung_: Das System formatiert jetzt cURL-Kopfzeilen korrekt, sodass der `newrelic:create:deploy-marker`-Befehl erfolgreich eine Bereitstellungsmarkierung in New Relic erstellen kann. Zuvor verhinderten falsche cURL-Kopfzeilen die Erstellung einer Bereitstellungsmarkierung in New Relic.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3183_: Die inlineJS-Skriptüberwachung von NewRelic verursacht CSP-Fehler
   * _Fehlerbehebung_: NewRelic-Browser-Überwachungsskripte werden jetzt von der Anwendung anstelle des APM-Agenten eingefügt, um die Einhaltung von CSP (Content Security Policy) zu gewährleisten. Zuvor waren die vom APM-Agent injizierten NewRelic-Browser-Überwachungsskripte nicht konform mit CSP und haben dazu geführt, dass die Skripte nicht ausgeführt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: Abfragen in die Tabelle sales_bestsellers_aggregated_daily einfügen werden im Projekt mit großem Auftragsvolumen langsam
   * _Fehlerbehebung_: Zuvor dauerte es sehr lange, bis der aggregierte Tagesbericht für Bestseller für eine große Anzahl von aufgegebenen Bestellungen erstellt wurde. Jetzt wird der Bericht rechtzeitig erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Bestellberichte mit dem falschen Währungssymbol
   * _Fix Hinweis_: Das Währungssymbol für Bestellbeträge im Bestellbericht wurde fälschlicherweise aus Währung/Optionen/Basis übernommen. Es wurde jetzt korrigiert, um Währung/Optionen/Standard für ein genaues Reporting zu verwenden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Cloud] Falsche Berechnungen im Couponnutzungsbericht
   * _Fehlerbehebung_: Die Umsatzsumme im Couponberichtsraster wird jetzt korrekt berechnet, indem sowohl der „Rabattsteuerausgleichsbetrag“ als auch der „Versandrabatt-Steuerausgleichsbetrag“ einbezogen werden. Zuvor fehlten diese Beträge in der Berechnung, was zu Diskrepanzen zwischen der Verkaufssumme und den Auftragsdaten führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: Probleme mit freigegebenen &quot;&lt;project_id>/var/tmp“
   * _Hinweis:_ temporären Analytics-Datenexport-Dateien wird das sys-tmp-Verzeichnis verwendet, das für häufigen Zugriff und Änderungen besser geeignet ist. Um Konflikte zu vermeiden, falls mehrere Instanzen auf demselben Server ausgeführt werden, wurde der tmp-Pfad aktualisiert, sodass er die eindeutige ID einer Instanz verwendet
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/Reporting, B2B

* _ACP2E-2300_: B2B - Sitemap enthält Produkte/Kategorien, die nicht dem freigegebenen Katalog zugewiesen sind
   * _Fehlerbehebung_: Beschränken Sie die von der Sitemap generierten Kategorien und Produkte auf die Kategorien und Produkte, die nur dem öffentlichen freigegebenen Katalog und/oder der Einrichtung der Katalogkategorie zugewiesen sind.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Reporting, Cloud

* _ACP2E-3067_: Magento verwirft die meisten New Relic-Cron-Transaktionen #34108
   * _Fehlerbehebung:_ meldet korrekt Cron-auftragsbezogene Transaktionen an NewRelic. Zuvor wurden einige Cron-Job-bezogene Transaktionen als „OtherTransaction/Action/Unknown“ in NR angezeigt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: Metrik in NR kann für Hintergrundtransaktionen irreführend sein - Follow-up von ACP2E-3067
   * _Fehlerbehebung_: Background Transactions (cron) will use New Relic app name defined in the config settings
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_: Produkte, die einem freigegebenen Katalog zugewiesen sind, werden beim Ausführen eines partiellen Index nicht am Frontend angezeigt
   * _Fehlerbehebung_: Produkte, die über die REST-API einem freigegebenen Katalog zugewiesen wurden, sind jetzt nach Abschluss der partiellen Indizierung sofort in der Storefront sichtbar. Zuvor waren Produkte nur nach einer vollständigen Neuindizierung sichtbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3044_: Unnötige Ränder im Abschnitt Meine Bestellungen
   * _Fehlerbehebung_: Zuvor wurde ein zusätzlicher Container (Auftragsreferenzen) erstellt, der zusätzliche CSS-Klassen anwandte, was dazu führte, dass unnötige Rahmenlinien unterhalb der Bestellnummer im Abschnitt Meine Bestellungen angezeigt wurden, der jetzt nicht sichtbar ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quotes cron löscht Angebote von bis zu noch genehmigten Bestellungen
   * _Fix Hinweis_: Angebote, die jetzt in Bestellungen verwendet werden, werden von sales_clean_quotes Cron-Auftrag nicht gelöscht
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>

### B2B, Framework

* _AC-9607_: Das Filtern des Firmenrasters und der anschließende Versuch, einen CSV-Export für das Raster durchzuführen, schlagen fehl und lösen eine Ausnahme aus
   * _Fehlerbehebung_: Das System ermöglicht jetzt einen erfolgreichen CSV-Export der Rasterdaten des Unternehmens im Admin-Bedienfeld, auch wenn Filter wie „Ausstehender Saldo“ und „Unternehmenstyp“ angewendet werden. Zuvor führte das Anwenden bestimmter Filter und der Versuch, die Rasterdaten zu exportieren, zu einem Fehler und einer Ausnahme.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/44cef3a9>

### Bündel

* _AC-10826_: Fehlermeldung bei der Validierung des Storefront-Bundles größer als 1
   * _Fehlerbehebung_: Das System zeigt jetzt nur noch eine Validierungsfehlermeldung an, wenn die Schaltfläche „Zum Warenkorb hinzufügen“ angeklickt wird, ohne Kontrollkästchen-Optionen für ein gebündeltes Produkt auszuwählen. Zuvor zeigte das System mehrere Validierungsfehlermeldungen für jedes nicht ausgewählte Kontrollkästchen an.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3ea26621>

### Warenkorb und Checkout

* _AC-10660_: Ausnahme wird beim Hinzufügen eines Produkts zum Warenkorb auf der Seite „Produkt vergleichen“ nicht ordnungsgemäß verarbeitet
   * _Fehlerbehebung_: Das System verarbeitet jetzt Ausnahmen korrekt, wenn ein Produkt von der Seite „Produkt vergleichen“ zum Warenkorb hinzugefügt wird und eine Meldung des Nachrichten-Managers im Controller angezeigt wird. Zuvor führte eine Ausnahme dazu, dass eine JSON-codierte Seite zurückgegeben wurde, anstatt ordnungsgemäß erfasst und verarbeitet zu werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38200>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag sendet keine Transaktionspreise und -summen.
   * _Fehlerbehebung_: Das System sendet jetzt die Transaktionspreise und -summen korrekt an Google Tag, wenn GTag aktiviert ist, was eine genaue Verfolgung von E-Commerce-Daten gewährleistet. Zuvor wurde die Währung fälschlicherweise als Teil der „All“-Bestellungen gesendet, anstatt mit der einzelnen Bestellung verknüpft zu werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37348>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Problem] [Checkout] Abhängige Anweisungen in fehlgeschlagener E-Mail-Vorlage für Zahlung aktualisiert
   * _Fehlerbehebung_: Die Versandadresse und Versandmethode in der E-Mail-Vorlage für fehlgeschlagene Zahlungen für virtuelle Produkte wird jetzt korrekt weggelassen, sodass die E-Mail nur relevante Informationen enthält. Zuvor enthielt die fehlgeschlagene Zahlungs-E-Mail für virtuelle Produkte fälschlicherweise die Versandadresse und die Versandmethode.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32781>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: Magento 2 meldet sich beim Checkout mit vorhandenem Kunden an und gibt im Firefox-Browser einen Konsolenfehler aus
   * _Hinweis beheben_: Das System ermöglicht es Benutzern jetzt, sich während des Checkout-Prozesses anzumelden, ohne dass Konsolenfehler im Firefox-Browser auftreten. Zuvor führte der Versuch, sich während des Checkouts als bestehender Kunde anzumelden, zu einem Konsolenfehler in Firefox.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38557>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [Problem] Regression der Verkaufsregeln in 2.4.7
   * _Fehlerbehebung_: Das System validiert jetzt die Verkaufsregeln korrekt, was die Anwendung eines Gutscheincodes auf einen Warenkorb verhindert, wenn die Produktbedingung mit keinem Produktnamen übereinstimmt. Zuvor konnte eine Verkaufsregel angewendet und ein Rabatt auf den Versandbetrag gewährt werden, selbst wenn die Produktbedingung mit keinem Produktnamen übereinstimmte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38671>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Problem] Verkaufsregel WarenkorbFeste Berechnung : Falscher Rabattbetrag
   * _Fixhinweis_: Das System berechnet jetzt den Rabattbetrag für Verkaufsregeln mit festen Warenkorbbeträgen korrekt und stellt sicher, dass genaue Rabatte unabhängig von Änderungen an den Warenkorbartikeln angewendet werden. Zuvor konnte der Rabattbetrag falsch variieren, wenn Artikel im Warenkorb geändert wurden, was manchmal zu erheblich größeren Rabatten als erwartet führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38694>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Problem] Der Lader blockiert die Versandmethoden, nachdem die Postleitzahl geändert wurde. Validierungsregeln für Versandraten
   * _Fehlerbehebung_: Das System verarbeitet jetzt benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten korrekt, sodass der Lader die Versandmethoden nicht blockiert, nachdem die Postleitzahl während des Checkouts in der Versandadresse geändert wurde. Zuvor führte eine Änderung der Postleitzahl in der Versandadresse während des Checkouts dazu, dass der Lader die Versandmethoden blockiert und nicht verschwindet, wenn benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten verwendet wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: Die Gutscheincode-Funktion funktioniert auf der Kaufbestätigungsseite in Magento 2.4.7 nicht ordnungsgemäß
   * _Fehlerbehebung_: Das System aktiviert jetzt das Eingabefeld für Rabattcode/Coupon auf der Checkout-Seite für virtuelle und herunterladbare Produkte, sodass Benutzer Rabattcodes wie erwartet anwenden können. Zuvor war die Eingabe des Rabattcodes/Coupons deaktiviert und der Text des Schaltflächentitels wurde als „Coupon abbrechen“ angezeigt, was Benutzer daran hinderte, Rabattcodes anzuwenden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_: Das Kontrollkästchen für Nutzungsbedingungen lässt HTML in der Storefront nicht zu
   * _Fehlerbehebung_: Das System unterstützt jetzt die HTML-Formatierung im Checkbox „Geschäftsbedingungen“ auf der Storefront, was eine bessere Anpassung und Lesbarkeit ermöglicht. Zuvor wurde der Checkbox-Text im Nur-Text-Format angezeigt, wobei alle verwendeten HTML-Tags ignoriert wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: Die für einen angemeldeten Benutzer erstellte Warenkorb-Preisregel wird fälschlicherweise für einen nicht angemeldeten Benutzer angewendet
   * _Fehlerbehebung_: Die Warenkorbpreisregel für angemeldete Benutzer wird jetzt korrekt entfernt, wenn sie aufgrund des Cookie-Ablaufs automatisch abgemeldet werden. So wird sichergestellt, dass der Rabatt nicht auf nicht angemeldete Benutzer angewendet wird. Zuvor wurde die Regel zum Warenkorbpreis auch dann angewendet, wenn sich der Benutzer abgemeldet hatte, was dazu führte, dass auf nicht angemeldete Benutzer ein falscher Rabatt angewendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38944>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Problem] [FEATURE] Leistungsoptimierung großer Warenkörbe durch…
   * _Fehlerbehebung_: Das System optimiert jetzt die Leistung für große Warenkörbe, indem doppelte getActions-Aufrufe verhindert werden, was die Geschwindigkeit und Effizienz von Warenkorbvorgängen erhöht. Zuvor wurde bei einem Warenkorb mit mehreren Artikeln die getActions-Funktion mehrmals aufgerufen, was die Systemleistung verlangsamte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39292>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39290>
* _AC-8103_: Umsatzsteuer in der Adressausgabe
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Übersetzung des Textes „VAT“, „T“, „F“ in den Adressen-Renderern, sodass Benutzer diese Begriffe in die spezifische Sprache des Geschäfts übersetzen können. Zuvor waren diese Begriffe nicht übersetzbar, was die Benutzer dazu zwang, eine Problemumgehung anzuwenden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36942>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: Doppelte Bestellungen mit derselben Angebots-ID zur gleichen Zeit mit wenig Zeitunterschied
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem Adobe Commerce-Kunden auf doppelte Bestellungen stießen, die mit derselben QuoteID aufgegeben wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Beständiger Warenkorb während des Checkout-Schritts gelöscht
   * _Fehlerbehebung_: Nach der Fehlerbehebung wird die persistente Sitzung nicht beendet, wenn Sie die Zahlungsmethode während des Checkouts auswählen, während Sie nicht angemeldet sind.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: Reorder fügt nicht zugewiesenes Produkt zum Warenkorb hinzu
   * _Fehlerbehebung_: Zuvor können für die verschiedenen Stores Produkte aus dem anderen Store neu bestellt werden. Nachdem diese Fehlerbehebung nur auf denselben Store angewendet wurde, kann dasselbe Produktumfang neu bestellt werden, wenn die Kundenkontofreigabe aktiviert ist
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: In Admin wird der „Warenkorb“ auf der linken Seite nicht aktualisiert, wenn die Artikel ausgewählt werden und „Zum Warenkorb wechseln“ auf der rechten Seite angezeigt wird
   * _Fehlerbehebung_: Der „Warenkorb“ auf der linken Seite wird aktualisiert, wenn Sie die Artikel auswählen und „Zum Warenkorb wechseln“ auf der rechten Seite in der Admin-Seite. Zuvor funktionierte diese Funktion nicht, da die umgewandelten Warenkorbelemente nicht aus der Sitzung leer wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Cloud] Verkaufsregel nicht auf erste Bestellung von Multi Shipping angewendet
   * _Fehlerbehebung_: Nach der Fehlerbehebung wird der Rabatt für jede Bestellung desselben Multi-Shipping-Angebots korrekt angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Cloud]-Produktionsanfragen zum Hinzufügen desselben Produkts zum Warenkorb führen zu zwei separaten Elementen in der Warenkorb-REST-API
   * _Fehlerbehebung_: Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte das parallele Anfordern desselben Produkts über die REST-API zum Warenkorb, zu mehreren Zeileneinträgen für dieselbe SKU.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Das Cookie kann nicht gesendet werden. Größe von „image-messages“ beim Versuch, eine Neuanordnung vorzunehmen
   * _Hinweis beheben_: Der Neuanordnungsprozess erzeugt jetzt keine eigenen Fehler. Dies beruht auf der Auflistung der in den Warenkorb integrierten Artikelprüfungen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Die Standard-Versandadresse ist beim Checkout nicht ausgewählt
   * _Fehlerbehebung_: Im Kontext der aktivierten Adresssuche wird jetzt die standardmäßige Versandadresse ausgewählt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [CLOUD] graphql addProductsToCart API-Problem mit benutzerdefinierter Option
   * _Fehlerbehebung_: GraphQL fügt dasselbe Produkt mit verschiedenen benutzerdefinierten Optionen korrekt in den Warenkorb
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Mehrere Adressen werden dem Konto beim Checkout als neuer Kunde hinzugefügt
   * _Hinweis beheben_: Das System speichert jetzt eine neue Kundenadresse nur einmal, wenn die Bestellung nicht erstellt werden konnte, wodurch die Erstellung mehrerer identischer Adressen im Falle von Fehlern bei der Bestellplatzierung verhindert wird. Zuvor speicherte das System jedes Mal eine neue Adresse, wenn ein Bestellplatzierungsversuch unternommen wurde, unabhängig davon, ob der Auftrag erfolgreich erstellt wurde oder nicht.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Die Neuanordnung einer Kundenbestellung über ein Gastbestellungsformular führt zu einem leeren Warenkorb
   * _Fehlerbehebung_: Zuvor wurde der Kunde bei der Neubestellung über die Seite Bestellungen und Rücksendungen zur Anmeldeseite weitergeleitet. Nachdem diese Fehlerbehebung angewendet wurde, wird der registrierte Kunde bei der Neubestellung korrekt zur Seite Warenkorb anzeigen weitergeleitet. Der Fluss funktioniert genauso wie bei Gastkunden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: Administratorbenutzer mit eingeschränkten Rollenressourcen kann den Warenkorb nicht anzeigen
   * _Fehlerbehebung_: Zuvor konnte der Admin, der über Einschränkungen verfügt, den abgebrochenen Warenkorb nicht über das Admin-Bedienfeld für eine zugehörige Website sehen. Nachdem diese Fehlerbehebung angewendet wurde, kann der eingeschränkte Administrator den Transaktionsabbruch im Admin-Bedienfeld einsehen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_: [Cloud] Schnellbestellung Große SKU-Leistung
   * _Fehlerbehebung_: Die Checkout-Leistung wurde verbessert, wenn in den Warenkorbpreisbedingungen verwendete Attribute nicht für alle Produkte vorhanden sind und die MAP-Funktion (Minimum Advertised Price) aktiviert ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Duplizierte Artikel im Warenkorb
   * _Fehlerbehebung_: Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte die parallele Anforderung, dasselbe Produkt zum Warenkorb in der Storefront hinzuzufügen, zu mehreren Zeileneinträgen für dieselbe SKU.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: Die E-Mail-Bestätigung der Checkout-Bestellung wird an E-Mails gesendet, die in Vor-/Nachname eingegeben wurden
   * _Fehlerbehebung_: Die E-Mail-Bestätigung für die Kaufbestätigung, die zuvor gesendet wurde, als ein E-Mail-ähnliches Muster in die Felder Vorname und Nachname eingegeben wurde, wird nicht mehr gesendet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: Checkout Versandadresse Formular mit falscher Adresse aktualisieren
   * _Fehlerbehebung_: shippingAddressFromData wird jetzt pro Website im lokalen Speicher gespeichert. Zuvor konnte eine Adresse von der falschen Website während des Checkouts automatisch in das Versandadressenformular eingefügt werden, wenn ein Store-Code in der URL verwendet wurde und der Checkout von mehreren Websites während derselben Gastsitzung initiiert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_: Geschenkkarte Produkt | Beim Zusammenführen des Warenkorbs werden Geschenkkarten zusammengeführt
   * _Fehlerbehebung_: Geschenkkartenprodukte werden jetzt korrekt im Warenkorb zusammengeführt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_: Die Persistenz des Warenkorbs wird beim Abmelden nicht eingehalten
   * _Fehlerbehebung_: Hinzugefügte Funktion „Merken Sie sich mich bei der Kundenanmeldung“ zum Authentifizierungs-Popup und zur Checkout-Anmeldung.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: Vorhandene Anführungsdaten werden nicht aktualisiert/nicht angezeigt. Erstellen Sie stattdessen einen neuen Anführungsdatensatz, wenn Trigger_recollect = 1 ist.
   * _Fehlerbehebung_: Die Artikel im Warenkorb des Kunden verschwinden nicht mehr, da ein Produkt gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3618_: [CLOUD] Funktion der Schaltfläche neu anordnen
   * _Fehlerbehebung_: Wenn Sie eine Bestellung im Administratorbereich neu bestellen, werden jetzt Produkte mit Lager zum Angebot hinzugefügt, obwohl es einige Produkte in der ursprünglichen Bestellung gibt, die nicht mehr vorrätig sind. Vor der Fehlerbehebung wurden keine Produkte zum neuen Angebot hinzugefügt, wenn Produkte ohne Lager in der ursprünglichen Bestellung waren.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: Suchvorgänge funktionieren nicht mit Postleitzahlen
   * _Fehlerbehebung_: Die Suche nach Abholorten nach Postleitzahl funktionierte für niederländische Lokalisierungen nicht ordnungsgemäß. Nach der Fehlerbehebung liefert die Suche nach dem Abholort Ergebnisse basierend auf der Postleitzahl.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/344fce23>

### Warenkorb &amp; Checkout, Checkout/ Eine Seite Checkout

* _AC-9386_: [Zufallsfehler] Das E-Mail-Feld wird nicht gerendert oder benötigt viel Zeit, um auf der Kaufbestätigungs-, Versand- oder Zahlungsseite anzuzeigen.
   * _Korrekturhinweis_: Commerce rendert das **[!UICONTROL Email]** Feld jetzt auf der Checkout Versand- und Zahlungsseite wie erwartet. Zuvor war dieses Feld entweder nicht vorhanden oder wurde nur langsam gerendert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/e1babcfd>

### Warenkorb und Kasse, Bestellung

* _ACP2E-3097_: Datumsauswahl für ein Produkt mit mehreren anpassbaren Optionen, wobei Datumsfelder bei der Bestellung von einem Administrator nicht funktionieren
   * _Fehlerbehebung_: Die Datumsauswahl wird jetzt für alle Datumsfelder korrekt angezeigt, wenn ein Produkt mit mehreren anpassbaren Datumsoptionen im Erstellungsprozess von Admin-Aufträgen konfiguriert wird. Zuvor wurde die Datumsauswahl nur für das erste Datumsfeld angezeigt, sodass die verbleibenden Felder keine Datumsauswahl aufweisen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Warenkorb und Checkout, Versand

* _AC-12119_: Sofortkauf „Günstigster Versand“ für konfigurierbare Produkte defekt
   * _Korrekturhinweis_: Die Funktion Sofortkauf hat fälschlicherweise die teurere In-Store-Lieferung Option für konfigurierbare Produkte anstelle der günstigsten Flatrate-Methode ausgewählt. Diese Fehlerbehebung stellt sicher, dass die richtige Versandart auf der Grundlage des tatsächlichen Preises ausgewählt wird.&quot;
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38811>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Katalog

* _AC-10910_: Die Bereinigung der Datenbanktabelle cron_schedule bereinigt keine nicht vorhandenen Aufträge
   * _Fix Hinweis_: Das System bereinigt jetzt automatisch die Datenbanktabelle cron_schedule und entfernt Einträge für Aufträge, die nicht mehr im System vorhanden sind. Dadurch wird eine optimale Leistung gewährleistet, indem eine minimale Anzahl von Zeilen in der Tabelle beibehalten wird. Zuvor wurden Einträge für Aufträge von inaktiven oder entfernten Modulen nicht bereinigt, was zu einer unnötigen Datenakkumulation in der cron_schedule-Tabelle führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: Stufenpreis wird nicht aus konfigurierbarem Produkt gelöscht
   * _Fehlerbehebung_: Das System entfernt jetzt den Stufenpreis eines Produkts korrekt, wenn es von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wird, um eine genaue Preisanzeige im Frontend zu gewährleisten. Zuvor wurde der Stufenpreis eines konfigurierbaren Produkts nicht gelöscht, wenn ein Produkt von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wurde, was zu einer Diskrepanz beim angezeigten Preis führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: Kategoriebeschreibung WYSIWYG ist in einer nicht standardmäßigen Storeview leer
   * _Fehlerbehebung_: Die Kategoriebeschreibung wird jetzt im WYSIWYG-Editor korrekt gespeichert und angezeigt, wenn eine Kategorie auf der Store-Ansichtsebene bearbeitet wird. Zuvor war der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38622>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38623>
* _AC-11970_: Konfigurierbare Produkte können nicht mit einer benutzerdefinierten Option neu angeordnet werden
   * _Fehlerbehebung_: Das System verarbeitet jetzt die Neuanordnung von konfigurierbaren Produkten mit einer einzigen benutzerdefinierten Checkbox-Option korrekt, was eine erfolgreiche Warenkorberstellung ermöglicht. Zuvor führte der Versuch, solche Produkte neu zu bestellen, zu einem Fehler und verhinderte, dass Artikel zum Warenkorb hinzugefügt wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_: [Problem] Wortlaut des Filterelements in der mehrschichtigen Navigation korrigieren
   * _Fehlerbehebung_: Das System verwendet jetzt korrekt die Wörter „Element“ und „Elemente“ im Filterelement für die mehrschichtige Navigation, wodurch die Klarheit und Genauigkeit der Filterbeschreibungen verbessert wird. Zuvor wurden diese Wörter falsch verwendet, was zu Verwirrung bei Benutzenden führen kann, die in den Filteroptionen navigieren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Datum- und Uhrzeitformat für benutzerdefinierte Option funktioniert nicht
   * _Fehlerbehebung_: Das System wendet das konfigurierte Datumsformat jetzt korrekt auf benutzerdefinierte Produktoptionen vom Typ Datum an, um sicherzustellen, dass das Datumsformat im Frontend korrekt angezeigt wird. Zuvor spiegelten Änderungen an der Datumsformatkonfiguration das Frontend für benutzerdefinierte Optionen des Typs Datum nicht wider.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38925>
* _AC-13068_: Dropdown-Optionen fehlen
   * _Fehlerbehebung_: Wenn Sie ein neues Attribut mit mehr als 20 Werten erstellen, zeigt das System jetzt alle Werte in der Dropdown-Liste korrekt an. Zuvor wurden nur die ersten 20 Werte oder andere ausgewählte Seitenwerte angezeigt, wodurch die verbleibenden Werte fehlten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Problem] Aktuelle Sore-ID für Laufzeitcache der Kategorie verwenden
   * _Fehlerbehebung_: Das System verwendet jetzt korrekt die aktuelle Speicher-ID für den Laufzeitcache der Kategorie, um zu verhindern, dass Daten überschrieben werden, wenn die Emulation verwendet wird, oder benutzerdefinierter Code die Kategorie in verschiedenen Stores speichert. Zuvor stammte das in der Laufzeit gespeicherte Objekt möglicherweise aus dem falschen Speicher, was zu einer Datenüberschreibungen führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39310>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update löst eine Ausnahme aus
   * _Hinweis beheben_: Das System akzeptiert jetzt korrekt einen booleschen Wert, wenn die Option —no-update im Befehl sampledata:deploy verwendet wird, um Fehler bei der Bereitstellung von Beispieldaten zu vermeiden. Zuvor wurde bei der Verwendung dieses Befehls ein Fehler ausgelöst, da das System fälschlicherweise einen ganzzahligen Wert erwartet hatte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39344>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [Problem] Behebung der Verwendung des EAV-Cache-Typs
   * _Fehlerbehebung_: Das System verwendet nun den EAV-Cache-Typ an allen relevanten Stellen korrekt, um ein konsistentes und effizientes Daten-Caching sicherzustellen. Zuvor wurde der EAV-Cache-Typ nicht konsistent verwendet, was zu potenziellen Ineffizienzen und Inkonsistenzen bei der Datenzwischenspeicherung führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: Die erweiterte Katalogsuche mit leeren Daten wird in die Verzweigung für Suchergebnisse [.2.4.dev verschoben]
   * _Fehlerbehebung_: Das System speichert Benutzer jetzt korrekt auf der Seite „Erweiterte Suche“ und zeigt eine Fehlermeldung an, wenn sie versuchen, eine Suche durchzuführen, ohne Daten einzugeben. Zuvor wurden Benutzer bei einer leeren Suche zur Seite für die erweiterte Katalogsuche weitergeleitet, wobei eine Meldung angezeigt wurde, die sie aufforderte, ihre Suche zu ändern.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_: [Problem] Produktlayout basierend auf attribute_set
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Anpassung des Produkt-Layouts auf der Grundlage des Attributsatzes und bietet so eine praktischere und effizientere Möglichkeit, die Produktanzeige im Frontend-Store zu verwalten. Zuvor konnte das Layout nur nach SKU oder Produktarten angepasst werden, was für viele Produkte oder bestimmte Artikel nicht immer praktisch war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38790>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: Fehlender eindeutiger Schlüssel in der Tabelle eav_attribute_option_value
   * _Fehlerbehebung_: Das System enthält jetzt einen eindeutigen Schlüssel für die Spalten „option_id“ und „store_id“ in der Tabelle „eav_attribute_option_value“, was verhindert, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hat. Zuvor konnte ein fehlerhafter Code dazu führen, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hatte, was Probleme bei der Bearbeitung von Produkten oder Attributen verursachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/24718>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Problem] Verwenden Sie die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte
   * _Fehlerbehebung_: Das System verwendet jetzt die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte, was die Modularität verbessert. Zuvor wurden im Produkt-Indexer der Kategorie hartcodierte Werte verwendet, was die Flexibilität und Anpassungsfähigkeit einschränkte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37200>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: Der Währungs-Code ändert sich nicht im Widget „Neues Produkt“
   * _Fehlerbehebung_: Der Währungs-Code im Widget „Neues Produkt“ wird jetzt korrekt aktualisiert, wenn die Währung im Frontend geändert wird. Dies gewährleistet die Konsistenz der Währungsanzeige auf der Website. Zuvor hatte das Ändern der Währung im Frontend keine Auswirkungen auf den Währungs-Code, der im Widget Neues Produkt angezeigt wird.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: Regulärer Preis wird nicht auf PLP für konfigurierbares Produkt angezeigt
   * _Fehlerbehebung_: Der reguläre Preis wird jetzt auf Produktlistenseiten für konfigurierbare Produkte angezeigt, die untergeordnete Produkte mit Sonderpreis enthalten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: Stock-Informationen werden im visuellen Merchandising-Raster nicht korrekt angezeigt
   * _Hinweis korrigieren_: Der Lagerbestand wird jetzt entsprechend dem ausgewählten Store angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: Widget-Inhalte werden auf der CMS-Seite nicht aktualisiert
   * _Fehlerbehebung_: Das System aktualisiert jetzt den Widget-Inhalt auf einer CMS-Seite, wenn ein Produkt als neu festgelegt und gespeichert wird, und stellt sicher, dass die Seite die aktualisierte Produktsammlung anzeigt. Zuvor wurde die Seite aufgrund der falschen Cache-Identitäten, die für das Widget im Cache verwendet wurden, nicht aktualisiert, um das neue Produkt anzuzeigen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: Probleme beim Einsparen von erweiterten Preisen für Bundle-Produkte
   * _Fix-Hinweis_: Leistungsverbesserung durch Bundle-Produkteinsparung.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [On-Premise]-Neuindizierungsprozess ist beim Erstellen von Katalogpreisregeln ineffizient
   * _Fix Hinweis_: Durch das Speichern einer Katalogpreisregel werden Indexer nicht ungültig, sondern nur die betroffenen Produkte neu indiziert
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Aktualisieren von Datums- und Uhrzeitattributen des Produkttyps über den CSV-Import
   * _Fix Hinweis_: Jetzt verfügen Datums-/Uhrzeitattribute über einen Zeitanteil in den exportierten Daten. Es ist auch möglich, die Zeit für solche Attribute mithilfe des Imports zu aktualisieren. Auch wenn „Einschließungsfelder“ aktiviert ist, werden Attributwerte in der Spalte „additional_attributes“ in doppelte Anführungszeichen gesetzt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38306>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: Keine entsprechende Fehlermeldung, wenn die Website-ID in der Anfrage falsch ist
   * _Fehlerbehebung_: Jetzt wurde die entsprechende Fehlermeldung hinzugefügt, die angezeigt wird, wenn die Website-ID in der Anfrage falsch ist. Zuvor gab es keine Validierung, wenn die Website-ID in der Anfrage falsch war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: Das Produktbild geht verloren, nachdem ein vorhandenes geplantes Update gelöscht wurde, das sich nicht auf das Bild auswirkt
   * _Fehlerbehebung_: Produktbilder werden beim Löschen der Staging-Aktualisierung nicht entfernt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] Falscher Bundle-Produktpreis bei Verwendung mit Stufenpreisen
   * _Hinweis:_ zuvor bei der Berechnung bestimmter prozentualer Rabatte, auf 2 Dezimalpunkte aufgerundet, werden unterschiedliche Endpreise für die Warenkorb- und Produktlistenseite/Produktdetailseite generiert. Nachdem diese Fehlerbehebung angewendet wurde, ist der Endpreis für das Bundle-Produkt derselbe wie auf der Produktdetailseite, der Produktlistenseite und der Mini-Warenkorbseite.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: Regel für Katalog-Promotions funktioniert nicht mit dem Attribut quantity_and_stock_status
   * _Fehlerbehebung_: Das Attribut quantity_and_stock_status wird jetzt von der Regel für die Katalogbeförderung berücksichtigt, die zuvor beim Generieren eines neuen Produkts von der Admin-Seite aus nicht berücksichtigt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35627>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: Spaltenwerte der Produktentität aktualisiert_at werden beim Aktualisieren des Preises über die REST-API nicht aktualisiert
   * _Fehlerbehebung_: Die Spalte „Zuletzt aktualisiert am“ des Administrators wird zum richtigen Zeitpunkt aktualisiert, während die vorhandenen Produkte über die REST-API aktualisiert werden. Zuvor wurde die Spalte „Zuletzt aktualisiert um“ nicht ordnungsgemäß aktualisiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Nicht eindeutige Werte können über den Produktimport festgelegt werden
   * _Fehlerbehebung_: Das System erzwingt jetzt beim Produktimport korrekt die Beschränkung des eindeutigen Werts für eindeutige Produktattribute, sodass für dieses Attribut keine doppelten Werte vorhanden sind. Zuvor war es möglich, nicht eindeutige Werte für Produktattribute festzulegen, die über den Produktimport für eindeutige Werte konfiguriert wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38445>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: Produkte im Frontend verwenden Store-spezifische Daten, wenn der Einzelspeicher-Modus aktiviert ist
   * _Fehlerbehebung_: Wenn wir zuvor den Einzelspeichermodus für die standardmäßige Store-Ansicht aktiviert haben, wurden die Änderungen nicht in den Umfang auf Website-Ebene migriert. Wenn wir nach dieser Fehlerbehebung den Einzelspeichermodus aktivieren, werden die standardmäßigen speicheransichtsspezifischen Daten mit Website-spezifischen Daten synchronisiert und die möglichen Konflikte für Produkte und Kategorien werden aufgelöst.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: „Standard-Sortieren nach“ kann in einer Kategorie nicht mit der REST-API festgelegt werden
   * _Hinweis korrigieren_: Aktualisieren Sie default_sort_by korrekt für eine Kategorie über eine REST-/SOAP-API-Anfrage.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Cloud] Der Händler hat Probleme mit der Anzahl der Wunschlisten
   * _Fehlerbehebung_: Wenn Sie ein Produkt in einem Geschäft zur Wunschliste hinzufügen, erhöht sich die Wunschlistenanzahl in anderen Geschäften, die im selben Browser geöffnet sind, nicht mehr. Wenn beide Stores im selben Browser geladen wurden, stieg die Anzahl der Wunschlisten auch im anderen Store.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: Kategorieseite am Frontend zeigt bei Verwendung des Bundle-Produkts leere Slots an
   * _Fehlerbehebung_: Bundle-Produkte, die im aktuellen Store-Kontext nicht verfügbar sind, werden nicht mehr indiziert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [Cloud] Problem des Zitats in der Architektur mit mehreren Websites
   * _Fehlerbehebung_: Zuvor konnten Multi-Website-Architekturen mit unterschiedlichen Währungen und Kundengruppen Rabatte nicht korrekt auf den Store anwenden. Nachdem diese Fehlerbehebung implementiert wurde, wird die Multi-Website-Architektur mit unterschiedlichen Preisnachlässen für Kundengruppen erfolgreich auf verschiedene Stores angewendet.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38506>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Nicht erfasster TypFehler: dataRecord.slice beim Bearbeiten von Bundle-Produkten
   * _Hinweis beheben_: Beim Löschen einer Option aus dem Produktpaket tritt in der Browser-Konsole kein JavaScript-Fehler auf.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Bundle Falsche Produktpreise in Bestellbestätigung
   * _Fehlerbehebung_: Wenn eine andere Währung als die Basiswährung verwendet wurde, wird der richtige Betrag für die Bundle-Optionen in der Reihenfolge auf der Storefront angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Fehler beim Hinzufügen von YouTube-Videos
   * _Fehlerbehebung_: Produktbilder und Videos werden im globalen Umfang konfiguriert. Da ein Produktvideo nicht in einem Umfang und nicht in einem anderen enthalten sein kann, wurde die Einstellung für den YouTube-API-Schlüssel auf den globalen Umfang festgelegt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Cloud] URL-Aktualisierung nur für store_id=0
   * _Fehlerbehebung_: Der „URL-Pfad“ wird jetzt mit der richtigen Store-ID gespeichert. Zuvor war die Store-ID falsch, was dazu führte, dass beim Verschieben von Kategorien falsche URL-Pfade in der Datenbank verbleiben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all ausgeführt und ein Fehler erstellt.
   * _Hinweis beheben_: Falsche Produktverknüpfungsdaten in REST-API-Aufrufen verursachen keine kritischen Fehler mehr.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Cloud] Problem bei Mobilgeräten kann nur das PDP-Bild nicht zusammendrücken
   * _Fehlerbehebung_: Das System unterstützt jetzt die Pinch-to-Zoom-Funktion bei Produktdetailseitenbildern in der mobilen Ansicht auf Chrome, was das mobile Benutzererlebnis verbessert. Zuvor wurde das Bild in der mobilen Ansicht auf Chrome beim Doppeltippen nicht wie erwartet vergrößert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Fehlende Beschriftung in LayeredNavigation mit Optionsname 0
   * _Hinweis beheben_: Das Problem wurde behoben, indem eine leere Werteprüfung für den Attributwert 0 übersprungen wurde. Zuvor wurde es als leer betrachtet und verursachte das Problem.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: Kunden sehen Preise von anderen Kundengruppen
   * _Hinweis_: Es wurde ein Problem behoben, bei dem Informationen zu Kundengruppen aufgrund des alten Werts von X-Magento-Vary in der Anfrage in einem falschen Segment gespeichert wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Fehler beim Löschen von Paketoptionen
   * _Hinweis beheben_: Das System löscht jetzt die Bundle-Optionen korrekt, ohne einen Fehler auszulösen oder die Seite nicht mehr reagieren zu lassen. Zuvor führte der Versuch, Bundle-Optionen zu löschen, zu einem Fehler „Seite reagiert nicht“ und verhindert, dass das Produkt gespeichert wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: [Cloud] Bilddatei ist nicht im New Relic-Fehlerprotokoll vorhanden
   * _Fehlerbehebung_: Das System synchronisiert jetzt benutzerdefinierte Platzhalterbilder mit dem lokalen Speicher, um sicherzustellen, dass sie bei der Verwendung von Remote-Speicher wie AWS S3 korrekt gerendert werden. Zuvor konnten benutzerdefinierte Platzhalterbilder bei der Verwendung des Remote-Speichers nicht gerendert werden, was zu einer fehlerhaften Bildanzeige und zu Fehlerprotokollen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_: RSS-Feed für neue Produkte wird aufgrund des Caches nicht mit neuen Produkten aktualisiert
   * _Hinweis:_ RSS-Feed für neue Produkte wird jetzt aktualisiert, wenn ein Produkt als neu festgelegt und gespeichert wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: [Cloud] Die GQL-Antwort der Produktmediensammlung ist nicht nach Bildposition sortiert
   * _Fehlerbehebung_: Das System sortiert jetzt Elemente in der Mediensammlung korrekt nach der Position in der GraphQL-Antwort, um eine genaue Anzeigereihenfolge zu gewährleisten. Zuvor wurden Elemente in der Mediensammlung nicht nach Position sortiert, was zu einer falschen Anzeigereihenfolge führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Cloud] Unterkategorieelemente werden nicht in der Widget-Bearbeitung im Admin-Backend angezeigt
   * _Hinweis beheben_: Die Kategoriestruktur auf der neuen Widget-Seite sollte keine Probleme mehr beim Laden von Kategorie(n) der Stufe 5+ aufweisen. Zuvor fehlten beim Laden des Baums über die Kategorie der Ebene 5 hinaus einige Kategorien.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_: [Cloud] Zoom- und Bewegungsproblem mit zwei Fingern auf dem echten Mobilgerät
   * _Fehlerbehebung_: Das System stellt nun auf Mobilgeräten eine konsistente Bildzoom-Funktion sicher und sorgt so für ein reibungsloses und vorhersehbares Benutzererlebnis. Zuvor war die Bildzoom-Funktion inkonsistent und zoomte bei der Ansicht auf einem Mobilgerät nach einem bestimmten Punkt plötzlich heraus.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: Wenn wir die Zuweisung von Produkten zum freigegebenen Katalog aufheben, werden die Produkte auf der Wunschliste nicht gelöscht
   * _Hinweis korrigieren_: Wenn ein Produkt nicht im freigegebenen Katalog verfügbar ist, werden jetzt keine Artikel auf der Wunschliste angezeigt. Zuvor wurde auf der Seite mit der Wunschliste fälschlicherweise die Anzahl „1 Artikel“ angezeigt, auch wenn keine Artikel in der Wunschliste verfügbar waren.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Verwandte Produkte Alle auswählen/Alle auswählen Problem aufheben
   * _Hinweis korrigieren_: Zuvor funktionierten die Schaltflächen „Alle auswählen“/„Alle Auswahl aufheben“ für zugehörige Produkte nicht ordnungsgemäß, wenn ein Produkt manuell ausgewählt wurde. Nach der Fehlerbehebung funktionieren diese Schaltflächen nun auch nach der manuellen Auswahl konsistent und stellen sicher, dass alle Produkte richtig ausgewählt oder deaktiviert sind.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] Stock Warnhinweis E-Mail-Übersetzung in die falsche Sprache
   * _Fixhinweis_: Wenn Sie Stock-/Preisalarme für eine Website mit mehreren Geschäft Ansichten in verschiedenen Sprachen senden, wird in der E-Mail die Sprache des Geschäft Ansicht verwendet, in dem der Warnhinweis erstellt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: Die Namen von deaktivierten Kategorien sind in der Kategoriestruktur nicht mehr ausgegraut
   * _Hinweis korrigieren_: Zuvor waren deaktivierte Kategorien in der Kategoriestruktur nicht ausgegraut. Jetzt werden sie mit einem Graustufeneffekt angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: Konfigurierbares Formular zum Bearbeiten von Produkten verursacht Zeitüberschreitung und Speichererschöpfung
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurden konfigurierbare Produktvarianten basierend auf allen möglichen Attributoptionenkombinationen erstellt. In Fällen, in denen Attribute viele Optionen hatten, führte dies zu einem langwierigen und ressourcenintensiven Vorgang. Jetzt werden konfigurierbare Produktvarianten basierend auf vorhandenen untergeordneten Produktattributen erstellt. Dies führt zu deutlich weniger Berechnungen - und damit zu einer verbesserten Nutzung von Ressourcen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama lädt Video nicht korrekt, wenn Farbfelder verwendet werden, und die Option ist über die URL vorausgewählt
   * _Fehlerbehebung_: Produktvideos werden jetzt auf der konfigurierbaren Produktdetailseite korrekt gerendert, wenn die URL ausgewählte Optionen enthält.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: Das PageBuilder-Karussell-Widget zeigt Produkte an, die nicht den Bedingungen entsprechen
   * _Hinweis korrigieren_: Die in Widgets verwendete Produktliste berücksichtigt jetzt die Kategoriebedingung
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Validierungsfehler wird für alle Produkte in der Gruppe ausgelöst, wenn eine ungültige Menge aufweist
   * _Hinweis korrigieren_: Der Validierungsfehler wird nun für alle Produkte in der Gruppe korrekt ausgelöst, wenn ein Produkt eine ungültige Menge aufweist, was zuvor nicht der Fall war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_: [CLOUD] Sonderpreis wird nicht im konfigurierbaren Produkt angezeigt
   * _Fehlerbehebung_: Nach der Fehlerbehebung wirkt sich eine Änderung des Werts „Wird in der Produktliste verwendet“ für das Sonderpreisattribut nicht auf die Anzeige des Sonderpreises für konfigurierbare Produkte aus.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-_: Indexer Temporäre Tabellen werden nicht bereinigt, wenn der Prozess beendet wird
   * _Fehlerbehebung_: Die temporären Tabellen des CatalogRule-Indexers werden jetzt bereinigt, wenn der Indexerprozess beendet wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] Fehler bei Modultests in 2.4.7-p3
   * _Fehlerbehebung_: Versionshinweise für diesen Test sind nicht erforderlich, da es sich um eine Verbesserung des Komponententests handelt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: Leistungsproblem beim Abrufen von Lagermengen für gruppierte Produkte mit mehreren Quellen
   * _Fehlerbehebung_: Die Seite zur Bearbeitung von gruppierten Produkten und Paketen ist jetzt optimiert, wenn zugewiesene Produkte über eine große Anzahl von Inventarquellen verfügen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Präfix https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Fehlerbehebung_: Verbesserte Leistung der Admin-Kategorieseite bei einer großen Anzahl von Anker-Kategorien
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Katalog, Inhalt

* _ACP2E-3063_: [Cloud]-Cache wird nicht invalidiert.
   * _Fehlerbehebung_: Beim Speichern einer CMS-Seite mit einem aktualisierten Design-Layout wurde diese zuvor nicht ordnungsgemäß am Frontend dargestellt. Nachdem diese Fehlerbehebung angewendet wurde, wird das entsprechende Design-Layout am Frontend angezeigt, wenn wir das Design-Layout ändern und die CMS-Seite speichern.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Cloud] Anker-/Nicht-Anker-Kategorien im Inhalts-Widget umgekehrt
   * _Hinweis korrigieren_: Zuvor wurden bei Auswahl von Anzeigen unter -> Ankerkategorien alle Kategorien angezeigt, die nicht der hierarchischen Beziehung zwischen Anker und Nicht-Anker entsprachen. Nachdem diese Fehlerbehebung angewendet wurde, zeigt „Anzeigen ein“ > „Ankerkategorien“ nur Ankerkategorien (auswählbar) an und „Anzeigen ein“ > „Nicht-Ankerkategorien“ zeigt „Nicht-Ankerkategorien“ (auswählbar) an
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Kategorien funktionieren nicht mit Widgets
   * _Fehlerbehebung_: Wenn wir den CMS-Block zuvor für verschiedene Anker-/Nicht-Ankerkategorien gespeichert haben, funktionierte er nicht für die untergeordneten Kategorien, wenn er am Frontend angezeigt wurde. Nach Anwendung dieser Fehlerbehebung wird der Block an der Vorderseite für verschiedene Kategorien angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d01ee51e>

### Katalog, Framework

* _AC-9111_: Bestellabruf (Sendungen|Creditmemos|Rechnung)Sammlung - Sammlung darf nicht geladen werden
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Sammlungen für Sendungen und Gutschriften beim Abrufen aus einer Bestellung nicht vorgeladen werden, sodass zusätzliche Filter oder Bestellungen auf diese Sammlungen angewendet werden können. Zuvor wurden diese Sammlungen automatisch geladen, was weitere Änderungen verhinderte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37561>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: [Cloud]Follow-up: Nicht übereinstimmender Datenvergleich bei der Überprüfung, ob Daten Änderungen aufweisen
   * _Hinweis korrigieren_: Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein beliebiges numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Außerdem werden die von der Zeichenfolge gekapselten Gleitkommazahlen nicht geprüft. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, und führt eine strikte Typübereinstimmung durch
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>

### Catalog, GraphQL

* _ACP2E-3090_: Umgang mit Kategoriefiltern in GraphQL: includeDirectChildrenOnly und category_uid
   * _Hinweis korrigieren_: Beim Filtern nach category_uid werden nur die direkt untergeordneten Kategorien abgerufen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [Cloud] GraphQL-Produktsortierung funktioniert nicht
   * _Fehlerbehebung_: Die Sortierung von GraphQL-Produkten nach mehreren Feldern, wenn die Felder in Variablen übergeben werden, funktioniert jetzt erwartungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: Stufenpreise geben in Produkten von GraphQL einen falschen Wert zurück (im Vergleich zu Storefront)
   * _Fehlerbehebung_: Nach der Fehlerbehebung haben die für GraphQL-Anfragen zurückgegebenen Stufenpreise des Produkts den Preis pro einem Element.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>

### Katalog, Preise, Staging und Vorschau

* _ACP2E-2672_: [Cloud] Der API-Endpunkt für Sonderpreise gibt einen Fehler zurück, wenn eine große Anzahl von Produkten gleichzeitig aktualisiert wird
   * _Fehlerbehebung_: Jetzt erstellt die Special Price Bulk Update API für jeden Datumsbereich eine einzelne Kampagne anstelle mehrerer geplanter Aktualisierungen für jedes Produkt und jeden Datumsbereich. Außerdem unterstützt es gleichzeitige API-Anfragen für eine schnellere Verarbeitung einer großen Anzahl von SKUs.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>

### Katalog, Produkt

* _AC-7050_: Die Kategorieauswahlstruktur im bearbeiteten Produkt ist nicht in der gleichen Reihenfolge wie im Katalog->Kategorien
   * _Fehlerbehebung_: Der Kategorieauswahlbaum im Produktbearbeitungsabschnitt wird nun in der gleichen Reihenfolge wie unter Katalog->Kategorien angezeigt, was die Produktverwaltung in großen Katalogen erleichtert. Zuvor wurde die Kategoriestruktur im Produktbearbeitungsabschnitt in der Reihenfolge der Kategorienerstellung angezeigt, unabhängig von der Anzeigereihenfolge, die unter Katalog->Kategorien festgelegt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36104>

### Katalog, SEO

* _ACP2E-3653_: Falsche kanonische URL für Kategorie bei Seite > 1
   * _Fehlerbehebung_: Zuvor funktionierte die kanonische URL für mehrseitige Inhalte nicht ordnungsgemäß, sodass die Basis-URL durchgängig angezeigt wurde. Nachdem die Fehlerbehebung implementiert wurde, zeigt die kanonische URL für mehrseitige Inhalte jetzt jedoch korrekt die URL mit der Seiten-ID an.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Katalog, Suche

* _ACP2E-2757_: Produkte werden nicht in Kategorie und Suche angezeigt, aber direkte Links funktionieren
   * _Hinweis korrigieren_: Zuvor funktioniert das benutzerdefinierte Attribut „Ja/Nein“ mit dem _* „price attribute_code“ nicht bei der Indizierung. Nach dieser Korrektur funktioniert das benutzerdefinierte Attribut Ja/Nein erwartungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Cloud] Elastischer Suchfehler auf bestimmten Kategorieseiten
   * _Fix Hinweis_: Wenn wir das Konfigurationsticket bereits erwähnt haben und den Preis 0 für mehrere Produkte angeben, wird auf der Frontend-Kategorieseite eine Ausnahme ausgelöst. Nachdem diese Fehlerbehebung angewendet wurde, wenn mehrere Produktpreise 0 sind und wir die Kategorieseite im Frontend laden, wird keine Ausnahme ausgelöst und die Kategorieseite wird erfolgreich geladen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: Beim Erstellen des Objekts ist ein Typfehler aufgetreten: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Ausnahme
   * _Fehlerbehebung_: Nach der Fehlerbehebung kann eine Instanz der Klasse Magento\CatalogSearch\Model\Indexer\Fulltext erstellt werden, ohne $data anzugeben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [CLOUD] Problem mit Produkten wird nach dem Speichern in Magento Admin nicht in Frontend angezeigt
   * _Fehlerbehebung_: Nach der Fehlerbehebung werden konfigurierbare Produkte, die untergeordnete Produkte mit langen Namen enthalten, nicht in der Storefront verpasst.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Cloud

* _ACP2E-_: [Cloud] PHPSESSID ändert jede POST-Anfrage
   * _Fehlerbehebung_: PHPSESSID wird für einen angemeldeten Kunden nicht mehr bei POST-Anfragen im Frontend-Bereich neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde vom Backend aktualisiert wurde
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: Sitemap-Generierungswarnungen
   * _Fehlerbehebung_: Nach der Fehlerbehebung wird die Sitemap im Verzeichnis „system-tmp“ generiert und in das endgültige Ziel kopiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>

### Inhalt

* _AC-10539_: [Problem] Problem mit der Preisanzeige im Widget „Kürzlich angezeigt“
   * _Fehlerbehebung_: Das System zeigt jetzt im Widget „Kürzlich angezeigtes Produkt“ den Preis nicht vorrätiger einfacher Produkte korrekt an, wodurch die Konsistenz aller Widgets und Produktlistenseiten sichergestellt wird. Zuvor wurde der Preis für nicht vorrätige einfache Produkte aufgrund einer Bedingung in den Preisladevorlagen nicht im Widget „Kürzlich angezeigtes Produkt“ angezeigt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38167>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problem] Korrigieren Sie Tippfehler und Grammatik in der Datei acl.xsd
   * _Fehlerbehebung_: Das System korrigiert jetzt einen Tippfehler und Grammatikfehler in der Datei acl.xsd, wodurch die Klarheit und Genauigkeit der Dokumentation verbessert wird. Zuvor enthielt die Datei acl.xsd einen Tippfehler und eine falsche Grammatik, was möglicherweise zu Verwirrung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38061>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: Bild des PageBuilder-Banners nicht in der Galerie sichtbar
   * _Fix Hinweis_: Das System zeigt jetzt korrekt Bannerbilder an, die in neu erstellte Ordner in der PageBuilder-Galerie hochgeladen wurden, sodass frühere Konsolenfehler vermieden werden. Vor dieser Fehlerbehebung waren Bannerbilder in der Galerie nicht sichtbar, wenn sie in einen neuen Ordner hochgeladen wurden, was einen Konsolenfehler verursachte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: „Area code not set“ nach der Aktualisierung auf 2.4.5-p8
   * _Fehlerbehebung_: Das System schließt jetzt den statischen Prozess der Inhaltsbereitstellung erfolgreich ab, wenn das Magento_CSP-Modul aktiviert ist und „dev/js/translate_strategy“ auf „embedded“ eingestellt ist, ohne den Fehler „Area Code Not Set“ auszulösen. Zuvor schlug der statische Prozess der Inhaltsbereitstellung unter diesen Bedingungen mit dem Fehler „Area Code Not Set“ fehl.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38845>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38922>
* _AC-12692_: Die Widget-Kategoriestruktur wird nicht korrekt gerendert
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39008>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: Meldung „Standardwert wird verwendet“ wird beim Ändern des Designs auf der Design-Konfigurationsseite nicht angezeigt
   * _Fehlerbehebung_: Das System enthält jetzt eine separate Spalte, um die Meldung „Standardwert verwenden“ je nach ausgewähltem Design auf der Design-Konfigurationsseite anzuzeigen. Dadurch wird Klarheit und Sichtbarkeit des Standardwertstatus sichergestellt. Zuvor wurde die Meldung „Standardwert verwenden“ nicht angezeigt, was zu Verwirrung über den Status des ausgewählten Designs führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problem] Stellt die Abwärtskompatibilität mit TinyMCE-Plug-ins wieder her (nach…
   * _Fix Hinweis_: Das System stellt jetzt die Abwärtskompatibilität mit TinyMCE-Plug-ins wieder her, sodass Funktionen, die innerhalb des Plug-ins definiert sind, aufgerufen werden können, wenn das Widget von einem anderen Ort aus verwendet wird. Zuvor gab es aufgrund einer Änderung in der TinyMCE-Version die Plug-ins die Widgets nicht als -Objekt zurück, was zu einem Fehler beim Versuch führte, bestimmte Funktionen auf der Widget-Instanz aufzurufen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39262>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39258>
* _AC-9638_: [Problem] Problem beim Hochladen von Dateien im WYSIWYG-Editor auf der Produktseite
   * _Fehlerbehebung_: Das System zeigt jetzt die Ordnerstruktur korrekt an und ermöglicht das Hochladen von Bildern im WYSIWYG-Editor auf der Produktseite, selbst nachdem die Registerkarte „Bild und Videos“ zuerst erweitert wurde. Zuvor führte das Erweitern der Registerkarte „Bild und Videos“ zunächst dazu, dass die Ordnerstruktur nicht angezeigt wurde und eine Fehlermeldung angezeigt wurde, wenn versucht wurde, ein Bild im WYSIWYG-Editor hochzuladen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-Premise] Problem mit dynamischen Blöcken
   * _Hinweis:_ werden Widgets jetzt ordnungsgemäß in dynamischen Blöcken gerendert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [Cloud] Frontend wird aufgrund eines Problems in der Newsletter-Vorlage nicht geladen
   * _Fehlerbehebung_: Das Hinzufügen von Blöcken über den Seiteninhaltsabschnitt von CMS führt nicht mehr zu einer Ausnahme
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] Investigate-Ausnahme im Protokoll gefunden: InvalidArgumentException: Klasse ist in vendor/magento/module-rule/Model/ConditionFactory.php nicht vorhanden
   * _Fehlerbehebung_: Wenn Sie eine Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten entfernen, wird keine Ausnahme mehr in den Protokolldateien aufgezeichnet. Zuvor führte das Entfernen einer Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten dazu, dass eine kritische Ausnahme in den Protokollen aufgezeichnet wurde, obwohl dies keine Probleme im Frontend verursachte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Wechseln zum Einzelspeichermodus - Globale Inhalte werden nicht mehr angezeigt
   * _Fehlerbehebung_: Das System synchronisiert jetzt Design-Konfigurationen für Store-Ansichten mit Website-Design-Konfigurationen, wenn es den Single-Store-Modus aktiviert, um sicherzustellen, dass Inhaltsaktualisierungen im Frontend sichtbar sind. Zuvor wurde durch den Wechsel zum Einzelspeichermodus verhindert, dass Inhaltsaktualisierungen in der Storefront widergespiegelt werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: Page Builder ersetzt das Bild, wenn versucht wird, Link- und andere Nutzungsfehler hinzuzufügen.
   * _Fehlerbehebung_: Wenn Sie jetzt auf ein Bild klicken, werden Links im WYSIWYG-Editor im Textelement von Page Builder ordnungsgemäß in das Bild geladen, und das Dialogfeld für die Link-Konfiguration wird angezeigt. Auch das Hinzufügen eines Links zu einem Bild im Editor funktioniert jetzt ordnungsgemäß. Zuvor wurde das Bild durch einen Link ersetzt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: Die alte Mediensammlung kann keine Bilder rendern, wenn ein 0-Byte-Bild im Verzeichnis platziert wird
   * _Fehlerbehebung_: Das System verarbeitet jetzt 0-Byte-Bilder in der Mediensammlung, ohne die Funktionalität zu beeinträchtigen, sodass andere Bilder im Verzeichnis wie erwartet angezeigt und ausgewählt werden können. Zuvor verhinderte das Vorhandensein eines 0-Byte-Bildes in der Mediensammlung, dass alle Bilder im Verzeichnis angezeigt oder ausgewählt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Fehler von Page Builder beim Bearbeiten des CMS-Blocks
   * _Fehlerbehebung_: Das System speichert jetzt mit Page Builder korrekt im Administratorbereich vorgenommene Änderungen, ohne den Fehler „Page Builder wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben.“ In der Browser-Konsole. Zuvor trat dieser Fehler beim Versuch auf, Änderungen zu speichern, wodurch die erfolgreiche Aktualisierung des Inhalts verhindert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Keine Schaltflächen für Checkout oder Warenkorb bearbeiten im Warenkorbabschnitt
   * _Fehlerbehebung_: Das Bundle-Produkt wird jetzt fehlerfrei über Widgets zum Warenkorb hinzugefügt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3122_: Schaltfläche [CLOUD] Bild hochladen funktioniert nicht
   * _Fehlerbehebung_: Vor der Schaltfläche Bild hochladen für Banner und Regler von PageBuilder funktionierte es nicht wie erwartet. Wenn Sie jetzt darauf klicken, wird der lokale Datei-Manager geöffnet, um das gewünschte Bild zum Hochladen auszuwählen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor(): Der #2 ($height) muss größer als 0 sein. Bestimmtes Bild kann nicht hochgeladen werden
   * _Hinweis_: Das Problem, das beim Hochladen von Bildern mit einer Höhe von 0 über die Mediensammlung zu Fehlern in der Admin-Instanz führte, wurde behoben und die Asset-Synchronisierung mithilfe des Befehls sync wurde erfolgreich durchgeführt. Zuvor kann das Bild nicht über die Mediensammlung hochladen, und der Synchronisierungsbefehl schlägt auch fehl, wenn sich ein bestimmtes Bild in der Galerie befindet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from steht im Konflikt mit der Google Maps-API
   * _Fehlerbehebung_: Google Maps werden jetzt im PageBuilder-Editor ordnungsgemäß gerendert. Zuvor verhinderte ein JavaScript-Fehler, dass Google Maps korrekt gerendert wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [Cloud] - CMS-Regler spiegelt nicht die neuesten Änderungen wider
   * _Hinweis:_ Problem wurde behoben, indem sichergestellt wurde, dass die Reglerliste aktualisiert wird, während das Speicherereignis auf dem Bildschirm „Folie bearbeiten“ ausgelöst wird. Zuvor wurde das Problem ausgelöst und verursacht.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Auf der CSM-Seite tritt ein Fehler auf, wenn CMS-Blöcke mit dem Seiten-Builder in einer bestimmten Reihenfolge eingefügt werden
   * _Fix Hinweis_: Zuvor war bei einigen Versionen von PHP und OS (Linux) das Rendern von Blöcken, die über PageBuilder auf andere CMS-Blöcke verwiesen hatten, mit dem Fehler „Ein unbekannter Fehler ist aufgetreten. Bitte erneut versuchen.“ Jetzt wird der Inhalt der CMS-Blöcke innerhalb eines von PageBuilder gesteuerten Inhalts korrekt wiedergegeben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3428_: Vorschaufehler von PageBuilder bei großen Inhalten
   * _Fehlerbehebung_: Große Inhalte führten dazu, dass das Canvas-Element die Beschränkungen des Browsers überschritt und einen falschen Wert zurückgab, was den Backend-Code beschädigte (das Bild kann nicht richtig decodiert werden). Es wurde ein Problem behoben, indem die Arbeitsfläche auf die Grenze des universellen Browsers beschränkt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: Neueste Sicherheitsaktualisierungen mit TinyMCE 7 fehlender Schriftgröße
   * _Hinweis korrigieren_: Die Auswahl der Schriftgröße und der Schriftfamilie ist jetzt im WYSIWYG-Editor verfügbar. Vor dieser Fehlerbehebung waren diese bei TinyMCE 7 nicht in der Editor-Oberfläche verfügbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: TinyMCE 7 Editor Schriftgröße in der Admin in PT und nicht PX Bitte klären
   * _Fehlerbehebung_: Vor der Fehlerbehebung konnten Sie die Schriftgröße in px in WYSIWYG-Bereichen nicht angeben. Jetzt können Sie die Schriftgröße in px statt pt einstellen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: Der Produktinhaltstyp in Page Builder wird ohne korrekte Meldungen reduziert
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurde die HTML-Vorschau nicht ordnungsgemäß generiert, wenn im Widget keine Produkte vorhanden waren. Jetzt wird die leere Antwort ordnungsgemäß generiert und das Produkt-Widget wird in der Vorschau korrekt angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [Page Builder]Hinzufügen einer Produktliste zum Blockieren führt zu Fehlern
   * _Hinweis beheben_: Das Hinzufügen der Bundle-Produktliste zum -Block über den Seiten-Builder führt jetzt nicht mehr zu Fehlern
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/344fce23>

### Kunde/Kunden

* _AC-12162_: Frontend - Die Validierung des Geburtsdatums schlägt auf der Kundenerstellungsseite fehl
   * _Fix Hinweis_: Stellen Sie sicher, dass die gesamte Validierung nach dem Upgrade von moment.js Systemabhängigkeit auf die neueste Nebenversion funktionieren sollte
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-8499_: Das Textfeld „Region“ wird nicht zurückgesetzt, wenn das Dropdown-Menü „Land“ geändert wird
   * _Fehlerbehebung_: Das Textfeld Region wird jetzt zurückgesetzt, wenn das Land im Dropdown-Menü geändert wird. Dadurch wird sichergestellt, dass die vorherigen Werte nicht beibehalten werden. Beim Ändern des Landes aus der Dropdown-Liste wurde das Feld Region zuvor nicht zurückgesetzt, sodass der zuletzt gespeicherte Wert beibehalten wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: Beim Löschen eines Kunden werden nicht alle Browser-Sitzungsdaten in der Storefront für angemeldete und gelöschte Kunden gelöscht
   * _Fehlerbehebung_: Durch das Löschen eines Kunden werden nun alle Browser-Sitzungsdaten aus der Storefront für angemeldete und gelöschte Kunden wie erwartet gelöscht. Der Käufer kann weiterhin einkaufen, und sein Browser behandelt seine Sitzung als Gastsitzung. Wenn das Kundenkonto eines angemeldeten Käufers aus dem Admin gelöscht wurde, gab es zuvor im Browser des Käufers JavaScript-Fehler.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7d5e3906>

### Framework

* _AC-10037_: [Question]Unused Type configuration in `app/code/Magento/Translation/etc/di.xml`
   * _Fehlerbehebung_: Das System entfernt jetzt nicht verwendete Abhängigkeiten in der Konfiguration, was die Code-Sauberkeit und -Effizienz insgesamt verbessert. Zuvor gab es in der Konfiguration nicht verwendete Abhängigkeiten, die zu keiner Funktion beitrugen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38030>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: Frage/Problem mit V1/customers/password-Endpunkt
   * _Fehlerbehebung_: Bei der Verarbeitung von Passwortänderungsanfragen über die API hält sich das System jetzt an die in der Verwaltungs-Benutzeroberfläche festgelegten Einschränkungen, um einen potenziellen Missbrauch der Passwortrücksetzfunktion zu verhindern. Zuvor konnte die API Passwortänderungsanfragen außerhalb der in der Verwaltungs-Benutzeroberfläche definierten Regeln verarbeiten, was möglicherweise einen konstanten Stream von Zurücksetzungs-E-Mails ermöglichte, wenn gültige E-Mails bekannt waren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38238>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: Die Lackkonfiguration schließt nicht alle Marketing-Parameter aus
   * _Fehlerbehebung_: Das System schließt jetzt alle gängigen Marketing-Parameter in der Lackkonfiguration korrekt aus, um ein genaues Tracking und Analysen zu gewährleisten. Zuvor wurden bestimmte Marketing-Parameter wie „gad_source“, „srsltid“ und „msclpid“ nicht ausgeschlossen, was zu möglichen Ungenauigkeiten bei der Datenerfassung führen kann.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: Indizierungsprozess für Katalogsuchindex-Fehler
   * _Fix Hinweis_: Das System führt nun den Neuindizierungsbefehl erfolgreich aus, ohne dass Fehler auftreten, unabhängig von der mit PHP kompilierten libxml-Version. Zuvor führte die Ausführung des Befehls re-index zu einem Fehler „Catalog Search index process error during indexation process“, wenn PHP mit bestimmten Versionen von libxml kompiliert wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: Filter „created_at“, „status“ und „grand_total“ wurden zur Abfrage von Kundenaufträgen hinzugefügt und Fehler bei mehreren Filtern behoben
   * _Fehlerbehebung_: Das System unterstützt jetzt die Verwendung der Filter „created_at“, „status“ und „grand_total“ in Kundenauftragsabfragen und hat ein Problem behoben, bei dem mehrere Filter nicht korrekt angewendet wurden. Zuvor hat das System diese Filter nicht unterstützt und würde nicht alle Filter anwenden, wenn mehr als einer in einer Abfrage verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: Willkürliche Überflutung mit Abfragen von verwandten / Upsell / Crosssell-Blöcken und Preisindexierung
   * _Fehlerbehebung_: Das System optimiert jetzt Abfragen aus verwandten, Upsell- und Crosssell-Blöcken, verbessert die Leistung und verhindert, dass die Site aufgrund übermäßiger Abfragen abstürzt. Zuvor konnte das System mit Abfragen aus diesen Blöcken überlastet werden, was zu erheblichen Verlangsamungen führte und die Website möglicherweise zum Absturz brachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Exception: Warning: Try to access array offset in… -> Calendar.php since upgrade to ICU 74.1 (PHP Intl)
   * _Fehlerbehebung_: Commerce protokolliert die folgende Ausnahme nicht mehr in „exception.log“, wenn ein Käufer oder Händler die Storefront oder den Administrator besucht: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problem] Beheben von Problemen mit Kundendaten, wenn das Formular ein Element mit dem Namen &quot;`method`&quot; enthält
   * _Fehlerbehebung_: Das System identifiziert jetzt das Attribut „method“ in Formularübermittlungen korrekt, auch wenn ein Element mit dem Namen „method“ im Formular vorhanden ist. Dadurch wird eine präzise Verarbeitung der Kundendaten gewährleistet. Wenn ein Formularelement zuvor „Methode“ genannt wurde, würde dies die Identifizierung des Attributs „Methode“ bei Formularübermittlungen beeinträchtigen, was zu potenziellen Problemen bei der Verarbeitung von Kundendaten führen würde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38484>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Problem] Fix PHPDocs for \Magento\Framework\Data\Collection::getItemById
   * _Fehlerbehebung_: Die PHPDocs für die Methode \Magento\Framework\Data\Collection::getItemById wurden aktualisiert, sodass sie null als möglichen Rückgabetyp enthalten, wodurch Probleme mit statischen Analyse-Tools behoben werden. Zuvor wurde in den PHPDocs der Methode nicht null als möglicher Rückgabetyp angegeben, was zu Warnungen oder Fehlern bei der statischen Analyse führte, wenn die Methode in bedingten Anweisungen verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38439>
* _AC-11592_: [Problem] Nur gültige Voreinstellungen während des `setup:di:compile` zulassen
   * _Fehlerbehebung_: Das System gibt jetzt während des `setup:di:compile`-Befehls einen Fehler aus, wenn eine Voreinstellung für eine Klasse erstellt wird, die nicht vorhanden ist oder speziell ausgeschlossen wurde, sodass nur gültige Voreinstellungen zulässig sind. Zuvor schlugen diese Szenarien im Hintergrund fehl und machten möglicherweise alle Plug-ins, die mit den ursprünglichen Klassen verknüpft sind, unbrauchbar.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento versucht, die schreibgeschützte Eigenschaft in der __wakeup-Methode von LoggerProxy zu ändern
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Änderung von zuvor schreibgeschützten Eigenschaften in der __wakeup-Methode von LoggerProxy, wodurch ein reibungsloser Betrieb gewährleistet wird, ohne dass Benutzer gezwungen werden, eine Problemumgehung zu verwenden. Zuvor hatte der Versuch, den Wert einer schreibgeschützten Eigenschaft in der WakeUp-Methode __ LoggerProxy neu zuzuweisen, Probleme verursacht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_: [Problem] AC-2039 AC-1667 Upgrade TinyMCE Referenzen
   * _Fix Hinweis_: Die tinymce-neueste Version in composer.json wurde aktualisiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38533>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker funktioniert nicht in mehreren Threads
   * _Hinweis beheben_: Das System unterstützt jetzt Process Fork für die MView-Indizierung, wodurch Fehler bei der Indexerausführung bei der Arbeit mit mehreren Threads verhindert werden. Zuvor führte das Ausführen von ChangelogBatchWalker auf mehreren Threads zum Löschen von Tabellen, die von anderen Threads verwendet wurden, was einen Fehler während der Indexerausführung verursachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38246>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problem] Umbenennen einer falsch benannten Variablen
   * _Fehlerbehebung_: Das System benennt nun die Variable, die den Betrag an Geld enthält, der noch zurückerstattet werden kann, korrekt, um Verwirrung beim Debugging zu vermeiden. Zuvor wurde diese Variable fälschlicherweise als totalRefund bezeichnet, was zu Missverständnissen für Entwickler führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38609>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [Problem] Übergeben Sie benutzerdefinierte Attribute über XML an den aktuellen Link.
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Übergabe benutzerdefinierter Attribute an den aktuellen Link per XML, um sicherzustellen, dass diese Attribute korrekt angezeigt werden, auch wenn der Link die aktuelle Seite ist. Zuvor wurden keine benutzerdefinierten Attribute für den aktuellen Seitenlink angezeigt, da die Methode getAttributesHtml() für den aktuellen Link nicht verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/30070>
* _AC-11819_: Der integrierte FPC-Cache ist in Version 2.4.7 für einige Konfigurationen fehlerhaft
   * _Fehlerbehebung_: Das System speichert jetzt korrekt Seiten zwischen, wenn der Parameter MAGE_RUN_CODE festgelegt ist, was eine optimale Leistung gewährleistet. Zuvor wurden Seiten unter diesen Bedingungen nicht zwischengespeichert, was zu potenziellen Leistungsproblemen führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38626>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problem] Behebung von Inkonsistenzen bei der Ausnahmebehandlung zwischen Entwickler- und Produktionsmodus
   * _Fehlerbehebung_: Das System verarbeitet jetzt durchgängig Ausnahmen zwischen dem Entwickler- und dem Produktionsmodus und verhindert so eine unerwartete Weiterleitung zur Anmeldeseite, wenn eine Ausnahme ausgelöst wird. Zuvor konnte eine Inkonsistenz bei der Ausnahmebehandlung zu einer Umleitung zur Anmeldeseite im Produktionsmodus führen, anstatt die Ausnahmemeldung anzuzeigen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38639>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: „PayPal-Konto“-Übersetzung in token_list.phtml ersetzen
   * _Fehlerbehebung_: Der Abschnitt für Tokenizable-Konto-Zahlungsmethoden wird jetzt auf der Seite „Gespeicherte Zahlungsmethoden“ als „Konto“ anstelle von „PayPal-Konto“ gekennzeichnet, wodurch er besser für seine Funktion repräsentativ ist. Zuvor wurde dieser Abschnitt speziell als „PayPal-Konto“ gekennzeichnet, was irreführend war, wenn andere Token-fähige Konto-Zahlungsmethoden hinzugefügt wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35622>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37959>
* _AC-11874_: Die Abwärtskompatibilität wurde für die Klasse Magento\Catalog\Model\ProductRepository nicht mehr unterstützt
   * _Fehlerbehebung_: Die ProductRepository-Klasse behält jetzt die Abwärtskompatibilität bei, indem sie die Initialisierungs-Helper-Klasse als zweiten Parameter wiederherstellt und sicherstellt, dass Module, die von dieser Klasse erweitert werden, erwartungsgemäß funktionieren. Zuvor führte das Entfernen des Initialization Helper aus dem Konstruktor in der ProductRepository-Klasse zu einem Verlust der Abwärtskompatibilität, was Benutzer zwang, eine Problemumgehung zu verwenden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [Problem] Statische Inhaltsbereitstellung - Typfehler
   * _Fehlerbehebung_: Das System verarbeitet jetzt leere LESS-Dateien während der Bereitstellung statischer Inhalte korrekt und zeigt die Fehlermeldung „LESS-Datei ist leer“ an. Zuvor wurde ein Fehler vom Typ „Falsch“ ausgelöst, wenn während der Bereitstellung eine leere LESS-Datei auftrat.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [Problem] [Ansicht] Zusätzlicher Platz im Link- und Skript-Tag entfernt
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Link- und Skript-Tags keine zusätzlichen Leerzeichen enthalten, was für saubereren und effizienteren Code sorgt. Zuvor konnten zwischen Attributen in den Link- und Skript-Tags doppelte Leerzeichen gefunden werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32919>
* _AC-12127_: [Problem] Vermeiden Sie eine Fehlkonfiguration in der Endlosschleife.
   * _Fehlerbehebung_: Das System vermeidet jetzt eine Endlosschleife, indem es in virtuellen Typkonfigurationen die selbstreferenzielle Zuordnung verhindert. Dadurch wird sichergestellt, dass die Anwendung beim Versuch, einen selbstverweisenden Knoten zu dereferenzieren, nicht in einer Endlosschleife hängt. Wenn eine Konfiguration eines virtuellen Typs zuvor selbstverweisend war, würde dies dazu führen, dass sich die Anwendung unbegrenzt dreht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38822>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: Object Manager wird nicht für Magento\Csp\Model\Mode\Data\ModeConfigured verwendet
   * _Fehlerbehebung_: Der Objekt-Manager wird jetzt beim Erstellen des ModeConfiged-Objekts korrekt verwendet, sodass Plug-ins für dieses Objekt verwendet werden können. Zuvor wurde der Objekt-Manager nicht verwendet, was verhinderte, dass Plug-ins auf das ModeConfiged-Objekt angewendet wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38875>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: Falscher Kommentar zu Dokumentblöcken in Produkt- und Preiswarnhinweisen
   * _Fehlerbehebung_: Der Blockkommentar für die Methode deleteCustomer in den Warnhinweisen für Warenbestand und Preise wurde korrigiert, um genau widerzuspiegeln, dass die Methode alle Warnhinweise für Warenbestände oder Preise löscht, die mit einer bestimmten Kundin oder einem bestimmten Kunden und einer bestimmten Website verbunden sind, nicht mit dem Kunden von der Website. Zuvor wurde in dem Kommentar fälschlicherweise angegeben, dass die Methode zum Löschen eines Kunden von der Website war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38939>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39001>
* _AC-12594_: [Problem] Verwenden Sie die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration.
   * _Fehlerbehebung_: Das System verwendet jetzt die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration, wodurch die Netzwerkübertragung und der Overhead von Daten, die von einer bestimmten Version des Codes abhängen, reduziert werden. Diese Änderung verhindert das Überschreiben des Caches in freigegebenen Instanzen beim Austausch von Containern, was zu verbesserter Stabilität und reduzierten Ausfallzeiten führt. Zuvor verwendeten bestimmte Kernklassen gemeinsame Konfigurationstypen, was aufgrund von Unterschieden in den Codeversionen über mehrere Server hinweg zu Cache-Überschreibungen oder Anwendungsausfällen führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problem] Verweise auf Dateien aus ExtJS entfernen, die in e1ccdb entfernt wurden…
   * _Fix Hinweis_: Das System entfernt jetzt Verweise auf Dateien aus ExtJS, die zuvor entfernt wurden, wodurch Fehler in der Browser-Konsole und der Systemprotokolldatei vermieden werden. Zuvor verursachten diese Verweise Fehler, da die referenzierten Dateien nicht vorhanden waren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38960>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [Problem] Kleinere Bereinigung: Fehlerhafte Verwendung von sprintf behoben, es braucht nur 2 Platzhalter hier und w…
   * _Fehlerbehebung_: Das System verwendet nun die sprintf-Funktion korrekt mit der entsprechenden Anzahl von Platzhaltern, was die Code-Sauberkeit und -Konsistenz verbessert. Zuvor wurde die Sprint-Funktion fälschlicherweise mit einem zusätzlichen Argument verwendet, was zwar keine größeren Probleme verursachte, aber nicht die richtige Verwendung war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 entfernt FTP-Erweiterung
   * _Fehlerbehebung_: Das System enthält jetzt die FTP-Erweiterung als Abhängigkeit in der Datei „composer.json“, wodurch die erfolgreiche Konfiguration von CSV-Importen über FTP sichergestellt wird. Zuvor wurde beim Versuch, CSV-Importe über FTP zu konfigurieren, ein Fehler ausgelöst, da die FTP-Erweiterung im PHP-Paket fehlt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_: [Problem] Behebt den Verweis falscher Klassen in Magento-Modulen.
   * _Fehlerbehebung_: Das System verweist jetzt korrekt auf Klassen in -Modulen, wodurch ein reibungsloserer Betrieb gewährleistet und Abstürze aufgrund nicht vorhandener Klassen verhindert werden. Dazu gehören eine Fehlerbehebung im Indexer- und Creditmemo-Modul sowie die Implementierung der HttpGetActionInterface-Klasse in der PrintAction-Klasse. Zuvor führten falsche Klassenverweise zu Fehlern und potenziellen Systemabstürzen, und bestimmte Funktionen, wie der Dateiname für CreditMemo-PDF-Dateien und die Neuindizierung von Aktien, funktionierten nicht wie erwartet.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39126>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: Möglichkeit, Bereich für `dev:di:info` CLI-Befehl zu definieren
   * _Fehlerbehebung_: Das System ermöglicht es Entwickelnden jetzt, einen Bereich für den `dev:di:info` CLI-Befehl zu definieren, wodurch der Entwicklungs- und Debugging-Prozess verbessert wird. Zuvor konnte dieser Befehl nur Informationen für den Bereich GLOBAL anzeigen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [Problem] Fügen Sie der Formularelementvorlage „Bild“ die Eigenschaft isMultipleFiles hinzu
   * _Hinweis korrigieren_: Dieser Fix verhindert, dass die Schaltfläche „Durchsuchen, um Bild zu suchen oder hierher zu ziehen“ verschwindet, wenn ein Bild in einem Bildelement mit mehreren Dateien hinzugefügt wird.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39219>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36325>
* _AC-13279_: [Problem] Entfernen Sie alle Marketing-GET-Parameter, um den Cache zu minimieren
   * _Fehlerbehebung_: Das System entfernt jetzt alle Marketing-GET-Parameter, um die Cache-Auslastung zu optimieren, und spiegelt die Logik wider, die bei der Verwendung von Varnish verwendet wird. Zuvor konnten diese Parameter zu einer Aufblähung des Cache und einer verringerten Leistung führen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39266>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Issue] [PHPDOC] Fehlerbehebung für fehlerhafte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Fehlerbehebung_: Das PHPDoc für die Methode AllowedCountries::getAllowedCountries() wurde korrigiert, um genaue Informationen bereitzustellen und so die Klarheit und Nützlichkeit der Dokumentation zu verbessern. Bisher enthielt das PHPDoc für diese Methode falsche Informationen, was zu Verwirrung oder Missbrauch der Methode führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39246>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [Problem] Entfernt Code für PHP-Versionen, die wir nicht mehr unterstützen.
   * _Fix Hinweis_: Entfernen von Code für PHP-Versionen, die in Magento nicht mehr unterstützt werden
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39361>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Problem] ImageMagick-Adapter mit PHP8 kompatibel machen (implizite Konvertierung von float zu int)
   * _Fix Hinweis_: Das System stellt nun die Kompatibilität mit PHP8 sicher, indem es bei der Berechnung der Bildabmessungen die Gleitkommazahlen korrekt verarbeitet und Fehler aufgrund der impliziten Konvertierung von float in int verhindert. Zuvor konnte die Berechnung der Bildabmessungen zu Gleitkommazahlen führen, die bei impliziter Rundung einen Fehler verursachen würden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39402>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [Problem] [PHPDOC] Schlechtes phpdoc Magento\Framework\App\Config\ScopeConfigInterface beheben
   * _Fehlerbehebung_: Diese Aktualisierung korrigiert die PHPDoc-Anmerkungen in Magento\Framework\App\Config\ScopeConfigInterface so, dass sie den Typ des $scopeCode-Arguments für die Methoden getValue und isSetFlag genau widerspiegeln.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39492>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39199>
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http hängt von der Ursachenphrase ab OK
   * _Hinweis korrigieren_: Die Prüfung der „OK“-Phrase wurde aus Magento\Framework\Filesystem\Driver\Http::isExists entfernt
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39546>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: Der Indexer für das Kundenraster funktioniert im Zeitplanmodus nicht ordnungsgemäß
   * _Fehlerbehebung_: Das Kundenraster zu einem früheren Zeitpunkt wurde sofort aktualisiert, jedoch nach der Fehlerbehebung wird das Kundenraster nach der Cron-Ausführung aktualisiert, es wird jedoch nicht sofort wiedergegeben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: Tippfehler in einer js-Datei.
   * _Fehlerbehebung_: Das System verwendet jetzt korrekt den Begriff „Abonnenten“ in der JavaScript-Datei, um sicherzustellen, dass die zugehörigen Funktionen ordnungsgemäß funktionieren. Zuvor führte ein typografischer Fehler in der JavaScript-Datei zur falschen Verwendung des Begriffs „Abonnenten“.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36163>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Problem] Entfernen Sie verbotenes `@author` Tag
   * _Fix-Hinweis_: Das System hält sich jetzt an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37253>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Customer` (Teil 2)
   * _Fix-Hinweis_: Das System hält sich jetzt an den Kodierungsstandard, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37250>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: Leerzeichen in editorconfig Syntax bricht Regel für [{composer,auth}.json]
   * _Hinweis beheben_: Nach der Behebung eines Syntaxfehlers in editorconfig wendet das System jetzt korrekt einen Einzug mit vier Leerzeichen auf die Dateien composer und auth.json an. Aufgrund eines Leerzeichens in der EditorConfig-Syntax wurden diese Dateien zuvor falsch mit einem Einzug aus zwei Leerzeichen formatiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37394>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37395>
* _AC-8662_: [Problem] Verbesserung der Cron-Fehlerprotokollierung
   * _Fix Hinweis_: Das System erfasst und protokolliert jetzt sowohl STDERR als auch STDOUT für Cron-Prozesse und liefert wertvolle Diagnoseinformationen in Szenarien, in denen Cron-Prozesse fehlschlagen. Zuvor wurden Fehlermeldungen innerhalb von Cron-Prozessen nicht aufgezeichnet, und STDERR und STDOUT für Cron-Gruppen, die in separaten Prozessen ausgeführt werden, gingen verloren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32690>
* _AC-8984_: [Problem] Fügt der Ausgabe bestimmter Setup-Befehlszeilenbefehle einige weitere Farben hinzu
   * _Fehlerbehebung_: Das System fügt jetzt der Ausgabe bestimmter Setup-Befehlszeilenschnittstellen-Befehle mehr Farben hinzu, was die Lesbarkeit und das Benutzererlebnis verbessert. Bisher war die Ausgabe dieser Befehle aufgrund fehlender Farbdifferenzierung schwieriger zu lesen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: Beim Upgrade von Magento wird „general/region/state_required“ zurückgesetzt, wenn ein neues Land mit dem erforderlichen Bundesland bzw. der erforderlichen Region hinzugefügt wird.
   * _Fehlerbehebung_: Das System fügt das geänderte Land jetzt nur noch dann zur Konfiguration „general/region/state_required“ hinzu, wenn ein neues Land mit den erforderlichen Status hinzugefügt wird. Dadurch wird jede Unterbrechung des benutzerdefinierten Codes verhindert, der davon ausgeht, dass die Region deaktiviert ist. Zuvor würde das Hinzufügen eines neuen Landes mit erforderlichen Status die Konfiguration „general/region/state_required“ auf Standardländer mit einem erforderlichen Status zurücksetzen und möglicherweise den Shop zerstören.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Unterschied in weniger Kompilierung zwischen php &amp; nodejs Bibliothek (grunt) mit komplizierten `calc` Ausdrücken
   * _Fix Hinweis_: Korrigieren Sie den Unterschied in weniger Kompilierung zwischen php und nodejs Bibliothek (grunt) nach dem Update wikimedia/less.php:^5.x
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Fehler „Basistabelle oder Ansicht nicht gefunden“ tritt auf, wenn eine partielle Indizierung ausgeführt wird
   * _Fix Hinweis_: Die partielle Neuindizierung funktioniert jetzt korrekt mit einem großen Änderungsprotokoll im Falle einer sekundären DB-Verbindung
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: Probleme nach der Aktualisierung von MariaDB auf 10.5.1 oder höher
   * _Fix Hinweis_: Es wurde ein Problem behoben, bei dem Datums-/Uhrzeitwerte in einer DB nach dem MySQL-Upgrade :00: 0000-00-00 00 00 konvertiert wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Nicht übereinstimmende Typen beim Datenvergleich bei der Überprüfung, ob Daten Änderungen aufweisen
   * _Hinweis korrigieren_: Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein beliebiges numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, führt eine strikte Typübereinstimmung durch.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [Cloud]-Import kann nicht mit Verzeichnis-Var verwendet werden
   * _Fehlerbehebung_: Das Produkt kann unabhängig vom Dateinamen erfolgreich importiert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: Auf dem iPad mini werden das Menü und die Kopfzeile als Mobilgerät geladen. Stattdessen sollten sie als Desktop geladen werden.
   * _Fehlerbehebung_: Das System behandelt Geräte mit einer Breite von 768 Pixel jetzt als Desktop, um sicherzustellen, dass das Menü und die Kopfzeile korrekt geladen werden. Zuvor wurden Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobilansicht geladen wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3230_: Die Änderung der Spaltenlänge über db_schema.xml funktioniert nicht bei Fremdschlüsseln
   * _Hinweis beheben_: Das Ändern der Spalte mit dem Fremdschlüssel über das deklarative Schema verursacht jetzt keine Fehler mehr bei MariaDB
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Einige der Beziehungsdatensätze werden bei der Speicherung des Bestelldatensatzes in der DB gespeichert
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurden unnötige UPDATE-Abfragen ausgelöst, die die Leistung beeinträchtigen können. Nach der Fehlerbehebung wurden die unnötigen UPDATE-Abfragen entfernt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] In Admin gibt es viele JavaScript-Fehler in der Konsole
   * _Hinweis beheben_: Zuvor gab es in der Admin-Konsole viele JavaScript-Fehler. Im Admin-Bedienfeld gibt es nun keine JavaScript-Fehler mehr in der Konsole, und alle standardmäßigen JavaScript-Funktionen werden problemlos ausgeführt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: Warteschlangennachricht wurde gelöscht
   * _Fehlerbehebung_: Warteschlangennachrichten werden jetzt ordnungsgemäß gelöscht. Vor der Fehlerbehebung hätten, da das SQL-Warteschlangensystem verwendet wurde, neue Nachrichten gelöscht werden können, wenn die Bereinigungswarteschlangennachricht gleichzeitig ausgeführt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3537_: Entsprechende Cache-Schlüsseleinträge sind in Cache-Tags nicht verfügbar, daher funktioniert die Cache-Bereinigung nicht ordnungsgemäß
   * _Fix Hinweis_: Der LUA-Modus ist jetzt standardmäßig für den Redis-Cache-Garbage Collector aktiviert, um Race-Bedingungen zu vermeiden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: Wert von MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK wird ignoriert
   * _Fehlerbehebung_: Nach der Fehlerbehebung wird eine auf „false“ gesetzte ENV-Variable als bool false und nicht als String „false“ behandelt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Framework, GraphQL

* _AC-7976_: [Problem] Einführung der Unterstützung benutzerdefinierter Skalartypen für GraphQL-Schemata
   * _Fehlerbehebung_: Das System unterstützt jetzt benutzerdefinierte Skalartypen für GraphQL-Schemata, sodass Entwickelnde benutzerdefinierte Skalartypen und Implementierungen definieren können. Diese Funktion kann besonders nützlich sein, um Werte auszudrücken, die möglicherweise einer Validierung bedürfen, z. B. HTML, E-Mails, URLs, Daten usw., und für komplexere Fälle wie EAV-Attribute. Zuvor unterstützte das System nicht die Verarbeitung von benutzerdefinierten Skalartypen in GraphQL.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, UI-Framework

* _ACP2E-3324_: Möglichkeit, den Konfigurationswert zu überschreiben, selbst wenn er gesperrt ist
   * _Fehlerbehebung_: Zuvor konnte die Designkonfiguration nicht über den Befehl bin/magento config:set festgelegt werden und die gesperrten Werte konnten durch Manipulation des Formulars, das sie anzeigte, geändert werden. Nach dem Fix können gesperrte Werte, die von cli mit —lock-env oder —lock-conf gesetzt wurden, nicht mehr aktualisiert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_: Magento_GraphQL führt Header-Verarbeitungen aus, auch wenn der Header-Wert die Validierung nicht besteht
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Kopfzeilenverarbeitung nur einmal und nur dann ausgeführt wird, wenn der Kopfzeilenwert die Validierung besteht, was die Sicherheit erhöht und potenzielle Sicherheitslücken verhindert. Zuvor wurde die Header-Verarbeitung auch dann ausgeführt, wenn der Header-Wert die Validierung nicht bestanden hat, was zu potenziellen Sicherheitslücken und unerwartetem Verhalten aufgrund der doppelten Verarbeitung von Header-Werten führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: Die physischen Geschenkkartenoptionen haben nicht die richtige Sortierreihenfolge
   * _Fehlerbehebung_: Das System sortiert jetzt bei der Abfrage über GraphQL die Optionen physischer Geschenkkartenprodukte korrekt, was eine konsistente Darstellung mit dem Luma-Design gewährleistet. Zuvor war die Sortierreihenfolge gemäß dem Luma-Design falsch, was zu einer falschen Anzeige und Sortierung von Optionen wie Absendername, Empfängername und Betrag führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [Der GraphQL-Resolver-Cache] wird beim Erstellen/Bearbeiten/Verschieben/Löschen eines Staging-Updates ungültig gemacht
   * _Korrekturhinweis_: Das System stellt jetzt sicher, dass der Resolver-Cache beim Erstellen, Bearbeiten, Verschieben oder Löschen eines Staging-Updates nicht ungültig gemacht wird, sondern nur, wenn das Staging-Update auf die Entität angewendet wird. Zuvor wurde der Resolver-Cache vorzeitig ungültig gemacht, Linear bevor das Staging-Update angewendet wurde, was zu unnötigen Cache-Invalidierungen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: Fastly-Cache nicht für die Aktualisierung des Inhalts-Staging gelöscht
   * _Fehlerbehebung_: Jetzt wird GraphQL mit PageBuilder-Inhaltsantwort-Cache ungültig, wenn die PageBuilder-Inhaltsentitäten aktualisiert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Deaktivieren der mehrschichtigen Navigation - entfernt die Aggregation nicht aus GraphQL
   * _Korrekturhinweis_: Das Problem wurde behoben, nachdem die Prüfung beim Anfordern eines Produkts suchen mit Kategorie Aggregationen über eine GraphQL-Abfrage angewendet wurde, wenn die Admin-Konfigurationseinstellung &quot;Katalog > mehrschichtige Navigation > Anzeigen Kategorie Filtern&quot;.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: Der Aufruf von GraphQL-Produkten, der den Preisfilter {from:&quot;0&quot;} enthält, liefert kein Ergebnis
   * _Fehlerbehebung_: Zuvor gab GraphQL-Produkte, die mit dem Filter nach Nullpreisen suchten, aufgrund einer ausgelösten Ausnahme überhaupt keine Ergebnisse zurück. Jetzt gibt die Suche die erwarteten Ergebnisse zurück.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: Übersetzungen für Kundenrückgabeattribute werden für die jeweilige StoreView nicht in der GraphQL-API angezeigt
   * _Fehlerbehebung_: Übersetzungen für Kundenrückgabeattribute werden in der GraphQL-API für die jeweilige StoreView angezeigt.
Zuvor wurden Kundenrückgabeattribute für die jeweilige StoreView nicht in der GraphQL-API angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [Cloud] Beschädigter GraphQL-Aufruf für getPurchaseOrder mit Knotenanführungszeichen
   * _Hinweis beheben_: Der GraphQL-Aufruf für Bestellungen kann die Aufgabe ausführen, ohne dass interne Server-Fehler auftreten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Cloud] Konfigurierbare Produkte werden nicht auf der Produktions-Site angezeigt, wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist
   * _Fehlerbehebung_: Das System zeigt jetzt konfigurierbare Produkte auf der Website korrekt an, auch wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist, sondern in bestimmten Store-Ansichtsbereichen aktiviert ist.
Wenn ein Produkt zuvor in „Alle Store-Ansichten“ deaktiviert und nur in bestimmten Store-Ansichtsbereichen aktiviert wurde, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, was dazu führt, dass das Produkt nicht richtig angezeigt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: GraphQL [Cloud]-Produkte mit Fehler, wenn dasselbe einfache Produkt mehreren konfigurierbaren Produkten zugewiesen wurde
   * _Fehlerbehebung_: Zuvor gibt grapQL mit separaten konfigurierbaren Produkten mit demselben einfachen Produkt einen Fehler zurück. Nachdem diese Fehlerbehebung angewendet wurde, gibt GraphQL ohne Fehler Ergebnisse für verschiedene konfigurierbare Produkte mit demselben einfachen Produkt zurück.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [Cloud]-Problem mit Benutzerauthentifizierung und Site-übergreifendem Token-Zugriff bei der Einrichtung mehrerer Sites
   * _Fehlerbehebung_: GraphQL-Kundeninformationen und Warenkorbabfragen bei der Einrichtung mehrerer Sites überprüfen, ob der Kunde auf einer nicht standardmäßigen Website vorhanden ist.
Zuvor funktionierte die Abfrage, ohne sicherzustellen, dass der Kunde bei der Einrichtung mehrerer Sites auf einer nicht standardmäßigen Website vorhanden ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: GraphQL-WarenkorbelementeV2-Paginierung funktioniert nicht ordnungsgemäß
   * _Hinweis beheben_: Das Problem wurde behoben, indem der richtige Wert für das aktuelle Seitenargument in der Sammlungsabfrage übergeben wurde. Zuvor wurde der falsche Wert übergeben, um die aktuelle Seite festzulegen, was das Problem verursachte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3255_: [GRAPHQL]-Modellwert sollte beim Abrufen von customerCart angegeben werden
   * _Fehlerbehebung_: Die GraphQL-Abfrage „customerCart“ kann jetzt einen leeren Warenkorb erstellen, selbst wenn das Angebot nicht in der Datenbank verfügbar ist. Zuvor schlug dieser Vorgang aufgrund von Problemen mit der Ländervalidierung beim Erstellen des leeren Warenkorbs fehl.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [GraphQL] Wunschlistenelemente sind über GraphQL sichtbar, aber nicht in der Storefront sichtbar
   * _Fix Hinweis_: Produkte auf der Wunschliste, die nicht ordnungsgemäß aufgeführt sind, wenn sie über GraphQL angefordert werden. Jetzt werden Produkte auf der Wunschliste basierend auf dem bereitgestellten Store-Kontext gefiltert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] E-Mail-Inkonsistenz des Kennworts zwischen Inhalt und Betreff/Link zurücksetzen
   * _Hinweis:_ Problem wurde behoben, indem der richtige Store simuliert wurde, in dem das Konto des Kunden beim Senden der Anforderung zum Zurücksetzen des Kennworts registriert ist, unabhängig vom Website-Store.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud]-Produkte GraphQL-Abfrage gibt verwandte Produkte zurück, die nicht der aktuellen Website zugewiesen sind
   * _Fehlerbehebung_: Zuvor wurden für GraphQL-Abfragen Produkte, die mit mehreren Stores verbunden sind, für die Produktabfrage nicht richtig angezeigt. Nachdem diese Fehlerbehebung angewendet wurde, werden für Produkte in der GraphQL-Abfrage Multistore-bezogene Produkte entsprechend angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: Die Verwendung der falschen Store-ID in der GraphQL-Kopfzeile verursacht einen schwerwiegenden Speicherfehler
   * _Fehlerbehebung_: Das Senden von falschem Speicher-Code in einer GraphQL-Anfrage führt nicht mehr zu übermäßigem Speicherverbrauch.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [Cloud]-500-Antwort auf leere GraphQL-Antwort auf 2.4.7
   * _Fehlerbehebung_: Nach der Fehlerbehebung werden ungültige GraphQL-Anfragen nicht mehr in der Datei „Exception.log“ protokolliert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_: [Cloud] Probleme mit der GraphQL-API
   * _Fehlerbehebung_: Vor der Fehlerbehebung mithilfe des GraphQL-Anwendungsservers hat die Kundenadressanfrage nicht die neuesten Daten zurückgegeben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: Deaktiviertes Produkt wird weiterhin in verwandten, Upsell-, Crosssell-Elementen in der GraphQL-Abfrage angezeigt
   * _Fehlerbehebung_: GraphQL bietet jetzt die richtige Antwort für deaktivierte verwandte Produkte, Upsell- und Crosssell-Produkte
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [CLOUD]: GraphQL-Fehler Interner Server-Fehler placeOrder-Mutation
   * _Fehlerbehebung_: Die „placeOrder“-Mutation mit Coupon-Code-Informationen in der Anfrage löst keine interne Fehlerausnahme mehr aus, die Bestellung wurde erfolgreich platziert. Zuvor schlug er mit „Interner Server-Fehler“ fehl.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: Der Rabatt-Prozentsatz wird nicht für Bundle-Produkte mit dynamischem Preis berechnet
   * _Fehlerbehebung_: Fehlerbehebung hinzugefügt für „discount_percentage“ des Produkts.price_details“ zeigt nicht den richtigen Wert für Bundle-Produkte mit aktiviertem dynamischen Preis und angewendetem Rabattcoupon an.
* _LYNX-485_: Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist
   * _Fehlerbehebung_: Es wurde das Problem behoben, dass Bundle-Produkte weiterhin „IN_STOCK“ zeigten, auch wenn eines ihrer gebündelten Produkte nicht vorrätig war.
* _LYNX-486_: not_available_message und only_x_left_in_stock zeigen nicht denselben verfügbaren Bestand an
   * _Hinweis korrigieren_: Es wurde das Problem behoben, bei dem die not_available_message und only_x_left_in_stock inkonsistente Lagerverfügbarkeit zeigten
* _LYNX-488_: original_row_total-Feld gibt falschen Wert zurück
   * _Hinweis korrigieren_: Das Problem mit dem Feld original_row_total wurde behoben, das falsche Werte zurückgab, wenn benutzerdefinierte Optionen ausgewählt wurden
* _LYNX-503_: Die gruppierte Produktminiatur sollte gemäß der Konfiguration angezeigt werden     .
   * _Hinweis:_ Problem wurde behoben, um sicherzustellen, dass die gruppierte Produktminiatur gemäß den Konfigurationseinstellungen angezeigt wird
* _LYNX-512_: original_item_price beinhaltet keine Rabatte
   * _Fixhinweis_: Der original_item_price wurde aktualisiert und enthält jetzt Rabatte.
* _LYNX-530_: Meldung „Nicht verfügbar“ zeigt nicht die verfügbare Lagermenge an
   * _Fehlerbehebung_: Fehlermeldung und Fehlercode für die AddProductsToCart-Mutation behoben, sodass sie mit der Nachrichtenkonfiguration „nicht verfügbar“ übereinstimmt
* _LYNX-532_: „OUT_OF_STOCK“-Status wird auf Einfach mit benutzerdefinierten Optionen zurückgegeben Produkte mit Mehrfachauswahl-Optionen
   * _Fehlerbehebung_: Der StockStatusProvider-Resolver im Inventar-Package wurde aktualisiert, um den stock_status für einfache Produkte mit benutzerdefinierten Optionen zu beheben.
* _LYNX-533_: Fehler (GQL): cart.itemsV2.items.product.custom_attributesV2 gibt einen Server-Fehler zurück
   * _Fehlerbehebung_: Der Server-Fehler, der auftrat, wenn eine Warenkorbabfrage die benutzerdefinierten Attribute eines Produkts enthielt, wurde behoben, indem ein Produkt ohne benutzerdefinierte Attribute hinzugefügt wurde.
* _LYNX-536_: orders/date_of_first_order gibt immer null zurück
   * _Hinweis korrigieren_: Es wurde das Problem behoben, bei dem „Orders“ > „date_of_first_order“ immer null zurückgab.
* _LYNX-544_: Der Kunde darf eine teilweise versendete Bestellung nicht stornieren können
   * _Fehlerbehebung_: Die Validierung wurde hinzugefügt, um Kunden daran zu hindern, eine teilweise versendete Bestellung zu stornieren.
* _LYNX-548_: Fehlercodes für die Stornierung von Bestellungen basierend auf der Fehlermeldung
   * _Fehlerbehebung_: Die Fehlercodes für die Stornierung von Bestellungen basieren jetzt auf der spezifischen Fehlermeldung.
* _LYNX-581_: Verschieben Sie Cookie-bezogene Eigenschaften von „privat“ zurück in „geschützt“
   * _Fehlerbehebung_: Setzt die Sichtbarkeit der Eigenschaften des Klassenkonstruktors Magento\Framework\App\PageCache\Version von privat auf geschützt zurück
* _LYNX-600_: Erhöhen Sie die maximale standardmäßige GraphQL-Abfrageleistung auf 1.000
   * _Fehlerbehebung_: Die standardmäßige maximale GraphQL-Abfragekomplexität wurde von 300 auf 1.000 erhöht.
* _LYNX-620_: GQL - itemsV2 > Ursprüngliche Zeilensumme, Preisspanne Preise wird als $0.00 für herunterladbare Produkte mit Dateioptionen zurückgegeben, die separate Preise haben.
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem herunterladbare Produkte mit aktivierten Optionen für den Kauf separater Links 0 $ für itemsV2 > Ursprüngliche Zeilensumme zurückgaben, Preisspanne als 0,00 $ für Produkte mit Dateioptionen mit separaten Preisen zurückgegeben wurde.
* _LYNX-772_: GraphQL-Kompatibilität für PHP-8.4 Version
   * _Fix Hinweis_: Es wurden GraphQL-Kompatibilitätsprobleme mit PHP 8.4 auf mehreren Resolvern behoben, wodurch eine reibungslose Funktionalität sichergestellt wurde. Betroffene Dateien in den Modulen CatalogRule, Customer, GiftMessage, GiftCard und GiftWrapping wurden aktualisiert.

### GraphQL, Inventar/MSI

* _ACP2E-2607_: Die MergeCart-Mutation löst eine Ausnahme aus, wenn Quell- und Zielkarten dieselben Bundle-Elemente enthalten
   * _Notiz korrigieren_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventar/MSI, Leistung

* _ACP2E-1716_: Standort nach Upgrade nicht verfügbar
   * _Fehlerbehebung_: Die Leistung beim Abrufen von Bundle-Produkten über GraphQL wurde verbessert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Leistung

* _AC-9569_: [GraphQL Resolver] Kundenresolverdaten werden nicht für den Import ungültig gemacht
   * _Fehlerbehebung_: Der Cache des GraphQL-Kundenauflösers wird jetzt wie erwartet ungültig, wenn ein Kunde durch Importe bearbeitet oder gelöscht wird. Zuvor wurde der Cache nicht ungültig gemacht, und Kundendaten konnten während des Imports bearbeitet oder gelöscht werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Suche

* _ACP2E-_: Sortieren von GraphQL-Produktlisten nach mehreren Parametern funktioniert nicht
   * _Fehlerbehebung_: Die Produktsortierung nach mehreren Feldern in GraphQL funktioniert jetzt wie in der Dokumentation beschrieben
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_: Produktliste GraphQL-Abfrage beschränkt auf total_count 10.000 Produkte nur
   * _Fehlerbehebung_: Nach der Fehlerbehebung ist das Suchergebnis nicht auf 10000 Produkte beschränkt, es wird möglich, alle Produkte zu erhalten, die den Suchkriterien entsprechen, auch wenn die Anzahl mehr als 10000 beträgt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, Test-Framework

* _ACP2E-3363_: Fehler beim Magento\GraphQl\App\GraphQlCustomerMutationsTest.php-Integrationstest
   * _Notiz korrigieren_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Import/Export

* _AC-12172_: Problem beim Produktimport bei Bereitstellung mit benutzerdefiniertem Optionstyp: Datei (Erstelltes Produkt enthält keinen Preis für benutzerdefinierte Option und zeigt nur die erste angegebene Dateityperweiterung an)
   * _Fehlerbehebung_: Das System importiert Produktdaten jetzt korrekt mit benutzerdefinierten Optionen vom Typ „Datei“, um sicherzustellen, dass alle bereitgestellten Dateierweiterungen angezeigt werden und der Preis für die benutzerdefinierte Option enthalten ist. Wenn beim Produktimport zuvor eine benutzerdefinierte Option des Typs „Datei“ mit mehr als einer Dateierweiterung bereitgestellt wurde, wurde nur die erste Erweiterung angezeigt und der Preis für die benutzerdefinierte Option fehlte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38805>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Falsche Ausführungszeit für Importvorgang im Importverlaufsraster
   * _Fehlerbehebung_: Die Ausführungszeit des Importberichts wird korrekt unabhängig vom Admin-Gebietsschema angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Doppelte Kunden werden mit derselben E-Mail-Adresse beim Import erstellt
   * _Fehlerbehebung_: Importieren Sie den Kunden, während die Kontofreigabe auf „Global“ eingestellt ist, wird der importierte Kunde, der im System vorhanden ist, aktualisiert.
Zuvor importierter Kunde wurde dupliziert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Import von Produkten hinzufügen/aktualisieren, die anpassbare Optionen duplizieren
   * _Hinweis zur Fehlerbehebung_: Das Problem wurde behoben, indem den Produktoptionen beim CSV-Import der richtige Store zugewiesen wurde.
Zuvor dem Admin-Store anstelle des entsprechenden Stores zugewiesen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Datum „created_at“ des Kunden wurde beim Export nicht in die Speicherzeitzone konvertiert
   * _Fehlerbehebung_: Ein Datumswert der Spalte „created_at“ wird basierend auf der Zeitzone des Speichers im CSV-Abschnitt für den Kundenexport in das richtige Datumsformat konvertiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Cloud] Fehler beim Überprüfen der Daten in Importdaten mithilfe von CSV
   * _Hinweis korrigieren_: Beim Überprüfen der Daten während des CSV-Imports tritt kein Fehler auf. Zuvor war die angezeigte Fehlermeldung: „Wir können keinen Kunden finden, der diese E-Mail- und Website-Code in Zeile(n): 1 abgleicht“, wenn die Daten im Importabschnitt mithilfe von CSV von der Administratorin bzw. dem Administrator überprüft werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-_: Importschaltfläche fehlt
   * _Hinweis korrigieren_: Beheben Sie das fehlende Problem mit der Importschaltfläche, nachdem die Daten in der CSV-Datei mit richtigen und falschen Datensätzen überprüft wurden. Zuvor wird die Schaltfläche Importieren nicht angezeigt, nachdem Daten mit richtigen und falschen Datensätzen in der CSV-Datei geprüft wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Exportierte Kundenadresse kann nicht importiert werden
   * _Fehlerbehebung_: Der Import von Kundenadressen wird erwartungsgemäß fortgesetzt. Zuvor verlief die Validierung einer Kundenadressenimportdatei nicht, wenn Kundenkonten freigeben = global gilt, und es gibt zwei Websites, auf denen die Standardwebsite eine eingeschränkte Länderliste hat und die importierte Adresse für eine andere Website gilt, auf der die zulässigen Länder unterschiedlich sind
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] Falsche Menge in CSV-Datei gab keinen Fehler zurück
   * _Hinweis korrigieren_: Beim Import von Lagerbeständen wird jetzt ein Validierungsfehler für nicht numerische Werte in der Spalte „Menge“ angezeigt. Zuvor führte der Import von Lagerbeständen mit nicht numerischem Wert in der Spalte „Menge“ dazu, dass die Menge auf 0 gesetzt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: Beim Importieren eines Produkts wurde die Fehlermeldung „Duplizierter URL-Schlüssel“ generiert, wenn der URL-Schlüssel bereits zu einer Kategorie gehört.
   * _Fehlerbehebung_: Während der Prüfung auf Produktimport wird die richtige Fehlermeldung angezeigt, wenn ein Kunde versucht hat, ein Produkt zu importieren, obwohl der URL-Schlüssel des Produkts bereits zu einer Kategorie gehört.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: Produktexport verursacht OOM auch bei 4G-Speicherbegrenzung
   * _Fehlerbehebung_: Vor dieser Fehlerbehebung ist der Produktexport fehlgeschlagen, wenn Produktattribute Tausende von Optionswerten hatten, selbst mit verfügbarem 4G-Speicher. Nach dieser Fehlerbehebung sollte der Produktexport den Export der CSV-Datei abschließen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [Cloud]-Importprozesse, die sich gegenseitig beeinflussen
   * _Fehlerbehebung_: Es werden korrekte Meldungen angezeigt, wenn derselbe Admin-Benutzer zwei oder mehr Importvorgänge mit derselben Benutzersitzung durchführt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>

### Import/Export, Leistung

* _ACP2E-3476_: [Cloud] Die Importzeit für Produkte wurde erheblich verlängert
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurde beim Produktimport aus dem Katalog mit über 10.000 Einträgen eine erhebliche Zeitbeeinträchtigung festgestellt. Nach der Fehlerbehebung wird der Import des Katalogprodukts zeitnah ausgeführt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/87d012e5>

### Installieren und Verwalten

* _AC-13242_: Magento-Upgrade schlägt auf MariaDB 11.4 + 2.4.8-beta1 fehl
   * _Fehlerbehebung_: Das Upgrade sollte fehlerfrei durchgeführt werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: Keine Export-VCL für die Schaltfläche „Lack 7“ im Admin-Bedienfeld
   * _Fix Hinweis_: Die Schaltfläche „VCL für Lack 7 exportieren“ wurde dem Admin-Bedienfeld hinzugefügt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventar/MSI

* _AC-10750_: Inventaraktualisierung des konfigurierbaren Produkts schlägt fehl, wenn die Datenbank Präfixe verwendet
   * _Fehlerbehebung_: Das System aktualisiert jetzt das Inventar der konfigurierbaren Produkte korrekt, wenn die Datenbank Präfixe verwendet, um Fehlermeldungen zu verhindern und sicherzustellen, dass die richtige Menge gespeichert wird. Zuvor trat ein Fehler auf, wenn versucht wurde, die Lagermenge für einfache Produkte innerhalb eines konfigurierbaren Produkts zu speichern, wenn die Datenbank Präfixe verwendete.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: Google-Google-API-Schlüssel funktioniert nicht beim Hinzufügen von Zuordnungen mit Attributen
   * _Fehlerbehebung_: Das System unterstützt jetzt die neueste Google Maps-API-Version 3.56, sodass Benutzende erfolgreich einen Zuordnungs-Inhaltsblock aus dem PageBuilder-Menü zum Staging hinzufügen können, ohne auf Fehler zu stoßen. Zuvor konnten Benutzende aufgrund von Kompatibilitätsproblemen mit der Google Maps API-Version keinen Zuordnungs-Inhaltsblock hinzufügen, was zu einer Fehlermeldung führte, dass etwas schiefgelaufen ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: Für einen Bestellartikel mit mehreren Quellen und beschädigter SKU kann keine Lieferung erstellt werden.
   * _Fehlerbehebung_: Zuvor, als Leerzeichen versehentlich über die Datenbank zur SKU hinzugefügt wurden, führte dies zu einem Fehler auf der Sendungsseite, der jetzt behoben ist, und die automatische Kürzung wird als benutzerfreundlicher Fehler betrachtet und es wurde keine Auswirkung gefunden. Daher wurde die Sendung erfolgreich erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [Test] Bundle-Produkte mit 0 Inventar, das auf der Ladenfront angezeigt wird
   * _Fehlerbehebung_: Das Bundle-Produkt wird auf den zusätzlichen Websites, auf denen zusätzliches Lager verwendet wird, nicht angezeigt.
* _ACP2E-2794_: [Cloud] Kritisches Problem mit Produktlisten mit leeren Platzierungen
   * _Fehlerbehebung_: Das System zeigt jetzt Produktlisten korrekt ohne Leerzeichen an, wenn Produkte auf „Nicht vorrätig“ eingestellt sind, was eine konsistente und genaue Anzeige der verfügbaren Produkte gewährleistet. Zuvor führte das Festlegen eines Produkts auf „Nicht vorrätig“ dazu, dass ein leerer Bereich in der Produktliste angezeigt wurde, was das Layout störte und Kunden möglicherweise verwirrte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: Bestellung kann nicht gesendet werden, wenn MSI Pick Up Store aktiviert ist
   * _Korrekturhinweis_: Verbesserte Warenbestand Performance der Versanderstellung bei vielen Quellen mit Abholung in Geschäft
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: Cron Reindex aktualisiert die Produktverfügbarkeit im Frontend nicht
   * _Fixhinweis_: Bisher blieben Produkte im Frontend nicht vorrätig, nachdem der Nachbestellungsstatus über die REST-API aktualisiert wurde. Nach der Aktualisierung des Auftragsstatus über die REST-API werden die Produkte nun als vorrätig angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Das Hinzufügen von Bildern zu konfigurierbaren funktioniert nicht, wenn MSI aktiviert ist.
   * _Fixhinweis_: Bild Upload für konfigurierbare Produkte funktioniert nun wie erwartet, wenn Warenbestand Modul verwendet wird. Zuvor funktionierte das Upload Bild nicht
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: Problem mit dem Bundle-Produkt + MSI in Clean M2.4.7-p3
   * _Fehlerbehebung_: Zuvor kann für Inventar-Bundle-Produkte nach der Duplizierung mit demselben einfachen Produkt das einfache Produkt nicht gespeichert werden. Nachdem diese Fehlerbehebung angewendet wurde, kann das einfache Produkt ohne Ausnahmen erfolgreich gespeichert werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39358>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/0208e433>

### Inventar/MSI, Suche

* _ACP2E-3413_: Alle Produkte werden mit [is_out_of_stock] = 1 indiziert, wenn die SKU nicht als durchsuchbares Attribut festgelegt ist
   * _Fehlerbehebung_: Nach der Fehlerbehebung ist „is_out_of_stock“ im Katalogsuchindex korrekt, auch wenn die SKU nicht durchsuchbar ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/5b21b7af>

### Reihenfolge

* _AC-10828_: Übersichtsbildschirm für Backend-Aufträge: Rückstandsmenge nicht auf Bestellartikelebene sichtbar
   * _Fehlerbehebung_: Das System zeigt jetzt die Anzahl der zurückgestellten Artikel in der Spalte „Menge“ auf dem Bildschirm „Auftragsübersicht“ des Backends an. Dadurch wird sichergestellt, dass Benutzende den Status aller Artikel in einer Bestellung genau verfolgen können. Zuvor wurde in der Spalte „Menge“ nur die Anzahl der bestellten, fakturierten und versandten Artikel angezeigt, nicht jedoch die Anzahl der nachbestellten Artikel.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problem] Falsche Store-ID im Renderer für Auftragsadressen verwendet
   * _Fehlerbehebung_: Das System verwendet jetzt bei der Darstellung der Bestelladresse korrekt die mit einer Bestellung verknüpfte Store-ID, um sicherzustellen, dass Adressen entsprechend ihrer jeweiligen Store-ID korrekt formatiert sind. Zuvor verwendete das System fälschlicherweise die aktuelle Store-ID, was zu einer falschen Adressformatierung führen konnte, wenn mehrere E-Mails zu Bestellungen aus verschiedenen Stores gesendet werden mussten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: Problem mit der Zwischenspeicherung von JoinProcessor
   * _Fehlerbehebung_: Der JoinProcessor wird jetzt für jede Iteration auch bei aufeinander folgenden Aufrufen korrekt angewendet, sodass ein korrekter Datenabruf gewährleistet ist. Zuvor wurde der JoinProcessor fälschlicherweise bereits in aufeinander folgenden Iterationen als angewendet markiert, was zu Fehlern beim Datenabruf führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/27504>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Problem] Versandpreis wird in gedruckter PDF angezeigt
   * _Fehlerbehebung_: Das System zeigt jetzt die Versandpreise in gedruckten PDFs entsprechend den Steuerkonfigurationseinstellungen korrekt an, um die Konsistenz zwischen der Seite mit der Kundenauftragsrechnung und der gedruckten Rechnung sicherzustellen. Zuvor war der im gedruckten PDF angezeigte Versandpreis ohne Steuer, unabhängig von den Steuerkonfigurationseinstellungen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_: Mit einem gelöschten übergeordneten konfigurierbaren Produkt neu anordnen
   * _Fehlerbehebung_: Beim Neuanordnen mit dem gelöschten Produkt zeigt das System jetzt nicht die Schaltfläche zum Neuanordnen an
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39568>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Problem] Schlechte Eigenschaft \Magento\Sales\Model\Order\Email\Container\Template::$id korrigieren
   * _Fix Hinweis_: Dies behebt das fehlerhafte phpdoc für \Magento\Sales\Model\Order\Email\Container\Template::$id, eigentlich ist $id der Typ int, aber in Wirklichkeit ist string.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39151>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: Änderungen an der Telefonnummer in den vorhandenen Bestelldetails können nicht gespeichert werden
   * _Fix Hinweis_: Jetzt kann der Benutzer das internationale Präfix 00 in das Telefonfeld der Bestelladresse einfügen
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38201>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: E-Mails werden nicht gesendet
   * _Fehlerbehebung_: Das System verfügt jetzt über die Konfigurationsoption async_sending_attempts , mit der Anzahl von Versuchen, eine E-Mail zu senden, bevor sie gestoppt werden, was die Handhabung von fehlgeschlagenen E-Mail-Sendungen verbessert, wenn „Asynchrones Senden“ aktiviert ist. Zuvor versuchte das System, eine E-Mail nicht zu senden, und versuchte kontinuierlich, sie erneut zu senden, was zu einer endlosen Schleife von Fehlermeldungen im Systemprotokoll führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [Cloud] Bestellstatus wurde in „Abgeschlossen“ geändert, wenn eine teilweise Rückerstattung einer teilweise versendeten Bestellung erfolgt ist
   * _Fehlerbehebung_: Beim Ausstellen einer Gutschrift wird der Bestellstatus nicht mehr in „Abgeschlossen“ geändert, wenn es Artikel gibt, die noch nicht versandt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] kann das Senden von E-Mails über die Admin-Benutzeroberfläche nicht deaktivieren, wie in den Entwicklungsdokumenten angezeigt wird
   * _Fehlerbehebung_: Das System verhindert jetzt korrekt, dass Verkaufs-E-Mails gesendet werden, wenn die E-Mail-Kommunikation deaktiviert ist. Diese E-Mails werden nicht mehr gesendet, wenn die E-Mail-Kommunikation wieder aktiviert wird. Zuvor wurden Verkaufs-E-Mails, die initiiert wurden, während die E-Mail-Kommunikation deaktiviert war, weiterhin gesendet, sobald die E-Mail-Kommunikation wieder aktiviert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Bestellung abgeschlossen ohne vollständige Rückerstattung
   * _Fehlerbehebung_: Der Bestellstatus wird jetzt korrekt als „Verarbeitung“ und der Rechnungsstatus als „Ausstehend“ beibehalten, wenn eine Bestellung mit einer nicht erfassten Zahlung erstellt wurde. Dadurch wird sichergestellt, dass Bestellungen erst nach vollständiger Rückerstattung als „Geschlossen“ gekennzeichnet werden. Zuvor wurde der Bestellstatus bei der Erstellung einer Lieferung für einen Auftrag mit ausstehender Rechnung fälschlicherweise in „Geschlossen“ geändert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Cloud] Bestellung kann nicht in Admin in einem Geschäft erstellt werden, wenn nur die Standard-Rechnungsadresse nicht eingerichtet wurde
   * _Fehlerbehebung_: Jetzt relevante Fehlermeldung „Ein Kunde mit derselben E-Mail-Adresse existiert bereits auf einer zugehörigen Website.“ wird angezeigt, wenn ein Kunde keine Standard-Rechnungsadresse hat und versucht, eine Bestellung in einem anderen Shop zu erstellen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Vom Administrator duplizierte Bestellanfragen wurden gesendet
   * _Fix Hinweis_: Zuvor konnte die Schaltfläche „Bestellung übermitteln“ im Admin-Bereich mehrmals angeklickt oder durch wiederholtes Drücken der Eingabetaste aktiviert werden, was zu doppelten oder fehlerhaften Bestellübermittlungen führte. Vermeiden Sie jetzt zusätzliche Aktionen, bis die Bestellung vollständig verarbeitet ist, sodass nur eine Bestellung gesendet wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: Der Administrator kann auch ohne Zahlungsmethode Bestellungen aufgeben
   * _Hinweis korrigieren_: Die zuvor ausgewählte Zahlungsmethode wird jetzt beibehalten, wenn die Zahlungsmethode in der Liste der verfügbaren Zahlungen erneut angezeigt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Bestellung, Zahlungen

* _ACP2E-3233_: Der Administrator kann auch ohne Zahlungsmethode Bestellungen aufgeben
   * _Fehlerbehebung_: Zuvor konnte der Händler Bestellungen über das Admin-Bedienfeld aufgeben, ohne eine Zahlungsmethode auszuwählen. Jetzt wird der Händler eine Zahlungsmethode benötigt, um mit der Bestellung fortzufahren.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Reihenfolge, Rückgabe

* _ACP2E-2982_: Die Bestellerstattung führt zu einer doppelten Gutschrift
   * _Fehlerbehebung_: Wenn die Rückerstattung über die REST-API erfolgt, wenn zwei identische Anfragen gleichzeitig ausgeführt wurden, werden keine doppelten Gutschriften mehr erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestellung, Steuer

* _ACP2E-3003_: [CLOUD] Falsche base_row_total in RESTFUL order API bei der Aktivierung grenzüberschreitender Transaktionen und der Anwendung von Couponrabatten
   * _Fehlerbehebung_: Jetzt wird die korrekte base_row_total von der RESTFUL Order API zurückgegeben, wenn die grenzüberschreitende Transaktion aktiviert ist und ein Couponrabatt angewendet wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>

### Sonstige

* _LYNX-339_: private_content_version -Cookie in GQL-Abfragen zurückgegeben
   * _Hinweis beheben_: Es wurde ein Problem behoben, bei dem das Cookie „private_content_version“ in GraphQL-Abfragen zurückgegeben wurde, selbst wenn das Sitzungs-Cookie deaktiviert war. Das Cookie ist nicht mehr in den GraphQL-Antworten enthalten, wenn die Sitzung erwartungsgemäß deaktiviert wird.
* _LYNX-380_: is_available-Attribut in CartItemInterface gibt für konfigurierbare Produkte immer false zurück
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem das Attribut is_available in CartItemInterface für auf Lager konfigurierbare Produkte immer „false“ zurückgab. Jetzt spiegelt sie die Verfügbarkeit korrekt wider, sofern zutreffend.
* _LYNX-382_: is_available-Attribut in CartItemInterface gibt „true“ zurück, auch wenn der verkaufbare Bestand kleiner als die Menge des Produkts ist
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem das Attribut is_available in der CartItemInterface fälschlicherweise „true“ zurückgegeben hat, selbst wenn die Menge des Warenkorbeartikels den verkäuflichen Bestand überschritten hat.
* _LYNX-399_: Platzhalter-Miniaturansicht wird zurückgegeben, wenn ein einfaches Produkt innerhalb eines gruppierten Produkts zum Warenkorb hinzugefügt wird
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem beim Hinzufügen eines einfachen Produkts (Teil eines gruppierten Produkts) zum Warenkorb ein Platzhalter-Miniaturbild zurückgegeben wurde, selbst wenn dem Produkt ein Bild zugewiesen war.
Fehlerbehebungsdetails:
* Die Produktminiatur zeigt nun das zugewiesene Bild, sofern verfügbar, korrekt an.
* Die Auswahl der Miniaturen berücksichtigt die Admin-Konfiguration unter:
Stores > Konfiguration > Verkauf > Checkout > Warenkorb > Gruppiertes Produktbild.
Dadurch wird ein konsistentes Verhalten von Miniaturansichten für gruppierte Produkte basierend auf Store-Einstellungen sichergestellt.
* _LYNX-400_: Benutzerdefinierte Optionsattribute des Kunden funktionieren nicht mit Ganzzahlwerten
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem die benutzerdefinierten Optionsattribute des Kunden nicht funktionierten, wenn der zurückgegebene Wert eine Ganzzahl war. Benutzerdefinierte Optionen verarbeiten und geben jetzt ganzzahlige Werte korrekt wie erwartet zurück.
* _LYNX-402_: Interner Server-Fehler beim Versuch, priceDetails für Bundle-Produkte mit dynamischem Preis abzurufen
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem die Abfrage von Preisdetails für Bundle-Produkte mit dynamischer Preisgestaltung über GraphQL zu einem internen Server-Fehler führte. Diese Verbesserung gewährleistet stabile Warenkorbabfragen bei der Arbeit mit Bundle-Produkten, die mit dynamischen Preisen konfiguriert sind.
* _LYNX-403_: only_x_left_in_stock gibt für konfigurierbare Produkte immer 0 zurück
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem das Attribut only_x_left_in_stock immer 0 für konfigurierbare Produkte zurückgab, wenn es mithilfe der übergeordneten SKU mit Optionen hinzugefügt wurde.
Fehlerbehebungsdetails:
* Der Wert only_x_left_in_stock spiegelt nun genau den Bestand der ausgewählten untergeordneten Variante statt der übergeordneten SKU wider.
* Dadurch wird sichergestellt, dass die Lagerbestände für konfigurierbare Produktvarianten auf den Warenkorb- und Produktseiten korrekt angezeigt werden.
* _LYNX-411_: GraphQL-Abfrage gibt nicht den richtigen berechneten regulären Preis für anpassbare Produkte zurück
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem GraphQL für anpassbare Produkte nicht den richtigen berechneten regulären Preis zurückgab. Die Abfrage enthält jetzt korrekt den berechneten regulären Preis mit anpassbaren Werten (z. B. 125 USD) in der Preiseigenschaft, die sowohl den Grundpreis als auch etwaige zusätzliche Anpassungskosten widerspiegeln.
* _LYNX-412_: Angewendete Steuern über EstimatedTotals bleiben mit aktualisierten Mutationen erhalten
   * _Fehlerbehebung_: Es wurde ein Problem mit der Mutation EstimatedTotals behoben, bei dem angewendete Steuern auf einem Warenkorb auch nach dem Aktualisieren der Region oder Postleitzahl beibehalten wurden. Die Mutation aktualisiert nun die angewendeten Steuern korrekt, wenn zwischen Regions- und Postcodewerten gewechselt wird, um sicherzustellen, dass nur die richtige Steuerregel auf der Grundlage der aktuellen Warenkorbdaten angewendet wird.
* _LYNX-420_: is_available-Attribut in CartItemInterface gibt „true“ zurück, auch wenn das verkaufbare Lager kleiner als die Menge des Produkts ist
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem das Attribut is_available in CartItemInterface fälschlicherweise „true“ zurückgegeben wurde, selbst wenn der verkaufbare Bestand kleiner als die angeforderte Produktmenge war. Das Feld is_available gibt jetzt korrekt „false“ zurück, wenn die Produktmenge den verfügbaren Bestand überschreitet.
* _LYNX-425_: Regulärer Produktpreis mit 12 Dezimalstellen und falschem Wert
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem der Wert „Regular_Price“ in den Pfaden „product.price_range.maximum_price“ und „minimum_price“ in GraphQL nicht mit dem Katalogpreis übereinstimmte, wenn mehrere Steuersätze angewendet wurden. Der reguläre Preis spiegelt nun den Katalogpreis über alle Steuerkonfigurationen hinweg konsistent wider und gewährleistet eine genaue Einzelpreisfindung, Berechnungen der GesamtZeilenkosten und Rabattprüfungen in der Warenkorbzusammenfassung.
* _LYNX-430_: GraphQL-Serverfehler im Warenkorb mit nicht vorrätigem gebündeltem Produkt
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem GraphQL beim Abrufen eines Warenkorbs mit einem gebündelten Produkt mit einem nicht vorrätigen Element einen internen Server-Fehler zurückgab, insbesondere wenn die Abfrage die itemsV2-Eigenschaft enthielt. GraphQL gibt jetzt wie erwartet korrekt eine Liste von Elementen mit relevanten Fehlermeldungen zurück, die an den Produkteintrag im Paket angehängt sind.
* _LYNX-441_: Eine Adresse mit benutzerdefinierten Attributen kann nicht erstellt werden
   * _Fehlerbehebung_: Es wurde ein Problem mit der createCustomerAddress-Mutation behoben, das die Erstellung von Adressen mit erforderlichen benutzerdefinierten Attributen verhinderte. Die Mutation verarbeitet jetzt benutzerdefinierte Adressattribute korrekt, wenn die entsprechende Payload bereitgestellt wird.
* _LYNX-447_: GraphQL-Server-Fehler im Warenkorb mit only_x_left_in_stock im Paket-Produkt
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem das Abrufen eines Warenkorbs, der ein gebündeltes Produkt mit dem Feld only_x_left_in_stock in der GraphQL-Abfrage enthält, zu einem internen Server-Fehler führte. GraphQL gibt jetzt für das Feld only_x_left_in_stock korrekt einen Float oder null zurück, ohne Fehler zu verursachen.
* _LYNX-464_: GraphQL-Fehler beim Entfernen anderer Produkte mit unzureichendem konfigurierbarem Produkt im Warenkorb
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem der Versuch, vorrätige Produkte aus dem Warenkorb zu entfernen, zu einem GraphQL-Fehler „Die angeforderte Menge ist nicht verfügbar“ führte, wenn der Warenkorb auch konfigurierbare Produkte mit unzureichendem Vorrat enthielt. Die Entfernung funktioniert nun erwartungsgemäß, ohne dass Fehler ausgelöst werden.
* _LYNX-469_: Es können keine Produkte hinzugefügt werden, da bei der Mutation der SKU die Groß-/Kleinschreibung beachtet wird
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem die addProductsToCart-Mutation einen „PRODUCT_NOT_FOUND“-Fehler zurückgab, wenn SKUs mit unterschiedlicher Groß-/Kleinschreibung verwendet wurden. Die Mutation verarbeitet SKUs nun ohne Unterscheidung der Groß-/Kleinschreibung und stellt so die Konsistenz mit Abfragen des Katalog-Service und dem PDP-Verhalten sicher.
* _LYNX-603_: Produktattribut > Marken-Kurzform &amp;trade; wird als &amp;trade; zurückgegeben.
   * _Hinweis:_ Problem mit der Zeichenkodierung mit dem Produktnamen für die GraphQL-API behoben
* _LYNX-619_: Problem mit updateCustomerEmail-Mutation
   * _Hinweis korrigieren_: Es wurde ein Problem mit der updateCustomerEmail-Mutation behoben, bei dem Kunden ohne erforderliche benutzerdefinierte Attribute (die nach der Kontoerstellung hinzugefügt wurden) ihre E-Mail nicht aktualisieren konnten.
* _LYNX-626_: Die Mutation setShippingAddressesOnCart gibt einen Fehler aus, wenn pickup_location_code verwendet wird
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem die setShippingAddressesOnCart-Mutation einen Fehler zurückgab, wenn Pickup_Location_Code ohne Angabe von customer_address_id oder Adresse verwendet wurde. Die Mutation ermöglicht es nun, eine Versandadresse nur mit dem PICKUP_LOCATION_CODE zu setzen.
* _LYNX-637_: Storefront-Kompatibilität - Aktualisieren der Logik, um den Tabellennamen mit Präfix und anderen kleineren Verbesserungen zu erhalten
   * _Hinweis korrigieren_: Die Logik zum Abrufen des Tabellennamen mit dem Präfix (im Zusammenhang mit SCP-Änderungen) wurde aktualisiert.
* _LYNX-643_: Das Speichern im Adressbuch funktioniert nicht, wenn das Feld „same_as_shipping“ von setBillingAddressOnCart GQL verwendet wird
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem die Versandadresse nicht im Adressbuch des Kunden gespeichert wurde, wenn die GraphQL-Mutation setBillingAddressOnCart verwendet wurde, wobei das Feld same_as_shipping auf true gesetzt war. Jetzt wird die Lieferadresse korrekt wie erwartet gespeichert.
* _LYNX-650_: Standardisieren der order_id in Mutationen
   * _Fehlerbehebung_: Die Eingabe von order_id in Mutationen wurde standardisiert und die E-Mail-Vorlage für die Auftragsabbruchsbestätigung wurde aktualisiert, um die Inkrement-ID anstelle der Bestell-ID anzuzeigen.
* _LYNX-651_: CustomerOrder zeigt die Bestellkommentare nicht an
   * _Hinweis korrigieren_: Es wurde ein Problem mit CustomerOrder behoben, um Bestellkommentare in GraphQL-Abfragen für Gast- und Kundenaufträge einzuschließen.
* _LYNX-652_: original_item_price darf keinen Rabatt enthalten
   * _Fixhinweis_: Die Logik für original_item_price in den GraphQL-Warenkorbartikelpreisen wurde aktualisiert, um Rabatte auszuschließen.
* _LYNX-681_: Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem product.stock_status für Bundle-Produkte weiterhin „IN_STOCK“ anzeigte, selbst wenn eines der gebündelten Elemente nicht vorrätig war.
* _LYNX-686_: Die Kundenabfrage gibt den internen Server-Fehler zurück, wenn für einen Kunden ein Wert für das gelöschte benutzerdefinierte Attribut vorhanden ist
   * _Hinweis beheben_ Es wurde ein Problem behoben, bei dem die Kundenabfrage einen internen Server-Fehler zurückgab, wenn ein gelöschtes benutzerdefiniertes Attribut noch einen gespeicherten Wert hatte. Jetzt wird eine korrekte Fehlermeldung zurückgegeben, wenn ein nicht vorhandenes Attribut angefordert wird. Erforderlicher Cache wird beim Löschen des benutzerdefinierten Kundenattributs ungültig.
* _LYNX-687_: Aktionsparameter für Rückgabe- und Abbruchsbestätigungs-Links
   * _Hinweis korrigieren_: Aktionsparameter für E-Mail-Links zu Rückgabe und Abbruch hinzugefügt
* _LYNX-689_: Die Bestätigungs-URL des Gastbenutzers wird zur Bestellstatus-Seite weitergeleitet, da sie „orderRef“ fehlt
   * _Fehlerbehebung_: Parameter „orderRef“ zum Link in der Bestätigungs-E-Mail zur Stornierung einer Gastbestellung hinzugefügt
* _LYNX-699_: Für das nicht auf NULL festlegbare Feld „TaxItem.title“ auf placeOrder GQL kann nicht null zurückgegeben werden
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem die placeOrder-Mutation aufgrund eines Nullwerts für das Feld TaxItem.title, das keine NULL-Werte zulässt, mit einem internen Server-Fehler fehlschlug. Jetzt gibt das Feld immer einen gültigen Wert zurück, um eine erfolgreiche Auftragserteilung sicherzustellen.
* _LYNX-702_: EstimateTotals: Rabatte sind null für virtuelle Produktarten
   * _Fehlerbehebung_: Es wurde das Problem behoben, bei dem die Mutation estimatedTotals für Rabatte null zurückgab, wenn ein Rabattcode auf einen Warenkorb mit virtuellen Produkten angewendet wird.
* _LYNX-703_: Das Bundle-Produkt gibt nicht den richtigen Rabattprozentsatz und Betrag zurück
   * _Fehlerbehebung_: Für Katalogartikel wurden neue Eigenschaften „catalog_discount“ und „row_catalog_dispatcher“ eingeführt, um die korrekten Rabattbeträge und -prozentsätze sowohl auf Zeilen- als auch auf Einzelartikelebene anzuzeigen.
* _LYNX-714_: Konfiguration von Geschenknachrichten auf Produktebene
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem Geschenknachrichten nicht auf Produktebene angewendet wurden, wenn sie global deaktiviert waren. Wenn jetzt Geschenknachrichten für ein bestimmtes Produkt aktiviert sind, können sie mit der UpdateCartItems-Mutation erfolgreich hinzugefügt werden und werden korrekt gespeichert und angezeigt.
* _LYNX-757_: Die Abfrage cart.rules gibt einen Fehler anstelle eines leeren Arrays zurück, wenn keine aktiven Warenkorbregeln angewendet werden
   * _Fehlerbehebung_: Die Abfrage „cart.rules“ wurde korrigiert, sodass ein leeres Array anstelle eines Fehlers zurückgegeben wird, wenn keine aktiven Warenkorbregeln angewendet werden.
* _LYNX-778_: GraphQL-Aufrufe mit der OPTIONS-Methode geben den 500-Antwort-Code zurück, wenn das Paket „adobe-commerce/storefront-compatibility“ installiert ist
   * _Fehlerbehebung_: Es wurde ein Problem behoben, bei dem GraphQL-Aufrufe unter Verwendung der OPTIONS-Methode einen 500-internen Serverfehler zurückgaben, als das Paket „adobe-commerce/storefront-compatibility“ installiert wurde. Der Endpunkt gibt jetzt korrekt eine 200/204-Antwort wie erwartet zurück.

### Andere Entwickler-Tools

* _AC-10658_: [Problem] Behebung eines HTML-Syntaxfehlers in visual.phtml
   * _Fehlerbehebung_: Das System schließt jetzt das Start-Tag in der Datei „visual.phtml“ korrekt, um eine ordnungsgemäße HTML-Syntax sicherzustellen. Zuvor wurde das Start-Tag nicht ordnungsgemäß geschlossen, was zu einem HTML-Syntaxfehler führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38247>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problem] im Befehl „bin/magento maintenance:status“ auf „aktiviert“ geändert
   * _Fehlerbehebung_: Das System bietet jetzt genauere Statusmeldungen für den Wartungsmodusbefehl, wobei der Status von „aktiv“ in „aktiviert“ und von „nicht aktiv“ in „deaktiviert“ geändert wird. Zuvor wurde die Statusmeldung für den Wartungsmodusbefehl als „aktiv“ oder „nicht aktiv“ angezeigt, was zu Verwirrung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38486>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: Die Navigation in der Kategoriestruktur führt zu Fehlern in Redis: „Redis-Sitzung hat gleichzeitige Verbindungen überschritten“
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38851>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_: CSP-Probleme in Kombination mit dev/css/use_css_critical_path
   * _Fehlerbehebung_: Das System lädt CSS-Dateien jetzt korrekt asynchron auf Auscheckseiten, selbst wenn die Einstellung „dev/css/use_css_critical_path“ aktiviert ist, um sicherzustellen, dass diese Seiten mit den richtigen CSS-Stilen gerendert werden. Zuvor verhinderte eine eingeschränkte Content Security Policy (CSP) die Ausführung von Inline-JavaScript, was dazu führte, dass CSS-Dateien nicht wie erwartet geladen wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Bei Verwendung des virtuellen Typs zum Konfigurieren des Plug-ins kann die Interceptor-Methode in `setup:di:compile` Befehl nicht korrekt generiert werden
   * _Fehlerbehebung_: Das System generiert jetzt korrekt Abfangmethoden, wenn ein virtueller Typ zum Konfigurieren eines Plug-ins verwendet wird, um konsistente Ergebnisse sicherzustellen, unabhängig davon, ob vorkompiliert oder zur Laufzeit kompiliert. Zuvor generiert das System beim Vorkompilieren falsche Ergebnisse im Vergleich zur Laufzeitkompilierung.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3631_: Adobe Commerce 2.4.7-p3-Modultests schlagen fehl
   * _Fehlerbehebung_: Es sind keine Versionshinweise erforderlich.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Zahlungs-/Zahlungsmethoden, Bestellung

* _AC-13699_: Für die spätere Verwendung gespeicherte Kreditkartendetails für den päpstlichen Zahlungsfluss werden nicht auf der Seite der gespeicherten Zahlungsmethode angezeigt
   * _Fehlerbehebung_: Frühere Kreditkartendetails, die für die spätere Verwendung gespeichert wurden, wurden nicht auf der Seite der gespeicherten Zahlungsmethode angezeigt, die jetzt auf der Seite der gespeicherten Zahlungsmethode angezeigt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/96dec499>

### Zahlungen

* _AC-13414_: Zahlung mit Kreditkarte (Payflow-Link) funktioniert nicht
   * _Fehlerbehebung_: Früherer Fehler beim Abrufen (Zahlung wurde abgelehnt) beim Platzieren der Bestellung mit einer Kreditkarte, nachdem die Fehlerbehebung erfolgreich platziert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: Payflow erstellt jedes Mal eine neue Transaktion, wenn wir auf den Abruf-Button im Bildschirm Transaktion anzeigen klicken
   * _Fehlerbehebung_: Das System ruft jetzt Transaktionsdaten korrekt ab, ohne eine neue Zahlungsbuchung zu erstellen, sobald die Schaltfläche „Abrufen“ auf dem Bildschirm „Transaktion anzeigen“ angeklickt wird. Zuvor wurde durch Klicken auf die Schaltfläche „Abrufen“ fälschlicherweise eine neue Zahlungstransaktion für eine bereits bezahlte Bestellung erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: PayLater-Nachricht wird für kanadisches PayPal-Händlerkonto nicht in PDP angezeigt
   * _Fehlerbehebung_: Die PayLater-Nachricht für kanadische PayPal-Händlerkonten wird jetzt korrekt auf der Produktdetailseite (PDP) angezeigt, wenn das Land des Käufers anhand der Rechnungsadresse oder der Lieferung des Kontos ermittelt werden kann. Zuvor wurde die PayLater-Nachricht aufgrund eines fehlenden Parameters nicht angezeigt, was zu einem Fehler in der Browser-Konsole führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_: PayPal-Bestellrückerstattung führt zu doppelter Gutschrift
   * _Fehlerbehebung_: Parallelitätsprobleme bei IPN-erstellten Gutschriften für den PayPal-Zahlungsdienst wurden behoben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: Warenkorb-Preisregel funktioniert nicht für Paypal
   * _Fixhinweis_: Der korrekte Betrag wird auf der PayPal-Seite angezeigt, wenn der Rabatt nach Zahlungsmethode angewendet wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Cloud] Benutzer mit einer bestimmten Rolle können sich nicht anmelden
   * _Fix Hinweis_: Admin-Benutzer mit der Rolle, die nur PayPal-Abschnittszugriff enthalten, können sich jetzt fehlerfrei anmelden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>

### Leistung

* _AC-11932_: Problem mit den standardmäßigen Produktattributeinstellungen
   * _Fehlerbehebung_: Benutzende können jetzt die Auswahl einer Standardoption für ein Produktattribut aufheben, um sicherzustellen, dass für das Attribut nicht immer eine Standardeinstellung festgelegt ist. Nachdem ein Standard für ein Produktattribut festgelegt wurde, gab es bisher keine Möglichkeit, die Auswahl aufzuheben, sodass für das Attribut immer ein Standardwert festgelegt war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38703>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_: [Problem] Code-Bereinigung und Hinzufügen eines neuen kritischen Head-Blocks und Verschieben von kritischem CSS vor Assets
   * _Fehlerbehebung_: Das System enthält jetzt einen neuen kritischen Head Block und verschiebt wichtiges CSS vor Assets, was eine bessere Anpassung und Leistungsoptimierung im Frontend ermöglicht. Zuvor wurde das kritische CSS nicht vor den Assets positioniert, was die Anpassungs- und Optimierungsmöglichkeiten einschränkte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: Die Design-Kompilierung funktioniert nicht mehr, wenn der MySQL-Host Port-Informationen enthält
   * _Fehlerbehebung_: Das System verarbeitet jetzt die MySQL-Host-Konfiguration, die Port-Informationen enthält, korrekt, um eine erfolgreiche Design-Kompilierung sicherzustellen. Zuvor schlug die Design-Kompilierung fehl, wenn die MySQL-Host-Konfiguration in der Datenbankverbindung Port-Informationen enthielt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: Unterstützung für Symfonys CommandLoaderInterface in Magento CLI
   * _Korrekturhinweis_: Diese Änderung verkürzt die Initialisierungszeit der Magento-CLI-App, indem die verzögerte Initialisierung von Befehlen ermöglicht wird, bis sie benötigt werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: Leistungsproblem beim Laden von Produktattributen in Warenkorbregeln
   * _Fix Hinweis_: Verbesserte Abfrageleistung für Verkaufsregeln - von rund 150 ms auf einstellige ms.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Preis-partielle Indexierungsleistung
   * _Fix Hinweis_: Die Leistung bei der partiellen Indizierung im Preis wurde verbessert, indem einige der Löschabfragen optimiert wurden, die im Indizierungsprozess verwendet werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: Bestellung wird bei Multi-Geschäft-Setup abgelehnt, wenn Async-bestellen-Verarbeitung verwendet wird + Geschäftsbedingungen
   * _Fehlerbehebung_: Die Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden jetzt verarbeitet.
Bevor sie automatisch abgelehnt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: Die Ausführung des Aufruf der Order-Rest-API dauert sehr lange
   * _Fehlerbehebung_: Das System führt nun den Aufruf der Order Rest-API innerhalb eines angemessenen Zeitraums aus, was die Leistung beim Abrufen einer großen Anzahl von Bestellungen verbessert. Zuvor dauerte die Ausführung des Order Rest-API-Aufrufs lange, was zu Verzögerungen beim Abrufen einer großen Anzahl von Bestellungen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/001e5188>

### Preisgestaltung

* _AC-11810_: Magento2.4.6-p4 Bestellung API Einfache Artikel fehlender Preis
   * _Fehlerbehebung_: Das System zeigt jetzt den Preis einfacher Produkte korrekt an, wenn sie über die Auftrags-API abgefragt werden, um eine genaue Datendarstellung zu gewährleisten. Zuvor wurde der Preis für einfache Produkte in der API-Antwort fälschlicherweise als null angezeigt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: Penny-Rundungsfehler in Katalogregel
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/276e0acd>

### Produkt

* _AC-10535_: Sonderzeichen im konfigurierbaren zugehörigen Produktnamen werden in HTML-Entitäten konvertiert.
   * _Fehlerbehebung_: Das System behält jetzt Sonderzeichen in den Namen der zugehörigen Produkte korrekt bei, wenn es ein konfigurierbares Produkt bearbeitet, was verhindert, dass sie in HTML-Entitäten konvertiert werden. Zuvor wurden Sonderzeichen in zugehörigen Produktnamen beim Bearbeiten des konfigurierbaren Produkts in HTML-Entitäten konvertiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38146>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: Die ProductRepository-Funktion GetById erstellt nicht den richtigen Cache-Schlüssel
   * _Fehlerbehebung_: Das System erstellt jetzt korrekt einen Cache-Schlüssel in der GetById-Funktion des ProductRepositorys, unabhängig davon, ob die Speicher-ID als Zeichenfolge oder als Ganzzahl übergeben wird. Dadurch wird sichergestellt, dass das Produkt bei nachfolgenden Aufrufen aus dem Speicher abgerufen wird, was die Leistung verbessert. Zuvor konnte das System das Produkt jedes Mal aus der Datenbank abrufen, wenn die Funktion aufgerufen wurde, auch mit denselben Parametern, da ein falscher Cache-Schlüssel erstellt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38384>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [Problem] [MFTF] AdminClickAddOptionForBundleItemsActionGroup hinzugefügt
   * _Fehlerbehebung_: Das System enthält jetzt die AdminClickAddOptionForBundleItemsActionGroup, wodurch die Funktionalität des Admin-Bedienfelds erweitert wird. Zuvor war diese Aktionsgruppe nicht verfügbar.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/30857>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/30838>
* _AC-13173_: [Problem] Beheben von Tippfehlern im PHPDoc-Block
   * _Fehlerbehebung_: Das System entfernt jetzt korrekt eine unbekannte referenzierte Variable in PHPDoc für die $helper-Variablendeklaration, was die Code-Klarheit und -Genauigkeit verbessert. Zuvor verursachte diese unbekannte referenzierte Variable in PHPDoc Verwirrung und potenzielle Ungenauigkeiten im Code.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problem] Layout für fehlerhafte Bundles und herunterladbare Produktseiten in Magento >= 2.4.7 behoben
   * _Fehlerbehebung_: Das Layout für Paket- und herunterladbare Produktseiten wurde korrigiert, um eine konsistente und korrekte Anzeige auf allen Geräten sicherzustellen. Zuvor traten auf diesen Seiten Layout-Probleme aufgrund einer Neuanordnung des Produktinfo-Medienblocks auf.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - #2 ($storeId) muss vom Typ int sein, Zeichenfolge angegeben
   * _Fehlerbehebung_: Das System erstellt jetzt einen korrekten Trigger der E-Mail-Warnungen für Produkte, indem sichergestellt wird, dass die Kennung des Stores vom richtigen Datentyp ist. Zuvor wurden keine E-Mails zu Produktwarnungen gesendet, da der Typ in der Store-Kennung nicht übereinstimmt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35602>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [Cloud] addFilterToMap-Funktion funktioniert für bestimmte Spalten nicht
   * _Hinweis korrigieren_: Jetzt kann das benutzerdefinierte Modul im Bestellraster verwendet werden. Bei der Verwendung eines benutzerdefinierten Moduls sind zuvor Fehler aufgetreten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>

### Promotion

* _ACP2E-2602_: Kundenattribut beim Erstellen eines Kontos aus einer Einladung nicht sichtbar
   * _Fehlerbehebung_: Kundenattribute sind beim Erstellen eines Kontos über eine Einladung verfügbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: Couponcode mit Uses per Coupon-Limit wird nicht für Zahlung freigegeben, der mit der Stornierung der Bestellung fehlgeschlagen ist
   * _Fehlerbehebung_: Das System aktualisiert jetzt sofort die Couponnutzung, wenn eine Bestellung erstellt oder storniert wird, und fügt einer Warteschlange Regelverwendungen hinzu, um potenzielle Deadlocks zu verhindern. Dadurch wird sichergestellt, dass ein Gutscheincode mit einem Limit „Nutzungen pro Gutschein“ freigegeben wird und wiederverwendet werden kann, wenn eine Bestellung aufgrund einer fehlgeschlagenen Zahlung storniert wird. Zuvor gab das System den Couponcode nicht zur Wiederverwendung frei, was zu einer Fehlermeldung führte, die besagt, dass der Couponcode nicht gültig war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] Neuindizierung Katalogregel Produktindexer throws SQLSTATE[HY000]: Allgemeiner Fehler: Der MySQL-Server 2006 ist verschwunden.
   * _Fix Hinweis_: Das System verarbeitet jetzt den benutzerdefinierten Wert „batchCount“ in der Datei „di.xml“ für &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot; korrekt, wodurch SQL-Fehler wie „Allgemeiner Fehler: 2006 MySQL Server ist verschwunden“ während der Neuindizierung des Catalog Rule Product Indexer aufgrund der falschen Batch-Größe bei großen Katalogen verhindert werden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3139_: Verkaufsregel mit dem Attribut „Rabatt-Mengenschritt (Kauf X)“ führt dazu, dass andere Regeln nicht angewendet werden
   * _Hinweis korrigieren_: Die Warenkorb-Preisregel hebt zuvor angewendete Regeln nicht auf, wenn die Menge des Produkts im Warenkorb nicht ausreicht, um die Regel anzuwenden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_: Verkaufsregeln für Probleme mit Festbetragsrabatt und „Maximaler Mengenrabatt wird angewendet auf“
   * _Hinweis korrigieren_: Es wurde ein Problem mit dem Rabatt auf Warenkorbregeln behoben, wenn ein fester Rabatt so konfiguriert ist, dass er auf eine begrenzte Anzahl von Produkten angewendet wird, wenn der Warenkorb der Warenkorb ist. Zuvor wurde der Wert „Maximaler Mengenrabatt wird auf angewendet“ verwendet, um den Preis des aktuellen Artikels im Warenkorb zu berechnen, nicht nur für die Berechnung des Rabatts der Regel.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_: Warenkorbregeln „Fester Betragsrabatt für den gesamten Warenkorb“  Aktion wendet Rabatte falsch an
   * _Fehlerbehebung_: Gutscheincodes werden unabhängig von Groß- oder Kleinbuchstaben ordnungsgemäß validiert, wenn sie im Administratorbereich bei der Auftragserstellung verwendet werden. Zuvor wurde der Couponcode nicht validiert, wenn er nicht mit der exakten Groß-/Kleinschreibung des konfigurierten Warenkorb-Regel-Codes übereinstimmte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: Speichern Sie im Backend Standardwerte für Produktattribute (anstelle von erwarteten Administratorwerten)
   * _Fehlerbehebung_: Im Backend werden jetzt Admin-Werte anstelle der standardmäßigen Store-Werte für Produktattribute verwendet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: Die Warenkorbregeln „Fester Betragsrabatt für den gesamten Warenkorb“ wenden Rabatte beim Hinzufügen von Bundle-Produkten falsch an
   * _Fehlerbehebung_: Die Regeln für den Warenkorb mit festem Betrag wurden für Bundle-Produkte nicht ordnungsgemäß angewendet. Jetzt werden bei der Berechnung des gesamten Rabattbetrags untergeordnete Bundle-Produkte berücksichtigt, was zu einer korrekten Rabattberechnung führt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: Regeln für Warenkorbpreise berechnen Rabatt falsch
   * _Hinweis:_ werden jetzt korrekt berechnet. Vor der Fehlerbehebung wurden die Festbetragsrabatte für Bundle-Produkte nicht korrekt summiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-_: Verschachtelte Kategorien in Regelbedingungen werden nicht angezeigt
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem verschachtelte Kategorien unter der Kategorie der Ebene 3 in Marketing-Regeln für die Kategoriebedingung nicht angezeigt wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit und uses_per_customer werden nicht in der Tabelle salesrule_coupon aktualisiert
   * _Fehlerbehebung_: Die Aktualisierung der Preisregeln „Benutzer pro Coupon“ und „Benutzer pro Kunde“ im Warenkorb wirkt sich jetzt auf bestehende automatisch generierte Coupons aus. Zuvor waren von den neuen Werten nur neue Coupons betroffen
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: Die Warenkorbpreisregel berücksichtigt keine übergeordnete Kategorie, wenn sie die Bedingung „gleich oder größer als“ verwendet.
   * _Hinweis korrigieren_: Die Warenkorbpreisregeln berücksichtigen jetzt die übergeordnete Kategorie korrekt, wenn sie in erweiterten Bedingungen verwendet wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: Ungültige Rabattberechnung mit Priorität
   * _Hinweis_: Im Fall eines festen Betrags, der für den Rabatttyp des gesamten Warenkorbs angewendet wurde, wurde der Betrag für Warenkorbartikel, die bereits durch eine frühere Promotion diskontiert wurden, nicht ordnungsgemäß berechnet. Jetzt sind die Rabatte richtig zusammengefasst.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_: [CLOUD] Versandberechnung berücksichtigt nicht die Warenkorbregel
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurde eine Warenkorb-Regel mit der Bedingung „Region“ nicht konsistent angewendet. Nach der Fehlerbehebung werden Warenkorbregeln mit Regionsbedingungen ordnungsgemäß angewendet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_: Die Warenkorbregel-SKU-Bedingung schlägt für die Rechnung fehl.
   * _Fixhinweis_: Rabatt auf ein Bundle-Produkt mit dynamischem Preis wird jetzt korrekt in der Rechnung angezeigt. Zuvor wurde der Rabatt nicht in der Rechnung berücksichtigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: Falscher Rabattwert, wenn mehrere Warenkorbpreisregeln gleichzeitig mit Produkten mit Rabatten/Sonderpreisen angewendet werden
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurde der feste Betrag für Regeln für den gesamten Warenkorb nicht ordnungsgemäß angewendet, wenn mehrere Regeln angewendet wurden. Jetzt werden die Regeln für den Rabatt auf feste Beträge ordnungsgemäß angewendet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### SEO

* _AC-11907_: Das Hinzufügen von URL-Neuschreibungen mit einem Akzent verursacht unendliche Ladevorgänge
   * _Fix Hinweis_: Das System erstellt und verwendet jetzt erfolgreich URL-Neuschreibungen mit Akzenten, wodurch das unendliche Laden während des Speichervorgangs verhindert wird. Zuvor führte das Hinzufügen einer URL-Umschreibung mit einem Akzent zu einem unendlichen Ladeproblem.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38692>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: URL-Rewrite für die falsche Kategorie in Multi Store für Kategorie der dritten Ebene
   * _Fehlerbehebung_: Generieren korrekter URL-Neuschreibungen für untergeordnete Elemente mit einem übergeordneten Element mit benutzerdefiniertem URL-Schlüssel
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: Doppelbyte-Zeichen (Sonderzeichen) im Feld Produktname blockieren die Produkterstellung im Backend
   * _Fehlerbehebung_: Es wurde eine neue Einstellung hinzugefügt, mit der Sie Transliteration auf Produkt-URLs anwenden können oder nicht. Einstellung ist hier verfügbar: Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung: „Transliteration für Produkt-URL anwenden“
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_: Falsche Erstellung von url_rewrite-Einträgen mit mehreren Stores in einer Store-Gruppe
   * _Fehlerbehebung_: Vor der Fehlerbehebung konnten Sie beim Bearbeiten eines Produkts nur URL-Neuschreibungen auf Website-Ebene generieren. Mit der Fehlerbehebung wurde eine neue Einstellung eingeführt (Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung, „Produkt-URL-Neuschreibungsbereich“ mit Optionen „Store-Ansicht“, „Website„), mit der Sie URL-Neuschreibungen auf Store-Ansicht- oder Website-Ebene generieren können.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/2d627301>

### Suche

* _AC-13053_: „Suchbegriff eingeben und erneut versuchen“ wird abgerufen. Fehler auf der Seite für die erweiterte Suche in der Storefront in 2.4.8-Beta1
   * _Fehlerbehebung_: Das System zeigt jetzt die Suchergebnisse auf der Seite „Erweiterte Suche“ korrekt an, wenn ein Produktattribut auf „Nein“ gesetzt ist. Wenn Sie ein Produktattribut zuvor auf „Nein“ festgelegt und eine Suche durchgeführt haben, wird die Fehlermeldung „Geben Sie einen Suchbegriff ein und versuchen Sie es erneut.“
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search hängt von nicht vorhandener opensearch-php-Verzweigung ab
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: search_query-Tabelle bei riesiger Größe hat große Auswirkungen auf die Ladezeit Frontend
   * _Fix Hinweis_: Die Ladezeit der Suchauflistungsseite wurde verbessert. Vor der Fehlerbehebung wurde die Suchauflistungsseite aufgrund einer nicht optimierten Abfrage verzögert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/55615e61>

### Sicherheit

* _AC-11855_: [Problem] Fehlendes Font CSP Paylater Popup
   * _Fix Hinweis_: Das System erlaubt jetzt das Laden der Schriftart &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; ohne gegen die Content Security Policy Direktive zu verstoßen, um die korrekte Anzeige des Paylater Popup sicherzustellen. Zuvor wurde das Laden der Schriftart aufgrund eines Verstoßes gegen die Content Security Policy-Direktive abgelehnt, was zu Anzeigeproblemen mit dem Paylater-Popup führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [Problem] Update js.js DOM-Text neu interpretiert als HTML
   * _Hinweis_: Durch die Verwendung von innerText wird das Risiko einer HTML-Einschleusung vermieden, da diese Eigenschaften automatisch alle HTML-Sonderzeichen im bereitgestellten Text mit Escape-Zeichen versehen. Diese Fehlerbehebung hilft, Sicherheitslücken beim Cross-Site-Scripting (XSS) zu vermeiden, indem die Eingabe als reiner Text behandelt wird, anstatt als HTML interpretiert zu werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 wird beim Checkout für die deutsche Sprache falsch angezeigt
   * _Fix Hinweis_: Zuvor erscheint das reCAPTCHA von unter der E-Mail-Adresse von der Kasse für Sprachen mit langen Wörtern wie Deutsch ungestylt. Danach sieht das reCAPTCHA genauso aus wie alle reCAPTCHA-Elemente aus dem Rest der Bereiche.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Für Captcha bei der Administratoranmeldung ist für einige Benutzer keine Interaktion erforderlich
   * _Fehlerbehebung_: ReCaptcha für die Admin-Anmeldung wird erwartungsgemäß validiert
   * _GitHub-Code-Beitrag_: <https://github.com/magento/security-package/commit/8f64ab3c>

### Lieferung

* _AC-10757_: [Problem] Tippfehler in tracking.phtml behoben - JS-Funktionen in „Currier“ umbenannt in „carrier“
   * _Fehlerbehebung_: Das System verwendet jetzt in den in der Bestellverfolgungsvorlage verwendeten JavaScript-Handler-Funktionen korrekt den Begriff „Carrier“ anstelle des falsch geschriebenen „Currier“, um eine ordnungsgemäße Funktionsbenennung und Code-Klarheit zu gewährleisten. Zuvor wurde der falsch geschriebene Begriff „Currier“ verwendet, was zu Verwirrung und Inkonsistenz in der Codebasis führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST „Eine Sendung darf keine KGS/IN- oder LBS/CM- oder OZS/CM-Einheit als Maßeinheit haben“
   * _Fix Hinweis_: Stellen Sie sicher, dass die UPS-Tarife an der Kasse und im Warenkorb sichtbar sind.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38618>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-13172_: [Problem] Korrigieren der Schreibweise von Variablen für die Kundenadresse
   * _Fehlerbehebung_: Das System schreibt nun Variablen für Kundenadressen korrekt, wodurch eine genaue Anzeige im Kontobereich des Frontends gewährleistet ist. Zuvor konnte eine falsche Schreibweise dieser Variablen zu Fehlern bei der Überprüfung des lokalen Codes führen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32817>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: Tracking-Fenster zeigt das falsche erwartete Lieferdatum an
   * _Fehlerbehebung_: Zeigt das richtige Lieferdatum für Fedex Carrier an.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Tabellen-Sätze werden weiterhin angezeigt, obwohl kostenloser Versand angewendet wird
   * _Fehlerbehebung_: Die Versandmethode „Table Rate“ wird jetzt angezeigt, auch wenn nach der Anwendung des Coupons der kostenlose Versand verfügbar wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF-Test AdminCreatingShippingLabelTest schlägt fehl aufgrund von Anmeldeinformationen, die nicht in der Jenkins-Umgebung hinzugefügt wurden
   * _Fehlerbehebung_: mftf test fix
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: FedEx-Track-API funktioniert nicht mit REST-Anmeldeinformationen
   * _Fehlerbehebung_: Zuvor waren für die FedEx-Integration keine zusätzlichen API-Schlüssel für die Tracking-API erforderlich. Jetzt wurde eine neue Konfiguration hinzugefügt, um Tracking-API-Schlüssel zu unterstützen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] FedEx Ausgehandelte Tarife werden nicht auf REST zurückgegeben
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurden für das FedEx-Konto spezifische Zinssätze nicht in der Antwort gesendet, auch wenn sie laut FedEx-Dokumentation hätten gesendet werden müssen. Nach der Fehlerbehebung werden die kontospezifischen Tarife für die Antwort gesendet, indem die Anfrage von unserer Seite geändert wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/55615e61>

### Staging und Vorschau

* _ACP2E-3453_: Geplante Aktualisierung kann nicht aktualisiert werden, wenn ein eindeutiges benutzerdefiniertes Kategorieattribut verwendet wird
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem das Aktualisieren einer geplanten Aktualisierung für eine Kategorie nicht möglich war, wenn die Kategorie ein eindeutiges Attribut hatte
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>

### Targeting

* _AC-9432_: [Problem] Verwendung von CIDR-Bereichen in der Wartungs-Zulassungsliste zulassen
   * _Fehlerbehebung_: Das System unterstützt jetzt die Verwendung von CIDR-Bereichen in der Zulassungsliste für IP-Adressen im Wartungsmodus, sodass ein Bereich von IP-Adressen den Wartungsmodus umgehen kann. Zuvor erlaubte der Wartungsmodus, dass die IP-Liste nur einzelne IP-Adressen den Wartungsmodus umgeht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37943>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/30699>

### Steuer

* _AC-13295_: [Problem] Feature/php8.1 Konstruktor Eigenschaftsförderung wee Graph ql
   * _Fix Hinweis_: Ersetzen Sie fast alle Eigenschaften durch die Konstruktor-Property-Promotion im Modul wee graph ql:
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39309>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: Fest Produktsteuer (FPT) funktioniert nicht mit konfigurierbaren Produkten
   * _Korrekturhinweis_: FPT für konfigurierbare Produktvarianten funktioniert ordnungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Test-Framework

* _AC-11654_: Integrationstest schlägt fehl bei testDbSchemaUpToDate aufgrund von JSON-Spaltentyp
   * _Fehlerbehebung_: Das System erkennt jetzt bei Integrationstests JSON-Spaltentypen im Datenbankschema korrekt, um Testfehler aufgrund einer Diskrepanz zwischen dem Datenbankschema und dem deklarativen Schema zu verhindern. Zuvor hat das System JSON-Spaltentypen in MariaDB fälschlicherweise als LONGTEXT identifiziert, wodurch Integrationstests fehlschlugen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Problem] Rechtschreibkorrektur PHPDoc
   * _Fehlerbehebung_: Das System erkennt nun veraltete Methoden in IDEs aufgrund einer Rechtschreibkorrektur im PHPDoc korrekt. Zuvor führte ein Rechtschreibfehler im PHPDoc dazu, dass IDEs bestimmte Methoden nicht als veraltet erkannten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Überprüfen des Verhaltens beim beständigen Warenkorb nach Ablauf der Sitzung
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13848_: Korrigieren Sie statische Tests, um die Verwendung durch Erweiterungen von 3D-Anbietern zu ermöglichen
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [Interne] Fehler bei der Anwendung der Vorrichtung wird während der Ausführung oder in Protokollen nicht angezeigt
   * _Notiz korrigieren_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Fix Hinweis_: Feste Mftfs
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>

### UI-Framework

* _AC-12128_: Behebung der Sicherheitslücke in Prototype.js CVE-2020-27511
   * _Fehlerbehebung_: Das System wurde aktualisiert, um die Sicherheitslücke CVE-2020-27511 in Prototype.js 1.7.3 zu beheben und so die allgemeine Sicherheit des Systems zu verbessern. Vor diesem Update war das System anfällig für einen regulären Ausdrucks-Denial-of-Service (ReDOS) durch Strippen von erstellten HTML-Tags.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less verwendet pub/prefix für Quellenkarten
   * _Fehlerbehebung_: Das System generiert jetzt bei der Verwendung von grunt less/css-Quellzuordnungen ohne das /pub-Präfix für Pfade, sodass keine Problemumgehung in der Webserver-Konfiguration erforderlich ist. Zuvor war für die Verwendung des Präfixes /pub in Quellzuordnungspfaden eine bestimmte Konfiguration im Webserver erforderlich, damit es ordnungsgemäß funktioniert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38840>
* _AC-12432_: Feld für Komponentendatei der Benutzeroberfläche
   * _Fehlerbehebung_: Das System validiert jetzt das Dateifeld in einem Formular der Benutzeroberflächenkomponente korrekt, sodass das Formular ohne Fehler gesendet werden kann, wenn eine Datei ausgewählt wird. Zuvor schlug die Validierung auch dann fehl, wenn eine Datei ausgewählt wurde, was verhinderte, dass das Formular gesendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38908>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Problem] Verbessertes Datumsformat in der js-Konsole: von 12 auf 24 Stunden umschalten…
   * _Fehlerbehebung_: Verbessertes Datumsformat in der JS-Konsole: von 12 auf 24 Stunden wechseln
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38983>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problem] SourceMap-Generierung für weniger Dateien im Entwicklermodus hinzufügen
   * _Fehlerbehebung_: Im Entwicklermodus generiert das System jetzt Quellzuordnungen für weniger Dateien, wodurch die Quelle eines Stils leichter identifiziert werden kann. Zuvor war es schwierig, die Quelle eines Stils zu identifizieren, wenn das System im Entwicklermodus ohne Server-seitige Kompilierung ausgeführt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38982>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38977>
* _AC-1306_: Statischer Inhalt wird für deaktivierte Module bereitgestellt.
   * _Fehlerbehebung_: Das System schließt jetzt CSS für deaktivierte Module aus den endgültigen CSS-Ausgabedateien aus, um sicherzustellen, dass unnötige Stile nicht geladen werden. Zuvor war CSS im Zusammenhang mit deaktivierten Modulen in den endgültigen CSS-Ausgabedateien enthalten, was zum Laden zusätzlicher, unnötiger Stile führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: Inkonsistentes Verhalten bei der Sortierung „Nicht vorrätig“ mit Mindestbestand
   * _Fehlerbehebung_: Das System sortiert jetzt Produkte im Katalog korrekt anhand der Lagerbestände, hält sich dabei an den festgelegten Mindestbestandsschwellenwert und verschiebt nicht vorrätige Artikel konsequent an das Ende der Liste. Zuvor war das Sortierverhalten inkonsistent, da Elemente basierend auf ihren Lagerbeständen nicht immer in der richtigen Reihenfolge angezeigt wurden und Änderungen bei der Sortierung nach dem Speichern, Aktualisieren oder Ändern der Kategoriehierarchie unvorhersehbar auftreten konnten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Vorschlag für eine verbesserte Fehlerberichterstattung für Require.js-Ladeprobleme
   * _Hinweis zur Fehlerbehebung_: Diese PR verbessert die Fehlermeldung, wenn Require eine Komponente nicht laden kann.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: PHP 8.4-Veraltungsfehler, die Build-Fehler in 2.4-develop verursachen
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Problem] Laden Sie den Backend-Blockkontext nicht in Frontend
   * _Fix Hinweis_: Das System stellt jetzt sicher, dass der Backend-Block-Kontext nicht im Frontend geladen wird, was die Erstellung unnötiger Backend-Sitzungen und potenzieller Sitzungssperren verhindert. Zuvor hat das System fälschlicherweise den Backend-Blockkontext im Frontend geladen, was zur Erstellung von Backend-Sitzungen und potenziellen Sitzungssperren geführt hat.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37617>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [Problem] Entfernen unnötiger Skripte - Zusammenfassung der Überprüfung
   * _Fehlerbehebung_: Das System optimiert jetzt die Seitenladezeit, indem unnötige JavaScript-Skripte aus dem Bewertungsabschnitt entfernt werden, anstatt Inline-CSS-Stile für einen effizienteren und besser lesbaren Code zu verwenden. Zuvor konnte die Verwendung von JavaScript-Skripten für den Bewertungsabschnitt die Seitenladezeit möglicherweise verlangsamen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37776>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: Ausnahme beim Überprüfen eines Geschenkgutscheinsaldos, wenn reCAPTCHA aktiviert ist
   * _Hinweis korrigieren_: Benutzer können auf dem Bildschirm „Warenkorb anzeigen“ und „Warenkorb bearbeiten“ den Guthaben der Geschenkkarte abrufen. Zuvor wurden diese Details nicht angezeigt, während reCAPTCHA aktiviert war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [Klärung] Funktionsanfrage ADA-Konformität
   * _Fehlerbehebung_: Das System stellt jetzt die ADA-Konformität sicher, indem es nicht unterstützte CSS-Eigenschaften entfernt und sie durch unterstützte Eigenschaften in der Datei „print.css“ ersetzt. Zuvor führte die Verwendung nicht unterstützter CSS-Eigenschaften zu Problemen mit der Browser-Kompatibilität.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Konfusionsbibliothekscode in effect-drop.js von AC 2.4.4-p8
   * _Fehlerbehebung_: Das System implementiert jetzt die Bibliothek „effect-drop.js“ korrekt, um die ordnungsgemäße Funktion der jQuery-UI-Effekte sicherzustellen. Zuvor wurde die Bibliothek „effect-drop.js“ versehentlich mit der Bibliothek „effect-clip.js“ überschrieben, was zu Problemen mit jQuery-UI-Effekten führen konnte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: Site-Kopfzeile | Sonderzeichen im Abschnitt „Kundenempfehlung“
   * _Fehlerbehebung_: Nach der Fehlerbehebung werden Sonderzeichen im Begrüßungsabschnitt des Kunden korrekt angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: Die Segmentbearbeitung des Kunden schlägt mit daterange fehl
   * _Hinweis korrigieren_: Es ist möglich, ein Kundensegment mit einer Bedingung für den Datumsbereich zu speichern, wenn nur eines der Datumsangaben bearbeitet wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a52ff98f>
