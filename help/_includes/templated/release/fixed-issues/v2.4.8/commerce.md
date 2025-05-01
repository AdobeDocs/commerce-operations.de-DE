---
source-git-commit: 53b2494d848c027e32f1493bbc7a9f204677afaa
workflow-type: tm+mt
source-wordcount: '27958'
ht-degree: 0%

---
# Behobene Probleme in Adobe Commerce (v2.4.8)

## Behobene Probleme in Version 2.4.8

Es wurden 582 Probleme im Adobe Commerce 2.4.8-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

* __/V1/Transactions REST API gibt einen Fehler zurück, wenn parent_txn_id = txn_id ist__
Das System verarbeitet jetzt die Transaktionen des übergeordneten und des untergeordneten Konzepts korrekt, bei denen die übergeordnete Transaktions-ID mit der Transaktions-ID identisch ist, sodass beim Abfragen des /V1/transaction-REST-API-Endpunkts keine Endlosschleife entsteht. Zuvor führte dieses Szenario aufgrund der Überschreitung der maximalen Ausführungszeit zu einem schwerwiegenden Fehler.
  _AC-10042 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_
* __[GraphQL] Typproblem in 2.4.7__
Das System verarbeitet jetzt Ganzzahlwerte in der GetCustomSelectedOptionAttributes-Funktion beim Ausführen einer GraphQL-Abfrage korrekt, sodass typbezogene Fehler vermieden werden. Zuvor führte das Starten einer GraphQL-Abfrage, die GetCustomSelectedOptionAttributes mit einem ganzzahligen Argument verwendet hat, zu einem Typfehler.
  _AC-11878 - [GitHub-Problem](https://github.com/magento/magento2/issues/38662) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38663)_
* __Sonderzeichen in Kategorie url_key (bei Erstellung über REST-API)__
Früher In category_url_key ist nach der Fehlerbehebung kein Sonderzeichen vorhanden, sondern es wird ein Sonderzeichen in category_url_key angezeigt.
  _AC-3223 - [GitHub-Problem](https://github.com/magento/magento2/issues/35577) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c699c206)_
* __REST-API mit Bestellungen von einer anderen Website. __
Das System unterstützt jetzt den autorisierten Zugriffsbereich für REST-API-Admin-Token und Magento_Sales-Endpunkte. Dadurch wird sichergestellt, dass die REST-API nur Bestellungen anzeigt, auf die Admins Zugriff haben. Zuvor zeigte die REST-API Bestellungen von allen Websites an, unabhängig von der zugewiesenen Website des Admin-Benutzers.
  _ACP2E-2703_
* __Problem mit der Rest-API nach der Aktivierung von 2FA Duo__
2FA mit Duo Sicherheitsoption generiert jetzt die richtige Signatur für die Rest-API
  _ACP2E-2755 - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/412fa642)_
* __[REST API]: „Standardwert in Store-Ansicht verwenden“ bleibt nach dem Hinzufügen von Konfigurationen für ein konfigurierbares Produkt nicht aktiviert__
Das Problem wurde behoben, indem sichergestellt wurde, dass die Datenbankeinträge für die anpassbaren Optionen eines nicht standardmäßigen Speichers korrekt sind. Das Kontrollkästchen für den benutzerdefinierten Store im Abschnitt „Admin > Katalog > Produktbearbeitung > Anpassbare Optionen“ war zuvor aufgrund ungenauer Datenbankeinträge deaktiviert, auch wenn der Optionstitel für den benutzerdefinierten Store genauso geblieben ist wie der Standardstore.
  _ACP2E-2927 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3056e9cb)_
* __REST-API kann bei Verwendung von Oauth1 keine Anfragen mit Schrägstrich (/) in der SKU stellen__
Vor der Fehlerbehebung waren Sie nicht in der Lage, einen erfolgreichen API-Aufruf für ein Produkt durchzuführen, das &quot;/&quot; in der SKU hatte. Jetzt können Sie eine erfolgreiche API-GET-Anfrage für Produktdetails ausführen, obwohl ihre SKU einen Schrägstrich enthält.
  _ACP2E-2969 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_
* __Die Aktualisierung der Kundenadresse schlägt beim Aktualisieren über die REST-API fehl, wenn „validateDefaultAddress“ aktiviert ist__
Der API-Endpunkt funktioniert jetzt wie beabsichtigt, nachdem das Problem mit dem in der API-Payload fehlenden ID-Schlüssel behoben wurde.
  _ACP2E-3079 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_
* __[Cloud] Erstellen der doppelten Website-Preisgruppe in der Preisstufen-API.__
Die Preis-Rest-API der Stufe erlaubt es jetzt nicht mehr, die Kundengruppe „Duplizierte Website-Preisgruppe“ zu erstellen.
Zuvor war es möglich, die Kundengruppe „Duplizierte Website-Preisgruppe“ in der Stufen-Preis-API zu erstellen, die die Validierung in Admin während der Produktspeicherung nicht bestehen konnte.
  _ACP2E-3091 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_
* __Bestellkommentar mit Status kann nicht über die REST-API hinzugefügt werden__
Das Problem wurde behoben, indem die Änderung des Bestellstatus zugelassen wurde, wenn sie nur aus dem aktuellen Status stammt. Zuvor wurde der Bestellstatus nicht berücksichtigt und Änderungen in einem Bestellstatus verhindert, selbst wenn er aus demselben Status stammte.
  _ACP2E-3130 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __Der asynchrone Vorgang schlägt fehl, wenn die SKU in der Payload fehlt__
Asynchrone und Synchronisierungsvorgänge sind zuvor aufgrund von Fehlern bei der Produktspeicherung fehlgeschlagen, wenn die SKU in der Payload fehlt. Nach der Behebung schlagen die Vorgänge der asynchronen und synchronisierten Produkt-REST-API mit der entsprechenden Ausnahmemeldung fehl.
  _ACP2E-3236 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_
* __[CLOUD] Die Basispreise können nicht mit der REST-API aktualisiert werden (der Wert von „value_id“ in „catalog_product_entity_decimal“ wird nicht korrekt inkrementiert).__
Vor dieser Fehlerbehebung wurde beim Aufruf der REST-API /rest/default/V1/products/base-prices die Inkrement-ID fälschlicherweise erhöht, sodass eine Lücke zwischen den Werten entstand. Nach der Fehlerbehebung wird die Inkrement-ID wie erwartet inkrementell erhöht. Außerdem wurde der Wertebereich des Feldes vergrößert.
  _ACP2E-3376 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Bestellartikel sind in E-Mails mit Gutschriften für die API POST V1/order/:orderId/fund nicht sichtbar__
Vor dieser Fehlerbehebung enthält eine Kundin oder ein Kunde, wenn sie bzw. er eine Gutschrift aus einer API-Anfrage erstellt, die send_email benachrichtigt, bisher kein Produktdetailraster. Nachdem diese Fehlerbehebung angewendet wurde, sendet der Kunde eine Anfrage zur Gutschrift-API und findet die Produktdetails in der E-Mail.
  _ACP2E-3460 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Standardwerte werden für Datums- und Uhrzeitattribute mit der Produkt-Rest-API nicht festgelegt__
Standardwerte legen jetzt für Datums- und Datums- und Uhrzeitattribute über die Rest-API korrekt fest
  _ACP2E-3486 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

### APIs, Warenkorb und Checkout

* __Kritischer 500-Fehler: Magento\Framework\Webapi\Exception im Zusammenhang mit dem Accept-HTTP-Header__
Nach der Behebung besteht kein Problem mit der Angabe des „Accept“-Headers.
  _ACP2E-3343 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_

### APIs, GraphQL

* __Es ist kein GraphQL zum Abonnieren von Reward Points-Updates für Kunden verfügbar__
Vor der Behebung konnte das Kundenattribut reward_warning_notification nicht über die GraphQL-Mutation und den REST-API-Aufruf aktualisiert werden. Jetzt kann auf die gleiche Weise aktualisiert werden wie das Kundenattribut reward_update_notification.
  _ACP2E-3348_

### APIs, GraphQL, Steuer

* __Sowohl Luma (Rest-API) als auch GraphQL berechnen keine Steuern, wenn nur eine Postleitzahl angegeben wird.__
Das System berechnet die Steuern jetzt korrekt, wenn nur eine Postleitzahl angegeben wird, was genaue Steuerschätzungen für Luma (Rest-API) und GraphQL gewährleistet. Zuvor wurden nur Versandschätzungen berechnet und keine Steuern berücksichtigt, wenn nur eine Postleitzahl angegeben wurde.
  _AC-12060_

### Konto

