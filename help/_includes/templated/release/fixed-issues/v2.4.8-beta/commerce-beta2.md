---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Behobene Probleme in Adobe Commerce (v2.4.8-beta2)

## Behobene Probleme in v2.4.8-beta2

Es wurden 206 Probleme im Kern-Code von Adobe Commerce 2.4.8 behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

* _ACP2E-3236_: Asynchroner Vorgang schlägt fehl, wenn die SKU in der Payload fehlt
   * _Hinweis_: Asynchrone und Synchronisierungsvorgänge sind zuvor aufgrund von Fehlern bei der Produktspeicherung fehlgeschlagen, wenn die SKU in der Payload fehlt. Nach der Behebung schlagen die Vorgänge der asynchronen und synchronisierten Produkt-REST-API mit der entsprechenden Ausnahmemeldung fehl.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Die Basispreise können nicht mit der REST-API aktualisiert werden (der Wert von „value_id“ in „catalog_product_entity_decimal“ wird nicht korrekt inkrementiert.)
   * _Fehlerbehebung_: Vor dieser Fehlerbehebung wurde beim Aufruf der rest-API /rest/default/V1/products/base-prices die Inkrement-ID fälschlicherweise erhöht, sodass eine Lücke zwischen den Werten entstand. Nach der Fehlerbehebung wird die Inkrement-ID wie erwartet inkrementell erhöht. Außerdem wurde der Wertebereich des Feldes vergrößert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_: Standardwerte werden für Datums- und Uhrzeitattribute mit der Produkt-Rest-API nicht festgelegt
   * _Hinweis korrigieren_: Die Standardwerte werden jetzt für Datums- und Datums- sowie Uhrzeitattribute über die Rest-API korrekt festgelegt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### APIs, Warenkorb und Checkout

* _ACP2E-3343_: Kritischer 500-Fehler: Magento\Framework\Webapi\Exception im Zusammenhang mit dem Accept-HTTP-Header
   * _Fehlerbehebung_: Nach der Fehlerbehebung gibt es kein Problem mehr mit der Angabe der „Accept“-Kopfzeile.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>

### APIs, GraphQL

* _ACP2E-3348_: Für das Abonnieren von Reward Points-Aktualisierungen für Kunden ist keine GraphQL verfügbar
   * _Fehlerbehebung_: Vor der Fehlerbehebung konnte das Kundenattribut reward_warning_notification nicht über den Aufruf der GraphQL-Mutation und der REST-API aktualisiert werden. Jetzt kann auf die gleiche Weise aktualisiert werden wie das Kundenattribut reward_update_notification.

### Konto

* _AC-10886_: Aktualisierung des Administratorkennworts.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: Umleitungsschleife bei URLs in Großbuchstaben
   * _Fix Hinweis_: Das System wandelt nun Großbuchstaben in URLs automatisch in Kleinbuchstaben um, wodurch eine Umleitungsschleife beim Zugriff auf die Homepage verhindert wird. Zuvor führte die Verwendung von Großbuchstaben in der Secure Base-URL beim Zugriff auf die Homepage zu einer kontinuierlichen Umleitungsschleife.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: Kontrollkästchen „Als Kunden-Opt-in anmelden“ nicht übersetzbar
   * _Fehlerbehebung_: Das System ermöglicht es jetzt, die Felder „Als Kunden-Opt-in anmelden“ und „Als Kunden-Checkbox-QuickInfo anmelden“ im Bereich „Store-Ansicht“ festzulegen, wodurch Übersetzungen für verschiedene Store-Ansichten ermöglicht werden. Zuvor wurden diese Felder nur im Umfang der „Website“ festgelegt, wodurch Übersetzungen für einzelne Store-Ansichten verhindert wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: Nach der Anmeldung sind die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.
   * _Fehlerbehebung_: Produkte, die vor der Anmeldung als Kunde zur Produktvergleichsliste hinzugefügt wurden, bleiben jetzt nach der Anmeldung erhalten.
Zuvor waren nach der Anmeldung die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Die Konfiguration von Ländern zulassen verursacht Probleme in den Konfigurationen von Kundenadressen
   * _Fehlerbehebung_: Die Auswahl der Konfiguration „Länder zulassen“ wirkt sich jetzt nicht auf Länder aus, die außerhalb des angegebenen Bereichs angezeigt werden. Zuvor durch die Konfiguration „Länder zulassen“ beeinflusste Kundenadressattribute außerhalb des angegebenen Bereichs.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: Die Shared Gift Registry zeigt das Ereignisdatum einen Tag früher an
   * _Fix Hinweis_: Das Datum der Geschenkregistrierung wird jetzt auf der Storefront korrekt angezeigt

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
* _AC-13131_: [Problem] Fehlerbehebung Warnung: Nicht definierter Array-Schlüssel „filter“
   * _Fehlerbehebung_: Das System verarbeitet jetzt Szenarien, in denen ein neuer Benutzer noch nicht mit Lesezeichen interagiert hat, sodass keine Warnung bezüglich eines nicht definierten Array-Schlüssels „Filter“ protokolliert wird. Zuvor wurde diese Warnung protokolliert, wenn ein neuer Benutzer nicht mit Lesezeichen interagiert hatte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: Die CSV-Datei des Produktimports mit Sonderzeichen schlägt aufgrund von Code-Änderungen in der Datei Validate.php fehl
   * _Fehlerbehebung_: Das System validiert und importiert jetzt Produkt-CSV-Dateien, die Sonderzeichen enthalten, korrekt, was eine erfolgreiche Datenübertragung ermöglicht. Zuvor führte der Versuch, eine Produkt-CSV-Datei mit Sonderzeichen zu importieren, zu einem Fehler, der den Importvorgang verhinderte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: Wenn die maximale Anzahl von Anfragen zum Zurücksetzen des Passworts größer als 0 festgelegt ist, z. B.: 3 , werden Fehlermeldungen zum „Überschreiten des Grenzwerts“ gesendet, bevor das Limit erreicht wird, d. h. ab dem zweiten Mal
