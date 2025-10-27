---
source-git-commit: ae571a9e7ca1234644a3bc9beade447009c58a3d
workflow-type: tm+mt
source-wordcount: '6079'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.9-alpha3)

## Es wurden Probleme in Version 2.4.9-Alpha3 behoben

Es wurden 129 Probleme im Magento Open Source 2.4.9-alpha3-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

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

#### Der REST-API-Endpunkt export-stock-salable-qty gibt falsche Elemente zurück_total_count

Fehlerkorrektur - Die Paginierung in der API für die verkäufliche Lagerbestände im Lager funktioniert jetzt problemlos, wenn total_count fälschlicherweise auf die Seitengröße beschränkt ist. Zuvor gab bei Verwendung des Endpunkts /rest/all/V1/inventory/export-stock-salable-qty/website/base mit Paginierungsparametern wie page_size=5 das Feld total_count in der Antwort 5 anstelle der tatsächlichen Gesamtzahl der Produkte zurück, die den Suchkriterien entsprechen. Nach dieser Fehlerbehebung spiegelt das Feld total_count jetzt korrekt die Gesamtzahl der verfügbaren Produkte wider, unabhängig vom Parameter page_size, was ein konsistentes Paginierungsverhalten über alle Magento REST-API-Endpunkte hinweg sicherstellt.

_ACP2E-4086 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### Validierungsproblem mit benutzerdefinierten Optionen-IDs in REST-APIs für Warenkorbelemente

Die REST-APIs V1/guest-carts/&lt;cartId>/items/ und V1/carts/mine/items/ validieren jetzt „product_options.extension_attributes.custom_options“.*.option_id“, um sicherzustellen, dass es auf eine gültige option_id für die Warenkorb-Artikel-SKU verweist. Zuvor wurde dieser Parameter ohne Validierung verarbeitet und in der Datenbank gespeichert.

_ACP2E-4138 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

### Konto

#### [Problem] Unnötiger Abstand im Backend-Raster wurde entfernt

Das System entfernt jetzt unnötigen Abstand im Backend-Raster, wenn Elemente ausgewählt sind