* __Das Formular „Kundenadresse“ ermöglicht zufälligen Code in den Namensfeldern__
Das System validiert jetzt die Eingabe in den Feldern Vorname und Nachname im Formular der Kundenadresse, wodurch die Verwendung von zufälligem Code verhindert wird. Zuvor ermöglichte das System die Verwendung von zufälligem Code in diesen Feldern ohne einen Fehler auszulösen.
  _AC-10782 - [GitHub-Problem](https://github.com/magento/magento2/issues/38331) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38345)_
* __Admin-Passwortaktualisierung.__
  _AC-10886 - [GitHub-Problem](https://github.com/magento/magento2/issues/38352) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4bca5dfe)_
* __Mein Konto Bei Speicherung Adresse hinzufügen stürzt ab__
Das System speichert Kundenadressen jetzt korrekt, selbst wenn das Feld Region nicht angezeigt wird, was einen Absturz während des Speichervorgangs verhindert. Zuvor führte der Versuch, eine Adresse ohne angezeigtes Bereichsfeld hinzuzufügen oder zu bearbeiten, zu einem Ausnahmefehler.
  _AC-10990 - [GitHub-Problem](https://github.com/magento/magento2/issues/38406) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38407)_
* __Umleitungsschleife bei URLs in Großbuchstaben__
Das System konvertiert nun in URLs Großbuchstaben automatisch in Kleinbuchstaben, wodurch eine Umleitungsschleife beim Zugriff auf die Homepage verhindert wird. Zuvor führte die Verwendung von Großbuchstaben in der Secure Base-URL beim Zugriff auf die Homepage zu einer kontinuierlichen Umleitungsschleife.
  _AC-11718 - [GitHub-Problem](https://github.com/magento/magento2/issues/38538) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38539)_
* __middlename(s) nicht für Gastkonten gespeichert__
Das System speichert nun den zweiten Vornamen für Gastkonten beim Checkout korrekt, sodass er in der E-Mail-Vorlage verfügbar ist. Zuvor wurde der zweite Vorname nicht in der Angebotstabelle gespeichert und war in der E-Mail-Vorlage für Gastkonten nicht zugänglich.
  _AC-11755 - [GitHub-Problem](https://github.com/magento/magento2/issues/38593) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39067)_
* __Admin: Schaltflächen für Seitenaktionen, die links statt rechts eingeblendet werden__
Das System richtet nun die Schaltflächen für die Seitenaktionen korrekt auf der rechten Seite der Sticky-Kopfzeile im Admin-Bedienfeld aus, wodurch das professionelle Look-and-Feel verbessert wird. Zuvor waren diese Schaltflächen fälschlicherweise auf der linken Seite der Sticky-Kopfzeile unverankert.
  _AC-11919 - [GitHub-Problem](https://github.com/magento/magento2/issues/38701) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44cef3a9)_
* __`dev:di:info`in Magento 2.4.7__
Das System zeigt jetzt beim Ausführen des `dev:di:info`-Befehls die Konstruktorparameter korrekt an, sodass keine Fehler auftreten. Zuvor führte die Ausführung dieses Befehls zu einem Fehler aufgrund eines Typkonflikts im -Argument.
  _AC-11999 - [GitHub-Problem](https://github.com/magento/magento2/issues/38740) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Anmeldung als Kunden-Opt-in-Checkbox nicht übersetzbar__
Das System ermöglicht jetzt, dass die Felder „Als Kunden-Opt-in anmelden“ und „Als Kunden-Checkbox-Tooltip anmelden“ im Bereich „Store-Ansicht“ festgelegt werden, was Übersetzungen für verschiedene Store-Ansichten ermöglicht. Zuvor wurden diese Felder nur im Umfang der „Website“ festgelegt, wodurch Übersetzungen für einzelne Store-Ansichten verhindert wurden.
  _AC-13000 - [GitHub-Problem](https://github.com/magento/magento2/issues/32329) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32359)_
* __Die Startseite der Frontend-Benutzeroberfläche in der Dropdown-Liste meines Profils ist nicht vorhanden.(gelegentlich)__
  _AC-14299_
* __Kunde ist angemeldet, zeigt aber 404-Fehler in Frontend an.__
Die Kunden-Dashboard-Seite der Storefront wird jetzt wie erwartet geladen, wenn sich ein Kunde anmeldet. Zuvor konnten sich Kunden zwar anmelden, auf dieser Seite wurde jedoch ein 404-Fehler angezeigt. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
  _AC-6071 - [GitHub-Problem](https://github.com/magento/magento2/issues/35838) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36263)_
* __Kundenattributinformationen können nicht im Abschnitt „Kunden bearbeiten“ von Admin gespeichert werden;__
Die Store-ID des Kunden wird jetzt ordnungsgemäß pro Website-Umfang für das Admin-Kundenbearbeitungsformular implementiert.
  _ACP2E-2791 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/488c1034)_
* __[Cloud] Kunde kann nicht über API erstellt werden, wenn „Privater Verkauf“ aktiviert ist__
Jetzt können Kunden sowohl von authentifizierten Admin-Benutzern als auch mit einem authentifizierten Integrations-Token über die REST-API erstellt werden, wenn die Website-Einschränkung aktiviert ist.
  _ACP2E-3115_
* __Nach der Anmeldung sind die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.__
Produkte, die vor der Anmeldung als Kunde zur Produktvergleichsliste hinzugefügt wurden, bleiben jetzt nach der Anmeldung erhalten.
Zuvor waren nach der Anmeldung die Produkte, die als Gastbenutzer zur Vergleichsliste hinzugefügt wurden, nicht sichtbar.
  _ACP2E-3329 – [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __Die Konfiguration &quot;Länder zulassen&quot; verursacht Probleme in der Konfiguration von Kundenadressen__
Die Auswahl von &quot;Länderkonfiguration zulassen&quot; hat jetzt keinen Einfluss auf Länder, die außerhalb der angegebenen Umfang angezeigt werden. Zuvor beeinflusste die Konfiguration &quot;Länder zulassen&quot; das Kundenadressattribut außerhalb einer bestimmten Umfang
  _ACP2E-3433 – [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __In der gemeinsamen Geschenkeliste wird das Ereignis Datum als 1 Tag früher__ angezeigt
Das Datum der Geschenkeliste wird jetzt in der Storefront korrekt angezeigt
  _ACP2E-3445_
* __VAPT: Business Logic Error - künftiges Datum als Geburtsdatum des Kunden__
Das Geburtsdatum des Kunden kann nicht nach heute festgelegt werden
  _ACP2E-3501 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

### Konto, APIs, GraphQL

* __Kunden-API – Anmeldung Fehler Zahl nach erfolgreicher Anmeldung nicht auf 0 Zurücksetzen__
Jetzt wird die Fehlernummer in der Kundenentitätstabelle auf Null zurückgesetzt, nachdem der Kunde erfolgreich über API-Endpunkte Log-in wurde.
  _ACP2E-3246 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### Konto, Admin-Benutzeroberfläche, B2B

* __Benutzende mit eingeschränktem Administratorzugriff können benutzerdefinierte freigegebene Kataloge nicht immer sehen__
Benutzende mit eingeschränkten Administratorrechten können jetzt Kundinnen und Kunden sowie alle freigegebenen Kataloge, denen die Produkte zugewiesen sind, konsistent anzeigen und verwalten, sofern sie Zugriff auf den jeweiligen Shop haben. Zuvor konnte ein Admin-Benutzer mit eingeschränktem Zugriff auf einen bestimmten Store nicht immer alle freigegebenen Kataloge sehen, denen die Produkte zugewiesen waren, oder er konnte Kunden sehen, die nicht speichern konnten, was zu Inkonsistenzen im System führte.
  _ACP2E-3038 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_

### Konto, Warenkorb und Checkout

* __benutzerdefinierte Kundenadressattribut „Auswählen“ wird für neue Kundenadresse nicht gerendert__
  _AC-2341 - [GitHub-Problem](https://github.com/magento/magento2/issues/34950)_

### Admin-Benutzeroberfläche

* __[Problem] Berechtigungsprüfung für die Datenschaltfläche „Daten neu laden“__
Das System umfasst jetzt eine Berechtigungsprüfung für die Schaltfläche „Daten neu laden“, um sicherzustellen, dass sie nur Benutzern mit den entsprechenden Berechtigungen angezeigt und zugänglich sind. Zuvor war die Schaltfläche „Daten neu laden“ für alle Benutzer sichtbar und klickbar, was zu einer „nicht zulässigen“ Seite führte, wenn Benutzer ohne die erforderlichen Berechtigungen darauf klickten.
  _AC-10705 - [GitHub-Problem](https://github.com/magento/magento2/issues/38283) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38279)_
* __[Problem] Inkonsistente Beschriftungen für Attribute in Marketing-Regeln__
Das System füllt nun die Beschriftungen für Kategorie- und Attributoptionen in der Warenkorb-Preisregel korrekt aus
  _AC-11427 - [GitHub-Problem](https://github.com/magento/magento2/issues/31232) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31231)_
* __Die Datenvalidierung ist erfolgreich und die Schaltfläche Importieren ist beim Importieren von Produkten mit dem Verhalten „Ersetzen“ vorhanden__
Das System validiert jetzt die Daten korrekt und blendet die Schaltfläche „Importieren“ während des Produktimports mit „Ersetzen“-Verhalten aus, um einen unbeabsichtigten Datenaustausch zu verhindern. Zuvor hat das System die Daten falsch validiert und die Schaltfläche „Importieren“ angezeigt, was zu potenziellen Dateninkonsistenzen führte.
  _AC-11588 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_
* __[Bug] Magento 2.4.7 lässt keine Produktfotos mit der Dateierweiterung „Großbuchstaben“ zu.__
Das System akzeptiert jetzt Produkt-Image-Uploads mit Großbuchstaben-Dateierweiterungen, was einen reibungslosen Produkterstellungsprozess gewährleistet. Zuvor wurden Bild-Uploads mit Großbuchstaben-Dateierweiterungen abgelehnt, was Benutzer zwang, die Dateierweiterung in Kleinbuchstaben zu ändern.
  _AC-12167 - [GitHub-Problem](https://github.com/magento/magento2/issues/38831) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __Ausgeblendetes Dropdown-Menü in Rastern mit Auswahl-Aktion (z. B. Inhalt > Elemente > Seiten)__
Jetzt wurde das System für alle ähnlichen Dropdown-Listen für alle Raster korrigiert.
  _AC-12319 - [GitHub-Problem](https://github.com/magento/magento2/issues/38891) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39371)_
* __[Problem] Warnung beheben: Nicht definierter Array-Schlüssel „filter“__
Das System verarbeitet jetzt Szenarien, in denen ein neuer Benutzer noch nicht mit Lesezeichen interagiert hat, sodass keine Warnung bezüglich eines nicht definierten Array-Schlüssels „Filter“ protokolliert wird. Zuvor wurde diese Warnung protokolliert, wenn ein neuer Benutzer nicht mit Lesezeichen interagiert hatte.
  _AC-13131 - [GitHub-Problem](https://github.com/magento/magento2/issues/39013) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38996)_
* __Die CSV-Datei des Produktimports mit Sonderzeichen schlägt aufgrund von Code-Änderungen in der Datei „Validate.php“ fehl__
Das System validiert und importiert jetzt Produkt-CSV-Dateien, die Sonderzeichen enthalten, korrekt, was eine erfolgreiche Datenübertragung ermöglicht. Zuvor führte der Versuch, eine Produkt-CSV-Datei mit Sonderzeichen zu importieren, zu einem Fehler, der den Importvorgang verhinderte.
  _AC-13529 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __Wenn die maximale Anzahl von Anfragen zum Zurücksetzen des Passworts“ größer als 0 festgelegt ist, z. B.: 3 , werden Fehlermeldungen zum „Überschreiten des Grenzwerts“ gesendet, bevor das Limit erreicht wird, d. h. ab dem zweiten Mal__
  _AC-13767_
* __Obwohl die maximale Anzahl von Anfragen zum Zurücksetzen des Kennworts“ auf 0 ( deaktiviert) festgelegt ist, werden „Fehlermeldungen zum Überschreiten des Grenzwerts ab dem 2. Mal gesendet“__
  _AC-13768_
* __Es gibt kein rotes Sternchen für das Pflichtfeld einer Telefonnummer__
Frühere rote Sternchen wurden nicht für Telefonnummer angezeigt, aber  Telefonnummer war obligatorisch. Was nun ein festes rotes Sternchen ist, kann auf der Telefonnummer als Pflichtfeld gesehen werden.
  _AC-13850 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c699c206)_
* __In Admin Wenn wir versuchen, die Schaltfläche „Bestellung übermitteln“ neu anzuordnen, kann nicht angeklickt werden. (gelegentlich)__
  _AC-14300_
* __[Problem] Setzen Sie den standardmäßigen Indexermodus auf „Zeitplan“__
Alle neuen Indexer befinden sich standardmäßig im **[!UICONTROL Update by Schedule]**.  Zuvor war der Standardmodus **[!UICONTROL Update on Save]**. Bestehende Indexer sind davon nicht betroffen. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
  _AC-6975 - [GitHub-Problem](https://github.com/magento/magento2/issues/36419) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0b410856)_
* __[Problem] Löschen von Indexer-Änderungsprotokolltabellen bei der Abmeldung von mview__
Das System entfernt jetzt automatisch nicht verwendete Änderungsprotokolltabellen, wenn ein Index von „Aktualisierung im Zeitplan“ zu „Aktualisierung beim Speichern“ wechselt. Der Index wird als ungültig markiert, um sicherzustellen, dass keine Einträge übersehen werden. Zuvor würde ein Wechsel eines Index zu „Aktualisierung beim Speichern“ nicht verwendete Änderungsprotokolltabellen im System belassen und alle geänderten Indizes als „gültig“ markieren.
  _AC-7700 - [GitHub-Problem](https://github.com/magento/magento2/issues/29789) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/25859)_
* __Kein Link zum Versand bei Zahlungen an der Kasse in der Mobiltelefonansicht__
Das System stellt jetzt sicher, dass die Checkout-Titel/Links „Versand“ und „Überprüfung und Zahlungen“ immer oben auf der Seite in der mobilen Ansicht sichtbar sind, sodass Benutzende einfach zwischen Schritten navigieren und notwendige Korrekturen vornehmen können. Zuvor waren diese Titel/Links in der mobilen Ansicht ausgeblendet, sodass es für Benutzende schwierig ist, ihren aktuellen Schritt zu kennen oder zu vorherigen Schritten zurückzukehren.
  _AC-7962 - [GitHub-Problem](https://github.com/magento/magento2/issues/36856) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36982)_
* __Die Abfrage der Versandkommentare der Kundenbestellungen CREATED_AT wird in der Zeitzone +0 zurückgegeben, die sich nicht in der konfigurierten Zeitzone des Speichers befindet__
Das System zeigt jetzt bei Verwendung der Abfrage „Kundenbestellungen“ das Feld „created_at“ aus den Versandkommentaren in der konfigurierten Zeitzone des Kunden korrekt an. Zuvor wurde das Feld „created_at“ in der Zeitzone +0 angezeigt, unabhängig von der konfigurierten Zeitzone des Kunden.
  _AC-8109 - [GitHub-Problem](https://github.com/magento/magento2/issues/36947) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37642)_
* __i18n:collect-phrases zerstört die Integrität der Übersetzungen__
Der Befehl `bin/magento i18n:collect-phrases -o` erfasst und fügt nun neue Ausdrücke aus JavaScript- und PHTML-Dateien hinzu, um sicherzustellen, dass die Übersetzungen korrekt in der Übersetzungsdatei wiedergegeben werden. Zuvor konnte das System nicht mehrzeilige Übersetzungsausdrücke aus JavaScript-Dateien und Ausdrücke aus .phtml-Dateien in die Übersetzungsdatei einbeziehen, was zu unvollständigen oder falschen Übersetzungen führte.
  _AC-9843 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Berechtigungsproblem für den Zugriff auf den dynamischen Block__
Zuvor gab es beim Hinzufügen eines neuen dynamischen Blocks für Administratoren mit eingeschränktem Administratorzugriff einen Fehler. Nach der Implementierung dieser Fehlerbehebung kann der eingeschränkte Administrator den dynamischen Block erfolgreich hinzufügen und den Block ohne Fehler bearbeiten
  _ACP2E-2687_
* __Apostroph im Namen der Store-Ansicht wird durch &quot;&amp;#039;__&quot; ersetzt
Die Store-View-Filter des Rasters zeigen jetzt korrekt Apostrophe an
  _ACP2E-2787 - [GitHub-Problem](https://github.com/magento/magento2/issues/38395) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Der Favicon-Upload kann .ico-Dateien nicht validieren__
Der Fehler bei der Dateivalidierung wurde in „Dateivalidierung fehlgeschlagen“ aktualisiert. Überprüfen Sie die Bildverarbeitungseinstellungen in der Store-Konfiguration.“ Zuvor hieß es einfach „Dateivalidierung fehlgeschlagen“.
  _ACP2E-2847 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __In der Galerie in PageBuilder wird die alte Miniaturansicht anstelle des neu hochgeladenen Bildes angezeigt__
Regenerieren Sie Bildvorschauen für Bilder, die gelöscht und mit demselben Namen über die Mediensammlung in Page Builder-Inhalten erneut hochgeladen wurden.
  _ACP2E-2957 - [GitHub-Code-](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/001e5188)_
* __Durch das Speichern eines Produkts durch einen Admin-Benutzer mit einem anderen Rollenbereich werden vorhandene zugehörige Produktinformationen im Produkt überschrieben/gelöscht__
Vor der Fehlerbehebung wurden die zugehörigen Produkte zurückgesetzt und leer, wenn der sekundäre Administrator auf die Schaltfläche Speichern geklickt hat, ohne das zugehörige Produkt zu ändern. Nach dieser Fehlerbehebung klickt der sekundäre Admin-Benutzer auf die Schaltfläche Speichern , das Produkt wird nicht zurückgesetzt und erfolgreich gespeichert.
  _ACP2E-2978 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3056e9cb)_
* __Es können nicht mehr als 200 Bestellungen exportiert werden__
Die Server-Beschränkungen für die Anfragegröße zuvor gesendeter ausgewählter IDs wurden vernachlässigt, indem die HTTP-Anfrage von GET in POST geändert wurde, um das Problem zu beheben. Aufgrund der Serverbeschränkungen für die GET-Anfragengröße trat zuvor das Problem auf.
  _ACP2E-3033 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __Überprüfungsmeldung für Checkout-Seite falsch.__
Wenn ein erforderliches Feld leer gelassen wird, z. B. „Adresse“, zeigt die Server-seitige Validierung die Nachricht nicht an. Die Client-seitige Validierung stellt sicher, dass die Fehlerbenachrichtigung für das erforderliche Feld angezeigt wird, in der steht: „Dies ist ein erforderliches Feld.“ Zuvor wurde zusätzlich zur Client-seitigen Validierungsmeldung die Meldung „Adresse ist erforderlich“ angezeigt, wenn ein erforderliches Feld leer gelassen wurde.
  _ACP2E-3037 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_
* __Problem mit der Vorlage zum Zurücksetzen des Kennworts mit dem Admin-Benutzer__
Das Problem wurde durch Verwendung des richtigen Schlüssels behoben, der jetzt den Admin-Benutzernamen in die E-Mail-Vorlage enthält und den Betreff ordnungsgemäß ausfüllt. Zuvor bestand das Problem aus einem veralteten Schlüssel, der verwendet wurde.
  _ACP2E-3125 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __Doppelte Schrägstriche in der Kundensegment-URL__
Doppelte Schrägstriche werden in der URL nicht angezeigt, wenn im Raster auf „Filter zurücksetzen“ geklickt wird.
  _ACP2E-3149 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Für bestimmte zulässige Länder ist kein Kabeljau verfügbar__
Jetzt ist Cash-on-Delivery für bestimmte zulässige Länder verfügbar, wann immer es erforderlich ist, und   AC-3216 funktioniert erwartungsgemäß.
  _ACP2E-3171 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __Status der benutzerdefinierten erstellten Bestellung kann nicht aktualisiert werden__
&#39;Wir können jetzt den Status der benutzerdefinierten Bestellung aktualisieren, während der Status zuvor nur geändert werden konnte, wenn der aktuelle Status entweder „Verarbeitung läuft“ oder „Betrug“ war.&#39;
  _ACP2E-3178 - [GitHub-Problem](https://github.com/magento/magento2/issues/38659) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Der Status der Versandadresse wird nicht automatisch aktualisiert__
Vor der Fehlerbehebung war die Region der Versandadresse (oder die Regions-ID) nicht mit den Rechnungsinformationen für die Adresse synchronisiert. Jetzt werden sowohl die Versandadressenregion als auch die Regions-ID ordnungsgemäß aktualisiert, wenn die Informationen zur Rechnungsadresse geändert werden.
  _ACP2E-3294 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Die Schaltfläche „Zurücksetzen“ funktioniert nicht beim Hinzufügen/Bearbeiten von Admin-Benutzern__
Zuvor funktionierte die Schaltfläche „Zurücksetzen“ nicht auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“. Jetzt funktioniert die Schaltfläche „Zurücksetzen“ im Admin-Bedienfeld unter „System“ > „Berechtigungen“ > „Alle Benutzer“ auf der Seite „Admin-Benutzer hinzufügen/bearbeiten“ ordnungsgemäß.
  _ACP2E-3364 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_
* __Fehlerkennung und CORS-Fehler beim Routing der Magento-Admin-URL__
Wenn nach der Fehlerbehebung die benutzerdefinierte Admin-Domain eine Subdomain der Hauptdomäne ist, kann auf den Admin nur über die konfigurierte Subdomain zugegriffen werden.
  _ACP2E-3373 - [GitHub-Problem](https://github.com/magento/magento2/issues/37663) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Fehlerhafte Validierung für „Maximal zulässige Menge im Warenkorb“__
Zuvor gab es bei leerem `Maximum Qty Allowed in Shopping Cart` keine Ausnahme, obwohl hier kein leerer Wert akzeptiert wird. Wenn diese Fehlerbehebung angewendet wird, werden beim Einfügen einer leeren Zeichenfolge Ausnahmen ausgelöst, sodass das Produkt nicht gespeichert werden kann.
  _ACP2E-3392 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Problem mit der PageBuilder]Vorschau-Benutzeroberfläche: Die Schaltflächen in der Page Builder-Spalte werden nicht korrekt ausgerichtet__
Die Schaltflächen in den Page Builder-Spalten sind jetzt korrekt ausgerichtet. Zuvor waren sie in den Page Builder-Spalten falsch ausgerichtet.
  _ACP2E-3408 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_
* __Der Bericht „Bestellte Produkte“ wird nicht exportiert. 404-Fehler.__
Der Export von bestellten Produkten in CSV und XML funktioniert jetzt erwartungsgemäß
  _ACP2E-3431 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_
* __TinyMCE JS Error in der Konsole nach JS-Minimierung aktivieren mit Produktionsmodus__
Zuvor wurden durch die Aktivierung der JavaScript-Minimierung im Produktionsmodus im Admin-Bedienfeld JavaScript-Fehler im Zusammenhang mit TinyMCE 6 in der Browser-Konsole angezeigt, was sich auf die Funktionalität und das Benutzererlebnis auswirkte. Dieses Problem wurde nun behoben, sodass TinyMCE 6 reibungslos funktioniert und keine Fehler erzeugt werden, auch wenn die JS-Minimierung aktiviert ist.
  _ACP2E-3457 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/56463d5e)_
* __Antrag auf zusätzliche Änderungen, um die Fehlerbehebung ACP2E-3375 vollständig abzuschließen__
&#39;-
  _ACP2E-3459 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Automatisches Aktivieren neuer ACL-Berechtigungen__
Neue Berechtigungen, die benutzerdefinierten Modulen hinzugefügt wurden, gewähren nicht mehr automatisch Zugriff auf alle vorhandenen Benutzerrollen, es sei denn, sie sind explizit konfiguriert.
  _ACP2E-3503 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Der Benutzerbericht für das Admin-Aktionsprotokoll zeigt keine Details für „adminhtml_user_delete“ an__
Adminhtml_user_delete protokolliert jetzt wichtige Details korrekt. Zuvor wurden keine Protokolle für das Löschen von Benutzern generiert.
  _ACP2E-3509 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4de008a9)_
* __Warenkorbregel, für die beim Aufgeben einer Bestellung vom Administrator keine Versandbedingung angewendet wird__
Wenn die Warenkorb-Preisregel mit dem Coupon einen Rabatt für die Versandmethode aufweist, kann sie zuvor nicht über die Admin-Benutzeroberfläche angewendet werden. Nachdem diese Fehlerbehebung angewendet wurde, wird der Rabatt auf den Warenkorbpreis mit einem Coupon für eine bestimmte Versandmethode erfolgreich von der Admin-Benutzeroberfläche aus angewendet.
  _ACP2E-3536 - [GitHub-Code-](https://github.com/magento/magento2/commit/a52ff98f) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/11ce816b)_
* __[FRESH] HEX-Code wird in SWATCH nicht korrekt aktualisiert__
HEX-Code, der vom Benutzer manuell in die Farbauswahl des visuellen Farb-/Bildmusters eingegeben wird, wird vom System nicht mehr geändert. Zuvor wurden bei bestimmten HEX-Codes aufgrund von Konversionsfehlern zwischen Farbmodellen leichte Anpassungen vorgenommen.
  _ACP2E-3559 - [GitHub-Code-](https://github.com/magento/magento2/commit/344fce23) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/1ef984c0)_

### Admin-Benutzeroberfläche, B2B

* __B2B-Anmeldung als Kunden-Header hat noch das Magento-Branding__
Zuvor wurde in der Kopfzeile der Storefront „You are now connected as &lt;customer name> on &lt;store name>&quot; (Sie sind jetzt als &lt;customer name> verbunden) mit Magento-Branding angezeigt. Was jetzt behoben ist und die Kopfzeile mit ADOBE-Branding angezeigt wird.
  _AC-13628 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/96dec499)_

### Admin-Benutzeroberfläche, Katalog

* __Die Positionen für die Kategorie „Produkte“ auf der zulässigen Website können als Benutzer mit eingeschränktem Administratorzugriff nicht geändert werden__
Erlauben Sie einem Benutzer mit eingeschränktem Administratorzugriff, Produkte unter einer Kategorie hinzuzufügen und zu sortieren, die unter der Stammkategorie enthalten ist, die unter der eingeschränkten Website zugewiesen wurde.
  _ACP2E-2708_

### Admin-Benutzeroberfläche, Zahlungs-/Zahlungsmethoden, Bestellung

* __Die Transaktionsautorisierung wird nach der Bestellung des PayPal-Smart-Buttons nicht auf der Registerkarte Transaktion angezeigt__
Das System zeigt nun die Transaktionsautorisierung auf der Registerkarte Transaktion korrekt an, nachdem eine Bestellung über den PayPal Smart Button aufgegeben wurde. Zuvor wurde die Autorisierungstransaktion nicht auf der Registerkarte Transaktion angezeigt, nachdem auf die Schaltfläche „Autorisieren“ geklickt wurde, und es wurde keine neue Transaktion vom Typ „Autorisierung“ erstellt.
  _AC-13520 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Admin-Benutzeroberfläche, Leistung

* __Nach der Aktualisierung auf 2.4.5-p8 treten beim Erstellen der Bestellung vom Administrator 500 Fehler auf__
Zuvor konnte bei Aktivierung der HTML-Minimierung keine Bestellung vom Administrator aufgegeben werden. Nachdem die HTML-Minimierung aktiviert wurde, kann die Bestellung vom Administrator aufgegeben werden.
  _ACP2E-3169 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_

### Admin-Benutzeroberfläche, Versand

* __Die Anzahl der Couponcodes wird in der   Die Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“, wenn eine Bestellung mit Mehrfachversand aufgegeben wird.__
Zuvor wurde bei einer Bestellung mit mehreren Versandvorgängen die Anzahl der Gutscheincodes nicht in der Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“ aktualisiert. Jetzt wird die richtige Anzahl sowohl in der „Verwendeten Zeit“ angezeigt, die die gewünschten Werte bei Multi-Versand widerspiegelt.
  _ACP2E-2519 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4745100c)_

### Admin-Benutzeroberfläche, Staging und Vorschau

* __[Cloud] Wenn Sie eine Vorlage mit fehlenden Bildern entfernen, wird Pub/Media gelöscht__
Zuvor wurde der Ordner „pub/media“ gelöscht, wenn der Name des Vorschaubilds für eine PageBuilder-Vorlage fehlte. Nach der Korrektur wird nur die Vorlage gelöscht und das Vorschaubild gefunden, falls vorhanden.
  _ACP2E-3424 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/Reporting

* __Google Analytics CSP-Fehler https://region1.analytics.google.com__
Das System lässt jetzt bei aktiviertem Google Analytics korrekt Verbindungen zu &quot;https://region1.analytics.google.com&#39;&quot; zu, wodurch CSP-Fehler (Content Security Policy) verhindert werden. Zuvor führte die Aktivierung von Google Analytics und die Anzeige der Website aus der EU zu CSP-Konsolenfehlern aufgrund einer Weigerung, eine Verbindung zu &quot;https://region1.analytics.google.com&#39;&quot; herzustellen.
  _AC-9922 - [GitHub-Problem](https://github.com/magento/magento2/issues/37750) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38991)_
* __Der erweiterte Bericht funktioniert nicht__
Das System unterstützt jetzt die Generierung von erweiterten Reporting-Datendateien für extragroße Datensätze, indem Berichte in Stapeln von 10.000 geladen und geschrieben werden. Zuvor konnte das Modul für erweiterte Berichterstellung keine Datendateien für besonders große Datensätze generieren, was zu Fehlern von „MySQL Server ist verschwunden“ während der Ausführung des Cron-Auftrags analytics_collect_data führte.
  _ACP2E-2570 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a12063bd)_
* __Problem mit der Sichtbarkeit des Datumsbereichs des vom Administrator bestellten Produktberichts.__
Der Benutzer kann ein beliebiges Datum aus dem Bericht Bestellte Produkte auswählen. Zuvor wird nach einer Tabellenaktualisierung durch die Auswahl von „Von“ das „Bis“-Datum zurückgesetzt.
  _ACP2E-3080 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __Falsche cURL-Kopfzeilen, die dazu führen, dass `newrelic:create:deploy-marker` nicht funktioniert__
Das System formatiert jetzt die cURL-Kopfzeilen korrekt, sodass der `newrelic:create:deploy-marker`-Befehl erfolgreich eine Bereitstellungsmarkierung in New Relic erstellen kann. Zuvor verhinderten falsche cURL-Kopfzeilen die Erstellung einer Bereitstellungsmarkierung in New Relic.
  _ACP2E-3096 - [GitHub-Problem](https://github.com/magento/magento2/issues/37641) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_
* __GTM fehlt das addToCart-Ereignis in dataLayer für ein konfigurierbares Produkt mit benutzerdefinierter Option__
Zuvor wurde das Ereignis „addToCart“ für konfigurierbare Produkte nicht ausgelöst. Jetzt wird das Ereignis ordnungsgemäß zur Datenschichtvariablen GTM hinzugefügt.
  _ACP2E-3146_
* __Das InlineJS-Skript der NewRelic-Browser-Überwachung verursacht CSP-Fehler__
NewRelic-Browser-Überwachungsskripte werden jetzt von der Anwendung anstelle des APM-Agenten eingefügt, um die Einhaltung von CSP (Content Security Policy) zu gewährleisten. Zuvor waren die vom APM-Agent injizierten NewRelic-Browser-Überwachungsskripte nicht konform mit CSP und haben dazu geführt, dass die Skripte nicht ausgeführt wurden.
  _ACP2E-3183 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_
* __Abfragen in die Tabelle sales_bestsellers_aggregated_daily einfügen werden bei einem Projekt mit großem Auftragsvolumen langsam__
Zuvor dauerte es sehr lange, bis der aggregierte Tagesbericht für die Bestseller für ein großes Volumen an aufgegebenen Bestellungen erstellt wurde. Jetzt wird der Bericht rechtzeitig erstellt.
  _ACP2E-3189 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_
* __Bestellungsberichte mit dem falschen Währungssymbol__
Das Währungssymbol für Bestellbeträge im Bestellbericht wurde fälschlicherweise aus Währung/Optionen/Basis übernommen. Es wurde jetzt korrigiert, um Währung/Optionen/Standard für ein genaues Reporting zu verwenden.
  _ACP2E-3276 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Cloud] Falsche Berechnungen im Bericht zur Couponnutzung__
Die Umsatzsumme im Berichtsraster „Coupons“ wird jetzt genau berechnet, indem sowohl der „Rabattsteuerausgleichsbetrag“ als auch der „Versandrabatt-Steuerausgleichsbetrag“ einbezogen werden. Zuvor fehlten diese Beträge in der Berechnung, was zu Diskrepanzen zwischen der Verkaufssumme und den Auftragsdaten führte.
  _ACP2E-3302 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_
* __Probleme mit freigegebenen &quot;&lt;project_id>/var/tmp“__
Temporäre Analytics-Datenexport-Dateien verwenden das sysTmp-Verzeichnis, das für häufigen Zugriff und Änderungen besser geeignet ist. Um Konflikte zu vermeiden, falls mehrere Instanzen auf demselben Server ausgeführt werden, wurde der tmp-Pfad aktualisiert, sodass er die eindeutige ID einer Instanz verwendet
  _ACP2E-3339 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/Reporting, B2B

* __B2B - die Sitemap enthält Produkte/Kategorien, die nicht dem freigegebenen Katalog zugewiesen sind__
Beschränken Sie die von der Sitemap generierten Kategorien und Produkte auf die Kategorien und Produkte, die nur dem öffentlichen freigegebenen Katalog und/oder der Einrichtung der Katalogkategorie zugewiesen sind.
  _ACP2E-2300 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/Reporting, Cloud

* __Magento verwirft die meisten New Relic Cron-Transaktionen #34108__
AC meldet korrekt Cron-auftragsbezogene Transaktionen an NewRelic. Zuvor wurden einige Cron-Job-bezogene Transaktionen als „OtherTransaction/Action/Unknown“ in NR angezeigt
  _ACP2E-3067 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/35b1b1da)_
* __Metrik in NR kann bei Hintergrundtransaktionen irreführend sein - Follow-up von ACP2E-3067__
Hintergrundtransaktionen (Cron) verwenden den in den Konfigurationseinstellungen definierten App-Namen von New Relic
  _ACP2E-3187 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

* __2.4.8-beta102-Paket Enterprise Edition schlägt mit Anwendungsausnahmen fehl__
  _AC-13501_
* __Produkte, die einem freigegebenen Katalog zugewiesen sind, werden bei der Ausführung eines partiellen Index nicht am Frontend angezeigt__
Produkte, die über die REST-API einem freigegebenen Katalog zugewiesen wurden, sind jetzt nach Abschluss der partiellen Indizierung sofort in der Storefront sichtbar. Zuvor waren Produkte nur nach einer vollständigen Neuindizierung sichtbar.
  _ACP2E-2139 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_
* __[Cloud] Preisanzeige in Mobil- und Desktop-Version nicht gleich in „Meine Anführungszeichen“__
Die nicht benötigte Steuerposition „Einschließen“ wird nicht mehr in „Verhandelbares Angebot“ angezeigt, wenn der Abschnitt „Gesamtpreis des Katalogs“ verbraucht ist.
  _ACP2E-2873_
* __Unnötige Rahmen im Abschnitt Meine Bestellungen__
Zuvor wurde ein zusätzlicher Container (Auftragsreferenzen) erstellt, der zusätzliche CSS-Klassen anwandte, was dazu führte, dass unnötige Rahmenlinien unter der Auftragsnummer im Abschnitt Meine Bestellungen angezeigt wurden, der jetzt nicht sichtbar ist.
  _ACP2E-3044 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_
* __sales_clean_quotes cron löscht Angebote aus noch nicht genehmigten Bestellungen__
Angebote, die jetzt in Bestellungen verwendet werden, werden von Sales_clean_quotes Cron-Auftrag nicht gelöscht.
  _ACP2E-3247 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Die Schaltfläche „Bestellung aufgeben“ verschwindet in den Bestelldetails__
Es wurde ein Problem behoben, bei dem die Schaltfläche Bestellung aufgeben für genehmigte Bestellungen ausgeblendet wurde, wenn für eine Produktvariante eine Mindestzahl in der Karte angegeben war
  _ACP2E-3465_
* __[CLOUD] Keine solche Entität mit ID = 0 mit B2B-Modul__
Angemeldeter Benutzer kann Produkt zum Warenkorb hinzufügen, wenn die Funktionen des freigegebenen Katalogs aktiviert sind.
Zuvor führte das Hinzufügen des Produkts zum Warenkorb zu dem Fehler „Keine solche Entität mit ID = 0“
  _ACP2E-3474_
* __Keine Fehlermeldung für unsere Lagerprodukte beim Massenhinzufügen aus der Anforderungsliste angezeigt__
Vor der Fehlerbehebung wurde eine Erfolgsmeldung angezeigt, unabhängig von der Anzahl der Produkte, die nicht zum Warenkorb hinzugefügt werden konnten. Jetzt werden separate Nachrichten für Produkte angezeigt, die dem Warenkorb erfolgreich hinzugefügt wurden, und für Produkte, die fehlgeschlagen sind.
  _ACP2E-3562_
* __Problem mit SKU-Updates nach geplanten Updates, das zu falschen Produktberechtigungen führt (-2 Ablehnen)__
Wenn Sie die SKU eines Produkts mit früheren geplanten Aktualisierungen ändern, ist das Produkt nicht mehr für die freigegebenen Katalogkunden verfügbar, die berechtigt sind, das Produkt zu sehen.
  _ACP2E-3628_

### B2B, Katalog

* __Produkte/Kategorien, die bei der Neuindizierung sichtbar sind, wenn NoDDL- und Kategorieberechtigungen verwendet werden__
Vermeiden Sie die Anzeige in Storefront-eingeschränkten Kategorien und deren Inhalten, während die Indizierung von Katalogberechtigungen durchgeführt wird.
  _ACP2E-2860_

### B2B, Framework

* __Filtern des Unternehmensrasters und anschließender Versuch des CSV-Exports des Rasters schlägt fehl und löst eine Ausnahme aus__
Das System ermöglicht jetzt einen erfolgreichen CSV-Export der Rasterdaten des Unternehmens im Admin-Bedienfeld, auch wenn Filter wie „Ausstehender Saldo“ und „Unternehmenstyp“ angewendet werden. Zuvor führte das Anwenden bestimmter Filter und der Versuch, die Rasterdaten zu exportieren, zu einem Fehler und einer Ausnahme.
  _AC-9607 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B, GraphQL

* __[Cloud] Custom_attributes können bei der Unternehmenserstellung über den GraphQL-Aufruf nicht festgelegt werden__
Nach der Fehlerbehebung ist es möglich, mithilfe einer GraphQL-Anfrage das Attribut „custom_attributes“ für den Unternehmensadministrator bei der Erstellung des Unternehmens festzulegen.
  _ACP2E-3391_

### Braintree

* __Admin Express Checkout Button ist deaktiviert.__
  _AC-14293_
* __Bezahlen Sie per LPM__
Das System stellt jetzt lokale Zahlungsmethoden (LPM) beim ersten Laden korrekt dar, Linear wenn die Liefer- und Abrechnung Adressen eines angemeldeten Kunden nicht übereinstimmen, um einen reibungslosen Checkout-Prozess zu gewährleisten. Bisher verhinderte eine Diskrepanz zwischen der Versand- und der Abrechnung Adresse eines Kunden das Rendern von LPM, was zu potenziellen Unterbrechungen während der Checkout führte.
  _BÜNDEL-3367_
* __Konfigurierbar mit &quot;Virtuell als untergeordnetes Produkt&quot;__
Das System ermöglicht nun Express-Zahlungsmethoden für konfigurierbare Produkte, die ein virtuelles untergeordnetes Produkt haben, und sorgt so für einen reibungslosen Checkout-Prozess. Bisher waren Expresszahlungsmethoden nicht verfügbar, wenn ein konfigurierbares Produkt mit einem virtuellen untergeordneten Produkt zur Warenkorb hinzugefügt wurde.
  _BÜNDEL-3368_
* __Fehler bei CVV-Überprüfung fehlgeschlagen__
  _BÜNDEL-3369_
* __Sprung über den Konto Bereich Probleme 247__
Das System ermöglicht es Kunden nun, neue Karte zu speichern oder Konto Informationen über mehrere Websites hinweg zu PayPal, ohne auf Autorisierung Fehler zu stoßen. Zuvor konnten Kunden keine neuen Zahlungsmethoden auf verschiedenen Websites speichern und erhielten eine Autorisierungsfehlermeldung.
  _BUNDLE-3370_
* __Lieferadresse eines anderen Landes__
Das System ermöglicht jetzt die fehlerfreie Verarbeitung von Transaktionen beim Versand an eine Adresse aus einem anderen Land und gewährleistet so einen reibungslosen Checkout-Prozess. Zuvor führte der Versuch, eine Adresse aus einem anderen Land zu versenden, zu Konsolenfehlern, obwohl keine sichtbaren Fehler im Frontend vorhanden waren.
  _BUNDLE-3371_
* __Kreditkarte - Zerlegung__
Das System verarbeitet jetzt den Zerfall von Braintree PayPal-Komponenten korrekt, wenn ein Kunde von der Zahlungsseite zur Versandseite zurückkehrt, um Fehler zu vermeiden und sicherzustellen, dass die PayPal Express-Schaltflächen korrekt dargestellt werden. Zuvor führte die Rückkehr von der Zahlungsseite zur Versandseite manchmal zu einem Fehler, wenn versucht wurde, die Braintree-PayPal-Komponenten zu zerlegen.
  _BUNDLE-3372_
* __Versandrückruf für PayPal Express__
Das System zeigt jetzt die verfügbaren Versandmethoden korrekt im PayPal Express-Modal an, sodass Kunden ihre bevorzugte Versandmethode auswählen können, bevor sie zur Überprüfungsseite wechseln oder ihre Transaktion abschließen. Zuvor waren im Modal „PayPal Express“ keine Versandmethoden verfügbar, sodass Kunden eine Versandmethode auf einer separaten Überprüfungsseite auswählen mussten, bevor sie ihre Transaktion abschließen konnten.
  _BUNDLE-3373_

### Bündel

* __Fehlermeldung bei der Validierung des Storefront-Bundles mit Checkbox-Konfiguration ist größer als 1__
Das System zeigt jetzt nur noch eine Validierungsfehlermeldung an, wenn die Schaltfläche „Zum Warenkorb hinzufügen“ angeklickt wird, ohne dass Kontrollkästchen-Optionen für ein gebündeltes Produkt ausgewählt werden. Zuvor zeigte das System mehrere Validierungsfehlermeldungen für jedes nicht ausgewählte Kontrollkästchen an.
  _AC-10826 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ea26621)_
* __Magento-Ausnahme in einigen Testfällen mit Bezug zur Reihenfolge ausgelöst__
Das System verarbeitet den Schritt „sendGuestPaymentInformation“ jetzt in verschiedenen Testfällen korrekt, wodurch das Auslösen von Magento-Ausnahmen verhindert wird. Zuvor traten diese Ausnahmen aufgrund einer Null-Zahlungsmethode auf, was in mehreren Testfällen zu Fehlern führte.
  _AC-13321_

### Warenkorb und Checkout

* __Ausnahme wird beim Hinzufügen eines Produkts zum Warenkorb auf der Seite „Produkt vergleichen“ nicht ordnungsgemäß verarbeitet__
Das System verarbeitet jetzt Ausnahmen ordnungsgemäß, wenn ein Produkt von der Seite Produkt vergleichen zum Warenkorb hinzugefügt wird und eine Meldung des Nachrichten-Managers im Controller angezeigt wird. Zuvor führte eine Ausnahme dazu, dass eine JSON-codierte Seite zurückgegeben wurde, anstatt ordnungsgemäß erfasst und verarbeitet zu werden.
  _AC-10660 - [GitHub-Problem](https://github.com/magento/magento2/issues/38200) - [GitHub-Code-](https://github.com/magento/magento2/pull/38257) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __GTag sendet keine Transaktionspreise und -summen.__
Das System sendet jetzt die Transaktionspreise und -summen korrekt an das Google-Tag, wenn das GT-Tag aktiviert ist, was eine genaue Verfolgung der E-Commerce-Daten gewährleistet. Zuvor wurde die Währung fälschlicherweise als Teil der „All“-Bestellungen gesendet, anstatt mit der einzelnen Bestellung verknüpft zu werden.
  _AC-10698 - [GitHub-Problem](https://github.com/magento/magento2/issues/37348) - [GitHub-Code-](https://github.com/magento/magento2/pull/37504) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37349)_
* __[Problem] [Checkout] Abhängigkeitsrichtlinien in der fehlgeschlagenen E-Mail-Zahlungsvorlage aktualisiert__
Das System lässt nun bei virtuellen Produkten die Lieferadresse und Versandmethode in der Vorlage für fehlgeschlagene Zahlungen korrekt aus, sodass die E-Mail nur relevante Informationen enthält. Zuvor enthielt die fehlgeschlagene Zahlungs-E-Mail für virtuelle Produkte fälschlicherweise die Versandadresse und die Versandmethode.
  _AC-11641 - [GitHub-Problem](https://github.com/magento/magento2/issues/32781) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32511)_
* __Magento 2 Melden Sie sich beim Checkout mit dem Fehler „Bestehender Kunde gibt Konsole“ im Firefox-Browser an__
Das System ermöglicht es Benutzern jetzt, sich während des Checkout-Prozesses anzumelden, ohne dass im Firefox-Browser Konsolenfehler auftreten. Zuvor führte der Versuch, sich während des Checkouts als bestehender Kunde anzumelden, zu einem Konsolenfehler in Firefox.
  _AC-11717 - [GitHub-Problem](https://github.com/magento/magento2/issues/38557) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39509)_
* __[Problem] Regression der Verkaufsregeln in 2.4.7__
Das System validiert nun die Verkaufsregeln korrekt und verhindert die Anwendung eines Gutscheincodes auf einen Warenkorb, wenn die Produktbedingung mit keinem Produktnamen übereinstimmt. Zuvor konnte eine Verkaufsregel angewendet und ein Rabatt auf den Versandbetrag gewährt werden, selbst wenn die Produktbedingung mit keinem Produktnamen übereinstimmte.
  _AC-11876 - [GitHub-Problem](https://github.com/magento/magento2/issues/38671) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_
* __[Problem] Verkaufsregel WarenkorbFeste Berechnung : Falscher Rabattbetrag__
Das System berechnet nun den Rabattbetrag für Verkaufsregeln mit festen Warenkorbbeträgen korrekt und stellt sicher, dass genaue Rabatte unabhängig von Änderungen an den Warenkorbartikeln angewendet werden. Zuvor konnte der Rabattbetrag falsch variieren, wenn Artikel im Warenkorb geändert wurden, was manchmal zu erheblich größeren Rabatten als erwartet führte.
  _AC-11914 – [GitHub-Problem](https://github.com/magento/magento2/issues/38694) – [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __[Problem:] Der Loader blockiert die Versandarten, nachdem die Postleitzahl, die Versandkosten Tauglichkeitsprüfung die Regeln__ geändert wurden
Das System behandelt nun benutzerdefinierte Versandmethoden ohne Versandkosten Tauglichkeitsprüfung Regeln korrekt und stellt sicher, dass der Verlader die Versandmethoden nicht blockiert, nachdem die Postleitzahl in der Lieferadresse während des Checkout geändert wurde. Bisher führte die Änderung der Postleitzahl in der Lieferadresse während der Checkout dazu, dass der Loader die Versandmethoden blockierte und nicht verschwand, wenn benutzerdefinierte Versandmethoden ohne Versandkosten Tauglichkeitsprüfung Regeln verwendet wurden.
  _AC-11993 - [GitHub-Problem](https://github.com/magento/magento2/issues/38742) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_
* __Die Coupon-Code-Funktion funktioniert im Checkout Seite bei Magento 2.4.7__ nicht richtig
Das System aktiviert jetzt das Eingabefeld Rabattcode/Coupon auf der Checkout Seite für virtuelle und herunterladbare Produkte, sodass Benutzer Rabattcodes wie erwartet anwenden können. Zuvor war die Eingabe des Rabattcodes/Coupons deaktiviert und der Text des Schaltflächentitels wurde als „Coupon abbrechen“ angezeigt, was Benutzer daran hinderte, Rabattcodes anzuwenden.
  _AC-12170 - [GitHub-Problem](https://github.com/magento/magento2/issues/38826) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_
* __Das Kontrollkästchen „Allgemeine Geschäftsbedingungen“ lässt HTML in der Storefront nicht zu__
Das System unterstützt jetzt die Formatierung von HTML im Checkbox „Geschäftsbedingungen“ auf der Storefront, was eine bessere Anpassung und Lesbarkeit ermöglicht. Zuvor wurde der Checkbox-Text im Nur-Text-Format angezeigt, wobei alle verwendeten HTML-Tags ignoriert wurden.
  _AC-12479 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __Die für einen angemeldeten Benutzer erstellte Warenkorbpreisregel wird fälschlicherweise für einen nicht angemeldeten Benutzer angewendet__
Das System entfernt jetzt die Warenkorb-Preisregel für angemeldete Benutzer korrekt, wenn sie aufgrund des Cookie-Ablaufs automatisch abgemeldet werden, sodass der Rabatt nicht auf nicht angemeldete Benutzer angewendet wird. Zuvor wurde die Regel zum Warenkorbpreis auch dann angewendet, wenn sich der Benutzer abgemeldet hatte, was dazu führte, dass auf nicht angemeldete Benutzer ein falscher Rabatt angewendet wurde.
  _AC-12541 - [GitHub-Problem](https://github.com/magento/magento2/issues/38944) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_
* __[Problem] [FUNKTION] Leistungsoptimierung großer Warenkörbe durch…__
Das System optimiert jetzt die Leistung für große Warenkörbe, indem doppelte getActions-Aufrufe verhindert werden, was die Geschwindigkeit und Effizienz von Warenkorbvorgängen erhöht. Zuvor wurde bei einem Warenkorb mit mehreren Artikeln die getActions-Funktion mehrmals aufgerufen, was die Systemleistung verlangsamte.
  _AC-13302 - [GitHub-Problem](https://github.com/magento/magento2/issues/39292) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39290)_
* __Geschenkregistrierungs-Produkt wird nicht richtig angezeigt__
  _AC-13797_
* __Geschenkregistrierungs-Produkt wird nicht richtig angezeigt__
  _AC-13841_
* __Umsatzsteuer in der Adressausgabe__
Das System ermöglicht nun die Übersetzung des Textes „VAT“, „T“, „F“ in den Adressrenderern, sodass die Benutzer diese Begriffe in die spezifische Sprache des Ladens übersetzen können. Zuvor waren diese Begriffe nicht übersetzbar, was die Benutzer dazu zwang, eine Problemumgehung anzuwenden.
  _AC-8103 - [GitHub-Problem](https://github.com/magento/magento2/issues/36942) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36943)_
* __Doppelte Bestellungen mit derselben Angebots-ID gleichzeitig mit wenig Zeitunterschied__
Es wurde ein Problem behoben, bei dem Adobe Commerce-Kunden auf doppelte Bestellungen stießen, die mit derselben QuoteID aufgegeben wurden
  _ACP2E-2055 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Beständiger Warenkorb beim Checkout geleert__
Nach der Behebung wird die persistente Sitzung nicht beendet, wenn Sie die Zahlungsmethode während des Checkouts auswählen, während Sie nicht angemeldet sind.
  _ACP2E-2470 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __Reorder fügt nicht zugewiesene Produkte zum Warenkorb hinzu__
Zuvor konnten für die verschiedenen Stores Produkte vom anderen Store nachbestellt werden. Nachdem diese Fehlerbehebung nur auf denselben Store angewendet wurde, kann dasselbe Produktumfang neu bestellt werden, wenn die Kundenkontofreigabe aktiviert ist
  _ACP2E-2518 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_
* __In Admin wird der „Warenkorb“ auf der linken Seite nicht aktualisiert, wenn Sie die Artikel auswählen und „Zum Warenkorb wechseln“ auf der rechten Seite__
Der „Warenkorb“ auf der linken Seite wird aktualisiert, wenn Sie die Artikel auswählen und „Zum Warenkorb wechseln“ auf der rechten Seite in der Admin-Seite. Zuvor funktionierte diese Funktion nicht, da die umgewandelten Warenkorbelemente nicht aus der Sitzung leer wurden.
  _ACP2E-2620 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __[Cloud] Verkaufsregel nicht auf die erste Bestellung von Multi-Shipping angewendet__
Nach der Fehlerbehebung wird der Rabatt für jede Bestellung desselben Multi-Shipping-Angebots korrekt angezeigt.
  _ACP2E-2646 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_
* __[Cloud] Produktionsanfragen zum Hinzufügen desselben Produkts zum Warenkorb führen zu zwei separaten Elementen in der Warenkorb-REST-API__
Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte das parallele Anfordern desselben Produkts über die REST-API zum Warenkorb, zu mehreren Zeileneinträgen für dieselbe SKU.
  _ACP2E-2664 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Problem mit der Bestellung über Gift Registry Magento 2.4.4 Enterprise/Commerce__
Das Problem, das den erfolgreichen Kauf eines Produkts aus einer Geschenkregistrierung verhindert, wurde behoben, sodass Bestellungen aufgegeben und die Geschenkregistrierung entsprechend aktualisiert werden kann. Zuvor ist beim Versuch, eine Bestellung über eine Geschenkregistrierung aufzugeben, ein Fehler aufgetreten, der den Abschluss des Kaufs verhindert hat.
  _ACP2E-2676 - [GitHub-Problem](https://github.com/magento/magento2/issues/35432)_
* __Das Cookie kann nicht gesendet werden. Größe von „image-messages“ beim Versuch, eine Neuanordnung vorzunehmen__
Der Neuanordnungsprozess erzeugt jetzt keine eigenen Fehler. Dies beruht auf der Auflistung der in den Warenkorb integrierten Artikelprüfungen.
  _ACP2E-2704 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Die Standard-Versandadresse ist beim Checkout nicht ausgewählt__
Die standardmäßige Versandadresse wird jetzt im Kontext der aktivierten Adresssuche für das Ereignis ausgewählt.
  _ACP2E-2798 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD] GraphQL addProductsToCart API-Problem mit benutzerdefinierter Option__
GraphQL fügt dasselbe Produkt mit verschiedenen benutzerdefinierten Optionen korrekt in den Warenkorb
  _ACP2E-2897 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_
* __[Cloud] Regeln für verwandte Produkte funktionieren nicht beim Ändern der Store-Ansicht__
Das Problem wurde behoben, indem bestätigt wurde, dass der benutzerdefinierte Eigenschaftswert erfolgreich auf der Warenkorbseite empfangen wurde. Zuvor wurde es beim Wechseln zwischen Stores auf der Warenkorbseite für Storefronts nicht richtig abgerufen.
  _ACP2E-2917_
* __Mehrere Adressen wurden dem Konto beim Checkout als neuer Kunde hinzugefügt__
Das System speichert jetzt eine neue Kundenadresse nur einmal, wenn die Bestellung nicht erstellt werden konnte, wodurch die Erstellung mehrerer identischer Adressen im Falle von Fehlern bei der Bestellplatzierung verhindert wird. Zuvor speicherte das System jedes Mal eine neue Adresse, wenn ein Bestellplatzierungsversuch unternommen wurde, unabhängig davon, ob der Auftrag erfolgreich erstellt wurde oder nicht.
  _ACP2E-2923 - [GitHub-Code-](https://github.com/magento/magento2/commit/001e5188) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/2ebcef39)_
* __Die Neuanordnung einer Kundenbestellung über ein Gastbestellungsformular führt zu einem leeren Warenkorb__
Zuvor wurde der Kunde bei der Neubestellung über die Seite Bestellungen und Rücksendungen zur Anmeldeseite weitergeleitet. Nachdem diese Fehlerbehebung angewendet wurde, wird der registrierte Kunde bei der Neubestellung korrekt zur Seite Warenkorb anzeigen weitergeleitet. Der Fluss funktioniert genauso wie bei Gastkunden.
  _ACP2E-3004 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_
* __Admin-Benutzer mit eingeschränkten Rollenressourcen kann den Warenkorb nicht anzeigen__
Zuvor konnte der Administrator mit Zugriffsbeschränkung den abgebrochenen Warenkorb im Admin-Bedienfeld für eine zugehörige Website nicht sehen. Nachdem diese Fehlerbehebung angewendet wurde, kann der eingeschränkte Administrator den Transaktionsabbruch im Admin-Bedienfeld einsehen.
  _ACP2E-3025 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d1f7dc95)_
* __[Cloud] Schnellbestellung große SKU-Leistung__
Die Checkout-Leistung wurde verbessert, wenn in den Warenkorbpreisregeln verwendete Attribute nicht für alle Produkte vorhanden sind und die MAP-Funktion (Minimum Advertised Price) aktiviert ist.
  _ACP2E-3176 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_
* __Duplizierte Artikel im Warenkorb__
Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte die parallele Anforderung, dasselbe Produkt zum Warenkorb in der Storefront hinzuzufügen, zu mehreren Zeileneinträgen für dieselbe SKU.
  _ACP2E-3211 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_
* __Die E-Mail-Bestätigung für die Kaufbestätigung wird an die im Vor-/Nachnamen angegebenen E-Mails gesendet__
Die E-Mail-Bestätigung für die Kaufbestätigung, die zuvor gesendet wurde, als ein E-Mail-ähnliches Muster in die Felder Vor- und Nachname eingegeben wurde, wird nicht mehr gesendet.
  _ACP2E-3296 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_
* __Das Formular für die Checkout-Versandadresse wird mit einer falschen Adresse aktualisiert__
shippingAddressFromData wird jetzt pro Website im lokalen Speicher gespeichert. Zuvor konnte eine Adresse von der falschen Website während des Checkouts automatisch in das Versandadressenformular eingefügt werden, wenn ein Store-Code in der URL verwendet wurde und der Checkout von mehreren Websites während derselben Gastsitzung initiiert wurde.
  _ACP2E-3402 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD] Beim Checkout wird die ausgewählte Rechnungsadresse nicht beibehalten, wenn die Adresssuche aktiviert ist__
Die Zahlungsseite des Checkouts behält jetzt die ausgewählte Rechnungsadresse bei, wenn die Adresssuche aktiviert ist. Wenn zuvor „Limit für Kundenadressen“ auf 1 konfiguriert wurde und der Kunde über mehr als eine Adresse verfügt, verschwindet die ausgewählte Rechnungsadresse nach dem Neuladen der Seite.
  _ACP2E-3405_
* __Geschenkkartenprodukt | Beim Zusammenführen des Warenkorbs werden Geschenkgutscheine zusammengeführt__
Geschenkkartenprodukte wurden jetzt korrekt im Warenkorb zusammengeführt
  _ACP2E-3407 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_
* __Die Warenkorbpersistenz wird beim Abmelden nicht eingehalten__
Es wurde eine Funktion hinzugefügt, mit der ich mich von der Kundenanmeldung zum Authentifizierungs-Popup und zur Checkout-Anmeldung erinnere.
  _ACP2E-3415 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/344fce23)_
* __Vorhandene Anführungsdaten werden nicht aktualisiert/nicht angezeigt. Erstellen Sie stattdessen einen neuen Anführungseintrag, wenn Trigger_recollect = 1 ist__
Die Artikel im Warenkorb des Kunden verschwinden nicht mehr, weil ein Produkt gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde.
  _ACP2E-3488 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_
* __Wenn ein Geschenkartikel gekauft wird, sieht der Kunde Artikel, die nicht in seiner Registrierung enthalten sind__
Das Update der Geschenkregistrierung enthält keine Elemente mehr, die nicht zur Geschenkregistrierung gehören.
  _ACP2E-3495_
* __[Cloud] Problem mit dem Bestätigungs-Popup „Alle entfernen“ Das Entfernen von Artikeln des Warenkorbs ohne Bestätigung__
Wenn Sie jetzt bei Produkten, für die besondere Aufmerksamkeit erforderlich ist, auf die Schaltfläche „Alle entfernen“ klicken, wird ein Bestätigungs-Popup angezeigt, um sicherzustellen, dass Elemente nur mit Ihrer Bestätigung entfernt werden. Zuvor wurden Elemente sofort ohne Bestätigung entfernt
  _ACP2E-3510_
* __[CLOUD] Funktion der Schaltfläche neu anordnen__
Wenn Sie eine Bestellung im Administratorbereich neu bestellen, werden jetzt Produkte mit Lager zum Angebot hinzugefügt, auch wenn es einige Produkte in der ursprünglichen Bestellung gibt, die nicht mehr vorrätig sind. Vor der Fehlerbehebung wurden keine Produkte zum neuen Angebot hinzugefügt, wenn Produkte ohne Lager in der ursprünglichen Bestellung waren.
  _ACP2E-3618 – [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a52ff98f)_
* __Suchvorgänge funktionieren nicht nach Postleitzahl__
Die Suche nach Abholorten per Postleitzahl funktionierte bei niederländischen Lokalisierungen nicht ordnungsgemäß. Nach der Fehlerbehebung liefert die Suche nach dem Abholort Ergebnisse basierend auf der Postleitzahl.
  _ACP2E-3622 – [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/344fce23)_

### Warenkorb und Kasse, Kasse/One Seite Kasse

* __[Das Feld &quot;Zufällige BUG-E-Mail] &quot; wird nicht gerendert oder es dauert lange, bis es im Checkout-, Versand- oder Zahlungs-Seite__ angezeigt wird
Commerce rendert das **[!UICONTROL Email]** Feld jetzt auf den Checkout Versand- und Zahlungsseiten wie erwartet. Zuvor war dieses Feld entweder nicht vorhanden oder wurde nur langsam gerendert.
  _AC-9386 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e1babcfd)_

### Warenkorb und Checkout, Bestellung

* __Datumsauswahl für ein Produkt mit mehreren anpassbaren Optionen, bei denen Datumsfelder bei der Bestellung durch den Administrator nicht funktionieren__
Das System zeigt jetzt bei der Konfiguration eines Produkts mit mehreren anpassbaren Datumsoptionen im Prozess zur Erstellung von Admin-Aufträgen die Datumsauswahl für alle Datumsfelder korrekt an. Zuvor wurde die Datumsauswahl nur für das erste Datumsfeld angezeigt, sodass die verbleibenden Felder keine Datumsauswahl aufweisen.
  _ACP2E-3097 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_

### Warenkorb und Checkout, Versand

* __Sofortkauf „Günstigster Versand“ bei konfigurierbaren Produkten defekt__
Die Funktion Instant Purchase wählte fälschlicherweise die teurere In-Store-Lieferoption für konfigurierbare Produkte anstelle der günstigsten Pauschalmethode aus. Durch diese Fehlerbehebung wird sichergestellt, dass die richtige Versandmethode auf der Grundlage des tatsächlichen Preises ausgewählt wird.“
  _AC-12119 - [GitHub-Problem](https://github.com/magento/magento2/issues/38811) - [GitHub-Code-](https://github.com/magento/magento2/pull/38819) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/29fe9097)_

### Katalog

* __Bereinigung der Datenbanktabelle cron_schedule bereinigt keine nicht vorhandenen Aufträge__
Das System bereinigt jetzt automatisch die Datenbanktabelle cron_schedule und entfernt Einträge für Aufträge, die nicht mehr im System vorhanden sind. Dadurch wird eine optimale Leistung gewährleistet, indem eine minimale Anzahl von Zeilen in der Tabelle beibehalten wird. Zuvor wurden Einträge für Aufträge von inaktiven oder entfernten Modulen nicht bereinigt, was zu einer unnötigen Datenakkumulation in der cron_schedule-Tabelle führte.
  _AC-10910 - [GitHub-Problem](https://github.com/magento/magento2/issues/38217) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38693)_
* __Der Stufenpreis wird nicht aus dem konfigurierbaren Produkt gelöscht__
Das System entfernt nun den Stufenpreis eines Produkts korrekt, wenn es von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wird, wodurch eine genaue Preisanzeige im Frontend gewährleistet ist. Zuvor wurde der Stufenpreis eines konfigurierbaren Produkts nicht gelöscht, wenn ein Produkt von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wurde, was zu einer Diskrepanz beim angezeigten Preis führte.
  _AC-10953 - [GitHub-Problem](https://github.com/magento/magento2/issues/38390) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38427)_
* __Kategoriebeschreibung WYSIWYG ist in der nicht standardmäßigen Storeview leer__
Das System speichert jetzt die Kategoriebeschreibung korrekt im WYSIWYG-Editor und zeigt sie an, wenn eine Kategorie auf der Store-Ansichtsebene bearbeitet wird. Zuvor war der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer.
  _AC-11804 - [GitHub-Problem](https://github.com/magento/magento2/issues/38622) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38623)_
* __Konfigurierbare Produkte können nicht mit einem Kontrollkästchen neu angeordnet werden, für das eine benutzerdefinierte Option ausgewählt wurde__
Das System verarbeitet jetzt die Neuanordnung von konfigurierbaren Produkten mit einer einzigen ausgewählten benutzerdefinierten Checkbox-Option korrekt, was eine erfolgreiche Warenkorberstellung ermöglicht. Zuvor führte der Versuch, solche Produkte neu zu bestellen, zu einem Fehler und verhinderte, dass Artikel zum Warenkorb hinzugefügt wurden.
  _AC-11970 - [GitHub-Problem](https://github.com/magento/magento2/issues/38736) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1d144bce)_
* __[Problem] Korrigieren Sie den Wortlaut des Filterelements in der mehrschichtigen Navigation__
Das System verwendet jetzt korrekt die Wörter „Element“ und „Elemente“ im Filterelement für die mehrschichtige Navigation, wodurch die Klarheit und Genauigkeit der Filterbeschreibungen verbessert wird. Zuvor wurden diese Wörter falsch verwendet, was zu Verwirrung bei Benutzenden führen kann, die in den Filteroptionen navigieren.
  _AC-12076 - [GitHub-Problem](https://github.com/magento/magento2/issues/38789) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37852)_
* __Format für Datum und Uhrzeit für benutzerdefinierte Option funktioniert nicht__
Das System wendet das konfigurierte Datumsformat jetzt korrekt auf benutzerdefinierte Produktoptionen des Typs Datum an, um sicherzustellen, dass das Datumsformat im Frontend korrekt angezeigt wird. Zuvor spiegelten Änderungen an der Datumsformatkonfiguration das Frontend für benutzerdefinierte Optionen des Typs Datum nicht wider.
  _AC-12164 - [GitHub-Problem](https://github.com/magento/magento2/issues/32990) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38925)_
* __Dropdown-Optionen fehlen__
Das System zeigt jetzt alle Werte in der Dropdown-Liste korrekt an, wenn ein neues Attribut mit mehr als 20 Werten erstellt wird. Zuvor wurden nur die ersten 20 Werte oder andere ausgewählte Seitenwerte angezeigt, wodurch die verbleibenden Werte fehlten.
  _AC-13068 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problem] Aktuelle Sore-ID für Laufzeitcache der Kategorie verwenden__
Das System verwendet jetzt die aktuelle Speicher-ID für den Laufzeitcache der Kategorie korrekt, um zu verhindern, dass Daten überschrieben werden, wenn die Emulation verwendet wird oder benutzerdefinierter Code die Kategorie in verschiedenen Stores speichert. Zuvor stammte das in der Laufzeit gespeicherte Objekt möglicherweise aus dem falschen Speicher, was zu einer Datenüberschreibungen führte.
  _AC-13296 - [GitHub-Problem](https://github.com/magento/magento2/issues/39310) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36394)_
* __bin/magento sampledata:deploy —no-update löst eine Ausnahme aus__
Das System akzeptiert jetzt bei Verwendung der Option —no-update im Befehl sampledata:deploy korrekt einen booleschen Wert, wodurch Fehler bei der Bereitstellung von Beispieldaten vermieden werden. Zuvor wurde bei der Verwendung dieses Befehls ein Fehler ausgelöst, da das System fälschlicherweise einen ganzzahligen Wert erwartet hatte.
  _AC-13324 - [GitHub-Problem](https://github.com/magento/magento2/issues/39344) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39345)_
* __[Problem] Behebung der Verwendung des EAV-Cache-Typs__
Das System verwendet jetzt den EAV-Cache-Typ an allen relevanten Stellen korrekt, um ein konsistentes und effizientes Daten-Caching sicherzustellen. Zuvor wurde der EAV-Cache-Typ nicht konsistent verwendet, was zu potenziellen Ineffizienzen und Inkonsistenzen bei der Datenzwischenspeicherung führte.
  _AC-13355 - [GitHub-Problem](https://github.com/magento/magento2/issues/32322) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31264)_
* __Die erweiterte Katalogsuche mit leeren Daten wird in die Verzweigung für Suchergebnisse [.2.4.dev verschoben]__
Das System speichert Benutzer jetzt korrekt auf der Seite Erweiterte Suche und zeigt eine Fehlermeldung an, wenn sie versuchen, eine Suche durchzuführen, ohne Daten einzugeben. Zuvor wurden Benutzer bei einer leeren Suche zur Seite für die erweiterte Katalogsuche weitergeleitet, wobei eine Meldung angezeigt wurde, die sie aufforderte, ihre Suche zu ändern.
  _AC-13596 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __[Problem] Produkt-Layout basierend auf attribute_set__
Das System ermöglicht jetzt die Anpassung des Produkt-Layouts auf der Grundlage des Attributsatzes und bietet so eine praktischere und effizientere Möglichkeit, die Produktanzeige im Frontend-Store zu verwalten. Zuvor konnte das Layout nur nach SKU oder Produktarten angepasst werden, was für viele Produkte oder bestimmte Artikel nicht immer praktisch war.
  _AC-13622 - [GitHub-Problem](https://github.com/magento/magento2/issues/38790) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36244)_
* __Fehlender eindeutiger Schlüssel in der Tabelle eav_attribute_option_value__
Das System enthält jetzt einen eindeutigen Schlüssel in den Spalten „option_id“ und „store_id“ in der Tabelle „eav_attribute_option_value“, was verhindert, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hat. Zuvor konnte ein fehlerhafter Code dazu führen, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hatte, was Probleme bei der Bearbeitung von Produkten oder Attributen verursachte.
  _AC-6738 - [GitHub-Problem](https://github.com/magento/magento2/issues/24718) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/28796)_
* __[Problem] Verwenden Sie die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte__
Das System verwendet jetzt die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte, was die Modularität verbessert. Zuvor wurden im Produkt-Indexer der Kategorie hartcodierte Werte verwendet, was die Flexibilität und Anpassungsfähigkeit einschränkte.
  _AC-8297 - [GitHub-Problem](https://github.com/magento/magento2/issues/37200) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37199)_
* __Der Währungs-Code ändert sich nicht im Widget „Neues Produkt“__
Das System aktualisiert jetzt den Währungs-Code im Widget Neues Produkt korrekt, wenn die Währung im Frontend geändert wird, und stellt so die Konsistenz der Währungsanzeige auf der Website sicher. Zuvor hatte das Ändern der Währung im Frontend keine Auswirkungen auf den Währungs-Code, der im Widget Neues Produkt angezeigt wird.
  _AC-9375 - [GitHub-Problem](https://github.com/magento/magento2/issues/37898) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37899)_
* __Regulärer Preis wird nicht auf PLP für konfigurierbares Produkt angezeigt__
Der reguläre Preis wird jetzt auf den Produktlistenseiten für konfigurierbare Produkte angezeigt, die untergeordnete Produkte mit Sonderpreis enthalten.
  _ACP2E-2224 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __Lagerinformationen werden im visuellen Merchandising-Raster nicht richtig angezeigt__
Der Lagerbestand wird jetzt entsprechend dem ausgewählten Geschäft angezeigt.
  _ACP2E-2478 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/bdbf97ea)_
* __Widget-Inhalte werden auf der CMS-Seite nicht aktualisiert__
Das System aktualisiert jetzt den Widget-Inhalt auf einer CMS-Seite, wenn ein Produkt als neu festgelegt und gespeichert wird, und stellt sicher, dass die Seite die aktualisierte Produktsammlung anzeigt. Zuvor wurde die Seite aufgrund der falschen Cache-Identitäten, die für das Widget im Cache verwendet wurden, nicht aktualisiert, um das neue Produkt anzuzeigen.
  _ACP2E-2621 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Probleme beim Speichern erweiterter Preise für Bundle-Produkte__
Leistungsverbesserung durch Einsparung von Produkten im Paket
  _ACP2E-2630 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __[On-Premise] Der Neuindizierungsprozess ist beim Erstellen von Katalogpreisregeln ineffizient__
Durch das Speichern der Katalogpreisregel werden Indexer nicht ungültig, sondern nur die betroffenen Produkte neu indiziert
  _ACP2E-2652 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Aktualisieren der Uhrzeit von Produktattributen vom Typ Datum und Uhrzeit über den CSV-Import__
Jetzt verfügen Datums-/Uhrzeitattribute über einen Zeitanteil in den exportierten Daten. Es ist auch möglich, die Zeit für solche Attribute mithilfe des Imports zu aktualisieren. Auch wenn „Einschließungsfelder“ aktiviert ist, werden Attributwerte in der Spalte „additional_attributes“ in doppelte Anführungszeichen gesetzt.
  _ACP2E-2679 - [GitHub-Problem](https://github.com/magento/magento2/issues/38306) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Keine entsprechende Fehlermeldung, wenn die Website-ID in der Anfrage falsch ist__
Jetzt wurde die entsprechende Fehlermeldung hinzugefügt, die angezeigt wird, wenn die Website-ID in der Anfrage falsch ist. Zuvor gab es keine Validierung, wenn die Website-ID in der Anfrage falsch war.
  _ACP2E-2689 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Das Produktbild geht verloren, nachdem ein vorhandenes geplantes Update gelöscht wurde, das sich nicht auf das Bild auswirkt__
Produktbilder werden beim Löschen der Staging-Aktualisierung nicht entfernt.
  _ACP2E-2785 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_
* __[Cloud] Falscher Bundle-Produktpreis bei Verwendung mit Stufenpreisen__
Zuvor wurden bei der Berechnung bestimmter prozentualer Rabatte, gerundet auf 2 Dezimalpunkte, unterschiedliche Endpreise für die Warenkorb- und Produktlistenseite/Produktdetailseite ermittelt. Nachdem diese Fehlerbehebung angewendet wurde, ist der Endpreis für das Bundle-Produkt derselbe wie auf der Produktdetailseite, der Produktlistenseite und der Mini-Warenkorbseite.
  _ACP2E-2799 - [GitHub-Problem](https://github.com/magento/magento2/issues/38091) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __Regel für Katalogförderungen funktioniert nicht mit dem Attribut quantity_and_stock_status__
Das Attribut quantity_and_stock_status wird jetzt von der Regel für die Katalogbeförderung berücksichtigt, die zuvor beim Generieren eines neuen Produkts von der Admin-Seite aus nicht berücksichtigt wurde.
  _ACP2E-2805 - [GitHub-Problem](https://github.com/magento/magento2/issues/35627) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/cf34971d)_
* __Die Spaltenwerte der Entität &#39;product_updated_at&#39; werden beim Aktualisieren des Preises über die REST-API nicht aktualisiert__
Die Spalte „Zuletzt aktualisiert am“ des Produkts vom Administrator wird zum richtigen Zeitpunkt aktualisiert, während die vorhandenen Produkte über die REST-API aktualisiert werden. Zuvor wurde die Spalte „Zuletzt aktualisiert um“ nicht ordnungsgemäß aktualisiert.
  _ACP2E-2837 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Es ist möglich, nicht eindeutige Werte über den Produktimport festzulegen__
Das System erzwingt jetzt beim Produktimport korrekt die Beschränkung des eindeutigen Werts für eindeutige Produktattribute, sodass für dieses Attribut keine doppelten Werte vorhanden sind. Zuvor war es möglich, nicht eindeutige Werte für Produktattribute festzulegen, die über den Produktimport für eindeutige Werte konfiguriert wurden.
  _ACP2E-2840 - [GitHub-Problem](https://github.com/magento/magento2/issues/38445) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __Produkte im Frontend verwenden speicherspezifische Daten, wenn der Einzelspeichermodus aktiviert ist__
Wenn wir zuvor den Einzelspeichermodus für die standardmäßige Store-Ansicht aktiviert haben, wurden die Änderungen nicht in den Umfang auf Website-Ebene migriert. Wenn wir nach dieser Fehlerbehebung den Einzelspeichermodus aktivieren, werden die standardmäßigen speicheransichtsspezifischen Daten mit Website-spezifischen Daten synchronisiert und die möglichen Konflikte für Produkte und Kategorien werden aufgelöst.
  _ACP2E-2843 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_
* __Standardeinstellung „Sortieren nach“ kann in einer Kategorie nicht mit der REST-API festgelegt werden__
Aktualisieren Sie default_sort_by korrekt für eine Kategorie über eine REST-/SOAP-API-Anfrage
  _ACP2E-2857 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] Der Händler hat Probleme mit der Anzahl der Wunschlisten__
Das Hinzufügen eines Produkts zur Wunschliste in einem Geschäft erhöht nicht mehr die Anzahl der Wunschlisten in anderen Geschäften, die im selben Browser geöffnet sind. Wenn beide Stores im selben Browser geladen wurden, stieg die Anzahl der Wunschlisten auch im anderen Store.
  _ACP2E-2871 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Kategorieseite im Frontend zeigt bei Verwendung des Bundle-Produkts leere Slots an__
Bundle-Produkte, die im aktuellen Store-Kontext nicht verfügbar sind, werden nicht mehr indiziert.
  _ACP2E-2874 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/bc37ec76)_
* __[KLARSTELLUNG] Probleme mit der Bundle-Produktsequenztabelle__
Die Datensätze in den Bundle-Produktsequenztabellen (sequence_product_bundle_option, sequence_product_bundle_selection) werden jetzt entfernt, wenn Bundle-Produkte gelöscht oder Bundle-Produktoptionen gelöscht werden.
Zuvor wurden die Datensätze in den Bundle-Produktsequenztabellen nicht entfernt.
  _ACP2E-2888_
* __[Cloud] Problem mit Zitaten in der Architektur mit mehreren Websites__
Zuvor konnten in einer Multi-Website-Architektur mit unterschiedlichen Währungen und Kundengruppen keine Rabatte korrekt auf den Store angewendet werden. Nachdem diese Fehlerbehebung implementiert wurde, wird die Multi-Website-Architektur mit unterschiedlichen Preisnachlässen für Kundengruppen erfolgreich auf verschiedene Stores angewendet.
  _ACP2E-2905 - [GitHub-Problem](https://github.com/magento/magento2/issues/38506) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __dynamic-rows.js:658 Nicht erfasster TypFehler: dataRecord.slice beim Bearbeiten von Bundle-Produkten__
In der Browser-Konsole tritt beim Löschen der Option aus dem Produktpaket kein JavaScript-Fehler auf.
  _ACP2E-2909 - [GitHub-Problem](https://github.com/magento/magento2/issues/38505) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __[Cloud] Bundle Produkt falsche Preise in Bestellbestätigung__
Der korrekte Betrag wird für Bundle-Optionen in der Reihenfolge auf der Storefront angezeigt, wenn eine andere Währung als die Basiswährung verwendet wurde.
  _ACP2E-2950 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __Fehler beim Hinzufügen von YouTube-Videos__
Produktbilder und Videos werden im globalen Umfang konfiguriert. Da ein Produktvideo nicht in einem Umfang und nicht in einem anderen enthalten sein kann, wurde die Einstellung für den YouTube-API-Schlüssel auf den globalen Umfang festgelegt.
  _ACP2E-2956 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __[Cloud] URL-Aktualisierung nur für store_id=0__
Der „URL-Pfad“ wird jetzt mit der richtigen Store-ID gespeichert. Zuvor war die Store-ID falsch, was dazu führte, dass beim Verschieben von Kategorien falsche URL-Pfade in der Datenbank verbleiben.
  _ACP2E-2964 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_
* __async.operations.all ausgeführt und ein Fehler erstellt.__
Falsche Produktverknüpfungsdaten in REST-API-Aufrufen verursachen keine kritischen Fehler mehr.
  _ACP2E-3009 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __[Cloud] Problem Nur für Mobilgeräte kann das PDP-Bild nicht gequetscht werden__
Das System unterstützt jetzt die Pinch-to-Zoom-Funktion auf Produktdetailseitenbildern in der mobilen Ansicht auf Chrome, wodurch das mobile Benutzererlebnis verbessert wird. Zuvor wurde das Bild in der mobilen Ansicht auf Chrome beim Doppeltippen nicht wie erwartet vergrößert.
  _ACP2E-3029 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_
* __Fehlende Beschriftung in LayeredNavigation mit Optionsname 0__
Das Problem wurde behoben, indem eine leere Werteprüfung für den Attributwert 0 übersprungen wurde. Zuvor wurde es als leer betrachtet und verursachte das Problem.
  _ACP2E-3058 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Kunden sehen Preise von anderen Kundengruppen__
Es wurde ein Problem behoben, bei dem Informationen zu Kundengruppen aufgrund des alten Werts der Anfrage „X-Magento-Vary“ in einem falschen Segment gespeichert wurden
  _ACP2E-3069 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d1f7dc95)_
* __Fehler beim Löschen von Paketoptionen__
Das System löscht jetzt die Bundle-Optionen korrekt, ohne einen Fehler auszulösen oder die Seite nicht mehr reagieren zu lassen. Zuvor führte der Versuch, Bundle-Optionen zu löschen, zu einem Fehler „Seite reagiert nicht“ und verhindert, dass das Produkt gespeichert wird.
  _ACP2E-3076 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_
* __Problem mit nicht genügend Arbeitsspeicher für Kategorieberechtigungen__
Die Benutzeroberfläche für Kategorieberechtigungen wurde umgestaltet, um eine große Anzahl von Berechtigungen mithilfe von vorkonfigurierten UI-Komponenten und Paginierung zu ermöglichen. Zuvor führten Kategorieberechtigungen dazu, dass der Browser mit einer großen Anzahl von der Kategorie zugewiesenen Berechtigungen abstürzte.
  _ACP2E-3094_
* __[Cloud] Bilddatei ist nicht im New Relic-Fehlerprotokoll vorhanden__
Das System synchronisiert jetzt benutzerdefinierte Platzhalterbilder mit dem lokalen Speicher, um sicherzustellen, dass sie bei der Verwendung von Remote-Speicher wie AWS S3 korrekt gerendert werden. Zuvor konnten benutzerdefinierte Platzhalterbilder bei der Verwendung des Remote-Speichers nicht gerendert werden, was zu einer fehlerhaften Bildanzeige und zu Fehlerprotokollen führte.
  _ACP2E-3100 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d1f7dc95)_
* __RSS-Feed für neue Produkte wird aufgrund des Cache nicht mit neuen Produkten aktualisiert__
Der RSS-Feed für neue Produkte wird jetzt aktualisiert, wenn ein Produkt als neu festgelegt und gespeichert wird
  _ACP2E-3103 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_
* __[Cloud] Die GQL-Antwort der Produktmediensammlung ist nicht nach Bildposition sortiert__
Das System sortiert jetzt die Elemente in der Mediensammlung korrekt nach der Position in der GraphQL-Antwort, um eine genaue Anzeigereihenfolge zu gewährleisten. Zuvor wurden Elemente in der Mediensammlung nicht nach Position sortiert, was zu einer falschen Anzeigereihenfolge führte.
  _ACP2E-3126 - [GitHub-Problem](https://github.com/magento/magento2/issues/37671) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b21e5d91)_
* __[Cloud] Unterkategorieelemente werden nicht in den Widgets angezeigt, die im Admin-Backend bearbeitet werden__
Die Kategoriestruktur auf der neuen Widget-Seite sollte keine Probleme mehr beim Laden von Kategorien der Stufe 5+ aufweisen. Zuvor fehlten beim Laden des Baums über die Kategorie der Ebene 5 hinaus einige Kategorien.
  _ACP2E-3136 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_
* __[cloud] Zwei-Finger-Zoom und Bewegungsproblem auf dem echten Mobilgerät__
Das System stellt nun auf mobilen Geräten eine konsistente Bildzoom-Funktionalität sicher und sorgt so für ein reibungsloses und vorhersehbares Benutzererlebnis. Zuvor war die Bildzoom-Funktion inkonsistent und zoomte bei der Ansicht auf einem Mobilgerät nach einem bestimmten Punkt plötzlich heraus.
  _ACP2E-3198 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __Wenn wir die Zuweisung von Produkten zum freigegebenen Katalog aufheben, werden die Produkte auf der Wunschliste nicht gelöscht__
Jetzt sind keine Elemente in der Wunschliste sichtbar, wenn ein Produkt nicht im freigegebenen Katalog verfügbar ist. Zuvor wurde auf der Seite mit der Wunschliste fälschlicherweise die Anzahl „1 Artikel“ angezeigt, auch wenn keine Artikel in der Wunschliste verfügbar waren.
  _ACP2E-3282 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_
* __Verwandte Produkte Wählen Sie „Alle“ aus bzw. heben Sie die Auswahl auf__
Zuvor funktionierten die Schaltflächen „Alle auswählen“/„Alle deaktivieren“ für zugehörige Produkte nicht richtig, wenn ein Produkt manuell ausgewählt wurde. Nach der Fehlerbehebung funktionieren diese Schaltflächen nun auch nach der manuellen Auswahl konsistent und stellen sicher, dass alle Produkte richtig ausgewählt oder deaktiviert sind.
  _ACP2E-3286 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Cloud] Übersetzen von Warnhinweis-E-Mails in die falsche Sprache__
Wenn Stock-/Preis-Warnhinweise für eine Website mit mehreren Store-Ansichten in verschiedenen Sprachen gesendet werden, wird die Sprache für die Store-Ansicht, in der der Warnhinweis erstellt wurde, in der E-Mail verwendet.
  _ACP2E-3336 - [GitHub-Code-](https://github.com/magento/magento2/commit/a4cf5e62) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Die Namen von deaktivierten Kategorien sind in der Kategoriestruktur nicht mehr ausgegraut__
Zuvor waren deaktivierte Kategorien in der Kategoriestruktur nicht ausgegraut. Jetzt werden sie mit einem Graustufeneffekt angezeigt.
  _ACP2E-3350 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_
* __Das konfigurierbare Formular zum Bearbeiten von Produkten führt zu einer Zeitüberschreitung und zu einer Speichererschöpfung__
Vor der Fehlerbehebung wurden konfigurierbare Produktvarianten basierend auf allen möglichen Attributoptionskombinationen erstellt. In Fällen, in denen Attribute viele Optionen hatten, führte dies zu einem langwierigen und ressourcenintensiven Vorgang. Jetzt werden konfigurierbare Produktvarianten basierend auf vorhandenen untergeordneten Produktattributen erstellt. Dies führt zu deutlich weniger Berechnungen - und damit zu einer verbesserten Nutzung von Ressourcen.
  _ACP2E-3410 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __Fotorama lädt Videos bei der Verwendung von Farbfeldern nicht korrekt, und die Option ist über die URL vorausgewählt__
Produktvideos werden jetzt auf der konfigurierbaren Produktdetailseite korrekt gerendert, wenn die URL ausgewählte Optionen enthält.
  _ACP2E-3454 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __Das Karussell-Widget von PageBuilder zeigt Produkte an, die nicht den Bedingungen entsprechen__
Die in Widgets verwendete Produktliste berücksichtigt jetzt die Kategoriebedingung
  _ACP2E-3461 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __Validierungsfehler wird für alle Produkte in der Gruppe ausgelöst, wenn eine ungültige Menge aufweist__
Jetzt wird der Validierungsfehler korrekt für alle Produkte in der Gruppe ausgelöst, wenn ein Produkt eine ungültige Menge hat, was zuvor nicht passiert ist.
  _ACP2E-3469 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/56463d5e)_
* __[CLOUD] Sonderpreis wird nicht im konfigurierbaren Produkt angezeigt__
Nach der Korrektur wirkt sich die Änderung des Werts „Wird in der Produktliste verwendet“ für das Sonderpreisattribut nicht auf die Anzeige des Sonderpreises für konfigurierbare Produkte aus.
  _ACP2E-3513 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_
* __Indexer Temporäre Tabellen werden nicht bereinigt, wenn der Prozess beendet wird__
Die temporären Tabellen des CatalogRule-Indexers werden jetzt bereinigt, wenn der Indexerprozess beendet wird
  _ACP2E-3516 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_
* __[QUANS] Fehler bei Kernkomponententests in 2.4.7-p3__
Versionshinweise für diesen Test sind nicht erforderlich, da es sich um eine Verbesserung bei Modultests handelt.
  _ACP2E-3520 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_
* __Leistungsproblem beim Abrufen der Lagermenge für gruppierte Produkte mit mehreren Quellen__
Die gruppierte Seite zur Bearbeitung von Produkten und Bundles wurde jetzt optimiert, wenn zugewiesene Produkte über eine große Anzahl von Inventarquellen verfügen.
  _ACP2E-3533 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/0208e433)_
* __Präfix ACP2e-3389__
Verbesserte Leistung der Admin-Kategorieseite bei einer großen Anzahl von Anker-Kategorien
  _ACP2E-3641 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Katalog, Inhalt

* __[Cloud]-Cache wird nicht ungültig gemacht.__
Beim Speichern einer CMS-Seite mit einem aktualisierten Design-Layout wurde diese zuvor nicht ordnungsgemäß am Frontend dargestellt. Nachdem diese Fehlerbehebung angewendet wurde, wird das entsprechende Design-Layout am Frontend angezeigt, wenn wir das Design-Layout ändern und die CMS-Seite speichern.
  _ACP2E-3063 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_
* __[Cloud] Anker-/Nicht-Anker-Kategorien im Inhalts-Widget umgekehrt__
Wenn wir zuvor „Anzeigen auf“ > „Ankerkategorien“ ausgewählt haben, wurden alle Kategorien angezeigt, die nicht die hierarchische Beziehung zwischen Anker und Nicht-Anker widerspiegeln. Nachdem diese Fehlerbehebung angewendet wurde, zeigt „Anzeigen ein“ > „Ankerkategorien“ nur Ankerkategorien (auswählbar) an und „Anzeigen ein“ > „Nicht-Ankerkategorien“ zeigt „Nicht-Ankerkategorien“ (auswählbar) an
  _ACP2E-3131 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_
* __Kategorien funktionieren nicht mit Widgets__
Wenn wir den CMS-Block zuvor für verschiedene Anker-/Nicht-Anker-Kategorien gespeichert haben, funktionierte er nicht für die untergeordneten Kategorien, als er am Frontend angezeigt wurde. Nach Anwendung dieser Fehlerbehebung wird der Block an der Vorderseite für verschiedene Kategorien angezeigt.
  _ACP2E-3152 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_

### Katalog, Framework

* __Bestellung get(Sendungen|Creditmemos|Rechnung)Sammlung - Sammlung darf nicht geladen werden__
Das System stellt jetzt sicher, dass die Sammlungen für Sendungen und Gutschriften beim Abrufen aus einer Bestellung nicht vorgeladen werden, sodass zusätzliche Filter oder Bestellungen auf diese Sammlungen angewendet werden können. Zuvor wurden diese Sammlungen automatisch geladen, was weitere Änderungen verhinderte.
  _AC-9111 - [GitHub-Problem](https://github.com/magento/magento2/issues/37561) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37562)_
* __[Cloud]Follow-up: Beim Datenvergleich beim Überprüfen, ob die Daten Änderungen aufweisen, stimmen die Werte nicht überein__
Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Außerdem werden die von der Zeichenfolge gekapselten Gleitkommazahlen nicht geprüft. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, und führt eine strikte Typübereinstimmung durch
  _ACP2E-2949 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_

### Catalog, GraphQL

* __Umgang mit Kategoriefiltern in GraphQL: includeDirectChildrenOnly und category_uid__
Beim Filtern nach category_uid werden nur die direkt untergeordneten Kategorien abgerufen.
  _ACP2E-3090 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __[Cloud] GraphQL-Produktsortierung funktioniert nicht__
Die GraphQL-Produktsortierung nach mehreren Feldern, wenn die Felder in Variablen übergeben werden, funktioniert jetzt erwartungsgemäß.
  _ACP2E-3166 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Stufenpreise geben in Produkten in GraphQL einen falschen Wert zurück (im Vergleich zu Storefront)__
Nach der Fehlerbehebung haben die für GraphQL-Anfragen zurückgegebenen Produktstufenpreise den Preis pro einem Element.
  _ACP2E-3312 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] B2B: Kategorieproblem über GraphQL__
Nach der Behebung gibt die GraphQL-Abfrage Kategorien mit der Berechtigung „Zulassen“ zurück, auch wenn die Stammkategorie keine Berechtigung „Zulassen“ hat.
  _ACP2E-3385_

### Katalog, Preise, Staging und Vorschau

* __[Cloud] Der API-Endpunkt für Sonderpreise gibt einen Fehler zurück, wenn eine große Anzahl von Produkten gleichzeitig aktualisiert wird__
Jetzt erstellt die Special Price Bulk Update API für jeden Datumsbereich eine einzelne Kampagne anstelle mehrerer geplanter Aktualisierungen für jedes Produkt und jeden Datumsbereich. Außerdem unterstützt es gleichzeitige API-Anfragen für eine schnellere Verarbeitung einer großen Anzahl von SKUs.
  _ACP2E-2672 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f89a447e)_

### Katalog, Produkt

* __Kategorieauswahlbaum im bearbeiteten Produkt ist nicht in der gleichen Reihenfolge wie in Katalog->Kategorien festgelegt__
Das System zeigt nun die Kategorieauswahl im Produktbearbeitungsbereich in der gleichen Reihenfolge wie unter Katalog->Kategorien an, was die Produktverwaltung in großen Katalogen erleichtert. Zuvor wurde die Kategoriestruktur im Produktbearbeitungsabschnitt in der Reihenfolge der Kategorienerstellung angezeigt, unabhängig von der Anzeigereihenfolge, die unter Katalog->Kategorien festgelegt wurde.
  _AC-7050 - [GitHub-Problem](https://github.com/magento/magento2/issues/36101) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36104)_

### Katalog, SEO

* __Falsche kanonische URL für Kategorie bei Seite > 1__
Zuvor funktionierte die kanonische URL für mehrseitige Inhalte nicht ordnungsgemäß, sodass die Basis-URL durchgängig angezeigt wurde. Nachdem die Fehlerbehebung implementiert wurde, zeigt die kanonische URL für mehrseitige Inhalte jetzt jedoch korrekt die URL mit der Seiten-ID an.
  _ACP2E-3653 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Katalog, Suche

* __Produkte werden nicht in Kategorie und Suche angezeigt, aber direkte Links funktionieren__
Zuvor funktionierte das benutzerdefinierte Attribut „Ja/Nein“ mit dem _* „Preis/Attribut_Code“ nicht mit der Indizierung. Nach dieser Korrektur funktioniert das benutzerdefinierte Attribut Ja/Nein erwartungsgemäß.
  _ACP2E-2757 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __[Cloud] Elastischer Suchfehler auf bestimmten Kategorieseiten__
Zuvor wurde mit dem erwähnten Konfigurations-Ticket, wenn wir den Preis 0 für mehrere Produkte setzen, eine Ausnahme auf der Frontend-Kategorieseite ausgelöst. Nachdem diese Fehlerbehebung angewendet wurde, wenn mehrere Produktpreise 0 sind und wir die Kategorieseite im Frontend laden, wird keine Ausnahme ausgelöst und die Kategorieseite wird erfolgreich geladen.
  _ACP2E-3053 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_
* __Fehler beim Erstellen des Objekts: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Ausnahme__
Nach der Fehlerbehebung kann eine Instanz der Klasse Magento\CatalogSearch\Model\Indexer\Fulltext erstellt werden, ohne $data anzugeben.
  _ACP2E-3345 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] Problem mit Produkten ist nach dem Speichern in Magento Admin nicht in Frontend sichtbar__
Nach der Fehlerbehebung werden konfigurierbare Produkte, die untergeordnete Produkte mit langen Namen haben, in der Storefront nicht übersehen.
  _ACP2E-3521 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

### Katalog, Versand

* __Lieferadresse leer bei der Bestellung eines Geschenkartikels__
Zuvor generierte bei Geschenk-Registrierungselementen für Gastbenutzer bei der Rückgabe von der E-Mail-Funktion eine leere leere leere Adresse, die für die Bestellung falsch ist. Nachdem dieser Fix angewendet wurde, prüft die Geschenkregistrierung angemeldete Benutzer/Gastbenutzer und zugewiesene Adressen, ob sie vorhanden sind.
  _ACP2E-3195_

### Cloud

* __[Cloud] PHPSESSID ändert jede POST-Anfrage__
PHPSESSID wird bei POST-Anfragen im Frontend-Bereich für einen angemeldeten Kunden nicht mehr neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde vom Backend aktualisiert wurde
  _ACP2E-3010 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_
* __Sitemap-Generierungswarnungen__
Nach der Fehlerbehebung wird die Sitemap im System-TMP-Verzeichnis generiert und in das endgültige Ziel kopiert.
  _ACP2E-3532 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

### Inhalt

* __[Problem] Problem mit der Preisanzeige im Widget „Kürzlich angezeigt“__
Das System zeigt jetzt den Preis nicht vorrätiger einfacher Produkte im Widget „Kürzlich angezeigtes Produkt“ korrekt an, wodurch die Konsistenz über alle Widgets und Produktlistenseiten hinweg sichergestellt wird. Zuvor wurde der Preis für nicht vorrätige einfache Produkte aufgrund einer Bedingung in den Preisladevorlagen nicht im Widget „Kürzlich angezeigtes Produkt“ angezeigt.
  _AC-10539 - [GitHub-Problem](https://github.com/magento/magento2/issues/38167) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38159)_
* __[Problem] Korrigieren Sie Tippfehler und Grammatik in der Datei acl.xsd__
Das System korrigiert jetzt einen Tippfehler und Grammatikfehler in der Datei acl.xsd, wodurch die Klarheit und Genauigkeit der Dokumentation verbessert wird. Zuvor enthielt die Datei acl.xsd einen Tippfehler und eine falsche Grammatik, was möglicherweise zu Verwirrung führen konnte.
  _AC-10596 - [GitHub-Problem](https://github.com/magento/magento2/issues/38061) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38046)_
* __PageBuilder Banner image not visible in gallery__
Das System zeigt jetzt korrekt Bannerbilder an, die in neu erstellte Ordner in der PageBuilder-Galerie hochgeladen wurden, sodass frühere Konsolenfehler vermieden werden. Vor dieser Fehlerbehebung waren Bannerbilder in der Galerie nicht sichtbar, wenn sie in einen neuen Ordner hochgeladen wurden, was einen Konsolenfehler verursachte.
  _AC-10845 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __„Vorwahl nicht festgelegt“ nach Aktualisierung auf 2.4.5-p8__
Das System schließt nun den statischen Prozess der Inhaltsbereitstellung erfolgreich ab, wenn das Magento_CSP-Modul aktiviert ist und „dev/js/translate_strategy“ auf „embedded“ gesetzt ist, ohne den Fehler „Area Code Not Set“ auszulösen. Zuvor schlug der statische Prozess der Inhaltsbereitstellung unter diesen Bedingungen mit dem Fehler „Area Code Not Set“ fehl.
  _AC-12283 - [GitHub-Problem](https://github.com/magento/magento2/issues/38845) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38922)_
* __Die Widget-Kategoriestruktur wird nicht korrekt gerendert__
  _AC-12692 - [GitHub-Problem](https://github.com/magento/magento2/issues/39008) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/58e40ceb)_
* __Meldung „Standardwert wird verwendet“ wird beim Ändern des Designs auf der Seite „Design-Konfiguration“ nicht angezeigt__
Das System enthält jetzt eine separate Spalte, in der die Meldung „Standardwert verwenden“ je nach ausgewähltem Design auf der Design-Konfigurationsseite angezeigt wird. Dadurch wird Klarheit und Sichtbarkeit des Standardwertstatus sichergestellt. Zuvor wurde die Meldung „Standardwert verwenden“ nicht angezeigt, was zu Verwirrung über den Status des ausgewählten Designs führte.
  _AC-13054 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problem] Stellt die Abwärtskompatibilität mit TinyMCE-Plug-ins wieder her (danach…__
Das System stellt jetzt die Abwärtskompatibilität mit TinyMCE-Plug-ins wieder her, sodass Funktionen, die innerhalb des Plug-ins definiert sind, aufgerufen werden können, wenn das Widget von einem anderen Ort verwendet wird. Zuvor gab es aufgrund einer Änderung in der TinyMCE-Version die Plug-ins die Widgets nicht als -Objekt zurück, was zu einem Fehler beim Versuch führte, bestimmte Funktionen auf der Widget-Instanz aufzurufen.
  _AC-13569 - [GitHub-Problem](https://github.com/magento/magento2/issues/39262) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39258)_
* __[Problem] Problem beim Hochladen von Dateien im WYSIWYG-Editor auf der Produktseite__
Das System zeigt nun die Ordnerstruktur korrekt an und ermöglicht das Hochladen von Bildern im WYSIWYG-Editor auf der Produktseite, auch nachdem zuerst die Registerkarte „Bild und Videos“ erweitert wurde. Zuvor führte das Erweitern der Registerkarte „Bild und Videos“ zunächst dazu, dass die Ordnerstruktur nicht angezeigt wurde und eine Fehlermeldung angezeigt wurde, wenn versucht wurde, ein Bild im WYSIWYG-Editor hochzuladen.
  _AC-9638 - [GitHub-Problem](https://github.com/magento/magento2/issues/38026) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38025)_
* __[On-Premise] Problem mit dynamischen Blöcken__
Widgets werden jetzt innerhalb dynamischer Blöcke ordnungsgemäß gerendert.
  _ACP2E-2392 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a12063bd)_
* __YouTube-nocookie-URL funktioniert nicht in Page Builder__
Jetzt lässt der Page Builder die YouTube-URL ohne Cookie in den Formularelementeinstellungen der Validierungsregeln zu. Zuvor funktionierte die Nicht-Cookie-URL von YouTube nicht in PageBuilder.
  _ACP2E-2606_
* __[Cloud] Frontend wird aufgrund eines Problems in der Newsletter-Vorlage nicht geladen__
Das Hinzufügen von Blöcken über den CMS-Seiteninhaltsabschnitt führt nicht mehr zu einer Ausnahme
  _ACP2E-2693 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __ACP2E-2836: [Cloud] Investigate-Ausnahme gefunden im Protokoll: InvalidArgumentException: Klasse ist in vendor/magento/module-rule/Model/ConditionFactory.php nicht vorhanden__
Wenn Sie eine Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten entfernen, wird keine Ausnahme mehr in den Protokolldateien aufgezeichnet. Zuvor führte das Entfernen einer Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten dazu, dass eine kritische Ausnahme in den Protokollen aufgezeichnet wurde, obwohl dies keine Probleme im Frontend verursachte.
  _ACP2E-2836 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_
* __Wechseln zum Einzelspeichermodus - Globale Inhalte werden nicht mehr angezeigt__
Das System synchronisiert jetzt Design-Konfigurationen für Store-Ansichten mit Website-Design-Konfigurationen, wenn es den Einzelspeichermodus aktiviert, um sicherzustellen, dass Inhaltsaktualisierungen im Frontend sichtbar sind. Zuvor wurde durch den Wechsel zum Einzelspeichermodus verhindert, dass Inhaltsaktualisierungen in der Storefront widergespiegelt werden.
  _ACP2E-2842 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __Page Builder ersetzt ein Bild, wenn versucht wird, Link- und andere Nutzungsfehler hinzuzufügen.__
Wenn Sie jetzt auf ein Bild klicken, werden Links im WYSIWYG-Editor im Textelement von Page Builder geladen. Dadurch werden die richtigen Daten in das Dialogfeld Bild- und Link-Konfiguration geladen. Auch das Hinzufügen eines Links zu einem Bild im Editor funktioniert jetzt ordnungsgemäß. Zuvor wurde das Bild durch einen Link ersetzt.
  _ACP2E-2903 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __Die alte Mediensammlung kann Bilder nicht rendern, wenn ein 0-Byte-Bild im Verzeichnis platziert wird__
Das System verarbeitet jetzt 0-Byte-Bilder in der Mediensammlung, ohne dass die Funktionalität beeinträchtigt wird, sodass andere Bilder im Verzeichnis wie erwartet angezeigt und ausgewählt werden können. Zuvor verhinderte das Vorhandensein eines 0-Byte-Bildes in der Mediensammlung, dass alle Bilder im Verzeichnis angezeigt oder ausgewählt wurden.
  _ACP2E-2970 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/35b1b1da)_
* __Fehler von Page Builder beim Bearbeiten des CMS-Blocks__
Das System speichert jetzt mit Page Builder korrekt die im Administratorbereich vorgenommenen Änderungen, ohne den Fehler „Page Builder wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben“ auszulösen. In der Browser-Konsole. Zuvor trat dieser Fehler beim Versuch auf, Änderungen zu speichern, wodurch die erfolgreiche Aktualisierung des Inhalts verhindert wurde.
  _ACP2E-3064 - [GitHub-Code-](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __[CLOUD] Keine Schaltflächen von Checkout oder Warenkorb bearbeiten im Warenkorb-Abschnitt__
Das Bundle-Produkt wird jetzt fehlerfrei über Widgets zum Warenkorb hinzugefügt.
  _ACP2E-3092 - [GitHub-Code-](https://github.com/magento/magento2/commit/b21e5d91) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_
* __Die Inhalts-Staging-Vorschau auf Kategorieseiten zeigt keine Produkt-Widgets an__
Dieses Problem wurde behoben, indem sichergestellt wurde, dass Produkteinträge für die zusätzliche, mit dem CMS-Block verknüpfte Kategorie korrekt in der Datenbank erfasst wurden. Zuvor wurde bei der Anforderung der Kategorievorschauseite ein leerer Ergebnissatz zurückgegeben.
  _ACP2E-3113_
* __[CLOUD] Schaltfläche Bild hochladen funktioniert nicht__
Bevor die Schaltfläche Bild hochladen für Banner und Regler von PageBuilder nicht erwartungsgemäß funktionierte, wird durch Drücken von nun der lokale Datei-Manager geöffnet, um das gewünschte Bild zum Hochladen auszuwählen.
  _ACP2E-3122 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_
* __imageCreateTrueColor(): Der #2 ($height) muss größer als 0 sein. Bestimmtes Bild kann nicht hochgeladen werden__
Es wurde das Problem behoben, das beim Hochladen von Bildern mit einer Höhe von 0 über die Mediensammlung zu Fehlern in der Administratorrolle führte und die Assets mit dem Befehl Synchronisieren erfolgreich synchronisierte. Zuvor kann das Bild nicht über die Mediensammlung hochladen, und der Synchronisierungsbefehl schlägt auch fehl, wenn sich ein bestimmtes Bild in der Galerie befindet.
  _ACP2E-3127 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __Prototype.js Array.from steht im Konflikt mit der Google Maps-API__
Google Maps werden im PageBuilder-Editor jetzt korrekt gerendert. Zuvor verhinderte ein JavaScript-Fehler, dass Google Maps korrekt gerendert wurden.
  _ACP2E-3154 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_
* __[Cloud] - CMS-Schieberegler spiegelt nicht die neuesten Änderungen wider__
Das Problem wurde behoben, indem sichergestellt wurde, dass die Schiebereglerliste aktualisiert wird, während das Speicherereignis auf dem Bildschirm Folie bearbeiten ausgelöst wird. Zuvor wurde das Problem ausgelöst und verursacht.
  _ACP2E-3275 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __Auf der CSM-Seite tritt ein Fehler auf, wenn CMS-Blöcke mithilfe des Seiten-Builders in einer bestimmten Reihenfolge eingefügt werden__
Zuvor wäre bei einigen Versionen von PHP und OS (Linux) das Rendern von Blöcken, die über PageBuilder auf andere CMS-Blöcke verwiesen haben, mit dem Fehler „Ein unbekannter Fehler ist aufgetreten. Bitte erneut versuchen.“ Jetzt wird der Inhalt der CMS-Blöcke innerhalb eines von PageBuilder gesteuerten Inhalts korrekt wiedergegeben.
  _ACP2E-3326 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __[Cloud] Dynamische Blöcke funktionieren nicht ordnungsgemäß__
Angemeldete Kundensegmente werden jetzt nach dem Abmelden gelöscht, was verhindert, dass die Gastsitzung zuvor angemeldete Segmente erbt
  _ACP2E-3388_
* __Vorlagenvorschau-Fehler von PageBuilder bei großen Inhalten__
Große Inhalte führten dazu, dass das Canvas-Element über die Beschränkungen des Browsers hinausreichte und einen falschen Wert zurückgab, wodurch der Backend-Code beschädigt wurde (das Bild kann nicht ordnungsgemäß decodiert werden). Es wurde ein Problem behoben, indem die Arbeitsfläche auf die Grenze des universellen Browsers beschränkt wurde.
  _ACP2E-3428 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/adfb1747)_
* __Neueste Sicherheitsupdates mit TinyMCE 7 fehlender Schriftgröße__
Die Auswahl der Schriftgröße und Schriftfamilie ist jetzt im WYSIWYG-Editor verfügbar. Vor dieser Fehlerbehebung waren diese bei TinyMCE 7 nicht in der Editor-Oberfläche verfügbar.
  _ACP2E-3430 - [GitHub-Code-](https://github.com/magento/magento2/commit/d50f6b5d) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_
* __TinyMCE 7 Editor Schriftgröße in der Admin in PT und nicht PX Bitte klären__
Vor der Korrektur konnten Sie die Schriftgröße in px in WYSIWYG-Bereichen nicht angeben. Jetzt können Sie die Schriftgröße in px statt pt einstellen.
  _ACP2E-3483 - [GitHub-Code-](https://github.com/magento/magento2/commit/3f12d152) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __Der Produktinhaltstyp in Page Builder wird ohne korrekte Meldungen reduziert__
Vor der Korrektur wurde die HTML-Vorschau nicht richtig generiert, wenn es keine Produkte im Widget gab. Jetzt wird die leere Antwort ordnungsgemäß generiert und das Produkt-Widget wird in der Vorschau korrekt angezeigt.
  _ACP2E-3490 - [GitHub-Code-](https://github.com/magento/magento2/commit/3f12d152) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __[Page Builder]Hinzufügen der Produktliste zum Blockieren führt zu Fehlern__
Das Hinzufügen der Bundle-Produktliste zum -Block über den Seiten-Builder führt jetzt nicht mehr zu Fehlern
  _ACP2E-3534 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/344fce23)_

### Inhalt, SEO

* __Die CMS-Seitenhierarchie kann zu Problemen beim Umschreiben von URLs führen__
Zuvor wurde für benutzerdefinierte permanente URL-Neuschreibungen für Stammseiten anderer Websites die Seite unendlich umgeleitet und nie geladen. Nachdem diese Fehlerbehebung angewendet wurde, funktioniert die benutzerdefinierte URL-Umschreibung für die Stammseite der Nicht-Website erwartungsgemäß und es tritt keine Umleitungsschleife auf.
  _ACP2E-2870_

### Inhalt, Staging und Vorschau

* __Katalogpreisregel wird nicht angezeigt, wenn sie auf „Mit dynamischen Blöcken planen“ festgelegt ist__
Das System zeigt nun auf der Produktdetailseite die dynamischen Inhalte, die mit den Preisregeln für geplante Kataloge verknüpft sind, korrekt an. Zuvor konnte dynamischer Inhalt nicht geladen werden, wenn Katalogpreisregeln geplant waren.
  _ACP2E-2979_

### Kunde/Kunden

* __Frontend - Die Validierung des Geburtsdatums schlägt auf der Seite zur Kundenerstellung fehl__
Stellen Sie sicher, dass die gesamte Validierung nach dem Upgrade von moment.js Systemabhängigkeit auf die neueste Nebenversion funktioniert
  _AC-12162 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Kundensegment > Bedingung > Produktverlauf* > „Produkt wurde angezeigt“ funktioniert nicht__
Das System zeigt jetzt korrekt übereinstimmende registrierte Kunden in der Bedingung „Produkt wurde angezeigt“ unter „Kundensegmente“ an, wenn die Bedingung erfüllt ist. Zuvor blieb die Anzahl der übereinstimmenden registrierten Kunden auch dann bei null, wenn die Bedingung erfüllt war.
  _AC-13060_
* __Das Textfeld „Region“ wird nicht zurückgesetzt, wenn die Dropdown-Liste „Land“ geändert wird__
Das Textfeld Region wird jetzt zurückgesetzt, wenn das Land im Dropdown-Menü geändert wird. Dadurch wird sichergestellt, dass die vorherigen Werte nicht beibehalten werden. Beim Ändern des Landes aus der Dropdown-Liste wurde das Feld Region zuvor nicht zurückgesetzt, sodass der zuletzt gespeicherte Wert beibehalten wurde.
  _AC-8499 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ea26621)_
* __Beim Löschen eines Kunden werden nicht alle Browser-Sitzungsdaten in der Storefront für angemeldete und gelöschte Kunden bereinigt__
Durch das Löschen eines Kunden werden jetzt alle Browser-Sitzungsdaten aus der Storefront für angemeldete und gelöschte Kunden wie erwartet bereinigt. Der Käufer kann weiterhin einkaufen, und sein Browser behandelt seine Sitzung als Gastsitzung. Wenn das Kundenkonto eines angemeldeten Käufers aus dem Admin gelöscht wurde, gab es zuvor im Browser des Käufers JavaScript-Fehler.
  _AC-9240 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_

### Framework

* __[Question]Unused Type configuration in`app/code/Magento/Translation/etc/di.xml`__
Das System entfernt jetzt nicht verwendete Abhängigkeiten in der Konfiguration, was die Code-Sauberkeit und -Effizienz insgesamt verbessert. Zuvor gab es in der Konfiguration nicht verwendete Abhängigkeiten, die zu keiner Funktion beitrugen.
  _AC-10037 - [GitHub-Problem](https://github.com/magento/magento2/issues/38030) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38064)_
* __V1/customers/password-Endpunkt - Frage/Problem__
Das System hält sich jetzt bei der Verarbeitung von Passwortänderungsanfragen über die API an die in der Verwaltungs-Benutzeroberfläche festgelegten Einschränkungen, um einen potenziellen Missbrauch der Passwortrücksetzfunktion zu verhindern. Zuvor konnte die API Passwortänderungsanfragen außerhalb der in der Verwaltungs-Benutzeroberfläche definierten Regeln verarbeiten, was möglicherweise einen konstanten Stream von Zurücksetzungs-E-Mails ermöglichte, wenn gültige E-Mails bekannt waren.
  _AC-10654 - [GitHub-Problem](https://github.com/magento/magento2/issues/38238) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Die Lackkonfiguration schließt nicht alle Marketing-Parameter aus__
Das System schließt jetzt alle gängigen Marketing-Parameter in der Lackkonfiguration korrekt aus, um eine genaue Verfolgung und Analyse zu gewährleisten. Zuvor wurden bestimmte Marketing-Parameter wie „gad_source“, „srsltid“ und „msclpid“ nicht ausgeschlossen, was zu möglichen Ungenauigkeiten bei der Datenerfassung führen kann.
  _AC-10738 - [GitHub-Problem](https://github.com/magento/magento2/issues/38298) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39188)_
* __Fehler-Indizierungsprozess des Katalogsuchindex-Prozesses__
Das System führt nun den Befehl zur Neuindizierung erfolgreich aus, ohne dass Fehler auftreten, unabhängig von der mit PHP kompilierten libxml-Version. Zuvor führte die Ausführung des Befehls re-index zu einem Fehler „Catalog Search index process error during indexation process“, wenn PHP mit bestimmten Versionen von libxml kompiliert wurde.
  _AC-10838 - [GitHub-Problem](https://github.com/magento/magento2/issues/38254) - [GitHub-Code-](https://github.com/magento/magento2/pull/38553) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_
* __CREATED_AT-, STATUS- und GRAND_TOTAL-Filter wurden zur Abfrage „Kundenaufträge“ hinzugefügt und mehrere Filterfehler wurden behoben__
Das System unterstützt jetzt die Verwendung der Filter CREATED_AT, STATUS und GRAND_TOTAL in Kundenauftragsabfragen und hat ein Problem behoben, bei dem mehrere Filter nicht korrekt angewendet wurden. Zuvor hat das System diese Filter nicht unterstützt und würde nicht alle Filter anwenden, wenn mehr als einer in einer Abfrage verwendet wurde.
  _AC-10941 - [GitHub-Problem](https://github.com/magento/magento2/issues/38392) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36949)_
* __Zufällige Flut von Abfragen aus verwandten / Upsell / Crosssell-Blöcken und Preisindizierung__
Das System optimiert jetzt Abfragen aus verwandten, Upsell- und Crosssell-Blöcken, verbessert die Leistung und verhindert, dass die Site aufgrund übermäßiger Abfragen abstürzt. Zuvor konnte das System mit Abfragen aus diesen Blöcken überlastet werden, was zu erheblichen Verzögerungen führte und möglicherweise die Site lahmlegte.
  _AC-10991 - [GitHub-Problem](https://github.com/magento/magento2/issues/36667) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38050)_
* __Ausnahme: Warnung: Versuch, auf Array-Offset in zuzugreifen… -> Calendar.php seit Upgrade auf ICU 74.1 (PHP Intl)__
Commerce protokolliert die folgende Ausnahme nicht mehr in der Datei „Exception.log“, wenn ein Käufer oder Händler die Storefront oder den Administrator besucht: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
  _AC-11423 - [GitHub-Problem](https://github.com/magento/magento2/issues/38214) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38364)_
* __[Problem] Beheben von Problemen mit Kundendaten, wenn das Formular ein Element mit dem Namen`method`__ enthält
Das System identifiziert nun das Attribut „method“ in Formularübermittlungen korrekt, auch wenn ein Element namens „method“ im Formular vorhanden ist. Dadurch wird eine präzise Verarbeitung der Kundendaten gewährleistet. Wenn ein Formularelement zuvor „Methode“ genannt wurde, würde dies die Identifizierung des Attributs „Methode“ bei Formularübermittlungen beeinträchtigen, was zu potenziellen Problemen bei der Verarbeitung von Kundendaten führen würde.
  _AC-11476 - [GitHub-Problem](https://github.com/magento/magento2/issues/38484) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38449)_
* __[Problem] Beheben von PHPDocs für \Magento\Framework\Data\Collection::getItemById__
Die PHPDocs für die Methode \Magento\Framework\Data\Collection::getItemById wurden aktualisiert, um null als möglichen Rückgabetyp einzuschließen und Probleme mit statischen Analyse-Tools zu beheben. Zuvor wurde in den PHPDocs der Methode nicht null als möglicher Rückgabetyp angegeben, was zu Warnungen oder Fehlern bei der statischen Analyse führte, wenn die Methode in bedingten Anweisungen verwendet wurde.
  _AC-11489 - [GitHub-Problem](https://github.com/magento/magento2/issues/38485) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38439)_
* __[Problem] Nur gültige Voreinstellungen während der`setup:di:compile`__ zulassen
Das System gibt jetzt während des `setup:di:compile`-Befehls einen Fehler aus, wenn eine Voreinstellung für eine Klasse erstellt wird, die nicht vorhanden ist oder speziell ausgeschlossen wurde, sodass nur gültige Voreinstellungen zulässig sind. Zuvor schlugen diese Szenarien im Hintergrund fehl und machten möglicherweise alle Plug-ins, die mit den ursprünglichen Klassen verknüpft sind, unbrauchbar.
  _AC-11592 - [GitHub-Problem](https://github.com/magento/magento2/issues/38517) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33161)_
* __Magento beim Versuch, die schreibgeschützte Eigenschaft in der __wakeup-Methode von LoggerProxy zu ändern__
Das System ermöglicht jetzt die Änderung von zuvor schreibgeschützten Eigenschaften in der __wakeup-Methode von LoggerProxy, um einen reibungslosen Betrieb zu gewährleisten, ohne die Benutzer zu zwingen, eine Problemumgehung zu verwenden. Zuvor hatte der Versuch, den Wert einer schreibgeschützten Eigenschaft in der WakeUp-Methode __ LoggerProxy neu zuzuweisen, Probleme verursacht.
  _AC-11651 - [GitHub-Problem](https://github.com/magento/magento2/issues/38526) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __[Problem] AC-2039 AC-1667 Upgrade TinyMCE-Referenzen__
Die tinymce-neueste Version wurde in composer.json aktualisiert.
  _AC-11681 - [GitHub-Problem](https://github.com/magento/magento2/issues/38533) - [GitHub-Code-](https://github.com/magento/magento2/pull/36543) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b34c0a75)_
* __ChangelogBatchWalker funktioniert nicht in mehreren Threads__
Das System unterstützt jetzt Process Fork für die MView-Indizierung, wodurch Fehler während der Indexerausführung bei der Ausführung auf mehreren Threads verhindert werden. Zuvor führte das Ausführen von ChangelogBatchWalker auf mehreren Threads zum Löschen von Tabellen, die von anderen Threads verwendet wurden, was einen Fehler während der Indexerausführung verursachte.
  _AC-11696 - [GitHub-Problem](https://github.com/magento/magento2/issues/38246) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38248)_
* __[Problem] Umbenennen einer falsch benannten Variablen__
Das System benennt nun die Variable korrekt, die den Betrag an Geld enthält, der noch zurückerstattet werden kann, um Verwirrung beim Debugging zu vermeiden. Zuvor wurde diese Variable fälschlicherweise als totalRefund bezeichnet, was zu Missverständnissen für Entwickler führen konnte.
  _AC-11781 - [GitHub-Problem](https://github.com/magento/magento2/issues/38609) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36205)_
* __[Problem] Übergeben Sie benutzerdefinierte Attribute über XML an den aktuellen Link__
Das System ermöglicht jetzt die Übergabe benutzerdefinierter Attribute über XML an den aktuellen Link, um sicherzustellen, dass diese Attribute korrekt angezeigt werden, auch wenn der Link die aktuelle Seite ist. Zuvor wurden keine benutzerdefinierten Attribute für den aktuellen Seitenlink angezeigt, da die Methode getAttributesHtml() für den aktuellen Link nicht verwendet wurde.
  _AC-11809 - [GitHub-Problem](https://github.com/magento/magento2/issues/38500) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30070)_
* __Der integrierte FPC-Cache ist in Version 2.4.7 für einige Konfigurationen fehlerhaft__
Das System speichert Seiten jetzt korrekt zwischen, wenn der Parameter MAGE_RUN_CODE festgelegt ist, was eine optimale Leistung gewährleistet. Zuvor wurden Seiten unter diesen Bedingungen nicht zwischengespeichert, was zu potenziellen Leistungsproblemen führte.
  _AC-11819 - [GitHub-Problem](https://github.com/magento/magento2/issues/38626) - [GitHub-Code-](https://github.com/magento/magento2/pull/38646) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __[Problem] Behebung von Inkonsistenzen bei der Ausnahmebehandlung zwischen dem Entwickler- und dem Produktionsmodus__
Das System verarbeitet jetzt Ausnahmen konsistent zwischen dem Entwickler- und dem Produktionsmodus, wodurch eine unerwartete Weiterleitung zur Anmeldeseite verhindert wird, wenn eine Ausnahme ausgelöst wird. Zuvor konnte eine Inkonsistenz bei der Ausnahmebehandlung zu einer Umleitung zur Anmeldeseite im Produktionsmodus führen, anstatt die Ausnahmemeldung anzuzeigen.
  _AC-11829 - [GitHub-Problem](https://github.com/magento/magento2/issues/38639) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37712)_
* __Ersetzen Übersetzung von &quot;PayPal Konto&quot; in token_Liste.phtml__
Das System kennzeichnet nun den Abschnitt für tokenisierbare Konto Zahlungsmethoden als &quot;Konto&quot; anstelle von &quot;PayPal Konto&quot; in der Seite &quot;Gespeicherte Zahlungsmethoden&quot;, was ihn repräsentativer für seine Funktion macht. Zuvor war dieser Abschnitt ausdrücklich als &quot;PayPal-Konto&quot; gekennzeichnet, was irreführend war, als andere tokenisierbare Konto Zahlungsmethoden hinzugefügt wurden.
  _AC-11852 - [GitHub-Problem](https://github.com/magento/magento2/issues/35622) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37959)_
* __Die Abwärtskompatibilität der Magento\Catalog\Model\ProductRepository-Klasse__ ist verloren gegangen.
Die ProductRepository-Klasse behält nun die Abwärtskompatibilität bei, indem die Initialization Helper-Klasse als zweiter Parameter wiederhergestellt wird, wodurch sichergestellt wird, dass Module, die sich von dieser Klasse erstrecken, wie erwartet funktionieren. Zuvor führte das Entfernen des Initialisierungshilfsprogramms aus dem Konstruktor in der ProductRepository-Klasse zu einem Verlust der Abwärtskompatibilität, sodass Benutzer gezwungen waren, eine Problemumgehung zu verwenden.
  _AC-11874 - [GitHub-Problem](https://github.com/magento/magento2/issues/38669)_
* __[Problem] Statische Inhaltsbereitstellung - Typfehler__
Das System verarbeitet jetzt leere LESS-Dateien während der Bereitstellung statischer Inhalte korrekt und zeigt die Fehlermeldung „LESS-Datei ist leer“ an. Zuvor wurde ein Fehler vom Typ „Falsch“ ausgelöst, wenn während der Bereitstellung eine leere LESS-Datei auftrat.
  _AC-11905 - [GitHub-Problem](https://github.com/magento/magento2/issues/38682) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38683)_
* __[Problem] [Anzeigen] Zusätzlicher Leerraum im Link- und Skript-Tag wurde entfernt__
Das System stellt jetzt sicher, dass es keine zusätzlichen Leerzeichen in den Link- und Skript-Tags gibt, was einen saubereren und effizienteren Code bietet. Zuvor konnten Dublette Leerzeichen zwischen Attributen in den verknüpfen- und Skript-Tags gefunden werden.
  _AC-12002 – [GitHub-Problem](https://github.com/magento/magento2/issues/32920) – [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32919)_
* __[Problem] Vermeiden Sie eine Fehlkonfiguration in der Endlosschleife__
Das System vermeidet jetzt eine Endlosschleife, indem es in virtuellen Typkonfigurationen die selbstreferenzielle Zuordnung verhindert. Dadurch wird sichergestellt, dass die Anwendung beim Versuch, einen selbstverweisenden Knoten zu dereferenzieren, nicht in einer Endlosschleife hängt. Wenn eine Konfiguration eines virtuellen Typs zuvor selbstverweisend war, würde dies dazu führen, dass sich die Anwendung unbegrenzt dreht.
  _AC-12127 - [GitHub-Problem](https://github.com/magento/magento2/issues/38822) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38794)_
* __Der Objekt-Manager wird nicht für Magento\Csp\Model\Mode\Data\ModeConfigured verwendet__
Das System verwendet nun den Objekt-Manager beim Erstellen des ModeConfiged-Objekts korrekt, sodass Plug-ins für dieses Objekt verwendet werden können. Zuvor wurde der Objekt-Manager nicht verwendet, was verhinderte, dass Plug-ins auf das ModeConfiged-Objekt angewendet wurden.
  _AC-12299 - [GitHub-Problem](https://github.com/magento/magento2/issues/38875) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38886)_
* __Falscher Kommentar zu Dokumentblöcken in Produkt- und Preiswarnhinweisen__
Der Blockkommentar für die Methode deleteCustomer in den Warnhinweisen für Warenbestand und Preise wurde korrigiert, um genau widerzuspiegeln, dass die Methode alle Warenbestand- oder Preiswarnhinweise löscht, die mit einer bestimmten Kundin oder einem bestimmten Kunden und einer bestimmten Website verbunden sind, nicht mit dem Kunden von der Website. Zuvor wurde in dem Kommentar fälschlicherweise angegeben, dass die Methode zum Löschen eines Kunden von der Website war.
  _AC-12540 - [GitHub-Problem](https://github.com/magento/magento2/issues/38939) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39001)_
* __[Problem] Verwenden Sie die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration__
Das System verwendet jetzt die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration, wodurch die Netzwerkübertragung und der Overhead von Daten, der von einer bestimmten Code-Version abhängt, reduziert werden. Diese Änderung verhindert das Überschreiben des Caches in freigegebenen Instanzen beim Austausch von Containern, was zu verbesserter Stabilität und reduzierten Ausfallzeiten führt. Zuvor verwendeten bestimmte Kernklassen gemeinsame Konfigurationstypen, was aufgrund von Unterschieden in den Codeversionen über mehrere Server hinweg zu Cache-Überschreibungen oder Anwendungsausfällen führen konnte.
  _AC-12594 - [GitHub-Problem](https://github.com/magento/magento2/issues/38785) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29954)_
* __[Problem] Verweise auf Dateien aus ExtJS entfernen, die aus e1ccdb entfernt wurden…__
Das System entfernt jetzt Verweise auf Dateien aus ExtJS, die zuvor entfernt wurden, wodurch Fehler in der Browser-Konsole und der Systemprotokolldatei vermieden werden. Zuvor verursachten diese Verweise Fehler, da die referenzierten Dateien nicht vorhanden waren.
  _AC-12597 - [GitHub-Problem](https://github.com/magento/magento2/issues/38960) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38951)_
* __[Problem] Kleinere Bereinigung: Fehlerhafte Verwendung von sprintf wurde behoben, es werden nur 2 Platzhalter verwendet…__
Das System verwendet nun die Sprintf-Funktion korrekt mit der entsprechenden Anzahl von Platzhaltern, was die Code-Sauberkeit und -Konsistenz verbessert. Zuvor wurde die Sprint-Funktion fälschlicherweise mit einem zusätzlichen Argument verwendet, was zwar keine größeren Probleme verursachte, aber nicht die richtige Verwendung war.
  _AC-12778 - [GitHub-Problem](https://github.com/magento/magento2/issues/39062) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38628)_
* __PHP 8.2.15 hat die FTP-Erweiterung entfernt__
Das System enthält jetzt die FTP-Erweiterung als Abhängigkeit in der Datei composer.json, wodurch die erfolgreiche Konfiguration von CSV-Importen über FTP sichergestellt wird. Zuvor wurde beim Versuch, CSV-Importe über FTP zu konfigurieren, ein Fehler ausgelöst, da die FTP-Erweiterung im PHP-Paket fehlt.
  _AC-12857 - [GitHub-Problem](https://github.com/magento/magento2/issues/39083) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problem] Behebt den Verweis falscher Klassen in Magento-Modulen.__
Das System verweist jetzt korrekt auf Klassen in -Modulen, um einen reibungsloseren Betrieb zu gewährleisten und Abstürze aufgrund nicht vorhandener Klassen zu verhindern. Dazu gehören eine Fehlerbehebung im Indexer- und Creditmemo-Modul sowie die Implementierung der HttpGetActionInterface-Klasse in der PrintAction-Klasse. Zuvor führten falsche Klassenverweise zu Fehlern und potenziellen Systemabstürzen, und bestimmte Funktionen, wie der Dateiname für CreditMemo-PDF-Dateien und die Neuindizierung von Aktien, funktionierten nicht wie erwartet.
  _AC-12869 - [GitHub-Problem](https://github.com/magento/magento2/issues/39126) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37784)_
* __Möglichkeit, Bereich für `dev:di:info` CLI-Befehl zu definieren__
Das System ermöglicht es Entwicklerinnen und Entwicklern jetzt, einen Bereich für den `dev:di:info` CLI-Befehl zu definieren, wodurch der Entwicklungs- und Debugging-Prozess verbessert wird. Zuvor konnte dieser Befehl nur Informationen für den Bereich GLOBAL anzeigen.
  _AC-12964 - [GitHub-Problem](https://github.com/magento/magento2/issues/38758) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38759)_
* __[Problem] Fügen Sie die Eigenschaft isMultipleFiles zur Vorlage für das Bildformularelement hinzu__
Diese Fehlerbehebung verhindert, dass die Schaltfläche „Nach Bild suchen oder Bild hierher ziehen“ ausgeblendet wird, wenn ein Bild in einem Bildelement mit mehreren Dateien hinzugefügt wird.
  _AC-13149 - [GitHub-Problem](https://github.com/magento/magento2/issues/39219) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36325)_
* __setup:Das Upgrade schlägt aufgrund von Änderungen an Zeichensatz und Sortierung mit MariaDB 11.4 fehl__
  _AC-13247_
* __[Problem] Entfernen Sie alle Marketing-GET-Parameter, um den Cache zu minimieren__
Das System entfernt jetzt alle Marketing-GET-Parameter, um die Cache-Nutzung zu optimieren, und spiegelt die Logik wider, die bei der Verwendung von Varnish verwendet wird. Zuvor konnten diese Parameter zu einer Aufblähung des Cache und einer verringerten Leistung führen.
  _AC-13279 - [GitHub-Problem](https://github.com/magento/magento2/issues/39266) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39099)_
* __[Problem] [PHPDOC] Fehlerbehebung für fehlerhafte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries()__
Das PHPDoc für die Methode AllowedCountries::getAllowedCountries() wurde korrigiert, um genaue Informationen bereitzustellen und so die Klarheit und Nützlichkeit der Dokumentation zu verbessern. Bisher enthielt das PHPDoc für diese Methode falsche Informationen, was zu Verwirrung oder Missbrauch der Methode führen konnte.
  _AC-13345 - [GitHub-Problem](https://github.com/magento/magento2/issues/39246) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39241)_
* __[Problem] Entfernt Code für PHP-Versionen, die wir nicht mehr unterstützen.__
Entfernen von Code für PHP-Versionen, die in Magento nicht mehr unterstützt werden
  _AC-13348 - [GitHub-Problem](https://github.com/magento/magento2/issues/39361) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39202)_
* __[Problem] ImageMagick-Adapter mit PHP8 kompatibel machen (implizite Konvertierung von float zu int)__
Das System stellt nun die Kompatibilität mit PHP8 sicher, indem es bei der Berechnung der Bildabmessungen die Gleitkommazahlen korrekt verarbeitet und Fehler durch implizite Konvertierung von float in int verhindert. Zuvor konnte die Berechnung der Bildabmessungen zu Gleitkommazahlen führen, die bei impliziter Rundung einen Fehler verursachen würden.
  _AC-13417 - [GitHub-Problem](https://github.com/magento/magento2/issues/39402) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37362)_
* __[Problem] [PHPDOC] Schlechtes phpdoc beheben Magento\Framework\App\Config\ScopeConfigInterface__
Durch diese Aktualisierung werden die PHPDoc-Anmerkungen in Magento\Framework\App\Config\ScopeConfigInterface korrigiert, damit sie den Typ des $scopeCode-Arguments für die Methoden getValue und isSetFlag genau widerspiegeln.
  _AC-13537 - [GitHub-Problem](https://github.com/magento/magento2/issues/39492) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39199)_
* __Magento\Framework\Filesystem\Driver\Http hängt von der Ursachenphrase ab OK__
Die Prüfung der „OK“-Phrase wurde aus Magento\Framework\Filesystem\Driver\Http::isExists entfernt.
  _AC-13725 - [GitHub-Problem](https://github.com/magento/magento2/issues/39546) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39558)_
* __Der Rasterindizierer des Kunden funktioniert im Zeitplanmodus nicht ordnungsgemäß__
Frühere Kundenraster wurden sofort aktualisiert, aber nach der Fehlerbehebung wird das Kundenraster nach der Cron-Ausführung aktualisiert, es wird jedoch nicht sofort wiedergegeben.
  _AC-13810 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1da9ba6f)_
* __Tippfehler in einer JS-Datei.__
Das System verwendet nun den Begriff „Abonnenten“ in der JavaScript-Datei korrekt, um eine ordnungsgemäße Funktionalität der zugehörigen Funktionen sicherzustellen. Zuvor führte ein typografischer Fehler in der JavaScript-Datei zur falschen Verwendung des Begriffs „Abonnenten“.
  _AC-6754 - [GitHub-Problem](https://github.com/magento/magento2/issues/36163) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36171)_
* __[Problem] Entfernen eines verbotenen `@author`-Tags__
Das System hält sich jetzt an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.
  _AC-8353 - [GitHub-Problem](https://github.com/magento/magento2/issues/37253) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37003)_
* __[Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Customer` (Teil 2)__
Das System hält sich jetzt an den Kodierungsstandard, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.
  _AC-8356 - [GitHub-Problem](https://github.com/magento/magento2/issues/37250) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37000)_
* __Durch Leerzeichen in der EditorConfig-Syntax wird die Regel für [{composer,auth}.json]__
Nach der Behebung eines Syntaxfehlers in editorconfig wendet das System jetzt einen Einzug mit vier Leerzeichen korrekt auf die Dateien composer und auth.json an. Aufgrund eines Leerzeichens in der EditorConfig-Syntax wurden diese Dateien zuvor falsch mit einem Einzug aus zwei Leerzeichen formatiert.
  _AC-8659 - [GitHub-Problem](https://github.com/magento/magento2/issues/37394) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37395)_
* __[Problem] Verbesserung der Cron-Fehlerprotokollierung__
Das System erfasst und protokolliert jetzt sowohl STDERR als auch STDOUT für Cron-Prozesse und liefert wertvolle Diagnoseinformationen in Szenarien, in denen Cron-Prozesse fehlschlagen. Zuvor wurden Fehlermeldungen innerhalb von Cron-Prozessen nicht aufgezeichnet, und STDERR und STDOUT für Cron-Gruppen, die in separaten Prozessen ausgeführt werden, gingen verloren.
  _AC-8662 - [GitHub-Problem](https://github.com/magento/magento2/issues/37453) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32690)_
* __[Problem] Fügt der Ausgabe bestimmter Setup-Befehlszeilenbefehle einige weitere Farben hinzu__
Das System fügt jetzt der Ausgabe bestimmter Befehle der Befehlszeilenschnittstelle (Command Line Interface, CLI) mehr Farben hinzu, was die Lesbarkeit und das Benutzererlebnis verbessert. Bisher war die Ausgabe dieser Befehle aufgrund fehlender Farbdifferenzierung schwieriger zu lesen.
  _AC-8984 - [GitHub-Problem](https://github.com/magento/magento2/issues/29335) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29298)_
* __Beim Upgrade von Magento wird „general/region/state_required“ zurückgesetzt, wenn ein neues Land mit dem erforderlichen Bundesland bzw. der erforderlichen Region hinzugefügt wird.__
Das System fügt das geänderte Land jetzt nur noch dann zur Konfiguration „general/region/state_required“ hinzu, wenn ein neues Land mit den erforderlichen Status hinzugefügt wird. Dadurch wird jede Unterbrechung des benutzerdefinierten Codes vermieden, bei der davon ausgegangen wird, dass die Region deaktiviert ist. Zuvor würde das Hinzufügen eines neuen Landes mit erforderlichen Status die Konfiguration „general/region/state_required“ auf Standardländer mit einem erforderlichen Status zurücksetzen und möglicherweise den Shop zerstören.
  _AC-9630 - [GitHub-Problem](https://github.com/magento/magento2/issues/37796) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38076)_
* __Unterschied in weniger Kompilierung zwischen php &amp; nodejs Bibliothek (grunt) mit komplizierten `calc` Ausdrücken__
Behebung des Unterschieds in weniger Kompilierung zwischen PHP &amp; NodeJS Library (grunt) nach dem Update wikimedia/less.php:^5.x
  _AC-9712 - [GitHub-Problem](https://github.com/magento/magento2/issues/37841) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b34c0a75)_
* __Fehler „Basistabelle oder Ansicht nicht gefunden“ tritt auf, wenn eine partielle Indizierung ausgeführt wird__
Die teilweise Neuindizierung funktioniert jetzt mit einem großen Änderungsprotokoll im Falle einer sekundären DB-Verbindung korrekt
  _ACP2E-2692 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Probleme nach dem Upgrade von MariaDB auf 10.5.1 oder höher__
Es wurde ein Problem behoben, bei dem Datums-/Uhrzeitwerte in einer DB nach dem MySQL-Upgrade in 0000-00-00 00:00:00 konvertiert wurden
  _ACP2E-2844 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a12063bd)_
* __Nicht übereinstimmender Typ beim Datenvergleich bei der Überprüfung, ob die Daten Änderungen aufweisen__
Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, führt eine strikte Typübereinstimmung durch.
  _ACP2E-2855 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud]-Import kann nicht mit Verzeichnis-Var verwendet werden__
Produkt kann unabhängig vom Dateinamen erfolgreich importiert werden.
  _ACP2E-2959 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Auf dem iPad mini werden das Menü und die Kopfzeile als Mobilgerät geladen. Stattdessen sollten sie als Desktop geladen werden.__
Das System behandelt Geräte mit einer Breite von 768 Pixel jetzt als Desktop, um sicherzustellen, dass das Menü und die Kopfzeile korrekt geladen werden. Zuvor wurden Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobilansicht geladen wurden.
  _ACP2E-2966 - [GitHub-Code-](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __Fehler „Basistabelle oder Ansicht nicht gefunden“ beim Ausführen von mview cron während eines DDL-Vorgangs__
Das System verarbeitet jetzt Datenbankaktualisierungsvorgänge korrekt, während das mview-Update im Hintergrund ausgeführt wird, wodurch das Auftreten von „Basistabelle oder Ansicht nicht gefunden“-Fehlern verhindert wird. Zuvor konnten einige Datenbankaktualisierungsvorgänge zu dem Fehler „Basistabelle oder Ansicht nicht gefunden“ führen, wenn die Aktualisierung von mview gleichzeitig ausgeführt wurde.
  _ACP2E-3046_
* __Die Änderung der Spaltenlänge über db_schema.xml funktioniert nicht bei Fremdschlüsseln__
Das Ändern der Spalte mit dem Fremdschlüssel über das deklarative Schema verursacht jetzt keine Fehler mehr bei MariaDB
  _ACP2E-3230 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Einige der Beziehungsdatensätze werden beim Speichern des Bestelldatensatzes in der DB gespeichert__
Vor der Behebung wurden unnötige UPDATE-Abfragen ausgelöst, die die Leistung beeinträchtigen können. Nach der Fehlerbehebung wurden die unnötigen UPDATE-Abfragen entfernt.
  _ACP2E-3361 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] In Admin gibt es viele JavaScript-Fehler in der Konsole__
Zuvor gab es im Admin-Bedienfeld viele JavaScript-Fehler in der Konsole. Im Admin-Bedienfeld gibt es nun keine JavaScript-Fehler mehr in der Konsole, und alle standardmäßigen JavaScript-Funktionen werden problemlos ausgeführt.
  _ACP2E-3375 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_
* __[Cloud] Magento: Warteschlangennachricht wurde gelöscht__
Warteschlangennachrichten werden jetzt ordnungsgemäß gelöscht. Vor der Fehlerbehebung hätten, da das SQL-Warteschlangensystem verwendet wurde, neue Nachrichten gelöscht werden können, wenn die Bereinigungswarteschlangennachricht gleichzeitig ausgeführt wurde.
  _ACP2E-3387 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Entsprechende Cache-Schlüsseleinträge sind in Cache-Tags nicht verfügbar, daher funktioniert die Cache-Bereinigung nicht ordnungsgemäß__
Der LUA-Modus ist jetzt standardmäßig für den Redis-Cache-Garbage Collector aktiviert, um Race-Bedingungen zu verhindern
  _ACP2E-3537 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a52ff98f)_
* Der Wert für __MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK wird ignoriert__
Nach der Fehlerbehebung wird eine auf „false“ gesetzte ENV-Variable als bool/false und nicht als String „false“ behandelt.
  _ACP2E-3681 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

* __[Problem] Die Unterstützung benutzerdefinierter Skalartypen für das GraphQL-Schema wurde eingeführt__
Das System unterstützt jetzt benutzerdefinierte Skalartypen für GraphQL-Schemata, sodass Entwickelnde benutzerdefinierte Skalartypen und Implementierungen definieren können. Diese Funktion kann besonders nützlich sein, um Werte auszudrücken, die möglicherweise einer Validierung bedürfen, z. B. HTML, E-Mails, URLs, Daten usw., und für komplexere Fälle wie EAV-Attribute. Zuvor unterstützte das System nicht die Verarbeitung von benutzerdefinierten Skalartypen in GraphQL.
  _AC-7976 - [GitHub-Problem](https://github.com/magento/magento2/issues/36877) - [GitHub-Code-](https://github.com/magento/magento2/pull/34651) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

### Framework, Produkt

* __2.4.8-beta1 EE-Berichte werden aufgrund einer Magento-Ausnahme nicht generiert__
  _AC-13011_

### Framework, UI-Framework

* __Möglichkeit, den Konfigurationswert zu überschreiben, selbst wenn er gesperrt ist__
Zuvor konnte die Design-Konfiguration nicht über den Befehl bin/magento:set festgelegt werden und gesperrte Werte konnten durch Manipulation des Formulars, das sie anzeigte, geändert werden. Nach dem Fix können gesperrte Werte, die von cli mit —lock-env oder —lock-conf gesetzt wurden, nicht mehr aktualisiert werden.
  _ACP2E-3324 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

* __Magento_GraphQL führt Header durch, die verarbeitet werden, selbst wenn der Header-Wert die Validierung nicht besteht__
Das System stellt jetzt sicher, dass die Header-Verarbeitung nur einmal und nur dann ausgeführt wird, wenn der Header-Wert die Validierung besteht, was die Sicherheit erhöht und potenzielle Sicherheitslücken verhindert. Zuvor wurde die Header-Verarbeitung auch dann ausgeführt, wenn der Header-Wert die Validierung nicht bestanden hat, was zu potenziellen Sicherheitslücken und unerwartetem Verhalten aufgrund der doppelten Verarbeitung von Header-Werten führte.
  _AC-11729 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __Physische Geschenkkartenoptionen haben nicht die richtige Sortierreihenfolge__
Das System sortiert jetzt bei der Abfrage über GraphQL die Optionen physischer Geschenkkartenprodukte korrekt, wodurch eine konsistente Darstellung mit dem Luma-Design gewährleistet ist. Zuvor war die Sortierreihenfolge gemäß dem Luma-Design falsch, was zu einer falschen Anzeige und Sortierung von Optionen wie Absendername, Empfängername und Betrag führte.
  _AC-8951 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_
* __[GraphQL] Resolver-Cache wird beim Erstellen/Bearbeiten/Verschieben/Löschen einer Staging-Aktualisierung ungültig__
Das System stellt jetzt sicher, dass der Resolver-Cache nicht beim Erstellen, Bearbeiten, Verschieben oder Löschen eines Staging-Updates ungültig gemacht wird, sondern nur, wenn das Staging-Update auf die Entität angewendet wird. Zuvor wurde der Resolver-Cache vorzeitig invalidiert, noch bevor die Staging-Aktualisierung angewendet wurde, was zu unnötigen Cache-Invalidierungen führte.
  _AC-9157 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Fastly-Cache für die Aktualisierung des Inhalts-Staging nicht gelöscht__
Jetzt wird der Antwort-Cache für GraphQL mit PageBuilder-Inhalt ungültig, wenn die Entitäten für den PageBuilder-Inhalt aktualisiert werden.
  _ACP2E-2642 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Deaktivieren der mehrschichtigen Navigation - Die Aggregation wird nicht aus GraphQL entfernt__
Das Problem wurde behoben, nachdem die Prüfung bei der Anforderung einer Produktsuche mit Kategorieaggregationen über eine GraphQL-Abfrage in der Admin-Konfigurationseinstellung von „Katalog > Mehrschichtige Navigation > Kategoriefilter anzeigen“ angewendet wurde.
  _ACP2E-2653 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/12e071c3)_
* __GraphQL-Produktanruf, der den Preisfilter {from:„0“} enthält, gibt kein Ergebnis zurück__
Zuvor gab GraphQL-Produkte, die mit dem Filter nach Nullpreisen suchten, aufgrund einer ausgelösten Ausnahme überhaupt keine Ergebnisse zurück. Jetzt gibt die Suche die erwarteten Ergebnisse zurück.
  _ACP2E-2928 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_
* __Übersetzungen für Kundenrückgabeattribute werden für die jeweilige StoreView nicht in der GraphQL-API angezeigt__
Übersetzungen für Kundenrückgabeattribute werden in der GraphQL-API für die jeweilige StoreView angezeigt.
Zuvor wurden Kundenrückgabeattribute für die jeweilige StoreView nicht in der GraphQL-API angezeigt.
  _ACP2E-2974 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] Beschädigter GraphQL-Aufruf für getPurchaseOrder mit Knotenanführungszeichen__
Der GraphQL-Aufruf für die Bestellung kann die Aufgabe ausführen, ohne dass interne Server-Fehler auftreten.
  _ACP2E-3128 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __[Cloud] Konfigurierbare Produkte werden auf der Produktions-Site nicht angezeigt, wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist__
Das System zeigt jetzt konfigurierbare Produkte auf der Website korrekt an, auch wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist, sondern in bestimmten Store-Ansichtsbereichen.
Wenn ein Produkt zuvor in „Alle Store-Ansichten“ deaktiviert und nur in bestimmten Store-Ansichtsbereichen aktiviert wurde, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, was dazu führt, dass das Produkt nicht richtig angezeigt wird.
  _ACP2E-3184 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/3f300077)_
* __[Cloud] GraphQL-Produkte mit Fehler, wenn dasselbe einfache Produkt mehreren konfigurierbaren Produkten zugewiesen wurde__
Zuvor gab GraphQL bei separaten konfigurierbaren Produkten mit demselben einfachen Produkt einen Fehler zurück. Nachdem diese Fehlerbehebung angewendet wurde, gibt GraphQL ohne Fehler Ergebnisse für verschiedene konfigurierbare Produkte mit demselben einfachen Produkt zurück.
  _ACP2E-3190 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/148c3ead)_
* __[Cloud] Problem mit der Benutzerauthentifizierung und dem Site-übergreifenden Token-Zugriff bei der Einrichtung mehrerer Sites__
GraphQL-Kundeninformationen und Warenkorbabfragen bei der Einrichtung mehrerer Websites überprüfen, ob der Kunde auf einer nicht standardmäßigen Website vorhanden ist.
Zuvor funktionierte die Abfrage, ohne sicherzustellen, dass der Kunde bei der Einrichtung mehrerer Sites auf einer nicht standardmäßigen Website vorhanden ist.
  _ACP2E-3215 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __GraphQL-Artikel im WarenkorbV2-Paginierung funktioniert nicht ordnungsgemäß__
Das Problem wurde behoben, indem der richtige Wert für das aktuelle Seitenargument in der Sammlungsabfrage übergeben wurde. Zuvor wurde der falsche Wert übergeben, um die aktuelle Seite festzulegen, was das Problem verursachte.
  _ACP2E-3253 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_
* __[GRAPHQL]-Modellwert sollte beim Abrufen von customerCart angegeben werden__
Die GraphQL-Abfrage „customerCart“ kann jetzt einen leeren Warenkorb erstellen, selbst wenn das Angebot nicht in der Datenbank verfügbar ist. Zuvor schlug dieser Vorgang aufgrund von Problemen mit der Ländervalidierung beim Erstellen des leeren Warenkorbs fehl.
  _ACP2E-3255 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[GraphQL] Wunschlistenelemente sind über GraphQL sichtbar, aber nicht in der Storefront__
Wunschzettel-Produkte, die nicht ordnungsgemäß aufgeführt werden, wenn sie über GraphQL angefragt werden. Jetzt werden Produkte auf der Wunschliste basierend auf dem bereitgestellten Store-Kontext gefiltert.
  _ACP2E-3380 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_
* __[GraphQL] E-Mail-Inkonsistenz des Kennworts zwischen Inhalt und Betreff/Link zurücksetzen__
Das Problem wurde behoben, indem der richtige Speicher simuliert wurde, in dem das Konto des Kunden beim Senden der Anforderung zum Zurücksetzen des Kennworts registriert ist, unabhängig vom Website-Speicher.
  _ACP2E-3404 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_
* __[Cloud]-Produkte Die GraphQL-Abfrage gibt verwandte Produkte zurück, die der aktuellen Website nicht zugewiesen sind__
Zuvor wurden für GraphQL-Abfragen Produkte, die mit mehreren Stores verbunden sind, für die Produktabfrage nicht richtig angezeigt. Nachdem diese Fehlerbehebung angewendet wurde, werden für Produkte in der GraphQL-Abfrage Multistore-bezogene Produkte entsprechend angezeigt.
  _ACP2E-3419 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __Die Verwendung der falschen Store-ID in der GraphQL-Kopfzeile verursacht einen schwerwiegenden Speicherfehler__
Das Senden von falschem Speicher-Code in einer GraphQL-Anfrage führt nicht mehr zu übermäßigem Speicherverbrauch.
  _ACP2E-3447 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Cloud] 500-Antwort auf leere GraphQL-Antwort auf 2.4.7__
Nach der Behebung werden ungültige GraphQL-Anfragen nicht mehr in der Datei Exception.log protokolliert.
  _ACP2E-3467 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_
* __[Cloud] Probleme mit der GraphQL-API__
Vor der Fehlerbehebung mithilfe des GraphQL-Anwendungsservers hat die Kundenadressanfrage nicht die neuesten Daten zurückgegeben.
  _ACP2E-3492 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Deaktiviertes Produkt wird weiterhin in verwandten, Upsell-, Crosssell-Elementen in der GraphQL-Abfrage angezeigt__
GraphQL bietet jetzt eine korrekte Antwort für deaktivierte verwandte Produkte, Upsell- und Crosssell-Produkte
  _ACP2E-3505 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_
* __[CLOUD]: GraphQL-Fehler Interner Server-Fehler placeOrder-Mutation__
Die „placeOrder“-Mutation mit Coupon-Code-Informationen in der Anfrage löst keine interne Fehlerausnahme mehr aus, die Bestellung wurde erfolgreich platziert. Zuvor schlug er mit „Interner Server-Fehler“ fehl.
  _ACP2E-3647 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_
* __Der Rabatt-Prozentsatz wird nicht für Bundle-Produkte mit dynamischem Preis berechnet__
Korrektur hinzugefügt für „DISCOUNT_PERCENTAGE“ von „product.price_details“, bei der für Bundle-Produkte mit aktiviertem dynamischen Preis und angewendetem Rabattcoupon der richtige Wert angezeigt wird.
  _LYNX-426_
* __Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist__
Es wurde das Problem behoben, dass Paketprodukte weiterhin „IN_STOCK“ zeigten, auch wenn eines ihrer Paketprodukte nicht vorrätig war.
  _LYNX-485_
* __NOT_AVAILABLE_MESSAGE und ONLY_X_LEFT_IN_STOCK zeigen nicht denselben verfügbaren Bestand__
Es wurde das Problem behoben, bei dem die Nachrichten not_available_message und only_x_left_in_stock inkonsistente Lagerverfügbarkeit zeigten
  _LYNX-486_
* __ORIGINAL_ROW_TOTAL-Feld gibt falschen Wert zurück__
Das Problem mit dem Feld original_row_total wurde behoben, das falsche Werte zurückgab, wenn benutzerdefinierte Optionen ausgewählt wurden
  _LYNX-488_
* __Die gruppierte Produktminiatur sollte gemäß der Konfiguration angezeigt werden.     .__
Das Problem wurde behoben, um sicherzustellen, dass die gruppierte Produktminiatur gemäß den Konfigurationseinstellungen angezeigt wird
  _LYNX-503_
* __Fehler bei der Abfrage von selected_options in OrderAddress__
AttributeSelectedOptions wurde in der GraphQL-Antwort in der Reihenfolge „custom_attributesV2“ aktualisiert.
  _LYNX-510_
* __original_item_price beinhaltet keine Rabatte__
Original_item_price wurde aktualisiert und enthält jetzt Rabatte.
  _LYNX-512_
* __Die Meldung „Nicht verfügbar“ zeigt nicht die verfügbare Lagermenge an__
Die Fehlermeldung und der Fehlercode für die AddProductsToCart-Mutation wurden behoben, sodass sie mit der Nachrichtenkonfiguration „nicht verfügbar“ übereinstimmen.
  _LYNX-530_
* __Status „OUT_OF_STOCK“ wird bei „Einfach“ mit benutzerdefinierten Optionen und Produkten mit Mehrfachauswahl zurückgegeben__
Der StockStatusProvider-Resolver im Inventar-Package wurde aktualisiert, um den stock_status für einfache Produkte mit benutzerdefinierten Optionen zu korrigieren.
  _LYNX-532_
* __Fehler (GQL): cart.itemsV2.items.product.custom_attributesV2 gibt einen Server-Fehler zurück__
Der Server-Fehler, der auftrat, wenn eine Warenkorbabfrage die benutzerdefinierten Attribute eines Produkts enthielt, wurde behoben, indem ein Produkt ohne benutzerdefinierte Attribute hinzugefügt wurde.
  _LYNX-533_
* __orders/date_of_first_order gibt immer null zurück__
Es wurde das Problem behoben, bei dem „orders“ > „date_of_first_order“ immer null zurückgab.
  _LYNX-536_
* __Der Kunde darf eine teilweise versendete Bestellung nicht stornieren können__
Die Validierung wurde hinzugefügt, um zu verhindern, dass Kunden eine teilweise versendete Bestellung stornieren.
  _LYNX-544_
* __Fehlercodes für die Stornierung von Bestellungen basierend auf der Fehlermeldung__
Die Fehler-Codes für die Stornierung von Bestellungen basieren nun auf der spezifischen Fehlermeldung.
  _LYNX-548_
* __Verschieben Sie die Eigenschaften, die sich auf Cookies beziehen, von privat nach geschützt zurück__
Setzt die Sichtbarkeit der Eigenschaften des Klassenkonstruktors Magento\Framework\App\PageCache\Version von privat auf geschützt zurück
  _LYNX-581_
* __Erhöhen Sie die maximale standardmäßige GraphQL-Abfragenkomplexität auf 1.000__
Die standardmäßige maximale GraphQL-Abfragekomplexität wurde von 300 auf 1.000 erhöht.
  _LYNX-600_
* __GQL - itemsV2 > Ursprüngliche Zeilensumme, Preisspanne Preise wird als $0.00 für herunterladbare Produkte mit Dateioptionen zurückgegeben, die separate Preise haben.__
Es wurde ein Problem behoben, bei dem herunterladbare Produkte mit aktivierten Kaufoptionen für separate Links 0 $ für itemsV2 > Ursprüngliche Zeilensumme und Preisspanne als 0,00 $ für Produkte mit Dateioptionen mit separaten Preisen zurückgaben.
  _LYNX-620_
* __Das Schema einer Tabelle, wenn erstellt wird, unterscheidet sich brandneu von dem beim Upgrade__
Es wurde ein Problem behoben, bei dem das Hinzufügen einer neuen VARCHAR-Spalte zu einer vorhandenen Tabelle Testfehler aufgrund von Schemaunterschieden zwischen Neuinstallationen und Upgrades verursachte. Die modifyColumn()-Methode verarbeitet jetzt VARCHAR-Spalten korrekt, indem sie den Standardzeichensatz und die Standardsortierung festlegt.
  _LYNX-711_
* __GraphQL-Kompatibilität für PHP-8.4 Version__
Es wurden GraphQL-Kompatibilitätsprobleme mit PHP 8.4 auf mehreren Resolvern behoben, wodurch eine reibungslose Funktionalität sichergestellt wurde. Betroffene Dateien in den Modulen CatalogRule, Customer, GiftMessage, GiftCard und GiftWrapping wurden aktualisiert.
  _LYNX-772_

### GraphQL, Inventar/MSI

* __Die MergeCart-Mutation löst eine Ausnahme aus, wenn Quell- und Zielkarten dieselben Bundle-Elemente enthalten__
&#39;-
  _ACP2E-2607 - [GitHub-Code-](https://github.com/magento/magento2/commit/c971859e) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, Inventar/MSI, Leistung

* __Site nach dem Upgrade nicht verfügbar__
Die Leistung beim Abrufen von Bundle-Produkten über GraphQL wurde verbessert.
  _ACP2E-1716 - [GitHub-Code-](https://github.com/magento/magento2/commit/ba25af8a) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Leistung

* __[GraphQL Resolver] Kundenresolverdaten werden nicht im Import ungültig gemacht__
Der Cache des GraphQL-Kundenauflösers wird jetzt erwartungsgemäß invalidiert, wenn ein Kunde durch Importe bearbeitet oder gelöscht wird. Zuvor wurde der Cache nicht ungültig gemacht, und Kundendaten konnten während des Imports bearbeitet oder gelöscht werden.
  _AC-9569 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Suche

* __Die Sortierung einer GraphQL-Produktliste nach mehreren Parametern funktioniert nicht__
Die Sortierung von Produkten nach mehreren Feldern in GraphQL funktioniert jetzt, wie in der Dokumentation beschrieben
  _ACP2E-2809 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_
* __Die GraphQL-Abfrage für die Produktliste ist auf insgesamt 10.000 Produkte beschränkt__
Nach der Fehlerbehebung ist das Suchergebnis nicht auf 10000 Produkte beschränkt, sondern es können alle Produkte abgerufen werden, die den Suchkriterien entsprechen, selbst wenn die Anzahl mehr als 10000 beträgt.
  _ACP2E-948 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, Test-Framework

* __Fehler beim Magento\GraphQl\App\GraphQlCustomerMutationsTest.php-Integrationstest__
&#39;-
  _ACP2E-3363 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### Import/Export

* __Problem beim Produktimport bei Bereitstellung mit benutzerdefiniertem Optionstyp: Datei (Erstelltes Produkt enthält keinen Preis für benutzerdefinierte Option und zeigt nur die erste angegebene Dateityperweiterung an)__
Das System importiert jetzt Produktdaten mit benutzerdefinierten Optionen vom Typ „Datei“ korrekt, um sicherzustellen, dass alle bereitgestellten Dateierweiterungen angezeigt werden und der Preis für die benutzerdefinierte Option enthalten ist. Wenn beim Produktimport zuvor eine benutzerdefinierte Option des Typs „Datei“ mit mehr als einer Dateierweiterung bereitgestellt wurde, wurde nur die erste Erweiterung angezeigt und der Preis für die benutzerdefinierte Option fehlte.
  _AC-12172 - [GitHub-Problem](https://github.com/magento/magento2/issues/38805) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38926)_
* __Falsche Ausführungszeit für Importvorgang im Importverlaufsraster__
Die Ausführungszeit des Importberichts ist korrekt unabhängig vom Admin-Gebietsschema.
  _ACP2E-2710 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Doppelte Kundinnen und Kunden mit derselben E-Mail-Adresse werden beim Import erstellt__
Wenn der Kunde importiert wird, während die Kontofreigabe auf „Global“ eingestellt ist, wird der importierte Kunde, der im System vorhanden ist, aktualisiert.
Zuvor importierter Kunde wurde dupliziert.
  _ACP2E-2737 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_
* __Import von Produkten hinzufügen/aktualisieren, die anpassbare Optionen duplizieren__
Das Problem wurde behoben, indem den Produktoptionen beim CSV-Import der richtige Store zugewiesen wurde.
Zuvor dem Admin-Store anstelle des entsprechenden Stores zugewiesen.
  _ACP2E-2902 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Kundendatum „created_at“ wird beim Export nicht in die Speicherzeitzone konvertiert__
Ein Datumswert der Spalte „created_at“ wird basierend auf der Zeitzone des Speichers im CSV-Abschnitt für den Kundenexport in das richtige Datumsformat konvertiert.
  _ACP2E-2990 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3056e9cb)_
* __[Cloud] Beim Überprüfen der Daten in Importdaten mithilfe von CSV wird ein Fehler angezeigt__
Beim Überprüfen der Daten während des CSV-Imports tritt kein Fehler auf. Zuvor war die angezeigte Fehlermeldung: „Wir können keinen Kunden finden, der diese E-Mail- und Website-Code in Zeile(n): 1 abgleicht“, wenn die Daten im Importabschnitt mithilfe von CSV von der Administratorin bzw. dem Administrator überprüft werden.
  _ACP2E-3165 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Importschaltfläche fehlt__
Beheben Sie das Problem fehlender Importschaltfläche nach Datenprüfungen mit richtigen und falschen Datensätzen in der CSV. Zuvor wird die Schaltfläche Importieren nicht angezeigt, nachdem Daten mit richtigen und falschen Datensätzen in der CSV-Datei geprüft wurden.
  _ACP2E-3172 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1819fe73)_
* __Exportierte Kundenadresse kann nicht importiert werden__
Der Import der Kundenadresse wird erwartungsgemäß fortgesetzt. Zuvor verlief die Validierung einer Kundenadressenimportdatei nicht, wenn Kundenkonten freigeben = global gilt, und es gibt zwei Websites, auf denen die Standardwebsite eine eingeschränkte Länderliste hat und die importierte Adresse für eine andere Website gilt, auf der die zulässigen Länder unterschiedlich sind
  _ACP2E-3382 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] Falsche Menge in CSV-Datei gab keinen Fehler zurück__
Beim Import von Lagerquellen wird nun ein Validierungsfehler für nicht numerische Werte in der Spalte Menge angezeigt. Zuvor führte der Import von Lagerbeständen mit nicht numerischem Wert in der Spalte „Menge“ dazu, dass die Menge auf 0 gesetzt wurde.
  _ACP2E-3448 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5b21b7af)_
* __Fehlermeldung zum Duplizieren des URL-Schlüssels, die beim Importieren eines Produkts generiert wird, ist nicht korrekt, wenn der URL-Schlüssel bereits zu einer Kategorie gehört__
Beim Überprüfen des Produktimports wird die richtige Fehlermeldung angezeigt, wenn ein Kunde versucht hat, ein Produkt zu importieren, obwohl der URL-Schlüssel des Produkts bereits zu einer Kategorie gehört.
  _ACP2E-3455 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_
* __Produktexport verursacht OOM auch bei 4G-Speicherbegrenzung__
Vor dieser Fehlerbehebung schlug der Produktexport fehl, wenn Produktattribute Tausende von Optionswerten hatten, selbst mit verfügbarem 4G-Speicher. Nach dieser Fehlerbehebung sollte der Produktexport den Export der CSV-Datei abschließen.
  _ACP2E-3475 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_
* __[Cloud] Importieren Sie Prozesse, die sich gegenseitig beeinflussen__
Es werden korrekte Meldungen angezeigt, wenn derselbe Admin-Benutzer zwei oder mehr Importvorgänge mit derselben Benutzersitzung durchführt.
  _ACP2E-3527 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_

### Import/Export, Leistung

* __[Cloud] Die Produktimportzeit wurde erheblich verlängert__
Vor der Fehlerbehebung wies der Katalogproduktimport mit über 10.000 Einträgen eine erhebliche Zeitbeeinträchtigung auf. Nach der Fehlerbehebung wird der Import des Katalogprodukts zeitnah ausgeführt.
  _ACP2E-3476 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/87d012e5)_

### Installieren und Verwalten

* __Magento-Upgrade schlägt auf MariaDB 11.4 + 2.4.8-beta1 fehl__
Das Upgrade sollte fehlerfrei durchgeführt werden.
  _AC-13242 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7b336d0a)_
* __Schaltfläche „VCL für Lack 7 exportieren“ im Admin-Bedienfeld__
Die Schaltfläche „VCL für Lack 7 exportieren“ wurde dem Admin-Bedienfeld hinzugefügt.
  _ACP2E-2102 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventar/MSI

* __Die Inventaraktualisierung des konfigurierbaren Produkts schlägt fehl, wenn die Datenbank Präfixe verwendet__
Das System aktualisiert jetzt das Inventar der konfigurierbaren Produkte korrekt, wenn die Datenbank Präfixe verwendet, wodurch Fehlermeldungen verhindert und sichergestellt wird, dass die richtige Menge gespeichert wird. Zuvor trat ein Fehler auf, wenn versucht wurde, die Lagermenge für einfache Produkte innerhalb eines konfigurierbaren Produkts zu speichern, wenn die Datenbank Präfixe verwendete.
  _AC-10750 - [GitHub-Problem](https://github.com/magento/magento2/issues/38045)_
* __Google-Google-API-Schlüssel funktioniert nicht beim Hinzufügen von Zuordnungen mit Attributen__
Das System unterstützt jetzt die neueste Google Maps-API-Version 3.56, sodass Benutzende erfolgreich einen Map-Inhaltsbaustein aus dem PageBuilder-Menü zum Staging hinzufügen können, ohne auf Fehler zu stoßen. Zuvor konnten Benutzende aufgrund von Kompatibilitätsproblemen mit der Google Maps API-Version keinen Zuordnungs-Inhaltsblock hinzufügen, was zu einer Fehlermeldung führte, dass etwas schiefgelaufen ist.
  _AC-11593 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_
* __Für einen Bestellartikel mit mehreren Quellen und beschädigter SKU kann keine Lieferung erstellt werden__
Früher, als Leerzeichen versehentlich in der SKU über die Datenbank hinzugefügt wurden, führt zu einem Fehler auf der Sendungsseite, der jetzt behoben ist, und das automatische Zuschneiden gilt als benutzerfreundlicher Fehler und es wurde keine Auswirkung gefunden. Daher wurde die Sendung erfolgreich erstellt.
  _AC-13922 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/c18eb5fa)_
* __[Testen] Bundle-Produkte mit 0 Inventar, das auf der Storefront angezeigt wird__
Das Bundle-Produkt wird nicht auf den zusätzlichen Websites angezeigt, die zusätzliche Lager verwenden.
  _ACP2E-1411_
* __[Cloud] Kritisches Problem bei der Produktliste mit leeren Platzierungen__
Das System zeigt jetzt Produktlisten korrekt ohne Leerzeichen an, wenn Produkte auf „Nicht vorrätig“ eingestellt sind, was eine konsistente und genaue Anzeige der verfügbaren Produkte gewährleistet. Zuvor führte das Festlegen eines Produkts auf „Nicht vorrätig“ dazu, dass ein leerer Bereich in der Produktliste angezeigt wurde, was das Layout störte und Kunden möglicherweise verwirrte.
  _ACP2E-2794 - [GitHub-Code-](https://github.com/magento/magento2/commit/ea79f7dd) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/b59e48ca)_
* __Bestellung kann nicht versendet werden, wenn MSI Pick Up Store aktiviert ist__
Verbesserte Inventarleistung der Versanderstellung bei vielen Quellen durch Abholung im Geschäft
  _ACP2E-3335 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Cron-Neuindizierung kann die Produktverfügbarkeit im Frontend nicht aktualisieren__
Zuvor waren Produkte im Frontend nicht vorrätig, nachdem der Auftragsstatus über die REST-API aktualisiert wurde. Nach der Aktualisierung des Auftragsstatus über die REST-API werden die Produkte nun als vorrätig angezeigt.
  _ACP2E-3355 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/e6fe0aa7)_
* __Das Hinzufügen von Bildern zum konfigurierbaren Modus funktioniert nicht, wenn MSI aktiviert ist.__
Der Bild-Upload für ein konfigurierbares Produkt funktioniert jetzt wie erwartet, wenn das Inventar-Modul verwendet wird. Zuvor funktionierte der Bild-Upload nicht
  _ACP2E-3357 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/fdf409aa)_
* __Problem mit Bundle Product + MSI in Clean M2.4.7-p3__
Zuvor konnte bei Inventar-Bundle-Produkten nach der Duplizierung mit demselben einfachen Produkt das einfache Produkt nicht gespeichert werden. Nachdem diese Fehlerbehebung angewendet wurde, kann das einfache Produkt ohne Ausnahmen erfolgreich gespeichert werden.
  _ACP2E-3470 - [GitHub-Problem](https://github.com/magento/magento2/issues/39358) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/0208e433)_

### Inventar/MSI, Suche

* __Alle Produkte werden mit [is_out_of_stock] = 1 indiziert, wenn die SKU nicht als durchsuchbares Attribut festgelegt ist__
Nach der Fehlerbehebung ist „is_out_of_stock“ im Katalogsuchindex korrekt, auch wenn die SKU nicht durchsuchbar ist.
  _ACP2E-3413 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5b21b7af)_

### Reihenfolge

* __Bildschirm „Übersicht Backend-Auftrag“: Rückstandsmenge nicht auf Bestellartikelebene sichtbar__
Das System zeigt jetzt die Anzahl der nachbestellten Artikel in der Spalte Menge auf dem Bildschirm „Auftragsübersicht“ des Backends an. Dadurch wird sichergestellt, dass Benutzende den Status aller Artikel in einer Bestellung genau verfolgen können. Zuvor wurde in der Spalte „Menge“ nur die Anzahl der bestellten, fakturierten und versandten Artikel angezeigt, nicht jedoch die Anzahl der nachbestellten Artikel.
  _AC-10828 - [GitHub-Problem](https://github.com/magento/magento2/issues/38252) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38320)_
* __[Problem] Falsche Store-ID im Renderer für die Bestelladresse verwendet__
Das System verwendet nun bei der Darstellung der Bestelladresse die einer Bestellung zugeordnete Speicher-ID korrekt, um sicherzustellen, dass die Adressen entsprechend ihrer jeweiligen Speicher-ID korrekt formatiert sind. Zuvor verwendete das System fälschlicherweise die aktuelle Store-ID, was zu einer falschen Adressformatierung führen konnte, wenn mehrere E-Mails zu Bestellungen aus verschiedenen Stores gesendet werden mussten.
  _AC-10994 - [GitHub-Problem](https://github.com/magento/magento2/issues/38412) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37932)_
* __JoinProcessor-Caching-Problem__
Das System wendet nun den JoinProcessor für jede Iteration korrekt an, auch bei aufeinander folgenden Aufrufen, was einen präzisen Datenabruf gewährleistet. Zuvor wurde der JoinProcessor fälschlicherweise bereits in aufeinander folgenden Iterationen als angewendet markiert, was zu Fehlern beim Datenabruf führte.
  _AC-11690 - [GitHub-Problem](https://github.com/magento/magento2/issues/27504) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37550)_
* __[Problem] Versandpreis wird in gedruckter PDF-Datei anders angezeigt__
Das System zeigt nun die Versandkosten in gedruckten PDFs entsprechend den Einstellungen für die Steuerkonfiguration korrekt an, sodass die Konsistenz zwischen der Seite mit der Rechnung für Kundenaufträge und der gedruckten Rechnung gewährleistet ist. Zuvor war der im gedruckten PDF angezeigte Versandpreis ohne Steuer, unabhängig von den Steuerkonfigurationseinstellungen.
  _AC-11798 - [GitHub-Problem](https://github.com/magento/magento2/issues/38608) - [GitHub-Code-](https://github.com/magento/magento2/pull/38595) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bafc571)_
* __Mit einem gelöschten übergeordneten konfigurierbaren Produkt neu anordnen__
Beim Neuanordnen mit dem gelöschten Produkt zeigt das System jetzt nicht die Schaltfläche zum Neuanordnen an
  _AC-13839 - [GitHub-Problem](https://github.com/magento/magento2/issues/39568) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39601)_
* __[Problem] Beheben Sie die fehlerhafte Eigenschaft \Magento\Sales\Model\Order\Email\Container\Template::$id__
Dies behebt die fehlerhafte phpdoc für \Magento\Sales\Model\Order\Email\Container\Template::$id, eigentlich ist $id type int, aber in Wirklichkeit ist string.
  _AC-13924 - [GitHub-Problem](https://github.com/magento/magento2/issues/39151) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39150)_
* __Änderungen an der Telefonnummer können nicht in den vorhandenen Bestelldetails gespeichert werden__
Jetzt kann der Benutzer das internationale Präfix 00 im Telefonfeld der Bestelladresse hinzufügen
  _ACP2E-2622 - [GitHub-Problem](https://github.com/magento/magento2/issues/38201) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/12e071c3)_
* __E-Mails können nicht gesendet werden__
Das System enthält jetzt die Konfigurationsoption async_sending_attempts , mit der vor dem Anhalten eine E-Mail gesendet werden soll, und die Handhabung von fehlgeschlagenen E-Mail-Sendungen verbessert, wenn „Asynchrones Senden“ aktiviert ist. Zuvor versuchte das System, eine E-Mail nicht zu senden, und versuchte kontinuierlich, sie erneut zu senden, was zu einer endlosen Schleife von Fehlermeldungen im Systemprotokoll führte.
  _ACP2E-2734 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __[Cloud] Der Bestellstatus wurde in „Abgeschlossen“ geändert, wenn eine teilweise zurückgesendete Bestellung teilweise zurückerstattet wurde__
Beim Ausstellen einer Gutschrift wird der Bestellstatus nicht mehr in „Abgeschlossen“ geändert, wenn es Artikel gibt, die noch nicht versandt wurden.
  _ACP2E-2756 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD] kann das Senden von E-Mails über die Admin-Benutzeroberfläche nicht deaktivieren, wie in den Entwicklungsdokumenten angezeigt wird__
Das System verhindert jetzt korrekt, dass Verkaufs-E-Mails gesendet werden, wenn die E-Mail-Kommunikation deaktiviert ist. Diese E-Mails werden nicht mehr gesendet, wenn die E-Mail-Kommunikation wieder aktiviert wird. Zuvor wurden Verkaufs-E-Mails, die initiiert wurden, während die E-Mail-Kommunikation deaktiviert war, weiterhin gesendet, sobald die E-Mail-Kommunikation wieder aktiviert wurde.
  _ACP2E-3002 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8931218)_
* __Bestellung abgeschlossen ohne vollständige Rückerstattung__
Das System behält nun den Bestellstatus als „Verarbeitung läuft“ und den Rechnungsstatus als „Ausstehend“ korrekt bei, wenn eine Bestellung mit einer nicht erfassten Zahlung erstellt wurde. Dadurch wird sichergestellt, dass Bestellungen erst nach vollständiger Rückerstattung als „Geschlossen“ gekennzeichnet werden. Zuvor wurde der Bestellstatus bei der Erstellung einer Lieferung für einen Auftrag mit ausstehender Rechnung fälschlicherweise in „Geschlossen“ geändert.
  _ACP2E-3045 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_
* __[Cloud] Es kann keine Bestellung in Admin in einem Geschäft erstellt werden, wenn nur die Standard-Rechnungsadresse nicht eingerichtet wurde__
Jetzt relevante Fehlermeldung „Ein Kunde mit derselben E-Mail-Adresse existiert bereits auf einer zugehörigen Website.“ wird angezeigt, wenn ein Kunde keine Standard-Rechnungsadresse hat und versucht, eine Bestellung in einem anderen Shop zu erstellen.
  _ACP2E-3311 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d75cff27)_
* __Admin hat doppelte Bestellanfragen gesendet__
Zuvor konnte die Schaltfläche „Bestellung abschicken“ im Admin-Panel mehrmals angeklickt oder durch wiederholtes Drücken der Eingabetaste aktiviert werden, was zu doppelten oder fehlerhaften Bestellübermittlungen führte. Vermeiden Sie jetzt zusätzliche Aktionen, bis die Bestellung vollständig verarbeitet ist, sodass nur eine Bestellung gesendet wird.
  _ACP2E-3416 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_
* __Der Administrator kann auch ohne Zahlungsmethode eine Bestellung aufgeben__
Zuvor ausgewählte Zahlungsmethode wird jetzt beibehalten, wenn die Zahlungsmethode in der Liste der verfügbaren Zahlungen erneut angezeigt wird.
  _ACP2E-3425 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Elemente werden dupliziert, nachdem wir eine Bestellung vom Administrator in Mozilla Firefox-Browser erstellt haben__
Produkte, die mit „Produkte nach SKU hinzufügen“ hinzugefügt wurden, werden in Firefox beim Erstellen einer Bestellung in Admin nicht mehr dupliziert.
  _ACP2E-3518_

### Bestellung, Zahlungen

* __Der Administrator kann bestellen Linear weiterhin ohne Zahlungsmethode__ platzieren
Bisher konnte der Händler Bestellungen über den Admin-Bereich aufgeben, ohne eine Zahlungsmethode auswählen zu müssen. Jetzt ist der Händler eine Zahlungsmethode erforderlich, um mit der Platzierung einer bestellen fortzufahren.
  _ACP2E-3233 – [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fd5cf3af)_

### Bestellung, Rückgabe

* __Die Bestellerstattung führt zu einer doppelten Gutschrift__
Wenn bei der Rückerstattung über die REST-API zwei identische Anfragen gleichzeitig ausgeführt wurden, werden keine doppelten Gutschriften mehr erstellt.
  _ACP2E-2982 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a4fbf702)_

### Bestellung, Steuer

* __[CLOUD] Falsche base_row_total in der RESTFUL-Auftrags-API bei der Aktivierung grenzüberschreitender Transaktionen und der Anwendung von Couponrabatten__
Jetzt wird der korrekte base_row_total von der RESTFUL-Auftrags-API zurückgegeben, wenn die grenzüberschreitende Transaktion aktiviert ist und ein Couponrabatt angewendet wird.
  _ACP2E-3003 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9af794a4)_

### Sonstige

* __[Braintree] Online-Rückerstattung bei Speicherung der Transaktion als transactionID-REFUNDY__
  _BUNDLE-3394_
* __[Bestellungen mit Braintree] + [CLOUD] Braintree (Kreditkarte) können nicht aufgeteilt werden__
  _BUNDLE-3421_
* __[Braintree][Cloud]Das Braintree-SSL-Zertifikat läuft am 30. Juni ab__
  _BUNDLE-3422_
* __private_content_version-Cookie, das in GQL-Abfragen zurückgegeben wird__
Es wurde ein Problem behoben, bei dem das Cookie „private_content_version“ in GraphQL-Abfragen zurückgegeben wurde, selbst wenn das Sitzungs-Cookie deaktiviert war. Das Cookie ist nicht mehr in den GraphQL-Antworten enthalten, wenn die Sitzung erwartungsgemäß deaktiviert wird.
  _LYNX-339_
* __Server-Fehler bei E-Mail-Props in Abfragen physischer Geschenkkarten__
Es wurde ein Problem behoben, bei dem Abfragen für sender_email und recipient_email auf physischen Geschenkkarten zu einem Server-Fehler führten. Diese Props werden jetzt für virtuelle Geschenkkarten korrekt zurückgegeben, und das Abfrageverhalten ist konsistent.
  _LYNX-366_
* __is_available-Attribut in CartItemInterface gibt für konfigurierbare Produkte immer „false“ zurück__
Es wurde ein Problem behoben, bei dem das Attribut is_available in CartItemInterface für auf Lager konfigurierbare Produkte immer „false“ zurückgab. Jetzt spiegelt sie die Verfügbarkeit korrekt wider, sofern zutreffend.
  _LYNX-380_
* __is_available-Attribut in CartItemInterface gibt „true“ zurück, auch wenn der verkaufbare Bestand kleiner als die Menge des Produkts ist__
Es wurde ein Problem behoben, bei dem das Attribut is_available in der CartItemInterface fälschlicherweise „true“ zurückgegeben wurde, selbst wenn die Menge des Warenkorbeartikels den verkäuflichen Lagerbestand überschritt.
  _LYNX-382_
* __only_x_left_in_stock-Attribut in ProductInterface ist bei konfigurierbaren Produkten nicht korrekt__
Es wurde ein Problem behoben, bei dem das Attribut only_x_left_in_stock in ProductInterface den verfügbaren Bestand für konfigurierbare Produktvarianten im Warenkorb nicht genau wiedergab. Jetzt entspricht der Wert „only_x_left_in_stock“ korrekt den tatsächlichen Lagerbeständen der Varianten, sodass in der GQL-Abfrage des Warenkorbs genaue Inventardaten zurückgegeben werden.
  _LYNX-395_
* __Platzhalter-Miniaturansicht gibt zurück, wenn ein einfaches Produkt innerhalb eines gruppierten Produkts zum Warenkorb hinzugefügt wird__
Es wurde ein Problem behoben, bei dem beim Hinzufügen eines einfachen Produkts (Teil eines gruppierten Produkts) zum Warenkorb ein Platzhalter-Miniaturbild zurückgegeben wurde, selbst wenn dem Produkt ein Bild zugewiesen war.
Fehlerbehebungsdetails:
* Die Produktminiatur zeigt nun das zugewiesene Bild, sofern verfügbar, korrekt an.
* Die Auswahl der Miniaturen berücksichtigt die Admin-Konfiguration unter:
Stores > Konfiguration > Verkauf > Checkout > Warenkorb > Gruppiertes Produktbild.
Dadurch wird ein konsistentes Verhalten von Miniaturansichten für gruppierte Produkte basierend auf Store-Einstellungen sichergestellt.
  _LYNX-399_
* __Die benutzerdefinierten Optionsattribute des Kunden funktionieren nicht mit Ganzzahlwerten__
Es wurde ein Problem behoben, bei dem die benutzerdefinierten Optionsattribute des Kunden nicht funktionierten, wenn der zurückgegebene Wert eine Ganzzahl war. Benutzerdefinierte Optionen verarbeiten und geben jetzt ganzzahlige Werte korrekt wie erwartet zurück.
  _LYNX-400_
* __Interner Server-Fehler beim Versuch, priceDetails für Bundle-Produkte mit dynamischem Preis abzurufen__
Es wurde ein Problem behoben, bei dem die Abfrage von Preisdetails für Bundle-Produkte mit dynamischer Preisgestaltung über GraphQL zu einem internen Server-Fehler führte. Diese Verbesserung gewährleistet stabile Warenkorbabfragen bei der Arbeit mit Bundle-Produkten, die mit dynamischen Preisen konfiguriert sind.
  _LYNX-402_
* __ONLY_X_LEFT_IN_STOCK gibt für konfigurierbare Produkte immer 0 zurück__
Es wurde ein Problem behoben, bei dem das Attribut only_x_left_in_stock bei Verwendung der übergeordneten SKU mit Optionen immer 0 für konfigurierbare Produkte zurückgab.
Fehlerbehebungsdetails:
* Der Wert only_x_left_in_stock spiegelt nun genau den Bestand der ausgewählten untergeordneten Variante statt der übergeordneten SKU wider.
* Dadurch wird sichergestellt, dass die Lagerbestände für konfigurierbare Produktvarianten auf den Warenkorb- und Produktseiten korrekt angezeigt werden.
  _LYNX-403_
* __GraphQL-Fehler: Nicht unterstützter „Dateityp“ in anpassbaren Abfrageoptionen__
Es wurde ein Problem behoben, bei dem GraphQL einen Fehler für anpassbare Optionen vom Typ „Datei“ in Warenkorbelementen zurückgab. Die Abfrage gibt jetzt korrekt Details für alle anpassbaren Optionstypen zurück, einschließlich dateibasierter Optionen, ohne Fehler zu verursachen.
  _LYNX-405_
* __GraphQL-Abfrage gibt nicht den richtigen berechneten regulären Preis für anpassbare Produkte zurück__
Es wurde ein Problem behoben, bei dem GraphQL für anpassbare Produkte nicht den richtigen berechneten regulären Preis zurückgab. Die Abfrage enthält jetzt korrekt den berechneten regulären Preis mit anpassbaren Werten (z. B. 125 USD) in der Preiseigenschaft, die sowohl den Grundpreis als auch etwaige zusätzliche Anpassungskosten widerspiegeln.
  _LYNX-411_
* __AppliedTaxes über EstimatedTotals bleiben mit aktualisierten Mutationen erhalten__
Es wurde ein Problem mit der Mutation EstimatedTotals behoben, bei dem angewendete Steuern auch nach dem Aktualisieren der Region oder Postleitzahl auf einem Warenkorb beibehalten wurden. Die Mutation aktualisiert nun die angewendeten Steuern korrekt, wenn zwischen Regions- und Postcodewerten gewechselt wird, um sicherzustellen, dass nur die richtige Steuerregel auf der Grundlage der aktuellen Warenkorbdaten angewendet wird.
  _LYNX-412_
* __is_available-Attribut in CartItemInterface gibt „true“ zurück, auch wenn der verkaufbare Bestand kleiner als die Menge des Produkts ist__
Es wurde ein Problem behoben, bei dem das Attribut is_available in CartItemInterface fälschlicherweise „true“ zurückgegeben wurde, selbst wenn der verkaufbare Bestand kleiner als die angeforderte Produktmenge war. Das Feld is_available gibt jetzt korrekt „false“ zurück, wenn die Produktmenge den verfügbaren Bestand überschreitet.
  _LYNX-420_
* __Gutschein kann nicht zum Warenkorb hinzugefügt werden, da nur der Rabatt für den Versand gilt__
Es wurde ein Problem behoben, bei dem ein Coupon nicht auf einen Warenkorb angewendet werden konnte, um Rabatte nur für den Versand zu erhalten. Der Coupon wird jetzt korrekt auf den Versandbetrag angewendet, wenn eine Verkaufsregel ohne Produktbedingungen verwendet wird, um sicherzustellen, dass der erwartete Rabatt auf die Versandkosten angewendet wird.
  _LYNX-421_
* __Regulärer Produktpreis mit 12 Dezimalstellen und falschem Wert__
Es wurde ein Problem behoben, bei dem der Wert „Regular_Price“ im GraphQL-Pfad „product.price_range.maximum_price“ und „minimum_price“ nicht mit dem Katalogpreis übereinstimmte, wenn mehrere Steuersätze angewendet wurden. Der reguläre Preis spiegelt nun den Katalogpreis über alle Steuerkonfigurationen hinweg konsistent wider und gewährleistet eine genaue Einzelpreisfindung, Berechnungen der GesamtZeilenkosten und Rabattprüfungen in der Warenkorbzusammenfassung.
  _LYNX-425_
* __GraphQL-Serverfehler im Warenkorb mit nicht vorrätigem gebündeltem Produkt__
Es wurde ein Problem behoben, bei dem GraphQL beim Abrufen eines Warenkorbs mit einem gebündelten Produkt mit einem nicht vorrätigen Element einen internen Server-Fehler zurückgab, insbesondere wenn die Abfrage die itemsV2-Eigenschaft enthielt. GraphQL gibt jetzt wie erwartet korrekt eine Liste von Elementen mit relevanten Fehlermeldungen zurück, die an den Produkteintrag im Paket angehängt sind.
  _LYNX-430_
* __Es ist nicht möglich, eine Adresse mit benutzerdefinierten Attributen zu erstellen__
Es wurde ein Problem mit der createCustomerAddress-Mutation behoben, das die Erstellung von Adressen mit erforderlichen benutzerdefinierten Attributen verhinderte. Die Mutation verarbeitet jetzt benutzerdefinierte Adressattribute korrekt, wenn die entsprechende Payload bereitgestellt wird.
  _LYNX-441_
* __GraphQL-Server-Fehler im Warenkorb mit only_x_left_in_stock auf gebündeltem Produkt__
Es wurde ein Problem behoben, bei dem das Abrufen eines Warenkorbs, der ein gebündeltes Produkt mit dem Feld only_x_left_in_stock in der GraphQL-Abfrage enthält, zu einem internen Server-Fehler führte. GraphQL gibt jetzt für das Feld only_x_left_in_stock korrekt einen Float oder null zurück, ohne Fehler zu verursachen.
  _LYNX-447_
* __GraphQL-Fehler beim Entfernen anderer Produkte mit unzureichendem konfigurierbarem Produkt im Warenkorb__
Es wurde ein Problem behoben, bei dem der Versuch, vorrätige Produkte aus dem Warenkorb zu entfernen, zu dem GraphQL-Fehler „Die angeforderte Menge ist nicht verfügbar“ führte, wenn der Warenkorb auch konfigurierbare Produkte mit unzureichendem Bestand enthielt. Die Entfernung funktioniert nun erwartungsgemäß, ohne dass Fehler ausgelöst werden.
  _LYNX-464_
* __Es können keine Produkte hinzugefügt werden, da bei der SKU-Mutation die Groß-/Kleinschreibung beachtet wird__
Es wurde ein Problem behoben, bei dem die addProductsToCart-Mutation bei Verwendung von SKUs mit unterschiedlicher Groß-/Kleinschreibung den Fehler „PRODUCT_NOT_FOUND“ zurückgab. Die Mutation verarbeitet SKUs nun ohne Unterscheidung der Groß-/Kleinschreibung und stellt so die Konsistenz mit Abfragen des Katalog-Service und dem PDP-Verhalten sicher.
  _LYNX-469_
* __Produktattribut > Marken-Kurzform &amp;trade; wird als &amp;trade;zurückgegeben__
Es wurde ein Zeichenkodierungsproblem mit dem Produktnamen für die GraphQL-API behoben
  _LYNX-603_
* __updateCustomerEmail-Mutationsproblem__
Es wurde ein Problem mit der updateCustomerEmail-Mutation behoben, bei dem Kunden ohne erforderliche benutzerdefinierte Attribute (die nach der Kontoerstellung hinzugefügt wurden) ihre E-Mail nicht aktualisieren konnten.
  _LYNX-619_
* __Die Mutation setShippingAddressesOnCart gibt einen Fehler aus, wenn pickup_location_code verwendet wird__
Es wurde ein Problem behoben, bei dem die setShippingAddressesOnCart-Mutation bei Verwendung von pickup_location_code ohne Angabe von customer_address_id oder -adresse einen Fehler zurückgab. Die Mutation ermöglicht es nun, eine Versandadresse nur mit dem PICKUP_LOCATION_CODE zu setzen.
  _LYNX-626_
* __CustomerOrder.items_eligibility_for_return-Liste muss mit Bestellartikeln übereinstimmen__
Behobene Inkonsistenzen mit der Rücksendeberechtigung in Bestellungen:
1. Die Liste CustomerOrder.items_eligibility_for_return stimmt jetzt mit den tatsächlichen Bestellartikeln überein.
2. Das Feld OrderItemInterface.eligibility_for_return gibt richtigerweise false zurück, wenn die vollständige Menge bereits zurückgegeben wurde.
3. CustomerOrder.items_eligibility_for_return enthält jetzt nur noch Artikel, die noch nicht zurückgegeben werden.
   _LYNX-627_
* __Feld „Menge hinzufügen_return_requested“__
Das Feld quantity_return_requested wurde der OrderItemInterface hinzugefügt, sodass Sie die Menge der Artikel identifizieren können, für die eine Rücksendung gesendet wurde. Dadurch wird die Rückgabeverfolgung neben dem vorhandenen Feld „quantity_returned“ verbessert.
  _LYNX-628_
* __Verfügbare Aktionen für Bestellungen dürfen keine Rücksendung enthalten, nachdem Rücksendungen für alle Artikel in voller Menge erstellt wurden__
Es wurde ein Problem behoben, bei dem das Feld available_actions in der Abfrage customer.orders von GraphQL fälschlicherweise RETURN enthielt, nachdem eine vollständige Rückgabe für alle Artikel erstellt wurde. Die Aktion „ZURÜCKGEBEN“ wird jetzt ordnungsgemäß entfernt, sobald der Rückgabevorgang abgeschlossen ist.
  _LYNX-634_
* __Storefront-Kompatibilität - Aktualisieren der Logik, um den Tabellennamen mit dem Präfix und anderen kleineren Verbesserungen zu erhalten__
Die Logik zum Abrufen des Tabellennamen mit dem Präfix (im Zusammenhang mit SCP-Änderungen) wurde aktualisiert.
  _LYNX-637_
* __Das Speichern im Adressbuch funktioniert nicht, wenn das Feld „same_as_shipping“ von setBillingAddressOnCart GQL verwendet wird__
Fehlerkorrektur - Die Lieferadresse wird nicht im Adressbuch des Kunden gespeichert, wenn die GraphQL-Mutation setBillingAddressOnCart verwendet wird und das Feld same_as_shipping auf true gesetzt ist. Jetzt wird die Lieferadresse korrekt wie erwartet gespeichert.
  _LYNX-643_
* __Standardisieren Sie die order_id in Mutationen__
Die Eingabe von order_id in Mutationen wurde standardisiert und die E-Mail-Vorlage für die Auftragsabbruchsbestätigung wurde aktualisiert, um die Inkrement-ID anstelle der Auftrags-ID anzuzeigen.
  _LYNX-650_
* __CustomerOrder zeigt die Bestellkommentare nicht an__
Es wurde ein Problem mit CustomerOrder behoben, um Bestellkommentare in GraphQL-Abfragen für Gast- und Kundenaufträge einzuschließen.
  _LYNX-651_
* __original_item_price darf keinen Rabatt enthalten__
Die Logik für original_item_price in GraphQL-Warenkorbartikelpreisen wurde aktualisiert, um Rabatte auszuschließen.
  _LYNX-652_
* __Paketprodukte zeigen weiterhin „IN_STOCK“ an, wenn eines ihrer gebündelten Produkte nicht vorrätig ist__
Es wurde ein Problem behoben, bei dem product.stock_status für Bundle-Produkte weiterhin „IN_STOCK“ zeigte, selbst wenn eines der gebündelten Elemente nicht vorrätig war.
  _LYNX-681_
* __Kundenabfrage gibt den internen Server-Fehler zurück, wenn für einen Kunden ein Wert für das gelöschte benutzerdefinierte Attribut vorhanden ist__
Es wurde ein Problem behoben, bei dem die Kundenabfrage einen internen Server-Fehler zurückgab, wenn ein gelöschtes benutzerdefiniertes Attribut noch einen gespeicherten Wert hatte. Jetzt wird eine korrekte Fehlermeldung zurückgegeben, wenn ein nicht vorhandenes Attribut angefordert wird. Erforderlicher Cache wird beim Löschen des benutzerdefinierten Kundenattributs ungültig.
  _LYNX-686_
* __Aktionsparameter für Bestätigungs-Links für Rücksendung und Abbruch__
Aktionsparameter für Links zu E-Mails mit Rückgabe- und Abbruchsbestätigung hinzugefügt
  _LYNX-687_
* __Die Bestätigungs-URL des Gastbenutzers wird zur Bestellstatus-Seite umgeleitet, da die „orderRef“ fehlt (Für GuestRMA)__
Dem Link in der Bestätigungs-E-Mail des Gast-RMA wurde der Parameter orderRef hinzugefügt.
  _LYNX-688_
* __Die Bestätigungs-URL des Gastbenutzers wird zur Bestellstatus-Seite weitergeleitet, da orderRef fehlt__
Der Parameter orderRef wurde zum Link in der Bestätigungs-E-Mail zur Stornierung einer Gastbestellung hinzugefügt
  _LYNX-689_
* __Probleme mit der Kundenabfrage bei deaktivierter RMA__
Die GraphQL-Logik wurde aktualisiert, um sicherzustellen, dass zuvor erstellte Rückgaben auch dann verfügbar bleiben, wenn RMA global deaktiviert ist. Die Fehlermeldung wurde entfernt, um die Storefront-Benutzeroberfläche zu verbessern und sicherzustellen, dass Kunden ihre früheren Rücksendungen weiterhin anzeigen können.
  _LYNX-690_
* __GraphQL gibt keine aktualisierten Warenkorb-Daten zurück, wenn widersprüchliche Coupons angewendet wurden__
Fest ein Problem, bei dem das Anwenden eines in Konflikt stehenden Coupon mit einer höheren Priorität zu einer Fehlermeldung führte, ohne dass die aktualisierten Warenkorb Daten zurückgegeben wurden. Wenn nun ein neuer Coupon die vorhandene ungültig macht, gibt die Mutation den Warenkorb mit angewendetem gültigem Coupon korrekt zurück.
  _LUCHS-696_
* __Kann für das Feld, das keine NULL-Werte zulässt, &quot;TaxItem.title&quot; für placeOrder GQL__ nicht null zurückgeben
Fest ein Problem, bei dem die placeOrder-Mutation mit einem internen Serverfehler fehlgeschlagen ist, der auf einen NULL-Wert für das Feld TaxItem.title zurückzuführen ist, das keine NULL-Werte zulässt. Jetzt gibt das Feld immer einen gültigen Wert zurück, um eine erfolgreiche bestellen Platzierung sicherzustellen.
  _LYNX-699_
* __Geschätzte Gesamtwerte: Rabatte sind null für virtuelle Produktarten__
Es wurde das Problem behoben, bei dem die Mutation estimatedTotals für Rabatte null zurückgab, wenn ein Rabattcode auf einen Warenkorb mit virtuellen Produkten angewendet wird.
  _LYNX-702_
* __Das Bundle-Produkt gibt nicht den richtigen Rabattprozentsatz und Betrag zurück__
Für Katalogartikelpreise wurden die neuen Eigenschaften „CATALOG_DISCOUNT“ und „ROW_CATALOG_DISCOUNT“ eingeführt, um die richtigen Rabattbeträge und -prozentsätze sowohl auf Zeilen- als auch Einzelartikelebene anzuzeigen.
  _LYNX-703_
* __Konfiguration von Geschenknachrichten auf Produktebene__
Es wurde ein Problem behoben, bei dem Geschenknachrichten nicht auf Produktebene angewendet wurden, wenn sie global deaktiviert waren. Wenn jetzt Geschenknachrichten für ein bestimmtes Produkt aktiviert sind, können sie mit der UpdateCartItems-Mutation erfolgreich hinzugefügt werden und werden korrekt gespeichert und angezeigt.
  _LYNX-714_
* __Problem beim Entfernen der Geschenkverpackung vom Warenkorbartikel__
Es wurde ein Problem behoben, bei dem das Entfernen des Geschenkverpackens aus einem Warenkorbelement mithilfe der updateCartItems-Mutation nicht wie erwartet funktionierte. Jetzt funktionieren sowohl das Anbringen als auch das Entfernen von Geschenkverpackungen korrekt und fehlerfrei.
  _LYNX-717_
* __Die passende Funktion für registrierte Kunden funktioniert nicht in Textbaustein und die trackViewedProduct-Mutation muss für Gäste aktiviert werden.__
Offene trackViewedProduct-Mutation zur Nachverfolgung des Produktansichtsereignisses für Kunden und Gäste
  _LYNX-751_
* __cart.rules-Abfrage gibt einen Fehler anstelle eines leeren Arrays zurück, wenn keine aktiven Warenkorbregeln angewendet werden__
Die Abfrage „cart.rules“ wurde korrigiert, sodass ein leeres Array anstelle eines Fehlers zurückgegeben wird, wenn keine aktiven Warenkorbregeln angewendet werden.
  _LYNX-757_
* __Problem beim Abrufen von Geschenkverpackungen für Artikel im Warenkorb__
Aktualisierte Abruflogik, um Geschenkverpackungsoptionen für Warenkorbartikel zurückzugeben, wenn diese global deaktiviert, aber auf Produktebene aktiviert sind
  _LYNX-758_
* __GraphQL-Aufrufe mit der OPTIONS-Methode geben bei der Installation des Pakets „adobe-commerce/storefront-compatibility“ den Antwort-Code 500 zurück__
Es wurde ein Problem behoben, bei dem GraphQL-Aufrufe mit der OPTIONS-Methode bei der Installation des Pakets „adobe-commerce/storefront-compatibility“ einen internen Server-Fehler 500 zurückgaben. Der Endpunkt gibt jetzt korrekt eine 200/204-Antwort wie erwartet zurück.
  _LYNX-778_

### Andere Entwickler-Tools

* __[Problem] Beheben Sie den HTML-Syntaxfehler in visual.phtml__
Das System schließt jetzt das Start-Tag in der Datei „visual.phtml“ korrekt, um eine ordnungsgemäße HTML-Syntax sicherzustellen. Zuvor wurde das Start-Tag nicht ordnungsgemäß geschlossen, was zu einem HTML-Syntaxfehler führte.
  _AC-10658 - [GitHub-Problem](https://github.com/magento/magento2/issues/38247) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37457)_
* __[Problem] Im Befehl „bin/magento maintenance:status“ wurde „aktiv“ in „aktiviert“ geändert__
Das System bietet jetzt genauere Statusmeldungen für den Wartungsmodusbefehl, wobei der Status von „aktiv“ in „aktiviert“ und von „nicht aktiv“ in „deaktiviert“ geändert wird. Zuvor wurde die Statusmeldung für den Wartungsmodusbefehl als „aktiv“ oder „nicht aktiv“ angezeigt, was zu Verwirrung führen konnte.
  _AC-11474 - [GitHub-Problem](https://github.com/magento/magento2/issues/38486) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38410)_
* __Die Navigation in der Kategoriestruktur führt zu Fehlern in Redis: „Redis-Sitzung hat gleichzeitige Verbindungen überschritten“__
  _AC-12571 - [GitHub-Problem](https://github.com/magento/magento2/issues/38851) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0611e750)_
* __CSP-Probleme in Kombination mit dev/css/use_css_critical_path__
Das System lädt CSS-Dateien nun korrekt asynchron auf Auscheckseiten, selbst wenn die Einstellung „dev/css/use_css_critical_path“ aktiviert ist, um sicherzustellen, dass diese Seiten mit den richtigen CSS-Stilen gerendert werden. Zuvor verhinderte eine eingeschränkte Content Security Policy (CSP) die Ausführung von Inline-JavaScript, was dazu führte, dass CSS-Dateien nicht wie erwartet geladen wurden.
  _AC-12731 - [GitHub-Problem](https://github.com/magento/magento2/issues/39020) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39040)_
* __Bei Verwendung des virtuellen Typs zum Konfigurieren des Plug-ins kann die Interceptor-Methode im `setup:di:compile`-Befehl nicht korrekt generiert werden__
Das System generiert jetzt korrekt Interceptor-Methoden, wenn ein virtueller Typ zum Konfigurieren eines Plug-ins verwendet wird, um konsistente Ergebnisse sicherzustellen, unabhängig davon, ob vorkompiliert oder zur Laufzeit kompiliert. Zuvor generiert das System beim Vorkompilieren falsche Ergebnisse im Vergleich zur Laufzeitkompilierung.
  _AC-13398 - [GitHub-Problem](https://github.com/magento/magento2/issues/33980) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38141)_
* __Dateien können nicht von der Datenerfassung heruntergeladen werden__
Beim Herunterladen der Sicherung wird keine leere Seite mehr angezeigt, anstatt die Datei herunterzuladen.
  _ACP2E-3441_
* __Adobe Commerce 2.4.7-p3-Modultests schlagen fehl__
Es sind keine Versionshinweise erforderlich.
  _ACP2E-3631 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/982b1c42)_

### Zahlungs-/Zahlungsmethoden, Bestellung

* __Papal Payflow Kreditkartendetails, die für die spätere Verwendung gespeichert wurden, werden nicht auf der Seite der gespeicherten Zahlungsmethode angezeigt__
Frühere Papal Payflow Kreditkartendetails, die für die spätere Verwendung gespeichert wurden, wurden nicht auf der Seite der gespeicherten Zahlungsmethode angezeigt, die jetzt feste Kreditkartendetails sind auf der Seite der gespeicherten Zahlungsmethode sichtbar.
  _AC-13699 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/96dec499)_

### Zahlungen

* __Zahlung mit Kreditkarte (Payflow-Link) funktioniert nicht__
Früher erhalten Fehler (Zahlung wurde abgelehnt) beim Platzieren der Bestellung mit Kreditkarte, nachdem die Bestellung erfolgreich platziert wurde.
  _AC-13414 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a68324bc)_
* __Payflow erstellt jedes Mal eine neue Transaktion, wenn wir auf dem Bildschirm Transaktion anzeigen auf die Schaltfläche Abrufen klicken__
Das System ruft jetzt bei jedem Klicken auf die Schaltfläche „Abrufen“ im Bildschirm „Transaktion anzeigen“ Transaktionsinformationen korrekt ab, ohne eine neue Zahlungstransaktion zu erstellen. Zuvor wurde durch Klicken auf die Schaltfläche „Abrufen“ fälschlicherweise eine neue Zahlungstransaktion für eine bereits bezahlte Bestellung erstellt.
  _ACP2E-2841 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __PayLater-Nachricht wird für kanadisches PayPal-Händlerkonto nicht in PDP angezeigt__
Das System zeigt nun auf der Produktdetailseite (PDP) korrekt die PayLater-Nachricht für kanadische PayPal-Händlerkonten an, wenn das Land des Käufers anhand der Rechnungsadresse oder der Lieferung des Kontos ermittelt werden kann. Zuvor wurde die PayLater-Nachricht aufgrund eines fehlenden Parameters nicht angezeigt, was zu einem Fehler in der Browser-Konsole führte.
  _ACP2E-3028 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6a185204)_
* __Die Rückerstattung bei PayPal-Bestellungen führt zu einer doppelten Gutschrift__
Fehlerkorrektur - Parallelitätsprobleme bei IPN-erstellten Gutschriften für den PayPal-Zahlungsdienst wurden behoben.
  _ACP2E-3143 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_
* __Warenkorb-Preisregel funktioniert nicht für Paypal__
Der korrekte Betrag wird auf der PayPal-Seite angezeigt, wenn der Rabatt nach Zahlungsmethode angewendet wird
  _ACP2E-3163 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_
* __[Cloud] Benutzer mit einer bestimmten Rolle können sich nicht anmelden__
Admin-Benutzer mit einer Rolle, die nur PayPal-Abschnittszugriff enthält, können sich jetzt fehlerfrei anmelden
  _ACP2E-3208 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/66dea0de)_

### Leistung

* __Problem mit den standardmäßigen Produktattributeinstellungen__
Das System ermöglicht es Benutzenden jetzt, die Auswahl einer Standardoption für ein Produktattribut aufzuheben, sodass das Attribut nicht immer über einen Standardsatz verfügt. Nachdem ein Standard für ein Produktattribut festgelegt wurde, gab es bisher keine Möglichkeit, die Auswahl aufzuheben, sodass für das Attribut immer ein Standardwert festgelegt war.
  _AC-11932 - [GitHub-Problem](https://github.com/magento/magento2/issues/38703) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_
* __[Problem] Code-Bereinigung und Hinzufügen eines neuen kritischen Head-Blocks und Verschieben von kritischem CSS vor Assets__
Das System umfasst jetzt einen neuen kritischen Hauptblock und verschiebt wichtiges CSS vor Assets, was eine bessere Anpassung und Leistungsoptimierung im Frontend ermöglicht. Zuvor wurde das kritische CSS nicht vor den Assets positioniert, was die Anpassungs- und Optimierungsmöglichkeiten einschränkte.
  _AC-12000 - [GitHub-Problem](https://github.com/magento/magento2/issues/38748) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35580)_
* __Die Design-Kompilierung funktioniert nicht mehr, wenn der MySQL-Host Port-Informationen enthält__
Das System verarbeitet jetzt die MySQL-Host-Konfiguration, die Port-Informationen enthält, korrekt, um eine erfolgreiche Design-Kompilierung sicherzustellen. Zuvor schlug die Design-Kompilierung fehl, wenn die MySQL-Host-Konfiguration in der Datenbankverbindung Port-Informationen enthielt.
  _AC-12176 - [GitHub-Problem](https://github.com/magento/magento2/issues/38799) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38842)_
* __Unterstützung für die CommandLoaderInterface-Schnittstelle von Symfony in Magento CLI__
Durch diese Änderung wird die Initialisierungszeit der Magento-CLI-App reduziert, da Befehle erst dann initialisiert werden können, wenn sie benötigt werden.
  _AC-13471 - [GitHub-Problem](https://github.com/magento/magento2/issues/29266) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29355)_
* __Leistungsproblem beim Laden von Produktattributen in Warenkorbregeln__
Verbesserte Abfrageleistung für Vertriebsregeln - von rund 150 ms bis zu einstelligen ms.
  _ACP2E-2494 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Preis partielle Indizierungsleistung__
Die Leistung bei der partiellen Indizierung wurde durch die Optimierung einiger Löschabfragen, die im Indizierungsprozess verwendet werden, verbessert.
  _ACP2E-2673 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Bestellung wird bei der Einrichtung mehrerer Stores bei Verwendung der asynchronen Auftragsverarbeitung + Geschäftsbedingungen abgelehnt__
Die Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden jetzt verarbeitet.
Bevor sie automatisch abgelehnt wurden.
  _ACP2E-2850 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_
* __Die Ausführung des Aufruf der Order Rest-API dauert sehr lange__
Das System führt nun den Aufruf der Auftrags-REST-API innerhalb eines angemessenen Zeitraums aus, was die Leistung beim Abrufen einer großen Anzahl von Aufträgen verbessert. Zuvor dauerte die Ausführung des Order Rest-API-Aufrufs lange, was zu Verzögerungen beim Abrufen einer großen Anzahl von Bestellungen führte.
  _ACP2E-2910 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/001e5188)_

### Leistung, Promotion

* __Verkaufsregelindizierung wurde angehalten__
Das System schließt den Vertriebsregelindizierer jetzt auch mit einer großen Anzahl kombinierter Filtergruppen erfolgreich ab, sodass die Warenkorbregelbedingungen wie erwartet auf den Warenkorb angewendet werden. Zuvor konnte der Verkaufsregelindizierer bei einer großen Anzahl von kombinierten Filtergruppen nicht abgeschlossen werden, was zu einer Fehlermeldung führte und die Anwendung von Warenkorbregelbedingungen verhinderte.
  _ACP2E-2617_

### Preisgestaltung

* __Magento2.4.6-p4 Bestellung API Einfaches Element fehlt Preis__
Das System zeigt jetzt den Preis einfacher Produkte korrekt an, wenn sie über die Auftrags-API abgefragt werden, wodurch eine genaue Datendarstellung gewährleistet ist. Zuvor wurde der Preis für einfache Produkte in der API-Antwort fälschlicherweise als null angezeigt.
  _AC-11810 - [GitHub-Problem](https://github.com/magento/magento2/issues/38603)_
* __Penny-Rundungsfehler in Katalogregel__
  _AC-13855 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/276e0acd)_

### Produkt

* __Sonderzeichen im konfigurierbaren zugehörigen Produktnamen werden in HTML-Entitäten konvertiert.__
Das System behält jetzt Sonderzeichen in den Namen der zugehörigen Produkte beim Bearbeiten eines konfigurierbaren Produkts korrekt bei, was verhindert, dass sie in HTML-Entitäten konvertiert werden. Zuvor wurden Sonderzeichen in zugehörigen Produktnamen beim Bearbeiten des konfigurierbaren Produkts in HTML-Entitäten konvertiert.
  _AC-10535 - [GitHub-Problem](https://github.com/magento/magento2/issues/38146) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38447)_
* __Die ProductRepository-Funktion GetById erstellt nicht den richtigen Cache-Schlüssel__
Das System erstellt nun korrekt einen Cache-Schlüssel in der GetById-Funktion des ProductRepositorys, unabhängig davon, ob die Speicher-ID als Zeichenfolge oder Ganzzahl übergeben wird. Dadurch wird sichergestellt, dass das Produkt bei nachfolgenden Aufrufen aus dem Speicher abgerufen wird, was die Leistung verbessert. Zuvor konnte das System das Produkt jedes Mal aus der Datenbank abrufen, wenn die Funktion aufgerufen wurde, auch mit denselben Parametern, da ein falscher Cache-Schlüssel erstellt wurde.
  _AC-10947 - [GitHub-Problem](https://github.com/magento/magento2/issues/38384) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38433)_
* __[Problem] [MFTF] AdminClickAddOptionForBundleItemsActionGroup hinzugefügt__
Das System enthält jetzt die AdminClickAddOptionForBundleItemsActionGroup, wodurch die Funktionalität des Admin-Bedienfelds erweitert wird. Zuvor war diese Aktionsgruppe nicht verfügbar.
  _AC-11992 - [GitHub-Problem](https://github.com/magento/magento2/issues/30857) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30838)_
* __[Problem] Beheben von Tippfehlern im PHPDoc-Block__
Das System entfernt jetzt korrekt eine unbekannte referenzierte Variable in PHPDoc für die $helper-Variablendeklaration, was die Code-Klarheit und -Genauigkeit verbessert. Zuvor verursachte diese unbekannte referenzierte Variable in PHPDoc Verwirrung und potenzielle Ungenauigkeiten im Code.
  _AC-13173 - [GitHub-Problem](https://github.com/magento/magento2/issues/38961) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38940)_
* __[Problem] Beschädigtes Layout von Bundles und herunterladbaren Produktseiten in Magento wurde behoben >= 2.4.7__
Das Layout für Paket- und herunterladbare Produktseiten wurde korrigiert, um eine konsistente und korrekte Anzeige auf allen Geräten sicherzustellen. Zuvor traten auf diesen Seiten Layout-Probleme aufgrund einer Neuanordnung des Produktinfo-Medienblocks auf.
  _AC-13423 - [GitHub-Problem](https://github.com/magento/magento2/issues/39403) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __AlertProcessor - #2 ($storeId) muss vom Typ int sein, angegebene Zeichenfolge__
Das System erstellt nun einen korrekten Trigger der E-Mail-Benachrichtigung mit dem Produkt, indem sichergestellt wird, dass die Kennung des Stores vom richtigen Datentyp ist. Zuvor wurden keine E-Mails zu Produktwarnungen gesendet, da der Typ in der Store-Kennung nicht übereinstimmt.
  _AC-5969 - [GitHub-Problem](https://github.com/magento/magento2/issues/35602) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0574ac23)_
* __[Cloud] Funktion addFilterToMap funktioniert für bestimmte Spalten nicht__
Jetzt kann das benutzerdefinierte Modul im Bestellraster verwendet werden. Bei der Verwendung eines benutzerdefinierten Moduls sind zuvor Fehler aufgetreten.
  _ACP2E-2944 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __[Cloud] Produkte in der Kategorie - Produkte hinzufügen - Zuweisen - Alle auswählen__
Benutzer können jetzt Produkte mit dem Umschalter auswählen oder die Auswahl aufheben.
  _ACP2E-3471_

### Promotion

* __Kundenattribut beim Erstellen eines Kontos aus einer Einladung nicht sichtbar__
Kundenattribute sind beim Erstellen eines Kontos über eine Einladung verfügbar.
  _ACP2E-2602 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Gutscheincode mit „Benutzer pro Coupon“-Limit wird nicht für Zahlung freigegeben. Die Stornierung der Bestellung ist fehlgeschlagen__
Das System aktualisiert jetzt sofort die Couponnutzung, wenn eine Bestellung erstellt oder storniert wird, und fügt einer Warteschlange Regelverwendungen hinzu, um potenzielle Deadlocks zu verhindern. Dadurch wird sichergestellt, dass ein Gutscheincode mit einem Limit „Nutzungen pro Gutschein“ freigegeben wird und wiederverwendet werden kann, wenn eine Bestellung aufgrund einer fehlgeschlagenen Zahlung storniert wird. Zuvor gab das System den Couponcode nicht zur Wiederverwendung frei, was zu einer Fehlermeldung führte, die besagt, dass der Couponcode nicht gültig war.
  _ACP2E-2627 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c971859e)_
* __[Cloud] Neuindizierung Katalogregel Produkt-Indexer gibt SQLSTATE[HY000] aus: Allgemeiner Fehler: Der MySQL-Server 2006 ist verschwunden.__
Das System verarbeitet jetzt den benutzerdefinierten Wert „batchCount“ in der Datei „di.xml“ für &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot; korrekt, wodurch SQL-Fehler wie „Allgemeiner Fehler: 2006 MySQL Server ist verschwunden“ während der Neuindizierung des Catalog Rule Product Indexers aufgrund der falschen Batch-Größe bei großen Katalogen verhindert werden
  _ACP2E-2811 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __[CLOUD]Warenkorb-Preisregel für Besucher-Kundensegment wendet keinen Rabatt auf den Warenkorb an__
Das System wendet jetzt die Warenkorb-Preisregeln für Besucher-Kundensegmente korrekt an, selbst wenn die Regel keinen Coupon verwendet. So wird sichergestellt, dass die entsprechenden Rabatte auf den Warenkorb angewendet werden. Zuvor wurden Rabatte nicht auf den Warenkorb für Besucherkundensegmente angewendet, es sei denn, die Warenkorb-Preisregel verwendet einen Coupon.
  _ACP2E-2926_
* __Fehlendes Attribut „type“ auf der Registerkarte „Abzugleichende Produkte“ der Regeln für verwandte Produkte__
Das Attribut „Typ“ ist jetzt als Filteroption auf der Registerkarte „Abzugleichende Produkte“ des Moduls „Zugehörige Produktregeln“ verfügbar, was eine präzisere Regeldefinition ermöglicht. Zuvor fehlte dieses Attribut auf der Registerkarte „Abzugleichende Produkte“, was die Möglichkeit einschränkte, genaue Abgleichskriterien zu erstellen.
  _ACP2E-3024_
* __Verkaufsregel mit dem Attribut Rabattmengenschritt (X kaufen) führt dazu, dass andere Regeln nicht angewendet werden__
Die Warenkorb-Preisregel hebt zuvor angewendete Regeln nicht auf, wenn die Menge des Produkts im Warenkorb nicht ausreicht, um die Regel anzuwenden.
  _ACP2E-3139 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d01ee51e)_
* __Leistungsproblem bei Warenkorb-Preisregel - Modul für erweiterte Verkaufsregel__
Fehlende DB-Indizes für AdvancedSalesRule-Filter hinzugefügt
  _ACP2E-3331_
* __Anfrageverkaufsregeln mit Festbetragsrabatt und „Maximaler Mengenrabatt wird angewendet auf“__
Es wurde ein Problem mit dem Rabatt auf Warenkorbregeln behoben, wenn der Rabatt auf einen festen Betrag so konfiguriert ist, dass er auf eine begrenzte Anzahl von Produkten angewendet wird, wenn der Warenkorb der Warenkorb ist. Zuvor wurde der Wert „Maximaler Mengenrabatt wird auf angewendet“ verwendet, um den Preis des aktuellen Artikels im Warenkorb zu berechnen, nicht nur für die Berechnung des Rabatts der Regel.
  _ACP2E-3332 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __[CLOUD] Beim Magento-Upgrade wurde zwischen Groß- und Kleinschreibung unterschieden__
Vor der Fehlerbehebung mussten Sie den Gutscheincode genau so eingeben, wie er unter Berücksichtigung von Groß- oder Kleinbuchstaben konfiguriert wurde. Jetzt wird der Coupon im Backend validiert, unabhängig von der Code-Konfiguration in Groß- oder Kleinbuchstaben.
  _ACP2E-3342_
* __Warenkorbregeln „Fester Rabatt auf den gesamten Warenkorb“  Aktion wendet Rabatte falsch an__
Couponcodes werden bei Verwendung der Auftragserstellung im Admin-Bereich unabhängig von Groß- oder Kleinschreibung ordnungsgemäß validiert. Zuvor wurde der Couponcode nicht validiert, wenn er nicht mit der exakten Groß-/Kleinschreibung des konfigurierten Warenkorb-Regel-Codes übereinstimmte.
  _ACP2E-3349 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Im Backend speichern Sie Standardwerte für Produktattribute (anstelle der erwarteten Administratorwerte)__
Im Backend werden jetzt Admin-Werte anstelle der standardmäßigen Store-Werte für Produktattribute verwendet.
  _ACP2E-3374 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5184c067)_
* __Die Aktion „Warenkorbregeln - Fester Rabatt für den gesamten Warenkorb“ wendet Rabatte beim Hinzufügen von Bundle-Produkten falsch an__
Regeln zum Warenkorb mit festem Betrag wurden für Bundle-Produkte nicht ordnungsgemäß angewendet. Jetzt werden bei der Berechnung des gesamten Rabattbetrags untergeordnete Bundle-Produkte berücksichtigt, was zu einer korrekten Rabattberechnung führt.
  _ACP2E-3377 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __Die Regeln für den Warenkorbpreis berechnen den Rabatt falsch__
Festbetragsrabatte werden jetzt ordnungsgemäß berechnet. Vor der Fehlerbehebung wurden die Festbetragsrabatte für Bundle-Produkte nicht korrekt summiert.
  _ACP2E-3403 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0b488dd1)_
* __Verschachtelte Kategorien in Regelbedingungen werden nicht angezeigt__
Es wurde ein Problem behoben, bei dem verschachtelte Kategorien unter der Kategorie der Ebene 3 in Marketing-Regeln für die Kategoriebedingung nicht angezeigt wurden
  _ACP2E-3406 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_
* __usage_limit und uses_per_customer werden nicht in der salesrule_coupon-Tabelle aktualisiert__
Die Aktualisierung der Preisregel Benutzer pro Coupon und Benutzer pro Kunde im Warenkorb wirkt sich jetzt auf bestehende automatisch generierte Coupons aus. Zuvor waren von den neuen Werten nur neue Coupons betroffen
  _ACP2E-3432 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/88660e79)_
* __Die Warenkorb-Preisregel berücksichtigt keine übergeordnete Kategorie, wenn die Bedingung „ist gleich oder größer als“ verwendet wird.__
Warenkorbpreisregeln berücksichtigen jetzt die übergeordnete Kategorie korrekt, wenn sie in erweiterten Bedingungen verwendet wird
  _ACP2E-3456 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/93359343)_
* __Ungültige Rabattberechnung mit Priorität__
Im Falle eines festen Betrags, der für den gesamten Warenkorb-Rabatttyp angewendet wurde, wurde der Betrag für Warenkorbartikel, die bereits durch eine frühere Promotion diskontiert wurden, nicht ordnungsgemäß berechnet. Jetzt sind die Rabatte richtig zusammengefasst.
  _ACP2E-3463 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD] Die Versandberechnung berücksichtigt nicht die Warenkorbregel__
Vor der Fehlerbehebung wurde eine Warenkorb-Regel mit der Bedingung Region nicht konsistent angewendet. Nach der Fehlerbehebung werden Warenkorbregeln mit Regionsbedingungen ordnungsgemäß angewendet.
  _ACP2E-3472 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_
* __Warenkorbregel-SKU-Bedingung schlägt für Rechnung fehl.__
Rabatt auf Bundle-Produkt mit dynamischem Preis wird jetzt korrekt in der Rechnung angezeigt. Zuvor wurde der Rabatt nicht in der Rechnung berücksichtigt.
  _ACP2E-3491 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Falscher Rabattwert, wenn mehrere Warenkorbpreisregeln gleichzeitig mit Produkten mit Rabatt/Sonderpreis angewendet werden__
Vor der Festsetzung wurde der Festbetrag für Regeln für den gesamten Warenkorb nicht ordnungsgemäß angewendet, wenn mehr als eine angewendet wurde. Jetzt werden die Regeln für den Rabatt auf feste Beträge ordnungsgemäß angewendet.
  _ACP2E-3498 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1984c61c)_

### Rückgabe

* __[CLOUD] Benutzer mit eingeschränktem Administratorzugriff können das Menü und die Schaltflächen für die Rückkehr sehen__
Benutzende mit eingeschränktem Administratorzugriff haben jetzt keinen Zugriff mehr auf RMA-bezogene Steuerelemente (Menü und Schaltflächen).
Zuvor eingeschränkte Admin-Benutzer konnten das Menü und die Schaltflächen „Zurück“ sehen.
  _ACP2E-3330_
* __Der Rückkehrbildschirm ist beim Aktualisieren des Bildschirms verkorkst__
Der/die Benutzende kann die Seite aktualisieren, ohne dass es zu einer Bildschirmverzerrung kommt.
  _ACP2E-3443_

### SEO

* __Das Hinzufügen von URL-Neuschreibungen mit einem Akzent verursacht unendliche Ladevorgänge__
Das System erstellt jetzt erfolgreich URL-Funktionen und schreibt sie mit Akzenten um, wodurch das unendliche Laden während des Speichervorgangs verhindert wird. Zuvor führte das Hinzufügen einer URL-Umschreibung mit einem Akzent zu einem unendlichen Ladeproblem.
  _AC-11907 - [GitHub-Problem](https://github.com/magento/magento2/issues/38692) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44cef3a9)_
* __Multi Store Falsche Kategorie URL-Rewrite für Kategorie der dritten Ebene__
Generieren korrekter URL-Neuschreibungen für untergeordnete Elemente mit einem übergeordneten Element mit benutzerdefiniertem URL-Schlüssel
  _ACP2E-2641 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Doppelbyte-Zeichen (Sonderzeichen) im Feld Produktname blockieren die Produkterstellung im Backend__
Es wurde eine neue Einstellung hinzugefügt, mit der Sie die Transliteration auf die Produkt-URL anwenden können oder nicht. Einstellung ist hier verfügbar: Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung: „Transliteration für Produkt-URL anwenden“
  _ACP2E-2770 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __Falsche Erstellung von url_rewrite Einträgen mit mehreren Stores in einer Store-Gruppe__
Vor der Fehlerbehebung konnten Sie beim Bearbeiten eines Produkts nur URL-Neuschreibungen auf Website-Ebene generieren. Mit der Fehlerbehebung wurde eine neue Einstellung eingeführt (Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung, „Produkt-URL-Neuschreibungsbereich“ mit Optionen „Store-Ansicht“, „Website„), mit der Sie URL-Neuschreibungen auf Store-Ansicht- oder Website-Ebene generieren können.
  _ACP2E-3383 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2d627301)_

### Verkauf

* __Die Preisregel für den zweiten Warenkorb wird nicht angewendet, wenn die Regel für den ersten Warenkorb bereits angewendet wurde__
  _AC-13751_

### Suche

* __Erhalten von „Geben Sie einen Suchbegriff ein und versuchen Sie es erneut.“ Fehler auf der Seite für die erweiterte Suche in der Storefront in 2.4.8-Beta1__
Das System zeigt jetzt die Suchergebnisse auf der Seite Erweiterte Suche korrekt an, wenn ein Produktattribut auf „Nein“ gesetzt ist. Wenn Sie ein Produktattribut zuvor auf „Nein“ festgelegt und eine Suche durchgeführt haben, wird die Fehlermeldung „Geben Sie einen Suchbegriff ein und versuchen Sie es erneut.“
  _AC-13053 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ea26621)_
* __Magento/module-open-search ist von einer nicht vorhandenen OpenSearch-PHP-Verzweigung abhängig__
  _AC-13721 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/05dc0bbf)_
* __SEARCH_QUERY-Tabelle hat bei großer Größe große Auswirkungen auf die Ladezeit von Frontend__
Die Ladezeit der Suchauflistungsseite wurde verbessert. Vor der Fehlerbehebung wurde die Suchauflistungsseite aufgrund einer nicht optimierten Abfrage verzögert.
  _ACP2E-3362 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

### Sicherheit

* __[Problem] Fehlendes PayLater-Popup für Schriftart-CSP__
Das System erlaubt jetzt das Laden der Schriftart &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;, ohne gegen die Content Security Policy Direktive zu verstoßen, um die korrekte Anzeige des Paylater Popup sicherzustellen. Zuvor wurde das Laden der Schriftart aufgrund eines Verstoßes gegen die Content Security Policy-Direktive abgelehnt, was zu Anzeigeproblemen mit dem Paylater-Popup führte.
  _AC-11855 - [GitHub-Problem](https://github.com/magento/magento2/issues/38624) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37401)_
* __[Problem] Aktualisieren des js.js-DOM-Texts, neu interpretiert als HTML__
Durch die Verwendung von innerText wird das Risiko einer HTML-Injektion vermieden, da diese Eigenschaften automatisch alle HTML-Sonderzeichen im bereitgestellten Text mit Escape-Zeichen versehen. Diese Fehlerbehebung hilft, Sicherheitslücken beim Cross-Site-Scripting (XSS) zu vermeiden, indem die Eingabe als reiner Text behandelt wird, anstatt als HTML interpretiert zu werden.
  _AC-12035 - [GitHub-Problem](https://github.com/magento/magento2/issues/38767)_
* __ReCaptcha V2 wird an der Kasse für die deutsche Sprache falsch angezeigt__
Zuvor erscheint das reCAPTCHA von unter der E-Mail-Adresse von der Kasse für Sprachen mit langen Wörtern wie Deutsch ungestylt. Danach sieht das reCAPTCHA genauso aus wie alle reCAPTCHA-Elemente aus dem Rest der Bereiche.
  _ACP2E-3273 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7377de59)_
* __Captcha bei der Admin-Anmeldung erfordert für einige Benutzer keine Interaktion__
ReCaptcha für die Admin-Anmeldung wird erwartungsgemäß validiert
  _ACP2E-3300 - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/8f64ab3c)_

### Lieferung

* __[Problem] Tippfehler in tracking.phtml behoben - JS-Funktionen wurden in „currier“ und „carrier“ umbenannt__
Das System verwendet nun in den in der Bestellverfolgungsvorlage verwendeten JavaScript-Handler-Funktionen korrekt den Begriff „Carrier“ anstelle des falsch geschriebenen „Currier“, um eine ordnungsgemäße Funktionsbenennung und Code-Klarheit zu gewährleisten. Zuvor wurde der falsch geschriebene Begriff „Currier“ verwendet, was zu Verwirrung und Inkonsistenz in der Codebasis führen konnte.
  _AC-10757 - [GitHub-Problem](https://github.com/magento/magento2/issues/34523) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33414)_
* __UPS REST „Eine Sendung darf keine KGS/IN- oder LBS/CM- oder OZS/CM-Einheit als Maßeinheit haben“__
Stellen Sie sicher, dass UPS-Tarife an der Kasse und im Warenkorb sichtbar sind.
  _AC-11938 - [GitHub-Problem](https://github.com/magento/magento2/issues/38618) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/493e01f5)_
* __UPS-REST-„Sandbox“- und „prod“-Setup-Anleitungsaktualisierungen in devDoc__
  _AC-12938_
* __[Problem] Korrigieren Sie die Schreibweise der Variablen für die Kundenadresse__
Das System schreibt nun Variablen für Kundenadressen korrekt und gewährleistet so eine genaue Anzeige im Kontobereich des Frontends. Zuvor konnte eine falsche Schreibweise dieser Variablen zu Fehlern bei der Überprüfung des lokalen Codes führen.
  _AC-13172 - [GitHub-Problem](https://github.com/magento/magento2/issues/32817) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32815)_
* __Tracking-Fenster mit dem falschen erwarteten Versanddatum__
Zeigt das richtige Lieferdatum für den Fedex-Provider an.
  _ACP2E-2738 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_
* __Die Tabelle zeigt immer noch an, obwohl kostenloser Versand angewendet wird__
Die Versandmethode Tabelle Tarif wird jetzt angezeigt, auch wenn der kostenlose Versand nach Anwendung des Coupons verfügbar wird
  _ACP2E-2763 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __MFTF-Test AdminCreatingShippingLabelTest schlägt fehl aufgrund von Anmeldeinformationen, die nicht in der Jenkins-Umgebung hinzugefügt wurden__
MFTF-Testkorrektur
  _ACP2E-2765 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __FedEx-Tracking-API funktioniert nicht mit REST-Anmeldeinformationen__
Zuvor waren für die FedEx-Integration keine zusätzlichen API-Schlüssel für die Tracking-API erforderlich. Jetzt wurde eine neue Konfiguration hinzugefügt, um Tracking-API-Schlüssel zu unterstützen.
  _ACP2E-3340 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] FedEx Ausgehandelte Tarife werden nicht auf REST zurückgegeben__
Vor der Fehlerbehebung wurden FedEx-kontospezifische Raten in der Antwort nicht gesendet, auch wenn sie laut FedEx-Dokumentation hätten gesendet werden müssen. Nach der Fehlerbehebung werden die kontospezifischen Tarife für die Antwort gesendet, indem die Anfrage von unserer Seite geändert wird.
  _ACP2E-3354 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/55615e61)_

### Staging und Vorschau

* __Einstellungen für das geplante Update werden nicht gespeichert, wenn sie ursprünglich durch Ausführen des Updates hinzugefügt wurden__
Das System löscht Produktattributwerte jetzt bei nachfolgenden geplanten Aktualisierungen korrekt, wenn solche Attribute in der aktuell ausgeführten Aktualisierung geändert werden. Wenn ein Produktattribut zuvor durch eine laufende geplante Aktualisierung geändert wurde, war es nicht möglich, diese Attributwerte beim Erstellen einer neuen geplanten Aktualisierung zu löschen, sodass die Benutzenden sie nach der Erstellung erneut bearbeiten mussten.
  _ACP2E-2901_
* __Warenkorb-Preisregel vom Datum und bis zum Datum, Problem nicht mit Staging-Aktualisierung synchronisiert__
Datumsangaben werden gemäß Aktualisierungen für die Staging-Regel Warenkorb-Preis gespeichert.
  _ACP2E-2999_
* __JS-Fehler in der Staging-Vorschau__
Jetzt wird die Datei „form-mini-stub.js“ ohne JS-Syntaxfehler in den Entwickler-Tools erfolgreich geladen.
  _ACP2E-3104_
* __Staging-Inhalte zum Sonderpreis für Produkte können nicht aktualisiert werden__
Das System ermöglicht jetzt die Bearbeitung des Enddatums einer Preisaktualisierungskampagne, nachdem sie gestartet wurde, sodass Benutzende die erforderlichen Anpassungen an ihren Kampagnen vornehmen können. Zuvor wurde beim Versuch, das Enddatum einer aktiven Kampagne zu aktualisieren, ein Fehler ausgelöst, der Benutzer daran hinderte, Änderungen vorzunehmen.
  _ACP2E-3162_
* __Geplante Aktualisierung kann bei Verwendung eines eindeutigen benutzerdefinierten Kategorieattributs nicht aktualisiert werden__
Es wurde ein Problem behoben, bei dem das Aktualisieren einer geplanten Aktualisierung für eine Kategorie nicht möglich war, wenn die Kategorie ein eindeutiges Attribut hatte
  _ACP2E-3453 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

### Targeting

* __[Problem] Zulassen der Verwendung von CIDR-Bereichen in der Wartungs-Zulassungsliste__
Das System unterstützt jetzt die Verwendung von CIDR-Bereichen in der Zulassungsliste des Wartungsmodus, sodass ein Bereich von IP-Adressen den Wartungsmodus umgehen kann. Zuvor erlaubte der Wartungsmodus, dass die IP-Liste nur einzelne IP-Adressen den Wartungsmodus umgeht.
  _AC-9432 - [GitHub-Problem](https://github.com/magento/magento2/issues/37943) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30699)_

### Steuer

* __[Problem] Feature/php8.1 Konstruktor Eigenschaftsförderung wee Graph ql__
Ersetzen Sie fast alle Eigenschaften mit dem Konstruktor-Eigenschaftsförderungsmodul in der Graph-SQL:
  _AC-13295 - [GitHub-Problem](https://github.com/magento/magento2/issues/39309) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36975)_
* __Feste Produktsteuer (FPT) funktioniert nicht mit konfigurierbaren Produkten__
FPT für konfigurierbare Produktvarianten, die ordnungsgemäß funktionieren.
  _ACP2E-3193 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### Test-Framework

* __Integrationstest schlägt fehl bei testDbSchemaUpToDate aufgrund von JSON-Spaltentyp__
Das System erkennt jetzt JSON-Spaltentypen im Datenbankschema während der Integrationstests korrekt, um Testfehler aufgrund einer Diskrepanz zwischen dem Datenbankschema und dem deklarativen Schema zu verhindern. Zuvor hat das System JSON-Spaltentypen in MariaDB fälschlicherweise als LONGTEXT identifiziert, wodurch Integrationstests fehlschlugen.
  _AC-11654 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef81f5a2)_
* __[Problem] Rechtschreibung für PHPDoc-Korrektur__
Das System erkennt nun veraltete Methoden in IDEs aufgrund einer Rechtschreibkorrektur im PHPDoc korrekt. Zuvor führte ein Rechtschreibfehler im PHPDoc dazu, dass IDEs bestimmte Methoden nicht als veraltet erkannten.
  _AC-13362 - [GitHub-Problem](https://github.com/magento/magento2/issues/31399) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31398)_
* __MAGETWO-95118: Überprüfen des Verhaltens beim beständigen Warenkorb nach Ablauf der Sitzung__
  _AC-13478 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7d5e3906)_
* __Integrationstests sind fehlgeschlagen Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission__
  _AC-13716_
* __[Datenbankvergleich] Schwerwiegender Fehler, wenn die Datenbank einen Datensatz über Target enthält Regel ohne Bedingungen__
Früher, wenn die Datenbank einen Datensatz über die Target-Komponente enthält, erhielt Regel ohne Bedingung schwerwiegende Fehler, aber nach der Korrektur verläuft der Datenbankvergleich Tool erfolgreich ohne schwerwiegende Fehler.
  _AC-13722_
* __Korrigieren Sie statische Tests, um die Verwendung von Erweiterungen von 3D-Anbietern zu ermöglichen__
  _AC-13848 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9e383b4d)_
* __[Intern] Fehler bei der Anwendung der Vorrichtung wird während der Ausführung oder in Protokollen nicht angezeigt__
&#39;-
  _ACP2E-3334 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d4de4726)_
* __[MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest__
Feste MFTFs
  _ACP2E-3458 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/078c387e)_

### UI-Framework

* __Behebung von Sicherheitslücken in Prototype.js CVE-2020-27511__
Das System wurde aktualisiert, um die Sicherheitslücke CVE-2020-27511 in Prototype.js 1.7.3 zu beheben und so die allgemeine Sicherheit des Systems zu verbessern. Vor diesem Update war das System anfällig für einen regulären Ausdrucks-Denial-of-Service (ReDOS) durch Strippen von erstellten HTML-Tags.
  _AC-12128 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Grunt Less verwendet das Pub/Präfix für Quellenkarten__
Das System generiert jetzt bei Verwendung von grunt LESS/css-Quellzuordnungen ohne das Präfix /pub für Pfade, sodass keine Problemumgehung in der Webserver-Konfiguration erforderlich ist. Zuvor war für die Verwendung des Präfixes /pub in Quellzuordnungspfaden eine bestimmte Konfiguration im Webserver erforderlich, damit es ordnungsgemäß funktioniert.
  _AC-12189 - [GitHub-Problem](https://github.com/magento/magento2/issues/38837) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38840)_
* __Feld für Komponentendatei der Benutzeroberfläche__
Das System validiert das Dateifeld in einem Benutzeroberflächen-Komponentenformular jetzt korrekt, sodass das Formular ohne Fehler gesendet werden kann, wenn eine Datei ausgewählt wird. Zuvor schlug die Validierung auch dann fehl, wenn eine Datei ausgewählt wurde, was verhinderte, dass das Formular gesendet wurde.
  _AC-12432 - [GitHub-Problem](https://github.com/magento/magento2/issues/38908) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39004)_
* __[Problem] Verbessertes Datumsformat in der js-Konsole: von 12 auf 24 Stunden wechseln…__
Verbessertes Datumsformat in der JS-Konsole: Wechsel von 12 auf 24 Stunden
  _AC-12645 - [GitHub-Problem](https://github.com/magento/magento2/issues/38983) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38972)_
* __[Problem] SourceMap-Generierung für weniger Dateien im Entwicklermodus hinzufügen__
Das System generiert jetzt Quellzuordnungen für weniger Dateien, wenn sie sich im Entwicklermodus befinden, wodurch die Identifizierung der Quelle eines Stils erleichtert wird. Zuvor war es schwierig, die Quelle eines Stils zu identifizieren, wenn das System im Entwicklermodus ohne Server-seitige Kompilierung ausgeführt wurde.
  _AC-12650 - [GitHub-Problem](https://github.com/magento/magento2/issues/38982) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38977)_
* __Statischer Inhalt wird für deaktivierte Module bereitgestellt__
Das System schließt jetzt CSS für deaktivierte Module aus den endgültigen CSS-Ausgabedateien aus, um sicherzustellen, dass unnötige Stile nicht geladen werden. Zuvor wurde CSS für deaktivierte Module in die endgültigen CSS-Ausgabedateien eingefügt, was dazu führte, dass zusätzliche, unnötige Stile geladen wurden.
  _AC-1306 - [GitHub-Problem](https://github.com/magento/magento2/issues/24666) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32922)_
* __Inkonsistentes Verhalten bei der Sortierung „Nicht vorrätig“ mit Mindestbestandsschwellenwert__
Das System sortiert jetzt Produkte im Katalog korrekt anhand der Lagerbestände, hält sich dabei an die festgelegte Mindestbestandsschwelle und verschiebt nicht vorrätige Artikel konsequent an das Ende der Liste. Zuvor war das Sortierverhalten inkonsistent, da Elemente basierend auf ihren Lagerbeständen nicht immer in der richtigen Reihenfolge angezeigt wurden und Änderungen bei der Sortierung nach dem Speichern, Aktualisieren oder Ändern der Kategoriehierarchie unvorhersehbar auftreten konnten.
  _AC-13459 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47b448e2)_
* __Vorschlag für eine verbesserte Fehlerberichterstattung bei „Require.js“-Ladeproblemen__
Diese PR verbessert die Fehlermeldung, wenn eine Komponente bei Bedarf nicht geladen werden kann.
  _AC-13472 - [GitHub-Problem](https://github.com/magento/magento2/issues/36761) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38971)_
* __PHP 8.4 Veraltungsfehler, die Build-Fehler in 2.4-develop verursachen__
  _AC-14004 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1da9ba6f)_
* __[Problem] Laden Sie den Backend-Blockkontext nicht in Frontend__
Das System stellt jetzt sicher, dass der Backend-Block-Kontext nicht in das Frontend geladen wird, wodurch die Erstellung unnötiger Backend-Sitzungen und potenzieller Sitzungssperren verhindert wird. Zuvor hat das System fälschlicherweise den Backend-Blockkontext im Frontend geladen, was zur Erstellung von Backend-Sitzungen und potenziellen Sitzungssperren geführt hat.
  _AC-9007 - [GitHub-Problem](https://github.com/magento/magento2/issues/37617) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36368)_
* __[Problem] Entfernen unnötiger Skripte - Überprüfungszusammenfassung__
Das System optimiert jetzt die Seitenladezeit, indem unnötige JavaScript-Skripte aus dem Bewertungsabschnitt entfernt werden, anstatt Inline-CSS-Stile zu verwenden, um Code effizienter und lesbarer zu gestalten. Zuvor konnte die Verwendung von JavaScript-Skripten für den Bewertungsabschnitt die Seitenladezeit möglicherweise verlangsamen.
  _AC-9168 - [GitHub-Problem](https://github.com/magento/magento2/issues/37776) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/34643)_
* __Ausnahme beim Überprüfen des Guthabens einer Geschenkkarte, wenn reCAPTCHA aktiviert ist__
Benutzer können den Guthaben der Geschenkkarte auf dem Bildschirm zum Anzeigen und Bearbeiten des Warenkorbs abrufen. Zuvor wurden diese Details nicht angezeigt, während reCAPTCHA aktiviert war.
  _ACP2E-2529 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_
* __[CLARIFICATION] Einhaltung der Funktionsanfrage-ADA__
Das System stellt jetzt die ADA-Konformität sicher, indem es nicht unterstützte CSS-Eigenschaften entfernt und sie durch unterstützte in der Datei „print.css“ ersetzt. Zuvor führte die Verwendung nicht unterstützter CSS-Eigenschaften zu Problemen mit der Browser-Kompatibilität.
  _ACP2E-2729 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] Confusion-Bibliothekscode in effect-drop.js von AC 2.4.4-p8__
Das System implementiert nun die Bibliothek „effect-drop.js“ korrekt, um die ordnungsgemäße Funktion der jQuery-UI-Effekte sicherzustellen. Zuvor wurde die Bibliothek „effect-drop.js“ versehentlich mit der Bibliothek „effect-clip.js“ überschrieben, was zu Problemen mit jQuery-UI-Effekten führen konnte.
  _ACP2E-3061 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/35b1b1da)_
* __Site-Kopfzeile | Sonderzeichen, die den Abschnitt „Kundenempfehlung“ durchbrechen__
Nach der Fehlerbehebung werden Sonderzeichen im Begrüßungsabschnitt des Kunden korrekt angezeigt.
  _ACP2E-3367 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __Die Kundensegmentbearbeitung schlägt mit daterange fehl__
Es ist möglich, ein Kundensegment mit der Bedingung „Datumsbereich“ zu speichern, wenn nur eines der Daten bearbeitet wurde.
  _ACP2E-3561 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a52ff98f)_