* _AC-13768_: Obwohl die maximale Anzahl von Anfragen zum Zurücksetzen des Kennworts“ auf 0 ( deaktiviert) festgelegt ist, werden „Fehlermeldungen zum Überschreiten des Grenzwerts ab dem 2. Mal gesendet“
* _AC-7962_: Kein Link zum Versand bei Zahlungen an der Kasse in der Mobiltelefonansicht
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Checkout-Titel/Links „Versand“ und „Überprüfung und Zahlungen“ in der mobilen Ansicht immer oben auf der Seite sichtbar sind, sodass Benutzende einfach zwischen Schritten navigieren und notwendige Korrekturen vornehmen können. Zuvor waren diese Titel/Links in der mobilen Ansicht ausgeblendet, sodass es für Benutzende schwierig ist, ihren aktuellen Schritt zu kennen oder zu vorherigen Schritten zurückzukehren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: Die Abfrage von Versandkommentaren für Kundenbestellungen CREATED_AT wird in +0 Zeitzone zurückgegeben, die sich nicht in der konfigurierten Zeitzone des Geschäfts befindet
   * _Fehlerbehebung_: Das System zeigt jetzt korrekt das Feld „created_at“ aus Versandkommentaren in der konfigurierten Zeitzone des Kunden an, wenn die Abfrage „Kundenaufträge“ verwendet wird. Zuvor wurde das Feld „created_at“ in der Zeitzone +0 angezeigt, unabhängig von der konfigurierten Zeitzone des Kunden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: Der Status der Versandadresse wird nicht automatisch aktualisiert
   * _Fehlerbehebung_: Vor der Fehlerbehebung war die Region (oder Regions-ID) der Versandadresse nicht mit den Rechnungsinformationen der Adresse synchronisiert. Jetzt werden sowohl die Versandadressenregion als auch die Regions-ID ordnungsgemäß aktualisiert, wenn die Informationen zur Rechnungsadresse geändert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: Zurücksetzen-Schaltfläche funktioniert nicht bei Admin-Benutzer hinzufügen/bearbeiten
   * _Hinweis korrigieren_: Zuvor funktionierte die Schaltfläche „Zurücksetzen“ auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“ nicht. Jetzt funktioniert die Schaltfläche „Zurücksetzen“ im Admin-Bedienfeld unter „System“ > „Berechtigungen“ > „Alle Benutzer“ auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“ ordnungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_: Beschädigte Validierung für „Maximal zulässige Menge im Warenkorb“
   * _Fehlerbehebung_: Wenn wir `Maximum Qty Allowed in Shopping Cart` leer gelassen haben, hat es zuvor keine Ausnahme ausgelöst, obwohl hier kein leerer Wert akzeptiert wird. Wenn diese Fehlerbehebung angewendet wird, werden beim Einfügen einer leeren Zeichenfolge Ausnahmen ausgelöst, sodass das Produkt nicht gespeichert werden kann.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problem mit der PageBuilder-Vorschau] Die Schaltflächen in der Page Builder-Spalte werden nicht korrekt ausgerichtet
   * _Hinweis korrigieren_: Die Schaltflächen in den Spalten des Seiten-Builders sind jetzt korrekt ausgerichtet. Zuvor waren sie in den Page Builder-Spalten falsch ausgerichtet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: Bericht „Bestellte Produkte“ wird nicht exportiert. 404-Fehler.
   * _Fehlerbehebung_: Der Export von sortierten Produkten in CSV und XML funktioniert jetzt erwartungsgemäß
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: TinyMCE JS-Fehler in der Konsole nach JS-Minimierung aktivieren mit Produktionsmodus
   * _Fehlerbehebung_: Zuvor wurden durch die Aktivierung der JavaScript-Minimierung im Produktionsmodus im Admin-Bedienfeld JavaScript-Fehler im Zusammenhang mit TinyMCE 7 in der Browser-Konsole angezeigt, was sich auf die Funktionalität und das Benutzererlebnis auswirkte. Dieses Problem wurde nun behoben, sodass TinyMCE 7 reibungslos funktioniert und keine Fehler erzeugt werden, auch wenn die JS-Minimierung aktiviert ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Antrag auf zusätzliche Änderungen, um die Fehlerbehebung ACP2E-3375 vollständig abzuschließen
   * _Notiz korrigieren_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Admin-Benutzeroberfläche, Zahlungs-/Zahlungsmethoden, Bestellung

* _AC-13520_: Transaktionsautorisierung wird nach der Bestellung des PayPal-Smart-Buttons nicht auf der Registerkarte Transaktion angezeigt
   * _Fix Hinweis_: Das System zeigt nun die Transaktionsautorisierung auf der Registerkarte Transaktion korrekt an, nachdem eine Bestellung mit dem PayPal Smart Button aufgegeben wurde. Zuvor wurde die Autorisierungstransaktion nicht auf der Registerkarte Transaktion angezeigt, nachdem auf die Schaltfläche „Autorisieren“ geklickt wurde, und es wurde keine neue Transaktion vom Typ „Autorisierung“ erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Admin-Benutzeroberfläche, Staging und Vorschau

* _ACP2E-3424_: [Cloud] Wenn Sie eine Vorlage mit fehlenden Bildern entfernen, wird Pub/Media gelöscht
   * _Fehlerbehebung_: Zuvor wurde der Ordner „pub/media“ gelöscht, wenn der Vorschaubildname für eine PageBuilder-Vorlage fehlte. Nach der Korrektur wird nur die Vorlage gelöscht und das Vorschaubild gefunden, falls vorhanden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/Reporting

* _AC-9922_: Google Analytics CSP-Fehler https://region1.analytics.google.com
   * _Hinweis beheben_: Das System lässt jetzt bei aktiviertem Google Analytics korrekt Verbindungen zu &quot;https://region1.analytics.google.com&#39;&quot; zu, wodurch CSP-Fehler (Content Security Policy) vermieden werden. Zuvor führte die Aktivierung von Google Analytics und die Anzeige der Website aus der EU zu CSP-Konsolenfehlern aufgrund einer Weigerung, eine Verbindung zu &quot;https://region1.analytics.google.com&#39;&quot; herzustellen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3146_: Bei GTM fehlt das addToCart-Ereignis in dataLayer für ein konfigurierbares Produkt mit benutzerdefinierter Option
   * _Fehlerbehebung_: Zuvor wurde das Ereignis „addToCart“ für konfigurierbare Produkte nicht ausgelöst. Jetzt wird das Ereignis ordnungsgemäß zur Datenschichtvariablen GTM hinzugefügt.
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

