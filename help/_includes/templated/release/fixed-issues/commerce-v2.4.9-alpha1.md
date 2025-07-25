---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Behobene Probleme in Adobe Commerce (v2.4.9-alpha1)

## Behobene Probleme in v2.4.9-alpha1

Es wurden 84 Probleme im Adobe Commerce 2.4.9-alpha1-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

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

### Konto

#### [Cloud] Der Löschvorgang ist aufgrund eines Fehlers im aktuellen Bereich bei der Erstellung des Kundenkontos verboten

Nach der Fehlerbehebung wird beim Speichern eines Kunden mit einer ungültigen Adresse eine Meldung zurückgegeben, die den Grund für die Invalidität anstelle von irrelevantem „Löschvorgang ist für den aktuellen Bereich verboten“ beschreibt.

_ACP2E-3791 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6ea61121)_

### Admin-Benutzeroberfläche

#### [Problem] Verbessern des Benutzererlebnisses mit der Rollenstruktur

Diese Pull-Anfrage fügt Schaltflächen hinzu, um alle zu reduzieren, alle zu erweitern und Verzweigungen mit ausgewählten Elementen zu erweitern. Diese Funktion ist ähnlich der in der Kategoriestruktur bereitgestellten Funktion (Katalog -> Inventar -> Kategorien).

