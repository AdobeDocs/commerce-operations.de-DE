---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '9924'
ht-degree: 0%
---
# Behobene Probleme in Magento Open Source (v2.4.10-alpha1)

## Behobene Probleme in v2.4.10-alpha1

Es wurden 152 Probleme im Magento Open Source 2.4.10-alpha1-Kerncode behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

#### [Problem] TypeError in Creditmemo\Validation\QuantityValidator verursacht durch min() mit String quantity

Um die Pipelines für die Finanzprotokollierung zu stabilisieren und API-Anforderungsfehler während der automatischen Massenauftragsrückerstattungen zu verhindern, wurden der internen Factory für Verkaufsgutschriften und den Validierungsschichten Schutzmaßnahmen für die Umwandlung von Datentypen hinzugefügt.

_AC-16056 - [GitHub-Problem](https://github.com/magento/magento2/issues/40302) - [GitHub-Code-](https://github.com/magento/magento2/pull/40429) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40303)_

#### REST API-Attributaktualisierung schlägt ohne attribute_id fehl

Es wurde ein Problem behoben, bei dem das Aktualisieren eines vorhandenen Produktattributs über die REST-API fehlschlug, wenn keine attribute_id angegeben wurde. Die API identifiziert das Attribut jetzt korrekt mithilfe des attribute_code aus der URL und aktualisiert es erfolgreich.

_AC-16424 - [GitHub-Problem](https://github.com/magento/magento2/issues/40458) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c10554e1)_

#### Visuelle Muster werden beim Aktualisieren der Option über die REST-API gelöscht

Um die Integrität der Katalogdaten zu schützen und automatisierte Integrationen zu optimieren, wurde ein Fehler in der EAV-Farbfeld-Verwaltungsschicht behoben, durch den vorhandene visuelle oder textuelle Farbfeldwerte bei Aktualisierungen der Standardoption versehentlich gelöscht wurden.

_AC-9199 - [GitHub-Problem](https://github.com/magento/magento2/issues/37794) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40872)_

#### Die Preis-API der Massenstufe schlägt beim gesamten Batch fehl, wenn eine SKU fehlt

Zuvor schlug die API zur Aktualisierung der Massenstufen-Preise (POST /V1/products/tier-prices) die gesamte Anfrage fehl, wenn keine SKU in der Payload vorhanden war, sodass gültige SKUs ohne Aktualisierungen blieben. Jetzt werden gültige SKUs erfolgreich verarbeitet, während fehlende SKUs als Fehler pro Element gemeldet werden, sodass ein einzelner fehlerhafter Eintrag nicht mehr den gesamten Batch abbricht.

_ACP2E-4998 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/51f6d191)_

#### Die Attributaktualisierung schlägt fehl, wenn der Kennzeichnungswert mit der vorhandenen Optionswert-ID übereinstimmt

Es wurde ein Problem behoben, bei dem eine neue Dropdown-/Mehrfachauswahl-Produktattributoption nicht über die REST-API erstellt werden konnte, wenn ihre Bezeichnung mit der ID einer vorhandenen Option übereinstimmte. Zuvor gab die API den Fehler „ist bereits vorhanden“ zurück (und gab möglicherweise die falsche Optionskennung zurück), obwohl dieselbe Option erfolgreich über die Admin-Benutzeroberfläche erstellt werden konnte.

_ACP2E-5107 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4d0357d7)_

### APIs, Import und Export

#### Die REST-API ermöglicht negative Produktpreise, während die Admin-Benutzeroberfläche sie blockiert.

Der Produktimport über den REST-API-Endpunkt lehnt jetzt negative Werte für Preisattributen (Preis-, Spezial-Preis-, Kosten- und zugehörige MSRP-Felder) ab, was dem Verhalten des Admin-Benutzeroberflächen-Imports entspricht. Zuvor akzeptierte die API negative Preise stillschweigend und hielt sie aufrecht.

_ACP2E-4941 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/08b91f1a)_

### APIs, Reihenfolge

#### Funktion „Order Rate Limit“ inkompatibel mit dem Valley-Cache-Backend

Zuvor wurde diese Begrenzung der Fixrate im Hintergrund umgangen und jede Anfrage wurde unabhängig vom konfigurierten Limit durchgelassen. Nach der Fehlerbehebung werden Anfragen, die das konfigurierte Limit überschreiten, korrekt mit HTTP 429 zurückgewiesen.

_ACP2E-4899 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Konto

#### [Problem] Behebung: Falsche Kennwortbeschriftung im Anmeldeformular

Es wurde ein Problem behoben, bei dem das Kennwortfeld auf der Anmeldeseite für Kunden eine falsche Beschriftungsverknüpfung aufwies. Die Kennwortbeschriftung ist jetzt korrekt auf das Kennwortfeld ausgerichtet, sodass es von automatisierten Test-Tools ordnungsgemäß identifiziert werden kann.