### Analytics/Reporting, Cloud

* _ACP2E-3187_: Metrik in NR kann für Hintergrundtransaktionen irreführend sein - Follow-up von ACP2E-3067
   * _Fehlerbehebung_: Background Transactions (cron) will use New Relic app name defined in the config settings
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: 2.4.8-beta102-Paket Enterprise Edition schlägt mit Anwendungsausnahmen fehl
* _AC-13816_: B2B-Funktion kann nicht erstmals in Backend Admin aktiviert werden
* _ACP2E-2139_: Produkte, die einem freigegebenen Katalog zugewiesen sind, werden beim Ausführen eines partiellen Index nicht am Frontend angezeigt
   * _Fehlerbehebung_: Produkte, die über die REST-API einem freigegebenen Katalog zugewiesen wurden, sind jetzt nach Abschluss der partiellen Indizierung sofort in der Storefront sichtbar. Zuvor waren Produkte nur nach einer vollständigen Neuindizierung sichtbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quotes cron löscht Angebote von bis zu noch genehmigten Bestellungen
   * _Fix Hinweis_: Angebote, die jetzt in Bestellungen verwendet werden, werden von sales_clean_quotes Cron-Auftrag nicht gelöscht
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: Schaltfläche „Bestellung aufgeben“ verschwindet in den Bestelldetails
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem die Schaltfläche „Bestellung aufgeben“ für genehmigte Bestellungen ausgeblendet war, wenn für eine Produktvariante eine Mindestzahl in der Karte angegeben war
* _ACP2E-3474_: [CLOUD] Keine solche Entität mit ID = 0 mit B2B-Modul
   * _Fehlerbehebung_: Angemeldeter Benutzer kann Produkt zum Warenkorb hinzufügen, wenn die Funktionen des freigegebenen Katalogs aktiviert sind.
Zuvor führte das Hinzufügen des Produkts zum Warenkorb zu dem Fehler „Keine solche Entität mit ID = 0“

### B2B, Warenkorb und Checkout

* _AC-13817_: Produkte werden nicht im Warenkorb angezeigt, wenn b2b-Funktionen aktiviert sind.

### B2B, GraphQL

* _ACP2E-3391_: [Cloud] Benutzerdefinierte Attribute können bei der Unternehmenserstellung über den GraphQL-Aufruf nicht festgelegt werden
   * _Fehlerbehebung_: Nach der Fehlerbehebung ist es möglich, das Attribut „custom_attributes“ für den Unternehmensadministrator bei der Erstellung des Unternehmens mithilfe einer GraphQL-Anfrage festzulegen.

### Bündel

* _AC-10826_: Fehlermeldung bei der Validierung des Storefront-Bundles größer als 1
   * _Fehlerbehebung_: Das System zeigt jetzt nur noch eine Validierungsfehlermeldung an, wenn die Schaltfläche „Zum Warenkorb hinzufügen“ angeklickt wird, ohne Kontrollkästchen-Optionen für ein gebündeltes Produkt auszuwählen. Zuvor zeigte das System mehrere Validierungsfehlermeldungen für jedes nicht ausgewählte Kontrollkästchen an.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: Magento-Ausnahme in einigen Testfällen mit Bezug zur Reihenfolge ausgelöst
   * _Fehlerbehebung_: Das System verarbeitet jetzt den Schritt „sendGuestPaymentInformation“ in verschiedenen Testfällen korrekt, wodurch das Auslösen von Magento-Ausnahmen verhindert wird. Zuvor traten diese Ausnahmen aufgrund einer Null-Zahlungsmethode auf, was in mehreren Testfällen zu Fehlern führte.

### Warenkorb und Checkout

* _AC-11914_: [Problem] Verkaufsregel WarenkorbFeste Berechnung : Falscher Rabattbetrag
   * _Fixhinweis_: Das System berechnet jetzt den Rabattbetrag für Verkaufsregeln mit festen Warenkorbbeträgen korrekt und stellt sicher, dass genaue Rabatte unabhängig von Änderungen an den Warenkorbartikeln angewendet werden. Zuvor konnte der Rabattbetrag falsch variieren, wenn Artikel im Warenkorb geändert wurden, was manchmal zu erheblich größeren Rabatten als erwartet führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38694>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
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
* _AC-13797_: Der Link zur Geschenkregistrierung funktioniert nicht ordnungsgemäß
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
* _ACP2E-3405_: [CLOUD] Checkout behält die ausgewählte Rechnungsadresse nicht bei, wenn die Adresssuche aktiviert ist
   * _Fehlerbehebung_: Die Zahlungsseite für die Kasse behält jetzt die ausgewählte Rechnungsadresse bei, wenn die Adresssuche aktiviert ist. Wenn zuvor „Limit für Kundenadressen“ auf 1 konfiguriert wurde und der Kunde über mehr als eine Adresse verfügt, verschwindet die ausgewählte Rechnungsadresse nach dem Neuladen der Seite.
* _ACP2E-3407_: Geschenkkarte Produkt | Beim Zusammenführen des Warenkorbs werden Geschenkkarten zusammengeführt
   * _Fehlerbehebung_: Geschenkkartenprodukte werden jetzt korrekt im Warenkorb zusammengeführt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_: Vorhandene Anführungsdaten werden nicht aktualisiert/nicht angezeigt. Erstellen Sie stattdessen einen neuen Anführungsdatensatz, wenn Trigger_recollect = 1 ist.
   * _Fehlerbehebung_: Die Artikel im Warenkorb des Kunden verschwinden nicht mehr, da ein Produkt gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Katalog