_AC-11579 - [GitHub-Problem](https://github.com/magento/magento2/issues/38502) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32622)_

#### Kommentar zum Wunschlistenelement kann über `updateProductsInWishlist` GraphQL-Mutation nicht gelöscht werden

Es wurde ein Problem behoben, bei dem Wunschlistenkommentare nicht durch GraphQL-Mutationen aktualisiert wurden.
Jetzt werden Kommentare korrekt aktualisiert und in der API-Antwort und Storefront widergespiegelt.

_AC-14682 - [GitHub-Problem](https://github.com/magento/magento2/issues/39911) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Einstellung für Präfix/Suffix anzeigen, die bei Festlegung auf „Nein“ ignoriert wird

Es wurde ein Problem behoben, bei dem das Präfix/Suffix des Kundennamens auch dann in Bestellungen angezeigt wurde, wenn es in der Konfiguration deaktiviert war.
Jetzt werden Präfix-/Suffixwerte aus den Bestelldetails basierend auf der Konfigurationseinstellung entfernt.

_AC-15074 - [GitHub-Problem](https://github.com/magento/magento2/issues/40036) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront Kundenkonto-Register: E-Mail-Adressformat wird mit anderem Domain-Format konvertiert

Dieser Fehler behob ein Problem, bei dem Kunden-E-Mails mit Sonderzeichen in der Domain (z. B. tec55241@adòbe.com) automatisch in das Punycode-Format (tec55241@xn--adbe-mqa.com) konvertiert wurden.
In Magento 2.4.9-alpha3 stellt die Korrektur sicher, dass diese E-Mail-IDs unverändert und gültig bleiben, sodass Versandfehler vermieden werden.

_AC-15177 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Fehlende Validierungsmeldungen (Bild-Fehler) im Registrierungsformular

Es wurde ein Problem behoben, bei dem in Pflichtfeldern auf der Seite zur Erstellung von Kundenkonten keine Validierungsmeldungen angezeigt wurden, wenn sie leer gelassen wurden.
Jetzt werden für alle leeren oder falschen Felder richtige Fehlermeldungen angezeigt.

_AC-15185 - [GitHub-Problem](https://github.com/magento/magento2/issues/40076) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problem nach der Anmeldung in Magento 2.4.8-p1

Es wurde ein Problem in Magento 2.4.8-p1 behoben, bei dem der Link „Konto erstellen“ nach der Anmeldung weiterhin auf der Homepage angezeigt wurde.
Jetzt wird der Link nach der Anmeldung korrekt ausgeblendet, was im Einklang mit anderen Seiten steht.

_AC-15292 - [GitHub-Problem](https://github.com/magento/magento2/issues/40120)_

### Admin-Benutzeroberfläche

#### [Problem] Veralteten Escaper ersetzen

Dieses PR entfernt die veralteten getEscaper() und fügt sie über den Konstruktor Injection hinzu

_AC-15132 - [GitHub-Problem](https://github.com/magento/magento2/issues/40062) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38135)_

#### Überlappende Willkommensnachricht in der Produktkategorie in der Mobilansicht.

Es wurde ein UI-Problem behoben, bei dem sich der Begrüßungsname mit Produktkategorien in der mobilen Ansicht überschnitt und Klicks blockierte.
Kategorien sind jetzt vollständig sichtbar und können ohne Überschneidungsprobleme angeklickt werden.

_AC-15166 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Einträge vom Typ „reCAPTCHA-Parameter kann nicht aufgelöst werden“ in Exception.log für Google reCAPTCHA Admin Panel

Ein reCAPTCHA-Fehler in der `var/log/exception.log` für die Google V3-reCAPTCHA-Admin-Anmeldung wurde behoben, und es werden keine Fehlermeldungen protokolliert. Zuvor wurde der folgende Fehler alle paar Sekunden ausgelöst, wenn ein Admin-Benutzer die Einstellungen **Konfiguration** > **Sicherheit** > **Google reCAPTCHA Admin Panel** konfiguriert hat: `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub-Problem](https://github.com/magento/magento2/issues/34975) - [GitHub-Code-](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub-Code-Beitrag](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

### Admin-Benutzeroberfläche, Steuer

#### Fehler in der Steuersatz-Admin-Benutzeroberfläche

Dieses Ticket hat ein Problem in der Admin-Benutzeroberfläche für Steuersätze behoben, bei dem beim Wechsel des Landes (z. B. von USA → Großbritannien) weiterhin der zuvor ausgewählte US-Bundesstaat angezeigt wurde, was Benutzer irregeführt hat.
In 2.4.9-alpha3 wird das Bundesland nun auf * zurückgesetzt, wenn das ausgewählte Land keine Bundesländer hat.

_AC-8440 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### REST API products-render-info gibt falschen Endpreis für angemeldeten Kunden zurück

Das Ticket hat eine Fehlerbehebung für REST API-Produkte - Render-Info geben einen falschen Endpreis für angemeldete Kunden zurück

_AC-5979 - [GitHub-Problem](https://github.com/magento/magento2/issues/35757) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/)_

#### Die Schaltfläche „Zur Anforderungsliste hinzufügen“ wird ausgeblendet, wenn versucht wird, sie von der Kategorieseite aus hinzuzufügen

Die Schaltfläche „Früher zur Anforderungsliste hinzufügen“ wird ausgeblendet, wenn versucht wird, sie von der Kategorieseite hinzuzufügen, die jetzt korrigiert ist, und die Schaltfläche „Anforderung“ auf der Kategorieseite angezeigt wird

_AC-8575_

### B2B, Warenkorb und Checkout

#### Keine solche Entität mit cartId = X-Fehler wird in der Storefront angezeigt, wenn sich der B2B-Firmenbenutzer über die Admin-Funktion „Als Kunde anmelden“ anmeldet

Jetzt ist der Fehler „Keine solche Entität mit cartId = X“ nach erfolgreicher Anmeldung über das Admin-Backend bei Verwendung der Funktion „Als Kunde anmelden“ nicht mehr sichtbar.

_ACP2E-3994 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

### Warenkorb und Checkout

#### [Problem] Hinzufügen von EventPrefix und EventObject zum Checkout-Vereinbarungsmodell

Das System enthält jetzt EventPrefix und EventObject für das Checkout-Vereinbarungsmodell, sodass Ereignisse mit einem Ereignispräfix ausgelöst werden können. Diese Verbesserung bietet Entwicklern mehr Flexibilität bei der Arbeit mit Checkout-Vereinbarungsereignissen. Zuvor unterstützte das Modell der Kaufbestätigung nicht EventPrefix und EventObject, was die Möglichkeit einschränkte, die Ereignisbehandlung anzupassen.

_AC-13252 - [GitHub-Problem](https://github.com/magento/magento2/issues/32510) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32451)_

#### [GraphQL] kann für das Feld „SelectedCustomizableOption.label“, das keine NULL-Werte zulässt, nicht null zurückgeben

Das System gibt jetzt keinen internen Server-Fehler mit der Meldung aus, wenn die ausgewählte Option nicht mehr vorhanden ist

_AC-14256 - [GitHub-Problem](https://github.com/magento/magento2/issues/39729) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] Es können keine Bestellungen aufgegeben werden, bei denen die Stadt Ziffern 0-9, ein kaufmännisches Und-Zeichen, einen Punkt oder Klammern im Stadtnamen hat

Es wurde ein Problem behoben, bei dem der Checkout für Städtenamen mit Sonderzeichen wie fehlgeschlagen ist. , &amp; oder Klammern.
Jetzt werden Bestellungen mit solchen Städtenamen erfolgreich ohne Validierungsfehler platziert.

_AC-14495 - [GitHub-Problem](https://github.com/magento/magento2/issues/39854) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Verkaufsregel-Unterauswahl mit Mengenbedingung kann nicht angewendet werden

Es wurde ein Problem behoben, bei dem Regeln zum Warenkorbpreis mit Bedingungen zur Produktunterauswahl beim Checkout nicht angewendet wurden.
Jetzt werden Rabatte gemäß den konfigurierten Regeln erfolgreich angewendet.

_AC-14884 - [GitHub-Problem](https://github.com/magento/magento2/issues/39965) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fe72c407)_

#### GraphQL - Zusammenführungs-Warenkorb funktioniert nicht richtig, wenn Rückstand aktiviert ist

Es wurde ein Problem behoben, bei dem Gast-Warenkorb-Artikel während der Warenkorbzusammenführung über GraphQL nicht mit dem Warenkorb zusammengeführt wurden.
Jetzt spiegelt der Warenkorb des Kunden die kombinierte Menge sowohl aus dem Gast- als auch aus dem Warenkorb des Kunden korrekt wider.

_AC-15148 - [GitHub-Problem](https://github.com/magento/magento2/issues/40064) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integration] [Checkout] Abhängigkeitsrichtlinien in der E-Mail-Vorlage für fehlgeschlagene Zahlungen aktualisiert

Fehlgeschlagene E-Mail-Vorlage für Zahlung wurde aktualisiert, um Abhängigkeitsanweisungen korrekt zu verarbeiten.
Fehlerbehebung stellt sicher, dass Lieferadresse und Versandmethode bei Bedarf korrekt angezeigt werden.
Zuvor fehlten diese Felder in E-Mails mit fehlgeschlagenen Zahlungen.

_AC-15363 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Cloud] Kostenloser Versandrabatt wurde nicht korrekt entfernt, wenn der Warenkorb die Anforderungen nicht mehr erfüllt

Die Zwischensumme (ohne Die Preisregel für den Warenkorb enthält jetzt Rabatte aus vorherigen Regeln.

_ACP2E-3973 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Doppelte Bestellung für denselben Kunden in Multishipping gefunden

Gleichzeitige Anfragen, Bestellungen mit mehreren Versandadressen zu tätigen, führen nicht mehr zu doppelten Bestellungen für denselben Kunden

_ACP2E-4117 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

### Warenkorb und Checkout, Bestellung, Produkt

#### Geschenkgutschein-E-Mail wird gesendet, auch wenn die Bestellrechnung fehlschlägt

Vor der Implementierung dieser Fehlerbehebung wurden E-Mails mit Geschenkkarten versendet, nachdem die Rechnung erstellt worden war. Nachdem die Fehlerbehebung angewendet wurde, werden jetzt Geschenkkarten-E-Mails gesendet, nachdem Rechnungen erfolgreich gespeichert und bestätigt wurden.

_ACP2E-3905_

### Warenkorb und Checkout, Sicherheit

#### [CLOUD] Abrufen der 404-Datei für JS auf der Checkout-Seite beim ersten Versuch nach der Implementierung des sri-Patches

Vor der Fehlerbehebung wurden Mixins nicht in den Warenkorb geladen und zur Kasse gebeten, wenn Minimieren und Bündeln aktiviert waren. Nach der Fehlerbehebung sollten alle Mixins erwartungsgemäß geladen werden.

_ACP2E-4128 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Katalog

#### Probleme mit dem Preisbereich und config.php

In Magento 2.4.2 wird durch die Änderung des Preisbereichs über config.php der Wert is_global in catalog_eav_attribute für das Preisattribut nicht ordnungsgemäß aktualisiert.
Produktpreise bleiben daher global und können nicht pro Website gespeichert werden, auch wenn der Preisbereich auf Website eingestellt ist.
Um dieses Problem zu umgehen, muss die Spalte „is_global“ in der Datenbank manuell aktualisiert werden, was für Produktionsumgebungen nicht ideal ist.
Dieses Verhalten entspricht dem standardmäßigen Design von Magento, bei dem der Preisbereich entweder „global“ oder „Website“ ist, aber nicht pro Shop-Ansicht.

_AC-13857 - [GitHub-Problem](https://github.com/magento/magento2/issues/33559)_

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

#### Dynamische Bildgenerierung generiert eine große Anzahl von Bildern

Nach der Fehlerbehebung werden Bilder nur für die Websites generiert, denen das Produkt zugewiesen ist.

_ACP2E-3927 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fab20b00)_

#### 500-Fehler treten im Frontend auf, da im Layout eine falsche Layout-Struktur zwischengespeichert wird

Es wurde ein Problem behoben, bei dem eine Seite aufgrund einer im Layout zwischengespeicherten falschen Layout-Struktur einen Fehler-Code 500 zurückgab

_ACP2E-4040 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

#### Validierungsfehler für das Feld Rabattbetrag der Katalogpreisregel in der geplanten Aktualisierung

Bevor Sie dieses Problem behoben haben, haben Sie bei der Zeitplanaktualisierung für die Katalogpreisregel zuvor Folgendes festgestellt: Wenn der Rabattbetrag nach_festgelegt ist, wurde er aufgrund der Regel für den Validierungs-Nummernbereich nicht ordnungsgemäß validiert. Nachdem diese Fehlerbehebung angewendet wurde, funktioniert die Validierung für die Regel Festpreis-Katalogpreis ordnungsgemäß.

_ACP2E-4054 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Produkte werden nach der Deaktivierung als nicht vorrätig angezeigt

Nach der Behebung sind deaktivierte Produkte nicht im Produkt-Widget vorhanden.

_ACP2E-4136 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Fehler mit doppelten Einträgen (temp_category_descendants_%)

Es wurde ein Problem mit doppelten Einträgen während der Erstellung geplanter Aktualisierungen für Umgebungen mit einer hohen Anzahl verschachtelter Kategorien behoben

_ACP2E-4159 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a1c57b2e)_

### Catalog, GraphQL

#### GraphQL: Ungültige Rabattberechnung

GraphQL zeigt jetzt Rabattprozentsätze und Basispreise korrekt an, wenn Katalogpreise so konfiguriert sind, dass sie Steuern beinhalten. Zuvor traten Rundungsfehler auf, z. B. wurden 19,99 % anstelle von 20 % angezeigt.

_ACP2E-3993 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Katalog, Produkt

#### Zugehörige Produkte über die zugehörige Produktregel werden nicht in der PDP über GraphQL angezeigt

Bevor diese Fehlerbehebung angewendet wurde, hat die relative Produktregel zuvor für ein Produkt, das mit der Regel übereinstimmte, leer/null zurückgegeben. Nachdem diese Fehlerbehebung angewendet wurde, gibt die relative Regel für das Produkt für übereinstimmende Produkte erfolgreich zurück.

_ACP2E-3949_

### Inhalt

#### GraphQL (Magento 2.4.6-P4 ) - Fehler beim Abrufen einer CMS-Seite mit dem Status Nicht aktiv .

Es wurde ein Problem behoben, bei dem die GraphQL-Abfrage für eine deaktivierte CMS-Seite einen internen Server-Fehler zurückgab.
Jetzt ruft die Abfrage eine korrekte Antwort ohne Fehler ab.

_AC-12302 - [GitHub-Problem](https://github.com/magento/magento2/issues/38877) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQL] Route-Abfrage mit Endlosschleife

Dieses Ticket behob das Problem, dass eine GraphQL-Routenabfrage mit identischem Anfragepfad und Zielpfad eine Endlosschleife verursachte und schließlich die Zeit überschritt.
In 2.4.9-alpha3 gibt die Abfrage jetzt die richtige Fehlerantwort zurück, anstatt eine Schleife zu durchlaufen.

_AC-14269 - [GitHub-Problem](https://github.com/magento/magento2/issues/39707) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ändern Sie für mehr Flexibilität das konstante IMAGE_FILE_NAME_PATTERN in public visible

Das konstante IMAGE_FILE_NAME_PATTERN in GenerateRenditions.php wurde veröffentlicht, um Entwicklern mehr Flexibilität bei der Arbeit mit Bildausgabedarstellungen zu ermöglichen. Die Fehlerbehebung ist in Magento 2.4.9-alpha3 mit vollständiger Abdeckung von Unit- und Integrationstests enthalten.

_AC-15338 - [GitHub-Problem](https://github.com/magento/magento2/issues/39733) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Die Vorschau des Inhalts-Staging funktioniert nicht mit Suchergebnissen

Die Suche in der Staging-Vorschau gibt jetzt Produkte entsprechend dem ausgewählten Bereich zurück. Zuvor wurden bei der Suche Ergebnisse im Standardbereich zurückgegeben, ohne Berücksichtigung des ausgewählten Speichers.

_ACP2E-4095_

#### Page Builder - Problem mit der Logik für Produktbedingungen (ODER-Logik zeigt falsch weniger Produkte an)

Das Page Builder-Produkt-Widget gibt jetzt das richtige Ergebnis zurück, wenn ein Attribut mit dem globalen Umfang in der Bedingung „Beliebige Übereinstimmung“ verwendet wird

_ACP2E-4096 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Kunde/Kunden

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

#### [Problem] Methodensignatur mit der Schnittstelle konsistent machen

Die Methodensignatur für getAttributes ist jetzt mit ihrer Schnittstelle konsistent und verhindert Fehler beim Überschreiben der Methode. Zuvor verursachten Inkonsistenzen in der Methodensignatur Fehler beim Versuch, die getAttributes-Methode zu überschreiben.

_AC-11578 - [GitHub-Problem](https://github.com/magento/magento2/issues/38501) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/31955)_

#### [Problem] Beheben der Regel „validate-emails“ für die UI-Komponente

Das System validiert nun mehrere in Benutzeroberflächenkomponenten eingegebene E-Mail-Adressen ordnungsgemäß, um sicherzustellen, dass jede E-Mail ordnungsgemäß zugeschnitten und validiert wird. Zuvor verwendete das System eine falsche Methode zum Zuschneiden von E-Mail-Adressen, was zu Validierungsfehlern führen konnte.

_AC-11719 - [GitHub-Problem](https://github.com/magento/magento2/issues/38528) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33470)_

#### [Problem] Entfernen redundanter Methoden

Code-Qualität: Redundante Methoden in Komponenten für asynchrone Vorgänge und Verkäufe wurden entfernt, die nur übergeordnete Methoden aufgerufen haben, ohne Funktionen hinzuzufügen. Dies verbessert die Code-Wartbarkeit.

_AC-11915 - [GitHub-Problem](https://github.com/magento/magento2/issues/29748) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/29147)_

#### Die XSD-Validierung schlägt in etc/adminhtml/system.xml-Dateien fehl, die Kommentare unterhalb von Feldelementen enthalten.

Diese PR behebt XML-Schemadefinitionen in PhpStorm für den Kommentarknoten

_AC-12945 - [GitHub-Problem](https://github.com/magento/magento2/issues/39148) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 verwendet Entwicklungspakete, die nicht der semantischen Versionierung folgen

Magento 2.4.8 erfordert dev-Versionen von pdepend/pdepend und phpmd/phpmd (3.x-dev) für die PHP 8.4-Kompatibilität.
Diese Entwicklungsversionen stehen im Konflikt mit Drittanbieter-Tools, die SemVer-kompatible Pakete erwarten, und verhindern einige Upgrades.
Eine temporäre Problemumgehung besteht darin, die Dev-Versionen in composer.json zu alias (z. B. „3.x-dev as 3.99.0„), um Kompatibilität zu ermöglichen und gleichzeitig die semantische Versionierung zu erfüllen.
Dies stellt die Unterstützung von PHP 8.4 sicher und vermeidet Konflikte, bis stabile Versionen verfügbar werden.

_AC-14519 - [GitHub-Problem](https://github.com/magento/magento2/issues/39796)_

#### Rest-API: Aufruf einer Memberfunktion getVideoProvider() auf null

Es wurde ein Problem behoben, bei dem der Aufruf der konfigurierbaren API für untergeordnete Produkte einen internen 500-Server-Fehler zurückgab, wenn ein untergeordnetes Produkt nur ein YouTube-Video und keine anderen Bilder hatte.
Der Fehler wurde durch einen Nullverweis im ExternalVideoEntryConverter verursacht.
Jetzt gibt die API untergeordnete Produkte mit Mediensammlungseinträgen, einschließlich externer Videodaten, korrekt zurück, ohne Fehler auszulösen.
Dadurch wird ein ordnungsgemäßer Abruf aller Medientypen für untergeordnete Produkte über die REST-API sichergestellt.

_AC-15046 - [GitHub-Problem](https://github.com/magento/magento2/issues/40021)_

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

#### Aktualisieren von Modul-Readmes und Korrigieren von Dokumenten-Links

_AC-15340 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec9459d0)_

#### [Problem] Nicht deklariertes Plug-in nur protokollieren, wenn es nicht deaktiviert ist

Diese PR behebt und protokolliert die Plug-ins, die tatsächlich nicht deklariert und nicht verwendet werden (aktivierte und fehlende Instanz).

_AC-15386 - [GitHub-Problem](https://github.com/magento/magento2/issues/40086) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, Magento/Framework, Version 103.0.8-p2: EmailMessage-Klasse, die eine nicht vorhandene Methode aufruft

_AC-15446 - [GitHub-Problem](https://github.com/magento/magento2/issues/40170) - [GitHub-Code-](https://github.com/magento/magento2/commit/059fd469) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Daten-/Schema-Patches getAliases() verursachen Fehler während der `setup:upgrade`

getAliases() verursacht Fehler während des Setups:upgrade und diese PR behebt dieselbe

_AC-15559 - [GitHub-Problem](https://github.com/magento/magento2/issues/31396) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38239)_

#### Erwarteter Typ &quot;Magento\Customer\Api\Data\GroupInterface&quot;. &#39;Magento\Customer\Model\Group&#39; gefunden.

Es wurde ein Problem behoben, bei dem das Speichern einer Kundengruppe über GroupRepositoryInterface mithilfe von GroupFactory einen Typfehler verursachte.
Zuvor hatte das Repository „GroupInterface“ erwartet, aber die Instanzen des Gruppenmodells wurden übergeben, was zu einem schwerwiegenden Fehler führte.
Kundengruppen können jetzt erfolgreich über das Repository gespeichert werden, indem eine ordnungsgemäße Implementierung der Schnittstelle sichergestellt wird.
Dadurch werden IDE-Warnungen und Laufzeitfehler beim programmgesteuerten Erstellen oder Aktualisieren von Kundengruppen behoben.

_AC-6909 - [GitHub-Problem](https://github.com/magento/magento2/issues/36269)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8349 - [GitHub-Problem](https://github.com/magento/magento2/issues/37266) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37016)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8350 - [GitHub-Problem](https://github.com/magento/magento2/issues/37265) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37015)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8359 - [GitHub-Problem](https://github.com/magento/magento2/issues/37262) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37012)_

#### [Problem] Unzulässiges `@author` entfernen

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8362 - [GitHub-Problem](https://github.com/magento/magento2/issues/37259) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37009)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Backup` und `Magento_Bundle`

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8367 - [GitHub-Problem](https://github.com/magento/magento2/issues/37244) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36979)_

#### [Problem] Variablennamen in der Katalogsuche beheben

Das System benennt nun Variablen im Suchmodul korrekt, was die Code-Klarheit und die Wartbarkeit verbessert. Zuvor wurde ein irrelevanter Variablenname, $defaultCountry, im Suchmodul verwendet, was zu Verwirrung führte.

_AC-9215 - [GitHub-Problem](https://github.com/magento/magento2/issues/37810) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]Server-Problem, das möglicherweise durch einen ungültigen S3-Zugriffsschlüssel verursacht wird

Falsche AWS S3-Anmeldeinformationen führen nicht mehr dazu, dass Seiten unendlich in der Storefront geladen werden.

_ACP2E-3890 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify funktioniert nicht

Die folgenden JS-Dateien werden jetzt vollständig und korrekt minimiert, wenn die JS-Minimierung aktiviert ist: mage/backend/tabs.min.j, jquery/jquery.validate.min.js und Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Daher funktioniert die CSS-Klassenfeldüberprüfung von Page Builder erwartungsgemäß.

_ACP2E-3925 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

#### Cron-Vorgang löscht die Datenbanktabelle nicht - verursacht Ausfall wegen Galera-Absturz

Die Bereinigung von Änderungsprotokolltabellen wird jetzt in Batches ausgeführt, um umfangreiche Löschvorgänge zu vermeiden.

_ACP2E-3995 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### Nicht minimierte JS lädt manchmal unter Ignorierung von „js-Minimierungen aktivieren“.

Vor der Fehlerbehebung wurden einige JS-Dateien ohne das Präfix „min“ angefordert, auch wenn Sie die Minimierung aktiviert hatten, was zu einem 404-Status-Code führte. Nach der Behebung werden bei aktivierter Minimierung keine nicht minimierten JS-Ressourcen angefordert.

_ACP2E-4058 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Datumsattribut in benutzerdefinierter Attributgruppe kann Datumsauswahl in Admin nicht anzeigen

Es wurde ein Problem behoben, bei dem das Kalender-Popup für Datumsattribute außerhalb des Bildschirms angezeigt wurde, wenn es benutzerdefinierten Attributgruppen zugewiesen wurde.

_ACP2E-4060 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### Kundenauftrag - GraphQL : Das Abrufen von Produktkategorien für das zugehörige Produkt ist „nicht einzeln sichtbar

Vor der Fehlerbehebung wurde in der GraphQL-Antwort der Kundenbestellung ein leeres -Array angezeigt, wenn die Bestellung ein ausgeblendetes Produkt enthielt.
Nach der Fehlerbehebung werden die Produktkategorien jetzt in die Antwort auf eine GraphQL-Anfrage zur Kundenbestellung aufgenommen, auch wenn das Produkt ausgeblendet ist.

_ACP2E-3945 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL, Inventar/MSI

#### Diskrepanzen bei GraphQL mergeCart-Mutation

Nach der Fehlerbehebung überprüft die GraphQL-Anfrage zum Zusammenführen von Warenkörben ordnungsgemäß die Produktmenge, wobei die Lagerkonfiguration berücksichtigt wird.

_ACP2E-4184 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Sicherheit

#### Das Zurücksetzen des Kundenkennworts über GraphQL berücksichtigt nicht die Einschränkungen.

Es wurde ein Problem behoben, bei dem Anfragen zum Zurücksetzen des Kundenkennworts, die durch GraphQL-Mutationen gesendet wurden, nicht den Kennwortrücksetzungsbeschränkungen entsprachen, die unter Store > Configuration > Customers > Customer Configuration > Password Options konfiguriert wurden. Diese Einstellungen werden nun korrekt durchgesetzt.

_ACP2E-3992 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### Import/Export

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

### Inventar/MSI

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

### Reihenfolge

#### Magento 2.4.8 GraphQL - Order items order_date falsch formatiert

Es wurde ein Problem behoben, bei dem das Feld order_date in der GraphQL-Antwort im Format JJJJ-MM-TT zurückgegeben wurde.
Jetzt wird das Datum order_date korrekt im Format TT-MM-JJJJ angezeigt.

_AC-14431 - [GitHub-Problem](https://github.com/magento/magento2/issues/39805) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Die Versand-E-Mail wird nicht gesendet, wenn sie über die Administrator-Bestellansicht gesendet wird, obwohl sie in der Store-Konfiguration aktiviert ist.

Das System sendet jetzt eine E-Mail zur Versandbestätigung, da sie in der Store-Konfiguration aktiviert ist, in der die Bestellung aufgegeben wurde.

_AC-14563 - [GitHub-Problem](https://github.com/magento/magento2/issues/39861) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39897)_

#### Das Filtern nach Datum funktioniert aufgrund mehrdeutiger Feldnamen nicht

In Magento 2.4.7-p6 wurde berichtet, dass das Filtern des Sortierungsrasters nach Datum einen Fehler aufgrund von Joins mit Braintree-Modulen verursacht.
Das Problem bestand darin, dass Abfragen beim Anwenden von Datumsfiltern die Tabellen braintree_transaction_details und sales_order schlossen.
Adobe Commerce Engineering hat den Fall geprüft, konnte den Fehler jedoch nicht in der Umgebung reproduzieren.
Erwartetes Verhalten ist, dass bei der Filterung nach Datum Bestellungen zurückgegeben werden sollten, die mit dem Filter übereinstimmen, ohne dass Fehler auftreten.

_AC-15037 - [GitHub-Problem](https://github.com/magento/magento2/issues/40024)_

#### Magento2: Promotion-Regel kann nicht erstellt werden

Diese PR-Fehlerbehebungen erhalten wir
Modell \Magento\Catalog\Model\ResourceModel\Eav\Attribute anstelle von \Magento\Catalog\Model\ResourceModel\Eav\Attribute in der Methode \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [GitHub-Problem](https://github.com/magento/magento2/issues/12176) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30479)_

#### Rechnungsumleitungen stornieren auf 404

Die Stornierung der Rechnung, die mit dem Nicht-Erfassung-Typ erstellt wurde, führt nicht mehr zu Seite 404.

_ACP2E-4001 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Verkaufsarchiv Cron-Aufträge verursachen Probleme mit der DB-Sperrung

Vor der Fehlerbehebung verursachten ungebundene DELETE-Abfragen im Auftragsarchiv Cron Probleme mit Galera. Nach der Aktualisierung werden Löschabfragen jetzt mit Einschränkungen ausgeführt.

_ACP2E-4010_

#### Problem mit aktualisierten Bestellungen mit konfigurierbaren Optionen unter Verwendung der REST-API

Vorhandene Produktoptionen für Kundenauftragselemente beibehalten, wenn eine Bestellung über REST-API-Endpunkte aktualisiert wird.

_ACP2E-4061 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### Andere Entwickler-Tools

#### [Problem] Nicht verwendeten Code bereinigen.

Das System entfernt jetzt nicht verwendeten Code für die nicht verwendeten Importe.

_AC-10980 - [GitHub-Problem](https://github.com/magento/magento2/issues/38424) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33499)_

#### [Problem] Barrierefreiheit: WAI-ARIA-Rollen verschachteln falsch im Menü

Das System generiert jetzt Lighthouse-Barrierefreiheit ohne WAI-ARIA-Rollen, die im Menüfehler falsch verschachtelt sind, und der Bericht sollte grün sein

_AC-15082 - [GitHub-Problem](https://github.com/magento/magento2/issues/40045) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38617)_

#### Konsolenfehler in der E-Mail-Vorschau im Magento-Admin

Das System gibt bei der Vorschau der E-Mail-Vorlage keinen Konsolenfehler aus

_AC-9245 - [GitHub-Problem](https://github.com/magento/magento2/issues/37820) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37933)_

### Zahlungen

#### Unbekannte IPNs von PayPal missbrauchen Anwendung IPN-Prozessor

Der IPN-Handler ignoriert jetzt nicht unterstützte oder unbekannte IPN-Typen. Anstatt einen 500-Fehler zurückzugeben, wird das Problem protokolliert und die Verarbeitung ohne Unterbrechung fortgesetzt.

_ACP2E-4049 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro gespeichertes Karten-Token bei Zahlung fehlgeschlagen

PayPal PayFlow Pro-Transaktions-IDs (PNREFs) sind jetzt für einen festen Zeitraum von 12 Monaten für die Verwendung in Referenztransaktionen gültig. Nach Ablauf wird die gespeicherte Karte nicht mehr angezeigt und muss erneut hinzugefügt werden. Zuvor wurde die Gültigkeit durch das Ablaufdatum der in der ursprünglichen Transaktion verwendeten Zahlungskarte bestimmt.

_ACP2E-4064 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

### Leistung

#### [Problem] Aktualisierung der Cache-Steuerung für statische Site unveränderlich

Diese PR sorgt für eine Leistungsverbesserung, indem sie den statischen Inhalt erst dann beim Laden der Seite validiert, wenn sich der Inhalt geändert hat.

_AC-15171 - [GitHub-Problem](https://github.com/magento/magento2/issues/39486) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39484)_

#### [CLOUD] Produkte können nicht zu Kategorien hinzugefügt werden

Verbesserte Leistung beim Hinzufügen von Produkten zur Kategorie über Visual Merchandiser.

_ACP2E-3946 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate über 10.000 Protokolle

Zuvor wurde der Cache bei jedem PLP- oder Cart-Besuch gelöscht, was zu unnötigem Leistungsaufwand führte. Der Cache der Zielregel wird auf diesen Seiten nicht mehr ungültig, was die Browser-Effizienz verbessert.

_ACP2E-4059_

### Preisgestaltung

#### Das Produkt wird gespeichert, selbst wenn der Sonderpreis ab Datum mithilfe einer Massenaktion nach Bis Datum liegt.

Es wurde ein Problem behoben, bei dem Produkte mit einem ungültigen Datumsbereich für Sonderpreise ohne Validierung gespeichert werden konnten.
Jetzt wird eine Fehlermeldung angezeigt: „Stellen Sie sicher, dass das „Bis“-Datum nach oder mit dem „Von“-Datum übereinstimmt.“

_AC-15252 - [GitHub-Problem](https://github.com/magento/magento2/issues/40113) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Versanddetails stimmen nicht überein, nachdem PayPal Express-Checkout für ein verhandelbares Angebot abgeschlossen wurde.

Dieses Problem behob eine Diskrepanz bei den Versandkosten beim Abschluss eines PayPal Express-Checkouts für ein genehmigtes verhandelbares Angebot.
Vor der Fehlerbehebung wurde der Versand fälschlicherweise verdoppelt (10 US-Dollar statt 5 US-Dollar), was zu überhöhten Gesamtwerten führte.
Die Fehlerbehebung in Magento 2.4.9-alpha3 stellt sicher, dass die richtigen Versandkosten angewendet werden

_AC-15280_

#### Bei Websites mit unterschiedlichen Zeitzonen wird der Sonderpreis nicht berücksichtigt

Vor der Fehlerbehebung wurde das Gültigkeitsdatum des Sonderpreises im Gültigkeitsbereich des aktuellen Zeitstempels des Stores erstellt. Nach der Fehlerbehebung wird nun die standardmäßige Zeitzone des Speichers berücksichtigt.

_ACP2E-4002_

#### Regulärer Preis ist nicht sichtbar, obwohl ein Sonderpreis gilt.

Es wurde ein Problem behoben, bei dem der reguläre Preis nicht angezeigt wurde, wenn ein Sonderpreis angewendet wurde. Der reguläre Preis erscheint nun korrekt neben dem Sonderpreis wie erwartet.

_ACP2E-4100 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/47721be6)_

### Produkt

#### Für ein konfigurierbares Produkt wird für den Testfall AC-6158 weiterhin die Bezeichnung „So niedrig wie“ angezeigt

Implementierte und verifizierte konfigurierbare Produkte (P1-P7) mit entsprechenden Varianten und Kategoriezuweisungen. Sichergestellt, dass der Preis der Storefront korrekt angezeigt wird und das Etikettenverhalten für Produkte der Kategorie C „So niedrig wie“ ist.

_AC-10847 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Zusätzliche Protokollierung bei Anforderung eines Produkts über das Repository schlägt fehl

Verbesserte Fehlermeldungen für ProductRepository::get und getById, wenn keine SKU oder ID gefunden wird.
Zuvor boten Ausnahmen keinen Kontext darüber, welche SKU oder ID den Fehler verursacht hat.
Jetzt enthält die Ausnahmemeldung die fehlende SKU oder ID, was beim Debugging hilft und das Entwicklererlebnis verbessert.
Diese Änderung wirkt sich nicht auf das funktionale Verhalten der API aus.

_AC-15199 - [GitHub-Problem](https://github.com/magento/magento2/issues/40090) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Zuweisung von einfachen Produkten aufgehoben, wenn konfigurierbares Produkt durch eingeschränkte Rolle bearbeitet

Vor dieser Fehlerbehebung wurde ein konfigurierbares Produkt, das einfache Produkte enthält, auf die der Admin-Benutzer keinen Zugriff hatte, beim Speichern aus dem konfigurierbaren Produkt entfernt, wenn ein Benutzer mit eingeschränktem Administratorzugriff dieses Produkt speichern würde. Nach der Fehlerbehebung wird das konfigurierbare Produkt als von einem Volladministrator gespeichert beibehalten.

_ACP2E-4081_

#### [Cloud] Die Leistung bei der Sitemap-Generierung ist erheblich beeinträchtigt

Die Sitemap-Generierung für Produkte mit Bildern erlebt keine exponentielle Verlangsamung mehr. Zuvor führte das Generieren von Sitemaps für Stores mit aktivierter Bildeinbindung zu langen Verarbeitungszeiten.

_ACP2E-4153 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Promotion

#### Fehler beim Abrufen der Rabatte für Bestellartikel, die auf die Kundenbestellung über die GraphQL-Kundenanfrage angewendet wurden

Zuvor, als ein interner Server-Fehler mit angewendeten Rabatten für die Kundenbestellung über die GraphQL-Kundenanfrage beobachtet wurde, der jetzt behoben ist und korrekte Kundenbestellungsdaten mit angewendetem Rabatt abgerufen werden

_AC-14888 - [GitHub-Problem](https://github.com/magento/magento2/issues/39963) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fe72c407)_

#### Fehler beim Abrufen des Gutscheincodes für einen Bestellartikel für eine Kundenbestellung über die GraphQL-Kundenanfrage

Es wurde ein Problem behoben, bei dem beim Abrufen von Bestellungen mit Coupondetails über GraphQL ein interner Server-Fehler zurückgegeben wurde.
Jetzt wird die Abfrage erfolgreich ausgeführt und gibt die richtigen Couponinformationen in der Antwort zurück.

_AC-14889 - [GitHub-Problem](https://github.com/magento/magento2/issues/39962) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Nicht definierter Array-Schlüssel in ProductRepository getById

Das Problem trat auf, wenn ProductRepository::getById() mit einer ungültigen ID wie 123abc aufgerufen wurde, was zu einem Fehler „Undefinierter Array-Schlüssel“ führte.
Nach der Fehlerbehebung in Magento 2.4.9-alpha3 geben solche Anfragen jetzt korrekt eine 404-Seite zurück, anstatt eine Ausnahme auszulösen.
Die Qualitätssicherung wurde mit gültigen und falsch formatierten IDs bestätigt, und es wurden keine weiteren Probleme festgestellt.

_AC-15345 - [GitHub-Problem](https://github.com/magento/magento2/issues/40146) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### [Cloud] Sitemap-Generierung endet nie

Vor der Korrektur konnte die Sitemap-Generierung nicht erfolgreich abgeschlossen werden, wenn der Katalog mehr als eine Million Produkte enthielt. Nach der Fehlerbehebung wird die Sitemap-Generierung mit geringerer Speicherzuweisung und mit bis zu einer Million Produkten pro Geschäft abgeschlossen.

_ACP2E-3902 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud] Store Switcher funktioniert nicht von EN nach FR für die FAQ-Seite

Fehlerkorrektur - Beim Wechseln zwischen Store-Ansichten werden Benutzer nicht mehr zur entsprechenden übersetzten CMS-Seite, sondern auf die Homepage umgeleitet. Der Store-Umschalter sucht jetzt im Ziel-Store nach URL-Neuschreibungen, um eine korrekte Umleitung sicherzustellen (z. B. die FAQ-Seite auf Englisch → die FAQ-Seite auf Französisch).

_ACP2E-4112_

### Staging und Vorschau

#### Bei Verwendung einer anderen Admin-Domain funktioniert die Vorschau des Staging-Updates nicht mehr beim Checkout

Eine Kundin oder ein Kunde kann sich anmelden und ihren Warenkorb im Store-Vorschaumodus anzeigen, wenn sich die Store-Basis-URL von der Admin-URL unterscheidet.

_ACP2E-3906_

#### Staging-Dashboard für Inhalte - Anzeige der Zeit falsch

Jetzt zeigen die Datumsfilter „Start Time“ und „End Time“ im „Content Staging Dashboard“ das richtige Datum und die richtige Uhrzeit an. Zuvor wurde nach Auswahl von Datum und Uhrzeit in der Datumsauswahl ein falsches Datum und eine falsche Uhrzeit angezeigt

_ACP2E-3969_

#### Der Umfang zeigt während der Vorschau für Produkte und Kategorien für geplante Updates unterschiedliche Shop-Ansichten an.

Zuvor wurde der Vorschau-Link für Kategorien und Produkte nicht für den richtigen Store generiert. Nach dieser Fehlerbehebung wählt der Vorschau-Link automatisch den Store aus, in dem die Vorschau erstellt wurde.

_ACP2E-4053_

### UI-Framework

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Backend`

Dieser PR entfernt `@author` Tag aus der Codebasis

_AC-8814 - [GitHub-Problem](https://github.com/magento/magento2/issues/37522) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36976)_