_AC-14020 - [GitHub-Problem](https://github.com/magento/magento2/issues/39654) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException: Der „Sender“-Header muss eine Instanz von &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; sein (nicht &quot;Symfony\Component\Mime\Header\MailboxListHeader„)

_AC-14520 - [GitHub-Problem](https://github.com/magento/magento2/issues/39823) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1e14bd72)_

#### Funktion bereitstellen, um Steuersätze mithilfe des Rasters für Massenlöschungen zu verwenden

Admin-Benutzer können jetzt mehrere Steuersätze gleichzeitig aus dem Admin-Steuersatzraster löschen.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub-Problem](https://github.com/magento/magento2/issues/33399) - [GitHub-Code-](https://github.com/magento/magento2/pull/33484) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Die Warenkorb-Preisregel mit der Bedingung-SKU berücksichtigt nicht die „führenden Nullen“ in der SKU (SKU: 01234 ist dasselbe wie 1234).

Das System verarbeitet jetzt die Warenkorb-Preisregel korrekt mit der Bedingung SKU und berücksichtigt die „führenden Nullen“ in der SKU

_AC-9428 - [GitHub-Problem](https://github.com/magento/magento2/issues/37919) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39525)_

#### Problem mit dem Verhalten des Werts der Standardattributoption für Mehrfachauswahl

Vor der Korrektur wurden die Standardwerte für mehrere Optionsattribute nicht ordnungsgemäß gespeichert. Nach der Korrektur werden die Werte ordnungsgemäß in der Datenbank gespeichert.

_ACP2E-3523 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Untertitel des Backend-Administratormenüs werden nicht angezeigt

Alle Titel der Hauptmenügruppen werden nun korrekt angezeigt. Zuvor wurde der Titel der Gruppe nicht angezeigt, wenn die zweite oder dritte Spalte des Hauptmenüs nur eine Gruppe von Links enthielt.

_ACP2E-3540_

#### Problem beim Verschieben der Produktmenge vom Administrator zurück in den Warenkorb

Wenn Sie eine Bestellung über den Administrator erstellen, werden Produkte im Warenkorb auf der Seitenleiste nicht ausgeblendet, wenn sie zur Bestellung hinzugefügt werden.

_ACP2E-3563 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Admin-Benutzeroberfläche, B2B

#### B2B-Anmeldung als Kunden-Header hat weiterhin das Magento-Branding

Zuvor wurde in der Kopfzeile der Storefront „You are now connected as &lt;customer name> on &lt;store name>&quot; (Sie sind jetzt als &lt;customer name> verbunden) mit Magento-Branding angezeigt. Was jetzt behoben ist und die Kopfzeile mit ADOBE-Branding angezeigt wird.

_AC-14361 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/fadcfa8b)_

### Admin-Benutzeroberfläche, Inhalt

#### Ausnahme „Ausgabedarstellung kann für Medien-Asset-Pfade nicht erstellt werden“ beim Einfügen des Bildes

Nach dem Entfernen der Werte für Maximale Breite und Maximale Höhe der Konfiguration der Bildoptimierung für die Mediensammlung tritt der Fehler während des Bildoptimierungsprozesses nicht mehr auf.

_ACP2E-3781 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

### Admin-Benutzeroberfläche, Sicherheit

#### Unzureichende Kennwortverwaltung

Der Administrator kann nicht mit demselben Kennwort gespeichert werden. Zuvor wurde sie erfolgreich ohne ordnungsgemäße Validierung gespeichert.

_ACP2E-3657 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

### Admin-Benutzeroberfläche, Sicherheit, Staging und Vorschau

#### Aktionsprotokolle für das Staging von Inhalten

In den Aktionsprotokollen werden nun die Staging-Aktualisierungsaktivitäten angezeigt. Zuvor wurde das Staging-Aktualisierungsprotokoll nicht in den Admin-Aktionsprotokollen aufgezeichnet.

_ACP2E-3679_

### B2B

#### Bestellung aufgeben funktioniert nicht mit der Zahlungsmethode Zur Kasse mit Kreditkarte per verhandelbarem Angebot mit PayFlow Pro wechseln

_AC-11973_

#### Erfolgsmeldung nach Umbenennen des Angebots verschwindet gelegentlich

_AC-13447_

#### Die Gesamtberechnung beinhaltet nicht den Steuerbetrag

Die Bestellung enthält korrekte Summen, wenn die Platzierungen aus einer bestehenden Bestellung mit aktiviertem „Grenzüberschreitender Handel“.

_ACP2E-3727_

#### Die Zuweisung von Kategorien in einem freigegebenen B2B-Katalog über die REST-API wird langsam aufgehoben

Jetzt wurde die Leistung beim Aufheben der Zuweisung von Kategorien in B2B erheblich verbessert. Zuvor dauerte es sehr lange, die Zuweisung von Kategorien im freigegebenen B2B-Katalog aufzuheben.

_ACP2E-3796_

#### Leistungsproblem mit neuem Setup-Patch in B2B

Es wurde das Leistungsproblem behoben, bei dem das Upgrade des Moduls Magento_Company nach dem Update auf B2B 1.5.2 bei der Verarbeitung einer großen Anzahl von Datensätzen (~100.000+) in der Tabelle company_structure übermäßig lange dauerte.

_ACP2E-3850_

### Warenkorb und Checkout

#### Magento 2.4.7 Update (Mini) Warenkorb Keine Dezimalmenge zulässig

Jetzt verarbeitet Magento korrekt, wenn wir die Menge mit Dezimalzahlen aus dem Mini-Warenkorb aktualisieren, wenn das Gebietsschema NL (Niederländisch) war

_AC-13238 - [GitHub-Problem](https://github.com/magento/magento2/issues/39236) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39669)_

#### [Problem] Aktualisieren von subtotal.phtml

Das System aktualisiert die Datei „subtotal.phtml“ mit dem richtigen Abstand

_AC-13907 - [GitHub-Problem](https://github.com/magento/magento2/issues/39619) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39612)_

#### Bestellung kann nicht beim Gast aufgegeben werden

_AC-14241 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/27217d0e)_

#### Abgelaufene persistente Anführungszeichen werden nicht durch einen Cron-Vorgang bereinigt sales_clean_quotes

Die abgelaufenen persistenten Anführungszeichen werden jetzt gelöscht, wenn der Cron-Auftrag „persistent_clear_expiration“ ausgeführt wird. Zuvor wurden die abgelaufenen persistenten Anführungszeichen von keinem anderen Cron-Auftrag gelöscht.

_ACP2E-3493 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/11be3dff)_

#### Fehler „Irgendetwas ist schiefgelaufen“ beim Checkout für ein inaktives Unternehmen

Vor der Behebung wurde die Abmeldeaktion auf der Warenkorbseite nicht ordnungsgemäß abgeschlossen, wenn der angemeldete Benutzer „Firma“ nicht mehr aktiviert war. Wenn die Firma nicht mehr verfügbar ist, wird die Abmeldung ordnungsgemäß durchgeführt.

_ACP2E-3541 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Die Adressenauswahl wird beim Auschecken mit mehreren Adressen nicht gespeichert

Vor der Fehlerbehebung beim Abbrechen der Option für den Mehrfachversand war die Adresse beim Zurücksetzen auf den Mehrfachversand nicht vorausgewählt. Jetzt wird die Standardadresse durch eine der Optionen ersetzt, die im Multi-Shipping-Bildschirm ausgewählt wurden.

_ACP2E-3646 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6ea61121)_

### Warenkorb und Checkout, SEO

#### Falsche Geschenkkartencode-URL in der E-Mail beim Kauf auf der sekundären Website

Zuvor leiteten das Multi-Store-Setup und die Geschenkkarte für nicht standardmäßige Geschäfte den Geschenkkartenantrag immer auf die Standard-Website um. Nachdem diese Fehlerbehebung angewendet wurde, leitet die E-Mail den Link für Geschenkkartenforderungen an den richtigen Umfang oder die richtige Website weiter.

_ACP2E-3699_

### Warenkorb und Checkout, Versand

#### [Mainline] Die Warenkorb-Preisregel respektiert nicht Multishipping

Vor der Implementierung dieser Korrektur galt die Warenkorb-Preisregel für Produkte mit mehreren Versandarten nicht korrekt, wenn Unterauswahlbedingungen angewendet wurden und der kostenlose Versand aktiviert war. Da die Korrektur jedoch angewendet wurde, funktioniert die Warenkorb-Preisregel für Warenkörbe mit mehreren Versand jetzt wie beabsichtigt.

_ACP2E-3666 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog

#### Cache-FPC für dieselbe Seite mit derselben Abfrage duplizieren

Das System identifiziert und verwendet nun denselben Vollseiten-Cache (FPC) für Seiten mit denselben Abfrageparametern, unabhängig von ihrer Reihenfolge oder nachfolgenden Zeichen. Dadurch wird eine unnötige Erhöhung der Größe des Seiten-Cache-Ordners verhindert. Zuvor erstellte das System eine andere FPC-Kennung für dieselbe Seite, wenn die Reihenfolge der Abfrageparameter unterschiedlich war oder nachfolgende Zeichen vorhanden waren, was zu einer Erhöhung der Größe des Seiten-Cache-Ordners führte.

_AC-10722 - [GitHub-Problem](https://github.com/magento/magento2/issues/38269) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38270)_

#### Fehlende Indizierung der erforderlichen Spalten in der Tabelle CATALOG_PRODUCT_ENTITY_INT

Die fehlende Indizierung der erforderlichen Spalten in der Tabelle catalog_product_entity_int wurde hinzugefügt.

_AC-10844 - [GitHub-Problem](https://github.com/magento/magento2/issues/38315) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38316)_

#### Produktseite gibt aufgrund von URL-Neuschreibungen einen Fehler aus

Jetzt wird die Produktseite erfolgreich geladen, wenn URL-Neuschreibungen durchgeführt werden

_AC-2950 - [GitHub-Problem](https://github.com/magento/magento2/issues/35371) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39670)_

#### [Cloud] Fehler beim Hinzufügen von Produkten zur Kategorie

Die Beschriftung für Paginierung und Datensatzanzahl funktioniert jetzt beim Hinzufügen von Produkten zu einer Kategorie über das Popup-Raster ordnungsgemäß. Zuvor führte das Laden von nur einer Seite mit Elementen, die der Seitengröße entsprechen, zu Problemen mit dem Dropdown-Menü zur Elementauswahl.

_ACP2E-3526_

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

#### Die Gültigkeit der Geschenkkarte schlägt bei der Bearbeitung aufgrund eines Tausendertrennzeichens fehl

Fehlerkorrektur - Beim Sparen von Produktarten für Geschenkkarten tritt jetzt kein Fehler mehr auf, wenn der Betrag der Geschenkkarte 1.000 und mehr beträgt.

_ACP2E-3704_

### Katalog, GraphQL, Suche

#### GraphQL-Produkte haben in den Kategorieaggregationen deaktivierte Kategorien zurückgegeben

Nach der Fehlerbehebung werden deaktivierte Kategorien für die GraphQL-Anfrage „Produkte“ nicht zurückgegeben.

_ACP2E-2885 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog, Produkt

#### [Random Bug] Fotorama-Bibliothek wird nicht geladen

Das System stellt nun sicher, dass die Fotorama-Bibliothek korrekt geladen wird, sodass alle angehängten Bilder wie erwartet in der Bildergalerie angezeigt werden. Zuvor war nur das erste Bild sichtbar, da ein Problem mit der Fotorama-Bibliothek nicht korrekt geladen wurde.

_AC-12124 - [GitHub-Code-](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/27217d0e)_

### Inhalt

#### Die Platzierung von csp_whitelist.xml im Design funktioniert nicht und verursacht zeitweise Probleme

Zwischenspeicherung der CSP-Whitelist pro Website-Bereich implementiert.

_AC-13069 - [GitHub-Problem](https://github.com/magento/magento2/issues/38933) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39672)_

#### Fehler: Skriptfehler für &quot;Magento_Catalog/js/validate-product“ für Admin Content Page Builder mit geladenen Produkten

Diese PR behebt den Skriptfehler für catalogAddToCart beim Bearbeiten des PageBuilders mit der Bedingung „products“

_AC-13891 - [GitHub-Problem](https://github.com/magento/magento2/issues/39604) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39677)_

#### Blockauswahl in Widgets mit derselben Kennung

Das System verarbeitet jetzt die Auswahl von Blöcken beim Erstellen von Widgets korrekt, wenn dieselben Kennungsblöcke vorhanden sind

_AC-14132 - [GitHub-Problem](https://github.com/magento/magento2/issues/39692) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39722)_

#### Tabellenpräfix wird nicht berücksichtigt

_AC-14556 - [GitHub-Problem](https://github.com/magento/magento2/issues/39847) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Bild mit relativ geringer Breite kann nicht hochgeladen werden

Das System versäumt es nicht mehr, die Größe des Bildes mit einer relativ kleinen Breite auf seine Höhe zu ändern.

_ACP2E-3558 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Falscher Konfigurationspfad für Konfiguration des Remote-Speicherpfads

Nach der Fehlerbehebung wirkt sich das Festlegen der Stilkonfiguration für Remote-Speicherpfade auf die tatsächliche Konfiguration des AWS S3-Pfads aus.

_ACP2E-3734 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

### Framework

#### Kompilieren des Codes eines deaktivierten Moduls.

Diese Pull-Anfrage löscht deaktivierte Module vor der Code-Kompilierung.

_AC-10933 - [GitHub-Problem](https://github.com/magento/magento2/issues/38241) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39723)_

#### Magento_Theme title.phtml Vorlage ungültig für PHP 8.2

Diese Pull-Anfrage behebt ein Problem, wenn eine CMS-Seite, die mit der Null-Überschrift erstellt wurde, wie in PHP 8.x, die null an trim() übergibt, eine Ausnahme auslöst: Veraltete Funktionalität: trim(): Übergeben von null an den Parameter #1 ($string) vom Typ String

_AC-12856 - [GitHub-Problem](https://github.com/magento/magento2/issues/39092) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39398)_

#### Bei der Verwendung des Dateispeichers für den Sperranbieter erhalten wir ein ständig wachsendes Verzeichnis von Dateien, ohne dass eine Bereinigung stattfindet

Diese Pull-Anfrage führt einen neuen Cron-Auftrag ein, der einmal pro Tag ausgeführt wird und nach Sperrdateien sucht, die in den letzten 24 Stunden nicht geändert wurden und daher sicher entfernt werden können. Dadurch wird der Inhalt des Sperrdateiverzeichnisses unter Kontrolle gehalten.
Dieser Cron-Vorgang wird nur ausgeführt, wenn der Sperranbieter für die Verwendung von Dateien konfiguriert ist, nicht, wenn einer der anderen verwendet wird (Datenbank - der Standard-, ZooKeeper- oder Cache)

_AC-13367 - [GitHub-Problem](https://github.com/magento/magento2/issues/39369) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39372)_

#### [Problem] Bereinigung: Verwenden Sie keinen ungültigen Rückgabewert aus Methodenaufrufen.

Diese PR führt kleinere Bereinigungen durch. Manchmal haben wir Methoden aufgerufen, die nichts zurückgegeben haben (void), und dann diesen Ergebniswert verwendet. Was wirklich nicht benötigt wird.

_AC-13664 - [GitHub-Problem](https://github.com/magento/magento2/issues/39524) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39516)_

#### [Problem] [PHPDOC] Schlechtes phpdoc für Magento\Framework\Message\ManagerInterface beheben

Dieser PR behebt das fehlerhafte phpdoc für \Magento\Framework\Message\ManagerInterface und entfernt alle doppelten phpdoc in \Magento\Framework\Message\Manager (verwenden Sie inheritdoc-Syntax).

_AC-14312 - [GitHub-Problem](https://github.com/magento/magento2/issues/39593) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39153)_

#### Minimale Betastabilität wurde von composer.json entfernt

Minimale Betastabilität wurde von composer.json entfernt

_AC-14450 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1cbbf187)_

#### allow_parallel_generation sollte über die Umgebungsvariable festgelegt werden

Nach der Fehlerbehebung kann die Umgebungsvariable &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION“ verwendet werden, um die Konfiguration „allow_parallel_generation“ festzulegen.

_ACP2E-3673 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] Das Ändern des Tabellenspaltentyps mithilfe der Datei „db_schema.xml“ in Magento 2 führt zu Fehlern

Das Ändern des Spalten-Datentyps funktioniert nicht ordnungsgemäß. Zuvor wird ein Fehler ausgegeben: Das Attribut „identity“ ist nicht zulässig.

_ACP2E-3709 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Unterstützung neuer Währungen (XCG) in Adobe

Caribbean Gulder (XCG) wird der Liste der Währungen hinzugefügt.

_ACP2E-3790 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### Die GraphQL-Antwort für die Bestellplatzierung enthält nicht die Ausnahmemeldung

Die vorherige Änderung, die Fehler in einem anderen Format zurückgab, wurde rückgängig gemacht. Jetzt werden potenzielle Fehler konsistent zurückgegeben, sodass das GraphQL-Schema nicht beschädigt wird. Dies sollte als bekannter BIC hinzugefügt werden, der von PM in ACP2E-3399 genehmigt wurde

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

### Import/Export

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

### Inventar/MSI

#### Store-Abholung berücksichtigt nicht den maximalen Suchradius, wenn Adresse an der Kasse geändert wird

Jetzt wird der vorausgewählte Store in „Pick-in-Store“ aktualisiert, wenn sich die Versandadresse ändert. Zuvor hat sich ein zuvor ausgewählter Store nicht geändert, auch wenn sich die neue Versandadresse nicht im Radius des ausgewählten Stores befindet

_ACP2E-3728 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/07620383)_

### Reihenfolge

#### Für das nicht auf NULL festlegbare Feld \&amp;quote;AppliedCoupon.code\&amp;quote; unerwartetes Problem kann nicht null zurückgegeben werden

_AC-14484 - [GitHub-Problem](https://github.com/magento/magento2/issues/39841) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/97b2ea42)_

#### [Cloud] Einige Inline-JavaScript funktionieren nach dem Upgrade auf Magento 2.4.6-p7 nicht

Durch Klicken auf die Schaltfläche „Löschen“ in „Zur Bestellung hinzufügen nach SKU“ in „Admin“ wird die SKU jetzt entfernt. Zuvor wurde durch Klicken auf die Schaltfläche „Löschen“ in „Zur Bestellung hinzufügen nach SKU“ die SKU nicht entfernt.

_ACP2E-3515_

#### Serialisierte Geschenkgutscheindaten sind in der Tabelle sales_order inkonsistent

Die Daten der Geschenkgutscheine in der Tabelle sales_order werden jetzt korrekt serialisiert. Zuvor wurde sie jedes Mal serialisiert, wenn die Bestellung aktualisiert wurde.

_ACP2E-3662_

### Bestellung, Preise

#### Der Administrator zeigt beim Erstellen der Rücksendung ein falsches Währungssymbol an.

In einem Multi-Website-Setup mit verschiedenen Währungen (EUR/USD/GBP) zeigt die Seite „Produktauswahl zurückgeben“ in „Admin“ jetzt das richtige Währungssymbol an. Zuvor wurde das standardmäßige Währungssymbol angezeigt.

_ACP2E-3658 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

### Andere Entwickler-Tools

#### Lighthouse-Barrierefreiheitsfehler

Das System hat jetzt den Barrierefreiheitswert 100 erreicht

_AC-12783 - [GitHub-Problem](https://github.com/magento/magento2/issues/39054) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39164)_

#### Deaktivieren Sie die Konfiguration der CAPTCHA-Storefront, um weiterhin CAPTCHA-JS-Dateien zu laden

Das System lädt jetzt keine CAPTCHA-JS-Dateien mehr, wenn wir CAPTCHA für die Storefront deaktiviert haben

_AC-14267 - [GitHub-Problem](https://github.com/magento/magento2/issues/32987) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39154)_

### Verpackung

#### [Packaging] Korrigieren der Abhängigkeit von magento/magento-coding-standard+ page-builder

_ACPLTSRV-6383_

### Zahlungen

#### [Problem] Offline-Rechnungserfassung beheben (404)

Der 404-Seitenfehler bei der Erfassung von Rechnungen für Offline-Zahlungsmethoden von Magento Admin wurde behoben

_AC-13336 - [GitHub-Problem](https://github.com/magento/magento2/issues/39298) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39297)_

### Leistung

#### Kategorieberechtigungsmodul verhindert möglicherweise das Zwischenspeichern

Controller von Drittanbietern werden jetzt korrekt mit Kundensegmenten zwischengespeichert

_ACP2E-3721_

### Produkt

#### Produktsammlung - addMediaGalleryData ruft getSize auf, wenn die Sammlung geladen werden kann oder wird (kann die Anzahl verwenden, um eine zusätzliche DB-Abfrage zu vermeiden)

Diese PR reduziert den zusätzlichen Abfrageaufruf mit count(), wenn die Produktsammlung bereits geladen ist, wenn Produkt-GraphQL mit dem darin enthaltenen media_gallery-Feld aufgerufen wird.

_AC-13055 - [GitHub-Problem](https://github.com/magento/magento2/issues/39111) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39681)_

#### [2.4.8] Keine Callbacks für Cron-Auftragskatalog_product_alert gefunden

_AC-14494 - [GitHub-Problem](https://github.com/magento/magento2/issues/39800) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Langsame Abfragen werden ausgeführt, wenn ein Produkt-Widget über den PageBuilder eingebunden wird

Die Abfrage für die Erstellung von Produkt-Widgets, einschließlich Produkt-SKUs, ist optimiert.

_ACP2E-3449 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

#### Produktbilder werden nicht in der Größe angepasst, wenn sie als konfigurierbares Produkt hinzugefügt werden

Zuvor entsprachen Bilder, die über Konfigurationen im Admin-Bedienfeld hinzugefügt wurden, nicht der maximalen Upload-Größe, was zu Inkonsistenzen und Verwaltungsproblemen führen konnte. Jetzt wurde eine Korrektur implementiert, um sicherzustellen, dass die Größe der Bilder beim Hochladen automatisch geändert wird, um die maximale Größe einzuhalten, den Prozess zu optimieren und die Systemstandards einzuhalten.

_ACP2E-3504 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/df92debe)_

### Lieferung

#### Das Dokument sollte für die Implementierung in % aktualisiert werden, die im offiziellen Dokument nicht korrekt ist

Die Dev-Dokumentation zur Unterstützung der DHL-Rest-API wurde aktualisiert.

_AC-14507_

#### [DHL]-Handle Optionale Dimensionen in regulären Größeneinstellungen und Preisabweichungen zwischen REST- und XML-API-Integrationen

_AC-14601 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/1e3bde4c)_

#### Ausnahme bei Erstellung des UPS Versandtitels

Behobener Warnhinweis: Array-zu-String-Konvertierung während der Erstellung der UPS-Versandkennzeichnung

_ACP2E-3676 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Staging und Vorschau

#### Bei der Vorschau eines geplanten Updates wird die erste Store-Ansicht in alphabetischer Reihenfolge anstelle der Store-Ansicht geöffnet, die von Interesse ist

Vor der Fehlerbehebung wurde die Vorschau eines geplanten Updates in der ersten Store-Ansicht in alphabetischer Reihenfolge anstelle der zugewiesenen Store-Ansicht geöffnet.
Nach der Fehlerbehebung wird die Vorschau jetzt korrekt in der Store-Ansicht geöffnet, die dem CMS-Block-Staging-Update zugewiesen ist.

_ACP2E-3671 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version Cron-Verhaltensproblem - special_price ignoriert

Nach der Korrektur werden die Angebotsumfänge nach der Änderung des Sonderpreises durch geplante Produktaktualisierung neu berechnet.

_ACP2E-3674_

### Steuer

#### Der Steuerbetrag wird nicht aktualisiert, wenn der Geschenkverpackungsinhalt aus dem Warenkorb entfernt wird

_AC-14637_