* _AC-11970_: Konfigurierbare Produkte können nicht mit einer benutzerdefinierten Option neu angeordnet werden
   * _Fehlerbehebung_: Das System verarbeitet jetzt die Neuanordnung von konfigurierbaren Produkten mit einer einzigen benutzerdefinierten Checkbox-Option korrekt, was eine erfolgreiche Warenkorberstellung ermöglicht. Zuvor führte der Versuch, solche Produkte neu zu bestellen, zu einem Fehler und verhinderte, dass Artikel zum Warenkorb hinzugefügt wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1d144bce>
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
* _AC-13786_: Weißer Rahmen wird nach der Deaktivierung von product_image_white_border für benutzerdefiniertes Design nicht entfernt
* _ACP2E-3103_: RSS-Feed für neue Produkte wird aufgrund des Caches nicht mit neuen Produkten aktualisiert
   * _Hinweis:_ RSS-Feed für neue Produkte wird jetzt aktualisiert, wenn ein Produkt als neu festgelegt und gespeichert wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [Cloud] Zoom- und Bewegungsproblem mit zwei Fingern auf dem echten Mobilgerät
   * _Fehlerbehebung_: Das System stellt nun auf Mobilgeräten eine konsistente Bildzoom-Funktion sicher und sorgt so für ein reibungsloses und vorhersehbares Benutzererlebnis. Zuvor war die Bildzoom-Funktion inkonsistent und zoomte bei der Ansicht auf einem Mobilgerät nach einem bestimmten Punkt plötzlich heraus.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: Wenn wir die Zuweisung von Produkten zum freigegebenen Katalog aufheben, werden die Produkte auf der Wunschliste nicht gelöscht
   * _Hinweis korrigieren_: Wenn ein Produkt nicht im freigegebenen Katalog verfügbar ist, werden jetzt keine Artikel auf der Wunschliste angezeigt. Zuvor wurde auf der Seite mit der Wunschliste fälschlicherweise die Anzahl „1 Artikel“ angezeigt, auch wenn keine Artikel in der Wunschliste verfügbar waren.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Verwandte Produkte Alle auswählen/Alle auswählen Problem aufheben
   * _Hinweis korrigieren_: Zuvor funktionierten die Schaltflächen „Alle auswählen“/„Alle Auswahl aufheben“ für zugehörige Produkte nicht ordnungsgemäß, wenn ein Produkt manuell ausgewählt wurde. Nach der Fehlerbehebung funktionieren diese Schaltflächen nun auch nach der manuellen Auswahl konsistent und stellen sicher, dass alle Produkte richtig ausgewählt oder deaktiviert sind.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] Übersetzen von Warnhinweis-E-Mails in die falsche Sprache
   * _Fehlerbehebung_: Beim Versand von Stock-/Preis-Warnhinweisen für eine Website mit mehreren Store-Ansichten in verschiedenen Sprachen wird die Sprache für die Store-Ansicht, in der der Warnhinweis erstellt wurde, in der E-Mail verwendet.
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
* _ACP2E-_: Indexer Temporäre Tabellen werden nicht bereinigt, wenn der Prozess beendet wird
   * _Fehlerbehebung_: Die temporären Tabellen des CatalogRule-Indexers werden jetzt bereinigt, wenn der Indexerprozess beendet wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] Fehler bei Modultests in 2.4.7-p3
   * _Fehlerbehebung_: Versionshinweise für diesen Test sind nicht erforderlich, da es sich um eine Verbesserung des Komponententests handelt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

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

### Catalog, GraphQL

* _ACP2E-3312_: Stufenpreise geben in Produkten von GraphQL einen falschen Wert zurück (im Vergleich zu Storefront)
   * _Fehlerbehebung_: Nach der Fehlerbehebung haben die für GraphQL-Anfragen zurückgegebenen Stufenpreise des Produkts den Preis pro einem Element.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [CLOUD] B2B: Kategorieproblem über GraphQL
   * _Fehlerbehebung_: Nach der Fehlerbehebung gibt die GraphQL-Abfrage für Kategorien Kategorien mit der Berechtigung „Zulassen“ zurück, auch wenn die Stammkategorie nicht über die Berechtigung „Zulassen“ verfügt.

### Katalog, Suche

* _ACP2E-3345_: Beim Erstellen des Objekts ist ein Typfehler aufgetreten: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Ausnahme
   * _Fehlerbehebung_: Nach der Fehlerbehebung kann eine Instanz der Klasse Magento\CatalogSearch\Model\Indexer\Fulltext erstellt werden, ohne $data anzugeben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [CLOUD] Problem mit Produkten wird nach dem Speichern in Magento Admin nicht in Frontend angezeigt
   * _Fehlerbehebung_: Nach der Fehlerbehebung werden konfigurierbare Produkte, die untergeordnete Produkte mit langen Namen enthalten, nicht in der Storefront verpasst.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Katalog, Versand

* _ACP2E-3195_: Lieferadresse leer bei Bestellung eines Geschenkartikels
   * _Fehlerbehebung_: Zuvor wurde für Geschenk-Registrierungselemente von Gastbenutzern bei der Rückgabe von der E-Mail-Funktion eine leere leere leere Adresse generiert, die für die Bestellung falsch ist. Nachdem dieser Fix angewendet wurde, prüft die Geschenkregistrierung angemeldete Benutzer/Gastbenutzer und zugewiesene Adressen, ob sie vorhanden sind.