_AC-16193 - [GitHub-Problem](https://github.com/magento/magento2/issues/40353) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64eb754d)_

#### [Problem] Validieren des Frontend-Eingabetyps für Datei-Uploads

Uploads von Kundenadressdateien überprüfen jetzt, ob der Eingabetyp des Zielattributs „Datei“ oder „Bild“ ist, bevor die Verarbeitung erfolgt, sodass Text und andere Nicht-Dateiattribute nicht als Upload-Ziele missbraucht werden können. Ungültige Upload-Versuche geben einen eindeutigen Validierungsfehler zurück, anstatt unvorhersehbar zu fehlschlagen oder unzulässige Dateitypen zu akzeptieren.

_AC-17076 - [GitHub-Problem](https://github.com/magento/magento2/issues/40795) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40583)_

#### Ein auf Website A generiertes Kunden-Token kann auf Website B in der Konfiguration für die gesamte Website verwendet werden

Um eine strikte Isolierung der Kundendaten auf Instanzen mit mehreren Websites zu erzwingen, wurde eine Sicherheitslücke auf der GraphQL-Authentifizierungsebene behoben, auf der Token fälschlicherweise über verschiedene Grenzen hinweg validiert wurden.

_AC-17299 - [GitHub-Problem](https://github.com/magento/magento2/issues/40847) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40858)_

#### [Problem] Behebung der PHP 8.5-Einstellung: Verwendung von null als Schlüsselparameter für array_key_exists()

Fehlerkorrektur - Die Kundenanmeldung während des Gast-Checkouts schlägt in PHP 8.5 aufgrund eines veralteten Aufrufs array_key_exists() mit einem Null-Schlüssel nicht mehr fehl. Die Kundenanmeldung funktioniert jetzt erfolgreich, ohne dass der Fehler „veraltet“ erzeugt wird.

_AC-17395 - [GitHub-Problem](https://github.com/magento/magento2/issues/40875) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problem] magento/magento2: Hinzufügen von i18-Übersetzungen zu den Mutationen requestPasswordResetEmail und resetPassword GraphQL

Um eine vollständig lokalisierte Headless-Storefront zu gewährleisten, wurden die API-Endpunkte für die Wiederherstellung von Kundenkonten um Übersetzungsfunktionen für die Internationalisierung (i18n) erweitert

_AC-9356 - [GitHub-Problem](https://github.com/magento/magento2/issues/29658) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/28950)_

### Admin-Benutzeroberfläche

#### Das Dashboard sollte bei Verwendung aggregierter Daten standardmäßig die letzten 7 Tage anzeigen

Es wurde ein Problem behoben, bei dem das Dashboard standardmäßig „Heute“ angezeigt wurde, wenn aggregierte Verkaufsdaten aktiviert waren. Im Dashboard werden nun bei Verwendung aggregierter Daten standardmäßig die letzten 7 Tage angezeigt.

_AC-13799 - [GitHub-Problem](https://github.com/magento/magento2/issues/28152) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Der FTP-Wert auf der Warenkorbseite und der Produktseite unterscheidet sich bei denselben Konfigurationen für ein einfaches Produkt

Es wurde ein Problem behoben, bei dem feste Produktsteuerwerte (FPT) auf Produkt- und Warenkorbseiten für dieselbe Steuerkonfiguration unterschiedlich angezeigt wurden. FPT-Werte werden nun konsistent auf den Produkt-, Katalog-, Mini-Warenkorb- und Warenkorbseiten angezeigt.

_AC-17007 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Implementierung der verzögerten Konfiguration

Leistungsoptimierung, die die Leistung beim Laden der Konfiguration verbessert, indem sie Systemkonfigurationsdaten im Umfang verzögert auflöst, während das vorhandene Konfigurationsverhalten beibehalten wird.

_ACP2E-4751 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/65f660bd)_

#### HugeRTE Editor blockiert Emojis - JavaScript-Validierung fehlgeschlagen

Es wurde ein Problem behoben, bei dem HugeRTE das Speichern von Inhalten mit utf8mb4-Emojis (z. B. 🔵⚪🔴) blockierte, wenn sie in Inhaltstyp-Modalen von PageBuilder (Text, Banner, Folie) bearbeitet wurden. Zuvor wurde die WYSIWYG-Validierungskonfiguration für diese modalen Formulare `allowUtf8mb4` auf `false` aufgelöst, was dazu führte, dass der Editor 4-Byte-UTF-8-Zeichen selbst bei Installationen verwirft, bei denen die Datenbank UTF8MB4 vollständig unterstützt.

_ACP2E-4822 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### Der Administrator wird abgemeldet, wenn im Admin-Bedienfeld Kunden mit großen Adressbüchern auf der Seite „Kundenbearbeitung“ angezeigt werden

Es wurde ein Problem behoben, bei dem der Administrator abgemeldet wird, wenn Kunden mit großen Adressbüchern auf der Seite „Kundenbearbeitung“ im Admin-Bedienfeld angezeigt werden

_ACP2E-4875 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

#### Bestellungen werden nicht im Verkaufsraster angezeigt

Es wurde ein Problem behoben, bei dem neue Aufträge in den Verkaufsrastern verzögert angezeigt wurden, wenn die asynchrone Rasterindizierung aktiviert war, da der Abstimmcursor zurückgesetzt wurde, sobald er die letzte Entität erreicht hatte. Neue Einträge werden jetzt beim nächsten Cron-Durchgang im Raster angezeigt.

_ACP2E-4893 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

### Admin-Benutzeroberfläche, Reihenfolge

#### Falscher Preis für gruppiertes Produkt in der Admin-Erstellungsreihenfolge angezeigt, wenn zwei gruppierte Produkte dasselbe einfache Produkt verwenden

Es wurde ein Problem behoben, bei dem der Preis eines gruppierten Produkts in der Admin-Erstellungsreihenfolge falsch berechnet wurde, wenn zwei gruppierte Produkte, die dasselbe einfache Produkt nutzen, beide konfiguriert wurden, ohne zum Warenkorb hinzugefügt zu werden.

_ACP2E-4965 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/08b91f1a)_

### Admin-Benutzeroberfläche, UI-Framework

#### Magento2 leitet zur Homepage um, anstatt Fehler mit falscher Menüdeklaration anzuzeigen

Um den Entwicklungs-Workflow für Erweiterungen zu optimieren und ein stabiles Laden des Backends sicherzustellen, wurde ein struktureller Routing-Fehler behoben, bei dem ungültige Admin-Menüdeklarationen stille Browser-Schleifenfehler auslösten, anstatt verwertbare Diagnosemeldungen anzuzeigen.

_AC-7543 - [GitHub-Problem](https://github.com/magento/magento2/issues/36632) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40881)_

### Analytics/Reporting

#### [QUANS] Kann es möglich sein, die E-Mail-ID und den Namen des Kunden in der KPI-Tabelle des Kunden unter „Erweiterte Berichterstellung“ anzuzeigen?

Adobe Commerce enthält jetzt den Vor-, Mittel- und Nachnamen des Kunden in den in das erweiterte Reporting exportierten Daten, sodass die KPI-Tabelle des Kunden den Kundennamen anzeigen kann. Zuvor wurde nur eine kodierte Kundenkennung exportiert, sodass Händler Kunden im erweiterten Reporting nicht anhand des Namens identifizieren konnten.

_ACP2E-3928 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4d0357d7)_

#### Umfangreiche EINFÜGUNG zu sales_bestsellers_aggregated_month

Verbesserte Leistung für aggregate_sales_report_bestsellers_data cron.

_ACP2E-4559 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Die Payload des Ereignisses „Zum Warenkorb hinzufügen“ befindet sich im alten Universal Analytics Enhanced E-Commerce-Format anstelle des GA4-E-Commerce-Formats.

Vor der Fehlerbehebung verwendeten E-Commerce-Ereignisse, die über Google Tag Manager an Google Analytics 4 gesendet wurden, das veraltete Universal Analytics-Format und enthielten mehrere Checkout-Ereignisse. Nach der Fehlerbehebung verwenden alle E-Commerce-Ereignisse das richtige GA4-Format und die vollständige Checkout-funnel wird verfolgt.

_ACP2E-5176 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

### B2B, Bestellung

#### Hilfe beim Bereinigen von mehr als 59M Angebotstabellen (sales_clean_quotes kann nicht ausgeführt werden)

Es wurde ein Problem behoben, bei dem der `sales_clean_quotes` Cron-Auftrag bei Instanzen mit großen Anführungszeichen-Tabellen eine Zeitüberschreitung aufwies. Zuvor wählte die Bereinigungsabfrage alle Spalten aus der `negotiable_quote` unnötigerweise aus, was dazu führte, dass MySQL eine vollständige Dateisortierung für Millionen von Zeilen durchführte; und jedes Zitat wurde einzeln über die PHP-Modellschicht gelöscht, was die Leistungskosten erhöhte.

_ACP2E-4891 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

### Warenkorb und Checkout

#### Benachrichtigung zum Warenkorb für zugehörige Produkte hinzufügen

Es wurde ein Problem behoben, bei dem die Benachrichtigung Zum Warenkorb hinzufügen das zugehörige Produkt nicht enthielt, wenn ein Produkt und das zugehörige Produkt zusammen hinzugefügt wurden.
Die Benachrichtigung zeigt jetzt die Namen beider Produkte an, die zum Warenkorb hinzugefügt wurden.

_AC-11976 - [GitHub-Problem](https://github.com/magento/magento2/issues/27164) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problem] Aktualisieren von CartRepositoryInterface.php

Die Datei „CartRepositoryInterface.php“ wurde aktualisiert, um die Ausnahmen zu deklarieren, die beim Speichern eines Warenkorbs ausgelöst werden können. Dadurch wird die Schnittstelle konsistent mit der zugrunde liegenden Warenkorb-Speicherimplementierung.

_AC-13323 - [GitHub-Problem](https://github.com/magento/magento2/issues/39328) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/29a7cdbe)_

#### [Fehler] Das Feld „Unternehmen“ in der Versandadresse wird bei der Einrichtung mehrerer Shops auf null gesetzt, wenn während des Checkout-Versandschritts eine neue Adresse hinzugefügt wird

Es wurde ein Problem behoben, bei dem das Firmenfeld nicht gespeichert wurde, wenn Kunden beim Checkout in einer Multi-Store-Einrichtung eine neue Versandadresse hinzugefügt haben. Der Unternehmenswert wird jetzt korrekt im Angebot, in der aufgegebenen Bestellung und im Kundenadressbuch gespeichert.

_AC-13456 - [GitHub-Problem](https://github.com/magento/magento2/issues/39424) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/515d3dd3)_

#### PayPal > Kundendatenkonflikt (Präfix, Vorname, Nachname)

Es wurde ein Problem behoben, bei dem Kundennamendetails während des PayPal-SEPA-Checkout-Flusses falsch zugeordnet wurden. Präfix, Vorname und Nachname werden jetzt korrekt in der Reihenfolge ausgefüllt, ohne dass eine Übereinstimmung vorliegt.

_AC-15366 - [GitHub-Problem](https://github.com/magento/magento2/issues/39061) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Falsche Free_Shipping-Markierung für virtuelle Produkte

Es wurde ein Problem behoben, bei dem das Flag „free_shipping“ für virtuelle Produkte falsch gesetzt wurde, wenn mehrere Artikel zum Warenkorb hinzugefügt wurden. Das Flag ist jetzt für alle Artikel korrekt gesetzt, wenn die entsprechende Versandregel angewendet wird.

_AC-15648 - [GitHub-Problem](https://github.com/magento/magento2/issues/40184) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c10554e1)_

#### Gast-Add-to-cart: Mini-Warenkorb-/Kundendaten-„Warenkorb“-Abschnitt unter meldet Warenkorb als leer, obwohl der Artikel korrekt persistiert wurde

Es wurde ein Problem behoben, bei dem der Gast-Mini-Warenkorb Elemente nicht sofort nach dem Hinzufügen eines Produkts zum Warenkorb zeigte. Der Zähler und das Dropdown-Menü des Mini-Warenkorbs werden nun korrekt aktualisiert, und hinzugefügte Produkte werden wie erwartet im Warenkorb angezeigt.

_AC-17973 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2b218686)_

#### AJAX-Inline-Fehlermeldungen vom Typ „In den Warenkorb legen“, verloren role=„alert“-Semantik

Es wurde ein Problem behoben, bei dem Fehlermeldungen zum Hinzufügen zum Warenkorb von AJAX in der Storefront sichtbar waren, aber von Sprachausgaben nicht angekündigt wurden. Fehler beim Hinzufügen zum Warenkorb werden jetzt in einer barrierefreien role=„alert“-Region angezeigt, um die Barrierefreiheit zu unterstützen.

_AC-18036 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2b218686)_

#### Nachfolgende Regeln für den Versandbetrag verwerfen

Um eine genaue Preisgestaltung für Werbeaktionen und die strikte Einhaltung der konfigurierten Rabattregeln zu gewährleisten, wurde ein Fehler im Warenkorbpreisregelrechner behoben, bei dem Versandrabatte mit niedrigerer Priorität falsch angewendet wurden

_AC-9612 - [GitHub-Problem](https://github.com/magento/magento2/issues/37985) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40869)_

#### Es wurden doppelte Bestellungen erstellt, obwohl der Fehler ausgelöst wurde

Es wurde ein Problem behoben, bei dem Bestellungen weiterhin mit einer ungültigen Kundenadresse aufgegeben werden konnten

_ACP2E-4774 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Auswirkungen der konfigurierbaren Produktleistung auf den Checkout (Summen-Informationen, Schätzung-Versand-Module)

Vor der Fehlerbehebung könnten Checkout-Anfragen wie totales-information und estimated-shipping-methods bei konfigurierbaren Produkten mit vielen untergeordneten Produkten erheblich langsamer sein, wenn das erste verkaufsfähige Kind spät in der Unterliste auftauchte. Nach der Behebung tritt diese Leistungsbeeinträchtigung nicht mehr auf und die Antwortzeiten bleiben unabhängig von der Position des ersten verkäuflichen Kindes gleich.

_ACP2E-4805 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Warenkorbsummen werden in jeder Ansicht der Warenkorbseite neu berechnet

Optimierte Warenkorbsummenanfragen auf der Warenkorbseite. Die Gesamtwerte für den Warenkorb werden in jeder Ansicht der Warenkorbseite zweimal neu berechnet.

_ACP2E-4817 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

#### Die Validierungsregeln für Stadt und Straße des Kundenadressattributs (EAV) stehen im Konflikt mit hartcodierten Validierungsregeln.

Fehlerkorrektur - Der City Validator hat fälschlicherweise gültige Stadtnamen mit mehr als 100 Zeichen zurückgewiesen (Datenbanklimit ist 255) und Straßenadressen mit mehr als 255 Zeichen in der Datenbank ohne\
Gibt einen Validierungsfehler zurück. Beide Validatoren erzwingen jetzt Beschränkungen, die mit der engsten Datenbankspaltenbeschränkung für alle Adresstabellen abgestimmt sind.

_ACP2E-4861 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

#### [Storefront] Nachricht „Angeforderte Menge ist nicht verfügbar“ in Warenkorb gelegentlich nicht auf PDP gerendert

Fehlerkorrektur - Die Meldung „Lager nicht verfügbar“ (Die angeforderte Menge ist nicht verfügbar. Bitte reduzieren Sie die Menge.) wurde nach einem fehlgeschlagenen Versuch zum Warenkorb hinzufügen gelegentlich nicht auf der Produktdetailseite angezeigt. Zuvor konnte die Seite im Hintergrund ohne Fehlerfeedback aktualisiert werden, wenn ein Käufer wiederholt auf Zum Warenkorb hinzufügen für ein Produkt klickte, dessen verfügbarer Bestand bereits vollständig im Warenkorb reserviert war.

_ACP2E-5071 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d70f246)_

#### Beständiger Warenkorb bei Ablauf der natürlichen Sitzung geleert, wenn Beständigkeit bei Abmeldung löschen = Ja

Es wurde ein Problem behoben, bei dem der persistente Warenkorb gelöscht wurde, wenn die Browser-Sitzung abgelaufen war. Zuvor wurde bei aktivierter Option „Persistenz beim Abmelden löschen“ der Warenkorb bei einer abgelaufenen Sitzung geleert und das persistente Cookie entfernt, obwohl sich der Käufer nicht abgemeldet hatte.

_ACP2E-5088 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

#### Gastangebot customer_email wurde nach restoreQuote() nicht von der Rechnungsadresse neu synchronisiert, wenn der Checkout erneut versucht wird

Fehlerkorrektur - Beim erneuten Versuch eines fehlgeschlagenen Gast-Checkouts wird die Bestellung nicht mehr mit der aktualisierten, sondern mit der zuvor eingegebenen E-Mail aufgegeben.

_ACP2E-5188 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

### Warenkorb und Checkout, GraphQL

#### Die Zitat-GraphQL-API kann Zitatfeldern Währungsobjekte anstelle von ISO-Währungscodes zuweisen

Die GraphQL-API für Angebote wurde aktualisiert, um ISO-Währungscodes den Speicher- und Angebotwährung-Feldern eines Angebots zuzuweisen, anstatt Währungsobjekte zuzuweisen.

_ACP2E-5229 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

### Katalog

#### [Problem] module.xml-Dateiverbesserungen für die Module Magento_ConfigurableProductGraphQL, Magento_MsrpConfigurableProduct, Magento_NewRelicReporting und Magento_Swatches.

Die Architektur der Moduldeklaration wurde optimiert, indem redundante Magento_Catalog-Abhängigkeiten aus vier Kern-Untermodulen entfernt wurden. Diese Bereinigung behebt unnötige Duplizierungen in der Abhängigkeitsstruktur, optimiert die Berechnung der Ladereihenfolge von Modulen und verbessert die langfristige Wartbarkeit des Frameworks, ohne grundlegende Änderungen vorzunehmen.

_AC-10762 - [GitHub-Problem](https://github.com/magento/magento2/issues/30675) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/30638)_

#### Möglicher Speicherverlust in der getUsedProducts-Funktion für konfigurierbare Dateien

Es wurde ein Problem behoben, bei dem die Verarbeitung mehrerer konfigurierbarer Produkte dazu führte, dass die Ausführungszeit und die Speichernutzung im Laufe der Zeit zunahmen.
Konfigurierbare Produkte können jetzt ohne die fortschreitende Verlangsamung und Speichererhöhung verarbeitet werden.

_AC-10942 - [GitHub-Problem](https://github.com/magento/magento2/issues/37639) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/8c058c2e)_

#### Filter „Nach Kategorie kaufen“ für Nicht-Anker-Kategorien sichtbar

Es wurde ein Problem behoben, bei dem der Filter Nach Kategorie kaufen für Nicht-Anker-Kategorien angezeigt wurde, selbst wenn der Kategoriefilter in Admin deaktiviert war.
Der Filter wird nun gemäß der konfigurierten Einstellung in der Storefront ausgeblendet.

_AC-10945 - [GitHub-Problem](https://github.com/magento/magento2/issues/38379) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64eb754d)_

#### Datentyp von applied_rule_ids in Angebot und Anführungselement ist unterschiedlich

Um die absolute Konsistenz des Datenbankschemas sicherzustellen und kritische Diskrepanzen zwischen den Warenkorbdaten in Werbe-Stores mit hohem Volumen zu verhindern, wurde die Datenspalten-Tracking für aktive Promo-Definitionen über übergeordnete Checkout-Strukturen hinweg erweitert.

_AC-14518 - [GitHub-Problem](https://github.com/magento/magento2/issues/39838) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40540)_

#### Das Attribut für `decimal` Produktsammlung kann nicht abgerufen werden, wenn der Preis global festgelegt ist.

Um präzise Preise für Storefronts und Attributrendering in internationalen Setups sicherzustellen, wurde ein Fehler bei der Core-Datenerfassung behoben, bei dem store-spezifische Dezimalwerte fälschlicherweise durch globale Standardwerte ersetzt wurden.

_AC-15806 - [GitHub-Problem](https://github.com/magento/magento2/issues/40218) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40419)_

#### Falsche Verarbeitung der GET-Parameter

Um die Plattformstabilität zu verbessern und den Checkout-funnel zu schützen, wurde eine Eingabevalidierungsschicht auf Blockebene hinzugefügt, um zu verhindern, dass fehlerhafte URL-Abfragen die Storefront-Produktseiten zum Absturz bringen.

_AC-16262 - [GitHub-Problem](https://github.com/magento/magento2/issues/40405) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributes wird in allen Warenkorbabfragen ausgelöst

Um die Belastung bei der Datenbankausführung zu reduzieren und nicht optimierte Datenbanktreffer während des Kunden-Checkouts zu vermeiden, wurde das Plug-in für die Konfiguration von Verkaufsregeln optimiert, um bedingte Ausführungsvorgänge auszuführen und Caching-Strukturen zu nutzen.

_AC-16559 - [GitHub-Problem](https://github.com/magento/magento2/issues/40226) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40251)_

#### [Problem] [PHPDOC] Korrigieren Sie die Funktionen orderComment in Magento\Sales\Model\Order

Um strikte Typisierungsbeschränkungen zu beseitigen, die Genauigkeit der statischen Analyse zu verbessern und das Entwicklererlebnis unter rigorosen Linting Engines wie PHPStan (Stufe 5 oder höher) zu verbessern, wurden Inline-Struktur-Dokumentationsblöcke innerhalb der Kernsubsysteme für Kundenaufträge standardisiert.

_AC-16759 - [GitHub-Problem](https://github.com/magento/magento2/issues/39575) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39572)_

#### [Problem] [Bug] GraphQL SearchCriteriaValidator nicht geladen — entfernt durch module-graph-ql di.xml Array-Überschreibung

Um eine robuste Abfragevalidierung beizubehalten und Platform-Leitplanken zu erzwingen, wurde ein Konfigurationsfehler bei der Abhängigkeitseinschleusung (Dependency Injection, DI) behoben, bei dem die SearchCriteriaValidator-Ebene versehentlich deaktiviert wurde.

_AC-16959 - [GitHub-Problem](https://github.com/magento/magento2/issues/40762) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40742)_

#### strpos() erwartet, dass Parameter 1 String ist, Array gegeben | magento/module-eav

Zum Schutz der Stabilität der Storefront und zur Bereitstellung eines unterbrechungsfreien Erlebnisses bei der Kundensuche wurde ein kritischer Fehler wegen nicht übereinstimmender Typen mit den erweiterten Suchmaschinen für die Katalogsuche behoben.

_AC-1706 - [GitHub-Problem](https://github.com/magento/magento2/issues/33588) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40422)_

#### Leere Angebotsdatensätze werden erstellt, wenn ein Kunde eine Seite besucht

Beim Besuch einer Produktseite auf der Storefront werden in einigen Situationen keine leeren Anführungszeichen erstellt.
Zuvor wurden leere Angebotssätze erstellt, wenn ein Kunde eine Produktseite in der Storefront besucht

_ACP2E-4682 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Das Attribut „Gewichtung“ der Produktdetailseite zeigt im Abschnitt „Zusätzliche Informationen“ kein Einheitensuffix an.

Es wurde das Problem behoben, bei dem das Attribut „Gewichtung“ auf der Storefront-Produktseite im Abschnitt „Zusätzliche Informationen“ oder „Weitere Informationen“ nur einen numerischen Rohwert ohne die konfigurierte Maßeinheit (lbs oder kg) anzeigte.

_ACP2E-4808 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud] Aktivierung der Katalogpreisregel wird in der Live-Suche erst bei der nächsten erzwungenen Resynchronisierung widergespiegelt — Verzögerung bei der Preisvorschubsynchronisierung

Es wurde ein Problem behoben, bei dem beim Aktivieren einer Katalogpreisregel die Preise in der Live-Suche erst aktualisiert wurden, nachdem eine spätere Resynchronisierung erzwungen wurde. Der Preisfeed-Indexer konnte ausgeführt werden, bevor der Katalogregel-Indexer, von dem er abhängt, fertig war, und so veraltete Preise exportiert hat. Indexer mit nicht abgeschlossenen Abhängigkeiten werden jetzt auf die nächste Cron-Ausführung verschoben, sodass der Preis-Feed immer mit den aktuellen Preisen ausgeführt wird.

_ACP2E-5029 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec436b10)_

#### Alternativtext (Beschriftung) wird für ein neu hinzugefügtes Produktbild nicht gespeichert

Es wurde ein Problem behoben, bei dem der Alternativtext (Titel) eines neu hochgeladenen Produktbilds nicht gespeichert wurde, wenn die hochgeladene Datei beim Speichern aufgrund einer Dateinamenkollision in der Mediensammlung umbenannt wurde. Zuvor wurden die Bildrollenattribute (image, small_image, thumbnail) korrekt gespeichert, aber die entsprechenden *_label-Attribute wurden im Hintergrund abgelegt, sodass der Alternativtext auf Storefront-Such- und Listingseiten leer blieb. Der Handler zum Erstellen von Galerien löst die umbenannte Datei jetzt wieder in den ursprünglichen Bildeintrag auf, sodass die Beschriftung für alle zugewiesenen Bildrollen beibehalten wird. Daher wird der bei der Produkterstellung eingegebene Alternativtext zuverlässig gespeichert und in der Storefront gerendert.

_ACP2E-5216 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

#### PHP 8.5 „null as array offset“ Fehler beim Öffnen der Seite Produkt hinzufügen in Admin, wenn der Benutzer nicht über die Ressource Produktstatus bearbeiten verfügt

Zuvor konnte bei Admin-Benutzern ohne die Berechtigung „Produktstatus bearbeiten“ beim Öffnen der Seite „Produkt hinzufügen“ der Fehler „null als Array-Offset“ auftreten. Dies wurde behoben, sodass die Seite unabhängig von den Produktstatusberechtigungen des Benutzers korrekt geladen wird.

_ACP2E-5248 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

### Catalog, GraphQL

#### [GraphQL]-Produktabfragepreisfilterprobleme bei in AdminHTML eingegebenen Nettopreisen

Es wurde ein Problem behoben, bei dem in der GraphQL-Produktabfrage bei der Anwendung eines Preisfilters keine Steuer berücksichtigt wurde.
Der Preisfilter verwendet nun den angezeigten steuerinklusiven Preis, sodass nur Produkte innerhalb der angegebenen Preisspanne zurückgegeben werden.

_AC-6883 - [GitHub-Problem](https://github.com/magento/magento2/issues/36337) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8b67e8ed)_

### Katalog, SEO

#### Kategorie URL_PATH wird bei url_key-Änderung für alle Store-Ansichten nicht synchronisiert

Zuvor konnte eine Änderung des URL-Schlüssels einer Kategorie im Bereich „Alle Store-Ansichten“ untergeordnete Kategorien mit einem veralteten oder falsch vorangestellten url_path belassen, und die Bearbeitung einer Kategorie mit einer eigenen store-spezifischen url_path-Überschreibung konnte den URL-Schlüssel vor der Bearbeitung anstelle des neu eingegebenen Schlüssels übernehmen. Dies ist jetzt behoben. Der URL-Schlüssel ändert sich korrekt an alle untergeordneten Elemente im Store-Bereich in der richtigen hierarchischen Reihenfolge mit dem richtigen übergeordneten Pfad, und die Überschreibung des eigenen Store-spezifischen URL-Pfads einer Kategorie wird mithilfe des gerade geänderten URL-Schlüssels neu berechnet, sodass die URLs im Store-Bereich sofort nach dem Speichern korrekt bleiben.

_ACP2E-5113 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

### Cloud, Framework

#### Performance-Regression und falscher Cache-Speicher mit aktiviertem SymfonyL2

Fehlerkorrektur - Beim Konfigurieren des L1-Cache-Speicherpfads als absoluter Pfad (z. B. /dev/shm) wird er jetzt nicht mehr leise zum Verzeichnis var/ umgeleitet. Fehlerkorrektur - Die Invalidierung von Cache-Tags in großen Katalogen kann zu erheblichen Verzögerungen bei der Reaktionszeit aufgrund eines blockierenden Redis-Vorgangs führen.

_ACP2E-4989 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/51f6d191)_

### Inhalt

#### Die AJAX-Vorschauanforderung von Page Builder gibt einen 500-Fehler mit deaktiviertem Übersetzungs-Cache zurück

Die PageBuilder-Vorschau wird jetzt korrekt gerendert, unabhängig davon, ob der Cache für Übersetzungen aktiviert oder deaktiviert ist. Zuvor konnte die PageBuilder-Vorschau nicht gerendert werden, wenn der Cache für Übersetzungen deaktiviert wurde.

_ACP2E-5118 - [GitHub-Code-Beitrag](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### Animierte GIF-Uploads werden in PNG konvertiert, wenn Alte Mediensammlung aktivieren aktiviert ist

Es wurde ein Problem behoben, bei dem animierte GIF-Bilder, die über die Mediensammlung hochgeladen wurden, in PNG konvertiert wurden, wenn die alte Mediensammlung aktiviert war. Wenn die Option Frontend-Größenänderung aktivieren aktiviert war, haben animierte GIFs, die über die Old Media Gallery hochgeladen wurden, zuvor die Animation verloren und wurden als statische PNG-Dateien gespeichert. Animierte GIFs werden jetzt hochgeladen und im Originalformat gespeichert.

_ACP2E-5232 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

### Inhalt/CMS

#### [Problem] Beheben Sie die Registerkarte „Produktkatalog“, wenn eine Bildattributbeschriftung ein einzelnes Anführungszeichen enthält

Um ein zuverlässiges und unterbrechungsfreies Katalogmanagement im Administrationsbereich zu gewährleisten, wurde ein JavaScript-Formatierungsfehler behoben, der die Backend-Benutzeroberfläche des Produktarbeitsbereichs vollständig beschädigte

_AC-16474 - [GitHub-Problem](https://github.com/magento/magento2/issues/40519) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40870)_

#### [Problem] Verbessern Sie die Leistung, wenn auf die URL des Bildes in der Größenanpassung zugegriffen wird, sie jedoch noch nicht vorhanden ist.

Um die Reaktionsgeschwindigkeit bei der Asset-Bereitstellung zu maximieren, die E/A-Vorgänge auf Serverfestplatten erheblich zu reduzieren und starke Serverprozessorspitzen zu vermeiden, wurde das Subsystem für die Erstellung von Katalogbildern optimiert, um fehlende Medien-URLs ausschließlich nach Bedarf zu verarbeiten.

_AC-16547 - [GitHub-Problem](https://github.com/magento/magento2/issues/40399) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40388)_

#### Regression: Die nicht UTF-8-kodierte URI-Komponente gibt weiterhin „Wert kann nicht serialisiert werden“ in CatalogWidget auf 2.4.7-p5 aus.

Um kritische Rendering-Fehler zu vermeiden, die durch fehlerhaften Produktions-Webtraffic verursacht werden, wurde der Katalog-Widget-Block dahingehend erweitert, dass er Nicht-UTF-8-Datensequenzen in angeforderten URLs ordnungsgemäß verarbeitet.

_AC-17264 - [GitHub-Problem](https://github.com/magento/magento2/issues/40824) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40825)_

#### `Using null as an array offset is deprecated, use an empty string instead` beim Bearbeiten des globalen Designkonfigurationsumfangs

Es wurde ein Problem behoben, bei dem beim Bearbeiten des globalen Bereichs unter Inhalt > Design > Konfiguration aufgrund eines veralteten Null-Array-Offsets ein HTTP-500-Fehler in PHP 8.5 zurückgegeben wurde. Die Konfiguration Globaler Entwurf wird jetzt erfolgreich und ohne Fehler geöffnet.

_AC-17456 - [GitHub-Problem](https://github.com/magento/magento2/issues/40886) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/515d3dd3)_

### Framework

#### Wählen Sie aus media_storage_file_storage , wenn der Media DB-Speicher nicht verwendet oder deaktiviert ist

Um unnötigen Datenbank-Query-Overhead zu reduzieren und laute Systemausnahmen zu vermeiden, wurde die Synchronisierungsschicht für Mediendateien optimiert, um Datenbankspeicherprüfungen zu umgehen, wenn das System explizit für die Verwendung des lokalen Dateisystems konfiguriert ist

_AC-10586 - [GitHub-Problem](https://github.com/magento/magento2/issues/38116) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40480)_

#### Schwerwiegender Fehler, der auf dem Ausnahmekonstruktor ausgelöst wurde, wenn der Cookie-Speicher ein Array ist

Es wurde ein Problem behoben, bei dem ein ungültiger Store-Cookie-Wert einen schwerwiegenden PHP-Fehler verursachte.
Magento gibt jetzt korrekt die Ausnahme „Ungültiger Speicherparameter“ aus, wenn das Speicher-Cookie einen ungültigen Wert enthält.

_AC-10888 - [GitHub-Problem](https://github.com/magento/magento2/issues/38365) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [Problem] Verwenden Sie statische Konstanten in Magento\Customer\Model\Address\Config.

Es wurde ein Problem behoben, bei dem benutzerdefinierte Adresskonfigurationsklassen getFormats() duplizieren mussten, um einen benutzerdefinierten Pfad für Adressvorlagen zu verwenden. Benutzerdefinierte Adresskonfigurationen können jetzt ihren eigenen Vorlagenpfad mithilfe einer statischen Konstante definieren, ohne die Methode zu duplizieren.

_AC-12906 - [GitHub-Problem](https://github.com/magento/magento2/issues/39135) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/29a7cdbe)_

#### processFilter kann nicht für Produktsammlung verwendet werden

Fehlerkorrektur - Das Anwenden mehrerer Filter auf eine Produktsammlung mithilfe von FilterProcessor hat einen PHP-Fehler verursacht. Produktsammlungen können jetzt mithilfe mehrerer Filterbedingungen korrekt gefiltert werden.

_AC-15018 - [GitHub-Problem](https://github.com/magento/magento2/issues/40014) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/7aecc9f1)_

#### Potenzielles Indexerleistungsproblem für große Kataloge - Masseneinfügung und Sperren der gesamten CL-Tabelle, um die neueste Version zu identifizieren

Um die Datenbankleistung bei großen Katalogen im Unternehmensmaßstab zu gewährleisten, wurde die Indexer-Pipeline der Systemdatenbank gehärtet, um geplante Datenänderungen in begrenzten Batches zu analysieren, wodurch Datenblöcke mit hohem Druck vermieden werden.

_AC-16238 - [GitHub-Problem](https://github.com/magento/magento2/issues/40331) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40546)_

#### [Problem] Leistungsverbesserung

Um unnötige Speicherzuweisung zu vermeiden und den Overhead der Laufzeitverarbeitung zu reduzieren, wurden mehrere Core-String-Manipulationsroutinen überarbeitet, um optimiertes natives PHP-Verhalten zu nutzen.

_AC-16565 - [GitHub-Problem](https://github.com/magento/magento2/issues/40383) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40375)_

#### [Problem] Behebung der Unterstützung für GLOB_BRACE auf Nicht-GNU-Linux-Systemen

Um eine nahtlose Bereitstellung in einfachen Virtualisierungsumgebungen zu gewährleisten, wurde ein kritischer Pfadsuchfehler behoben, um die Ausführungsunterstützung für Systeme, die nicht-GNU-Bibliotheken verwenden, wie Alpine Linux Docker-Images, vollständig wiederherzustellen.

_AC-16568 - [GitHub-Problem](https://github.com/magento/magento2/issues/40552) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40538)_

#### Marketing-Parameter wieder in die Abfrage eingefügt, die für die Erstellung der integrierten FPC-Kennung verwendet wird

Um die Cache-Trefferraten zu verbessern und Regressionen bei der Server-Leistung zu vermeiden, wurde ein struktureller Fehler im nativen integrierten Full Page Cache (FPC)-System behoben, bei dem Marketing- und Tracking-Abfrageparameter versehentlich in Cache-Kennungssignaturen wieder eingeführt wurden.

_AC-16583 - [GitHub-Problem](https://github.com/magento/magento2/issues/40350) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40349)_

#### Unterstützung für einfache Objekte mit hochgestuften Eigenschaften in der Nachrichtenwarteschlangen-Kommunikation hinzufügen

Um moderne PHP-Entwicklungspraktiken zu unterstützen und asynchrone Architektur-Workflows zu vereinfachen, wurde die Framework Reflection Engine verbessert, um nativ Datenübertragungs-Objekte (DTOs) mit öffentlichen, unterstützten und schreibgeschützten Konstruktor-Eigenschaften zu verarbeiten.

_AC-16672 - [GitHub-Problem](https://github.com/magento/magento2/issues/36660) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40457)_

#### [Problem] Beheben: Die Selbstprüfung des realen Spaltentyps überspringt nicht signierte/nullfähige Prozessoren, verwendet Standardwerte

Um eine genaue Verfolgung des System-Setups zu gewährleisten, wurde ein Fehler bei der Datenbankabstraktion behoben, bei dem deklarative Schemaüberprüfungsbefehle ständig ausstehende Änderungsänderungen für DOUBLE UNSIGNED-Spalten melden, denen es an expliziten Präzisions- oder Skalierungsattributen fehlt.

_AC-16758 - [GitHub-Problem](https://github.com/magento/magento2/issues/40646) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40582)_

#### [Funktion] Unterstützung des Status „Deaktiviert“ für einzelne Auswahloptionen in der Admin-Konfiguration

Um die Flexibilität von Backend-Formularen zu verbessern und Entwicklern eine granulare Layout-Steuerung zu bieten, wurde die Unterstützung auf Framework-Ebene eingeführt, um einzelne Optionstags innerhalb von Formularelementen als nicht auswählbar zu markieren.

_AC-16761 - [GitHub-Problem](https://github.com/magento/magento2/issues/40564) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40565)_

#### ⚡ Performance: Fehlender Speicher im StoreManager und Plug-in-Overhead im Store-Modul

Um die CPU-Ausführungsbelastung drastisch zu reduzieren und unnötige Anwendungsspeicherabwanderungen zu minimieren, wurde eine wichtige Konfigurationswert-Caching-Routine implementiert, um redundante Speicherprüfprozesse abzufangen.

_AC-16838 - [GitHub-Problem](https://github.com/magento/magento2/issues/40706) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40732)_

#### [Problem] Behebung: Entfernen des toten openssl_free_key()-Code-Pfads in JwkFactory

Um strukturelle Technologieschulden zu bereinigen und Kryptografie-Tools an moderne Ausführungsprofile anzupassen, wurden alte ressourcenschonende Hooks aus dem JSON Web Key Utility-Backend entfernt.

_AC-16958 - [GitHub-Problem](https://github.com/magento/magento2/issues/40761) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40688)_

#### [Problem] Rechtschreibung für PHPDoc-Korrektur

Um die hohen Code-Qualitätsstandards beizubehalten und die Genauigkeit der Code-Hinweise in der integrierten Entwicklungsumgebung (IDE) zu verbessern, wurden strukturelle Bereinigungen auf Inline-Code-Dokumentationsebenen in den Kern-Framework-Modulen angewendet.

_AC-16960 - [GitHub-Problem](https://github.com/magento/magento2/issues/40763) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40745)_

#### [Problem] perf(di:compile): Cache-ReflectionClass-Instanzen in Type, Config/Reader und ClassReader

Um die Kompilierungszeiten erheblich zu beschleunigen und den Durchsatz der kontinuierlichen Integration (CI) zu maximieren, wurde das interne Dependency Injection Compiler Backend (`setup:di:compile`) optimiert, um redundante PHP-Reflexionszyklen zu eliminieren.

_AC-17077 - [GitHub-Problem](https://github.com/magento/magento2/issues/40796) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40615)_

#### [Problem] Aktualisieren Sie Filter.php, um `{{block template="Magento_Module::path/to/template.phtml"}}` zuzulassen und \Magento\Framework\View\Element\Template als Standardklasse festzulegen

Um die Inhaltserstellung zu vereinfachen und CMS-Anweisungen an Vorlagenlayoutstandards anzupassen, wurde das Kernsystem für die Verarbeitung von Markup-Tags verbessert, sodass Blockdeklarationen ohne explizite Klassendefinition unterstützt werden.

_AC-17078 - [GitHub-Problem](https://github.com/magento/magento2/issues/38477) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38469)_

#### [Problem] perf(di:compile): Speichern des Interception-Konfigurations-Scope liest während der Kompilierung

Um Site-Bereitstellungen und automatisierte Backend-Kompilierung erheblich zu beschleunigen, wurde der Dependency Injection Compiler (`setup:di:compile`) optimiert, um redundante XML-Parsing-Vorgänge zu vermeiden.

_AC-17313 - [GitHub-Problem](https://github.com/magento/magento2/issues/40852) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40614)_

#### Aktualisieren Sie underscore.js auf 1.13.8, um Sicherheitslücken zu schließen

Die gebündelte Underscore.js-Bibliothek (lib/web/underscore.js) wurde von 1.13.7 auf 1.13.8 aktualisiert. Es sind keine Konfigurationsänderungen erforderlich.

_AC-17349 - [GitHub-Problem](https://github.com/magento/magento2/issues/40857) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/12d0be1e)_

#### Das Magento-Composer-Installationsprogramm lässt im Hintergrund Setup/Cloud (und andere zugeordnete Verzeichnisse) unbefüllt, wenn ein Bereitstellungsziel ein Symlink ist

Es wurde ein Problem behoben, bei dem magento-composer-installer beim Konfigurieren des Bereitstellungsziels als symbolischer Link im Hintergrund das Setup/Mapping und andere vom Composer zugeordnete Verzeichnisse nicht auffüllen konnte. Dies kann zu fehlenden Dateien und einer unvollständigen Commerce-Bereitstellung führen.

_AC-17360 - [GitHub-Problem](https://github.com/magento/magento2/issues/40864)_

#### Cache-Preload-Schlüssel benötigen kein ID-Präfix mehr, wenn der Symfony Cache-Adapter verwendet wird

Preload-Schlüssel (preload_keys) für den Symfony Cache-Adapter können jetzt ohne das Cache-ID-Präfix konfiguriert werden. Zuvor wurde nach der dokumentierten Konfiguration und dem Einschließen des Präfixes in jeden Schlüssel (z. B. 061_SYSTEM_DEFAULT) verhindert, dass die Schlüssel vorgeladen wurden. Sie können die Schlüssel jetzt genau so angeben, wie die Anwendung sie anfordert (z. B. SYSTEM_DEFAULT), und Adobe Commerce wendet das id_prefix automatisch an.

_AC-17407 - [GitHub-Problem](https://github.com/magento/magento2/issues/40877) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/3a6b9667)_

#### [Problem] Behebung der PHP 8.5-Einstellung, wenn das Kategorieattribut „frontend_input“ enthält …

Es wurde ein Problem behoben, bei dem das Öffnen einer Kategorie im Admin-Bedienfeld einen Fehler in PHP 8.5 verursachte, wenn für ein Kategorieattribut frontend_input auf null gesetzt war. Kategorieseiten können jetzt geöffnet und erfolgreich bearbeitet werden, ohne dass ein Fehler bei der Einstellung auftritt.

_AC-17499 - [GitHub-Problem](https://github.com/magento/magento2/issues/40908) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [Problem] Veraltete PHPUnit-Assertionen und Test-Stub-Konfiguration ersetzen

Die Test-Suite von Magento 2 für zukünftige PHPUnit-Upgrades wurde aktualisiert, indem sieben veraltete PHPUnit-Verwendungen ersetzt wurden. Die Änderungen betreffen `isType()` Assertionen und `with*()` auf Test-Stubs - Muster, die Trigger in aktuellen PHPUnit-Versionen feststellen und die in PHPUnit 13 oder höher entfernt werden sollen.

_AC-17750 - [GitHub-Problem](https://github.com/magento/magento2/issues/41040) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/41033)_

#### GraphQL order_date- und comment-Zeitstempel geben unter nicht-de_US-Gebietsschemata ein falsches Kalenderdatum zurück (IntlDateFormatter falsch analysieren) — AC-14431-Fehlerbehebung unvollständig

Es wurde ein Problem behoben, bei dem GraphQL-Bestelldaten für französische und deutsche Gebietsschemata ein falsches Kalenderdatum anzeigen konnten.
Bestelldaten und zugehörige Kommentarzeitstempel geben jetzt das richtige Datum und die richtige Uhrzeit zurück.
Die Datumsformatierung wurde verbessert, sodass GraphQL-Datumswerte von Anwendungen zuverlässig analysiert werden können.
Das vorhandene Verhalten für das Gebietsschema en_US bleibt unverändert.

_AC-18084 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/d10ab92b)_

#### [Problem] Unzulässiges @author entfernen

Um eine strikte Übereinstimmung mit den wichtigsten technischen Richtlinien sicherzustellen, wurde ein inkrementeller Sweep zur Code-Wartung durchgeführt, um Inline-Dokumentationsblöcke für Ressourcen über mehrere Systemmodule hinweg zu bereinigen.

_AC-8366 - [GitHub-Problem](https://github.com/magento/magento2/issues/37248) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36993)_

#### [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Catalog` (Teil 2)

Um eine vollständige Anpassung an die Bereitstellungsrichtlinien für Unified Code von Magento sicherzustellen, wurde ein inkrementeller Bereinigungsdurchgang ausgeführt, um nicht konforme Dateikommentare systematisch aus den grundlegenden Storefront-Ressourcenmodellen zu entfernen.

_AC-8370 - [GitHub-Problem](https://github.com/magento/magento2/issues/37247) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/36988)_

#### Stufe Preis Speicherschnittstelle Löschen Bug löscht nicht alle Stufen Preise

Es wurde ein Problem in TierPriceStorage behoben, bei dem beim Löschen von Produktstufenpreisen über mehrere Websites nicht alle Preise gelöscht werden konnten, indem die Abgleichlogik der Preis-ID aktualisiert wurde, um die zugewiesene Website-ID zu berücksichtigen.

_AC-9738 - [GitHub-Problem](https://github.com/magento/magento2/issues/37949) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40557)_

#### [B2B] Bestellungen werden nicht automatisch in Kundenaufträge mit ActiveMQ konvertiert

Es wurde ein Problem behoben, bei dem von Cron gestartete Verbraucher keine Nachrichten verarbeiteten, wenn ActiveMQ mit dem STOMP-Protokoll verwendet wurde. Daher wurden automatisch genehmigte Bestellungen nicht in Kundenaufträge umgewandelt. Die Nachrichtenverarbeitung für STOMP-Warteschlangen ist jetzt zuverlässiger und konsistenter mit der DB- und AMQP-Warteschlangenimplementierung.

_ACP2E-4349 - [GitHub-Code-](https://github.com/magento/magento2/commit/08b91f1a) - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/239464da)_

#### Fehler beim Exportieren mit konfiguriertem AWS S3-Speicher

Der Produktexport funktioniert jetzt ordnungsgemäß, wenn der AWS S3-Remote-Speicher konfiguriert ist. Zuvor konnten exportierte Dateien aufgrund einer ungültigen Pfadauflösung im Speichertreiber nicht in S3 geschrieben werden.

_ACP2E-4786 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Indexer stecken in einer Selbstsperrschleife mit dem Anbieter &#39;use_application_lock&#39; und &#39;file&#39; fest

Es wurde ein Problem behoben, bei dem Indexer während der Neuindizierung unbegrenzt hingen, wenn die Einstellung „Indexer use_application_lock“ zusammen mit dem Dateisperranbieter aktiviert wurde. Die Neuindizierung wird jetzt erwartungsgemäß abgeschlossen.

_ACP2E-5027 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec436b10)_

#### Langsame Leistung mit MAGENTO_DC-Variablen, die in der Cloud-Benutzeroberfläche festgelegt sind

Nach der Behebung wird die Bereitstellungskonfiguration nicht jedes Mal neu geladen, wenn der angeforderte Schlüssel nicht vorhanden ist und einige Umgebungsvariablen definiert sind.

_ACP2E-5094 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2b9e8316)_

#### [CLOUD] Fehlerhafter URL-Pfad gibt beim URL-Rewrite-Router HTTP 500 statt 404 zurück

Es wurde ein Problem behoben, bei dem eine falsch formatierte Storefront-URL eine HTTP-500-Fehlerseite anstelle der standardmäßigen 404-Fehlerseite zurückgab. Zuvor führten bestimmte falsch formatierte Anfragepfade zu einem nicht abgefangenen Fehler während der URL-Umschreibungsauflösung.

_ACP2E-5154 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4d0357d7)_

#### [CLOUD] PHP 8.5-Kompatibilität — ComponentRegistrar::getPath() null array offset crashes setup:static-content:deploy (compact strategy) auf 2.4.9

Fehlerkorrektur - `setup:static-content:deploy` in PHP 8.5 schlägt nicht mehr fehl mit dem Fehler „Using null as an array offset“ , wenn Module LESS-Dateien kompiliert werden, die die //@magento_import-Direktive verwenden. Die Bereitstellung statischer Inhalte wird jetzt in PHP 8.5 erfolgreich abgeschlossen.

_ACP2E-5183 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS] Falsch-Positiv „Ungültiger HTML-Inhalt bereitgestellt“ beim Speichern des CMS-Blocks mit einem Anker href gefolgt von einem anderen Attribut

CMS-Inhalte, die einen standardmäßigen Anker-Link enthalten (z. B. `&lt;a href="https://example.com/page" target="_blank" rel="noopener">`), haben keinen falschen Trigger mehr: Bei aktiviertem CMS/WYSIWYG/FORCE_VALID wird die Validierungswarnung „Ungültiger HTML-Inhalt bereitgestellt“ oder ein Speicherfehler angezeigt.

_ACP2E-5203 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

### Framework, GraphQL

#### Das Array-Element „di.xml“ wird ersetzt, wenn eine spätere Konfiguration einen numerischen Schlüssel verwendet

Um die Integrität der Architekturdaten zu schützen und die modulare Erweiterbarkeit zu verbessern, wurde ein Hauptfehler innerhalb der XML-Parsing-Engine von Dependency Injection (DI) behoben, bei dem Array-Konfigurationen mit dem numerischen Schlüssel „0“ während der Modulkompilierung stumm überschrieben oder gelöscht wurden.

_AC-8102 - [GitHub-Problem](https://github.com/magento/magento2/issues/36861) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### addProductsToCart gibt Fehler für custom_attributesV2 aus, wenn der Attributcode Modell ist

Es wurde ein Problem behoben, bei dem addProductsToCart einen internen Server-Fehler zurückgab, wenn ein Produkt ein benutzerdefiniertes Attribut mit dem Code-Modell hatte. Das benutzerdefinierte Attribut kann jetzt korrekt über custom_attributesV2 abgerufen werden.

_AC-16987 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/809ba93c)_

#### GQL Menge Null, wenn stock_status in_STOCK ist

Das Mengenfeld in der GraphQL-Produktabfrage hat fälschlicherweise null für Produkte zurückgegeben, die in einem benutzerdefinierten MSI-Lager vorrätig waren. Der Resolver hat die Antwort für den Konfigurationswert catalogInventory/options/not_available_message abgerufen, bevor die tatsächliche Lagermenge abgerufen wurde, und der XML-Standard dieser Konfiguration (2 — „Nicht genügend Artikel zum Verkauf„) hat dazu geführt, dass in jedem neuen Speicher null zurückgegeben wurde, ohne dass eine explizite Admin-Überschreibung erforderlich war.
Der Scheck wird nun ausgewertet, nachdem die verkaufsfähige Menge geklärt ist. null wird nur zurückgegeben, wenn das Produkt keinen verfügbaren Lagerbestand hat (saleableQty &lt;= 0) und der Store explizit mit „Nicht genügend Artikel zum Verkauf“ konfiguriert ist. Produkte, die auf Lager sind, geben immer ihre tatsächliche verkaufsfähige Menge zurück, unabhängig von dieser Konfigurationseinstellung. Die gelesene Konfiguration wird auch dahingehend korrigiert, dass sie den Speicherbereich verwendet, sodass Überschreibungen auf Speicherebene berücksichtigt werden.

_ACP2E-4840 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price ignoriert Preise im Website-Bereich, wenn Katalogpreis = Website

Preise für Bundles mit Website-Umfang in GraphQL: Es wurde ein Problem behoben, bei dem die Abfrage von Bundle-Produktoptionen über GraphQL globale Preise für „Alle Store-Ansichten“ anstelle von Preisen für die Website zurückgab, wenn der Katalogpreisbereich auf „Website“ festgelegt war. Der Magento\BundleGraphQl\Model\Resolver\Links\Collection-Resolver überprüft nun den Preisbereich ordnungsgemäß und fügt websitespezifische Auswahlpreise basierend auf dem angeforderten Speicherbereich hinzu.

_ACP2E-5057 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

#### Doppelter aktiver Warenkorb für Kunden aufgrund gleichzeitiger CustomerCart GraphQL-Anfragen-Racebedingungen erstellt

Das System stellt jetzt sicher, dass unabhängig von der gleichzeitigen Anfrage nur ein aktiver Warenkorb pro Kunde erstellt wird. Zuvor konnten zwei gleichzeitige GraphQL-Abfragen von CustomerCart oder POST /V1/carts/mine-REST-Anfragen für denselben authentifizierten Kunden ohne aktiven Warenkorb zu doppelten aktiven Warenkorbdatensätzen in der Datenbank führen.

_ACP2E-5077 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud] Handled GraphQlNoSuchEntityException von QuoteGraphQL in Exception.log protokolliert, was zu unbegrenztem Protokollwachstum führt

Es wurde ein Problem behoben, bei dem erwartete GraphQlNoSuchEntityException-Fehler, wie jene, die für eine abgelaufene oder ungültige Warenkorb-ID zurückgegeben wurden, in var/log/exception.log geschrieben wurden. Diese behandelten Fehler werden weiterhin als normale GraphQL-Fehlerantworten an den Client zurückgegeben, aber sie füllen nicht mehr das Ausnahmeprotokoll aus.

_ACP2E-5122 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL, Inventar/MSI

#### GraphQL: Die als Website-ID übergebene Store-ID in ProductStock::isProductAvailable verursacht den Fehler „Website … wurde nicht gefunden“

Zuvor trat bei einigen Storefronts beim Überprüfen der Verfügbarkeit des Produktbestands beim Hinzufügen von Artikeln zum Warenkorb der Fehler „Website nicht gefunden“ auf, da die Store-ID dort verwendet wurde, wo eine Website-ID erforderlich war. Dies wurde behoben, sodass bei Verfügbarkeitsprüfungen der richtige Website-Kontext verwendet wird, um den Fehler zu vermeiden.

_ACP2E-5242 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL, Bestellung

#### [Funktionsanfrage] Löschen Sie redundante Daten für die Ladenabholung beim Wechsel des Versandunternehmens

Beim Wechsel von der Abholung im Geschäft zur Versandmethode „Zuhause“ werden der Abholort und die zugehörige Store-Adresse aus dem Warenkorb entfernt. Eine gültige Lieferadresse muss angegeben werden, bevor die Bestellung aufgegeben werden kann.

_ACP2E-4973 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL, Produkt

#### Fehlender Schlüssel \„model\&quot; in den Daten der Wunschliste

Es wurde ein Problem behoben, bei dem die Abfrage von Wunschlistendetails über GraphQL einen internen Server-Fehler zurückgab.
Die Wunschlistenabfrage wird jetzt erfolgreich ohne den Fehler „Fehlendes Schlüsselmodell in Wunschlistenwert-Daten“ zurückgegeben.

_AC-8062 - [GitHub-Problem](https://github.com/magento/magento2/issues/36909) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/515d3dd3)_

### Import und Export

#### [Problem] Import-iFrame-Sichtbarkeit korrigieren

Um eine saubere und optimierte Benutzeroberfläche innerhalb des Magento Admin-Bedienfelds zu gewährleisten, wurde ein Fehler im Vorlagen-Layout behoben, bei dem während der Datenvalidierung ein interner Hintergrund-Ausführungs-IFrame für Speicher-Manager sichtbar wurde

_AC-13250 - [GitHub-Problem](https://github.com/magento/magento2/issues/39267) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/39265)_

#### [Problem] Behebung: Hartcode xxh128-Hash-Algorithmus beim Produktimport

Um interne Subsysteme zu bereinigen und moderne Systemoptimierungs-Baselines zu nutzen, wurde die Produktimport-Komponente so optimiert, dass sie einen einzigen permanenten Hash-Algorithmus verwendet.

_AC-16967 - [GitHub-Problem](https://github.com/magento/magento2/issues/40770) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40687)_

#### Die Importschaltfläche bleibt nach Validierungsfehlern verfügbar, wenn die Validierungsstrategie auf „Bei Fehler anhalten“ festgelegt ist.

Es wurde ein Problem behoben, bei dem die Schaltfläche Importieren nach einer fehlgeschlagenen Datenvalidierung, wenn die Validierungsstrategie auf „Bei Fehler stoppen“ eingestellt war, noch immer in den Validierungsergebnissen angezeigt wurde. Zuvor wurde die Schaltfläche angezeigt und konnte angeklickt werden, obwohl alle Datensätze bei der Validierung fehlgeschlagen waren, sodass der Importversuch sofort abgebrochen wurde.

_ACP2E-5124 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2b9e8316)_

### Installieren und Verwalten

#### [Cloud] Korrektur veralteter bestehender ISO-Unterteilungscodes

Die Regionscodes für 13 Länder wurden aktualisiert, damit sie der ISO-Norm 3166-2 entsprechen. Zuvor entsprachen einige Regionalcodes nicht dem Standard, was zu Problemen mit Drittanbieterintegrationen und der internationalen Compliance führen konnte. Für Belgien, Kolumbien, Spanien, Frankreich, Italien und Lettland wurden neue Regionen hinzugefügt. Regionscodes wurden für Deutschland, Estland, Finnland, Frankreich, Indien, Estland, Kolumbien, Lettland, Kolumbien und Costa Rica aktualisiert.

_ACP2E-4495 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Inventar/MSI

#### [CLOUD] Geschenkkarte und verwandte nicht verkaufbare WF-1688

Das Produkt verschwindet nicht, wenn ein nicht standardmäßiger Bestand/eine nicht standardmäßige Quelle verwendet wird und das zugehörige Produkt (verwandtes Produkt oder Upsell- oder Crosssell-Produkt) gespeichert wird.

_ACP2E-4741 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Inkonsistenz des Produktbestandsstatus eines Pakets

Zuvor wurde, wenn ein Store-Administrator bzw. eine Store-Administratorin den Lagerstatus eines Produktpakets im Admin-Bedienfeld manuell aktualisiert hat, die Änderung bei Stores, die mit mehreren Inventarquellen konfiguriert sind, nicht in der Storefront übernommen. Kunden würden trotz der Änderungen durch den Administrator weiterhin einen veralteten Lagerstatus sehen.

Dieses Problem wurde behoben. Änderungen des Produktlagerstatus von Paketen, die im Admin-Bedienfeld vorgenommen wurden, werden jetzt korrekt auf alle konfigurierten Lagerquellen und Lagerplätze übertragen, sodass Kundinnen und Kunden immer die genaue Verfügbarkeit der Lagerbestände in der Storefront sehen.

_ACP2E-4866 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/db712a46)_

#### NoSuchEntityException „Store that was requested was not found“ geworfen von GetStockIdForCurrentWebsite.php

Es wurde ein Problem behoben, bei dem beim Besuch einer Storefront-Seite mit einem ungültigen Abfrageparameter ?store= bei jeder solchen Anfrage eine NoSuchEntityException auf KRITISCHER Ebene protokolliert wurde. Zuvor übergab das MSI Stock Data Plug-in den Roh-Speicher-Code direkt an StoreManager::getStore(), ohne den Fall zu behandeln, dass der Speicher nicht vorhanden war, was zu einer Ausnahme-Log-Unordnung führte.

_ACP2E-5003 - [GitHub-Code-Beitrag](https://github.com/magento/inventory/commit/1bf25e46)_

### Reihenfolge

#### Cancel Order Observer nicht ausgeführt, wenn der Bereich der Frontend- oder webapi_rest-Bereich ist

Fehlerkorrektur - Beim Abbrechen einer Bestellung über die Storefront oder den Bereich „webapi_rest“ wird der Abbruchsbeobachter jetzt korrekt ausgeführt. Die Beträge der Geschenkkarte werden jetzt bei Stornierung der Bestellung auf die Gutschrift des Kundengeschäfts zurückgebucht.

_AC-16353 - [GitHub-Problem](https://github.com/magento/magento2/issues/40414) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/64eb754d)_

#### Warenkorb-Preisregel mit begrenzter Nutzung wird beim Bearbeiten einer vorhandenen Bestellung in Admin nicht angewendet (z. B. „Verwendungen pro Kunde = 1„)

Es wurde ein Problem behoben, bei dem Rabatte für Warenkorbpreisregeln mit Nutzungsbeschränkungen entfernt wurden, wenn eine vorhandene Bestellung in Admin bearbeitet wurde. Der ursprüngliche Rabatt wird jetzt bei der Bearbeitung der Bestellung beibehalten, auch wenn die Nutzungsbeschränkung erreicht wurde.

_AC-16671 - [GitHub-Problem](https://github.com/magento/magento2/issues/40624) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c10554e1)_

#### Fehler bei der Mindestmenge im Admin-Bedienfeld für Bundle-Produkte

Um die Backend-Bestellabwicklung zu verbessern und Funktionsblöcke beim Generieren manueller Anführungszeichen zu entfernen, wurde ein Validierungsfehler behoben, bei dem untergeordnete Artikelparameter bei der Admin-Auftragserstellung falsch ausgewertet wurden.

_AC-17193 - [GitHub-Problem](https://github.com/magento/magento2/issues/40812) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40863)_

#### Inkonsistente Menge untergeordneter Elemente von Bundle-Produkten in Frontend-Bestellansicht

Auf der Seite mit den Bestelldetails für die Storefront wird jetzt die gesamte bestellte Menge für jede Bundle-Produktoption angezeigt. Zuvor wurde in der Spalte „Menge“ für jede untergeordnete Option die geordnete Menge des übergeordneten Bundles anstelle der insgesamt pro Option bestellten Menge angezeigt.

_ACP2E-4820 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex::execute() fehlende DeadlockException-Wiederholung verursacht permanenten ShipOrder-/InvoiceOrder-Fehler

Vorgänge von ShipOrder und InvoiceOrder werden jetzt im Falle eines Deadlocks erfolgreich aufgelöst.
Zuvor schlagen ShipOrder- und InvoiceOrder-Vorgänge aufgrund von Deadlock dauerhaft fehl

_ACP2E-4913 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/51f6d191)_

#### Falsche Berechnung auf Zeilenebene von FPT/WEEE für übergeordnete konfigurierbare Artikel bei der Rechnungserstellung

Die Gesamtsummen der Rechnungen und Gutschriften für konfigurierbare Produkte enthalten nun korrekt den Festbetrag der Produktsteuer. Zuvor wurden die Beträge auf Zeilenebene der VZÄ nicht auf den übergeordneten konfigurierbaren Auftragsposten übertragen, sodass die Summe der Rechnungen und Gutschriften niedriger als die Summe der Aufträge um den VZÄ-Betrag war.

_ACP2E-4977 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/51f6d191)_

#### Produktmengen wurden bei der Seitenaktualisierung beim Erstellen einer Bestellung vom Administrator geändert

Es wurde ein Problem behoben, bei dem beim Aktualisieren der Seite dieselbe SKU mehrmals hinzugefügt werden konnte.

_ACP2E-5046 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec436b10)_

#### Gleichzeitige asynchrone E-Mail-Cron-Worker senden doppelte E-Mails zur Bestellbestätigung für dieselbe Bestellung

Es wurde ein Problem behoben, bei dem gleichzeitige E-Mail-Sekundäre doppelte E-Mails zur Bestellbestätigung für dieselbe Bestellung senden konnten.

_ACP2E-5059 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8d70f246)_

#### [CLOUD] sales_clean_quotes Cron-Auftrag hat keinen Speicher mehr

Es wurde ein Problem behoben, bei dem dem Cron-Auftrag sales_clean_quotes beim Bereinigen einer großen Anzahl abgelaufener Anführungszeichen der Speicher ausging. Zuvor behielt der Auftrag jedes verarbeitete Anführungszeichen im Speicher und endete mit einem schwerwiegenden Fehler bei der Speichererschöpfung, bevor alle abgelaufenen Anführungszeichen entfernt wurden.

_ACP2E-5137 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/4d0357d7)_

### Bestellung, Promotion

#### Preisregel für Warenkorb mit festgelegtem Betrag Rabatte für nicht übereinstimmende untergeordnete dynamische Bundles, wenn die Regel mit dem übergeordneten Bundle übereinstimmt

Es wurde ein Problem behoben, bei dem eine Preisregel mit festem Betrag für den Warenkorb mit einer Kategoriebedingung fälschlicherweise einen Rabatt auf alle untergeordneten Elemente eines dynamischen Preis-Bundles anwandte, wenn die Regel nur mit dem übergeordneten Bundle übereinstimmte. Zuvor erhielten Bundle-Kinder, die nicht zur Zielkategorie gehörten, einen proportionalen Anteil des Rabatts anstelle von null.

_ACP2E-5075 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/2b9e8316)_

### Zahlungen

#### Der Befehl :show funktioniert nicht mit partiellen Pfaden in neueren Versionen

Der `config:show`-Befehl akzeptiert jetzt partielle Konfigurationspfade, z. B. eine Zahlung, und zeigt die Konfigurationswerte unter diesem Pfad an. Zuvor wurde bei `php bin/magento config:show` Ausführung der Zahlung der Fehler `The "payment" path doesn't exist. Verify and try again.` statt der Anzeige der richtigen Werte zurückgegeben.

_AC-13908 - [GitHub-Problem](https://github.com/magento/magento2/issues/39610) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40432)_

### Leistung

#### Setup:upgrade ändert den Indexermodus in `save` von `schedule` und verlangsamt ihn enorm

Es wurde ein langjähriges Problem behoben, bei dem die Ausführung des bin/magento-Setups :upgrade Indexermodi versehentlich von „Planmäßig speichern“ in „Beim Speichern speichern“ änderte und unnötigerweise Datenbank-Trigger ignorierte und neu erstellte, wodurch Ausfallzeiten drastisch reduziert wurden und Leistungsengpässe bei Bereitstellungen in großen Katalogen vermieden wurden.

_AC-2423 - [GitHub-Problem](https://github.com/magento/magento2/issues/33386) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40643)_

#### Valley LAYOUT-Cache-Schlüssel verbrauchen viel Platz für einen großen Produktkatalog

Zuvor generierte jedes Produkt seinen eigenen LAYOUT-Cache-Eintrag pro Shop-Ansicht, was zu übermäßigem Speicherverbrauch in Redis/Valley bei großen Katalogen führte. Jetzt werden LAYOUT-Cache-Einträge über Produkte mit demselben Typ, demselben Attributsatz und derselben Speicheransicht hinweg gemeinsam genutzt, wodurch das Cache-Wachstum unabhängig von der Kataloggröße begrenzt wird.

_ACP2E-4908 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### Deadlock-Fehler bei der Produktabfrage

Es wurde ein InnoDB-Deadlock auf Seiten mit einer CatalogWidget-Produktliste behoben, die nach Kategorie gefiltert wurde und beim gleichzeitigen Ausführen des Zeitplanmodus-Preisindizierers auftrat.

_ACP2E-5052 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] Adobe Commerce URL-Auflösung Verschlechterung der Abfrageleistung

Es wurde ein Problem behoben, bei dem die GraphQL-Routenabfrage immer den vollständigen Seiteninhalt von CMS wiedergab - einschließlich der Ausführung des Page Builder-Widgets und des Ladens der Produktsammlung -, selbst wenn nur URL-Routing-Metadaten (relative_url, redirect_code, type) angefordert wurden. Zuvor führte dies zu unnötigem Widget-/Produkt-Rendering und zu einem erheblichen Anstieg der Datenbankabfragen pro Anfrage für CMS-Seiten, die Page Builder-Widgets enthielten.

_ACP2E-5143 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/597c7211)_

#### Admin Customer Edit Performance Tanks, wenn die Freigabe des Kundenkontos auf „Global“ eingestellt ist

Es wurde ein Leistungsproblem auf der Seite „Kunden bearbeiten“ in Admin behoben, bei dem Ladezeit und HTTP-Antwortgröße quadratisch anstiegen, wenn Kundenkonten freigeben auf „global“ gesetzt war.

_ACP2E-5164 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/24667df1)_

### Produkt

#### Die Schaltfläche Zum Warenkorb hinzufügen im Popup-Fenster „Klick für Preis“ funktioniert nicht.

Es wurde ein Problem behoben, bei dem die Schaltfläche Zum Warenkorb hinzufügen im Popup „Zum Preis klicken“ auf der Produktlistenseite das Produkt nicht zum Warenkorb hinzugefügt hat.
Produkte können jetzt über das Popup erfolgreich zum Warenkorb hinzugefügt werden.

_AC-11896 - [GitHub-Problem](https://github.com/magento/magento2/issues/30356) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/29a7cdbe)_

#### BundleGraphQL-Resolver erstellen separate verzögerte Produktinstanzen, wodurch das Abfrage-Batching (n+1) umgangen wird

Um den Durchsatz der API-Antworten drastisch zu beschleunigen und den Server-Overhead zu minimieren, wurde die GraphQL-Auflösungsschicht optimiert, um echtes Abfrage-Batching für Bundle-Produkte zu erzwingen, wodurch leistungsintensive N+1-Datenbanklecks vermieden werden.

_AC-16647 - [GitHub-Problem](https://github.com/magento/magento2/issues/40595) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40867)_

#### Bei der EAV Select- und Mehrfachauswahl-Attributvalidierung werden Optionsbeschriftungen mit dem Wert „0“ fälschlicherweise zurückgewiesen

Um die Datenintegrität zu verbessern und unerwartete Übermittlungsfehler in Kunden- und Katalogformularen zu vermeiden, wurde ein Validierungsfehler behoben, bei dem Optionsbeschriftungen, die den genauen Zeichenfolgenwert „0“ enthalten, vom EAV-Core-Framework fälschlicherweise abgelehnt wurden

_AC-16986 - [GitHub-Problem](https://github.com/magento/magento2/issues/40634) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40827)_

#### Anpassbare Optionsbeschriftungen und Optionstitel können nicht gespeichert werden, wenn die Rolle eines Benutzers auf einen bestimmten Bereich beschränkt ist.

Es wurde ein Problem behoben, bei dem anpassbare Optionsbeschriftungen und -titel zurückgesetzt wurden, wenn sie von einem Admin-Benutzer bearbeitet wurden, dessen Zugriff auf einen bestimmten Speicherbereich beschränkt war.
Die aktualisierten Beschriftungen und Titel werden nun für den ausgewählten Bereich korrekt gespeichert.

_AC-2684 - [GitHub-Problem](https://github.com/magento/magento2/issues/35210)_

#### Product Alert Consumer ignoriert System/Stmp/Disable im Store

Der Produktwarnhinweis-Verbraucher berücksichtigt jetzt die Einstellung für „System/Stmp/Disable“ im Store.

_ACP2E-4870 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/ec436b10)_

#### Frontend-Vergleichsseite mit falscher Kurzbeschreibungsübersetzung

Zuvor konnten auf der Seite Produkte vergleichen vergleichbare Attributbeschriftungen wie Kurzbeschreibung eine Übersetzung aus einer anderen Shop-Ansicht anstelle der des aktuellen Stores anzeigen. Jetzt werden die richtigen Store-spezifischen Übersetzungen angezeigt.

_ACP2E-4929 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/08b91f1a)_

#### Das Produktkarussell von Page Builder ignoriert die Sortierreihenfolge der Kategorieposition und zeigt stattdessen Produkte in der DESC-Reihenfolge entity_id an

Es wurde ein Problem behoben, bei dem in einem Page Builder-Karussell angezeigte Produkte, die nach Kategorieposition sortiert werden sollen, in der falschen Reihenfolge in der Storefront angezeigt wurden. Produkte werden jetzt in der Reihenfolge angezeigt, die in der Admin → Catalog → Categories → der Registerkarte Produkte konfiguriert ist.

_ACP2E-4980 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/51f6d191)_

### Regeln für die Promotion

#### Falsche Rabattberechnung, wenn eine der angewendeten Warenkorbpreisregeln den Wert „Rabattmenge - Schritt“ hat

Es wurde ein Problem behoben, bei dem der Rabatt falsch berechnet wurde, wenn mehrere Regeln für den Warenkorbpreis angewendet wurden und eine Regel einen Wert für „Rabattmengenschritt (Kauf X)“ hatte.
Die Rabatte werden nun für alle in Frage kommenden Mengen korrekt berechnet.

_AC-12307 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c10554e1)_

### Rückgabe

#### RMA - Add Return Comments API - E-Mails werden an den Absender (Vertriebsmitarbeiter), aber nicht an den Kunden ausgelöst

Es wurde ein Problem behoben, bei dem E-Mails zu Rücksendekommentaren, die über die Rückgabe-API gesendet wurden, an den Vertriebsmitarbeiter, aber nicht an den Kunden gesendet wurden.
Kunden erhalten jetzt eine E-Mail-Benachrichtigung, wenn über die API ein Rückkehrkommentar mit aktivierter Kundenbenachrichtigung hinzugefügt wird.

_AC-1138 - [GitHub-Problem](https://github.com/magento/magento2/issues/33985)_

### Verkauf

#### `[Order][REST]` Spalte sales_order_items product_options fehlen Daten, wenn eine Bestellung über die REST-API V1/orders oder V1/orders/create-Endpunkte aufgegeben wurde

Es wurde ein Problem behoben, bei dem über die REST-API erstellte Bestellelemente keine vollständigen product_options-Daten enthielten. Benutzerdefinierte Optionsbeschriftungen und relevante Optionsdetails werden jetzt für Bestellungen, die über die REST-API erstellt wurden, korrekt gespeichert.

_AC-15187 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8b67e8ed)_

#### Das Kundenauftragsraster bleibt dauerhaft im veralteten Status stecken, wenn die asynchrone Rasterindizierung aufgrund eines verknüpften Zeitstempels „updated_at“ aktiviert wurde

Es wurde ein Problem behoben, bei dem das Kundenauftragsraster mit einem veralteten Auftragsstatus feststecken konnte, wenn die asynchrone Rasterindizierung aktiviert war. Der Bestellrasterstatus wird jetzt korrekt aktualisiert, sodass er dem aktuellen Bestellstatus entspricht, einschließlich der Fälle, in denen mehrere Bestellaktualisierungen innerhalb derselben Sekunde erfolgen.

_AC-17118 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/478f8e7c)_

### Sicherheit

#### [Problem] Aktualisieren von js.phtml-DOM-Text, der als HTML neu interpretiert wird

Um die Sicherheitsgrundlinie der Plattform zu stärken und das Risiko der böswilligen Eingabeausführung zu minimieren, wurde die primäre Inline-Skriptvorlage, die dynamische DOM-Aktualisierungen verarbeitet, überarbeitet, um Cross-Site-Scripting (XSS)-Injections-Vektoren zu eliminieren.

_AC-12118 - [GitHub-Problem](https://github.com/magento/magento2/issues/38821) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/38804)_

### Lieferung

#### Problem mit der USPS-REST-API, falsche Raten für die maximale Paketgewichtung

Fehlerhafte Versandschätzungen wurden behoben, wenn eine Bestellung in mehrere Pakete aufgeteilt wurde (z. B. über „Maximales Paketgewicht„). Der Provider fordert nun für jedes Paket eine Rate an und addiert die Summen, entsprechend dem Fluss der alten Web-Tools.

_ACP2E-4813 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/6c67a9b5)_

### Steuer

#### base_wee_tax_applied_amount ist für übergeordnetes Produkt nicht festgelegt

Der Wert base_weee_tax_applied_amount wird jetzt für das konfigurierbare Produkt in Datenbanktabellen wie sales_order_item, sales_bill_item, sales_creditmemo_item ausgefüllt, nicht nur für das untergeordnete Element

_ACP2E-4922 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/08b91f1a)_

### Test-Framework

#### [Problem] Update GraphQL testet Client.php auf den Vergleich von Teilzeichenfolgen ohne Unterscheidung der Groß-/Kleinschreibung

Es wurde ein Problem behoben, bei dem GraphQL-API-Tests Set-Cookie-Kopfzeilen nicht erkannten, wenn die Kopfzeile eine andere Groß-/Kleinschreibung verwendete. Die Tests verarbeiten jetzt die Kopfzeilen Set-Cookie, Set-Cookie und SET-COOKIE korrekt.

_AC-15337 - [GitHub-Problem](https://github.com/magento/magento2/issues/39713) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/c10554e1)_

#### Extrem langsame WebAPI GraphQL-Funktionstests

Um Bereitstellungseinstellungen zu optimieren und CI-Umgebungen (Continuous Integration) zu beschleunigen, wurde ein Engpass in der Testinfrastruktur behoben, indem das Cache-Löschverhalten von externen Systembefehlen auf die native Speicherverarbeitung im Prozess umgestellt wurde.

_AC-15395 - [GitHub-Problem](https://github.com/magento/magento2/issues/39725) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40804)_

### UI-Framework

#### Minicart kann nicht zweimal auf derselben Seite verwendet werden

Um Frontend-Entwicklern eine größere Layout-Flexibilität zu bieten, wurde eine langjährige Einschränkung der Kern-Benutzeroberfläche aufgelöst, sodass mehrere Minicart-Blöcke (z. B. einer in der Kopfzeile und ein anderer in der Fußzeile) unabhängig voneinander in einem Einzelseiten-Layout vorhanden und aktualisiert werden können.

_AC-12579 - [GitHub-Problem](https://github.com/magento/magento2/issues/38958) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [Problem] beheben (pagecache): PATCH in der VCL von Varnish als gültige HTTP-Methode erkennen

Die standardmäßige Varnish-VCL von Magento erkennt PATCH jetzt als gültige HTTP-Methode an, sodass partielle REST-API-Aktualisierungsanfragen (z. B. PATCH /rest/V1/products/:sku) an das Backend übergeben werden, anstatt weitergeleitet zu werden. Dadurch wird behoben, dass PATCH-Aufrufe fehlschlagen oder sich falsch verhalten, wenn der vollständige Seitencache auf Varnish festgelegt ist.

_AC-16954 - [GitHub-Problem](https://github.com/magento/magento2/issues/40757) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40657)_

#### [Problem] Alle gad_*-Parameter in VCL ersetzen

Um Leistungsregressionen zu vermeiden, die durch dynamische Anzeigenkampagnen verursacht werden, wurden die Caching-Ebenen des Programms aktualisiert, sodass proaktiv alle Google Ads gad_*-Abfragezeichenfolgen ignoriert werden. Dadurch wird verhindert, dass externe Kampagnen-Links die Seiten-Caches ungültig machen und Zielseiten verlangsamen

_AC-16980 - [GitHub-Problem](https://github.com/magento/magento2/issues/40781) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40780)_

#### [Problem] Behebung: Aktualisieren der minimalen PHP-Versionsüberprüfung im Bootstrap auf 8.3

Um verwirrende Laufzeitfehler zu vermeiden und die Fehlerbehebung bei der Entwicklerinstallation zu verbessern, wurde der native PHP Environment Validator innerhalb des Bootstrap-Frameworks des Systems an die aktuellen Kernanforderungen des Programms angepasst.

_AC-17312 - [GitHub-Problem](https://github.com/magento/magento2/issues/40851) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40686)_

#### `health_check.php` gibt 500 zurück, wenn `igbinary` installiert ist und der standardmäßige Datei-Cache verwendet wird (Varnish 503)

Es wurde ein Problem behoben, bei dem health_check.php HTTP 500 zurückgab, wenn igbinary mit dem standardmäßigen Dateicache-Backend installiert wurde. Die Konsistenzprüfung akzeptiert jetzt gültige Cache-Konfigurationen ohne expliziten Backend-Schlüssel, sodass Varnish das Backend nicht als fehlerhaft markieren und HTTP 503 zurückgeben kann.

_AC-17400 - [GitHub-Problem](https://github.com/magento/magento2/issues/40876) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [Problem] Behebung: Aktualisieren Sie gzip-Typen und entfernen Sie IE6-Workaround in der nginx-Konfiguration

Um die Seitenladegeschwindigkeit zu verbessern und die Bereitstellung von Netzwerk-Assets zu optimieren, wurde die Fallback-Server-Konfiguration modernisiert, um moderne Storefront-Komponenten besser zu unterstützen und Legacy-Technologie-Overhead zu entfernen

_AC-17498 - [GitHub-Problem](https://github.com/magento/magento2/issues/40774) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40681)_

#### [Problem] Versuchen Sie, fehlerhafte GraphQL-OrderStatusChangeDateTest zu beheben.

Um die Zuverlässigkeit der kontinuierlichen Integration (CI) zu verbessern und falsch-positive Build-Fehler zu reduzieren, wurde eine Race-Bedingung in der WebAPI Functional Test Suite behoben. Beim GraphQL-Validierungstest für den Bestellstatus (OrderStatusChangeDateTest) traten aufgrund subtiler Zeitabweichungen zwischen PHP-Speicher und MySQL-Zeitstempeln zuvor zeitweise Fehler auf

_AC-17959 - [GitHub-Problem](https://github.com/magento/magento2/issues/41126) - [GitHub-Code-Beitrag](https://github.com/magento/magento2/pull/40618)_
