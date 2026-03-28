---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '24355'
ht-degree: 0%

---
# Behobene Probleme in Magento Open Source (v2.4.9-beta1)

## Behobene Probleme in v2.4.9-beta1

Es wurden 501 Probleme im Magento Open Source 2.4.9-beta1-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

#### Sonderpreis Bis dato wird bei applySpecialPrice falsch validiert

Das System funktioniert einwandfrei bezüglich des Sonderpreises. Der Sonderpreis für das Produkt läuft an dem Datum ab, das vom Administrator oder dem Drittanbietersystem durch die REST-API festgelegt wurde

_AC-13130 - [GitHub-Problem](https://github.com/magento/magento2/issues/39169) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39690)_

#### [WebAPI] Kunden-E-Mail-Bestätigung über das WebAPI-Paradox

Es wurde ein Problem behoben, bei dem Kundinnen und Kunden ihre Konten über die Web-API nicht aktivieren konnten, da ein Autorisierungsparadox ein Token vor der Bestätigung erforderte. Die Aktualisierung ermöglicht es nicht bestätigten Kundinnen und Kunden, ihre Konten erfolgreich über die API zu aktivieren, was einen konsistenten und funktionalen Bestätigungsfluss gewährleistet.

_AC-13281 - [GitHub-Problem](https://github.com/magento/magento2/issues/39255) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Fehler „Rechnungsadresse fehlt“ im Admin-Dashboard beim Erstellen einer Bestellung über die REST-API mit nur Zahlungsinformationen

Es wurde ein Problem behoben, bei dem Bestellungen ohne Rechnungsadresse über die API erstellt werden konnten, was zu Abstürzen im Admin-Dashboard führte.
Jetzt werden Bestellungen ohne Rechnungsadresse eingeschränkt und nicht mehr erstellt.

_AC-14049 - [GitHub-Problem](https://github.com/magento/magento2/issues/39651) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problem beim Hinzufügen eines Produkts zum Warenkorb in der REST-API

Es wurde ein Problem behoben, bei dem Produkte, die keiner bestimmten Website zugewiesen waren, weiterhin in den Warenkorb gelegt und gekauft werden konnten.
Jetzt wird eine Fehlermeldung angezeigt: „Das Produkt, das Sie hinzufügen möchten, ist nicht verfügbar.“

_AC-15054 - [GitHub-Problem](https://github.com/magento/magento2/issues/40029) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f5cc09fc)_

#### Attributoptionstitel wird beim Aktualisieren von Store-Titeln überschrieben

Es wurde ein Problem behoben, bei dem durch die Aktualisierung eines multiselect-Produktattributs über die REST-API alle store_labels überschrieben und vorhandene store-spezifische Kennzeichnungen entfernt wurden.
Beim Aktualisieren der standardmäßigen Kennzeichnung für die Store-Ansicht führt Magento jetzt die bereitgestellten Kennzeichnungen mit den vorhandenen zusammen, anstatt sie vollständig zu überschreiben.
Dadurch wird sichergestellt, dass Store-spezifische Beschriftungen für andere Store-Ansichten nach Aktualisierungen intakt bleiben.

_AC-15208 - [GitHub-Problem](https://github.com/magento/magento2/issues/40093) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Problem] Die Option „Präzisiertes Attribut“ existiert bereits als Antwort

Das System ersetzte nun den peinlichen Satz „Get new file name if the same is already exists“ durch eine klarere und grammatisch korrekte Version: „Get a new file name if one already exists“ (Erhalten Sie einen neuen Dateinamen, falls bereits vorhanden). Dies verbessert die Lesbarkeit und das Benutzerverständnis.
Dasselbe gilt für die Antwort der Attributoption.

_AC-15473 - [GitHub-Problem](https://github.com/magento/magento2/issues/39943) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39941)_

#### Interner Server-Fehler in API-Endpunkt /V1/products/special-price

Fehlerhafte Anfragen an /V1/products/special-price und die zugehörigen Preis-APIs haben jetzt aufgrund eines Null-TypeError einen internen Server-Fehler von 500 zurückgegeben.
Jetzt überprüfen die APIs die Eingabe ordnungsgemäß und geben einen 400-Fehler für ungültige Payloads zurück, was die Fehlerbehandlung und die API-Zuverlässigkeit verbessert.

_AC-6419 - [GitHub-Problem](https://github.com/magento/magento2/issues/35934) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a7ef6300)_

#### Interner Server-Fehler `/V1/order/&lbrace;orderId&rbrace;/ship` API-Endpunkt

Das System behebt jetzt den internen Server-Fehler in `/V1/order/{orderId}/ship` API-Endpunkt und gibt einen 400-Fehler zurück, da die Anfrage fehlerhaft ist.

_AC-6420 - [GitHub-Problem](https://github.com/magento/magento2/issues/35931) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38282)_

#### Interner Server-Fehler im API-Endpunkt /v1/creditmemo

Fehlerhafte Anfragen an die /V1/creditmemo-API haben jetzt einen 500-Fehler zurückgegeben.
Jetzt validiert die API die Anfrage ordnungsgemäß und gibt bei ungültigen Payloads einen 400-Fehler zurück, was die Fehlerbehandlung und -stabilität verbessert.

_AC-6422 - [GitHub-Problem](https://github.com/magento/magento2/issues/35924) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a7ef6300)_

#### Die REST-API und das Magento-Backend verwenden beim Erstellen neuer Attribute unterschiedliche Validierungsmethoden für attribute_code

Fehlerkorrektur - Der Magento-Administrator erlaubt jetzt Großbuchstaben im attribute_code, aber die REST-API lehnt diese bei der Erstellung von Produktattributen ab.
Jetzt folgen sowohl die Admin- als auch die REST-API der gleichen Validierung, was die erfolgreiche Erstellung von Attributen mit Großbuchstaben ermöglicht.

_AC-6660 - [GitHub-Problem](https://github.com/magento/magento2/issues/33138) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Unterschiedliche Validierung zwischen Attributerstellung und -aktualisierung über REST-API

Es wurde ein Problem behoben, bei dem eine inkonsistente Validierung während der Attributerstellung über die REST-API dazu führte, dass ein falscher Backend-Typ zugewiesen wurde.
Jetzt legt das System den richtigen Backend-Typ fest, wenn er gültig ist, gibt eine Ausnahme für ungültige Werte aus oder springt entsprechend zurück, wenn er nicht angegeben wird, um ein konsistentes Attributverhalten zu gewährleisten.

_AC-6885 - [GitHub-Problem](https://github.com/magento/magento2/issues/36327) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64823f95)_

#### Fehlerhafter Anfragetext oder fehlerhafte Parameter verursachen „Interner Server-Fehler“

Fehlerhafte Anfragetexte oder -parameter geben jetzt eine eindeutige „400 Bad Request“-Antwort zurück.
Zuvor führte das Senden fehlerhafter Anfragetexte oder Parameter an verschiedene REST-API-Endpunkte (z. B. /V1/carts/search, /V1/orders, /V1/products usw.) zu einem generischen „Internen Server-Fehler“ (500), wodurch die Diagnose von Eingabeproblemen erschwert wurde.
Jetzt gibt Adobe Commerce die Antwort „400 Fehlerhafte Anfrage“ zurück, die ein klareres Feedback liefert, wenn Anfragen ungültig sind.

_AC-746 - [GitHub-Problem](https://github.com/magento/magento2/issues/32784) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders` (oder `/orders/:id`) Endpunkt fehlt das Feld „Status“ und „Status“

Es wurde ein Problem behoben, bei dem in den `/orders`- und `/orders/{id}`-API-Antworten die Status- und Statusfelder weggelassen wurden, wenn die Datenbankwerte null waren.
Jetzt werden beide Felder in der Antwort konsistent zurückgegeben, was die Einhaltung der API-Dokumentation gewährleistet und die Datenzuverlässigkeit verbessert.

_AC-9244 - [GitHub-Problem](https://github.com/magento/magento2/issues/37807) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Der asynchrone Massenvorgang bleibt für „async.magento.configurableProduct.api.optionRepositoryInterface.save.post“ im geöffneten Status.

Bulk-API-Endpunkte geben jetzt einen Fehler aus, wenn der Anfragetext kein Array ist, sodass Bulk-Elementschlüssel aufeinander folgende Zahlen sein müssen, die mit 0 beginnen. Zuvor wurde der Status des Massenelements aufgrund des willkürlichen Elementschlüssels, der in der Massenanfrage übermittelt wurde, nicht aktualisiert.

_ACP2E-3544 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### [CLOUD] API REST-Fehler bei is_subscribed-Wert nicht aus dem aktuellen Store mit searchCriteria berücksichtigt

API-REST-Kundenabfrage ruft mithilfe von searchCriteria den richtigen Wert „is_subscribed“ aus dem richtigen Store ab
Zuvor berücksichtigte die API-REST-Kundenabfrage beim Abrufen des Werts „is_subscribed“ keinen Speicher.

_ACP2E-3621 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all kann mehrere Einträge für 1 SKU erstellen

Gleichzeitige Anfragen zum Speichern und Aktualisieren desselben Produkts werden jetzt serialisiert, um Wettlaufbedingungen zu verhindern, die zu Dateninkonsistenz oder doppelten Produkten führen können

_ACP2E-3744 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Bestellung „base_row_total“ und „row_total“ zeigen in der REST-API-Antwort einen einzelnen Artikelpreis an

Die REST-API-Antwort für Auftragsdetails enthält jetzt die korrekten Werte für die Attribute „base_row_total“ und „row_total“, falls mehrere gleiche Artikel bestellt wurden

_ACP2E-3874 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

#### Der REST-API-Endpunkt export-stock-salable-qty gibt falsche Elemente zurück_total_count

Fehlerkorrektur - Die Paginierung in der API für die verkäufliche Lagerbestände im Lager funktioniert jetzt problemlos, wenn total_count fälschlicherweise auf die Seitengröße beschränkt ist. Zuvor gab bei Verwendung des Endpunkts /rest/all/V1/inventory/export-stock-salable-qty/website/base mit Paginierungsparametern wie page_size=5 das Feld total_count in der Antwort 5 anstelle der tatsächlichen Gesamtzahl der Produkte zurück, die den Suchkriterien entsprechen. Nach dieser Fehlerbehebung spiegelt das Feld total_count jetzt korrekt die Gesamtzahl der verfügbaren Produkte wider, unabhängig vom Parameter page_size, was ein konsistentes Paginierungsverhalten über alle Magento REST-API-Endpunkte hinweg sicherstellt.

_ACP2E-4086 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### Validierungsproblem mit benutzerdefinierten Optionen-IDs in REST-APIs für Warenkorbelemente.

Die REST-APIs V1/guest-carts/&lt;cartId>/items/ und V1/carts/mine/items/ validieren jetzt „product_options.extension_attributes.custom_options“.*.option_id“, um sicherzustellen, dass es auf eine gültige option_id für die Warenkorb-Artikel-SKU verweist. Zuvor wurde dieser Parameter ohne Validierung verarbeitet und in der Datenbank gespeichert.

_ACP2E-4138 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Beim Abrufen des Produkts aus dem Warenkorb und Ändern der Store-Kopfzeilensprache ändert sich nichts.

Die Abfrage &quot;GraphQL CustomerCart“ gibt jetzt Produktattributwerte entsprechend dem Wert der Store-Kopfzeile zurück. Zuvor entsprach das Ändern der Store-Kopfzeilensprache beim Abrufen eines Produkts aus dem Warenkorb über GraphQL nicht der aktualisierten Sprache, was zu einer inkonsistenten Lokalisierung führte.

_ACP2E-4227 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6e134409)_

#### REST-API/Medien-Endpunkt schlägt für Geschenkkartenprodukte fehl - gibt „Das Produkt kann nicht gespeichert werden“ zurück.

Vor der Fehlerbehebung durften Sie Geschenkkartenprodukte erstellen, die keinen Betrag im globalen Umfang enthielten. Mit der Korrektur wurde eine Validierung hinzugefügt, die auf Beträge im globalen Umfang prüft.

_ACP2E-4395 - [GitHub-Problem](https://mcstaging.panini.it/shp_ita_it/)_

### APIs, Warenkorb und Checkout

#### Für Versandinformationen funktioniert die Server-seitige Validierung nicht mit der REST-API

Es wurde ein Problem in der REST-API behoben, bei dem die Validierung von Versandadresseninformationen nicht der im Admin-Backend definierten Attributkonfiguration entsprach. Die Validierung folgt nun ordnungsgemäß den konfigurierten Einstellungen.

_ACP2E-4156 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

### APIs, Katalog

#### API-Endpunkt für Standard-Website-/Store-Brüche bei Preisen löschen

Zuvor führte das Löschen der Standard-Basis-Website und die Verwendung der sekundären Website als Standard-Website zu einem Fehler beim Versuch, den Stufenpreis für die sekundäre Website zu aktualisieren. Nach Anwendung dieser Fehlerbehebung kann der Stufenpreis jedoch erfolgreich aktualisiert werden, selbst wenn die Basis-Website gelöscht oder deaktiviert wird.

_ACP2E-4334 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a3b7032)_

### APIs, Framework

#### Ausnahme bei RedisRequestLogger\RedisClient (Ratenbegrenzer) auf dem Anwendungsserver

Nach der Fehlerbehebung kann die Ratenbegrenzungsfunktion zusammen mit dem GraphQL-Anwendungsserver verwendet werden, wenn die PHP-Redis-Erweiterung installiert ist.

_ACP2E-4237 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e885088b)_

### APIs, Import/Export

#### Die asynchrone Rechnungserstattungs-API erstellt Offline-Erstattungen anstelle von Online-Erstattungen

Es wurden asynchrone Rückerstattungsvorgänge korrigiert, bei denen Rückerstattungsanfragen mit dem `is_online` nicht korrekt verarbeitet wurden.

_ACP2E-4394 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

### APIs, Reihenfolge

#### [CLOUD] Problem mit Bestellinformationen, wobei die Zeile für die 000075568 insgesamt angezeigt wird

Es wurde das Problem behoben, bei dem der Wert row_total_incl_tax in der Antwort der Auftrags-API als Restwert von nahezu null anstelle von 0,00 zurückgegeben wurde, wenn ein Element vollständig diskontiert wurde.

_ACP2E-3950 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### Konto

#### [Problem] Beheben von Tippfehlern in den Optionen für Katalog-Widget-Vorlagen

Das System behebt jetzt Tippfehler in den Vorlagenoptionen für Katalog-Widgets.

_AC-11576 - [GitHub-Problem](https://github.com/magento/magento2/issues/38185) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38178)_

#### [Problem] Unnötiger Abstand im Backend-Raster wurde entfernt

Das System entfernt jetzt unnötigen Abstand im Backend-Raster, wenn Elemente ausgewählt sind

_AC-11579 - [GitHub-Problem](https://github.com/magento/magento2/issues/38502) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32622)_

#### Gespeicherter Kundengruppen-Code stimmt nicht mit der Eingabe bei der Verwendung von Multibyte-Zeichen überein

Es wurde ein Problem behoben, bei dem Kunden-Gruppencodes mit Multibyte-Zeichen abgeschnitten wurden und nicht mit dem eingegebenen Wert übereinstimmten. Die Aktualisierung stellt sicher, dass die vollständige Eingabe korrekt gespeichert wird, sodass Kundengruppen mit Multibyte-Namen präzise erstellt werden können.

_AC-13335 - [GitHub-Problem](https://github.com/magento/magento2/issues/39342) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a06a4a57)_

#### Problem beim Aktualisieren der Kunden-E-Mail im Admin Panel mit der Domain ö und .swiss

Das Admin Panel akzeptiert jetzt Kunden-E-Mails mit Sonderzeichen und Schweizer Domains.
Zuvor schlug das Aktualisieren einer Kunden-E-Mail auf eine Adresse wie max@möstermann.swiss mit Fehlern über ungültige Host-Namen und TLDs fehl.
13409

_AC-13409 - [GitHub-Problem](https://github.com/magento/magento2/issues/39394) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### Schalter zum Abonnieren von Newslettern aktiviert funktioniert nicht pro Website/Store

Das System verwaltet die Anmeldung für Newsletter korrekt, wenn mehrere Websites/Storeviews vorhanden sind, obwohl diese global deaktiviert wurden

_AC-14283 - [GitHub-Problem](https://github.com/magento/magento2/issues/39751) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39752)_

#### [Problem] Entfernte E-Mail-Offenlegung

Das System zeigt jetzt eine Fehlermeldung an, die auf eine falsche E-Mail hinweist, wenn die eingegebene E-Mail nicht zur Bestätigung des Kontos erforderlich ist, unabhängig davon, ob der Kunde existiert oder nicht.

_AC-14561 - [GitHub-Problem](https://github.com/magento/magento2/issues/39574) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39570)_

#### Kommentar zum Wunschlistenelement kann über `updateProductsInWishlist` GraphQL-Mutation nicht gelöscht werden

Es wurde ein Problem behoben, bei dem Wunschlistenkommentare nicht durch GraphQL-Mutationen aktualisiert wurden.
Jetzt werden Kommentare korrekt aktualisiert und in der API-Antwort und Storefront widergespiegelt.

_AC-14682 - [GitHub-Problem](https://github.com/magento/magento2/issues/39911) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Das auf dem Mobilgerät entfernte Produkt wird bis zur erneuten Anmeldung weiterhin im Minivergleichsbereich des Web angezeigt

Das System entfernt jetzt das Produkt sofort aus allen Vergleichsansichten sowohl auf Mobilgeräten als auch im Web, einschließlich des Mini-Vergleichsabschnitts.

_AC-14703 - [GitHub-Problem](https://github.com/magento/magento2/issues/39905) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40023)_

#### Einstellung für Präfix/Suffix anzeigen, die bei Festlegung auf „Nein“ ignoriert wird

Es wurde ein Problem behoben, bei dem das Präfix/Suffix des Kundennamens auch dann in Bestellungen angezeigt wurde, wenn es in der Konfiguration deaktiviert war.
Jetzt werden Präfix-/Suffixwerte aus den Bestelldetails basierend auf der Konfigurationseinstellung entfernt.

_AC-15074 - [GitHub-Problem](https://github.com/magento/magento2/issues/40036) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront Kundenkonto-Register: E-Mail-Adressformat wird mit anderem Domain-Format konvertiert

Dieser Fehler behob ein Problem, bei dem Kunden-E-Mails mit Sonderzeichen in der Domain (z. B. òbe.com) automatisch in das Punycode-Format (tec55241@xn--adbe-mqa.com) konvertiert wurden.
In Magento 2.4.9-alpha3 stellt die Korrektur sicher, dass diese E-Mail-IDs unverändert und gültig bleiben, sodass Versandfehler vermieden werden.

_AC-15177 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Fehlende Validierungsmeldungen (Bild-Fehler) im Registrierungsformular

Es wurde ein Problem behoben, bei dem in Pflichtfeldern auf der Seite zur Erstellung von Kundenkonten keine Validierungsmeldungen angezeigt wurden, wenn sie leer gelassen wurden.
Jetzt werden für alle leeren oder falschen Felder richtige Fehlermeldungen angezeigt.

_AC-15185 - [GitHub-Problem](https://github.com/magento/magento2/issues/40076) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Modaler Titel für Auftragsstornierung fehlt Übersetzung

Das System behebt jetzt eine fehlende Übersetzung im Modal „Auftragsstornierung“ in der Storefront. Wenn ein Kunde auf der Seite Mein Konto > Meine Bestellungen auf die Schaltfläche „Abbrechen“ klickt, wird ein Modal angezeigt, in dem er nach einem Kündigungsgrund gefragt wird. Der Modal-Titel war jedoch zuvor hartcodiert und nicht übersetzbar. Durch diese Änderung wird sichergestellt, dass der modale Titel eine geeignete Übersetzungsmethode verwendet.

_AC-15260 - [GitHub-Problem](https://github.com/magento/magento2/issues/40098) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40100)_

#### Problem nach der Anmeldung in Magento 2.4.8-p1

Es wurde ein Problem in Magento 2.4.8-p1 behoben, bei dem der Link „Konto erstellen“ nach der Anmeldung weiterhin auf der Homepage angezeigt wurde.
Jetzt wird der Link nach der Anmeldung korrekt ausgeblendet, was im Einklang mit anderen Seiten steht.

_AC-15292 - [GitHub-Problem](https://github.com/magento/magento2/issues/40120)_

#### [Problem] Legen Sie isSecureArea fest, bevor Sie einen Kunden löschen.

Das System funktioniert jetzt einwandfrei und dieser PR legt isSecureArea für den Löschvorgang fest und der Kunde kann sich erneut erfolgreich registrieren.

_AC-15723 - [GitHub-Problem](https://github.com/magento/magento2/issues/40211) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38462)_

#### [Cloud] Der Löschvorgang ist aufgrund eines Fehlers im aktuellen Bereich bei der Erstellung des Kundenkontos verboten

Nach der Fehlerbehebung wird beim Speichern eines Kunden mit einer ungültigen Adresse eine Meldung zurückgegeben, die den Grund für die Invalidität anstelle von irrelevantem „Löschvorgang ist für den aktuellen Bereich verboten“ beschreibt.

_ACP2E-3791 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6ea61121)_

#### [B2B] WebAPI-Anfragen durchlaufen eine Endlosschleife für angemeldete Kunden, wenn der „eav“-Cache deaktiviert ist

Nach der Behebung führt die Deaktivierung des eav-Cache bei bestimmten REST-Anfragen nicht zu einer unendlichen Schleife.

_ACP2E-4191 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Fehler beim Laden eines Gebietsschemas

Es wurde ein Problem behoben, bei dem das Erstellen eines Kundenkontos bei Verwendung des arabischen Gebietsschemas fehlschlug und das Geburtsdatum-Attribut so eingestellt war, dass es in der Storefront angezeigt wurde. Das Konto kann jetzt erfolgreich in dieser Konfiguration erstellt werden.

_ACP2E-4311 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2687b487)_

#### Ungültiges Datum bei der Aktualisierung der Kontoinformationen

Kunden können ihr Konto jetzt erfolgreich aktualisieren, wenn sie das arabische Gebietsschema verwenden. Zuvor, beim Versuch, die Kontoinformationen zu speichern, schlug das Geburtsdatum aufgrund eines ungültigen Datumsfehlers fehl.

_ACP2E-4344 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

### Konto, Admin-Benutzeroberfläche

#### [Cloud] Keine solche Entität mit cartId

Es wurde ein Problem behoben, bei dem die Verwendung von Anmelden als Kunde mit zwei Unternehmensadministratorkonten in derselben Sitzung den Fehler „Keine solche Entität mit Warenkorb-ID“ verursachte.

_ACP2E-4137 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e885088b)_

#### Fehlermeldungen in Kundenformularen werden nicht übersetzt

Es wurde ein Problem behoben, bei dem Fehlermeldungen bei der Kundenvalidierung nicht ordnungsgemäß über verschiedene Schnittstellen hinweg übersetzt und formatiert wurden. Validierungsfehler zeigen jetzt korrekt übersetzte Nachrichten in allen Bereichen der Anwendung an: Storefront, AdminHTML, REST-API und GraphQL.

_ACP2E-4354 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

### Admin-Benutzeroberfläche

#### Kategorie Produktraster > Status- und Sichtbarkeitsspalten sind beim Sortieren nach Namen leer

Es wurde ein Problem behoben, bei dem die Spalten Status und Sichtbarkeit im Kategorieproduktraster leer erschienen, wenn nach Produktname sortiert wurde.
Das Raster zeigt nun alle Spaltendaten nach der Sortierung korrekt an, sodass im Admin-Bedienfeld präzise Produktinformationen verfügbar sind.

_AC-10659 - [GitHub-Problem](https://github.com/magento/magento2/issues/38233) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### Store-Switcher für E-Mail-Vorlagen

Es wurde ein Problem behoben, bei dem der Store-Umschalter in der Vorschau der Newsletter-E-Mail-Vorlage beim Klicken auf aufgrund eines veralteten jQuery-Codes nicht geöffnet wurde. Durch die Aktualisierung des Load-Ereignisses wurde die ordnungsgemäße Funktion wiederhergestellt, sodass Benutzer erwartungsgemäß auf den Store Switcher zugreifen können.

_AC-12334 - [GitHub-Problem](https://github.com/magento/magento2/issues/38892) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Der FTP-Wert auf der Warenkorbseite und der Produktseite unterscheidet sich für dieselben Konfigurationen für einfache Produkte.

Die FTP-Werte sind jetzt zwischen den Warenkorb- und Produktseiten für einfache Produkte konsistent.
Zuvor konnten sich die FPT-Werte (Fixed Product Tax) in den Dezimalstellen zwischen den Warenkorb- und Produktseiten unterscheiden, selbst wenn dieselben Konfigurationen angewendet wurden.
13066

_AC-13066 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8953613e)_

#### Die Optionen für Mehrfachauswahl-/Attributauswahl können nicht gespeichert werden, wenn die Farbfelder-Module deaktiviert sind

Mehrfachauswahl-/Attributoptionen können jetzt gespeichert werden, wenn Farbfelder-Module deaktiviert sind.
Zuvor verursachte das Deaktivieren von Farbfeldmodulen Ausnahmen beim Erstellen neuer Mehrfachauswahl-/Attributauswahloptionen.
13071

_AC-13071 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8953613e)_

#### Der FTP-Wert auf der Warenkorbseite und der Produktseite unterscheidet sich bei denselben Konfigurationen für ein dynamisches Produkt

Die FTP-Werte sind jetzt zwischen den Warenkorb- und Produktseiten für dynamische Produkte konsistent.
Zuvor konnten FPT-Werte (Feste Produktsteuer) in Dezimalstellen zwischen den Warenkorb- und Produktseiten für dieselben Konfigurationen unterschiedlich sein.
13075

_AC-13075 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8953613e)_

#### Datumsformat wird in der Datums-UI-Komponente nicht berücksichtigt

Es wurde ein Problem behoben, bei dem die Datums-UI-Komponente das konfigurierte Format ignorierte und falsche Werte anzeigte. Die Korrektur stellt sicher, dass das Datumsfeld jetzt das angegebene Format (z. B. Y-m-d) sowohl für die Anzeige als auch für die Eingabe berücksichtigt.

_AC-13174 - [GitHub-Problem](https://github.com/magento/magento2/issues/39218) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Keine Option zum Löschen von Quellen verfügbar

Es wurde eine Löschoption für Inventarquellen in der Admin-Benutzeroberfläche hinzugefügt, mit der Admins zusätzliche Quellen entfernen können, anstatt sie nur zu aktivieren oder zu deaktivieren. Diese Verbesserung verbessert die Bestandsverwaltung durch eine bessere Kontrolle nicht verwendeter Quellen.

_AC-13354 - [GitHub-Problem](https://github.com/magento/magento2/issues/32362) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### Die Kategoriestruktur in Admin wird nicht erweitert, um alle ausgewählten verschachtelten Kategorien aus Ebene 3 anzuzeigen

Es wurde ein Problem behoben, bei dem die Administrator-Kategoriestruktur nicht erweitert wurde, um ausgewählte verschachtelte Kategorien über Ebene 3 hinaus anzuzeigen. Nach der Fehlerbehebung werden alle ausgewählten Kategorien automatisch erweitert, was die Sichtbarkeit und Benutzerfreundlichkeit in allen kategoriebezogenen Bedingungen verbessert.

_AC-13363 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problem] Verbessern des Benutzererlebnisses mit der Rollenstruktur

Diese Pull-Anfrage fügt Schaltflächen hinzu, um alle zu reduzieren, alle zu erweitern und Verzweigungen mit ausgewählten Elementen zu erweitern. Diese Funktion ist ähnlich der in der Kategoriestruktur bereitgestellten Funktion (Katalog -> Inventar -> Kategorien).

_AC-14020 - [GitHub-Problem](https://github.com/magento/magento2/issues/39654) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36511)_

#### Die Aktionsprotokolle für Import/Export werden nicht in „System“ > „Aktionsprotokolle“ > „Berichtsraster“ erstellt

Die Protokollierung für Import/Export-Admin-Aktionen wurde implementiert, sodass sie jetzt unter System > Aktionsprotokolle > Bericht angezeigt werden. Dadurch wird eine bessere Prüfungsverfolgung gewährleistet, indem Importaktivitäten erfasst werden, die zuvor fehlten.

_AC-14266 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: Der „Sender“-Header muss eine Instanz von &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; sein (nicht &quot;Symfony\Component\Mime\Header\MailboxListHeader„)

Adobe Commerce sendet jetzt erfolgreich Registrierungs-E-Mails, wenn eine benutzerdefinierte Rückgabepfadadresse für SMTP konfiguriert ist. Zuvor wurde in Vanilla Adobe Commerce 2.4.8 mit system/smtp/set_return_path auf 2 und system/smtp/return_path_email auf eine benutzerdefinierte Adresse gesetzt die Kundenregistrierung abgeschlossen, aber die Registrierungs-E-Mail wurde nicht gesendet, und Adobe Commerce protokollierte diesen Fehler: Symfony\Component\Mime\Exception\LogicException: Der „Absender“-Header muss eine Instanz von &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; sein (nicht &quot;Symfony\Component\Mime\Header\MailboxListHeader„).

_AC-14520 - [GitHub-Problem](https://github.com/magento/magento2/issues/39823) - [GitHub-Code-](https://github.com/magento/magento2/commit/1e14bd72) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1514117f)_

#### Aktualisierungsreihenfolge erhält nicht die neuesten benutzerdefinierten Attributdaten

Fehlerkorrektur - Bei der Aktualisierung der Bestellseite werden jetzt die neuesten benutzerdefinierten Kundenattributdaten angezeigt. Nach der Korrektur werden die aktualisierten Attributwerte angezeigt, ohne dass die Bestellung abgebrochen und neu erstellt werden muss.

_AC-14690 - [GitHub-Problem](https://github.com/magento/magento2/issues/30301)_

#### [Problem] Veralteten Escaper ersetzen

Der veraltete getEscaper() wurde entfernt und über den Konstruktor Injection hinzugefügt.

_AC-15132 - [GitHub-Problem](https://github.com/magento/magento2/issues/40062) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38135)_

#### Überlappende Willkommensnachricht in der Produktkategorie in der Ansicht für Mobilgeräte

Es wurde ein UI-Problem behoben, bei dem sich der Begrüßungsname mit Produktkategorien in der mobilen Ansicht überschnitt und Klicks blockierte.
Kategorien sind jetzt vollständig sichtbar und können ohne Überschneidungsprobleme angeklickt werden.

_AC-15166 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Schaltfläche zum Zurücksetzen des Formulars in der Benutzeroberfläche funktioniert nicht erwartungsgemäß

Das System funktioniert jetzt einwandfrei, wenn auf die Schaltfläche zum Zurücksetzen geklickt wird, ohne dass die gesamte Seite neu geladen wird. Die Formulardaten werden zurückgesetzt.

_AC-15204 - [GitHub-Problem](https://github.com/magento/magento2/issues/40092) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40094)_

#### [Problem] PageCache/AccessList: Hinzufügen von CIDR-Unterstützung

Das System akzeptiert jetzt Bereinigungsanfragen innerhalb eines Netzwerks. Es ist einfacher, einfach einen CIDR-Bereich bereitzustellen.

_AC-15804 - [GitHub-Problem](https://github.com/magento/magento2/issues/39953) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37809)_

#### [Problem] Hinzufügen erklärender Titel zu Cache-Verwaltungs-Schaltflächen

Das System fügt den Cache-Verwaltungs-Schaltflächen jetzt erklärende Titel hinzu, wenn Sie den Cursor bewegen

_AC-16212 - [GitHub-Problem](https://github.com/magento/magento2/issues/38607) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38598)_

#### Funktion bereitstellen, um Steuersätze mithilfe des Rasters für Massenlöschungen zu verwenden

Admin-Benutzer können jetzt mehrere Steuersätze gleichzeitig aus dem Admin-Steuersatzraster löschen.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub-Problem](https://github.com/magento/magento2/issues/33399) - [GitHub-Code-](https://github.com/magento/magento2/pull/33484) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Hover-Farbe nicht auf statische Raster in Admin angewendet

Hover-Farben werden jetzt erwartungsgemäß auf die Zeilen der statischen Admin-Raster angewendet.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub-Problem](https://github.com/magento/magento2/issues/35358) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35384)_

#### Einträge vom Typ „reCAPTCHA-Parameter kann nicht aufgelöst werden“ in Exception.log für Google reCAPTCHA Admin Panel

Ein reCAPTCHA-Fehler in der `var/log/exception.log` für die Google V3-reCAPTCHA-Admin-Anmeldung wurde behoben, und es werden keine Fehlermeldungen protokolliert. Zuvor wurde der folgende Fehler alle paar Sekunden ausgelöst, wenn ein Admin-Benutzer die Einstellungen **Konfiguration** > **Sicherheit** > **Google reCAPTCHA Admin Panel** konfiguriert hat: `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub-Problem](https://github.com/magento/magento2/issues/34975) - [GitHub-Code-](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/804dbc2a)_

#### Die Warenkorb-Preisregel mit der Bedingung-SKU berücksichtigt nicht die „führenden Nullen“ in der SKU (SKU: 01234 ist dasselbe wie 1234)

Das System verarbeitet jetzt die Warenkorb-Preisregel korrekt mit der Bedingung SKU und berücksichtigt die „führenden Nullen“ in der SKU

_AC-9428 - [GitHub-Problem](https://github.com/magento/magento2/issues/37919) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39525)_

#### Problem mit dem Verhalten des Werts der Standardattributoption für Mehrfachauswahl

Vor der Korrektur wurden die Standardwerte für mehrere Optionsattribute nicht ordnungsgemäß gespeichert. Nach der Korrektur werden die Werte ordnungsgemäß in der Datenbank gespeichert.

_ACP2E-3523 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Problem beim Verschieben der Produktmenge vom Administrator zurück in den Warenkorb

Wenn Sie eine Bestellung über den Administrator erstellen, werden Produkte im Warenkorb auf der Seitenleiste nicht ausgeblendet, wenn sie zur Bestellung hinzugefügt werden.

_ACP2E-3563 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [Staging2] Gespeicherte Karten sind im Admin-Bedienfeld nicht sichtbar

Es wurde ein Problem behoben, bei dem die Zahlungsoption „Gespeicherte Karte“ nach einem Upgrade nicht mehr im Formular für die Platzierung von Backend-Bestellungen angezeigt wurde.

_ACP2E-3830 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Ein eingeschränkter Admin-Benutzer kann Standardkonfigurationen trotz Store-spezifischer Berechtigungen speichern/aktualisieren

Es wurde das Problem behoben, bei dem Administratoren mit eingeschränkter Administratorberechtigung den Bereich „Standardkonfiguration“ sehen und versuchen konnten, ihn zu aktualisieren, obwohl er nur bestimmten Website-Bereichen zugewiesen war, was zu Verwirrung führen konnte.

_ACP2E-4011 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Konfigurierbarer Produktpreis, der für jeden Shop-Ansichtsbereich unter DB gespeichert wird. Dies führt zu Problemen in der Sortierungsfunktion „Produkte in Kategorie“, bei denen der gespeicherte Preis im Frontend nicht relevant ist.

Das Kontrollkästchen „Standardwert verwenden“ für ein konfigurierbares Produkt wurde entfernt, wenn der Preis pro Website konfiguriert ist und eine Store-Ansicht auf der Seite für die konfigurierbare Produktbearbeitung in der Admin-Benutzeroberfläche ausgewählt ist.

_ACP2E-4036 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]Admin-Passwortrichtlinie entspricht nicht der PCI DSS 4.0-Konformität (mindestens 12 Zeichen)

Administratoren können jetzt die erforderliche Mindestpasswortlänge für Admin-Benutzer über Stores > Konfiguration > Erweitert > Admin > Sicherheit konfigurieren. Diese Verbesserung bietet mehr Sicherheitsflexibilität bei gleichzeitiger Beibehaltung bestehender Passwortrichtlinien. Die Validierung wird sowohl bei der Erstellung/Änderung von Admin-Benutzern als auch beim Speichern der Konfiguration erzwungen, wobei die Frontend-Validierung in Echtzeit erfolgt, um das Benutzererlebnis zu verbessern.

_ACP2E-4044 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

#### Datumsfilterproblem, wenn die Sprache der Admin-Benutzeroberfläche Japanisch ist

Geburtstagsfilter und -spalte verwenden das einheitliche Format M/D/Y, genauso wie Filter/Spalte „Kunde seit“

_ACP2E-4052 - [GitHub-Problem](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### Weiße Blöcke auf beiden Seiten der Admin-Rasterkopfzeile

Fehlerkorrektur - Die visuelle Ausrichtung in Admin-Rastern ist jetzt fehlerfrei. Zuvor wurden beim horizontalen Scrollen durch Produktraster im Admin-Bedienfeld weiße Blöcke auf der linken und rechten Seite der Rasterkopfzeile falsch ausgerichtet angezeigt. Die Rasterkopfzeilenelemente behalten jetzt beim Scrollen die korrekte vertikale Ausrichtung bei und bieten Admins, die große Produktkataloge verwalten, ein klareres visuelles Erlebnis.

_ACP2E-4104 - [GitHub-Problem](https://mcprod.pap-store.acer.com/index.html)_

#### UI-KomponentendateiUploader funktioniert nicht ordnungsgemäß auf 2.4.8-p1/ 2.4-develop

Verbesserter Datei-Upload für benutzerdefinierte UI-Komponente mit Mehrfachauswahl-Funktion zum Hochladen beim Klicken auf den Upload-Bereich.

_ACP2E-4162 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### [On-Premise] Neu erstellte Bestellungen/Firmen/Kunden, die während des Auswahlprozesses automatisch im Bereich „Alle auswählen“ enthalten sind

Es wurde ein Problem behoben, bei dem bei der manuellen Auswahl aller Datensätze auf einer veralteten Admin-Grid-Seite bei der Durchführung von Massenaktionen unbeabsichtigt alle Datensätze gelöscht wurden. Zuvor wechselte das Raster intern automatisch in den Modus „Alle auswählen“, wenn die Anzahl der ausgewählten Elemente mit der Gesamtanzahl übereinstimmte, wodurch Massenaktionen sich auf alle Datensätze und nicht nur auf die explizit ausgewählten auswirkten.

_ACP2E-4202 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6e134409)_

#### Lösung von ACP2E-3362 funktioniert langsam auf MariaDB 10.6

Verbesserte Leistung der Frontend-Suchseite bei einer großen Anzahl historischer Suchanfragen.

_ACP2E-4225 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ab891304)_

#### Datumsfilter funktioniert nicht gemäß der Speicherzeitzone im Raster für Gutschriften

Vor der Korrektur haben Filterlisten nach Datumsattributen fehlende Elemente verursacht, da Zeitzonenunterschiede zwischen dem ausgewählten Datum und dem gespeicherten Datum bestehen. Jetzt, nachdem die Filter für das Korrekturdatum ordnungsgemäß angewendet wurden.

_ACP2E-4239 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Das Dialogfeld „Datei-Uploader“ wird zweimal geöffnet, wenn PageBuilder installiert ist

Vor der Schaltfläche Benutzerdefinierte Komponente hochladen korrigieren trat ein zweimaliger Trigger auf. Nach der Fehlerbehebung funktioniert die Schaltfläche Hochladen erwartungsgemäß.

_ACP2E-4241 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Validierungsfehler bei gelöschten Kundenattributen beim Ändern von Kundendaten.

Vor der Fehlerbehebung schlug das Speichern der Kunden- und Kundenadresse fehl, wenn mehrere gelöschte Attributoptionen enthalten waren. Nach der Behebung können beide erfolgreich gespeichert werden, selbst wenn mehrere Attributoptionen noch vorhanden sind.

_ACP2E-4281 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### JS-Warnung im Admin-Dashboard: „Es wurde erwartet, dass der Lader gestartet wird, aber es wurde kein Lader im DOM gefunden“

Fehlerkorrektur - In der Browser-Konsole wird jetzt keine JavaScript-Warnung mehr angezeigt, wenn Diagramme für das Admin-Dashboard aktiviert sind. Bislang wurde beim Zugriff auf das Admin-Dashboard mit aktivierten Diagrammen durch eine veraltete Debugging-Prüfung fälschlicherweise die Warnung „Es wurde erwartet, dass das Ladeprogramm gestartet wird, aber es wurde kein Lader im DOM gefunden“ ausgegeben, obwohl die Funktion ordnungsgemäß funktionierte.

_ACP2E-4336 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2687b487)_

#### [CLOUD]-Konfiguration mit Abhängigkeitskonfiguration, die bearbeitet werden kann, wenn die standardmäßige Konfiguration in Store aktiviert ist

Es wurde ein Problem behoben, bei dem Systemkonfigurationsfelder nach dem Laden der Seite aktiviert werden konnten, obwohl „Standard/Website verwenden“ aktiviert war.

_ACP2E-4337 - [GitHub-Problem](https://mcstaging.pap-store.acer.com) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

#### Diagramm mit Admin-Dashboard-Reihenfolge wird in die endgültige Größe animiert

Das Bestelldiagramm des Admin-Dashboards wird jetzt sofort angezeigt, ohne dass eine unnötige Größenanpassung erforderlich ist.

_ACP2E-4398 - [GitHub-Problem](https://github.com/magento/magento2/issues/38860) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Page Builder kann Inhalte in der mobilen Ansicht aufgrund eines JS-Fehlers nicht speichern (TypeError: Eigenschaften von nicht definierten Inhalten können nicht gelesen werden)

Es wurde ein Problem behoben, das das Speichern von Seiten in Page Builder beim Hinzufügen von Bannern in der mobilen Ansicht verhinderte.

_ACP2E-4399 - [GitHub-Problem](https://github.com/magento/magento2/issues/38565) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### Admin-Benutzeroberfläche, B2B

#### B2B-Anmeldung als Kunden-Header hat weiterhin das Magento-Branding

Zuvor wurde in der Kopfzeile der Storefront „You are now connected as &lt;customer name> on &lt;store name>&quot; (Sie sind jetzt als &lt;customer name> verbunden) mit Magento-Branding angezeigt. Was jetzt behoben ist und die Kopfzeile mit ADOBE-Branding angezeigt wird.

_AC-14361 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fadcfa8b)_

### Admin-Benutzeroberfläche, Katalog

#### Das Speichern des Produkts schlägt fehl, wenn die Katalogregel aktiv und der Echtzeitmodus aktiviert ist

Es wurde ein Problem behoben, bei dem die Indizierung von Katalogregeln während Produktspeichervorgängen mit einem DDL-Transaktionsfehler fehlschlagen konnte, indem die Indizierung von Katalogregeln von der Produkttransaktion entkoppelt wurde.

_ACP2E-4378 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Admin-Benutzeroberfläche, Inhalt

#### Ausnahme „Ausgabedarstellung kann für Medien-Asset-Pfade nicht erstellt werden“ beim Einfügen des Bildes

Nach dem Entfernen der Werte für Maximale Breite und Maximale Höhe der Konfiguration der Bildoptimierung für die Mediensammlung tritt der Fehler während des Bildoptimierungsprozesses nicht mehr auf.

_ACP2E-3781 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

### Admin-Benutzeroberfläche, Reihenfolge

#### Erstellung von Admin-Aufträgen: Sitzungsgrößenüberlauf beim Hinzufügen von mehr als 20 Produkten (Sitzungsgröße überschreitet das Limit von 256 KB)

Es wurde ein Sitzungsgrößenüberlauf bei der Erstellung von Administratoraufträgen behoben, indem verhindert wurde, dass große HTML-Antworten für JSON-Anfragen in der Sitzung gespeichert wurden. So wurde sichergestellt, dass das Hinzufügen von Massenprodukten reibungslos funktioniert, ohne den Administrator abzumelden.

_AC-15893_

### Admin-Benutzeroberfläche, Sicherheit

#### Unzureichende Kennwortverwaltung

Der Administrator kann nicht mit demselben Kennwort gespeichert werden. Zuvor wurde sie erfolgreich ohne ordnungsgemäße Validierung gespeichert.

_ACP2E-3657 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

### Admin-Benutzeroberfläche, Steuer

#### Fehler in der Steuersatz-Admin-Benutzeroberfläche

Dieses Ticket hat ein Problem in der Admin-Benutzeroberfläche für Steuersätze behoben, bei dem beim Wechsel des Landes (z. B. von USA → Großbritannien) weiterhin der zuvor ausgewählte US-Bundesstaat angezeigt wurde, was Benutzer irregeführt hat.
In 2.4.9-alpha3 wird das Bundesland nun auf * zurückgesetzt, wenn das ausgewählte Land keine Bundesländer hat.

_AC-8440 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analytics/Reporting

#### [Problem] Die scp-Zulassungsliste für Analytics wurde hinzugefügt, wenn Sie nur Google Analytics verwenden

Dieser PR fügt dem Google Analytics-Modul eine CSP-Whitelist hinzu, sodass es unabhängig ohne Google Adwords-Abhängigkeit funktionieren kann. Google Analytics funktioniert jetzt korrekt, auch wenn das Google Adwords-Modul deaktiviert ist.

_AC-16311 - [GitHub-Problem](https://github.com/magento/magento2/issues/40051) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40032)_

#### Doppelte Dateikopfzeilen in CSV-Dateien von erweiterten Berichten, die leere Berichte verursachen

Nach der Korrektur enthalten Berichte, die für die erweiterte Berichtsfunktion generiert werden, keine doppelten Kopfzeilen mehr, wenn die Zeilenanzahl die Batch-Größe überschreitet.

_ACP2E-4187 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Bericht zu Transaktionsabbrüchen enthält ungültige Zeichen

Der Bericht zu Transaktionsabbrüchen, der als CSV-Datei exportiert wurde, enthält jetzt korrekt gerenderte Zeichen für Währungssymbole wie Indische Rupie, wenn er in MS Excel geöffnet wird.

_ACP2E-4288 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Update für MDVA-19640 zur Kompatibilität mit 2.4.8

Durch die Fehlerbehebung werden die Cron-Auftragsaufgaben für die Analyse von der Standardgruppe in die Analytics-Gruppe verschoben

_ACP2E-4309 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### Umsatz wird nicht in Bestellungen/Rechnungsberichten in Admin für kanadische Website/Währung angezeigt

In einigen der auftragsbezogenen Berichte wurden keine Speicherwährungskurse angewendet. Nach der Fehlerbehebung werden die konfigurierten Speicherraten in Berichten ordnungsgemäß angewendet.

_ACP2E-4361 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### Die Überprüfung des Unternehmensfelds schlägt für den Gast-Checkout fehl

Durch den Gast-Checkout wird das Firmenfeld jetzt korrekt validiert.
Zuvor schlug der Gast-Checkout bei der Anforderung des Firmenattributs mit dem Fehler fehl: „Firma ist ein erforderlicher Wert“, auch wenn das Feld ausgefüllt war.
14987

_AC-14987 - [GitHub-Problem](https://github.com/magento/magento2/issues/40011) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### REST API products-render-info gibt falschen Endpreis für angemeldeten Kunden zurück

Das Ticket hat eine Fehlerbehebung für REST API-Produkte - Render-Info geben einen falschen Endpreis für angemeldete Kunden zurück

_AC-5979 - [GitHub-Problem](https://github.com/magento/magento2/issues/35757)_

### B2B, Warenkorb und Checkout

#### Keine solche Entität mit cartId = X-Fehler wird in der Storefront angezeigt, wenn sich der B2B-Firmenbenutzer über die Admin-Funktion „Als Kunde anmelden“ anmeldet

Jetzt ist der Fehler „Keine solche Entität mit cartId = X“ nach erfolgreicher Anmeldung über das Admin-Backend bei Verwendung der Funktion „Als Kunde anmelden“ nicht mehr sichtbar.

_ACP2E-3994 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Fehlende Rechnungsadresse verhindert die Auftragserteilung mit der Versandart „Versand im Geschäft“

Es wurde ein Problem behoben, bei dem die Rechnungsadresse beim Checkout nicht automatisch ausgefüllt wurde, wenn Die Abholung im Geschäft als Versandmethode ausgewählt wurde. Ohne Rechnungsadresse konnte der Checkout nicht abgeschlossen werden.

_ACP2E-4030 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/42d23211)_

### Warenkorb und Checkout

#### Magento 2.4.7 Update (Mini) Warenkorb Keine Dezimalmenge zulässig

Jetzt verarbeitet Magento korrekt, wenn wir die Menge mit Dezimalzahlen aus dem Mini-Warenkorb aktualisieren, wenn das Gebietsschema NL (Niederländisch) war

_AC-13238 - [GitHub-Problem](https://github.com/magento/magento2/issues/39236) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39669)_

#### [Problem] Hinzufügen von EventPrefix und EventObject zum Checkout-Vereinbarungsmodell

Das System enthält jetzt EventPrefix und EventObject für das Checkout-Vereinbarungsmodell, sodass Ereignisse mit einem Ereignispräfix ausgelöst werden können. Diese Verbesserung bietet Entwicklern mehr Flexibilität bei der Arbeit mit Checkout-Vereinbarungsereignissen. Zuvor unterstützte das Modell der Kaufbestätigung nicht EventPrefix und EventObject, was die Möglichkeit einschränkte, die Ereignisbehandlung anzupassen.

_AC-13252 - [GitHub-Problem](https://github.com/magento/magento2/issues/32510) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32451)_

#### [Problem] Entwicklererlebnis: Zitat AbstractItem-Code-Stil (SOP-348 von SwiftOtter)

Diese Pull-Anfrage behebt irreführende Methodendeklarationen für abstrakte Item-Methoden.

_AC-13334 - [GitHub-Problem](https://github.com/magento/magento2/issues/39340)_

#### Validierungen der Frontend-Menge für gruppierte Produkte fehlen

Das System funktioniert jetzt einwandfrei und zeigt einen Validierungsfehler an, wenn wir versuchen, negative und maximale Mengen hinzuzufügen

_AC-13524 - [GitHub-Problem](https://github.com/magento/magento2/issues/39479) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39480)_

#### [Problem] Aktualisieren von subtotal.phtml

Das System aktualisiert die Datei „subtotal.phtml“ mit dem richtigen Abstand

_AC-13907 - [GitHub-Problem](https://github.com/magento/magento2/issues/39619) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39612)_

#### Bestellung kann nicht beim Gast aufgegeben werden

Adobe Commerce ermöglicht es jetzt Gastkäufern, erfolgreich Bestellungen aufzugeben, wenn das Feld „Zweiter Vorname“ wie in der Admin-Liste erforderlich konfiguriert ist. Zuvor wurde in Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4) durch das Konfigurieren des zweiten Vornamens nach Bedarf und das Auschecken als Gast die Bestellplatzierung verhindert, selbst wenn ein zweiter Vorname angegeben wurde, was den Abschluss des Auscheckens blockierte. 14241

_AC-14241 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/27217d0e)_

#### [GraphQL] kann für das Feld „SelectedCustomizableOption.label“, das keine NULL-Werte zulässt, nicht null zurückgeben

Das System gibt jetzt keinen internen Server-Fehler mit der Meldung aus, wenn die ausgewählte Option nicht mehr vorhanden ist

_AC-14256 - [GitHub-Problem](https://github.com/magento/magento2/issues/39729) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39888)_

#### GraphQL addWishlistItemsToCart kann die Anzahl für vorhandene Warenkorbartikel nicht aktualisieren, wenn ein Wunschlistenelement ungültig ist (Magento 2.4.7-p3)

Es wurde ein Problem behoben, bei dem die GraphQL addWishlistItemsToCart-Mutation die Verarbeitung stoppte, wenn ein ungültiges konfigurierbares Produkt gefunden wurde. Nach der Fehlerbehebung werden gültige Artikel der Wunschliste zum Warenkorb hinzugefügt und die Mengen aktualisiert, während ungültige Artikel mit entsprechenden Fehlern übersprungen werden.

_AC-14464 - [GitHub-Problem](https://github.com/magento/magento2/issues/39820) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] Es können keine Bestellungen aufgegeben werden, bei denen die Stadt Ziffern 0-9, ein kaufmännisches Und-Zeichen, einen Punkt oder Klammern im Stadtnamen hat

Es wurde ein Problem behoben, bei dem der Checkout für Städtenamen mit Sonderzeichen wie , &amp; oder Klammern fehlschlug.
Jetzt werden Bestellungen mit solchen Städtenamen erfolgreich ohne Validierungsfehler platziert.

_AC-14495 - [GitHub-Problem](https://github.com/magento/magento2/issues/39854) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Gastpräfix nicht in Anführungsadresse 2.4.8 gespeichert

Das Präfix des Gastkunden (Herr/Frau) wird jetzt während des Checkouts gespeichert.
Zuvor gingen die von den Gastkunden ausgewählten Anrede vor Erreichen der endgültigen Bestellung verloren, während alle anderen Adressfelder korrekt übertragen wurden.
14705

_AC-14705 - [GitHub-Problem](https://github.com/magento/magento2/issues/39915) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### Verkaufsregel-Unterauswahl mit Mengenbedingung kann nicht angewendet werden

Es wurde ein Problem behoben, bei dem Regeln zum Warenkorbpreis mit Bedingungen zur Produktunterauswahl beim Checkout nicht angewendet wurden.
Jetzt werden Rabatte gemäß den konfigurierten Regeln erfolgreich angewendet.

_AC-14884 - [GitHub-Problem](https://github.com/magento/magento2/issues/39965) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fe72c407)_

#### [Problem] Leerzeichen im Klassenattribut entfernen

Das System entfernt jetzt einen zusätzlichen Platz im Klassenattribut

_AC-14939 - [GitHub-Problem](https://github.com/magento/magento2/issues/39977) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39970)_

#### GraphQL - Zusammenführungs-Warenkorb funktioniert nicht richtig, wenn Rückstand aktiviert ist

Es wurde ein Problem behoben, bei dem Gast-Warenkorb-Artikel während der Warenkorbzusammenführung über GraphQL nicht mit dem Warenkorb zusammengeführt wurden.
Jetzt spiegelt der Warenkorb des Kunden die kombinierte Menge sowohl aus dem Gast- als auch aus dem Warenkorb des Kunden korrekt wider.

_AC-15148 - [GitHub-Problem](https://github.com/magento/magento2/issues/40064) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integration] [Checkout] Abhängigkeitsrichtlinien in der E-Mail-Vorlage für fehlgeschlagene Zahlungen aktualisiert

Fehlgeschlagene E-Mail-Vorlage für Zahlung wurde aktualisiert, um Abhängigkeitsanweisungen korrekt zu verarbeiten.
Fehlerbehebung stellt sicher, dass Lieferadresse und Versandmethode bei Bedarf korrekt angezeigt werden.
Zuvor fehlten diese Felder in E-Mails mit fehlgeschlagenen Zahlungen.

_AC-15363 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Warenkorb] Die Warenkorbseite wird nicht geladen, wenn die feste Produktsteuer aktiviert ist

Es wurde ein Problem behoben, bei dem die Warenkorbseite unendlich geladen wurde, wenn die feste Produktsteuer (FPT) aktiviert war. Das Problem wurde durch falsche Zwischensummenberechnungen verursacht, da die Steuer in dasselbe HTML-Element wie der Artikelpreis einbezogen wurde, was zu einer Diskrepanz zwischen mittleren und zusammenfassenden Zwischensummen führte. Nach der Fehlerbehebung wird der Warenkorb korrekt geladen und zeigt genaue Gesamtwerte an.

_AC-16096 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Warenkorb-Preisregel Aktion der Bedingung „Preis im Warenkorb“, wird angewendet, wenn dies nicht der Fall sein sollte

Es wurde ein Problem behoben, bei dem Regeln zum Warenkorbpreis mit der Bedingung „Preis im Warenkorb kleiner als“ fälschlicherweise auf nicht förderfähige Produkte angewendet wurden.
Jetzt werden Coupons ordnungsgemäß validiert und zurückgewiesen, wenn die Preise der Warenkorbartikel die konfigurierten Regelbedingungen nicht erfüllen.

_AC-6997 - [GitHub-Problem](https://github.com/magento/magento2/issues/36433) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### [Problem] Festlegen des Preises für einen Angebotselement anstelle des Basispreises

Das System verarbeitet den Preis des Angebotselements korrekt, der auf den base_price statt auf den Preis gesetzt wird, wenn mehrere Währungen auf einer Website im Frontend vorhanden sind

_AC-9985 - [GitHub-Problem](https://github.com/magento/magento2/issues/38094) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36878)_

#### Abgelaufene persistente Anführungszeichen werden nicht durch einen Cron-Vorgang bereinigt sales_clean_quotes

Die abgelaufenen persistenten Anführungszeichen werden jetzt gelöscht, wenn der Cron-Auftrag „persistent_clear_expiration“ ausgeführt wird. Zuvor wurden die abgelaufenen persistenten Anführungszeichen nicht durch einen anderen Cron-Auftrag gelöscht.

_ACP2E-3493 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/11be3dff)_

#### Fehler „Irgendetwas ist schiefgelaufen“ beim Checkout für ein inaktives Unternehmen

Vor der Behebung wurde die Abmeldeaktion auf der Warenkorbseite nicht ordnungsgemäß abgeschlossen, wenn die angemeldete Benutzerfirma nicht mehr aktiviert war. Wenn die Firma nicht mehr verfügbar ist, wird die Abmeldung ordnungsgemäß durchgeführt.

_ACP2E-3541 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Die Adressenauswahl wird beim Auschecken mit mehreren Adressen nicht gespeichert

Vor der Fehlerbehebung beim Abbrechen der Option für den Mehrfachversand war die Adresse beim Zurücksetzen auf den Mehrfachversand nicht vorausgewählt. Jetzt wird die Standardadresse durch eine der Optionen ersetzt, die im Multi-Shipping-Bildschirm ausgewählt wurden.

_ACP2E-3646 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6ea61121)_

#### [Cloud] Letzte Bestellungen werden nicht in der anderen Shop-Ansicht angezeigt, wenn die Bestellungen in einer Shop-Ansicht erstellt wurden

Es wurde ein Problem behoben, bei dem auf der Seite „Mein Konto“ keine aktuellen Bestellungen aus anderen Store-Ansichten innerhalb desselben Stores angezeigt wurden. Die Logik zum Abrufen von Bestellungen wurde aktualisiert, um eine konsistente Sichtbarkeit der Bestellung über alle Store-Ansichten hinweg sicherzustellen. Dies entspricht dem Verhalten der Seite „Meine Bestellungen“.

_ACP2E-3807 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Anzeige der Menge als  0 im Admin-Warenkorbabschnitt des Kunden beim Hinzufügen von BUNDLE-Produkten  

Im Abschnitt Warenkorb in Kundenaktivitäten wird jetzt die richtige Menge angezeigt. Zuvor wurde die Menge als 0 angezeigt.

_ACP2E-3872 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [Cloud] Kostenloser Versandrabatt wurde nicht korrekt entfernt, wenn der Warenkorb die Anforderungen nicht mehr erfüllt

Die Zwischensumme (ohne Die Preisregel für den Warenkorb enthält jetzt Rabatte aus vorherigen Regeln.

_ACP2E-3973 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Doppelte Bestellung für denselben Kunden in Multishipping gefunden

Gleichzeitige Anfragen, Bestellungen mit mehreren Versandadressen zu tätigen, führen nicht mehr zu doppelten Bestellungen für denselben Kunden

_ACP2E-4117 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Die Benachrichtigung „Bestandsbeschränkung überschritten“ wird zweimal angezeigt, wenn der Schwellenwert für nicht vorrätige Artikel erreicht wird

Fehlerkorrektur - Bei Warenkorbaktualisierungen werden jetzt keine doppelten Fehlerbanner mehr angezeigt. Zuvor wurde nach einem AJAX-Validierungsfehler beim Absenden des Formulars dieselbe Nachricht vom Backend erneut hinzugefügt, sodass Käufer zwei identische Warnhinweise sehen würden. Jetzt überspringen wir das Hinzufügen der zusätzlichen Backend-Nachricht, wodurch die Warenkorbseite in einem einzigen leeren Fehlerbanner verbleibt.

_ACP2E-4192 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e885088b)_

#### Für Rechnungsinformationen funktioniert die Server-seitige Validierung nicht mit der Versandinformationen-REST-API

Die Validierung von Kundenadressdaten wurde verbessert, um zwischen REST und GraphQL für den Checkout konsistenter zu sein.

_ACP2E-4223 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] Problem mit Produktpreisen im Bundle auf der Warenkorbseite

Fehlerkorrektur - Der Produktpreis des Pakets wird jetzt auf der Warenkorbseite für Stores mit mehreren Währungen behoben.

_ACP2E-4245 - [GitHub-Problem](https://www.techbuyer.com/) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cbca0396)_

#### Probleme mit dem Warenkorbspeicherbereich verwalten

Jetzt werden Warenkorbfehler dem Admin-Benutzer beim Verwalten des Warenkorbs für einen Kunden angezeigt, der einer nicht standardmäßigen Website zugewiesen ist. Zuvor wurden keine Fehler angezeigt.

_ACP2E-4348 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

#### Coupon times_USED wird nach teilweiser Stornierung der Rechnung zurückgesetzt

Die Anzahl der verwendeten Coupons wird jetzt korrekt aktualisiert, wenn eine Bestellung teilweise storniert wird.

_ACP2E-4365 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

### Warenkorb und Checkout, GraphQL

#### Fehler bei der Zuordnung der Nachricht zum Fehlercode bei der Bestellung über GraphQL

GraphQL-Aufrufe zum Aufgeben einer Bestellung für einen nicht vorhandenen oder inaktiven Warenkorb geben jetzt korrekt die Fehler-Codes „CART_NOT_ACTIVE“ oder „CART_NOT_FOUND“ in allen Store-Ansichten zurück. Damit wird ein Problem behoben, bei dem übersetzte Fehlermeldungen zuvor zu einem „UNDEFINIERTER“ Code geführt haben.

_ACP2E-3942 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQL] Warenkorbabfrage-Artikel-Rabattproblem bei virtuellen Angeboten

Es wurde ein Problem behoben, bei dem die GraphQL-Warenkorbabfrage einen falschen Rabattbetrag für virtuelle Angebote zurückgab. Zuvor wurden Rabatte fälschlicherweise auf bestimmte virtuelle Produkte angewendet, die nicht förderfähig waren.

_ACP2E-4248 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 erstellt ein weiteres Problem

Wenn eine GraphQL-Anfrage für ein Element mit unzureichender Menge durchgeführt wurde, wurde eine korrekte Fehlermeldung mit einem Fehlercode zurückgegeben. Wenn die angeforderte Menge verfügbar ist, wurde die Warenkorbaktualisierung erfolgreich durchgeführt.

_ACP2E-4404 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1c547060)_

### Warenkorb und Checkout, GraphQL, Inventar / MSI

#### Das Attribut is_available in CartItemInterface gibt „false“ zurück, selbst wenn der verkaufbare Bestand hoch ist.

Das Attribut is_available gibt „true“ zurück, wenn das verkäufliche Lager hoch ist. Zuvor wird immer „false“ zurückgegeben.

_ACP2E-3885 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Warenkorb und Checkout, Inventar / MSI

#### 414 Fehler beim Endpunkt „Nach Abholort suchen“ mit großen Warenkorbgrößen

Die Auswahl eines Shops während des Checkouts mithilfe von „Pick in Store“ schlägt aufgrund langer URLs nicht mehr fehl, wenn sich viele Produkte im Warenkorb befinden.
Zuvor wurde ein 414-Fehler ausgelöst, der durch zu lange URLs verursacht wurde, die während der Store-Auswahl generiert wurden, was Kunden daran hinderte, den Checkout abzuschließen.

_ACP2E-4266 - [GitHub-Problem](https://mcstaging.casamyers.com.mx/) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/ae1f272f)_

### Warenkorb und Checkout, Promotion

#### Das Guthaben auf der Geschenkkarte wird nicht durch den Umfang der Website eingeschränkt

Geschenkgutscheinprüfung mit dem zugewiesenen Website-Umfang eingeschränkt.

_ACP2E-4379 - [GitHub-Problem](https://www.panini.it)_

### Warenkorb und Checkout, Sicherheit

#### [CLOUD] Abrufen der 404-Datei für JS auf der Checkout-Seite beim ersten Versuch nach der Implementierung des sri-Patches

Vor der Fehlerbehebung wurden Mixins nicht in den Warenkorb geladen und zur Kasse gebeten, wenn Minimieren und Bündeln aktiviert waren. Nach der Fehlerbehebung sollten alle Mixins erwartungsgemäß geladen werden.

_ACP2E-4128 - [GitHub-Problem](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Warenkorb und Checkout, Versand

#### [Mainline] Die Warenkorb-Preisregel respektiert nicht Multishipping

Vor der Implementierung dieser Korrektur galt die Warenkorb-Preisregel für Produkte mit mehreren Versandarten nicht korrekt, wenn Unterauswahlbedingungen angewendet wurden und der kostenlose Versand aktiviert war. Da die Korrektur jedoch angewendet wurde, funktioniert die Warenkorb-Preisregel für Warenkörbe mit mehreren Versand jetzt wie beabsichtigt.

_ACP2E-3666 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog

#### Cache-FPC für dieselbe Seite mit derselben Abfrage duplizieren

Das System identifiziert und verwendet nun denselben Vollseiten-Cache (FPC) für Seiten mit denselben Abfrageparametern, unabhängig von ihrer Reihenfolge oder nachfolgenden Zeichen. Dadurch wird verhindert, dass die Größe des Seiten-Cache-Ordners unnötigerweise erhöht wird. Zuvor erstellte das System eine andere FPC-Kennung für dieselbe Seite, wenn die Reihenfolge der Abfrageparameter unterschiedlich war oder nachfolgende Zeichen vorhanden waren, was zu einer Erhöhung der Größe des Seiten-Cache-Ordners führte.

_AC-10722 - [GitHub-Problem](https://github.com/magento/magento2/issues/38269) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38270)_

#### Fehlende Indizierung der erforderlichen Spalten in der Tabelle CATALOG_PRODUCT_ENTITY_INT

Die fehlende Indizierung der erforderlichen Spalten in der Tabelle catalog_product_entity_int wurde hinzugefügt.

_AC-10844 - [GitHub-Problem](https://github.com/magento/magento2/issues/38315) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38316)_

#### Umfang des Fehlers in der Katalog-URL-Ressource (_getCategories)

Diese PR fügt einen Fallback zum Standardbereich hinzu, wenn für den Store-Bereich in der Kategorie-URL-Ressource kein Wert definiert ist.

_AC-11011 - [GitHub-Problem](https://github.com/magento/magento2/issues/38393) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38394)_

#### [Problem] Überprüfen, ob OpenGraph den Preis anzeigen kann

Das System funktioniert einwandfrei, wenn wir ein Plugin verwenden, das den Preis ausblendet und mit dieser Änderung ist der Preis nicht im OG-Tag sichtbar.

_AC-11635 - [GitHub-Problem](https://github.com/magento/magento2/issues/38512) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38510)_

#### Rundungsproblem bei Preisen beim Hinzufügen von Steuern zu den angezeigten Preisen

Das System behebt jetzt ein Rundungsproblem bei Preisen, wenn Steuern zur Preisanzeige hinzugefügt werden

_AC-11725 - [GitHub-Problem](https://github.com/magento/magento2/issues/18025) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35730)_

#### [Problem] Zulassen von Bedingungen für benutzerdefinierte Katalogregeln

Es wurde ein Problem behoben, das aufgrund einer strikten Typüberprüfung die Verwendung benutzerdefinierter Katalogregelbedingungen verhinderte. Der Fix ersetzt die Klassengleichheitsprüfung durch instanceOf, sodass benutzerdefinierte Bedingungsklassen ordnungsgemäß funktionieren und eine erfolgreiche Regelvalidierung und -indizierung ermöglicht wird.

_AC-13338 - [GitHub-Problem](https://github.com/magento/magento2/issues/39339) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Konfigurierbare Optionen für Produktverluste beim Hinzufügen zur Wunschliste

Fehlerkorrektur - Konfigurierbare Produktoptionen gehen jetzt verloren, nachdem das Produkt zur Wunschliste hinzugefügt wurde. Jetzt werden die ausgewählten Optionen beibehalten, sodass das Produkt problemlos zum Warenkorb hinzugefügt werden kann, ohne dass die Benutzer aufgefordert werden, die Optionen erneut auszuwählen.

_AC-13373 - [GitHub-Problem](https://github.com/magento/magento2/issues/39363) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### Der Sonderpreis wird für das untergeordnete Produkt des konfigurierbaren Produkts (einfaches Produkt) nicht korrekt angezeigt.

Es wurde ein Problem behoben, bei dem der Sonderpreis für das untergeordnete (einfache) Produkt eines konfigurierbaren Produkts auf der Produktlistenseite nicht korrekt angezeigt wurde, wenn „In der Produktliste verwendet“ auf „Nein“ gesetzt war. Jetzt wird der Sonderpreis richtig zusammen mit dem regulären Preis angezeigt, um eine konsistente Preisanzeige über alle Produktarten hinweg sicherzustellen.

_AC-13594 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### [Bug] REST-API: Die Aktualisierung von Sonderpreisen legt keine Werte für alle Store-Ansichten fest

Die REST-API aktualisiert jetzt die Sonderpreise für alle Store-Ansichten in einer Website.
Zuvor wirkte sich die Aktualisierung von Sonderpreisen über die REST-API nur auf die angegebene Store-Ansicht aus, nicht auf alle Store-Ansichten in der Website.
13671

_AC-13671 - [GitHub-Problem](https://github.com/magento/magento2/issues/39521) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Probleme mit dem Preisbereich und config.php

In Magento 2.4.2 wird durch die Änderung des Preisbereichs über config.php der Wert is_global in catalog_eav_attribute für das Preisattribut nicht ordnungsgemäß aktualisiert.
Produktpreise bleiben daher global und können nicht pro Website gespeichert werden, auch wenn der Preisbereich auf Website eingestellt ist.
Um dieses Problem zu umgehen, muss die Spalte „is_global“ in der Datenbank manuell aktualisiert werden, was für Produktionsumgebungen nicht ideal ist.
Dieses Verhalten entspricht dem standardmäßigen Design von Magento, bei dem der Preisbereich entweder „global“ oder „Website“ ist, aber nicht pro Shop-Ansicht.

_AC-13857 - [GitHub-Problem](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP-Fehler nicht bemerkt

Der Name einer Schleifenvariablen wurde geändert, um die „_cache_instance_product_ids“-Daten zum angegebenen Produkt korrekt hinzuzufügen, damit sie bei nachfolgenden Aufrufen verwendet werden können.

_AC-14159 - [GitHub-Problem](https://github.com/magento/magento2/issues/39641) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39642)_

#### Die elastische Suche beeinträchtigt die standardmäßige Sortierreihenfolge der Produkte (von neu zuerst nach alt zuerst)

Das System sortiert nun die neuesten Produkte in der Datenbank (das mit der höchsten entity_id) werden zuerst angezeigt

_AC-14411 - [GitHub-Problem](https://github.com/magento/magento2/issues/31043) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36900)_

#### Die Seite nach dem Umschalten des Speichers stammt aus dem Cache (Speicherumschalter funktioniert nicht) in 2.4.8

Es wurde ein Problem behoben, bei dem das Wechseln zwischen Store-Ansichten und der Storefront-Kopfzeile erst funktionierte, wenn der Cache manuell gelöscht wurde.
Jetzt funktioniert der Wechsel der Speicheransicht korrekt, ohne dass der Cache bereinigt werden muss.

_AC-14426 - [GitHub-Problem](https://github.com/magento/magento2/issues/39806)_

#### Ignorierte .less-Stile mit min-width: (@screen__l)

Es wurde ein Problem behoben, bei dem nur drei Produkte pro Zeile auf Kategorieseiten angezeigt wurden.
Jetzt werden wie erwartet vier Produkte pro Zeile angezeigt.

_AC-14463 - [GitHub-Problem](https://github.com/magento/magento2/issues/39817) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Wunschzettel-Anzahl wird nicht auf der Homepage/anderen Seiten angezeigt, außer Wunschzettel-Seite im Kundenmenü

Es wurde ein Problem behoben, bei dem die Anzahl der Wunschlisten als leere Klammern auf Nicht-Wunschlisten-Seiten angezeigt wurde.
Jetzt wird neben „Meine Wunschliste“ auf allen Seiten die richtige Wunschlistenanzahl angezeigt.

_AC-14607 - [GitHub-Problem](https://github.com/magento/magento2/issues/39892) - [GitHub-Code-](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before -Beobachter gibt bei Verwendung der REST-API ohne Werte auf Speicherebene einen datumsbezogenen Fehler aus (getFinalPrice()-Problem)

Diese PR passt die Verarbeitung von SpecialFromDate an, um eine korrekte Formatierung sicherzustellen, wenn das Datum als DateTimeInterface-Instanz bereitgestellt wird. Dadurch wird verhindert, dass bei der Ausführung von getFinalPrice() in bestimmten Szenarien Fehler auftreten.

_AC-14847 - [GitHub-Problem](https://github.com/magento/magento2/issues/39959) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40003)_

#### DRINGEND - Produkt kann nicht zum Bundle hinzugefügt werden, wenn das hinzuzufügende Produkt anpassbare Optionen hat

Es wurde ein Problem behoben, bei dem Produkte mit anpassbaren Optionen nicht zu Paketprodukten hinzugefügt werden konnten.
Zuvor wurden solche Produkte bei der Bundle-Erstellung von der Liste „Produkte zur Option hinzufügen“ ausgeschlossen.
Jetzt können Produkte mit anpassbaren Optionen zu Bundles hinzugefügt werden, ohne ihre benutzerdefinierten Optionen einzubeziehen, was eine ordnungsgemäße Bestandsverwaltung ermöglicht.
Dies ermöglicht die Bundle-Erstellung, ohne dass Produkte dupliziert werden oder sich dies auf die Lagerbestände auswirkt.

_AC-14958 - [GitHub-Problem](https://github.com/magento/magento2/issues/39993)_

#### Negative `?p=` Abfragezeichenfolge verursacht Elasticsearch-Ausnahme

Das System adressiert nun den negativen ?p=-Wert in der Kategorienpaginierung, was derzeit zu einer Ausnahme führt und als gültige Anfrage betrachtet wird

_AC-15191 - [GitHub-Problem](https://github.com/magento/magento2/issues/40079) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40080)_

#### Preisschild „So niedrig wie“ wird für konfigurierbare Produkte mit einer Option angezeigt

Es wurde ein Problem behoben, bei dem konfigurierbare Produkte den Preis mit einer falschen „So niedrig wie“-Kennzeichnung auf PDP/PLP anzeigten.
Jetzt zeigt das Produkt den richtigen Preis (500 $) ohne irreführende Etiketten.

_AC-15237 - [GitHub-Problem](https://github.com/magento/magento2/issues/40104) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Falsche Methode für die Schaltfläche „Zum Vergleich hinzufügen“ aufgerufen

Korrektur der in \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect() verwendeten Methode.
Zuvor wurde getAddToCartButton() fälschlicherweise anstelle von getAddToCompareButton() aufgerufen.
Durch diese Änderung wird das richtige Verhalten für das Rendern der Schaltfläche „Zum Vergleich hinzufügen“ in den Produktlisten sichergestellt.
Es werden keine funktionalen Verhaltensänderungen eingeführt; die Aktualisierung verbessert das Erlebnis für Entwickler und die Code-Korrektheit.

_AC-15323 - [GitHub-Problem](https://github.com/magento/magento2/issues/39754) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Falscher Produktpreis wird im Warenkorb mit verschiedenen Währungen in verschiedenen Shop-Ansichten angezeigt

Fehlerkorrektur - Im Warenkorb werden jetzt die falschen Produktpreise angezeigt, wenn in verschiedenen Storeansichten unterschiedliche Währungen verwendet werden. Nach der Fehlerbehebung zeigt der Warenkorb jetzt den richtigen umgerechneten Preis basierend auf der konfigurierten Währung an, um die Konsistenz zwischen der Produktseite und dem Warenkorb sicherzustellen.

_AC-15385 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Falsche „So niedrig wie“-Preisanzeige für konfigurierbare Produkte bei aktiviertem FTP

Bestätigt, dass der falsche „So niedrig wie“ Preis für konfigurierbare Produkte, wenn FPT aktiviert wurde, durch die doppelte Anwendung von Steuern verursacht wurde; die Korrektur stellt sicher, dass die endgültige Preisberechnung die Steuerkonfiguration berücksichtigt und jetzt den richtigen Preis anzeigt.

_AC-15718 - [GitHub-Problem](https://github.com/magento/magento2/issues/40171) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a06a4a57)_

#### Die Zeitkomplexität von _loadAttributes in Eav\Model\Entity\Collection\AbstractCollection nimmt mit der Anzahl der Produkte im Warenkorb und den Attributen zu

Dieser PR optimierte _loadAttributes in Eav\Model\Entity\Collection\AbstractCollection, indem er verschachtelte Schleifen durch eine Array-Vereinigung (+) ersetzte und Aufrufe von _setItemAttributeValue reduzierte, wodurch die Leistung bei großen Warenkörben verbessert wurde.

_AC-15833 - [GitHub-Problem](https://github.com/magento/magento2/issues/40216) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40217)_

#### Fehlerkorrektur - Interaktion zwischen Sammlungs-Cache und konfigurierbarer Produktgalerie

Es wurde ein Caching-Problem mit konfigurierbaren Produktkatalogen behoben, indem eine defensive Typprüfung hinzugefügt wurde, um sicherzustellen, dass media_gallery_images immer als Sammlung behandelt wird. Dadurch wurden schwerwiegende Fehler verhindert, die durch beschädigte Cache-Daten verursacht wurden.

_AC-16066 - [GitHub-Problem](https://github.com/magento/magento2/issues/33965) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### Produktseite gibt aufgrund von URL-Neuschreibungen einen Fehler aus

Jetzt wird die Produktseite erfolgreich geladen, wenn URL-Neuschreibungen durchgeführt werden

_AC-2950 - [GitHub-Problem](https://github.com/magento/magento2/issues/35371) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39670)_

#### indexer_update_all_views cron-Fehler mit MAGE_INDEXER_THREADS_COUNT

Es wurde ein Problem für MAGE_INDEXER_THREADS_COUNT > 2 mit dem Kundensegmentindexer behoben

_ACP2E-3538 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Ausnahme beim Hinzufügen der „Bedingungskombination“ in der Widget-Bedingung von Page Builder-Produkten

Das Problem wurde behoben, indem eine Prüfung hinzugefügt wurde, um fehlende oder unvollständige Bedingungen zu überspringen. Zuvor wurden aufgrund der Behandlung unvollständiger Bedingungen im System Fehlerprotokolle generiert.

_ACP2E-3545 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/11be3dff)_

#### Browser stürzt beim Laden des eingestellten Attributs ab

Der Browser stürzt auf der Seite zum Bearbeiten von Attributsätzen nicht mehr ab, wenn mehr als 4K-Produktattribute vorhanden sind

_ACP2E-3633 - [GitHub-Problem](https://github.com/magento/magento2/issues/38810) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [CLOUD] Neuschreibungen der Produkt-URLs für neuen Store: Go-Live-Blocker nicht erstellt

Produkt-URL-Neuschreibungen für neuen Store wurden erfolgreich erstellt.
Zuvor wurde der Vorgang mit einem Speicherverlust oder einer Zeitüberschreitung beendet.

_ACP2E-3669 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Standardwert des Attributs für Optionen funktioniert nicht

Zuvor, als wir den Standardwert eines Produktauswahlattributs geändert haben, wurde es als Array-Element mit den vorherigen Werten angezeigt. Wenn diese Fehlerbehebung angewendet wird und wir einen Produktattributwert aktualisieren, wird er als einzelnes Element in der Tabelle „eav_attribute“ gespeichert.

_ACP2E-3688 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

#### [Mainline] [CLOUD] Das Ändern der Bildgröße verbraucht mehr als 400 GB Festplattenspeicher

Nach der Behebung generiert der mit `catalog:images:resize` Flag verwendete `--skip_hidden_images`-Befehl keine Bild-Caches für Websites, auf denen Bilder nicht vorhanden sind.

_ACP2E-3869 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### Dynamische Bildgenerierung generiert eine große Anzahl von Bildern

Nach der Fehlerbehebung werden Bilder nur für die Websites generiert, denen das Produkt zugewiesen ist.

_ACP2E-3927 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fab20b00)_

#### Bereitgestellte Länder-ID existiert nicht - Irland (IE)

Nach der Fehlerbehebung stehen Postleitzahlen für Irland zur Verfügung, um Abholstandorte zu suchen.

_ACP2E-3932 - [GitHub-Code-](https://github.com/magento/magento2/commit/4ca73607) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### 500-Fehler treten im Frontend auf, da im Layout eine falsche Layout-Struktur zwischengespeichert wird

Es wurde ein Problem behoben, bei dem eine Seite aufgrund einer im Layout zwischengespeicherten falschen Layout-Struktur einen Fehler-Code 500 zurückgab

_ACP2E-4040 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

#### Falscher Bericht zu Produktansichten - niedrigere Anzahl im Vergleich zu allgemeiner Verfügbarkeit

Es wurde ein Fehler behoben, durch den in der Tabelle report_viewed_product_index nicht die richtige Anzahl von Produktseitenansichten angezeigt wurde.

_ACP2E-4045 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6e134409)_

#### Validierungsfehler für das Feld Rabattbetrag der Katalogpreisregel in der geplanten Aktualisierung

Bevor Sie dieses Problem behoben haben, haben Sie bei der Zeitplanaktualisierung für die Katalogpreisregel zuvor Folgendes festgestellt: Wenn der Rabattbetrag nach_festgelegt ist, wurde er aufgrund der Regel für den Validierungs-Nummernbereich nicht ordnungsgemäß validiert. Nachdem diese Fehlerbehebung angewendet wurde, funktioniert die Validierung für die Regel Festpreis-Katalogpreis ordnungsgemäß.

_ACP2E-4054 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Die MwSt.-Validierung schlägt aufgrund des MwSt.-API-Ratenbegrenzers fehl - Trigger: falsch positive Änderung der Kundengruppe

Die Anfragen an das Europa-Validierungstool für die Mehrwertsteuer wurden optimiert, was zu einem geringeren „Ratenbegrenzungsfehler“ führt

_ACP2E-4072 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### Massenlöschung im Kern-Indexer löst Fehler wegen maximaler Größe des Writesets in der Produktion aus

Optimiert die Bereinigung der Katalogregel und des Produktindex, indem zwei Löschstrategien basierend auf dem Datenvolumen implementiert werden.

_ACP2E-4085 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a3b7032)_

#### Produkte werden nach der Deaktivierung als nicht vorrätig angezeigt

Nach der Behebung sind deaktivierte Produkte nicht im Produkt-Widget vorhanden.

_ACP2E-4136 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Fehler mit doppelten Einträgen (temp_category_descendants_%)

Es wurde ein Problem mit doppelten Einträgen während der Erstellung geplanter Aktualisierungen für Umgebungen mit einer hohen Anzahl verschachtelter Kategorien behoben

_ACP2E-4159 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Problem mit nicht übereinstimmender Anzahl von Produkten für verschiedene Stores vergleichen

Produktlistenvergleich funktioniert jetzt nach dem Wechsel zu einer anderen Storeview ordnungsgemäß

_ACP2E-4249 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98f028ab)_

#### Keine Option zur Verwendung von „Standard“ für „Bilder und Videos“ für die Zuweisung von Bildrollen

Die Optionen „Standardwert verwenden“ wurden zum Abschnitt Produktbilder und Videos hinzugefügt und ermöglichen die Vererbung von Einstellungen aus dem Standardbereich.

_ACP2E-4280 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

#### Produkte mit eingeschränkter Kategorie werden nach dem Update der Kundengruppe noch in der Wunschliste gezählt

Vor der Fehlerbehebung wurden Kategorieberechtigungen nicht ordnungsgemäß auf Elemente der Kunden-Wunschliste angewendet. Nach der Fehlerbehebung werden Wunschlistenelemente jetzt ordnungsgemäß im Web und in GraphQL angezeigt und paginiert.

_ACP2E-4294 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### [Cloud] Produktpreisproblem im Bundle auf PDP und PLP

Preis für Bundle Produkt mit regulärem Preis wird korrekt auf PDP/PLP für nicht standardmäßige Währung angezeigt

_ACP2E-4298 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a3b7032)_

#### Kunde kann Bestellung für nicht zugängliches Produkt nach Änderung der Kundengruppe aufgeben

Beim Ändern der Kundengruppe von „Admin“ spiegelten der Frontend-Katalog und der Warenkorb bisher die Änderungen in den Katalogberechtigungen nicht wider. Nach Anwendung dieser Fehlerbehebung ändert sich das Frontend-Angebot jetzt jedoch entsprechend den aktualisierten Katalogberechtigungen, wenn die Kundengruppe von „admin“ geändert wird.

_ACP2E-4300 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Neuindizierung aufgrund hoher Speichernutzung blockiert

Es wurde ein Problem behoben, bei dem der Indexer für Katalogregeln zu viel Speicher verbrauchte und nicht abgeschlossen werden konnte, was zu Instabilität und Fehlern bei ungenügendem Speicher führte.

_ACP2E-4303 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### Der Vorschau-Link für [ geplante Updates von ]CMS leitet zur Wartungsseite weiter

Vorschau des geplanten Updates des Links zur Startseite mit konfigurierbaren Produkten zeigt die Liste der Produkte korrekt an. Zuvor wurden Benutzer zur Wartungsseite umgeleitet

_ACP2E-4401 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1c547060)_

### Catalog, GraphQL

#### GraphQL: Ungültige Rabattberechnung

GraphQL zeigt jetzt Rabattprozentsätze und Basispreise korrekt an, wenn Katalogpreise so konfiguriert sind, dass sie Steuern beinhalten. Zuvor traten Rundungsfehler auf, z. B. wurden 19,99 % anstelle von 20 % angezeigt.

_ACP2E-3993 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

#### Das Feld GetCart GraphQL Media Gallery gibt nach der Cache-Leerung leere Daten zurück

Nach der Fehlerbehebung wird die media_gallery des Produkts wie erwartet in der GraphQL-Antwort für die Warenkorbanfrage zurückgegeben.

_ACP2E-4185 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

### Katalog, GraphQL, Suche

#### GraphQL-Produkte haben in den Kategorieaggregationen deaktivierte Kategorien zurückgegeben

Nach der Fehlerbehebung werden deaktivierte Kategorien für die GraphQL-Anfrage „Produkte“ nicht zurückgegeben.

_ACP2E-2885 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog, Leistung

#### Kategorien in Admin werden sehr langsam geladen

Die Leistung beim Laden von Kategorien wurde deutlich verbessert. Zuvor dauerte es so lange, die Kategorie zu laden, die ein Zeitüberschreitungsproblem verursacht hat.

_ACP2E-3891 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

### Katalog, Preise

#### Falscher Rabatt für Katalogpreisregel auf das untergeordnete Produkt angewendet

Es wird das Problem behoben, bei dem die Katalogpreisregel für die Variante vom übergeordneten konfigurierbaren Produkt überschrieben wird, wenn beide Regeln dieselbe Priorität haben.

_ACP2E-3693 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Cloud] Problem mit dem Produktpreis des Pakets

Der Preis für das Bundle-Produkt mit Sonderpreis wird auf PDP/PLP für die nicht standardmäßige Währung korrekt angezeigt

_ACP2E-4110 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6e134409)_

### Katalog, Produkt

#### [Random Bug] Fotorama-Bibliothek wird nicht geladen

Das System stellt nun sicher, dass die Fotorama-Bibliothek korrekt geladen wird, sodass alle angehängten Bilder wie erwartet in der Bildergalerie angezeigt werden. Zuvor war nur das erste Bild sichtbar, da ein Problem mit der Fotorama-Bibliothek nicht korrekt geladen wurde.

_AC-12124 - [GitHub-Code-](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/27217d0e)_

#### Der Link „Produkte manuell hinzufügen“ sollte immer sichtbar sein

Es wurde ein Problem behoben, bei dem der Link „Produkte manuell hinzufügen“ beim Erstellen eines konfigurierbaren Produkts ohne vorhandene Konfigurationen nicht sichtbar war. Der Link wird jetzt immer angezeigt, sodass Administratoren einfache Produkte verknüpfen können, ohne Platzhalterkonfigurationen zu erstellen.

_AC-13866 - [GitHub-Problem](https://github.com/magento/magento2/issues/39595) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Durch die Bearbeitung eines Produkts im Backend werden zusätzliche Dezimalstellen aus den Produktoptionspreisen entfernt

Es wurde ein Problem behoben, bei dem beim Bearbeiten eines Produkts in der Admin-Produktoptionspreise auf zwei Dezimalstellen gekürzt wurden. Das System behält jetzt die Preise mit höherer Dezimalgenauigkeit bei, sodass nach dem Speichern genaue Werte beibehalten werden.

_AC-14050 - [GitHub-Problem](https://github.com/magento/magento2/issues/39655) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3b5ac075)_

### Katalog, Suche

#### Die RestAPI-Anfrage &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; schlägt mit einem Zeitüberschreitungsfehler fehl

Kategorie-REST-API-Anfragen schlagen nicht mehr mit Zeitüberschreitungsfehlern fehl.
Zuvor konnten Anfragen an /rest/default/V1/categories?searchCriteria[page_size]=1 nach bestimmten Code-Änderungen mit einer Zeitüberschreitung fehlschlagen.
13358

_AC-13358 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

### Inhalt

#### GraphQL (Magento 2.4.6-P4 ) - Fehler beim Abrufen einer CMS-Seite mit dem Status Nicht aktiv .

Es wurde ein Problem behoben, bei dem die GraphQL-Abfrage für eine deaktivierte CMS-Seite einen internen Server-Fehler zurückgab.
Jetzt ruft die Abfrage eine korrekte Antwort ohne Fehler ab.

_AC-12302 - [GitHub-Problem](https://github.com/magento/magento2/issues/38877) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Formular zur Freigabe einer Wunschliste ermöglicht zufälligen Code in den Namensfeldern

Fehlerkorrektur - Eine kritische Server-Side Template Injection (SSTI)-Sicherheitslücke im Formular zur Freigabe der Wunschliste wurde behoben, durch die bösartiger Code in das Nachrichtenfeld eingegeben und per E-Mail gesendet werden konnte. Durch die Aktualisierung wird eine Eingabevalidierung zu Blockvorlagenanweisungen und unsicheren Mustern hinzugefügt, sodass jetzt eine Fehlermeldung angezeigt wird, wenn ungültige Inhalte erkannt werden.

_AC-12730 - [GitHub-Problem](https://github.com/magento/magento2/issues/39024) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Die Platzierung von csp_whitelist.xml im Design funktioniert nicht und verursacht zeitweise Probleme

Zwischenspeicherung der CSP-Whitelist pro Website-Bereich implementiert.

_AC-13069 - [GitHub-Problem](https://github.com/magento/magento2/issues/38933) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39672)_

#### Nach dem Upgrade auf Magento 2.4.7 p2 kann nicht sehen, neu hochgeladene Dateien Media Gallery

Neu hochgeladene Dateien werden nun nach dem Upgrade in der Mediensammlung angezeigt.
Nach dem Upgrade auf Magento 2.4.7 p2 wurden neu hochgeladene Bilder erst nach der manuellen Synchronisierung in der Mediensammlung angezeigt.
13262

_AC-13262 - [GitHub-Problem](https://github.com/magento/magento2/issues/39275)_

#### Media Gallery zeigt falsche Bilder aus Verzeichnissen mit identischen Namen, aber unterschiedlicher Groß-/Kleinschreibung an

Das System behebt jetzt ein Problem, bei dem Dateien, die in ein bestimmtes Verzeichnis in der Mediensammlung hochgeladen wurden, auch in Verzeichnissen mit ähnlichen Namen, aber unterschiedlicher Groß-/Kleinschreibung sichtbar sind.

_AC-13489 - [GitHub-Problem](https://github.com/magento/magento2/issues/39382) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39502)_

#### Wenn Sie ein gallery-image vollständig aus dem Bereich entfernen, bleiben Rollen/Typen (Basis/Klein/Miniatur) festgelegt und nach dem erneuten Hinzufügen „alter“ Rollen/Typen erscheinen

Das System funktioniert wie erwartet In den Speicherbereichen übernehmen die Bilder die Rollen/Typen des neu hinzugefügten Bildes gemäß dem Standardbereich

_AC-13556 - [GitHub-Problem](https://github.com/magento/magento2/issues/39481) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39680)_

#### [Kleiner Fehler] Filter der Admin-Panel-`listing component` kann nicht aufgerufen werden, wenn der Feldwert `\` enthält

Das System funktioniert einwandfrei, wenn wir Seitentitel mit Schrägstrich filtern (z. B.: Magento\Store)

_AC-13661 - [GitHub-Problem](https://github.com/magento/magento2/issues/39513) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39535)_

#### Fehler: Skriptfehler für &quot;Magento_Catalog/js/validate-product“ für Admin Content Page Builder mit geladenen Produkten

Diese PR behebt den Skriptfehler für catalogAddToCart beim Bearbeiten des PageBuilders mit der Bedingung „products“

_AC-13891 - [GitHub-Problem](https://github.com/magento/magento2/issues/39604) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39677)_

#### Skriptfehler „catalogAddToCart“ beim Konfigurieren des Produkt-Widgets.

Es wurde ein Skriptfehler behoben, der beim Konfigurieren des Widgets Produkte mit der Kombination „Bedingungen“ in Page Builder auftrat. Das Problem wurde durch fehlende Frontend-JS-Dateien verursacht, was zu Konsolenfehlern führte. Nach der Behebung wird das Widget korrekt und ohne Konsolenfehler geladen.

_AC-13892 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/528af81a)_

#### Blockauswahl in Widgets mit derselben Kennung

Das System verarbeitet jetzt die Auswahl von Blöcken beim Erstellen von Widgets korrekt, wenn dieselben Kennungsblöcke vorhanden sind

_AC-14132 - [GitHub-Problem](https://github.com/magento/magento2/issues/39692) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39722)_

#### „Die CMS-Seite mit der ID „0“ existiert nicht“ Protokollflut

Das System funktioniert wie erwartet, nachdem ein Admin-Benutzer erstellt wurde und wenn eine neue Seite erstellt wird, gibt system.log keine Fehlermeldungen

_AC-14254 - [GitHub-Problem](https://github.com/magento/magento2/issues/39743) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39746)_

#### [GraphQL] Route-Abfrage mit Endlosschleife

Dieses Ticket behob das Problem, dass eine GraphQL-Routenabfrage mit identischem Anfragepfad und Zielpfad eine Endlosschleife verursachte und schließlich die Zeit überschritt.
In 2.4.9-alpha3 gibt die Abfrage jetzt die richtige Fehlerantwort zurück, anstatt eine Schleife zu durchlaufen.

_AC-14269 - [GitHub-Problem](https://github.com/magento/magento2/issues/39707) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Eine nicht vorhandene Sitemap antwortet mit dem Produktbild.

Das System behebt jetzt, wenn wir auf Nicht vorhandene Sitemap zugreifen, antwortet mit Produktbild mit Antwort: 404 NICHT GEFUNDEN

_AC-14295 - [GitHub-Problem](https://github.com/magento/magento2/issues/39756) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40135)_

#### Kataloglink-Widgets verwenden eine falsche URL

Das System verarbeitet Widgets jetzt korrekt, nachdem ein Katalog-Produkt-Link und ein Katalog-Kategorie-Link hinzugefügt wurden, und es zeigt auch die richtigen URLs in der HTML-Quelle an

_AC-14437 - [GitHub-Problem](https://github.com/magento/magento2/issues/39464) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39710)_

#### Tabellenpräfix wird nicht berücksichtigt

Adobe Commerce berücksichtigt jetzt beim Laden des Designrasters Design > Konfiguration in Admin die Datenbanktabellen-Präfixe. Zuvor führte die Navigation in Adobe Commerce 2.4.8 mit einem in app/etc/env.php konfigurierten Tabellenpräfix zu Inhalt > Design > Konfiguration zu einem Fehler, da das Tabellenpräfix nicht berücksichtigt wurde und das Raster der Designs nicht gerendert wurde.

_AC-14556 - [GitHub-Problem](https://github.com/magento/magento2/issues/39847) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Ändern Sie für mehr Flexibilität das konstante IMAGE_FILE_NAME_PATTERN in public visible

Das konstante IMAGE_FILE_NAME_PATTERN in GenerateRenditions.php wurde veröffentlicht, um Entwicklern mehr Flexibilität bei der Arbeit mit Bildausgabedarstellungen zu ermöglichen. Die Fehlerbehebung ist in Magento 2.4.9-alpha3 mit vollständiger Abdeckung von Unit- und Integrationstests enthalten.

_AC-15338 - [GitHub-Problem](https://github.com/magento/magento2/issues/39733) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Falsche Versandmethode wird auf der Seite „Überprüfungsauftrag“ für Mehrfachversand angezeigt

Fehlerkorrektur - Beim Multi-Shipping-Checkout wird auf der Seite Prüfungsauftrag jetzt nicht mehr der richtige Versandbetrag angezeigt (5 INR statt 10 INR). Durch die Aktualisierung wird sichergestellt, dass für jede Adresse der richtige Versandbetrag angezeigt wird.

_AC-15664 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento config:show(or set) design/theme/theme_id schlägt fehl

Es wurde ein Problem behoben, bei dem die CLI-Befehle bin:show/magento config:set und config für den Pfad design/theme/theme_id trotz der vorhandenen Konfiguration fehlschlugen.
Jetzt werden die Befehle erfolgreich ausgeführt und ermöglichen das Anzeigen und Festlegen der Design-ID ohne Fehler.

_AC-5915 - [GitHub-Problem](https://github.com/magento/magento2/issues/35751) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64823f95)_

#### Bild mit relativ geringer Breite kann nicht hochgeladen werden

Das System versäumt es nicht mehr, die Größe des Bildes mit einer relativ kleinen Breite auf seine Höhe zu ändern.

_ACP2E-3558 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Die Produktkomponente von Page Builder funktioniert nicht, wenn der Benutzer keine Widget-Berechtigung hat

Vor der Behebung gab es auf der Seite beim Zugriff auf ein Widget ohne Berechtigungen einen allgemeinen Fehler und die GIF „wird geladen“. Nach der Fehlerbehebung wird ein modales Fenster mit der Meldung angezeigt, dass Sie zum Anzeigen dieses Inhalts Berechtigungen benötigen. Nachricht.

_ACP2E-3664 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Falscher Konfigurationspfad für Konfiguration des Remote-Speicherpfads

Nach der Fehlerbehebung wirkt sich das Festlegen der Stilkonfiguration für Remote-Speicherpfade auf die tatsächliche Konfiguration des AWS S3-Pfads aus.

_ACP2E-3734 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Die Reihenfolge der Produkt-Widgets von Page Builder wird in GraphQL nicht angewendet

Es wurde ein Problem behoben, bei dem die GraphQL-Antwort auf die Abfrage „route“ Produkte innerhalb des Inhaltstyps Page Builder-Produkte nicht in der richtigen Sortierreihenfolge zurückgab.

_ACP2E-3898 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problem mit der Preisanzeige an nicht englischen Storefronts aufgrund der Version der ICU-Bibliothek

Nach der Fehlerbehebung wird der Produktpreis im hebräischen Gebietsschema (Israel) korrekt angezeigt.

_ACP2E-3938 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Aktualisieren der vom Store-Code bereinigten Design-Konfiguration

Es wurde ein Problem behoben, bei dem durch die Aktualisierung des Code für die Store-Ansicht die Design-Konfigurationseinstellungen gelöscht wurden, da der Konfigurations-Cache nicht ordnungsgemäß aktualisiert wurde.

_ACP2E-3941 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

#### Page Builder - Problem mit der Logik für Produktbedingungen (ODER-Logik zeigt falsch weniger Produkte an)

Das Page Builder-Produkt-Widget gibt jetzt das richtige Ergebnis zurück, wenn ein Attribut mit dem globalen Umfang in der Bedingung „Beliebige Übereinstimmung“ verwendet wird

_ACP2E-4096 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

#### Das Produktkarussell fügt Page Builder falsche Produkte hinzu

Vor der Fehlerbehebung wäre ein konfigurierbares Produkt automatisch in die PageBuilder-Produktkarusselllisten aufgenommen worden, wenn eines seiner untergeordneten Elemente die Filterbedingungen erfüllt hätte. Nach der Fehlerbehebung wird das übergeordnete Produkt nur dann einbezogen, wenn das untergeordnete Produkt allein nicht sichtbar ist.

_ACP2E-4341 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

#### Das Produktlisten-Widget gibt ein falsches Ergebnis zurück, wenn mehrere Kategorien in der Kategoriebedingung aufgelistet sind

Das Widget „Liste der Katalogprodukte“ zeigt jetzt genaue Ergebnisse an, wenn mehrere Kategorien in der Bedingung „Kategorie ist eine von“ aufgeführt sind. Zuvor wurde nur die erste Kategorie in der Liste verarbeitet.

_ACP2E-4353 - [GitHub-Code-](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [Cloud] Die Erstellung von Mediensammlungs-Ordnern erfordert die Berechtigung DELETE_FOLDER in der Neuen Mediensammlung - Rollen, bei denen nur create_folder vorhanden ist, können keine Ordner erstellen

Vor dieser Fehlerbehebung konnte ein Admin-Benutzer bzw. eine Admin-Benutzerin, der bzw. die nur über die Berechtigung zum Erstellen von Ordnern für Inhalte verfügt, keinen Ordner in der CMS Media Gallery erstellen. Nach der Fehlerbehebung können Inhaltsersteller in der Mediensammlung jetzt jedoch Ordner nur mit der Berechtigung Ordner erstellen erstellen .

_ACP2E-4376 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] Duplizieren einer CMS-Seite

Vor dieser Fehlerbehebung wäre das Duplizieren einer CMS-Seite mit einer benutzerdefinierten Layout-Aktualisierung fehlgeschlagen. Jetzt können CMS-Seiten mit benutzerdefinierten Layout-Aktualisierungen ohne Fehler dupliziert werden.

_ACP2E-4449 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Kunde/Kunden

#### Ausnahme bei Storefront, wenn Admin den CustomAttribute-Block über den CMS-Seiteninhalt hinzufügt

Es wurde ein Problem behoben, bei dem das Hinzufügen des CustomerCustomAttribute-Blocks über den Seiteninhalt der CMS zu einer Storefront-Ausnahme führte und das Laden der Seite verhinderte.
Die Storefront wird jetzt normal angezeigt und zeigt eine aussagekräftige Meldung an, wenn der Inhalt nicht gerendert werden kann, wodurch kritische Fehler vermieden werden.

_AC-11004_

#### Das Online-Admin-Raster von Kunden zeigt doppelte Zeilen an, wenn sich ein Benutzer anmeldet, dann abmeldet und dann wieder einloggt

Es wurde ein Problem behoben, bei dem im Admin-Raster „Kunden jetzt Online“ doppelte Zeilen angezeigt wurden, wenn sich ein Kunde abgemeldet und wieder angemeldet hat.
Das Raster aktualisiert nun den vorhandenen Datensatz mit der neuesten Aktivität, anstatt doppelte Einträge zu erstellen, um eine genaue Verfolgung der Kundensitzungen sicherzustellen.

_AC-11511 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/528af81a)_

#### Die Validierung des Mindest- und Höchstwerts funktioniert nicht für das DOB-Attribut in der Storefront

Dieser Fehler behob das Problem, dass die Validierung des Mindest- und Höchstdatums für das Geburtsdatum (Geburtsdatum) in der Storefront nicht funktionierte (obwohl sie in Admin funktionierte).
In 2.4.9-alpha3 blockiert die Validierung jetzt korrekt das Speichern von Kundinnen und Kunden mit einem Geburtsdatum außerhalb des zulässigen Bereichs, sodass eine Fehlermeldung angezeigt wird.

_AC-13535 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ajax 401-Fehler beim Laden auf dem Warnbildschirm im Admin-Bedienfeld, während die Anmeldung als Kunde widerrufen wurde

Dieser Fehler wurde behoben, durch den bei einer widerrufenen Anmeldung als Kundin oder Kunde ein Ajax 401-Fehler mit unbearbeitetem HTML im Warnfenster angezeigt wurde.
Nach der Fehlerbehebung zeigt das System jetzt korrekt eine normale Warnmeldung anstelle von unbearbeitetem HTML an.
Die Lösung wurde in Magento 2.4.9-alpha3 bereitgestellt

_AC-15336 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

### Framework

#### Kompilieren des Codes des deaktivierten Moduls.

Diese Pull-Anforderung löscht deaktivierte Module vor der Code-Kompilierung.

_AC-10933 - [GitHub-Problem](https://github.com/magento/magento2/issues/38241) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39723)_

#### Fehler beim Ausführen des Befehls „setup:upgrade mit benutzerdefiniertem DB-Trigger

Benutzerdefinierte Datenbankfehler verursachen keine Trigger mehr während des Setups:upgrade.
Zuvor konnte das Ausführen von bin/:upgrade-Setup mit einem benutzerdefinierten Datenbank-Trigger (z. B. AFTER INSERT in der Speichertabelle) zu dem Fehler führen:
„Warnung: Versuch, auf den Array-Offset für den Wert vom Typ null in vendor/magento/framework/Mview/View/Subscription.php in Zeile 357 zuzugreifen“
11487

_AC-11487 - [GitHub-Problem](https://github.com/magento/magento2/issues/38481)_

#### [Problem] Methodensignatur mit der Schnittstelle konsistent machen

Die Methodensignatur für getAttributes ist jetzt mit ihrer Schnittstelle konsistent und verhindert Fehler beim Überschreiben der Methode. Zuvor verursachten Inkonsistenzen in der Methodensignatur Fehler beim Versuch, die getAttributes-Methode zu überschreiben.

_AC-11578 - [GitHub-Problem](https://github.com/magento/magento2/issues/38501) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31955)_

#### Formular einer Website/Gruppe/Store-Entität kann nicht mit einem Formularelement mit mehreren Werten für Erweiterungsattribute erweitert werden

Diese PR ermöglicht es mehrwertigen Formularelementen, Daten an ein Website-/Gruppen-/Store-Formular zu senden.

_AC-11657 - [GitHub-Problem](https://github.com/magento/magento2/issues/24070) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/24094)_

#### [Problem] Beheben der Regel „validate-emails“ für die UI-Komponente

Das System validiert nun mehrere in Benutzeroberflächenkomponenten eingegebene E-Mail-Adressen ordnungsgemäß, um sicherzustellen, dass jede E-Mail ordnungsgemäß zugeschnitten und validiert wird. Zuvor verwendete das System eine falsche Methode zum Zuschneiden von E-Mail-Adressen, was zu Validierungsfehlern führen konnte.

_AC-11719 - [GitHub-Problem](https://github.com/magento/magento2/issues/38528) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33470)_

#### [Problem] Verwendung des Bereichsauflösers entfernen

Diese PR löst die Admin-URL-Einstellungen global anstelle des aktuellen Speichers auf

_AC-11736 - [GitHub-Problem](https://github.com/magento/magento2/issues/38566) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38554)_

#### [Problem] Entfernen redundanter Methoden

Code-Qualität: Redundante Methoden in Komponenten für asynchrone Vorgänge und Verkäufe wurden entfernt, die nur übergeordnete Methoden aufgerufen haben, ohne Funktionen hinzuzufügen. Dies verbessert die Code-Wartbarkeit.

_AC-11915 - [GitHub-Problem](https://github.com/magento/magento2/issues/29748) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml Vorlage ungültig für PHP 8.2

Diese Pull-Anfrage behebt ein Problem, wenn eine CMS-Seite, die mit der Null-Überschrift erstellt wurde, wie in PHP 8.x, die null an trim() übergibt, eine Ausnahme auslöst: Veraltete Funktionalität: trim(): Übergeben von null an den Parameter #1 ($string) vom Typ String

_AC-12856 - [GitHub-Problem](https://github.com/magento/magento2/issues/39092) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39398)_

#### Die XSD-Validierung schlägt in etc/adminhtml/system.xml-Dateien fehl, die Kommentare unterhalb von Feldelementen enthalten.

Diese PR behebt XML-Schemadefinitionen in PhpStorm für den Kommentarknoten

_AC-12945 - [GitHub-Problem](https://github.com/magento/magento2/issues/39148) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39867)_

#### Offenlegung der Magento-Version über die Einrichtungsroute mit der standardmäßigen Nginx-Konfiguration

Das System funktioniert jetzt erwartungsgemäß und zeigt nicht die genaue Version von Magento an, die auf der Site ausgeführt wird

_AC-13205 - [GitHub-Problem](https://github.com/magento/magento2/issues/39227) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39228)_

#### [Problem] Entpacken Sie Objektargumente als benannte Parameter

Das System nutzt nun die PHP 8.1-Funktion zum Entpacken von Arrays mit benannten Parametern, wodurch die Notwendigkeit von array_values-Aufrufen entfällt und die Gesamtleistung verbessert werden kann. Zuvor forderte das System array_values zum Entpacken von Objektargumenten.

_AC-13210 - [GitHub-Problem](https://github.com/magento/magento2/issues/39233) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37411)_

#### [Problem] Angebotsadresse refaktorieren Methode nicht validieren

Diese PR enthält Verbesserungen der Lesbarkeit der doValidate-Methode.

_AC-13214 - [GitHub-Problem](https://github.com/magento/magento2/issues/38230) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38219)_

#### Magento Option —magento-init-params nie verwendet, wenn CLI ausgeführt wird?

Die Option —magento-init-params wird jetzt beim Ausführen von CLI-Befehlen verwendet.
Zuvor hatte die Übergabe von —magento-init-params an CLI-Befehle keine Auswirkungen auf Parameter wie MAGE_MODE.
13231

_AC-13231 - [GitHub-Problem](https://github.com/magento/magento2/issues/39248) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue - Falsche Typdeklaration

Das System definiert nun in der Funktion getItemsByColumnValue den Eingabeparameter $value als primitiven Typ, nicht als Array, und stellt sicher, dass die Funktion die erwartete Auflistung zurückgibt. Wenn zuvor ein Array mit einem einzelnen Wert als Eingabeparameter verwendet wurde, gab die Funktion null zurück und IDEs markierten dies als Fehler.

_AC-13240 - [GitHub-Problem](https://github.com/magento/magento2/issues/33070) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33120)_

#### Bei der Verwendung des Dateispeichers für den Sperranbieter erhalten wir ein ständig wachsendes Verzeichnis von Dateien, ohne dass eine Bereinigung stattfindet

Diese Pull-Anfrage führt einen neuen Cronjob ein, der einmal pro Tag ausgeführt wird und nach Sperrdateien sucht, die in den letzten 24 Stunden nicht geändert wurden und daher sicher entfernt werden können. Dadurch wird der Inhalt des Sperrdateiverzeichnisses unter Kontrolle gehalten.
Dieser Cronjob wird nur ausgeführt, wenn der Sperranbieter für die Verwendung von Dateien konfiguriert ist, nicht, wenn einer der anderen verwendet wird (Datenbank - der Standard, ZooKeeper oder Cache)

_AC-13367 - [GitHub-Problem](https://github.com/magento/magento2/issues/39369) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39372)_

#### [Problem] Bereinigung: Verwenden Sie keinen ungültigen Rückgabewert aus Methodenaufrufen.

Diese PR führt kleinere Bereinigungen durch. Manchmal haben wir Methoden aufgerufen, die nichts zurückgegeben haben (void), und dann diesen Ergebniswert verwendet. Was wirklich nicht benötigt wird.

_AC-13664 - [GitHub-Problem](https://github.com/magento/magento2/issues/39524) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39516)_

#### Mit FPC verknüpfte Cache-Schlüssel in Magento 2.4.7-Implementierungen mit mehreren Speichern

Es wurde ein Problem behoben, bei dem Cache-Schlüssel für vollständige Seiten (Full Page Cache, FPC) in Multi-Store-Setups keine MAGE_RUN_CODE und MAGE_RUN_TYPE enthielten, was zu einem inkonsistenten Verhalten der Cache-Schlüssel im Vergleich zu früheren Versionen führte. Cache-Schlüssel enthalten jetzt korrekt den Speicherkontext, wodurch eine ordnungsgemäße Cache-Isolierung über Speicher hinweg sichergestellt wird.

_AC-13719 - [GitHub-Problem](https://github.com/magento/magento2/issues/39456) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problem] [PHPDOC] Schlechtes phpdoc für Magento\Framework\Message\ManagerInterface beheben

Dieser PR behebt das fehlerhafte phpdoc für \Magento\Framework\Message\ManagerInterface und entfernt alle doppelten phpdoc in \Magento\Framework\Message\Manager (verwenden Sie inheritdoc-Syntax).

_AC-14312 - [GitHub-Problem](https://github.com/magento/magento2/issues/39593) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39153)_

#### Partielle Indizierung funktioniert nicht mehr für Kunden mit einer großen Anzahl von Aktualisierungen.

Die partielle Indizierung funktioniert jetzt für Kunden mit einer großen Anzahl von Aktualisierungen.
Zuvor führte das Erreichen des Maximalwerts für die Spalte version_id in der Änderungsprotokolltabelle dazu, dass Indexaktualisierungen angehalten wurden.
14424

_AC-14424 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 verwendet Entwicklungspakete, die nicht der semantischen Versionierung folgen

Magento 2.4.8 erfordert dev-Versionen von pdepend/pdepend und phpmd/phpmd (3.x-dev) für die PHP 8.4-Kompatibilität.
Diese Entwicklungsversionen stehen im Konflikt mit Drittanbieter-Tools, die SemVer-kompatible Pakete erwarten, und verhindern einige Upgrades.
Eine temporäre Problemumgehung besteht darin, die Dev-Versionen in composer.json zu alias (z. B. „3.x-dev as 3.99.0„), um Kompatibilität zu ermöglichen und gleichzeitig die semantische Versionierung zu erfüllen.
Dies stellt die Unterstützung von PHP 8.4 sicher und vermeidet Konflikte, bis stabile Versionen verfügbar werden.

_AC-14519 - [GitHub-Problem](https://github.com/magento/magento2/issues/39796)_

#### Der MView-Mechanismus ignoriert Fehler bei der Ausführung von Triggern im Hintergrund

Der MView-Mechanismus meldet nun Fehler bei der Ausführung des Triggers ordnungsgemäß.
Zuvor wurden Fehler bei der Ausführung von Trigger im Hintergrund ignoriert, was dazu führen konnte, dass Indexaktualisierungen ohne Benachrichtigung fehlten.
14567

_AC-14567 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problem] Vermeiden Sie viele unnötige Ausnahmen beim Laden der XML-Zusammenführung des Layouts

Diese PR führt eine neue Funktion ein (für die B/C-Komprimierung überschreiben wir nicht die geschützte _loadXmlString), die geladen werden soll, und löst keine Ausnahme aus

_AC-14580 - [GitHub-Problem](https://github.com/magento/magento2/issues/39877) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37570)_

#### [Problem] Verwenden der Konstruktor-Eigenschaftsförderung im Modul Vault-Graph QL

Diese PR ersetzt Konstruktoreigenschaften durch Eigenschaftsförderung im VaultGraphQL-Modul

_AC-14616 - [GitHub-Problem](https://github.com/magento/magento2/issues/39900) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36996)_

#### [Problem] Code-Redundanz für Modul-Frontend-Layouts wurde entfernt.

Diese PR entfernt Code-Redundanz zu Design-Layouts für Magento_MSRP-, Magento_LoginAsCustomerAssistance-, Magento_Newsletter- und Magento_Sitemap-Module Frontend-Layouts.

_AC-14625 - [GitHub-Problem](https://github.com/magento/magento2/issues/30673) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30644)_

#### [Problem] Schließen Sie den Konstruktor als Teil `CommandListInterface` API ein und erweitern Sie die Inline-Dokumentation

Dieses PR-Update kennzeichnet Magento\Framework\Console\CommandList als API und führt den Konstruktor zur besseren Erweiterbarkeit in die CommandListInterface-Klasse ein. Außerdem wird die Inline-Dokumentation verbessert, um die Klarheit und Wartbarkeit für Entwickler zu verbessern, die Konsolenbefehle erweitern.

_AC-14680 - [GitHub-Problem](https://github.com/magento/magento2/issues/31102) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37901)_

#### [Problem] Entfernen von Code im Zusammenhang mit Microsoft IIS

Diese PR bereinigt den Code im Zusammenhang mit Microsoft IIS gemäß der Magento-Systemanforderungsdokumentation, die besagt, dass das Microsoft Windows-Betriebssystem nicht unterstützt wird

_AC-14702 - [GitHub-Problem](https://github.com/magento/magento2/issues/39910) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js-Syntaxfehler

Die Funktion „Systemvergrößerung“ sollte weiterhin so funktionieren wie zuvor, und „Vergrößerungsoptionen“ sollte nicht global verfügbar sein

_AC-14722 - [GitHub-Problem](https://github.com/magento/magento2/issues/36200) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39321)_

#### Backport Verbose-Modus `setup:db:status` CLI-Befehl

Der `setup:db:status` CLI-Befehl unterstützt jetzt den Verbose-Modus.
Zuvor war es schwierig, die für Upgrades erforderlichen Datenbankänderungen zu verstehen. Jetzt bietet die Ausführung von `bin/magento setup:db:status -v` detaillierte Informationen zu Schema- und Datenunterschieden.
14807

_AC-14807 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### SMTP-Mail-Versand mit TLS und 2.4.8

Der SMTP-E-Mail-Versand mit TLS funktioniert jetzt erwartungsgemäß.
Zuvor führte das Senden von E-Mails über SMTP mit TLS zu dem Fehler: error:1408F10B:SSL-Routinen:ssl3_get_record:falsche Versionsnummer.
14883

_AC-14883 - [GitHub-Problem](https://github.com/magento/magento2/issues/39947) - [GitHub-Code-](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8b453942) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problem] Beheben eines Gleichzeitigkeitsproblems bei der Bereitstellung statischer Inhalte

Diese PR behebt einen Fehler, bei dem mehrere gleichzeitige Prozesse sich drehen, um dasselbe Design-Paket zu verarbeiten, je nachdem, wie die Designs mit ihren übergeordneten Elementen definiert werden.

_AC-14944 - [GitHub-Problem](https://github.com/magento/magento2/issues/39990) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39954)_

#### [Problem] Legacy-Kompatibilitätscode für PHP-Versionen &lt; 8.1 entfernen

Diese Pull-Anfrage entfernt Code, der für die Ausführung auf PHP &lt;8.1 entwickelt wurde.
Auch entfernt Prüfungen für PHP_VERSION_ID Kontakt Verfügbarkeit, da es in allen PHP-Versionen verfügbar ist

_AC-14971 - [GitHub-Problem](https://github.com/magento/magento2/issues/39891) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39882)_

#### FPC funktioniert nicht bei der Anmeldung

Der vollständige Seiten-Cache (FPC) funktioniert jetzt für angemeldete Kunden ordnungsgemäß.
Zuvor wurde die Homepage nach der Anmeldung nicht aus dem Cache geladen und die Kopfzeile „x-magento-cache-debug“ zeigte „MISS“ anstelle von „HIT“ an.
14999

_AC-14999 - [GitHub-Problem](https://github.com/magento/magento2/issues/40007)_

#### Generische Typen in bestimmten PHP-Klassen hinzufügen, um die Unterstützung der statischen Analyse zu verbessern

Das System verwendet jetzt eine generische Typdefinition, um dies erheblich zu verbessern, indem sie als die genaue Klasse interpretiert wird, die ein Methodenaufruf zurückgibt

_AC-15013 - [GitHub-Problem](https://github.com/magento/magento2/issues/40017) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40119)_

#### [Problem] Verbesserung der Fehlerbehandlung in SchemaBuilder

Diese PR verbessert die Handhabung von Fehlermeldungen des DB-Schemas. Dies hilft uns, ein Problem zu identifizieren, ohne dass umfangreiche Debugging-Maßnahmen erforderlich sind.

_AC-15020 - [GitHub-Problem](https://github.com/magento/magento2/issues/39816) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39799)_

#### Rest-API: Aufruf einer Memberfunktion getVideoProvider() auf null

Es wurde ein Problem behoben, bei dem der Aufruf der konfigurierbaren API für untergeordnete Produkte einen internen 500-Server-Fehler zurückgab, wenn ein untergeordnetes Produkt nur ein YouTube-Video und keine anderen Bilder hatte.
Der Fehler wurde durch einen Nullverweis im ExternalVideoEntryConverter verursacht.
Jetzt gibt die API untergeordnete Produkte mit Mediensammlungseinträgen, einschließlich externer Videodaten, korrekt zurück, ohne Fehler auszulösen.
Dadurch wird ein ordnungsgemäßer Abruf aller Medientypen für untergeordnete Produkte über die REST-API sichergestellt.

_AC-15046 - [GitHub-Problem](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Text/JavaScript aus der Cookie-Skript-Tag-Deklaration entfernen

Durch diese PR wurde das unnötige Attribut type=„text/javascript“ aus dem Cookie-Skript-Tag entfernt, um die HTML5-Konformität zu gewährleisten.

_AC-15061 - [GitHub-Problem](https://github.com/magento/magento2/issues/39982) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39983)_

#### [Problem] Beheben Sie einige Tippfehler in PHPDoc-Kommentaren

Diese PR behebt die wenigen Tippfehler in der phpdoc

_AC-15075 - [GitHub-Problem](https://github.com/magento/magento2/issues/40042) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38809)_

#### [Problem] Sprintf-Nutzung in Phrasenaufrufen entfernen

Durch diese PR wird die Verwendung von sprintf im Aufruf der Phrase-Funktion im Magento-Core entfernt.

_AC-15183 - [GitHub-Problem](https://github.com/magento/magento2/issues/40050) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40033)_

#### Es können nicht alle ungültigen Indizes auf Multithread-Indizierern mit aktiver Anwendungssperre neu indiziert werden

Dieses Problem behob einen Multi-Thread-Indexerfehler, wenn USE_APPLICATION_LOCK aktiviert war.
Zuvor gingen bei der parallelen Verarbeitung DB-Sperren verloren, was dazu führte, dass Indexer im „funktionierenden“ Zustand blieben und SQL-Fehler auslösten (Tabelle nicht gefunden).
In Magento 2.4.9-alpha3 stellt die Korrektur sicher, dass Indexer bei aktivierter Anwendungssperre korrekt neu indiziert werden.

_AC-15270 - [GitHub-Problem](https://github.com/magento/magento2/issues/40102) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Unklare/ungültige Rückgabetypen in Magento\Framework\Escaper

Das System akzeptiert Typen von Ausweichmethoden bei der statischen Analyse mit Phpstan auf Ebene 5

_AC-15272 - [GitHub-Problem](https://github.com/magento/magento2/issues/40012) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40114)_

#### [Problem] Zulassen, dass die warteschlangenspezifische Konfiguration den standardmäßigen Wert für max-messages überschreitet

Das System lässt jetzt zu, dass die Warteschlangen-spezifische Konfiguration den standardmäßigen Wert für max-messages überschreitet

_AC-15284 - [GitHub-Problem](https://github.com/magento/magento2/issues/40121) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40110)_

#### [Problem] Doppelter Cache-FPC für dieselbe Seite mit derselben Abfrage bei Verwendung von „lackieren“

Diese PR behebt doppelte Vollseiten-Cache-Einträge bei Verwendung von Varnish, indem die Reihenfolge der Abfrageparameter normalisiert wird, um konsistente Cache-Schlüssel für identische Anfragen sicherzustellen.
Verbessert die Cache-Trefferrate und Leistung für URLs mit denselben Parametern in verschiedenen Sequenzen.

_AC-15325 - [GitHub-Problem](https://github.com/magento/magento2/issues/39706) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39704)_

#### Community-Designs enthalten Ressourcen für Commerce Edition-Module

Formatierungsressourcen, die nur für Commerce vorgesehen sind, wurden aus den Community-Designs entfernt, indem sie in die entsprechenden Modulverzeichnisse verschoben wurden. Dadurch wird verhindert, dass nicht verwendetes CSS in der Community Edition gebündelt wird, was unnötige Payloads reduziert und tote Stilregeln eliminiert, während gleichzeitig eine ordnungsgemäße Formatierung sichergestellt wird, wenn Commerce-Module aktiviert sind.

_AC-15347 - [GitHub-Problem](https://github.com/magento/magento2/issues/21446) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9bcd880a)_

#### [Problem] Das Hinzufügen von Store-Code zu URLs sollte global sein

Diese PR löst das Problem, indem sie sicherstellt, dass die Einstellung „Store-Code zu URLs hinzufügen“ unter Verwendung des globalen Bereichs im Kern-Code abgerufen wird

_AC-15365 - [GitHub-Problem](https://github.com/magento/magento2/issues/40069) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40065)_

#### [Problem] Nicht deklariertes Plug-in nur protokollieren, wenn es nicht deaktiviert ist

Diese PR behebt und protokolliert die Plug-ins, die tatsächlich nicht deklariert und nicht verwendet werden (aktivierte und fehlende Instanz).

_AC-15386 - [GitHub-Problem](https://github.com/magento/magento2/issues/40086) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40081)_

#### [Problem] Kleine Bereinigung, doppelte Schlüssel aus Array entfernt

Das System führte jetzt eine kleine Bereinigung durch, und es wurde kein Fehler im Zusammenhang mit dem Array gefunden, das zwei doppelte Schlüssel mit dem Wert „Gewichtung (und höher)“ enthält.

_AC-15414 - [GitHub-Problem](https://github.com/magento/magento2/issues/39851) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, Magento/Framework, Version 103.0.8-p2: EmailMessage-Klasse, die eine nicht vorhandene Methode aufruft

Die EmailMessage-Klasse verarbeitet jetzt das Abrufen von E-Mail-Textkörpern korrekt.
Zuvor versuchte die Klasse Magento\Framework\Mail\EmailMessage in Magento 2.4.8-p2 mit Magento/Framework Version 103.0.8-p2, eine nicht vorhandene Methode (getTextBody) für das Symfony-E-Mail-Nachrichtenobjekt aufzurufen. Dies führte zu Fehlern, wenn Module oder Anpassungen von Drittanbietern für die E-Mail-Verarbeitung auf diese Methode angewiesen waren.
Jetzt ruft die EmailMessage-Klasse keine undefinierten Methoden mehr auf, um diese Fehler zu verhindern. 15446

_AC-15446 - [GitHub-Problem](https://github.com/magento/magento2/issues/40170) - [GitHub-Code-](https://github.com/magento/magento2/commit/059fd469) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Daten-/Schema-Patches getAliases() verursachen Fehler während der `setup:upgrade`

getAliases() verursacht Fehler während des Setups:upgrade und diese PR behebt dieselbe

_AC-15559 - [GitHub-Problem](https://github.com/magento/magento2/issues/31396) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38239)_

#### Unzulässige Mischung von Sortierungen für den Vorgang

_AC-15614 - [GitHub-Problem](https://github.com/magento/magento2/issues/40138) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44329e9d)_

#### [Problem] [PHPDOC] Fehlerbehebung für fehlerhafte phpdoc Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

Diese PR aktualisiert das PHPDoc für \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs(), damit korrekt widergespiegelt wird, dass der $alias-Parameter zusätzlich zur Zeichenfolge null sein kann. Dadurch werden PHPStan-Probleme auf Ebene 5+ behoben und die Kompatibilität der Code-Qualitäts-Tools verbessert.

_AC-15626 - [GitHub-Problem](https://github.com/magento/magento2/issues/39598) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39581)_

#### Unzulässige Mischung von Sortierungen im urlrewrite-Modul

_AC-15647 - [GitHub-Problem](https://github.com/magento/magento2/issues/40189) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/44329e9d)_

#### Bedingung ist in `\Magento\Framework\Escaper::escapeScriptIdentifiers` nie erfüllt

Es wurde eine nicht erreichbare Bedingung in \Magento\Framework\Escaper::escapeScriptIdentifiers korrigiert, indem die Prüfung auf „false“ durch „null“ ersetzt, an den Rückgabewerten von „preg_replace“ ausgerichtet und die Code-Genauigkeit verbessert wurde, ohne dass die Funktionalität beeinträchtigt wurde.

_AC-15667 - [GitHub-Problem](https://github.com/magento/magento2/issues/40195) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### Lack 7.3 (neueste Version)- Unterkategorien Links / Optionen der Standardkategorie werden nicht auf der Shop-Startseite angezeigt

Bestätigt, dass fehlende Unterkategorielinks auf der Storefront-Startseite bei Verwendung von Varnish 7.3 durch die ESI-Anfrageverarbeitung und Serverkonfiguration verursacht wurden und nicht durch einen Magento-Code-Fehler. Das Problem wird durch empfohlene Anpassungen der Varnish-Konfiguration behoben, ohne dass Änderungen am Kern-Code erforderlich sind.

_AC-15674 - [GitHub-Code-](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9a62604c)_

#### [Problem] Hinzufügen zusätzlicher Debugging-Daten zu `cache_invalidate` Protokoll

Diese PR erweiterte das Protokoll cache_invalidate um Anforderungskontext und Stacktrace für vollständige Cache-Bereinigungen, wodurch Debugging und Sichtbarkeit verbessert wurden.
Auf diese Weise können Sie die Quelle unerwarteter vollständiger Cache-Invalidierungen identifizieren, ohne die vorhandenen Funktionen zu ändern.

_AC-15719 - [GitHub-Problem](https://github.com/magento/magento2/issues/40204) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40196)_

#### [Problem] Die Autoloader-Ausschlussliste des Komponisten wurde etwas verbessert.

Diese PR verfeinert Composer-Autoloader-Ausschlüsse, um Testklassen zu überspringen, unnötige Klassenzuordnungseinträge zu reduzieren und PSR-4-Warnungen zu vermeiden.

_AC-15743 - [GitHub-Problem](https://github.com/magento/magento2/issues/40109) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40107)_

#### [Problem] Verhindern Sie, dass Bereitstellungen ohne Ausfallzeiten durch `db_schema.xml`-Deklarationen mit `comment=""` unterbrochen werden

Das System verhindert jetzt, dass db_schema.xml-Deklarationen mit comment=&quot;&quot; Bereitstellungen ohne Ausfallzeiten unterbrechen

_AC-15980 - [GitHub-Problem](https://github.com/magento/magento2/issues/40254) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40242)_

#### `\Magento\Framework\Filesystem\Glob::glob(...)` Cache kann nicht gelöscht werden

Dieses PR-Update bietet eine Möglichkeit, den von \Magento\Framework\Filesystem\Glob verwendeten internen statischen Cache zu löschen, um sicherzustellen, dass neue und genaue Ergebnisse erzielt werden, wenn sich die Dateistrukturen ändern. Es verbessert die Zuverlässigkeit und das Entwicklererlebnis, insbesondere in Testszenarien und langwierigen Prozessen, bei denen die globalen Ergebnisse auf dem neuesten Stand bleiben müssen.

_AC-15989 - [GitHub-Problem](https://github.com/magento/magento2/issues/35741) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35742)_

#### Die Link-URL von ReadME Leaders weist eine permanente Weiterleitung auf.

Der Link zu README-Leadern wurde aktualisiert, indem die dauerhaft umgeleitete und abgelaufene URL durch korrekte Arbeitslinks ersetzt wurde, um sicherzustellen, dass Mitwirkende und Betreuer die Seiten ordnungsgemäß öffnen.

_AC-16046 - [GitHub-Problem](https://github.com/magento/magento2/issues/40292) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problem] [PHPDOC] Schlechtes phpdoc beheben Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

Die PHPDoc-Anmerkungen für joinLeft() in der Attributsammlung wurden korrigiert, um korrekte Array-Definitionen zu ermöglichen und die Code-Korrektheit und Kompatibilität mit Tools wie PHPStan zu verbessern.

_AC-16187 - [GitHub-Problem](https://github.com/magento/magento2/issues/40354) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39155)_

#### Stellen Sie sicher, dass bei einem einzelnen Befehlsfehler der Fehler (Datei oder „stderr„) protokolliert wird, ohne die Ausführung nachfolgender CLI-Befehle zu stoppen.

Das System stellt nun sicher, dass bei einem einzelnen Befehlsfehler der Fehler (Datei oder „stderr„) protokolliert wird, ohne die Ausführung nachfolgender CLI-Befehle zu stoppen

_AC-16244 - [GitHub-Problem](https://github.com/magento/magento2/issues/40006) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40063)_

#### [Problem] Fügen Sie den int-Typ zu $maxAge im PageCache-Kernel hinzu.

Dieser PR stellt sicher, dass der $maxAge-Parameter im PageCache-Kernel als Ganzzahl ausschließlich typisiert wird, um die Typsicherheit zu verbessern und PHPStan/statische Analysefehler bei der Cache-Handhabung zu vermeiden.

_AC-16313 - [GitHub-Problem](https://github.com/magento/magento2/issues/40438) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36600)_

#### Zum Warenkorb hinzufügen Ereignis : leere Preise

Es wurde ein Problem behoben, bei dem Produktpreise während des Prozesses „Zum Warenkorb hinzufügen“ im Ereignis Checkout_Cart_product_add_after Observer als null zurückgegeben wurden.
Jetzt werden der Basispreis und die damit verbundenen Preiswerte korrekt abgerufen, sodass für Beobachter und benutzerdefinierte Implementierungen genaue Daten verfügbar sind.

_AC-5966 - [GitHub-Problem](https://github.com/magento/magento2/issues/35638) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1 Typ Fehlerbehebung

Die zugehörigen Produkte werden jetzt in ein leeres -Array anstelle von „false“ initialisiert, wenn der strikte Verarbeitungsmodus nicht aktiv ist oder wenn Produktinformationen verfügbar sind. Durch diese Änderung wird sichergestellt, dass sich die nachfolgende Logik bei der Handhabung zugehöriger Produkte konsistent verhält und die Stabilität und Vorhersagbarkeit im Produktvorbereitungsprozess verbessert wird.

_AC-6017 - [GitHub-Problem](https://github.com/magento/magento2/issues/35808) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35842)_

#### Erwarteter Typ &quot;Magento\Customer\Api\Data\GroupInterface&quot;. &#39;Magento\Customer\Model\Group&#39; gefunden.

Es wurde ein Problem behoben, bei dem das Speichern einer Kundengruppe über GroupRepositoryInterface mithilfe von GroupFactory einen Typfehler verursachte.
Zuvor hatte das Repository „GroupInterface“ erwartet, aber die Instanzen des Gruppenmodells wurden übergeben, was zu einem schwerwiegenden Fehler führte.
Kundengruppen können jetzt erfolgreich über das Repository gespeichert werden, indem eine ordnungsgemäße Implementierung der Schnittstelle sichergestellt wird.
Dadurch werden IDE-Warnungen und Laufzeitfehler beim programmgesteuerten Erstellen oder Aktualisieren von Kundengruppen behoben.

_AC-6909 - [GitHub-Problem](https://github.com/magento/magento2/issues/36269)_

#### Validierung von Feldern auf Gutschriften

Fehlerkorrektur - Die Feldüberprüfung auf der Gutschriftenseite verhindert die Übermittlung auch dann, wenn die erforderlichen benutzerdefinierten Felder ausgefüllt wurden.
Jetzt funktioniert die Validierung ordnungsgemäß und die Senden-Schaltfläche wird aktiviert, sobald alle Pflichtfelder ausgefüllt sind.

_AC-8308 - [GitHub-Problem](https://github.com/magento/magento2/issues/37182) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64823f95)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus dem Framework (Teil 3)

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8343 - [GitHub-Problem](https://github.com/magento/magento2/issues/37270) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37020)_

#### [Problem] Verwenden der Konstruktor-Eigenschaftsförderung im Modul „Freund senden“ in GraphQL

Das System verwendet jetzt die Konstruktoreigenschaftsförderung im GraphQL-Modul „Freund senden“, wodurch die Code-Lesbarkeit verbessert und die Komplexität reduziert wird. Zuvor verwendete das Modul Eigenschaften, die zahlreiche Zeilen belegten, was den Code komplexer und weniger lesbar machte.

_AC-8346 - [GitHub-Problem](https://github.com/magento/magento2/issues/37235) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37197)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8349 - [GitHub-Problem](https://github.com/magento/magento2/issues/37266) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37016)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8350 - [GitHub-Problem](https://github.com/magento/magento2/issues/37265) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37015)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Downloadable`

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8355 - [GitHub-Problem](https://github.com/magento/magento2/issues/37251) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37001)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich jetzt an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, was die Code-Qualität und -Konsistenz verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8358 - [GitHub-Problem](https://github.com/magento/magento2/issues/37264) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37014)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8359 - [GitHub-Problem](https://github.com/magento/magento2/issues/37262) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37012)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich jetzt an die Codierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, was die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8360 - [GitHub-Problem](https://github.com/magento/magento2/issues/37261) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37011)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um einen saubereren und standardisierten Code zu gewährleisten. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8361 - [GitHub-Problem](https://github.com/magento/magento2/issues/37260) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37010)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8362 - [GitHub-Problem](https://github.com/magento/magento2/issues/37259) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37009)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8363 - [GitHub-Problem](https://github.com/magento/magento2/issues/37258) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37008)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Backup` und `Magento_Bundle`

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8367 - [GitHub-Problem](https://github.com/magento/magento2/issues/37244) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36979)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8375 - [GitHub-Problem](https://github.com/magento/magento2/issues/37257) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37007)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8376 - [GitHub-Problem](https://github.com/magento/magento2/issues/37256) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37006)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8400 - [GitHub-Problem](https://github.com/magento/magento2/issues/37254) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37004)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8401 - [GitHub-Problem](https://github.com/magento/magento2/issues/37255) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37005)_

#### [Problem] Verbessern der Erweiterbarkeit der Service-URL-Generierung

Das System ermöglicht jetzt die Anpassung der Service-URL-Generierungsfunktion über Plug-ins, wodurch ein besser wartbarer Ansatz für Änderungen gefördert wird. Zuvor wurde die Anpassung dieser Funktion durch Voreinstellungen erreicht, die möglicherweise nicht so effizient oder wartbar waren.

_AC-8813 - [GitHub-Problem](https://github.com/magento/magento2/issues/37404) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37403)_

#### [Problem] Variablennamen in der Katalogsuche beheben

Das System benennt nun Variablen im Suchmodul korrekt, was die Code-Klarheit und die Wartbarkeit verbessert. Zuvor wurde ein irrelevanter Variablenname, $defaultCountry, im Suchmodul verwendet, was zu Verwirrung führte.

_AC-9215 - [GitHub-Problem](https://github.com/magento/magento2/issues/37810) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation sollte über die Umgebungsvariable festgelegt werden

Nach der Fehlerbehebung kann die Umgebungsvariable &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION“ verwendet werden, um die Konfiguration „allow_parallel_generation“ festzulegen.

_ACP2E-3673 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] Das Ändern des Tabellenspaltentyps mithilfe der Datei „db_schema.xml“ in Magento 2 führt zu Fehlern

Das Ändern des Spalten-Datentyps funktioniert nicht ordnungsgemäß. Zuvor wird ein Fehler ausgegeben: Das Attribut „identity“ ist nicht zulässig.

_ACP2E-3709 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Unterstützung neuer Währungen (XCG) in Adobe

Caribbean Gulder (XCG) wird der Liste der Währungen hinzugefügt.

_ACP2E-3790 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Problem mit dem Upgrade 2.4.7-p5 aufgrund einer hinzugefügten neuen Validierung

Es wurde ein Problem in der SchemaBuilder-Klasse behoben, bei dem eine nicht definierte Array-Schlüssel-„Spalte“ während der Schemaerstellung oder -aktualisierungen einen Absturz verursachte. Dies trat bei der Verarbeitung von Tabellendaten auf, die keinen Schlüssel „Spalte“ enthielten.

_ACP2E-3871 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]Server-Problem, das möglicherweise durch einen ungültigen S3-Zugriffsschlüssel verursacht wird

Falsche AWS S3-Anmeldeinformationen führen nicht mehr dazu, dass Seiten unendlich in der Storefront geladen werden.

_ACP2E-3890 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify funktioniert nicht

Die folgenden JS-Dateien werden jetzt vollständig und korrekt minimiert, wenn die JS-Minimierung aktiviert ist: mage/backend/tabs.min.j, jquery/jquery.validate.min.js und Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Daher funktioniert die CSS-Klassenfeldüberprüfung von Page Builder erwartungsgemäß.

_ACP2E-3925 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4 Veraltungsfehler: E_USER_ERROR nach der Aktualisierung auf Adobe Commerce 2.4.8

*ES SIND KEINE VERSIONSHINWEISE ERFORDERLICH*
Kundenorientierte Szenarien sind von der Fehlerbehebung nicht betroffen.

_ACP2E-3963 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron-Vorgang löscht die Datenbanktabelle nicht - verursacht Ausfall wegen Galera-Absturz

Die Bereinigung von Änderungsprotokolltabellen wird jetzt in Batches ausgeführt, um umfangreiche Löschvorgänge zu vermeiden.

_ACP2E-3995 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### Nicht minimierte JS lädt manchmal unter Ignorierung von „js-Minimierungen aktivieren“.

Vor der Fehlerbehebung wurden einige JS-Dateien ohne das Präfix „min“ angefordert, auch wenn Sie die Minimierung aktiviert hatten, was zu einem 404-Status-Code führte. Nach der Behebung werden bei aktivierter Minimierung keine nicht minimierten JS-Ressourcen angefordert.

_ACP2E-4058 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Datumsattribut in benutzerdefinierter Attributgruppe kann Datumsauswahl in Admin nicht anzeigen

Es wurde ein Problem behoben, bei dem das Kalender-Popup für Datumsattribute außerhalb des Bildschirms angezeigt wurde, wenn es benutzerdefinierten Attributgruppen zugewiesen wurde.

_ACP2E-4060 - [GitHub-Problem](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Prüfung der ACL-Berechtigung in der Produktion führte zu Leistungsbeeinträchtigung - Engpass ist die Methode „PopulateACL“

Optimierte Verarbeitung von ACL-Regeln

_ACP2E-4114 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98f028ab)_

#### Checkout wird nicht in der neuesten Version mit AC-15867 + ACP2E-4296 und SCD Compact geladen

Vor der Fehlerbehebung konnte es zu Problemen kommen, wenn benutzerdefinierte JavaScripts über den head-Abschnitt geladen wurden. Nach der Einführung der neuen Einstellung können solche Skripte automatisch zurückgestellt werden, um eine bessere Kompatibilität mit dem Magento 2-Framework sicherzustellen.

_ACP2E-4319 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1c547060)_

#### Warnung vor veralteten Elementen: Verwenden Sie moment.updateLocale(localeName, config), um ein vorhandenes Gebietsschema zu ändern. moment.defineLocale(localeName, config)

Vor der Fehlerbehebung wurde in der Browser-Konsole eine veraltete Warnung ausgelöst. Nach der Fehlerbehebung wird nun keine solche Warnung mehr angezeigt.

_ACP2E-4338 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2687b487)_

#### Inkompatibilität mit MariaDB 10.11

Zuvor schlug die Installation der neuesten Magento 2-Version bei der Verwendung von MariaDB 10.11 fehl, was den Abschluss des Einrichtungsprozesses verhinderte. Dieses Problem wurde behoben, indem die Handhabung der Datenbankkompatibilität aktualisiert wurde, um MariaDB 10.11.x während der Installation zu unterstützen.

_ACP2E-4367 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

### Framework, Suche

#### OpenSearch 2.19.1 Illegal_Argument_Exception auf Einpreiskategorien

OpenSearch löst für die Kategorien, die alle Produkte mit demselben Preis enthalten, kein Illegal_Argument_Exception mehr aus. Zuvor hatte sie die Ausnahme &quot;[from] Parameter darf nicht negativ sein“.

_ACP2E-3896 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Die Bestellung in GraphQL ist mit einer ungültigen Versandmethode erfolgreich

Es wurde ein Problem behoben, bei dem Bestellungen über GraphQL mit einer deaktivierten oder ungültigen Versandmethode aufgegeben werden konnten.
Jetzt validiert das System die ausgewählte Versandmethode und gibt einen Fehler zurück, wenn sie nicht verfügbar ist. Dadurch wird verhindert, dass die Bestellung erstellt wird.

_AC-10472 - [GitHub-Code-](https://github.com/magento/magento2/pull/38268) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Ausnahme, die beim Ausführen einer GraphQL-Abfrage ausgelöst wird

Es wurde ein Problem behoben, bei dem eine GraphQL-Abfrage aufgrund eines ungültigen Sortierparameters eine Ausnahme auslöste. Nach der Behebung wird die Abfrage erfolgreich ausgeführt, ohne Fehler oder Ausnahmeprotokolle zu generieren.

_AC-14835 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Interner Server-Fehler beim Hinzufügen eines Geschenkkartenprodukts zum Warenkorb über die AddProductsToCart-Mutation einschließlich custom_attributesV2

Es wurde ein interner Server-Fehler behoben, der beim Hinzufügen von Geschenkgutscheinprodukten (und ähnlichen Produkten mit benutzerdefinierter Option) zum Warenkorb über GraphQL mit custom_attributesV2 ausgelöst wurde. Die Korrektur verarbeitet komplexe Attributwerte ordnungsgemäß, sodass Produkte ohne Fehler hinzugefügt werden können.

_AC-15856 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7fa400a7)_

#### Null-Felder in `Country` Abfrage

Es wurde ein Problem behoben, bei dem Aufträge, die virtuelle, zurückerstattete und versandte Artikel enthielten, in der Verarbeitung blieben, indem sichergestellt wurde, dass virtuelle Artikel in die Berechnungen der Versandmenge einbezogen wurden, sodass der Auftragsstatus korrekt auf „Abgeschlossen“ übergehen konnte.

_AC-7731 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### GraphQL-Abfrage „customerOrders“ mit dem Attribut „number“ verursacht internen Server-Fehler

Es wurde ein Problem behoben, bei dem die Abfrage &quot;GraphQL customerOrders“ beim Anfordern des Zahlenfelds einen internen Server-Fehler zurückgab.
Jetzt gibt der Resolver korrekt die ID des Bestellinkrements zurück, sodass die Abfrage erfolgreich ausgeführt und die Bestellnummer abgerufen werden kann.

_AC-8949 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### Die GraphQL-Antwort für die Bestellplatzierung enthält nicht die Ausnahmemeldung

Die vorherige Änderung, die Fehler in einem anderen Format zurückgab, wurde rückgängig gemacht. Jetzt werden potenzielle Fehler konsistent zurückgegeben, sodass das GraphQL-Schema nicht beschädigt wird. Dieser sollte als bekannter BIC hinzugefügt werden, genehmigt von PM hier: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL-Antwort für die Auftragserteilung ist teilweise lokalisiert

Von der placeOrder-GraphQL-Mutation zurückgegebene Fehler wurden nicht vollständig lokalisiert. In einem mehrsprachigen Kontext werden Fehler ordnungsgemäß übersetzt.

_ACP2E-3506 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Gleichzeitige Aufrufe zur Neuanordnung der GraphQL-API - Gleiche Produkte wurden zu verschiedenen Zeilen hinzugefügt

Es wurde ein Problem behoben, bei dem gleichzeitige Aufrufe an die GraphQL-API zur Neuanordnung dazu führten, dass dieselben Produkte als verschiedene Zeilen hinzugefügt wurden, was zu Dateninkonsistenzen führte.

_ACP2E-3774 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL-Mutation (E-Mail-Adresse ändern) verursacht keinen Trigger in der E-Mail-Benachrichtigung

Zuvor wurde keine E-Mail an Kunden gesendet, nachdem diese ihre E-Mail-Adressen in ihren Konten erfolgreich aktualisiert hatten. Nachdem die Fehlerbehebung angewendet wurde, erhalten Kunden jetzt E-Mail-Benachrichtigungen, nachdem sie ihre E-Mail-Adressen erfolgreich aktualisiert haben.

_ACP2E-3785 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Dynamisches Attribut wird in der Geschenkregistrierung nicht über die UpdateGiftRegistry-Mutation aktualisiert

Vor dieser Korrektur durch die UpdateGiftRegistry-Mutation wurde das benutzerdefinierte Attribut der Geschenkregistrierung nicht durch GraphQL-Mutationen geändert oder aktualisiert. Nachdem diese Fehlerbehebung angewendet wurde, kann das dynamische Attribut der Geschenkregistrierung erfolgreich durch die UpdateGiftRegistry-Mutation aktualisiert werden.

_ACP2E-3805 - [GitHub-Problem](https://mcstaging.briscoes.co.nz/)_

#### Kundenauftrag - GraphQL : Das Abrufen von Produktkategorien für das zugehörige Produkt ist „nicht einzeln sichtbar

Vor der Fehlerbehebung wurde in der GraphQL-Antwort der Kundenbestellung ein leeres -Array angezeigt, wenn die Bestellung ein ausgeblendetes Produkt enthielt.
Nach der Fehlerbehebung werden die Produktkategorien jetzt in die Antwort auf eine GraphQL-Anfrage zur Kundenbestellung aufgenommen, auch wenn das Produkt ausgeblendet ist.

_ACP2E-3945 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Artikel auf der Wunschliste werden in GraphQL-Anfragen nicht zwischen Storeansichten innerhalb einer Website geteilt

Vor der Fehlerbehebung wurden Wunschlistenelemente nach Store-ID gefiltert. Nach der Fehlerbehebung werden jetzt die Elemente der Wunschliste nach Website gefiltert.

_ACP2E-3987 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud] getRemoteAddress - 127.0.0.1 in der Produktion

Vor dieser Fehlerbehebung wurde die Remote-Adresse bei Verwendung des Anwendungsservers nicht korrekt ermittelt. Nach der Fehlerbehebung wird die Remote-Adresse korrekt bestimmt, kombiniert mit der richtigen Header-Einrichtung in der nginx- und Header-Konfiguration.

_ACP2E-3991 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] Verhaltensrückkehr bei Ausnahmebehandlung bei GQL-Auftragsplatzierung bestätigen

Adressierte rückwärts inkompatible Änderung für die placeOrder-Mutation.

_ACP2E-4031 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### Problem-Mapping übersetzte Nachricht zu Fehler-Code bei Bestellung über GraphQL

Fehlerkorrektur - Jetzt tritt kein Fehler mehr auf, wenn die übersetzte Ausnahmemeldung verwendet wird, um den Fehlercode für GraphQL-Anfragen zuzuordnen, was zu unbekannten Fehler-Codes führt.

_ACP2E-4033 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fab20b00)_

#### [CLOUD] Kundenauftragsfilter funktioniert nicht für Datumsangaben

Nach der Fehlerbehebung wird beim Abrufen von Bestellungen über GraphQL mithilfe eines Datumsbereichsfilters das richtige Ergebnis zurückgegeben.

_ACP2E-4090 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Behebung der in ACP2E-4031 aufgeworfenen Probleme

Vor der Behebung bot die Position des Fehlerknotens keine nahtlose Kompatibilität mit den Versionen 2.4.7 und 2.4.9. Nach der Fehlerbehebung wird der Fehlerknoten ordnungsgemäß platziert, um beide Versionen zu berücksichtigen.

_ACP2E-4115 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

#### Das übergeordnete Paket wird nicht vorrätig angezeigt, selbst wenn das untergeordnete Element in einem GraphQL-Aufruf vorrätig ist.

Nach der Fehlerbehebung wird durch die Anforderung einer Produktliste mit GraphQL der richtige Lagerstatus für Bundle-Produkte zurückgegeben.

_ACP2E-4168 - [GitHub-Code-](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### GraphQL-Ausnahmefehler in SWAT

Nach der Fehlerbehebung werden die Antworten für GraphQL-Anfragen mit den GraphQL über HTTP-Spezifikationen abgestimmt. Ein 4XX-Antwort-Code wird zurückgegeben, wenn es unmöglich ist, die Anfrage zu parsen, die Anfrage nicht autorisiert ist oder ein anderes allgemeines Problem mit der Anfrage vorliegt. Wenn die Anfrage geparst wird und verarbeitet werden kann, wird ein Antwort-Code von 200 zurückgegeben.

_ACP2E-4194 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Produkt wird nicht aus der Vergleichsliste entfernt, nachdem die Liste dem Kunden zugewiesen wurde

Nachdem die Vergleichsliste eines Gastbenutzers einem Kundenkonto zugewiesen wurde, können als Gast hinzugefügte Produkte jetzt vom Kunden entfernt werden.
Zuvor schlugen Entfernungsvorgänge fehl, da die vom Gast hinzugefügten Elemente nach der Zuweisung nicht ordnungsgemäß mit dem Konto des Kunden verknüpft waren.

_ACP2E-4244 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### Falsche Fehlerantwort bei updateCartItems-GraphQL

Zuvor wurde bei einer GraphQL-Anfrage für einen Artikel mit unzureichender Menge eine korrekte Fehlermeldung mit einem Fehlercode sowie die Berechnung der angeforderten Menge und des angeforderten Preises zurückgegeben, auch wenn der Artikel nicht verfügbar war. Nachdem diese Fehlerbehebung angewendet wurde, wird jetzt eine korrekte Fehlermeldung mit einem Fehlercode zurückgegeben, und die Menge des Elements wird auf seinen alten Wert festgelegt, wenn es nicht in der Antwort verfügbar ist.

_ACP2E-4283 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cbca0396)_

#### Fehler bei der Website-übergreifenden Zuweisung von Gastaufträgen im MergeGuestOrder-Plug-in

Vor der Fehlerbehebung hat eine Kundenzuweisung für einen Gastauftrag keine Optionen zur Kontofreigabe in Betracht gezogen. Nach der Fehlerbehebung wird nun eine Bestellung einem Kunden zugewiesen, wenn Kunde und Bestellspeicher übereinstimmen (angesichts der Tatsache, dass die Option zur Freigabe des Kundenkontos auf „Pro Website“ festgelegt ist).

_ACP2E-4312 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, Inventar/MSI

#### Problem mit only_x_left_in_stock in Magento 2 GraphQL - Falsche Berechnung bei Verwendung von Schwellenwerten

Es wurde ein Problem behoben, bei dem das GraphQL-Feld only_x_left_in_stock aufgrund eines falschen doppelten Abzugs von MinQty null zurückgab. Die Berechnung wurde korrigiert, sodass nun der genaue Lagerwert basierend auf Schwellenwerten zurückgegeben wird.

_AC-15832 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/35458c7f)_

#### Diskrepanzen bei GraphQL mergeCart-Mutation

Nach der Fehlerbehebung überprüft die GraphQL-Anfrage zum Zusammenführen von Warenkörben ordnungsgemäß die Produktmenge, wobei die Lagerkonfiguration berücksichtigt wird.

_ACP2E-4184 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Produkt

#### Fehlender media_type in MediaGalleryInterface in Produktgraphql

Die GraphQL-Anfrage von MediaGallery enthält jetzt das Feld „Typen“ für Produktbildtypen. Zuvor war dieses Feld „Typen“ in der MediaGallery-GraphQL-Anfrage nicht vorhanden.

_ACP2E-3880 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, Sicherheit

#### Das Zurücksetzen des Kundenkennworts über GraphQL berücksichtigt nicht die Einschränkungen.

Es wurde ein Problem behoben, bei dem Anfragen zum Zurücksetzen des Kundenkennworts, die durch GraphQL-Mutationen gesendet wurden, nicht den Kennwortrücksetzungsbeschränkungen entsprachen, die unter Store > Configuration > Customers > Customer Configuration > Password Options konfiguriert wurden. Diese Einstellungen werden nun korrekt durchgesetzt.

_ACP2E-3992 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### Import/Export

#### [Problem] Parametertyp beheben

Fehlerkorrektur - Der Parametertyp stimmt im Import/Export-Modul nicht mehr überein, wenn ein zuvor als Zeichenfolge definierter Wert jetzt korrekt als Array festgelegt wird. Dies entspricht den erwarteten Eingaben vom Export-Controller und verhindert statische Analysewarnungen.

_AC-11665 - [GitHub-Problem](https://github.com/magento/magento2/issues/38529) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64823f95)_

#### [Problem] Copyedit: „Kopieren“ in „Kopieren“ ändern

PR repariert die Nebenversion, um die Schreibweise von „Kopieren“ zu korrigieren

_AC-13300 - [GitHub-Problem](https://github.com/magento/magento2/issues/39311) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39307)_

#### REST-Endpunkt - Produktimport-JSON validiert die Pflichtfelder nicht

Das Namensfeld ist jetzt beim Erstellen neuer Produkte über den Importprozess (Admin oder API) erforderlich. Vor der Fehlerbehebung hätten Sie neue Produkte ohne Namen erstellen können. Dies hätte die Admin-Benutzeroberfläche beschädigt und ungültige Produkte erstellt.

_ACP2E-3660 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Fehlende Website-Filteroption im Exportprozess

Es ist jetzt möglich, Produkte beim Erstellen von Exportprodukten nach Websites zu filtern.

_ACP2E-3720 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplikat von AC-13913 - Asynchrone Bereinigung statischer Attribute.

Nach der Fehlerbehebung tritt kein Fehler „Undefined Array key „apply_to“ auf, wenn zahlreiche Instanzen von \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType erstellt werden.

_ACP2E-3752 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

#### CSV-Produktimport : Ein Musterbild kann nicht aufgehoben werden

Vor der Fehlerbehebung konnten Sie das Musterbild eines Produkts nicht durch den Produktimport aktualisieren. Wenn Sie nach der Korrektur die Spalte für das Produktmuster-Bild mit der konfigurierten leeren Markierung markieren, wird das Bild auf „Ausgeblendet“ gesetzt.

_ACP2E-3972 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Produktimport generiert leere URLs für den Store-Umfang

Produkt-URL-Schlüssel in der Store-Ansicht übernimmt jetzt den im Standardbereich festgelegten Wert, wenn url_key in der Import-Datenquelle einen leeren Wert hat. Zuvor führte das Festlegen von url_key auf einen leeren Wert in der Importdatenquelle für einen Store-Ansichtsdatensatz dazu, dass url_key mit einem leeren Wert in diesem Bereich überschrieben wurde.

_ACP2E-4038 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### Beim Produktimport tritt ein Fehler auf, wenn ein Attribut mit mehreren Auswahlmöglichkeiten wie erforderlich konfiguriert ist

Es wurde ein Problem behoben, bei dem Produktimporte fehlschlugen, wenn ein erforderliches Attribut vom Typ Mehrfachauswahl enthalten war. Die Datenvalidierung wird jetzt korrekt durchgeführt, sodass der Produktimport erfolgreich abgeschlossen werden kann.

_ACP2E-4057 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Produkte, bei denen keine Nachbestellungen für „Lager verwalten“ ausgewählt wurden, ermöglichen es Kunden, beim Import weiterhin über unsere Lagerbestände zu bestellen

Nach der Korrektur ist es nicht mehr möglich, einen inakzeptablen Wert für das Attribut „allow_backorders“ des Produkts zu importieren.

_ACP2E-4116 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Produktimport schlägt fehl aufgrund einer Beschreibungslänge von mehr als 65.536 Zeichen. Validierung

Nach der Korrektur ist es möglich, Produktattribute mit dem Typ Text zu importieren, deren Werte 65.536 Zeichen überschreiten.

_ACP2E-4119 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Exportfilter für Produktattribute Ja Nein Funktioniert nicht erwartungsgemäß

Nach der Fehlerbehebung enthalten exportierte Produkte, die nach dem Attribut Ja/Nein gefiltert wurden, die erwarteten Produkte, die die angewendeten Filter berücksichtigen.

_ACP2E-4160 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### Problem mit dem Optionspreis des Aktualisierungspakets pro Website über den Import

Es ist jetzt möglich, Paketoptionspreise pro Website zu exportieren und zu importieren

_ACP2E-4243 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/98f028ab)_

#### Kunde mit einer E-Mail-Adresse in Großbuchstaben kann nicht importiert werden

Fehlerkorrektur - Beim Importieren von Kunden mit E-Mails in Großbuchstaben tritt jetzt kein undefinierter Array-Schlüsselfehler mehr auf, wenn die Kontofreigabe auf „global“ eingestellt ist. Die E-Mail-Normalisierung ist jetzt während des gesamten Importvorgangs konsistent, sodass Kunden unabhängig von der E-Mail-Groß-/Kleinschreibung importiert werden können. Das Verhalten bei der Kontofreigabe auf Website-Ebene bleibt unverändert.

_ACP2E-4373 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

### Import/Export, Kunde/Kunden

#### Der Administrator kann einen Kunden importieren, dessen Geburtsdatum nach dem aktuellen Datum liegt.

Es wurde ein Problem behoben, bei dem Administratoren Kunden importieren konnten, deren Geburtsdatum in der Zukunft festgelegt wurde. Das System validiert jetzt das Geburtsdatum während des Imports, zeigt einen Fehler bei ungültigen Datensätzen an und verhindert den Import zukünftiger Geburtsdaten, wodurch genaue Kundendaten sichergestellt werden.

_AC-13641 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

### Inventar/MSI

#### Store-Abholung berücksichtigt nicht den maximalen Suchradius, wenn Adresse an der Kasse geändert wird

Jetzt wird der vorausgewählte Store in „Pick-in-Store“ aktualisiert, wenn sich die Versandadresse ändert. Zuvor hat sich ein zuvor ausgewählter Store nicht geändert, auch wenn sich die neue Versandadresse nicht im Radius des ausgewählten Stores befindet

_ACP2E-3728 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/07620383)_

#### Nach der Umleitung zur Startseite und dem Checkout ist kein Store verfügbar

Zuvor ausgewählter Store wird jetzt im Versand „Pick-in-Store“ vorausgewählt, wenn der Kunde zur Zahlungsseite navigiert, dann zur Startseite zurückkehrt und schließlich zur Checkout-Seite zurückkehrt. Zuvor wurde nach wiederholter Rückkehr zur Kaufbestätigungsseite der ausgewählte Store im „Pick-in-Store“ gelöscht.

_ACP2E-3793 - [GitHub-Code-](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/62c0d79b)_

#### Stock-Löschvorgang wird nicht abgeschlossen

Nach der Behebung führt das Löschen eines Quellelements nicht zu einer vollständigen Neuindizierung und aktualisiert nur die betroffenen Produkte, was die Leistung erhöht.

_ACP2E-3917 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] Keine Angabe in Admin, ob der Kunde asynchron über „Bestellung ist abholbereit“ benachrichtigt wurde.

Dem Auftragsverlauf wurde eine Benachrichtigung über den Kunden hinzugefügt, der asynchron darüber benachrichtigt wurde, dass die Bestellung abholbereit ist.

_ACP2E-3968 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/29653b1d)_

#### Duplizierte Bestandsstatusabfragen beim Laden des Angebots

Fehlerkorrektur - Die doppelte Ausführung der Abfrage catalogInventory_stock_status beim Laden eines Angebots in der Storefront wurde korrigiert, was zu redundanten DB-Aufrufen führte.

_ACP2E-4102 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/fc15a9ae)_

#### Post-Patch ACP2E-4118: Änderung des Lagerschwellenwerts in Admin verursacht negative Verkaufsmengen und Lagerstatus-Inkongruenzen

Der Lagerstatus wird jetzt automatisch angepasst, wenn globale Lagerkonfigurationen wie Menge, Rückstände und Schwellenwert für nicht vorrätige Artikel über den Import aktualisiert werden.

_ACP2E-4142 - [GitHub-Code-](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### [CLOUD] Admin-Bericht zeigt keine Details an, wenn der Bestand aktualisiert wird

Änderungen an der Produktinventarquelle werden jetzt vom Protokollierungsmodul protokolliert. Vor der Fehlerbehebung wurden beim Speichern eines Produkts und Durchführen inventarbezogener Änderungen keine Details protokolliert.

_ACP2E-4167 - [GitHub-Code-](https://github.com/magento/magento2/commit/cbca0396) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/76b88f7c)_

#### Bundle-Produkt kann nicht in den Warenkorb gelegt werden, während es als auf Lager markiert ist

Der Status des Produktpakets spiegelt jetzt korrekt die Reservierungen untergeordneter Produkte und die Schwellenwerte für nicht vorrätige Produkte wider.
Zuvor wurden Bundle-Produkte als „auf Lager“ gekennzeichnet, auch wenn einem oder mehreren untergeordneten Produkten eine ausreichende Verkaufsmenge fehlte. Dies führte zu Fehlern bei „Nicht genügend Artikel zum Verkauf“ beim Hinzufügen des Bundles zum Warenkorb.

_ACP2E-4220 - [GitHub-Code-](https://github.com/magento/magento2/commit/cbca0396) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/76b88f7c)_

#### Das gruppierte Produkt wird in der PDP nach dem Import aus CSV falsch als Nicht vorrätig angezeigt, wenn ein untergeordnetes Element einer benutzerdefinierten Quelle/einem benutzerdefinierten Lager zugewiesen wird (nach der manuellen Neuindizierung korrigiert)

Nach der Fehlerbehebung wird beim Erstellen eines zusammengesetzten Produkts mithilfe von Import automatisch eine Neuindizierung des Bestands durchgeführt, sodass das Produkt verfügbar wird, ohne dass eine manuelle Neuindizierung erforderlich ist.

_ACP2E-4233 - [GitHub-Code-](https://github.com/magento/magento2/commit/98f028ab) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] Fehlgeschlagene MFTF-Tests im Zusammenhang mit den neuesten Mainline-Änderungen.

Bevor der Fehler behoben wurde, wurde die Rechnungsadresse von Gastkunden, die sich für In-Store-Abholung ohne Versandadresse entschieden, automatisch mit der Adresse des Geschäfts ausgefüllt, die nicht geändert werden konnte, was zu falschen Rechnungsdetails führte. In diesem Szenario kann die Rechnungsadresse nach der Fehlerbehebung bearbeitet werden, sodass die Gäste ihre eigenen Details eingeben können. Registrierte Benutzer sehen ihre gespeicherte Rechnungsadresse anstelle der des Shops.

_ACP2E-4260 - [GitHub-Code-](https://github.com/magento/magento2/commit/ab891304) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/13e432a6)_

#### Falsche Inventarreservierung für virtuelle Geschenkkarten erstellt

Vor der Implementierung dieser Fehlerbehebung wurde die Menge einer virtuellen Geschenkkarte, die mehrere Artikel enthielt, in der Lagerreservierung nicht genau wiedergegeben. Nach Anwendung der Fixierung wurden jedoch die Lagerreservierung und die Lagerbestände synchronisiert.

_ACP2E-4267 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5704166a)_

#### Ausgleichsbefehl für Lagerreservierung schlägt mit null und nicht vorhandenen Produktverweisen fehl

Es wurde ein Problem behoben, bei dem die CLI für die Ausgleichszahlung für Lagerreservierungen eine Ausnahme auslöste, wenn die verarbeitete Kombination eine fehlende Auftrags-ID hatte

_ACP2E-4301 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/76b88f7c)_

#### Produkt ist nach Änderung des SKU-Falls nicht vorrätig

Wenn Sie den SKU-Fall ändern, ist das Produkt in der Storefront nicht mehr vorrätig.

_ACP2E-4375 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/0836c2ed)_

#### Bestellung nach Preis/Preisfacetten mit ungültigen Daten

Vor der Fixierung wurden die Paketpreise nicht richtig indiziert, wenn untergeordnete Produkte unter Zollquellen vorrätig waren. Jetzt, nach der Fehlerbehebung, werden die Paketpreise ordnungsgemäß indiziert, unabhängig von der Zuordnung der untergeordneten Produktbestände.

_ACP2E-4380 - [GitHub-Code-](https://github.com/magento/magento2/commit/1c547060) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/1f83ed24)_

### Reihenfolge

#### AbstractAddress(setData(&#39;custom_attributes&#39;, AttributeValue[]) bricht customAttributes

Benutzerdefinierte Attribute für Adressen werden jetzt beim Checkout und bei API-Vorgängen korrekt verarbeitet.
Zuvor konnte die Verwendung von $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) die Behandlung benutzerdefinierter Attribute beschädigen, was dazu führte, dass Attributwerte falsch strukturiert waren.
10568

_AC-10568 - [GitHub-Problem](https://github.com/magento/magento2/issues/31644)_

#### Wenn der Kunde für die Angebotsbestellung eingestellt ist, ist dies noch eine Gastbestellung

_AC-11689 - [GitHub-Problem](https://github.com/magento/magento2/issues/38540)_

#### Die Bestellung ist beim Mischen von virtuellen, zurückerstatteten und versendeten Artikeln nicht abgeschlossen

Es wurde ein Problem behoben, bei dem Aufträge, die virtuelle, zurückerstattete und versandte Artikel enthielten, in der Verarbeitung blieben, indem sichergestellt wurde, dass virtuelle Artikel in die Berechnungen der Versandmenge einbezogen wurden, sodass der Auftragsstatus korrekt auf „Abgeschlossen“ übergehen konnte.

_AC-11691 - [GitHub-Problem](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento-Neuanordnung -1 Bestellnummern

Das System funktioniert wie erwartet und nach der Neuanordnung über das Backend wird die Bestellnummer eindeutig 8 Stellen sein

_AC-12854 - [GitHub-Problem](https://github.com/magento/magento2/issues/39089) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39399)_

#### Verlust des Uploads der benutzerdefinierten Optionsdatei für das Produkt beim Auschecken mit der Kreditkartenzahlungsmethode von Adobe

Uploads von benutzerdefinierten Optionsdateien für Produkte werden jetzt beim Auschecken mit der Kreditkartenzahlungsmethode von Adobe beibehalten.
Zuvor gingen Datei-Uploads bei Verwendung dieser Zahlungsmethode verloren, funktionierten aber mit anderen.
14306

_AC-14306 - [GitHub-Problem](https://github.com/magento/magento2/issues/39647)_

#### Administratoraufträge - Suche nach Will nicht möglich

Es wurde ein Problem behoben, bei dem bei der Suche nach Bestellungen anhand des Kundennamens (z. B. „Wird„) im Admin-Bestellraster keine Ergebnisse zurückgegeben wurden. Nach der Fehlerbehebung werden relevante Bestellungen korrekt angezeigt, wenn sie nach Kundenname gefiltert werden.

_AC-14360 - [GitHub-Problem](https://github.com/magento/magento2/issues/36596) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - Order items order_date falsch formatiert

Es wurde ein Problem behoben, bei dem das Feld order_date in der GraphQL-Antwort im Format JJJJ-MM-TT zurückgegeben wurde.
Jetzt wird das Datum order_date korrekt im Format TT-MM-JJJJ angezeigt.

_AC-14431 - [GitHub-Problem](https://github.com/magento/magento2/issues/39805) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Für ein unerwartetes Problem im Feld \„AppliedCoupon.code\&quot;, das keine NULL-Werte zulässt, kann nicht null zurückgegeben werden

Adobe Commerce gibt jetzt bei der Abfrage von Kundenbestellungen angewendete Couponcodes über GraphQL korrekt zurück. Zuvor konnte in Adobe Commerce 2.4.8 das Abrufen einer Bestellung mit dem Feld applied_coupons.code (z. B. über die Abfrage customer.orders) mit einem internen Server-Fehler fehlschlagen und die Meldung „Cannot return null for non-nullable field „AppliedCoupon.code“ (Keine Nullwerte für Feld „AppliedCoupon.code„) und applied_coupons wurde als [null] anstelle einer Liste mit dem Couponcode zurückgegeben. 14484

_AC-14484 - [GitHub-Problem](https://github.com/magento/magento2/issues/39841) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/97b2ea42)_

#### Die Versand-E-Mail wird nicht gesendet, wenn sie über die Administrator-Bestellansicht gesendet wird, obwohl sie in der Store-Konfiguration aktiviert ist.

Das System sendet jetzt eine E-Mail zur Versandbestätigung, da sie in der Store-Konfiguration aktiviert ist, in der die Bestellung aufgegeben wurde.

_AC-14563 - [GitHub-Problem](https://github.com/magento/magento2/issues/39861) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39897)_

#### Das Filtern nach Datum funktioniert aufgrund mehrdeutiger Feldnamen nicht

In Magento 2.4.7-p6 wurde berichtet, dass das Filtern des Sortierungsrasters nach Datum einen Fehler aufgrund von Joins mit Braintree-Modulen verursacht.
Das Problem bestand darin, dass Abfragen beim Anwenden von Datumsfiltern die Tabellen braintree_transaction_details und sales_order schlossen.
Adobe Commerce Engineering hat den Fall geprüft, konnte den Fehler jedoch nicht in der Umgebung reproduzieren.
Erwartetes Verhalten ist, dass bei der Filterung nach Datum Bestellungen zurückgegeben werden sollten, die mit dem Filter übereinstimmen, ohne dass Fehler auftreten.

_AC-15037 - [GitHub-Problem](https://github.com/magento/magento2/issues/40024)_

#### Die Bestellerstellung in BackOffice mit mehreren Produkten, von denen mindestens eines benutzerdefinierte Optionen enthält, führt dazu, dass unerwünschte zusätzliche Produkte zur Bestellung hinzugefügt werden

Es wurde ein Problem behoben, bei dem das Erstellen einer Bestellung im Back-Office mit mehreren Produkten, einschließlich eines mit benutzerdefinierten Optionen, unbeabsichtigt zusätzliche Produkte hinzufügte und Fehler verursachte. Das System fügt jetzt nur noch die ausgewählten Produkte hinzu, sodass Bestellungen ohne unerwartete Artikel erstellt werden können.

_AC-15286 - [GitHub-Problem](https://github.com/magento/magento2/issues/40122) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: Promotion-Regel kann nicht erstellt werden

Diese PR-Fehlerbehebungen erhalten wir
Modell \Magento\Catalog\Model\ResourceModel\Eav\Attribute anstelle von \Magento\Catalog\Model\ResourceModel\Eav\Attribute in der Methode \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [GitHub-Problem](https://github.com/magento/magento2/issues/12176) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30479)_

#### Magento hat den Entitätstyp $order nach Aufrufen von $bill = $this->_billService->preparationInvoice($order) geändert;

Es wurde ein Problem behoben, durch das beim Bearbeiten einer vorhandenen geplanten Aktualisierung für eine Unterkategorie die Anzahl der untergeordneten Elemente für übergeordnete Kategorien in der Datenbank fälschlicherweise erhöht wurde. Das Problem führte nach dem Speichern von Aktualisierungen zu ungenauen Kategoriehierarchiedaten. Nach der Behebung bleibt die Anzahl der untergeordneten Elemente korrekt und wird nicht mehr unerwartet erhöht.

_AC-15401 - [GitHub-Problem](https://github.com/magento/magento2/issues/40154)_

#### Die Bestellung verbleibt nach dem Versand im Status &#39;Verarbeitung läuft&#39;, wenn Artikel teilweise zurückerstattet werden

Es wurde ein Problem behoben, bei dem Bestellungen im Status Verarbeitung läuft blieben, nachdem Artikel teilweise zurückerstattet und der Rest versendet wurde. Der Bestellstatus wird jetzt korrekt auf „Abgeschlossen“ aktualisiert, sobald die gesamten versandten und rückerstatteten Mengen mit der fakturierten Menge übereinstimmen, was eine genaue Verwaltung des Auftragslebenszyklus gewährleistet.

_AC-15419 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### Das Senden einer Verkaufs-E-Mail über das Backend ist immer erfolgreich - auch wenn es deaktiviert ist

Fehlerkorrektur - Die E-Mail-Benachrichtigung zum Verkauf im Backend zeigt jetzt keine korrekten Nachrichten mehr an, indem das E-Mail-Service-Ergebnis validiert wird. So wird sichergestellt, dass Benutzer informiert werden, wenn Bestell- oder Rechnungs-E-Mails deaktiviert und nicht gesendet werden.

_AC-16059 - [GitHub-Problem](https://github.com/magento/magento2/issues/40309) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Benutzerdefinierter Preis von 0 wird bei der Neubestellung auf den ursprünglichen Preis zurückgesetzt.

Es wurde ein Problem behoben, bei dem Produkte mit einem benutzerdefinierten Preis von 0 während der Neubestellung auf ihren ursprünglichen Preis zurückgesetzt wurden.
Jetzt wird der benutzerdefinierte Preis korrekt beibehalten, was eine genaue Preisgestaltung bei der Neubestellung von Artikeln gewährleistet.

_AC-8147 - [GitHub-Problem](https://github.com/magento/magento2/issues/36970) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Bestellung mit deaktivierter Zahlungsmethode aufgeben

Fehlerkorrektur - Bestellungen können jetzt über GraphQL mit einer deaktivierten Zahlungsmethode aufgegeben werden.
Jetzt wird beim Versuch, eine nicht verfügbare Zahlungsmethode festzulegen oder zu verwenden, ein Fehler zurückgegeben, der die Erstellung der Bestellung verhindert.

_AC-9605 - [GitHub-Problem](https://github.com/magento/magento2/issues/37983) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Auftragsstatus bei Verarbeitung hängen

Vor der Fehlerbehebung wurde bei der Bestellung eines Produktpakets mit aktivierter Option „Gemeinsam versenden“ der Bestellstatus nach der Rechnung und dem Versand nicht automatisch auf „Abgeschlossen“ geändert. Nach der Fehlerbehebung wechselt der Bestellstatus nun automatisch auf „Abgeschlossen“, nachdem die Bestellung fakturiert und versendet wurde.

_ACP2E-3947 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Vorkonfigurierter Magento-Code - Problem bei der Einrichtung der E-Mail-Vorlage

Vor der Fehlerbehebung waren bei der Verwendung des asynchronen E-Mail-Versands die Versand-E-Mails nicht mit der Bestellung im Store konsistent. Nach der Fehlerbehebung wird nun die richtige E-Mail-Bestellung für die Ladenlieferung zugestellt.

_ACP2E-3998 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

#### Rechnungsumleitungen stornieren auf 404

Die Stornierung der Rechnung, die mit dem Nicht-Erfassung-Typ erstellt wurde, führt nicht mehr zu Seite 404.

_ACP2E-4001 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Problem mit aktualisierten Bestellungen mit konfigurierbaren Optionen unter Verwendung der REST-API

Vorhandene Produktoptionen für Kundenauftragselemente beibehalten, wenn eine Bestellung über REST-API-Endpunkte aktualisiert wird.

_ACP2E-4061 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Asynchrone Verkäufe nach ID-Einfügung begrenzt auf 100 Einträge pro Cron-Durchgang

Verbesserte Verarbeitung des asynchronen Einfügens des Verkaufsrasters. Ein Cron-Durchgang fügt jetzt alle ausstehenden Zeilen in Batches ein, statt strikter 100 pro Durchgang.

_ACP2E-4360 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/31258bf6)_

#### Fehlermeldung „Das Produkt mit der ID „1“ existiert nicht.“ wird wiederholt in „Exception.log“ protokolliert

Vor der Behebung wurden kritische Fehler protokolliert, wenn gelöschte Produkte im Abschnitt Letzte bestellte Artikel gefunden wurden. Nach der Fehlerbehebung können Händler über den Parameter `skipDeletedProductLogging` in di.xml konfigurieren, ob gelöschte Produkte protokolliert oder übersprungen werden sollen. Standardmäßig bleibt das Verhalten aus Gründen der Abwärtskompatibilität unverändert, Händler können den Parameter jedoch auf `true` setzen, um gelöschte Produkte im Hintergrund zu überspringen und Protokollgeräusche zu vermeiden.

_ACP2E-4366 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

#### Doppelbesteuerung der Rückerstattung einer zweiten Gutschrift

Fehlerkorrektur - Die Steuerberechnung in Gutschriften erfolgt jetzt korrekt, wenn eine Teilerstattung aus einer Rechnung erstellt wird, nachdem eine vorherige Gutschrift auf der Seite „Bestellansicht“ erstellt wurde.

_ACP2E-4384 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

### Bestellung, Preise

#### Der Administrator zeigt beim Erstellen der Rücksendung ein falsches Währungssymbol an.

In einem Multi-Website-Setup mit verschiedenen Währungen (EUR/USD/GBP) zeigt die Seite „Produktauswahl zurückgeben“ in „Admin“ jetzt das richtige Währungssymbol an. Zuvor wurde das standardmäßige Währungssymbol angezeigt.

_ACP2E-3658 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

### Reihenfolge, Rückgabe

#### Fehler beim Erstellen einer Gutschrift für die Offline-Rückerstattung

Fehlerkorrektur - Das Erstellen einer Gutschrift für Bundle-Produkte mit der Einstellung Dynamischer Preis = Nein funktioniert jetzt fehlerfrei. Gutschriften können jetzt fehlerfrei erstellt werden.

_ACP2E-4157 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

### Andere Entwickler-Tools

#### [Problem] Falscher Typhinweis für das geschützte Mitglied $_urlHelper

Das System behebt jetzt den falschen Typhinweis mit dem richtigen, der auch im -Konstruktor verwendet wird

_AC-10716 - [GitHub-Problem](https://github.com/magento/magento2/issues/32503) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32496)_

#### [Problem] Nicht verwendeten Code bereinigen.

Das System entfernt jetzt nicht verwendeten Code für die nicht verwendeten Importe.

_AC-10980 - [GitHub-Problem](https://github.com/magento/magento2/issues/38424) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33499)_

#### Lighthouse-Barrierefreiheitsfehler

Das System hat jetzt den Barrierefreiheitswert 100 erreicht

_AC-12783 - [GitHub-Problem](https://github.com/magento/magento2/issues/39054) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39164)_

#### Deaktivieren Sie die Konfiguration der CAPTCHA-Storefont, um weiterhin CAPTCHA-JS-Dateien zu laden

Das System lädt jetzt keine CAPTCHA-JS-Dateien mehr, wenn wir CAPTCHA deaktiviert haben
für Storefont

_AC-14267 - [GitHub-Problem](https://github.com/magento/magento2/issues/32987) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39154)_

#### [Problem] Barrierefreiheit: WAI-ARIA-Rollen verschachteln falsch im Menü

Das System generiert jetzt Lighthouse-Barrierefreiheit ohne WAI-ARIA-Rollen, die im Menüfehler falsch verschachtelt sind, und der Bericht sollte grün sein

_AC-15082 - [GitHub-Problem](https://github.com/magento/magento2/issues/40045) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38617)_

#### Konsolenfehler in der E-Mail-Vorschau im Magento-Admin

Das System gibt bei der Vorschau der E-Mail-Vorlage keinen Konsolenfehler aus

_AC-9245 - [GitHub-Problem](https://github.com/magento/magento2/issues/37820) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37933)_

### Zahlungs-/Zahlungsmethoden

#### PayLater-Nachricht wird beim erfolgreichen Konfigurieren von im Backend nicht in der Storefront angezeigt

Es wurde ein Problem behoben, bei dem die PayPal-Nachricht Später bezahlen trotz der Konfiguration im Backend nicht auf den Seiten Startseite und Warenkorb angezeigt wurde. Das Banner konnte nicht gerendert werden, wenn das Käuferland für Gäste oder Kunden ohne Standardadresse null war. Nach der Fehlerbehebung wird die Nachricht Später bezahlen in der Storefront korrekt angezeigt.

_AC-12335 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/528af81a)_

### Zahlungen

#### [Problem] Offline-Rechnungserfassung beheben (404)

Der 404-Seitenfehler bei der Erfassung von Rechnungen für Offline-Zahlungsmethoden von Magento Admin wurde behoben

_AC-13336 - [GitHub-Problem](https://github.com/magento/magento2/issues/39298) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39297)_

#### Unbekannte IPNs von PayPal missbrauchen Anwendung IPN-Prozessor

Der IPN-Handler ignoriert jetzt nicht unterstützte oder unbekannte IPN-Typen. Anstatt einen 500-Fehler zurückzugeben, wird das Problem protokolliert und die Verarbeitung ohne Unterbrechung fortgesetzt.

_ACP2E-4049 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro gespeichertes Karten-Token bei Zahlung fehlgeschlagen

PayPal PayFlow Pro-Transaktions-IDs (PNREFs) sind jetzt für einen festen Zeitraum von 12 Monaten für die Verwendung in Referenztransaktionen gültig. Nach Ablauf wird die gespeicherte Karte nicht mehr angezeigt und muss erneut hinzugefügt werden. Zuvor wurde die Gültigkeit durch das Ablaufdatum der in der ursprünglichen Transaktion verwendeten Zahlungskarte bestimmt.

_ACP2E-4064 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### Problem mit Vault-Karte bei der Bestellung bei Admin

Eine Bestellung mit gespeicherter Kreditkarte unter einer Website mit einer anderen Zahlungsaktionskonfiguration führt nicht mehr zu einem Fehler oder einem falschen Transaktionstyp

_ACP2E-4270 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] PayflowPro gespeicherte Karte (Vault) letzte 4-stellige Zahl wird in der Reihenfolge nicht angezeigt

Karteninformationen werden jetzt korrekt beibehalten und angezeigt, wenn gespeicherte Karten mit der Aktion „Zahlung an Verkauf“ verwendet werden. Dies entspricht dem Verhalten bei Verwendung der Aktion „Zahlung an Autorisierung“ für PayflowPro.

_ACP2E-4346 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a3b7032)_

### Leistung

#### [Problem] Aktualisieren Sie store.php

Diese PR verbessert die Leistung, indem die aktuelle Speicherauflösung übersprungen wird.

_AC-14791 - [GitHub-Problem](https://github.com/magento/magento2/issues/39949) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38717)_

#### [Problem] Aktualisierung der Cache-Steuerung für statische Site unveränderlich

Diese PR sorgt für eine Leistungsverbesserung, indem sie den statischen Inhalt erst dann beim Laden der Seite validiert, wenn sich der Inhalt geändert hat.

_AC-15171 - [GitHub-Problem](https://github.com/magento/magento2/issues/39486) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39484)_

#### [Problem] Speichern Sie die Ergebnisse von isCache-fähigen Aufrufen, um die Leistung zu verbessern

Diese PR fügt eine Zwischenspeicherung für die Methode isCaching() hinzu, was zum Layout-Rendering-Prozess führt, um redundante Prüfungen zu reduzieren und die Gesamt-Rendering-Leistung der Seite zu verbessern.

_AC-16054 - [GitHub-Problem](https://github.com/magento/magento2/issues/40156) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40112)_

#### [Problem] Geringfügige Leistungsverbesserung der Rasterverarbeitung mit asynchroner Reihenfolge

Diese PR führt eine Leistungsoptimierung für die asynchrone Rasterordnerverarbeitung in Magento ein, indem sie die vorübergehende cachebasierte last_updated_at-Suche durch ein persistentes DB-gestütztes Flag ersetzt, das in der Flag-Tabelle gespeichert ist. Dadurch wird sichergestellt, dass das System den zuletzt verarbeiteten Zeitstempel auch nach Cache-Leerungen oder -Bereitstellungen konsequent beibehält, was unnötige Volltabellen-Scans bei großen Sales_Order-Datensätzen verhindert. Dadurch werden Aktualisierungen des asynchronen Rasters effizienter und vorhersehbarer, insbesondere bei Geschäften mit hohem Volumen und häufiger Bestellaktivität.

_AC-16109 - [GitHub-Problem](https://github.com/magento/magento2/issues/40282) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40271)_

#### [CLOUD] Produkte können nicht zu Kategorien hinzugefügt werden

Verbesserte Leistung beim Hinzufügen von Produkten zur Kategorie über Visual Merchandiser.

_ACP2E-3946 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/29653b1d)_

#### Leistungsproblem bei der Changelog-Bereinigung nach ACP2E-3995

Nach der Fehlerbehebung bereinigt der Cron-Auftrag „indexer_clean_all_changelogs“ die Änderungsprotokolle vollständig, wobei der Batch-Vorgang beibehalten wird.

_ACP2E-4211 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] Der Fastly-Cache funktioniert nicht, nachdem wir auf 2.4.8 aktualisiert haben

Es wurde ein Problem behoben, bei dem zwischenspeicherbare Seiten nicht ordnungsgemäß gespeichert oder aus dem Fastly-Cache bereitgestellt wurden, was zu inkonsistentem Caching-Verhalten und reduzierter Leistung führte.

_ACP2E-4324 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2687b487)_

#### Untersuchen Sie die Gründe für die erhöhte Erstellung von Redis und Cache-Schlüsseln

Vor der Fehlerbehebung waren die für Remote-Speicher-Metadaten verwendeten Cache-Schlüssel nicht abgelaufen. Nach der Behebung können Sie jetzt eine TTL für solche Cache-Schlüssel durch Injektion von Abhängigkeiten festlegen.

_ACP2E-4345 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a3b7032)_

### Preisgestaltung

#### Der Preis ist immer 0 für gebündelte Produktelemente ohne dynamischen Preis in der Auftrags-REST-API

Die Auftrags-REST-API gibt jetzt korrekte Preise für Bundle-Produktelemente ohne dynamischen Preis zurück.
Zuvor wurde beim Exportieren von Bestellungen über die REST-API der Preis für Bundle-Produktelemente ohne dynamische Preisfindung immer als 0 zurückgegeben, anstelle des tatsächlichen Preises, der auf der Bundle-Seite angezeigt wurde.
11925

_AC-11925 - [GitHub-Problem](https://github.com/magento/magento2/issues/38687) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7da46f52)_

#### Falscher Umfang wurde Preisattributen bei der Erstellung zugewiesen

Es wurde ein Problem behoben, bei dem neu erstellte Preisattribute fälschlicherweise dem Bereich „Store-Ansicht“ unabhängig von der Konfiguration zugewiesen wurden. Nach der Fehlerbehebung wird der Attributbereich jetzt standardmäßig mit der Einstellung „Katalogpreisbereich“ (global oder Website) abgestimmt.

_AC-14945 - [GitHub-Problem](https://github.com/magento/magento2/issues/39986) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Das Produkt wird gespeichert, selbst wenn der Sonderpreis ab Datum mithilfe einer Massenaktion nach Bis Datum liegt.

Es wurde ein Problem behoben, bei dem Produkte mit einem ungültigen Datumsbereich für Sonderpreise ohne Validierung gespeichert werden konnten.
Jetzt wird eine Fehlermeldung angezeigt: „Stellen Sie sicher, dass das „Bis“-Datum nach oder mit dem „Von“-Datum übereinstimmt.“

_AC-15252 - [GitHub-Problem](https://github.com/magento/magento2/issues/40113) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Regulärer Preis ist nicht sichtbar, obwohl ein Sonderpreis gilt.

Es wurde ein Problem behoben, bei dem der reguläre Preis nicht angezeigt wurde, wenn ein Sonderpreis angewendet wurde. Der reguläre Preis erscheint nun korrekt neben dem Sonderpreis wie erwartet.

_ACP2E-4100 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

### Produkt

#### Konfigurierbares Produkt mit schlechtem Verhalten im Frontend

Es wurde ein Problem behoben, bei dem konfigurierbare Produkte ein falsches Frontend-Verhalten zeigten, wenn ein Farbmuster-Attribut enthalten war, was dazu führte, dass Preise, Dropdown-Layout und erforderliche Feldindikatoren falsch angezeigt wurden.
Jetzt werden konfigurierbare Produkte korrekt gerendert, mit angemessener Preisgestaltung, angepassten Dropdown-Listen und erwartetem Benutzeroberflächenverhalten.

_AC-1014 - [GitHub-Problem](https://github.com/magento/magento2/issues/14296) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Preisbestätigungszeichenfolge stimmt nicht überein, wenn konfigurierbares Produkt der Test-Stock- und Test-Website zugewiesen ist, wobei die Option zum Anzeigen nicht vorrätiger Produkte aktiviert ist

Der fehlgeschlagene Test wurde aktualisiert, damit er dem tatsächlichen Preisverhalten für konfigurierbare Produkte entspricht, wenn alle untergeordneten Produkte denselben Preis haben.
Die Bestätigung validiert nun den angezeigten Preis korrekt, wodurch Fehler beim Testversand verhindert werden, ohne dass die Funktionalität beeinträchtigt wird.

_AC-10843 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/1ccc786b)_

#### Für ein konfigurierbares Produkt wird für den Testfall AC-6158 weiterhin die Bezeichnung „So niedrig wie“ angezeigt

Implementierte und verifizierte konfigurierbare Produkte (P1-P7) mit entsprechenden Varianten und Kategoriezuweisungen. Sichergestellt, dass der Preis der Storefront korrekt angezeigt wird und das Etikettenverhalten für Produkte der Kategorie C „So niedrig wie“ ist.

_AC-10847 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Prozentualer Rabatt auf Stufenpreis und Katalogpreisregel, berechnet auf Basis des ursprünglichen Preises ohne ausgewählte Optionen.

Prozentuale Rabatte auf Stufenpreis- und Katalogpreisregeln enthalten jetzt ausgewählte benutzerdefinierte Optionen.
Zuvor wurden prozentuale Rabatte auf den ursprünglichen Produktpreis berechnet, ohne ausgewählte benutzerdefinierte Optionen zu berücksichtigen, was zu falschen Endpreisen führte.
12004

_AC-12004 - [GitHub-Problem](https://github.com/magento/magento2/issues/38750)_

#### [Problem] Validierungs-Bewertung funktioniert nicht, der Selektor der Überprüfungs-Bewertung wurde geändert

Es wurde ein Problem behoben, bei dem die Validierung der Überprüfungsbewertung aufgrund eines geänderten Selektors nicht ausgelöst wurde. Zuvor konnten Reviews gespeichert werden, ohne eine Bewertung auszuwählen. Nach der Korrektur funktioniert die Validierung ordnungsgemäß und verhindert das Speichern einer Überprüfung, es sei denn, eine Bewertung wird ausgewählt.

_AC-12686 - [GitHub-Problem](https://github.com/magento/magento2/issues/33424) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 MinZulässige fehlende Produktbestellmenge

Das System funktioniert einwandfrei, und die Seitenquelle zeigt die Mindestmenge des Produkts korrekt an

_AC-12909 - [GitHub-Problem](https://github.com/magento/magento2/issues/39142) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39480)_

#### Produktsammlung - addMediaGalleryData ruft getSize auf, wenn die Sammlung geladen werden kann oder wird (kann die Anzahl verwenden, um eine zusätzliche DB-Abfrage zu vermeiden)

Diese PR reduziert den zusätzlichen Abfrageaufruf mit count(), wenn die Produktsammlung bereits geladen ist, wenn Produkt-GraphQL mit dem darin enthaltenen media_gallery-Feld aufgerufen wird.

_AC-13055 - [GitHub-Problem](https://github.com/magento/magento2/issues/39111) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39681)_

#### Ungültige SKU-Verarbeitung für verknüpfte Produkte in Magento

Es wurde ein Problem behoben, bei dem Produkte mit SKU „0“ aufgrund einer ungültigen SKU-Validierung nicht als verwandte, Upsell- oder Crosssell-Artikel verknüpft werden konnten. Die Aktualisierung stellt sicher, dass solche Produkte erfolgreich verknüpft werden können, sodass das Produkt ohne Fehler gespeichert werden kann.

_AC-13311 - [GitHub-Problem](https://github.com/magento/magento2/issues/39329) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Problem mit dem Raster Anpassbare Optionen auf der Produktseite im Admin-Bedienfeld

Das System funktioniert wie erwartet, wenn wir eine anpassbare Option mit Typ-Dropdown erstellen

_AC-14003 - [GitHub-Problem](https://github.com/magento/magento2/issues/39640) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39694)_

#### Admin-Produktseitenfehler, wenn alle Produktattribute auf den globalen Umfang eingestellt sind

Es wurde ein Problem behoben, bei dem auf der Admin-Produktbearbeitungsseite ein Fehler angezeigt wurde, wenn alle Produktattribute auf den globalen Umfang eingestellt waren. Der Fehler wurde durch eine leere Datenbankabfrage verursacht, wodurch die Seite unbrauchbar wurde. Nach der Behebung wird die Produktseite korrekt gerendert und Produkte können problemlos erstellt werden.

_AC-14011 - [GitHub-Problem](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] Keine Callbacks für Cron-Auftragskatalog_product_alert gefunden

Adobe Commerce verhindert jetzt korrekt, dass fehlerhafte Catalog_Product_Alert Cron-Aufträge geplant werden, nachdem der Produktwarnungs-Cron-Auftrag in Product_Alert umbenannt wurde. Zuvor wurde in Adobe Commerce 2.4.8 durch die Konfiguration von Stores > Configuration > Catalog > Catalog > Product Alerts Run Settings ein catalog_product_alert-Cron-Eintrag in core_config_data erstellt, und als Cron ausgeführt wurde, wurde der Fehler Magento_Cron protokolliert. CRITICAL: Exception: No callbacks found for cron job_catalog_product_alert, obwohl die gültigen product_alert-Aufträge korrekt ausgeführt wurden.

_AC-14494 - [GitHub-Problem](https://github.com/magento/magento2/issues/39800) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### [Produktvergleich] Die Vergleichsliste ist nicht verwendbar

Es wurde ein Problem behoben, bei dem die Vergleichsliste unbrauchbar wurde, wenn dasselbe Produkt aus verschiedenen Store-Ansichten hinzugefügt wurde. Nach der Behebung wurde die Vergleichsliste korrekt geladen und zeigt Elemente basierend auf dem bestimmten Store an.

_AC-14885 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Zusätzliche Protokollierung bei Anforderung eines Produkts über das Repository schlägt fehl

Verbesserte Fehlermeldungen für ProductRepository::get und getById, wenn keine SKU oder ID gefunden wird.
Zuvor boten Ausnahmen keinen Kontext darüber, welche SKU oder ID den Fehler verursacht hat.
Jetzt enthält die Ausnahmemeldung die fehlende SKU oder ID, was beim Debugging hilft und das Entwicklererlebnis verbessert.
Diese Änderung wirkt sich nicht auf das funktionale Verhalten der API aus.

_AC-15199 - [GitHub-Problem](https://github.com/magento/magento2/issues/40090) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Der Fehler „Attributsatz existiert nicht“ unterbricht die Seite

Es wurde ein Problem behoben, bei dem die Eingabe einer ungültigen Attributsatz-ID in der URL einen schwerwiegenden Fehler verursachte. Das System zeigt jetzt eine korrekte Fehlermeldung an, die besagt, dass der Attributsatz nicht vorhanden ist, anstatt die Seite zu beschädigen.

_AC-15753 - [GitHub-Problem](https://github.com/magento/magento2/issues/40213) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a06a4a57)_

#### Rückerstattung mit negativer Menge immer Rückerstattungsrabatt

Fehlerkorrektur - Beim Erstellen einer Gutschrift mit einer negativen Menge wird der Rabattbetrag fälschlicherweise zurückerstattet.
Jetzt werden Rabatte für negative Mengen nicht zurückerstattet, und die Rückerstattungsmenge wird korrekt auf null gesetzt.

_AC-9424 - [GitHub-Problem](https://github.com/magento/magento2/issues/37917) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Langsame Abfragen werden ausgeführt, wenn ein Produkt-Widget über den PageBuilder eingebunden wird

Die Abfrage für die Erstellung von Produkt-Widgets, einschließlich Produkt-SKUs, ist optimiert.

_ACP2E-3449 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Produktbilder werden nicht in der Größe angepasst, wenn sie als konfigurierbares Produkt hinzugefügt werden

Zuvor entsprachen Bilder, die über Konfigurationen im Admin-Bedienfeld hinzugefügt wurden, nicht der maximalen Upload-Größe, was zu Inkonsistenzen und Verwaltungsproblemen führen konnte. Jetzt wurde eine Korrektur implementiert, um sicherzustellen, dass die Größe der Bilder beim Hochladen automatisch geändert wird, um die maximale Größe einzuhalten, den Prozess zu optimieren und die Systemstandards einzuhalten.

_ACP2E-3504 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Alle Elemente aus anderen Kunden-Vergleichslisten werden dem Kunden nach der Anmeldung über den Administrator zugewiesen

Wenn ein Administrator bzw. eine Administratorin im Backend die Funktion „Als Kunde anmelden“ verwendet hat, wurden Produkte aus der Vergleichsliste eines zuvor angemeldeten Kunden bzw. einer zuvor angemeldeten Kundin fälschlicherweise dem aktuell stellvertretenden Kunden bzw. der Kundin zugewiesen.  Nach der Fehlerbehebung wird die Vergleichsliste für den richtigen angemeldeten Kunden korrekt geladen.

_ACP2E-3818 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

#### [B2B]-Speichervorgang für freigegebenen Katalog gibt den Fehler „Veraltete Funktionalität“ zurück

Der Administrator kann die Zuweisung von Produkten zum freigegebenen Katalog erfolgreich aufheben.
Zuvor führte das Aufheben der Zuweisung von Produkten mit einer großen Anzahl langer Produkt-SKUs aus dem freigegebenen Katalog zu einem Fehler

_ACP2E-4097 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ab891304)_

#### [Cloud] Die Leistung bei der Sitemap-Generierung ist erheblich beeinträchtigt

Die Sitemap-Generierung für Produkte mit Bildern erlebt keine exponentielle Verlangsamung mehr. Zuvor führte das Generieren von Sitemaps für Stores mit aktivierter Bildeinbindung zu langen Verarbeitungszeiten.

_ACP2E-4153 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Produkt, Steuer

#### Feste Produktsteuer (FPT) wird nicht separat mit konfigurierbaren Produkten angezeigt

Es wurde ein Problem behoben, bei dem die feste Produktsteuer (FPT) für konfigurierbare Produkte nach Auswahl einer Option nicht separat angezeigt wurde. Jetzt wird die FTP-Aufschlüsselung auf den Produktlisten- und Detailseiten korrekt angezeigt und stimmt mit dem Anzeigeformat einfacher Produkte überein.

_AC-13171 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b5e99d20)_

### Promotion

#### Preisregel „X-Warenkorb abrufen“ fügt falschen Rabatt hinzu, wenn bereits eine andere Regel angewendet wurde

Es wurde ein Problem behoben, bei dem die Preisregel „X-Warenkorb abrufen“ Rabatte anhand des ursprünglichen Produktpreises berechnete, selbst wenn dieser bereits durch eine andere Regel reduziert wurde. Die Aktualisierung stellt sicher, dass die zweite Regel jetzt den Rabatt auf den angepassten Preis anwendet, was zu genauen Gesamtrabatten führt, wenn mehrere Promotions aktiv sind.

_AC-12325 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Fehler beim Abrufen der Rabatte für Bestellartikel, die auf die Kundenbestellung über die GraphQL-Kundenanfrage angewendet wurden

Zuvor, als ein interner Server-Fehler mit angewendeten Rabatten für die Kundenbestellung über die GraphQL-Kundenanfrage beobachtet wurde, der jetzt behoben ist und korrekte Kundenbestellungsdaten mit angewendetem Rabatt abgerufen werden

_AC-14888 - [GitHub-Problem](https://github.com/magento/magento2/issues/39963) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fe72c407)_

#### Fehler beim Abrufen des Gutscheincodes für einen Bestellartikel für eine Kundenbestellung über die GraphQL-Kundenanfrage

Es wurde ein Problem behoben, bei dem beim Abrufen von Bestellungen mit Coupondetails über GraphQL ein interner Server-Fehler zurückgegeben wurde.
Jetzt wird die Abfrage erfolgreich ausgeführt und gibt die richtigen Couponinformationen in der Antwort zurück.

_AC-14889 - [GitHub-Problem](https://github.com/magento/magento2/issues/39962) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fe72c407)_

#### `[Cloud][experienceleague]` Katalogpreisregel nicht angewendet

Vor der Katalogpreisfixierung galten die Preisregeln nicht, wenn `special_price` nur auf Website-Ebene festgelegt wurde (nicht auf „Alle Store-Ansichten„). Nach der Korrektur gelten die Katalogpreisregeln jetzt korrekt, wenn `special_price` auf Website-Ebene festgelegt wird, indem zuerst der Standardspeicher der Website überprüft wird.

_ACP2E-4372 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() verfügt nicht über die entity_type-Filterung, sodass CMS-Seiten in Kategorie-URLs als Produkte behandelt werden

Es wurde ein Problem behoben, bei dem DynamicStorage nicht nach entity_type gefiltert wurde, sodass CMS-Seiten fälschlicherweise als Produkte in Kategorie-URLs behandelt wurden. Fehlerhafte URLs geben jetzt korrekt eine 404 zurück, anstatt CMS-Inhalte bereitzustellen.

_AC-14991 - [GitHub-Problem](https://github.com/magento/magento2/issues/39996) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64823f95)_

#### Durch die Aktivierung des Kategoriepfads in Produkt-URLs wird der Speicherumschalter auf mehrere Arten unterbrochen

Es wurde ein Problem behoben, bei dem das Aktivieren von Kategoriepfaden in Produkt-URLs dazu führte, dass der Store-Umschalter fehlschlug. Durch den Store-Wechsel werden jetzt Produkt-URLs über Store-Ansichten hinweg korrekt aufgelöst, ohne zur Homepage umgeleitet zu werden oder Fehler zurückzugeben.

_AC-15110 - [GitHub-Problem](https://github.com/magento/magento2/issues/40037) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a7ef6300)_

#### Nicht definierter Array-Schlüssel in ProductRepository getById

Das Problem trat auf, wenn ProductRepository::getById() mit einer ungültigen ID wie 123abc aufgerufen wurde, was zu einem Fehler „Undefinierter Array-Schlüssel“ führte.
Nach der Fehlerbehebung in Magento 2.4.9-alpha3 geben solche Anfragen jetzt korrekt eine 404-Seite zurück, anstatt eine Ausnahme auszulösen.
Die Qualitätssicherung wurde mit gültigen und falsch formatierten IDs bestätigt, und es wurden keine weiteren Probleme festgestellt.

_AC-15345 - [GitHub-Problem](https://github.com/magento/magento2/issues/40146) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Storefront-Vergleichsprodukt erstellt Google-SEO-Fehler - Links sind nicht durchsuchbar

Es wurde ein SEO-Problem behoben, bei dem der Link für die Storefront „Produkte vergleichen“ aufgrund eines fehlenden oder falsch gebundenen href-Attributs nicht von Suchmaschinen durchsucht werden konnte. Durch die Aktualisierung wird sichergestellt, dass der Link jetzt eine gültige, durchsuchbare URL enthält, was die Website-Auffindbarkeit verbessert und dazu beiträgt, dass Google-SEO-Audits bestanden werden.

_AC-15547 - [GitHub-Problem](https://github.com/magento/magento2/issues/40185) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Die Aktualisierung von product_url_key über die REST-API generiert keine 301-URL-Umschreibung

Wenn Sie den URL-Schlüssel des Produkts über die REST-API aktualisieren und die Einstellung „Ständige Umleitung für URLs erstellen, wenn der URL-Schlüssel geändert wird“ auf „Ja“ gesetzt ist, wird bei den Umschreibungen der Produkt-URL eine Umleitung von der alten URL zur neuen erstellt.

_ACP2E-3900 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

#### [Cloud] Sitemap-Generierung endet nie

Vor der Korrektur konnte die Sitemap-Generierung nicht erfolgreich abgeschlossen werden, wenn der Katalog mehr als eine Million Produkte enthielt. Nach der Fehlerbehebung wird die Sitemap-Generierung mit geringerer Speicherzuweisung und mit bis zu einer Million Produkten pro Geschäft abgeschlossen.

_ACP2E-3902 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud] Store Switcher funktioniert nicht von EN nach FR für die FAQ-Seite

Fehlerkorrektur - Beim Wechseln zwischen Store-Ansichten werden Benutzer nicht mehr zur entsprechenden übersetzten CMS-Seite, sondern auf die Homepage umgeleitet. Der Store-Umschalter sucht jetzt im Ziel-Store nach URL-Neuschreibungen, um eine korrekte Umleitung sicherzustellen (z. B. die FAQ-Seite auf Englisch → die FAQ-Seite auf Französisch).

_ACP2E-4112 - [GitHub-Problem](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [Cloud] Deaktivieren der alten Sitemap-Generierung

Eine neue Konfigurationsoption ist jetzt verfügbar, um zwischen dem Standard-Sitemap-Generierungsprozess und einem neu implementierten Batch-Modus zu wechseln. Diese Verbesserung ermöglicht eine größere Flexibilität und Skalierbarkeit in Workflows zur Sitemap-Erstellung.

_ACP2E-4132 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Verdächtige Anfragen lösen Ausnahmen im Exception.log aus.

Fehlerkorrektur - Bösartige oder falsch formatierte URL-Anfragen verursachen jetzt keine Fehler mehr bei der Datenbanksortierung und füllen die Ausnahmeprotokolle auf.
Wenn bisher verdächtige Anfragen mit ungültigen Zeichenkodierungen oder nicht unterstützten Zeichen empfangen wurden, versuchte das System, diese zu dekodieren und zu verarbeiten, was zu MySQL-Sortierkonflikten führte.

_ACP2E-4328 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2687b487)_

### Verkauf

#### Wenn die Geschenknachricht auf Auftragsebene aktiviert ist, der Benutzer jedoch keine Daten eingibt und keine Bestellung aufgibt, werden in der Admin weiterhin Von Name und Bis Name angezeigt, wobei Vor- und Nachname des Kunden angezeigt werden.

Fehlerkorrektur - Die Felder „Geschenknachrichten-Absender“ und „Empfänger“ werden jetzt nicht mehr automatisch mit Kundennamen ausgefüllt, auch wenn keine Geschenknachricht eingegeben wurde. Die Felder bleiben jetzt leer, es sei denn, der Benutzer gibt die Details an.

_AC-15140 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a8cf637b)_

### Suche

#### „Erneute Übermittlung des Formulars bestätigen“ bei der Katalogsuche mit „Kategorienumbruch speichern“

Wenn Sie nach der Änderung der Symbolleisteneinstellungen von einer Produktseite zur Katalogsuchergebnisseite zurückkehren, wird das Dialogfeld „Erneute Übermittlung des Formulars bestätigen“ nicht mehr Trigger, wenn „Kategorienpaginierung speichern“ aktiviert ist.
Zuvor ist bei Benutzern ein Browser-Fehler oder eine Warnung zur erneuten Übermittlung des Formulars aufgetreten, wenn sie zur Suchergebnisseite zurückkehrten, nachdem sie Symbolleistenparameter wie die Sortierreihenfolge geändert hatten.

_ACP2E-4208 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e885088b)_

#### Das aggregierte Suchfeld „_search“ wird in der Suchabfrage nicht mehr verwendet

Die Volltextsuche gibt jetzt übereinstimmende Produkte zurück, wenn die Bedingung für die Mindestübereinstimmung über alle durchsuchbaren Felder hinweg gemeinsam erfüllt sein soll, anstatt zu verlangen, dass die Bedingung durch ein einzelnes Feld erfüllt wird.

_ACP2E-4285 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cbca0396)_

### Sicherheit

#### Interner Server-Fehler

Magento fügt jetzt bei Verwendung des asynchronen REST-Endpunkts POST /rest/default/async/V1/carts/mine/items erfolgreich Produkte zum Warenkorb eines Kunden hinzu. Zuvor führte diese asynchrone „Zum Warenkorb hinzufügen“-Anfrage zu einem internen Server-Fehler, und Magento protokollierte den folgenden Fehler: Error: Call to a member function setFinalPrice() on null in app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162.

_AC-16344 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Gebündelte/zusammengeführte JS ist nicht Teil von SRI-Hashes

Vor der Fehlerbehebung wurden generierte Bundles oder zusammengeführte Dateien nicht zur SRI-Hash-Liste hinzugefügt. Jetzt werden die Dateien ordnungsgemäß zu den SRI-Hashes hinzugefügt.

_ACP2E-3854 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] Es wurde ein Problem mit der Schreibberechtigung für Newrelic empfangen.

Vor der Fehlerbehebung waren die Protokolle mit Ausnahmen überladen. Nach Anwendung der Fehlerbehebung sind die Protokolle jetzt sauber und frei von Ausnahmen.

_ACP2E-4296 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/61c96348)_

### Lieferung

#### Falsche Liefermenge nach wenigen Gutschriften

Fehlerkorrektur - Der Wert „Menge zu Versand“ wurde nach mehreren Gutschriften nicht korrekt berechnet, sodass erstattete Artikel versendet werden können.
Jetzt aktualisiert das System genau die verbleibende versandfähige Menge basierend auf versendeten und zurückerstatteten Artikeln, um ungültige Sendungen zu verhindern.

_AC-1479 - [GitHub-Problem](https://github.com/magento/magento2/issues/34289) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Potenzielles Leistungsproblem beim Laden von Versandmethoden

Der Ladevorgang für Versandmethoden wurde optimiert, indem sichergestellt wurde, dass nur aktive Spediteure geladen werden, wenn dies angefordert wurde. Zuvor wurden Fabriken für alle Versandmethoden initialisiert, was zu unnötigem Leistungsaufwand führte. Die Fehlerbehebung verbessert die Effizienz, indem nur aktive Spediteure bedingt geladen werden, wodurch die Ladezeit und die Ressourcennutzung reduziert werden.

_AC-15415 - [GitHub-Problem](https://github.com/magento/magento2/issues/40153) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### [Problem] Kommerzielles Ziel sollte nicht als Wohnort behandelt werden

Fehlerkorrektur - In der UPS-REST-Versandintegration werden kommerzielle Ziele jetzt nicht mehr fälschlicherweise als Wohnziele behandelt. Der ResidentialAddressIndicator ist jetzt nur noch für Wohnadressen in der UPS-Tarifanfrage enthalten, um unbeabsichtigte Wohnungszuschläge zu verhindern und genaue kommerzielle Versandraten zu gewährleisten.

_AC-16285 - [GitHub-Problem](https://github.com/magento/magento2/issues/40314) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40307)_

#### Ausnahme bei Erstellung des UPS Versandtitels

Behobener Warnhinweis: Array-zu-String-Konvertierung während der Erstellung der UPS-Versandkennzeichnung

_ACP2E-3676 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Prüft das Magento_Fedex-Kernmodul auf ein gültiges-aktives Token, bevor eine Anfrage zum Abrufen eines neuen gesendet wird?

Adobe Commerce stellt nicht mehr viele Anfragen an den FedEx-API-Service für das Zugriffstoken. Zuvor führte Adobe Commerce immer neue Anfragen an die FedEx-API durch, die ein Problem mit der Ratenbegrenzung verursachten, obwohl das Zugriffstoken weiterhin gültig ist.

_ACP2E-3930 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

### Staging und Vorschau

#### Der Preis des Produkts im Warenkorb, der von der Katalogpreisregel beeinflusst wird, ändert sich nicht, wenn die Regel durch die Staging-Aktualisierung angepasst wird

Es wurde ein Problem behoben, bei dem Produktpreise im Warenkorb nach der Änderung einer Katalogpreisregel durch eine Staging-Aktualisierung nicht vollständig aktualisiert wurden. Zuvor erschien der aktualisierte Preis nur im Zusammenfassungsabschnitt, während der zentrale Warenkorbblock den alten Wert anzeigte. Jetzt aktualisiert die überarbeitete Regel den Produktpreis korrekt für den gesamten Warenkorb.

_AC-15304 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Wenn eine geplante Aktualisierung für die Kategorie gelöscht wird, wird die Anzahl der untergeordneten Elemente für die übergeordnete Kategorie nicht reduziert

Es wurde ein Problem behoben, durch das beim Löschen einer geplanten Aktualisierung für eine Kategorie die Anzahl der untergeordneten Elemente der übergeordneten Kategorie nicht reduziert wurde, sodass die Anzahl korrekt aktualisiert wird, wenn geplante Aktualisierungen oder Unterkategorien entfernt werden.

_AC-15670 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Beim Bearbeiten geplanter Aktualisierungen für Kategorien werden der übergeordneten Kategorie untergeordnete Elemente hinzugefügt

Es wurde ein Problem behoben, durch das beim Bearbeiten einer vorhandenen geplanten Aktualisierung für eine Unterkategorie die Anzahl der untergeordneten Elemente für übergeordnete Kategorien in der Datenbank fälschlicherweise erhöht wurde. Das Problem führte nach dem Speichern von Aktualisierungen zu ungenauen Kategoriehierarchiedaten. Nach der Behebung bleibt die Anzahl der untergeordneten Elemente korrekt und wird nicht mehr unerwartet erhöht.

_AC-16239 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Bei der Vorschau eines geplanten Updates wird die erste Store-Ansicht in alphabetischer Reihenfolge anstelle der Store-Ansicht geöffnet, die von Interesse ist

Vor der Fehlerbehebung wurde die Vorschau eines geplanten Updates in der ersten Store-Ansicht in alphabetischer Reihenfolge anstelle der zugewiesenen Store-Ansicht geöffnet.
Nach der Fehlerbehebung wird die Vorschau jetzt korrekt in der Store-Ansicht geöffnet, die dem CMS-Block-Staging-Update zugewiesen ist.

_ACP2E-3671 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### Geplante Produktaktualisierungen mit aktivierten Kategorieberechtigungen können nicht in der Vorschau angezeigt werden

Vor der Fehlerbehebung wurde ein zukünftiges Produkt, das aktiviert werden soll, nicht im Vorschaumodus angezeigt. Jetzt wird sie angezeigt, auch wenn der aktuelle Status deaktiviert ist.

_ACP2E-3786 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Fehlende Validierung für das Feld „Rabattbetrag für Katalogpreisregel“

Zuvor wurde das Feld „DISCOUNT_AMOUNT“ im Update des Staging-Zeitplans nicht korrekt mit den aktuellen Validierungsregeln validiert. Nach Anwendung der Korrektur wird das Feld „Rabatt_Betrag“ jedoch entsprechend validiert.

_ACP2E-3867 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

#### Produkt mit geplanten Aktualisierungen bündeln entfernt die Option „Bundle-Elemente“ der Aktion zum Speichern eines Produkts

Das Entfernen von Bundle-Produktoptionen oder zugehörigen Produkten bei der geplanten Aktualisierung wirkt sich nicht mehr auf die ursprünglichen Bundle-Optionen und zugehörigen Produkte aus und umgekehrt. Auch das Entfernen der Bundle-Produktionsoptionen im Originalprodukt und das Ersetzen durch andere Optionen nach der Planung einer Aktualisierung führt nicht mehr zum Entfernen der neu hinzugefügten Optionen

_ACP2E-4212 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ab891304)_

#### Navigieren zwischen Websites in der Vorschau für Zeitplanaktualisierung nicht möglich

Vor dieser Fehlerbehebung würde die Vorschau für geplante Updates fehlschlagen, wenn versucht wird, Inhalte für Stores mit benutzerdefinierten Domains in der Vorschau anzuzeigen. Nach dieser Fehlerbehebung können benutzerdefinierte Store-Domains wie vorliegend in der Vorschau angezeigt und innerhalb des Vorschau-IFrame navigiert werden. Die Fehlerbehebung gilt für Produkte, Kategorien, CMS-Seiten und CMS-Blöcke und unterstützt Navigationslinks mit `{{store url}}` Markup-Tags, wie in [Adobe Commerce-Variablen und Markup-Tags](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags) dokumentiert.

_ACP2E-4308 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/0a3b7032)_

### Steuer

#### Falsche Bestellsumme, die Runde wird nicht auf die Preisberechnung angewendet.

Das System wird nun bei der Berechnung des Betrags für den Preis-Nachlass-Rabatt, den Rabatt-Betrag und die Steuern korrekt verarbeitet.
Die tatsächliche Summe der Bestellung

_AC-11389 - [GitHub-Problem](https://github.com/magento/magento2/issues/38455) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39687)_

#### [Problem] Behebung: Der Wert für base_weee_tax_applied_row_amnt der Gutschriftenartikel ist falsch

Die Berechnung der Gutschrift wurde korrigiert, indem der richtige Setter für base_weee_tax_applied_row_amnt verwendet wurde. Dabei wurde sichergestellt, dass der Steuerwert nur die erstattete Menge widerspiegelt. Zuvor wurde für den Zeilenbetrag fälschlicherweise der volle Bestellwert anstelle des teilweisen Gutschriftsbetrags verwendet.

_AC-12049 - [GitHub-Problem](https://github.com/magento/magento2/issues/38765) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### Artikel im Mini-Warenkorb zeigen Fremdwährungspreise ohne Umrechnung an

Der Mini-Warenkorb konvertiert nun die Währung korrekt und zeigt den genauen Betrag basierend auf den konfigurierten Konversionsraten an.

_ACP2E-4364 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1c547060)_

### Test-Framework

#### [Problem] Entfernen eines duplizierten &lt;Severity>-Tags aus dem MFTF-Test „AdminSetUpWatermarkForSwatchImageTest“

Das System enthält jetzt nur noch ein einziges Schweregrad-Tag im AdminSetUpWatermarkForSwatchImageTest, was die Code-Klarheit und -Konsistenz verbessert. Zuvor enthielt dieser Test zwei identische Schweregrad-Tags, was unnötig war und zu Verwirrung führen konnte.

_AC-11873 - [GitHub-Problem](https://github.com/magento/magento2/issues/38504) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31862)_

#### [Problem] lib/internal/Magento/framework/app/test/unit/_files/app/etc/en ignorieren…

Das System ignoriert jetzt die Datei „env.php“, die beim Ausführen von Modultests generiert wird, um sicherzustellen, dass der Git-Status nach dem Ausführen von Tests sauber bleibt. Zuvor wurden durch Ausführen von Modultests eine neue Datei „env.php“ generiert, wodurch der Git-Status anzeigt, dass eine neue Datei gefunden wurde, wodurch sie schmutzig erscheint.

_AC-13293 - [GitHub-Problem](https://github.com/magento/magento2/issues/39304) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37631)_

#### [Problem] Beheben eines Integrationstestproblems mit dem Interceptor

Das System identifiziert und verarbeitet jetzt im Integrationstest korrekt \Magento\TestFramework\App\Config\Interceptor , sodass der Test auch dann auf die erforderlichen Daten zugreifen kann, wenn ein Plug-in für die Klasse vorhanden ist. Zuvor konnte das System nicht berücksichtigen, dass \Magento\TestFramework\App\Config möglicherweise ein \Magento\TestFramework\App\Config\Interceptor ist, was zu einem Fehler beim Versuch führte, auf die $data -Eigenschaft zuzugreifen.

_AC-13305 - [GitHub-Problem](https://github.com/magento/magento2/issues/39324) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37187)_

#### [Problem] MFTF: Senden einer E-Mail an ein Freundschaftsformular mit aktiviertem CAPTCHA

Der Testfall behandelt die Funktionalität des Formulars „E-Mail an Freund“, wenn CAPTCHA aktiviert ist, um sicherzustellen, dass der Formularübermittlungsprozess mit falschen und richtigen CAPTCHA-Werten korrekt funktioniert.

_AC-13492 - [GitHub-Problem](https://github.com/magento/magento2/issues/39462) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32830)_

#### Hartcodierte Bearbeitungspfade schlagen in Composer-Builds fehl

_AC-16488_

#### [Problem] magento/magento2#: GraphQL-Mutation. Zusätzliche Testabdeckung für StoreConfig-Einstellungen des Kunden.

Das System fügt jetzt die zusätzliche Testabdeckung für die StoreConfig-Optionen des nächsten Kunden hinzu:
required_character_classes_number
minimum_password_length

_AC-9370 - [GitHub-Problem](https://github.com/magento/magento2/issues/37915) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/28761)_

#### Umgebungsspezifische Unit-Test-Fehler in AC 2.4.7-p3

Dieses Problem behebt Fehler bei Modultests, die nicht in allen Versionen und Umgebungen reproduziert werden. Zuvor schlugen einige Modultests aufgrund verschiedener Bibliotheksversionen oder fehlender Funktionen, die in einer späteren Version hinzugefügt wurden, fehl.

_ACP2E-3712 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9ad7d277)_

### UI-Framework

#### [Problem] Entfernen doppelter Variablen aus einer der Dateien mit der geringeren Anzahl

Das System entfernt jetzt duplizierte Variablen aus weniger Dateien, was einen saubereren und effizienteren Code gewährleistet. Zuvor waren diese duplizierten Variablen in den LESS-Dateien vorhanden, was zu unnötiger Redundanz im Code führte.

_AC-11743 - [GitHub-Problem](https://github.com/magento/magento2/issues/31154) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG ist in dynamischen Zeilen leer

WYSIWYG-Felder in dynamischen Zeilen sind jetzt korrekt initialisiert und ausgefüllt.
Zuvor konnten WYSIWYG-Felder in dynamischen Zeilen (z. B. in Design-Konfigurationsformularen) nach bestimmten Aktionen leer erscheinen oder ihren Inhalt verlieren, was manuelles Eingreifen zur Wiederherstellung von Daten erforderlich machte.
12336

_AC-12336 - [GitHub-Problem](https://github.com/magento/magento2/issues/38893) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problem] MIME-Typ-Tippfehler beheben

Das System verarbeitet den MIME-Typ und den Tippfehler für das gif-Bild korrekt und korrigiert ihn

_AC-8001 - [GitHub-Problem](https://github.com/magento/magento2/issues/36899) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36669)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Backend`

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8814 - [GitHub-Problem](https://github.com/magento/magento2/issues/37522) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36976)_

#### [Problem] Vermeiden des direkten Zugriffs auf die Rezensionsliste Ajax

Das System verarbeitet und vermeidet den direkten Zugriff auf die Rezensionsliste Ajax

_AC-9381 - [GitHub-Problem](https://github.com/magento/magento2/issues/37920) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33876)_

#### Header-Login/-Logout wird in Multi-Store-Setup mit freigegebenen Cookies nicht aktualisiert

Der Anmelde-Header wird beim Abmelden gemäß den Konfigurationseinstellungen korrekt aktualisiert. Die Datei „customer-data.js“ verwendet ein Cookie, um den Wert „image-customer-login“ zu speichern, wenn Kundenkonten global freigegeben werden. Andernfalls wird der lokale Speicher verwendet.

_ACP2E-4149 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobil] Fotorama kann Mini-Warenkorb im Bild-Viewer schließen Aktion

Das Problem mit Fotorama wurde behoben. Zuvor wurde ein Minicart beim Schließen des Bild-Viewers geöffnet

_ACP2E-4231 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e885088b)_

#### Zusammengeführte JS-Dateien werden nicht ordnungsgemäß in Projekten mit vielen Stores generiert.

Das Zusammenführen von JavaScript-Dateien funktioniert jetzt ordnungsgemäß, wenn mehrere Stores konfiguriert sind.
Zuvor konnten Dateien in Multi-Store-Setups manchmal nicht ordnungsgemäß zusammengeführt werden, was zu unvollständigen oder inkonsistenten Ergebnissen führte.

_ACP2E-4246 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ab891304)_

### Aktualisierungen - Upgrade-Kompatibilitäts-Tool

#### Veraltete Funktionen: Erstellung der dynamischen Eigenschaft &quot;Magento\Framework\Acl::$_roleRegistry“

Veraltete Funktionsfehler verhindern nicht mehr den Zugriff auf das Admin-Bedienfeld nach dem Upgrade.
Nach dem Upgrade auf Magento 2.4.6 konnte der Versuch, auf das Admin Panel zuzugreifen, zu einem Fehler führen:
„Veraltete Funktionen: Die Erstellung der dynamischen Eigenschaft &quot;Magento\Framework\Acl::$_roleRegistry“ ist in vendor/magento/framework/Session/SessionManager.php in Zeile 186 veraltet.“
Dies hinderte Administratoren daran, sich anzumelden.
12343

_AC-12343 - [GitHub-Problem](https://github.com/magento/magento2/issues/37469)_