### Inhalt

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
* _ACP2E-3122_: Schaltfläche [CLOUD] Bild hochladen funktioniert nicht
   * _Fehlerbehebung_: Vor der Schaltfläche Bild hochladen für Banner und Regler von PageBuilder funktionierte es nicht wie erwartet. Wenn Sie jetzt darauf klicken, wird der lokale Datei-Manager geöffnet, um das gewünschte Bild zum Hochladen auszuwählen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Cloud] - CMS-Regler spiegelt nicht die neuesten Änderungen wider
   * _Hinweis:_ Problem wurde behoben, indem sichergestellt wurde, dass die Reglerliste aktualisiert wird, während das Speicherereignis auf dem Bildschirm „Folie bearbeiten“ ausgelöst wird. Zuvor wurde das Problem ausgelöst und verursacht.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Auf der CSM-Seite tritt ein Fehler auf, wenn CMS-Blöcke mit dem Seiten-Builder in einer bestimmten Reihenfolge eingefügt werden
   * _Fix Hinweis_: Zuvor war bei einigen Versionen von PHP und OS (Linux) das Rendern von Blöcken, die über PageBuilder auf andere CMS-Blöcke verwiesen hatten, mit dem Fehler „Ein unbekannter Fehler ist aufgetreten. Bitte erneut versuchen.“ Jetzt wird der Inhalt der CMS-Blöcke innerhalb eines von PageBuilder gesteuerten Inhalts korrekt wiedergegeben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [Cloud] Dynamische Blöcke funktionieren nicht ordnungsgemäß
   * _Fehlerbehebung_: Angemeldete Kundensegmente werden jetzt nach dem Abmelden gelöscht, was verhindert, dass die Gastsitzung zuvor angemeldete Segmente erbt
* _ACP2E-3430_: Neueste Sicherheitsaktualisierungen mit TinyMCE 7 fehlender Schriftgröße
   * _Hinweis korrigieren_: Die Auswahl der Schriftgröße und der Schriftfamilie ist jetzt im WYSIWYG-Editor verfügbar. Vor dieser Fehlerbehebung waren diese bei TinyMCE 7 nicht in der Editor-Oberfläche verfügbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Kunde/Kunden

* _AC-13060_: Kundensegment > Bedingung > Produktverlauf* > „Produkt wurde angezeigt“ funktioniert nicht
   * _Fehlerbehebung_: Das System zeigt jetzt korrekt übereinstimmende registrierte Kunden in der Bedingung „Produkt wurde angezeigt“ unter „Kundensegmente“ an, wenn die Bedingung erfüllt ist. Zuvor blieb die Anzahl der übereinstimmenden registrierten Kunden auch dann bei null, wenn die Bedingung erfüllt war.
* _AC-8499_: Das Textfeld „Region“ wird nicht zurückgesetzt, wenn das Dropdown-Menü „Land“ geändert wird
   * _Fehlerbehebung_: Das Textfeld Region wird jetzt zurückgesetzt, wenn das Land im Dropdown-Menü geändert wird. Dadurch wird sichergestellt, dass die vorherigen Werte nicht beibehalten werden. Beim Ändern des Landes aus der Dropdown-Liste wurde das Feld Region zuvor nicht zurückgesetzt, sodass der zuletzt gespeicherte Wert beibehalten wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: Beim Löschen eines Kunden werden nicht alle Browser-Sitzungsdaten in der Storefront für angemeldete und gelöschte Kunden gelöscht
   * _Fehlerbehebung_: Durch das Löschen eines Kunden werden nun alle Browser-Sitzungsdaten aus der Storefront für angemeldete und gelöschte Kunden wie erwartet gelöscht. Der Käufer kann weiterhin einkaufen, und sein Browser behandelt seine Sitzung als Gastsitzung. Wenn das Kundenkonto eines angemeldeten Käufers aus dem Admin gelöscht wurde, gab es zuvor im Browser des Käufers JavaScript-Fehler.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7d5e3906>

### Framework

* _AC-10738_: Die Lackkonfiguration schließt nicht alle Marketing-Parameter aus
   * _Fehlerbehebung_: Das System schließt jetzt alle gängigen Marketing-Parameter in der Lackkonfiguration korrekt aus, um ein genaues Tracking und Analysen zu gewährleisten. Zuvor wurden bestimmte Marketing-Parameter wie „gad_source“, „srsltid“ und „msclpid“ nicht ausgeschlossen, was zu möglichen Ungenauigkeiten bei der Datenerfassung führen kann.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [Problem] Nur gültige Voreinstellungen beim Setup zulassen:di:kompilieren
   * _Fehlerbehebung_: Das System gibt jetzt während des Befehls setup:di:compile einen Fehler aus, wenn eine Voreinstellung für eine Klasse erstellt wird, die nicht vorhanden ist oder ausdrücklich ausgeschlossen wird, sodass nur gültige Voreinstellungen zulässig sind. Zuvor schlugen diese Szenarien im Hintergrund fehl und machten möglicherweise alle Plug-ins, die mit den ursprünglichen Klassen verknüpft sind, unbrauchbar.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [Problem] Übergeben Sie benutzerdefinierte Attribute über XML an den aktuellen Link.
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Übergabe benutzerdefinierter Attribute an den aktuellen Link per XML, um sicherzustellen, dass diese Attribute korrekt angezeigt werden, auch wenn der Link die aktuelle Seite ist. Zuvor wurden keine benutzerdefinierten Attribute für den aktuellen Seitenlink angezeigt, da die Methode getAttributesHtml() für den aktuellen Link nicht verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/30070>
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
* _AC-12857_: PHP 8.2.15 entfernt FTP-Erweiterung
   * _Fehlerbehebung_: Das System enthält jetzt die FTP-Erweiterung als Abhängigkeit in der Datei „composer.json“, wodurch die erfolgreiche Konfiguration von CSV-Importen über FTP sichergestellt wird. Zuvor wurde beim Versuch, CSV-Importe über FTP zu konfigurieren, ein Fehler ausgelöst, da die FTP-Erweiterung im PHP-Paket fehlt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: Möglichkeit, Bereich für den CLI-Befehl :di:/info zu definieren
   * _Fehlerbehebung_: Das System ermöglicht es Entwicklerinnen und Entwicklern jetzt, einen Bereich für den CLI-Befehl dev:di:info zu definieren, wodurch der Entwicklungs- und Debugging-Prozess verbessert wird. Zuvor konnte dieser Befehl nur Informationen für den Bereich GLOBAL anzeigen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38759>
