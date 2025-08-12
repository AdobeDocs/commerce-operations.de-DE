---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4173'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.9-alpha2)

## Behobene Probleme in v2.4.9-alpha2

Es wurden 109 Probleme im Magento Open Source 2.4.9-alpha2-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

#### Sonderpreis Bis dato wird bei applySpecialPrice falsch validiert

Das System funktioniert einwandfrei bezüglich des Sonderpreises. Der Sonderpreis für das Produkt läuft an dem Datum ab, das vom Administrator oder dem Drittanbietersystem durch die REST-API festgelegt wurde

_AC-13130 - [GitHub-Problem](https://github.com/magento/magento2/issues/39169) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39690)_

#### Fehlerhafter Anfragetext oder fehlerhafte Parameter verursachen „Interner Server-Fehler“

_AC-746 - [GitHub-Problem](https://github.com/magento/magento2/issues/32784) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### Bestellung „base_row_total“ und „row_total“ zeigen in der REST-API-Antwort einen einzelnen Artikelpreis an

Die REST-API-Antwort für Auftragsdetails enthält jetzt die korrekten Werte für die Attribute „base_row_total“ und „row_total“, falls mehrere gleiche Artikel bestellt wurden

_ACP2E-3874 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

### APIs, Reihenfolge

#### [CLOUD] Problem mit Bestellinformationen, wobei die Zeile für die 000075568 insgesamt angezeigt wird

Es wurde das Problem behoben, bei dem der Wert row_total_incl_tax in der Antwort der Auftrags-API als Restwert von nahezu null anstelle von 0,00 zurückgegeben wurde, wenn ein Element vollständig diskontiert wurde.

_ACP2E-3950 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### Konto

#### Problem beim Aktualisieren der Kunden-E-Mail im Admin Panel mit der Domain ö und .swiss

_AC-13409 - [GitHub-Problem](https://github.com/magento/magento2/issues/39394) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### Schalter zum Abonnieren von Newslettern aktiviert funktioniert nicht pro Website/Store

Das System verwaltet die Anmeldung für Newsletter korrekt, wenn mehrere Websites/Storeviews vorhanden sind, obwohl diese global deaktiviert wurden

_AC-14283 - [GitHub-Problem](https://github.com/magento/magento2/issues/39751) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39752)_

#### [Problem] Entfernte E-Mail-Offenlegung

Das System zeigt jetzt eine Fehlermeldung an, die auf eine falsche E-Mail hinweist, wenn die eingegebene E-Mail nicht zur Bestätigung des Kontos erforderlich ist, unabhängig davon, ob der Kunde existiert oder nicht.

_AC-14561 - [GitHub-Problem](https://github.com/magento/magento2/issues/39574) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39570)_

### Admin-Benutzeroberfläche

#### Der FTP-Wert auf der Warenkorbseite und der Produktseite unterscheidet sich für dieselben Konfigurationen für einfache Produkte.

_AC-13066 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8953613e)_

#### Die Optionen für Mehrfachauswahl-/Attributauswahl können nicht gespeichert werden, wenn die Farbfelder-Module deaktiviert sind

_AC-13071 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8953613e)_

#### Der FTP-Wert auf der Warenkorbseite und der Produktseite unterscheidet sich bei denselben Konfigurationen für ein dynamisches Produkt

_AC-13075 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8953613e)_

#### Hover-Farbe nicht auf statische Raster in Admin angewendet

Hover-Farben werden jetzt erwartungsgemäß auf die Zeilen der statischen Admin-Raster angewendet.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub-Problem](https://github.com/magento/magento2/issues/35358) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35384)_

#### [Staging2] Gespeicherte Karten sind im Admin-Bedienfeld nicht sichtbar

Es wurde ein Problem behoben, bei dem die Zahlungsoption „Gespeicherte Karte“ nach einem Upgrade nicht mehr im Formular für die Platzierung von Backend-Bestellungen angezeigt wurde.

_ACP2E-3830 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### Die Überprüfung des Unternehmensfelds schlägt für den Gast-Checkout fehl

_AC-14987 - [GitHub-Problem](https://github.com/magento/magento2/issues/40011) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f1adb44e)_

### Bündel

#### Ausschließen von Huberte Editor JS-Dateien aus der gebündelten Ausgabe über Designs hinweg

_AC-15128 - [GitHub-Code-](https://github.com/magento/magento2/commit/43648891) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2bc584af)_

### Warenkorb und Checkout

#### Validierungen der Frontend-Menge für gruppierte Produkte fehlen

Das System funktioniert jetzt einwandfrei und zeigt einen Validierungsfehler an, wenn wir versuchen, negative und maximale Mengen hinzuzufügen

_AC-13524 - [GitHub-Problem](https://github.com/magento/magento2/issues/39479) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39480)_

#### Gastpräfix nicht in Anführungsadresse 2.4.8 gespeichert

_AC-14705 - [GitHub-Problem](https://github.com/magento/magento2/issues/39915) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### [Problem] Festlegen des Preises für einen Angebotselement anstelle des Basispreises

Das System verarbeitet den Preis des Angebotselements korrekt, der auf den base_price statt auf den Preis gesetzt wird, wenn mehrere Währungen auf einer Website im Frontend vorhanden sind

_AC-9985 - [GitHub-Problem](https://github.com/magento/magento2/issues/38094) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36878)_

#### [Cloud] Letzte Bestellungen werden nicht in der anderen Shop-Ansicht angezeigt, wenn die Bestellungen in einer Shop-Ansicht erstellt wurden

Es wurde ein Problem behoben, bei dem auf der Seite „Mein Konto“ keine aktuellen Bestellungen aus anderen Store-Ansichten innerhalb desselben Stores angezeigt wurden. Die Logik zum Abrufen von Bestellungen wurde aktualisiert, um eine konsistente Sichtbarkeit der Bestellung über alle Store-Ansichten hinweg sicherzustellen. Dies entspricht dem Verhalten der Seite „Meine Bestellungen“.

_ACP2E-3807 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Anzeige der Menge als  0 im Admin-Warenkorbabschnitt des Kunden beim Hinzufügen von BUNDLE-Produkten  

Im Abschnitt Warenkorb in Kundenaktivitäten wird jetzt die richtige Menge angezeigt. Zuvor wurde die Menge als 0 angezeigt.

_ACP2E-3872 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Warenkorb und Checkout, GraphQL

#### Fehler bei der Zuordnung der Nachricht zum Fehlercode bei der Bestellung über GraphQL

GraphQL-Aufrufe zum Aufgeben einer Bestellung für einen nicht vorhandenen oder inaktiven Warenkorb geben jetzt korrekt die Fehler-Codes „CART_NOT_ACTIVE“ oder „CART_NOT_FOUND“ in allen Store-Ansichten zurück. Damit wird ein Problem behoben, bei dem übersetzte Fehlermeldungen zuvor zu einem „UNDEFINIERTER“ Code geführt haben.

_ACP2E-3942 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

### Warenkorb und Checkout, GraphQL, Inventar / MSI

#### Das Attribut is_available in CartItemInterface gibt „false“ zurück, selbst wenn der verkaufbare Bestand hoch ist.

Das Attribut is_available gibt „true“ zurück, wenn das verkäufliche Lager hoch ist. Zuvor wird immer „false“ zurückgegeben.

_ACP2E-3885 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Katalog

#### Umfang des Fehlers in der Katalog-URL-Ressource (_getCategories)

Diese PR fügt einen Fallback zum Standardbereich hinzu, wenn für den Store-Bereich in der Kategorie-URL-Ressource kein Wert definiert ist.

_AC-11011 - [GitHub-Problem](https://github.com/magento/magento2/issues/38393) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38394)_

#### [Problem] Überprüfen, ob OpenGraph den Preis anzeigen kann

Das System funktioniert einwandfrei, wenn wir ein Plugin verwenden, das den Preis ausblendet und mit dieser Änderung ist der Preis nicht im OG-Tag sichtbar.

_AC-11635 - [GitHub-Problem](https://github.com/magento/magento2/issues/38512) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38510)_

#### [Bug] REST-API: Die Aktualisierung von Sonderpreisen legt keine Werte für alle Store-Ansichten fest

_AC-13671 - [GitHub-Problem](https://github.com/magento/magento2/issues/39521) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP-Fehler nicht bemerkt

Diese PR Ändern Sie einen Schleifenvariablennamen, um die „_cache_instance_product_ids“-Daten auf dem angegebenen Produkt korrekt hinzuzufügen, die bei nachfolgenden Aufrufen verwendet werden sollen.

_AC-14159 - [GitHub-Problem](https://github.com/magento/magento2/issues/39641) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [CLOUD] Das Ändern der Bildgröße verbraucht mehr als 400 GB Festplattenspeicher

Nach der Fehlerbehebung generiert der `catalog:images:resize`-Befehl, der mit dem Flag —skip_hidden_images verwendet wird, keine Bild-Caches für Websites, auf denen Bilder nicht vorhanden sind.

_ACP2E-3869 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### Bereitgestellte Länder-ID existiert nicht - Irland (IE)

Nach der Fehlerbehebung stehen Postleitzahlen für Irland zur Verfügung, um Abholstandorte zu suchen.

_ACP2E-3932 - [GitHub-Code-](https://github.com/magento/magento2/commit/4ca73607) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Katalog, Leistung

#### Kategorien in Admin werden sehr langsam geladen

Die Leistung beim Laden von Kategorien wurde deutlich verbessert. Zuvor dauerte es so lange, die Kategorie zu laden, die ein Zeitüberschreitungsproblem verursacht hat.

_ACP2E-3891 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

### Katalog, Preise

#### Falscher Rabatt für Katalogpreisregel auf das untergeordnete Produkt angewendet

Es wird das Problem behoben, bei dem die Katalogpreisregel für die Variante vom übergeordneten konfigurierbaren Produkt überschrieben wird, wenn beide Regeln dieselbe Priorität haben.

_ACP2E-3693 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/a20a6ff2)_

### Katalog, Suche

#### Die RestAPI-Anfrage &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; schlägt mit einem Zeitüberschreitungsfehler fehl

_AC-13358 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

### Inhalt

#### Nach dem Upgrade auf Magento 2.4.7 p2 kann nicht sehen, neu hochgeladene Dateien Media Gallery

_AC-13262 - [GitHub-Problem](https://github.com/magento/magento2/issues/39275)_

#### Wenn Sie ein gallery-image vollständig aus dem Bereich entfernen, bleiben Rollen/Typen (Basis/Klein/Miniatur) festgelegt und nach dem erneuten Hinzufügen „alter“ Rollen/Typen erscheinen

Das System funktioniert wie erwartet In den Speicherbereichen übernehmen die Bilder die Rollen/Typen des neu hinzugefügten Bildes gemäß dem Standardbereich

_AC-13556 - [GitHub-Problem](https://github.com/magento/magento2/issues/39481) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39680)_

#### [Kleiner Fehler] Filter der Admin-Panel-`listing component` kann nicht aufgerufen werden, wenn der Feldwert `\` enthält

Das System funktioniert einwandfrei, wenn wir Seitentitel mit Schrägstrich filtern (z. B.: Magento\Store)

_AC-13661 - [GitHub-Problem](https://github.com/magento/magento2/issues/39513) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39535)_

#### „Die CMS-Seite mit der ID „0“ existiert nicht“ Protokollflut

Das System funktioniert wie erwartet, nachdem ein Admin-Benutzer erstellt wurde und wenn eine neue Seite erstellt wird, gibt system.log keine Fehlermeldungen

_AC-14254 - [GitHub-Problem](https://github.com/magento/magento2/issues/39743) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39746)_

#### Kataloglink-Widgets verwenden eine falsche URL

Das System verarbeitet Widgets jetzt korrekt, nachdem ein Katalog-Produkt-Link und ein Katalog-Kategorie-Link hinzugefügt wurden, und es zeigt auch die richtigen URLs in der HTML-Quelle an

_AC-14437 - [GitHub-Problem](https://github.com/magento/magento2/issues/39464) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39710)_

#### Die Produktkomponente von Page Builder funktioniert nicht, wenn der Benutzer keine Widget-Berechtigung hat

Vor der Behebung gab es auf der Seite beim Zugriff auf ein Widget ohne Berechtigungen einen allgemeinen Fehler und die GIF „wird geladen“. Nach der Fehlerbehebung wird ein modales Fenster mit der Meldung angezeigt, dass Sie zum Anzeigen dieses Inhalts Berechtigungen benötigen. Nachricht.

_ACP2E-3664 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Die Reihenfolge der Produkt-Widgets von Page Builder wird in GraphQL nicht angewendet

Es wurde ein Problem behoben, bei dem die GraphQL-Antwort auf die Abfrage „route“ Produkte innerhalb des Inhaltstyps Page Builder-Produkte nicht in der richtigen Sortierreihenfolge zurückgab.

_ACP2E-3898 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problem mit der Preisanzeige an nicht englischen Storefronts aufgrund der Version der ICU-Bibliothek

Nach der Fehlerbehebung wird der Produktpreis im hebräischen Gebietsschema (Israel) korrekt angezeigt.

_ACP2E-3938 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Aktualisieren der vom Store-Code bereinigten Design-Konfiguration

Es wurde ein Problem behoben, bei dem durch die Aktualisierung des Code für die Store-Ansicht die Design-Konfigurationseinstellungen gelöscht wurden, da der Konfigurations-Cache nicht ordnungsgemäß aktualisiert wurde.

_ACP2E-3941 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### Framework

#### Fehler beim Ausführen des Befehls „setup:upgrade mit benutzerdefiniertem DB-Trigger

_AC-11487 - [GitHub-Problem](https://github.com/magento/magento2/issues/38481)_

#### Formular einer Website/Gruppe/Store-Entität kann nicht mit einem Formularelement mit mehreren Werten für Erweiterungsattribute erweitert werden

Diese PR ermöglicht es mehrwertigen Formularelementen, Daten an ein Website-/Gruppen-/Store-Formular zu senden.

_AC-11657 - [GitHub-Problem](https://github.com/magento/magento2/issues/24070) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/24094)_

#### [Problem] Verwendung des Bereichsauflösers entfernen

Diese PR löst die Admin-URL-Einstellungen global anstelle des aktuellen Speichers auf

_AC-11736 - [GitHub-Problem](https://github.com/magento/magento2/issues/38566) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38554)_

#### Offenlegung der Magento-Version über die Einrichtungsroute mit der standardmäßigen Nginx-Konfiguration

Das System funktioniert jetzt erwartungsgemäß und zeigt nicht die genaue Version von Magento an, die auf der Site ausgeführt wird

_AC-13205 - [GitHub-Problem](https://github.com/magento/magento2/issues/39227) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39228)_

#### [Problem] Angebotsadresse refaktorieren Methode nicht validieren

Diese PR enthält Verbesserungen der Lesbarkeit der doValidate-Methode.

_AC-13214 - [GitHub-Problem](https://github.com/magento/magento2/issues/38230) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38219)_

#### Magento Option —magento-init-params nie verwendet, wenn CLI ausgeführt wird?

_AC-13231 - [GitHub-Problem](https://github.com/magento/magento2/issues/39248) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue - Falsche Typdeklaration

Das System definiert nun in der Funktion getItemsByColumnValue den Eingabeparameter $value als primitiven Typ, nicht als Array, und stellt sicher, dass die Funktion die erwartete Auflistung zurückgibt. Wenn zuvor ein Array mit einem einzelnen Wert als Eingabeparameter verwendet wurde, gab die Funktion null zurück und IDEs markierten dies als Fehler.

_AC-13240 - [GitHub-Problem](https://github.com/magento/magento2/issues/33070) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33120)_

#### Mit FPC verknüpfte Cache-Schlüssel in Magento 2.4.7-Implementierungen mit mehreren Speichern

_AC-13719 - [GitHub-Problem](https://github.com/magento/magento2/issues/39456) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ae6f305b)_

#### Bereitstellen von personenbezogenen Daten durch die Magento REST-API

_AC-13904 - [GitHub-Problem](https://github.com/magento/magento2/issues/39336)_

#### Partielle Indizierung funktioniert nicht mehr für Kunden mit einer großen Anzahl von Aktualisierungen.

_AC-14424 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Untersuchen, ob „Verwendung streng“ innerhalb von Modulen nicht erforderlich ist

_AC-14517 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/77c589a6)_

#### Der MView-Mechanismus ignoriert Fehler bei der Ausführung von Triggern im Hintergrund

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

#### [Problem] Entfernen von Code im Zusammenhang mit Microsoft IIS

Diese PR bereinigt den Code im Zusammenhang mit Microsoft IIS gemäß der Magento-Systemanforderungsdokumentation, die besagt, dass das Microsoft Windows-Betriebssystem nicht unterstützt wird

_AC-14702 - [GitHub-Problem](https://github.com/magento/magento2/issues/39910) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js-Syntaxfehler

Die Funktion „Systemvergrößerung“ sollte weiterhin so funktionieren wie zuvor, und „Vergrößerungsoptionen“ sollte nicht global verfügbar sein

_AC-14722 - [GitHub-Problem](https://github.com/magento/magento2/issues/36200) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39321)_

#### Backport Verbose-Modus `setup:db:status` CLI-Befehl

_AC-14807 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### SMTP-Mail-Versand mit TLS und 2.4.8

_AC-14883 - [GitHub-Problem](https://github.com/magento/magento2/issues/39947) - [GitHub-Code-](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8b453942) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problem] Beheben eines Gleichzeitigkeitsproblems bei der Bereitstellung statischer Inhalte

Diese PR behebt einen Fehler, bei dem mehrere gleichzeitige Prozesse sich drehen, um dasselbe Design-Paket zu verarbeiten, je nachdem, wie die Designs mit ihren übergeordneten Elementen definiert werden.

_AC-14944 - [GitHub-Problem](https://github.com/magento/magento2/issues/39990) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39954)_

#### [Problem] Legacy-Kompatibilitätscode für PHP-Versionen &lt; 8.1 entfernen

Diese Pull-Anfrage entfernt Code, der für die Ausführung auf PHP &lt;8.1 entwickelt wurde.
Auch entfernt Prüfungen für PHP_VERSION_ID Kontakt Verfügbarkeit, da es in allen PHP-Versionen verfügbar ist

_AC-14971 - [GitHub-Problem](https://github.com/magento/magento2/issues/39891) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39882)_

#### FPC funktioniert nicht bei der Anmeldung

_AC-14999 - [GitHub-Problem](https://github.com/magento/magento2/issues/40007) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/)_

#### [Problem] Verbesserung der Fehlerbehandlung in SchemaBuilder

Diese PR verbessert die Handhabung von Fehlermeldungen des DB-Schemas. Dies hilft uns, ein Problem zu identifizieren, ohne dass umfangreiche Debugging-Maßnahmen erforderlich sind.

_AC-15020 - [GitHub-Problem](https://github.com/magento/magento2/issues/39816) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39799)_

#### Fehler beim Integrationstest für SYNC PR für 2.4.9-alpha2-develop aufgrund von CliStateTest.

_AC-15136 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2d0f8066)_

#### PHP8.1 Typ Fehlerbehebung

Die zugehörigen Produkte werden jetzt in ein leeres -Array anstelle von „false“ initialisiert, wenn der strikte Verarbeitungsmodus nicht aktiv ist oder wenn Produktinformationen verfügbar sind. Durch diese Änderung wird sichergestellt, dass sich die nachfolgende Logik bei der Handhabung zugehöriger Produkte konsistent verhält und die Stabilität und Vorhersagbarkeit im Produktvorbereitungsprozess verbessert wird.

_AC-6017 - [GitHub-Problem](https://github.com/magento/magento2/issues/35808) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/35842)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus dem Framework (Teil 3)

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8343 - [GitHub-Problem](https://github.com/magento/magento2/issues/37270) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37020)_

#### [Problem] Verwenden der Konstruktor-Eigenschaftsförderung im Modul „Freund senden“ in GraphQL

Das System verwendet jetzt die Konstruktoreigenschaftsförderung im GraphQL-Modul „Freund senden“, wodurch die Code-Lesbarkeit verbessert und die Komplexität reduziert wird. Zuvor verwendete das Modul Eigenschaften, die zahlreiche Zeilen belegten, was den Code komplexer und weniger lesbar machte.

_AC-8346 - [GitHub-Problem](https://github.com/magento/magento2/issues/37235) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37197)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Downloadable`

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8355 - [GitHub-Problem](https://github.com/magento/magento2/issues/37251) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37001)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich jetzt an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, was die Code-Qualität und -Konsistenz verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8358 - [GitHub-Problem](https://github.com/magento/magento2/issues/37264) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37014)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich jetzt an die Codierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, was die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8360 - [GitHub-Problem](https://github.com/magento/magento2/issues/37261) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37011)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um einen saubereren und standardisierten Code zu gewährleisten. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8361 - [GitHub-Problem](https://github.com/magento/magento2/issues/37260) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37010)_

#### [Problem] Unzulässiges `@author` entfernen

Das System hält sich nun an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt und so die gesamte Code-Qualität verbessert. Bisher verstieß das Vorhandensein dieses Tags in einigen Modulen gegen die etablierten Kodierungsstandards.

_AC-8363 - [GitHub-Problem](https://github.com/magento/magento2/issues/37258) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37008)_

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

#### Problem mit dem Upgrade 2.4.7-p5 aufgrund einer hinzugefügten neuen Validierung

Es wurde ein Problem in der SchemaBuilder-Klasse behoben, bei dem eine nicht definierte Array-Schlüssel-„Spalte“ während der Schemaerstellung oder -aktualisierungen einen Absturz verursachte. Dies trat bei der Verarbeitung von Tabellendaten auf, die keinen Schlüssel „Spalte“ enthielten.

_ACP2E-3871 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4 Veraltungsfehler: E_USER_ERROR nach der Aktualisierung auf Adobe Commerce 2.4.8

Kundenorientierte Szenarien sind von der Fehlerbehebung nicht betroffen.

_ACP2E-3963 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

### Framework, Suche

#### OpenSearch 2.19.1 Illegal_Argument_Exception auf Einpreiskategorien

OpenSearch löst für die Kategorien, die alle Produkte mit demselben Preis enthalten, kein Illegal_Argument_Exception mehr aus. Zuvor hatte sie die Ausnahme &quot;[from] Parameter darf nicht negativ sein“.

_ACP2E-3896 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Artikel auf der Wunschliste werden in GraphQL-Anfragen nicht zwischen Storeansichten innerhalb einer Website geteilt

Vor der Fehlerbehebung wurden Wunschlistenelemente nach Store-ID gefiltert. Nach der Fehlerbehebung werden jetzt die Elemente der Wunschliste nach Website gefiltert.

_ACP2E-3987 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, Produkt

#### Fehlender media_type in MediaGalleryInterface in Produktgraphql

Die GraphQL-Anfrage von MediaGallery enthält jetzt das Feld „Typen“ für Produktbildtypen. Zuvor war dieses Feld „Typen“ in der MediaGallery-GraphQL-Anfrage nicht vorhanden.

_ACP2E-3880 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Inventar/MSI

#### Nach der Umleitung zur Startseite und dem Checkout ist kein Store verfügbar

Zuvor ausgewählter Store wird jetzt im Versand „Pick-in-Store“ vorausgewählt, wenn der Kunde zur Zahlungsseite navigiert, dann zur Startseite zurückkehrt und schließlich zur Checkout-Seite zurückkehrt. Zuvor wurde nach wiederholter Rückkehr zur Kaufbestätigungsseite der ausgewählte Store im „Pick-in-Store“ gelöscht.

_ACP2E-3793 - [GitHub-Code-](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/62c0d79b)_

### Reihenfolge

#### AbstractAddress(setData(&#39;custom_attributes&#39;, AttributeValue[]) bricht customAttributes

_AC-10568 - [GitHub-Problem](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento-Neuanordnung -1 Bestellnummern

Das System funktioniert wie erwartet und nach der Neuanordnung über das Backend wird die Bestellnummer eindeutig 8 Stellen sein

_AC-12854 - [GitHub-Problem](https://github.com/magento/magento2/issues/39089) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39399)_

#### Verlust des Uploads der benutzerdefinierten Optionsdatei für das Produkt beim Auschecken mit der Kreditkartenzahlungsmethode von Adobe

_AC-14306 - [GitHub-Problem](https://github.com/magento/magento2/issues/39647)_

#### Auftragsstatus bei Verarbeitung hängen

Vor der Fehlerbehebung wurde bei der Bestellung eines Produktpakets mit aktivierter Option „Gemeinsam versenden“ der Bestellstatus nach der Rechnung und dem Versand nicht automatisch auf „Abgeschlossen“ geändert. Nach der Fehlerbehebung wechselt der Bestellstatus nun automatisch auf „Abgeschlossen“, nachdem die Bestellung fakturiert und versendet wurde.

_ACP2E-3947 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Vorkonfigurierter Magento-Code - Problem bei der Einrichtung der E-Mail-Vorlage

Vor der Fehlerbehebung waren bei der Verwendung des asynchronen E-Mail-Versands die Versand-E-Mails nicht mit der Bestellung im Store konsistent. Nach der Fehlerbehebung wird nun die richtige E-Mail-Bestellung für die Ladenlieferung zugestellt.

_ACP2E-3998 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### Andere Entwickler-Tools

#### [Problem] Falscher Typhinweis für das geschützte Mitglied $_urlHelper

Das System behebt jetzt den falschen Typhinweis mit dem richtigen, der auch im -Konstruktor verwendet wird

_AC-10716 - [GitHub-Problem](https://github.com/magento/magento2/issues/32503) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32496)_

### Leistung

#### [Problem] Aktualisieren Sie store.php

Diese PR verbessert die Leistung, indem die aktuelle Speicherauflösung übersprungen wird.

_AC-14791 - [GitHub-Problem](https://github.com/magento/magento2/issues/39949) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38717)_

### Preisgestaltung

#### Der Preis ist immer 0 für gebündelte Produktelemente ohne dynamischen Preis in der Auftrags-REST-API

_AC-11925 - [GitHub-Problem](https://github.com/magento/magento2/issues/38687) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7da46f52)_

### Produkt

#### Prozentualer Rabatt auf Stufenpreis und Katalogpreisregel, berechnet auf Basis des ursprünglichen Preises ohne ausgewählte Optionen.

_AC-12004 - [GitHub-Problem](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 MinZulässige fehlende Produktbestellmenge

Das System funktioniert einwandfrei, und die Seitenquelle zeigt die Mindestmenge des Produkts korrekt an

_AC-12909 - [GitHub-Problem](https://github.com/magento/magento2/issues/39142) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39480)_

#### Problem mit dem Raster Anpassbare Optionen auf der Produktseite im Admin-Bedienfeld

Das System funktioniert wie erwartet, wenn wir eine anpassbare Option mit Typ-Dropdown erstellen

_AC-14003 - [GitHub-Problem](https://github.com/magento/magento2/issues/39640) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39694)_

#### Alle Elemente aus anderen Kunden-Vergleichslisten werden dem Kunden nach der Anmeldung über den Administrator zugewiesen

Wenn ein Administrator bzw. eine Administratorin im Backend die Funktion „Als Kunde anmelden“ verwendet hat, wurden Produkte aus der Vergleichsliste eines zuvor angemeldeten Kunden bzw. einer zuvor angemeldeten Kundin fälschlicherweise dem aktuell stellvertretenden Kunden bzw. der Kundin zugewiesen.  Nach der Fehlerbehebung wird die Vergleichsliste für den richtigen angemeldeten Kunden korrekt geladen.

_ACP2E-3818 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### Die Aktualisierung von product_url_key über die REST-API generiert keine 301-URL-Umschreibung

Wenn Sie den URL-Schlüssel des Produkts über die REST-API aktualisieren und die Einstellung „Ständige Umleitung für URLs erstellen, wenn der URL-Schlüssel geändert wird“ auf „Ja“ gesetzt ist, wird bei den Umschreibungen der Produkt-URL eine Umleitung von der alten URL zur neuen erstellt.

_ACP2E-3900 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### Sicherheit

#### Gebündelte/zusammengeführte JS ist nicht Teil von SRI-Hashes

Vor der Fehlerbehebung wurden generierte Bundles oder zusammengeführte Dateien nicht zur SRI-Hash-Liste hinzugefügt. Jetzt werden die Dateien ordnungsgemäß zu den SRI-Hashes hinzugefügt.

_ACP2E-3854 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

### Lieferung

#### [QUANS] - Prüft das Magento_Fedex-Kernmodul auf ein gültiges-aktives Token, bevor eine Anfrage zum Abrufen eines neuen gesendet wird?

Adobe Commerce stellt nicht mehr viele Anfragen an den FedEx-API-Service für das Zugriffstoken. Zuvor führte Adobe Commerce immer neue Anfragen an die FedEx-API durch, die ein Problem mit der Ratenbegrenzung verursachten, obwohl das Zugriffstoken weiterhin gültig ist.

_ACP2E-3930 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4ca73607)_

### Staging und Vorschau

#### Geplante Produktaktualisierungen mit aktivierten Kategorieberechtigungen können nicht in der Vorschau angezeigt werden

Vor der Fehlerbehebung wurde ein zukünftiges Produkt, das aktiviert werden soll, nicht im Vorschaumodus angezeigt. Jetzt wird sie angezeigt, auch wenn der aktuelle Status deaktiviert ist.

_ACP2E-3786 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Fehlende Validierung für das Feld „Rabattbetrag für Katalogpreisregel“

Zuvor wurde das Feld „DISCOUNT_AMOUNT“ im Update des Staging-Zeitplans nicht korrekt mit den aktuellen Validierungsregeln validiert. Nach Anwendung der Korrektur wird das Feld „Rabatt_Betrag“ jedoch entsprechend validiert.

_ACP2E-3867 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/462ede94)_

### Steuer

#### Falsche Bestellsumme, die Runde wird nicht auf die Preisberechnung angewendet.

Das System wird nun bei der Berechnung des Betrags für den Preis-Nachlass-Rabatt, den Rabatt-Betrag und die Steuern korrekt verarbeitet.
Die tatsächliche Summe der Bestellung

_AC-11389 - [GitHub-Problem](https://github.com/magento/magento2/issues/38455) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39687)_

### Test-Framework

#### [Problem] lib/internal/Magento/framework/app/test/unit/_files/app/etc/en ignorieren…

Das System ignoriert jetzt die Datei „env.php“, die beim Ausführen von Modultests generiert wird, um sicherzustellen, dass der Git-Status nach dem Ausführen von Tests sauber bleibt. Zuvor wurden durch Ausführen von Modultests eine neue Datei „env.php“ generiert, wodurch der Git-Status anzeigt, dass eine neue Datei gefunden wurde, wodurch sie schmutzig erscheint.

_AC-13293 - [GitHub-Problem](https://github.com/magento/magento2/issues/39304) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37631)_

#### [Problem] Beheben eines Integrationstestproblems mit dem Interceptor

Das System identifiziert und verarbeitet jetzt im Integrationstest korrekt \Magento\TestFramework\App\Config\Interceptor , sodass der Test auch dann auf die erforderlichen Daten zugreifen kann, wenn ein Plug-in für die Klasse vorhanden ist. Zuvor konnte das System nicht berücksichtigen, dass \Magento\TestFramework\App\Config möglicherweise ein \Magento\TestFramework\App\Config\Interceptor ist, was zu einem Fehler beim Versuch führte, auf die $data -Eigenschaft zuzugreifen.

_AC-13305 - [GitHub-Problem](https://github.com/magento/magento2/issues/39324) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/37187)_

#### [Problem] MFTF: Senden einer E-Mail an ein Freundschaftsformular mit aktiviertem CAPTCHA

Der Testfall behandelt die Funktionalität des Formulars „E-Mail an Freund“, wenn CAPTCHA aktiviert ist, um sicherzustellen, dass der Formularübermittlungsprozess mit falschen und richtigen CAPTCHA-Werten korrekt funktioniert.

_AC-13492 - [GitHub-Problem](https://github.com/magento/magento2/issues/39462) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] Die Verwendung von TestCase::getTestResultObject ist seit phpunit v10 ungültig.

_AC-13502 - [GitHub-Problem](https://github.com/magento/magento2/issues/39463)_

#### Umgebungsspezifische Unit-Test-Fehler in AC 2.4.7-p3

Dieses Problem behebt Fehler bei Modultests, die nicht in allen Versionen und Umgebungen reproduziert werden. Zuvor schlugen einige Modultests aufgrund verschiedener Bibliotheksversionen oder fehlender Funktionen, die in einer späteren Version hinzugefügt wurden, fehl.

_ACP2E-3712 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9ad7d277)_

### UI-Framework

#### WYSIWYG ist in dynamischen Zeilen leer

_AC-12336 - [GitHub-Problem](https://github.com/magento/magento2/issues/38893) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problem] MIME-Typ-Tippfehler beheben

Das System verarbeitet den MIME-Typ und den Tippfehler für das gif-Bild korrekt und korrigiert ihn

_AC-8001 - [GitHub-Problem](https://github.com/magento/magento2/issues/36899) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36669)_

#### [Problem] Vermeiden des direkten Zugriffs auf die Rezensionsliste Ajax

Das System verarbeitet und vermeidet den direkten Zugriff auf die Rezensionsliste Ajax

_AC-9381 - [GitHub-Problem](https://github.com/magento/magento2/issues/37920) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/33876)_

### Aktualisierungen - Upgrade-Kompatibilitäts-Tool

#### Veraltete Funktionen: Erstellung der dynamischen Eigenschaft &quot;Magento\Framework\Acl::$_roleRegistry“

_AC-12343 - [GitHub-Problem](https://github.com/magento/magento2/issues/37469)_