* _AC-13247_: setup:upgrade schlägt mit MariaDB 11.4-Version aufgrund von Änderungen an Zeichensatz und Sortierung fehl
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
* _AC-8662_: [Problem] Verbesserung der Cron-Fehlerprotokollierung
   * _Fix Hinweis_: Das System erfasst und protokolliert jetzt sowohl STDERR als auch STDOUT für Cron-Prozesse und liefert wertvolle Diagnoseinformationen in Szenarien, in denen Cron-Prozesse fehlschlagen. Zuvor wurden Fehlermeldungen innerhalb von Cron-Prozessen nicht aufgezeichnet, und STDERR und STDOUT für Cron-Gruppen, die in separaten Prozessen ausgeführt werden, gingen verloren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32690>
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

### Framework, UI-Framework

* _ACP2E-3324_: Möglichkeit, den Konfigurationswert zu überschreiben, selbst wenn er gesperrt ist
   * _Fehlerbehebung_: Zuvor konnte die Designkonfiguration nicht über den Befehl bin/magento config:set festgelegt werden und die gesperrten Werte konnten durch Manipulation des Formulars, das sie anzeigte, geändert werden. Nach dem Fix können gesperrte Werte, die von cli mit —lock-env oder —lock-conf gesetzt wurden, nicht mehr aktualisiert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: Übersetzungen für Kundenrückgabeattribute werden für die jeweilige StoreView nicht in der GraphQL-API angezeigt
   * _Fehlerbehebung_: Übersetzungen für Kundenrückgabeattribute werden in der GraphQL-API für die jeweilige StoreView angezeigt.
Zuvor wurden Kundenrückgabeattribute für die jeweilige StoreView nicht in der GraphQL-API angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: [Cloud]-Problem mit Benutzerauthentifizierung und Site-übergreifendem Token-Zugriff bei der Einrichtung mehrerer Sites
   * _Fehlerbehebung_: GraphQL-Kundeninformationen und Warenkorbabfragen bei der Einrichtung mehrerer Sites überprüfen, ob der Kunde auf einer nicht standardmäßigen Website vorhanden ist.
Zuvor funktionierte die Abfrage, ohne sicherzustellen, dass der Kunde bei der Einrichtung mehrerer Sites auf einer nicht standardmäßigen Website vorhanden ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
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
* _LYNX-600_: Erhöhen Sie die maximale standardmäßige GraphQL-Abfrageleistung auf 1.000

### GraphQL, Suche

* _ACP2E-948_: Produktliste GraphQL-Abfrage beschränkt auf total_count 10.000 Produkte nur
   * _Fehlerbehebung_: Nach der Fehlerbehebung ist das Suchergebnis nicht auf 10000 Produkte beschränkt, es wird möglich, alle Produkte zu erhalten, die den Suchkriterien entsprechen, auch wenn die Anzahl mehr als 10000 beträgt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, Test-Framework

* _ACP2E-3363_: Fehler beim Magento\GraphQl\App\GraphQlCustomerMutationsTest.php-Integrationstest
   * _Notiz korrigieren_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Import/Export

* _ACP2E-_: Importschaltfläche fehlt
   * _Hinweis korrigieren_: Beheben Sie das fehlende Problem mit der Importschaltfläche, nachdem die Daten in der CSV-Datei mit richtigen und falschen Datensätzen überprüft wurden. Zuvor wird die Schaltfläche Importieren nicht angezeigt, nachdem Daten mit richtigen und falschen Datensätzen in der CSV-Datei geprüft wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Exportierte Kundenadresse kann nicht importiert werden
   * _Fehlerbehebung_: Der Import von Kundenadressen wird erwartungsgemäß fortgesetzt. Zuvor verlief die Validierung einer Kundenadressenimportdatei nicht, wenn Kundenkonten freigeben = global gilt, und es gibt zwei Websites, auf denen die Standardwebsite eine eingeschränkte Länderliste hat und die importierte Adresse für eine andere Website gilt, auf der die zulässigen Länder unterschiedlich sind
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] Falsche Menge in CSV-Datei gab keinen Fehler zurück
   * _Hinweis korrigieren_: Beim Import von Lagerbeständen wird jetzt ein Validierungsfehler für nicht numerische Werte in der Spalte „Menge“ angezeigt. Zuvor führte der Import von Lagerbeständen mit nicht numerischem Wert in der Spalte „Menge“ dazu, dass die Menge auf 0 gesetzt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: Produktexport verursacht OOM auch bei 4G-Speicherbegrenzung
   * _Fehlerbehebung_: Vor dieser Fehlerbehebung ist der Produktexport fehlgeschlagen, wenn Produktattribute Tausende von Optionswerten hatten, selbst mit verfügbarem 4G-Speicher. Nach dieser Fehlerbehebung sollte der Produktexport den Export der CSV-Datei abschließen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Import/Export, Leistung

* _ACP2E-3476_: [Cloud] Die Importzeit für Produkte wurde erheblich verlängert
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurde beim Produktimport aus dem Katalog mit über 10.000 Einträgen eine erhebliche Zeitbeeinträchtigung festgestellt. Nach der Fehlerbehebung wird der Import des Katalogprodukts zeitnah ausgeführt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/87d012e5>

### Installieren und Verwalten

* _AC-13242_: Magento-Upgrade schlägt auf MariaDB 11.4 + 2.4.8-beta1 fehl
   * _Fehlerbehebung_: Das Upgrade sollte fehlerfrei durchgeführt werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7b336d0a>

### Inventar/MSI

* _ACP2E-3335_: Bestellung kann nicht gesendet werden, wenn MSI Pick Up Store aktiviert ist
   * _Fehlerbehebung_: Verbesserte Inventarleistung der Versanderstellung bei vielen Quellen mit Abholung im Geschäft
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: Cron Reindex aktualisiert die Produktverfügbarkeit im Frontend nicht
   * _Fehlerbehebung_: Zuvor waren Produkte im Frontend nicht vorrätig, nachdem der Auftragsstatus über die REST-API aktualisiert wurde. Nach der Aktualisierung des Auftragsstatus über die REST-API werden die Produkte nun als vorrätig angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Das Hinzufügen von Bildern zu konfigurierbaren funktioniert nicht, wenn MSI aktiviert ist.
   * _Fehlerbehebung_: Der Bild-Upload für ein konfigurierbares Produkt funktioniert jetzt wie erwartet, wenn das Bestandsmodul verwendet wird. Zuvor funktionierte der Bild-Upload nicht
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/fdf409aa>

### Inventar/MSI, Suche

* _ACP2E-3413_: Alle Produkte werden mit [is_out_of_stock] = 1 indiziert, wenn die SKU nicht als durchsuchbares Attribut festgelegt ist
   * _Fehlerbehebung_: Nach der Fehlerbehebung ist „is_out_of_stock“ im Katalogsuchindex korrekt, auch wenn die SKU nicht durchsuchbar ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/5b21b7af>

### Reihenfolge

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

### Sonstige

* _LYNX-426_: Der Rabatt-Prozentsatz wird nicht für Bundle-Produkte mit dynamischem Preis berechnet
* _LYNX-485_: Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist
* _LYNX-486_: not_available_message und only_x_left_in_stock zeigen nicht denselben verfügbaren Bestand an
* _LYNX-488_: original_row_total-Feld gibt falschen Wert zurück
* _LYNX-503_: Die gruppierte Produktminiatur sollte gemäß der Konfiguration angezeigt werden     .
* _LYNX-510_: Fehler bei der Abfrage von selected_options in OrderAddress
* _LYNX-512_: original_item_price beinhaltet keine Rabatte
* _LYNX-530_: Meldung „Nicht verfügbar“ zeigt nicht die verfügbare Lagermenge an
* _LYNX-532_: „OUT_OF_STOCK“-Status wird auf Einfach mit benutzerdefinierten Optionen zurückgegeben Produkte mit Mehrfachauswahl-Optionen
* _LYNX-533_: Fehler (GQL): cart.itemsV2.items.product.custom_attributesV2 gibt einen Server-Fehler zurück
* _LYNX-536_: orders/date_of_first_order gibt immer null zurück
* _LYNX-544_: Der Kunde darf eine teilweise versendete Bestellung nicht stornieren können
* _LYNX-548_: Fehlercodes für die Stornierung von Bestellungen basierend auf der Fehlermeldung
* _LYNX-581_: Verschieben Sie Cookie-bezogene Eigenschaften von „privat“ zurück in „geschützt“

### Andere Entwickler-Tools

* _AC-12731_: CSP-Probleme in Kombination mit dev/css/use_css_critical_path
   * _Fehlerbehebung_: Das System lädt CSS-Dateien jetzt korrekt asynchron auf Auscheckseiten, selbst wenn die Einstellung „dev/css/use_css_critical_path“ aktiviert ist, um sicherzustellen, dass diese Seiten mit den richtigen CSS-Stilen gerendert werden. Zuvor verhinderte eine eingeschränkte Content Security Policy (CSP) die Ausführung von Inline-JavaScript, was dazu führte, dass CSS-Dateien nicht wie erwartet geladen wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Bei Verwendung des virtuellen Typs zum Konfigurieren des Plug-ins kann die Abfangmethode im setup-compile:di:Befehl nicht korrekt generiert werden
   * _Fehlerbehebung_: Das System generiert jetzt korrekt Abfangmethoden, wenn ein virtueller Typ zum Konfigurieren eines Plug-ins verwendet wird, um konsistente Ergebnisse sicherzustellen, unabhängig davon, ob vorkompiliert oder zur Laufzeit kompiliert. Zuvor generiert das System beim Vorkompilieren falsche Ergebnisse im Vergleich zur Laufzeitkompilierung.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: Dateien können nicht von der Datenerfassung heruntergeladen werden
   * _Fehlerbehebung_: Beim Herunterladen der Sicherung wird keine leere Seite mehr angezeigt, sondern die Datei wird heruntergeladen.

### Zahlungen

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
* _AC-13471_: Unterstützung für die CommandLoaderInterface-Schnittstelle von Symfony in Magento CLI
   * _Fehlerbehebung_: Durch diese Änderung wird die Initialisierungszeit der Magento-CLI-App verkürzt, da Befehle erst dann initialisiert werden können, wenn sie benötigt werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/29355>

### Produkt

* _AC-13173_: [Problem] Beheben von Tippfehlern im PHPDoc-Block
   * _Fehlerbehebung_: Das System entfernt jetzt korrekt eine unbekannte referenzierte Variable in PHPDoc für die $helper-Variablendeklaration, was die Code-Klarheit und -Genauigkeit verbessert. Zuvor verursachte diese unbekannte referenzierte Variable in PHPDoc Verwirrung und potenzielle Ungenauigkeiten im Code.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problem] Layout für fehlerhafte Bundles und herunterladbare Produktseiten in Magento >= 2.4.7 behoben
   * _Fehlerbehebung_: Das Layout für Paket- und herunterladbare Produktseiten wurde korrigiert, um eine konsistente und korrekte Anzeige auf allen Geräten sicherzustellen. Zuvor traten auf diesen Seiten Layout-Probleme aufgrund einer Neuanordnung des Produktinfo-Medienblocks auf.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_: [Cloud] Produkte in Kategorie - Produkte hinzufügen - Zuweisen - Alle auswählen
   * _Hinweis korrigieren_: Benutzer können jetzt Produkte mit dem Umschalter auswählen oder die Auswahl aufheben.

### Promotion

* _ACP2E-3139_: Verkaufsregel mit dem Attribut „Rabatt-Mengenschritt (Kauf X)“ führt dazu, dass andere Regeln nicht angewendet werden
   * _Hinweis korrigieren_: Die Warenkorb-Preisregel hebt zuvor angewendete Regeln nicht auf, wenn die Menge des Produkts im Warenkorb nicht ausreicht, um die Regel anzuwenden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: Leistungsproblem bei Warenkorb-Preisregel - Modul für erweiterte Verkaufsregel
   * _Fehlerbehebung_: Fehlende DB-Indizes für AdvancedSalesRule-Filter hinzugefügt
* _ACP2E-3332_: Verkaufsregeln für Probleme mit Festbetragsrabatt und „Maximaler Mengenrabatt wird angewendet auf“
   * _Hinweis korrigieren_: Es wurde ein Problem mit dem Rabatt auf Warenkorbregeln behoben, wenn ein fester Rabatt so konfiguriert ist, dass er auf eine begrenzte Anzahl von Produkten angewendet wird, wenn der Warenkorb der Warenkorb ist. Zuvor wurde der Wert „Maximaler Mengenrabatt wird auf angewendet“ verwendet, um den Preis des aktuellen Artikels im Warenkorb zu berechnen, nicht nur für die Berechnung des Rabatts der Regel.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: Beim [CLOUD] Magento-Upgrade wurde zwischen Groß- und Kleinschreibung unterschieden
   * _Fehlerbehebung_: Vor der Fehlerbehebung mussten Sie den Gutscheincode genau so eingeben, wie er unter Berücksichtigung von Groß- oder Kleinbuchstaben konfiguriert wurde. Jetzt wird der Coupon im Backend validiert, unabhängig von der Code-Konfiguration in Groß- oder Kleinbuchstaben.
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
* _ACP2E-3498_: Falscher Rabattwert, wenn mehrere Warenkorbpreisregeln gleichzeitig mit Produkten mit Rabatten/Sonderpreisen angewendet werden
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurde der feste Betrag für Regeln für den gesamten Warenkorb nicht ordnungsgemäß angewendet, wenn mehrere Regeln angewendet wurden. Jetzt werden die Regeln für den Rabatt auf feste Beträge ordnungsgemäß angewendet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Rückgabe

* _ACP2E-3330_: [CLOUD] Benutzer mit eingeschränktem Administratorzugriff können das Rückgabemenü und die Schaltflächen sehen
   * _Fehlerbehebung_: Benutzer mit eingeschränktem Administratorzugriff haben jetzt keinen Zugriff auf RMA-bezogene Steuerelemente (Menü und Schaltflächen).
Zuvor eingeschränkte Admin-Benutzer konnten das Menü und die Schaltflächen „Zurück“ sehen.
* _ACP2E-3443_: Der Rückgabebildschirm ist fehlerhaft, wenn der Bildschirm aktualisiert wird
   * _Hinweis korrigieren_: Der Benutzer kann die Seite aktualisieren, ohne dass es zu einer Bildschirmverzerrung kommt.

### Verkauf

* _AC-13750_: Gesamtsumme und Basisgesamtsumme stimmen nicht mit den Testergebnisschritten überein
* _AC-13751_: Die Preisregel für den zweiten Warenkorb wird nicht angewendet, wenn die Regel für den ersten Warenkorb bereits angewendet wurde

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

* _ACP2E-3273_: ReCaptcha V2 wird beim Checkout für die deutsche Sprache falsch angezeigt
   * _Fix Hinweis_: Zuvor erscheint das reCAPTCHA von unter der E-Mail-Adresse von der Kasse für Sprachen mit langen Wörtern wie Deutsch ungestylt. Danach sieht das reCAPTCHA genauso aus wie alle reCAPTCHA-Elemente aus dem Rest der Bereiche.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Für Captcha bei der Administratoranmeldung ist für einige Benutzer keine Interaktion erforderlich
   * _Fehlerbehebung_: ReCaptcha für die Admin-Anmeldung wird erwartungsgemäß validiert

### Lieferung

* _AC-12938_: UPS-REST-„Sandbox“- und „prod“-Setup-Anleitungsaktualisierungen in devDoc
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

### Steuer

* _ACP2E-3193_: Feste Produktsteuer (FPT) funktioniert nicht mit konfigurierbaren Produkten
   * _Fix Hinweis_: FPT für konfigurierbare Produktvarianten, die ordnungsgemäß funktionieren.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Test-Framework

* _AC-13362_: [Problem] Rechtschreibkorrektur PHPDoc
   * _Fehlerbehebung_: Das System erkennt nun veraltete Methoden in IDEs aufgrund einer Rechtschreibkorrektur im PHPDoc korrekt. Zuvor führte ein Rechtschreibfehler im PHPDoc dazu, dass IDEs bestimmte Methoden nicht als veraltet erkannten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Überprüfen des Verhaltens beim beständigen Warenkorb nach Ablauf der Sitzung
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: Integrationstests sind fehlgeschlagen Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Fix Hinweis_: Feste Mftfs
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/078c387e>

### UI-Framework

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
* _AC-13459_: Inkonsistentes Verhalten bei der Sortierung „Nicht vorrätig“ mit Mindestbestand
   * _Fehlerbehebung_: Das System sortiert jetzt Produkte im Katalog korrekt anhand der Lagerbestände, hält sich dabei an den festgelegten Mindestbestandsschwellenwert und verschiebt nicht vorrätige Artikel konsequent an das Ende der Liste. Zuvor war das Sortierverhalten inkonsistent, da Elemente basierend auf ihren Lagerbeständen nicht immer in der richtigen Reihenfolge angezeigt wurden und Änderungen bei der Sortierung nach dem Speichern, Aktualisieren oder Ändern der Kategoriehierarchie unvorhersehbar auftreten konnten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Vorschlag für eine verbesserte Fehlerberichterstattung für Require.js-Ladeprobleme
   * _Hinweis zur Fehlerbehebung_: Diese PR verbessert die Fehlermeldung, wenn Require eine Komponente nicht laden kann.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [Problem] Entfernen unnötiger Skripte - Zusammenfassung der Überprüfung
   * _Fehlerbehebung_: Das System optimiert jetzt die Seitenladezeit, indem unnötige JavaScript-Skripte aus dem Bewertungsabschnitt entfernt werden, anstatt Inline-CSS-Stile für einen effizienteren und besser lesbaren Code zu verwenden. Zuvor konnte die Verwendung von JavaScript-Skripten für den Bewertungsabschnitt die Seitenladezeit möglicherweise verlangsamen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37776>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: Site-Kopfzeile | Sonderzeichen im Abschnitt „Kundenempfehlung“
   * _Fehlerbehebung_: Nach der Fehlerbehebung werden Sonderzeichen im Begrüßungsabschnitt des Kunden korrekt angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1366ae5e>
