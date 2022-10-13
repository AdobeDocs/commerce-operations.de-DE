---
title: Versionshinweise
description: Erfahren Sie mehr über die für Adobe Commerce verfügbaren Patches und die von ihnen gelösten Probleme.
source-git-commit: bb1cb17b75a799409336068967c9d0facefeaf41
workflow-type: tm+mt
source-wordcount: '9467'
ht-degree: 0%

---

# Versionshinweise

Die [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) bietet individuelle Patches, die von Adobe und der Magento Open Source Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce oder Magento Open Source verfügbar sind, anwenden, wiederherstellen und anzeigen. Sie können Patches auf Adobe Commerce- und Magento Open Source-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.

>[!INFO]
>
>Siehe [Anwenden von Patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) für Anweisungen zum Anwenden von Patches auf Ihre Adobe Commerce- oder Magento Open Source-Projekte. Siehe [Verfügbare Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch für Softwareaktualisierungen , um eine vollständige Liste der veröffentlichten Patches zu lesen.

>[!INFO]
>
>Informationen zu [!DNL quality patches] , die von der Gemeinschaft zur Magento Open Source erstellt wurden, siehe [Versionshinweise](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem ein Benutzer beim Zuweisen einer großen Anzahl von Produktquellen einen Fehler erhält.
* **ACSD-46856** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Verbessert die Leistungs-Aktualisierungsstufen-Preise über System > Konfiguration > Import > Erweiterte Preise.
* **ACSD-46541** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem ein Admin-Benutzer kein Kreditmemo erstellen kann, wenn ein Bestellelement gelöscht wird.
* **ACSD-46581** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem die geschätzte Steuersumme nach Auswahl eines Landes im Warenkorb nicht aktualisiert wird.
* **ACSD-46618** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem das Produktlisten-Widget falsche, zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt.
* **ACSD-46674** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem benutzerdefinierte Optionen eines Bildtyps in E-Mails von Kunden als HTML angezeigt werden.
* **ACSD-46988** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem die GraphQL-API-Anfrage &quot;currency&quot;NULL-Werte für eine benutzerdefinierte Währung zurückgibt.
* **ACSD-47076** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5) - Behebung des Problems, bei dem Vimeo-Videos nicht auf der Storefront wiedergegeben werden können.
* **ACSD-45071** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4) - Behebung des Problems, bei dem die Standardquelle beim Import zum Produkt hinzugefügt wird.
* **AC-3023** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Aktualisierung des DHL-Schemas auf die neueste Version 10.0.
* Aktualisierte Patches: MDVA-42584.
* Ersetzte Patches: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem ein Benutzer einen falschen Bestellstatus erhält, wenn er mit dem Store-Guthaben zurückerstattet wird.
* **ACSD-46703** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6*) - Behebung des Problems, bei dem es nicht möglich ist, benutzerdefinierte Optionen per Drag-and-Drop auf eine Produktbearbeitungsseite zu ziehen.
* **ACSD-44851** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6*) - Behebung des Problems, bei dem eine Kategorie mit Unterkategorien nicht geöffnet oder erweitert werden kann.
* **ACSD-46815** (*für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6*) - Behebung des Problems, bei dem die Kategoriebaumanfrage auf 20 Kategorien beschränkt ist.
* **ACSD-45675** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6*) - Behebung des Problems, bei dem der Produktexport Kategorienamen aus der *Standardspeicheransicht* Umfang.
* **ACSD-46869** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6*) - Behebt das Problem, dass ein konfigurierbares Produkt in einem Warenkorb nicht über aktualisiert wird. *PUT REST API* Anforderung ohne Änderung der Produktmenge.
* **MDVA-42768-V2** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem für konfigurierbares Produkt der reguläre Preis angezeigt wurde als *0* when *Nicht auf Lager anzeigen* is *Ja*.
* Aktualisierte Patches: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Veralteter Patch: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem die Kategoriebaumanfrage auf 20 Kategorien beschränkt ist.
* **ACSD-45781** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.2*) - Behebt das Problem, dass das Feld für die Vorderseite des Stores nicht auf einem Mobilgerät angezeigt wird.
* **ACSD-46192** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;2.4.5*) - Behebt das Problem mit der Verwendung des `async/bulk/V1/configurable-products/bySku/options` -Endpunkt.
* **ACSD-46404** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebung des Problems, bei dem sich ein Admin-Benutzer nach einem Upgrade auf 2.4.4 nicht anmelden kann.
* Aktualisierte Patches: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem eine GraphQL-Produktmutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der nicht dem angeforderten Store zugewiesenen.
* **ACSD-46146** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.6*) - Behebung des Problems, bei dem zwei Bestellbestätigungs-E-Mails nach einer Bestellung durch den Administrator gesendet werden.
* **ACSD-45255** (*für Adobe Commerce >=2.4.3 &lt;2.4.6*) - Behebt eine Ausnahme für einen eingeschränkten Administrator auf der Seite &quot;Bericht zu geringem Lagerbestand&quot;.
* **ACSD-45488** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6*) - Behebung des Problems, bei dem ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch an In Stock zurückgegeben wird.
* **ACSD-45754** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.6*) - Behebung des Problems, bei dem nach dem Anwenden eines Gutscheins auf den Warenkorb keine Prämienpunkte hinzugefügt werden.
* **ACSD-45849** (*für Adobe Commerce >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem Videometadaten nach dem Anwenden einer Staging-Aktualisierung verloren gehen.
* **ACSD-45257** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.4*) - Behebung des Problems, bei dem GraphQL keinen korrekten Rabatt auf den Warenkorb anzeigte.
* **ACSD-44938** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebt das Problem, bei dem `VAT_ID` kann nicht in einer GraphQL-Anfrage für einen Gastbenutzer angewendet werden.
* Aktualisierte Patches: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.4*) - Behebung des Problems, bei dem die Lagerbestände für ein virtuelles Produkt nach dem Erstellen eines Kreditmemo falsch berechnet wurden.
* **ACSD-43887** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem falsche Details auf der Zahlungsseite angezeigt werden, wenn &quot;Kaufaufträge für Unternehmen&quot;aktiviert ist.
* **ACSD-45143** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebt das Problem, bei dem der `setShippingAddressesOnCart` Die Mutation ermöglicht nicht, numerischen Regionscode als *region*.
* **ACSD-44591** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.6*) - Behebt den Fehler, der auftritt, wenn eine Bestellung ohne CAPTCHA-Bestätigung platziert wird.
* **ACSD-45520** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.6*) - Behebung des Problems, bei dem Musteroptionen nicht auf der Produktdetailseite vorausgewählt sind, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet.
* **ACSD-45169** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.6*) - Behebt das Problem, bei dem [!DNL Visual Merchandiser] zeigt nach Anwendung eines Staging-Updates nicht den richtigen Lager- und Preis für ein konfigurierbares Produkt an.
* **ACSD-45424** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.6*) - Behebung des Problems, bei dem nach einer teilweisen Rückerstattung eine falsche Reservierungsentschädigung entsteht (Kreditvermerk).
* **MDVA-42807** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.6*) - Behebung des Problems, bei dem das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird.
* Aktualisierte Patches: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem die Bestellsummen im Bestellbericht für den eingeschränkten Admin-Benutzer falsch berechnet wurden.
* **MDVA-44940** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt den SQL-Fehler, der beim Speichern der Kategorie aus dem Admin auftritt.
* **MDVA-44562** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Behebung des Problems, bei dem die nicht standardmäßige Store-ID für Anführungszeichen-Elemente von der standardmäßigen Store-ID überschrieben wird, trotz der GraphQL-Anfrage, die von der nicht standardmäßigen Store-Ansicht stammt.
* **MDVA-43167** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem die Massenaktion des Administrationsnetzwerks nicht für mehrere Seiten gilt, wenn der Admin-Benutzer alle Bestellungen auswählt.
* **MDVA-44044** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Behebung des Problems, bei dem ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde.
* **MDVA-42509** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.4*) - Behebung des Problems, bei dem eine CSV-Datei nicht für eine schnelle Bestellung hochgeladen werden konnte, was zu einem *Cookie kann nicht gesendet werden* Fehler.
* Aktualisierte Patches: MDVA-41061, MDVA-42584.
* Das Präfix für das neue [!DNL Quality Patches Tool] Patches werden geändert von *MDVA* nach *ACSD* aufgrund interner Prozessänderungen.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem ein zusätzliches Element nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist.
* **MDVA-44887** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebt die *Uncaught SyntaxError: Unerwartetes Token &quot;const&quot;* im Admin-Bereich angezeigt.
* **MDVA-43718** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Fehlerbehebungen *Der Verbraucher ist nicht berechtigt, auf %resources zuzugreifen.* Fehler, der beim Zugriff auf einen freigegebenen Katalog von einer benutzerdefinierten Integration angezeigt wird.
* **MDVA-44660** (*für Adobe Commerce und Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Behebt das Problem, bei dem das Zeichen für Gravis ``` ` ``` konnte nicht für den Vor- und Nachnamen eines Kunden verwendet werden.
* **MDVA-40896** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt die *Fehler: TypeError: Argument 3 wird an Magento übergeben* Fehler in der asynchronen Produkt-Bulk-API.
* **MDVA-38559** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt die */V1/Customers/search-API* Fehler bei Kunden mit mehr als einem Abonnement.
* **MDVA-44533** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.4*) - Behebung des Problems, bei dem der Rabatt fälschlicherweise auf ein untergeordnetes Bundle-Produkt angewendet wird.
* Aktualisierte Patches: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, bei dem Produkte *Individuell nicht sichtbar* weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt.
* **MDVA-44100** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem alle FPTs dem letzten Produkt im Warenkorb zugewiesen und für andere Produkte zurückgesetzt wurden.
* **MDVA-43605** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebung des Problems, bei dem Bestelldaten bei Verwendung der Rest-API negative Werte für Zeilensummen zurückgeben.
* **MDVA-43102** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebung des Problems, bei dem die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt.
* **MDVA-43178** (*für Adobe Commerce und Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Behebung des Problems, bei dem ein Kunden-Token für einen benutzerdefinierten Store nicht in GraphQL abgerufen werden kann.
* **MDVA-43859** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, bei dem der Fehler auftrat *Keine solche Entität mit customerId =* wird protokolliert, wenn ein gelöschter Kunde versucht, sich anzumelden.
* **MDVA-44147** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem eine GraphQL-Anfrage keine Anforderungslisten zurückgibt.
* **MDVA-44505** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebt die Probleme, bei denen GraphQL beim Anwenden von Prämienpunkten die Gesamtsumme nicht aktualisiert und bei denen während der Bestellplatzierung mehrmals eine Speichergutschrift angewendet wird.
* Aktualisierte Patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebung des Problems, bei dem die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf *Alle*.
* **MDVA-39605** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebung des Problems, bei dem Redis cache TTL (Ablaufdatum) einen falschen Wert hat.
* **MDVA-43862** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Kunde aufgrund einer GraphQL keine Artikel im Warenkorb aktualisieren kann *UpdateCartItems-Mutation* Fehler.
* **MDVA-43824** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p3 | | >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem beim Abbrechen von Bestellungen mit einem Rabatt ein Fehler angezeigt wird.
* **MDVA-43451** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebt das Problem, bei dem der Fehler auftrat *Der Laden, der angefordert wurde, wurde nicht gefunden. Überprüfen Sie den Speicher und versuchen Sie es erneut.* angezeigt, während Sie einen freigegebenen Katalog für eine bestimmte Website konfigurieren.
* **MDVA-43491** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebung des Problems, bei dem die Beschriftung des Basisbilds beim Importieren von Produkten für eine Website mit mehreren Stores nicht aktualisiert wird.
* **MDVA-43601** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem mit fehlenden Triggern nach vollständiger Neuindizierung.
* **MDVA-42046** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2 | | >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem einem Produktattribut mit einem Datumseingabefeld beim Aktualisieren eines Produkts ein falscher Wert zugewiesen wurde.
* **MDVA-43935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem Upsell-Produkt zweimal angezeigt wird.
* **MDVA-44188** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem vom System ausgegebene E-Mails mit `.-` in -Adressen nicht gesendet werden.
* **MDVA-42283** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Datums-/Uhrzeitformat im Raster der Admin-Reihenfolge für das französische Gebietsschema ungültig ist.
* Aktualisierte Patches: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Hinzugefügte Patchmetadaten für die [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem der Benutzer die Startzeit für eine aktive geplante Aktualisierung bearbeiten kann.
* **MDVA-42410** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem Gutscheinberichte nur die Standardgrundwährung anzeigten.
* **MDVA-41136** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Ablaufdatum der `mage-cache-sessid` nicht erweitert wird, was zu einer Bereinigung der Kundendaten führt.
* **MDVA-39993** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Behebung des Problems, bei dem Bestandsänderungen, die über die API vorgenommen wurden, nicht auf der Produktseite am Frontend übernommen wurden.
* **MDVA-42855** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem eine neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wurde.
* **MDVA-42645** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Administrator keine Bonuspunkte zurückgeben kann, wenn die Funktion zum Speichern von Guthaben deaktiviert ist.
* **MDVA-43414** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Behebt den schwerwiegenden PHP-Fehler, der beim Ausführen der `inventory.reservations.updateSalabilityStatus` Warteschlangen-Consumer für numerische SKUs.
* **MDVA-41628** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem bestehende eingeschränkte Admin-Benutzer beim Hinzufügen neuer Module Zugriff auf die neuen Ressourcen erhalten.
* **MDVA-43348** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, dass die GraphQL-Anfrage der Geschenkkarte einen Fehler anzeigt, wenn `gift_card_options` contain *uid*.
* **MDVA-39546** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Startdatum für die Staging-Aktualisierung während der Bearbeitung auf ein früheres Datum als das aktuelle Datum festgelegt werden konnte.
* **MDVA-42950** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem Videos nicht auf der Produktseite wiedergegeben werden.
* **MDVA-42689** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, bei dem Adobe Commerce eine *Verletzung von Integrationsbeschränkungen* beim Aktualisieren der Produktkategorien während des Imports.
* **MDVA-41229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem im Backend verfügbare Bilder nach einem konfigurierbaren Produktimport nicht im Frontend angezeigt werden.
* **MDVA-43731** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt das Problem, bei dem *Synonyme suchen* funktioniert nicht mehr, wenn ein Wert in *Mindestens passende Begriffe*.
* **MDVA-43232** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebt das Problem, dass Produkte in [!DNL Visual Merchandiser] durch &quot;Special Price To Bottom/Top&quot;verursacht beim Speichern der Kategorie einen Fehler.
* **MDVA-43726** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.3*) - Behebung des Problems, bei dem die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer partiellen Neuindizierung nicht angewendet werden konnte.
* Aktualisierte Patches: MDVA-36464, MDVA-37478, MDVA-38608.
* Hinzugefügte Patchmetadaten für die [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem Produktpreisattribute für eine bestimmte Website nicht über die REST-API aktualisiert werden können.
* **MDVA-41350** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem eine Ausnahme ausgelöst wird, wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt in einer Bestellung außerhalb seines Aufgabenbereichs durch die SKU hinzufügt.
* **MDVA-42269** (*für Adobe Commerce und Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Behebung des Problems, bei dem sich ein Admin-Benutzer aufgrund der *TypeError: strtotime() erwartet, dass Parameter 1 Zeichenfolge ist, null gegeben* Fehler.
* **MDVA-40830** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Store-Guthaben während der Bestellplatzierung mehrmals angewendet wird.
* **MDVA-42237** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem ein konfigurierbarer Produktspezialpreis nach Änderungen am Unterproduktpreis nicht aktualisiert wird.
* **MDVA-42520** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem der Steuersatz zweimal angewendet wird, wenn *Grenzüberschreitenden Handel aktivieren* verwendet.
* Aktualisierte Patches: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Veralteter Patch: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.4.5*) - Behebung des Problems, bei dem durch die Aktualisierung eines Massenattributs nur nach einer Änderung eine URL-Neufassung für den Standardspeicher erstellt wird *Produktsichtbarkeit*.
* **MDVA-43091** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem bei der Bestellung eines Bundle-Produkts vom Admin im Backend der Fehler auftritt *Für dieses Produkt kann keine Dezimalzahl verwendet werden*.
* **MDVA-40816** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem verwandte Produktregeln Produkte aus nicht in den Regelbedingungen definierten Kategorien anzeigen.
* **MDVA-41305** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem die GraphQL-Mutation nach dem Hinzufügen zur Wunschliste keine konfigurierbaren Produktoptionen zurückgibt.
* **MDVA-39181** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem verwandte Produktregeln Produkte aus nicht in den Regelbedingungen definierten Kategorien anzeigen.
* **MDVA-42584** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem der konfigurierbare Lagerstatus im Backend nicht aktualisiert wird, nachdem Menge und Lagerstatus über Import oder API geändert wurden.
* **MDVA-40175** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt das Problem, bei dem *Klicken Sie auf , um die Versandmethode zu ändern.* zeigt keine Optionsfelder an, mit denen Versandmethoden im Admin während der Neuanordnung ausgewählt werden können.
* **MDVA-42768** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebung des Problems, bei dem für konfigurierbares Produkt der reguläre Preis 0 angezeigt wurde, wenn *Nicht auf Lager anzeigen* ist Ja.
* **MDVA-43201** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem bei der Kundenanmeldung bei der Verwendung des DOB-Attributs mit bestimmten Gebietsschemata ein Fehler auftritt.
* Aktualisierte Patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem Datumsfilter nicht ordnungsgemäß funktionierten, wenn sich die Adobe Commerce-Zeitzone von der lokalen Zeitzone der Umgebung unterscheidet.
* **MDVA-42657** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem der Admin-Benutzer nicht in der Lage ist, Kategorien in den Kundensegmentbedingungen auszuwählen.
* **MDVA-42806** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, bei dem ein *Registrierung neuer Unternehmen* E-Mail wird jedes Mal gesendet, wenn ein bestehendes Unternehmen über die REST-API aktualisiert wird.
* **MDVA-37984** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, bei dem der [!DNL Visual Merchandiser] *Produkt nach Regel abgleichen* -Funktion Produkte nicht korrekt mit Staging-Updates filtert.
* **MDVA-40488** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden.
* **MDVA-42507** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem der vollständige Seiten-Cache nach dem Anwenden eines Staging-Updates für die Warenkorbregel bereinigt wird.
* **MDVA-39163** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebung des Problems, bei dem Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert wird und Produkte im Warenkorb aus der Gastsitzung stammen.
* **MDVA-38626** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Administrator mithilfe der [!DNL PayPal Payflow Pro] Zahlung.
* **MDVA-38666** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.3.6*) - Behebung des Problems, bei dem der Administrator die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern kann.
* **MDVA-38526** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem der Admin-Benutzer nicht auf die [!DNL Site-Wide Analysis tool].
* Aktualisierte Patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Benutzer den 500-Fehler erhalten, nachdem die *image-messages* -Cookie, wenn es bereits vorhanden ist, aber keine neuen Nachrichten vorhanden sind.
* **MDVA-41139** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem konfigurierbare Produkte nach dem Produktimport aus &quot;Nicht auf Lager&quot;werden, wenn die Menge eines einfachen Produkts = 0 für eine seiner Quellen beträgt.
* **MDVA-42326** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem Kunden nach einem Sitzungs-Timeout beim Checkout einen Fehler erhalten, selbst wenn der beständige Warenkorb aktiviert ist.
* **MDVA-42341** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, bei dem der `categoryList` Die GraphQL-Abfrage filtert keine Ergebnisse, wenn eine Anforderung über die Store-Kopfzeile verfügt.
* **MDVA-38393** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wurde.
* **MDVA-39153** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem ein Rabattbetrag bei der Neubestellung in der Admin-Konsole falsch berechnet wurde.
* Aktualisierte Patches: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Admin-Benutzer nach dem Löschen der Website nicht auf das Raster des Kunden zugreifen können.
* **MDVA-40311** (*für Adobe Commerce und Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Behebung des Problems, bei dem Admin-Benutzer die Fehlermeldung erhalten *Ungültige Sicherheit oder ungültiger Formularschlüssel. Aktualisieren Sie die Seite.* nach der Anmeldung beim Administrator, wenn der benutzerdefinierte Admin-Pfad konfiguriert und der geheime Schlüssel aktiviert ist.
* **MDVA-41631** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem Benutzer beim Versuch, Bestellinformationen ohne optionale *Telefon* Wert durch GraphQL.
* **MDVA-27239** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem Crosssell-Produkte nicht angezeigt werden.
* Aktualisierte Patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.4*) - Behebt das Problem mit fehlenden Produkten auf der Vorderseite während der Neuindizierung.
* **MDVA-40120** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem die GraphQL-Sortierung nach DESC/ASC nicht mit Produkten mit derselben Relevanz oder demselben Preis funktioniert.
* **MDVA-41399** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem Admin-Benutzer nicht auf die *Warenkorb verwalten* Seite, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt.
* **MDVA-40609** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem Daten zu deaktivierten Produkten in der `cataloginventory_stock_status` Indextabelle mit falschen deaktivierten Produktmengen.
* **MDVA-39031** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem das Hinzufügen eines Produkts zum Warenkorb über GraphQL möglich ist, selbst wenn es nicht der Ziel-Website zugewiesen ist.
* **MDVA-41597** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem Benutzer beim Hinzufügen von mehr als einem konfigurierbaren Produkt zum Warenkorb mit GraphQL einen Fehler erhalten.
* **MDVA-27456** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.3.7*) - Behebung des Problems, bei dem Benutzer beim Laden einen Fehler erhalten [!DNL Swagger].
* **MDVA-32776** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versendet wird.
* **MDVA-30862** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.0*) - Behebt das Problem mit dem falschen Bestelldatum auf der gedruckten PDF-Rechnung.
* Die Indexseite für die [!DNL Quality Patch Tool]. Es wurde eine praktische Suche und Filterung für [!DNL quality patches] auf der neuesten Version des Tools.
* Aktualisierte Patches: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem es nicht möglich ist, eine neue zu erstellen oder eine vorhandene geplante Aktualisierung für ein Produkt zu bearbeiten, wenn das Enddatum zuvor entfernt wurde.
* **MDVA-41046** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem einfache Produkte mit benutzerdefinierten Optionen für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind.
* **MDVA-40545** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem nur der erste Knoten für eine Seite abgerufen wurde, selbst wenn mehr als ein Knoten für dieselbe Seite vorhanden war.
* **MDVA-41164** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Behebung des Problems, bei dem ein Admin-Benutzer ein Unternehmen mit einem benutzerdefinierten Kundenattribut vom Typ Datei oder Bild nicht speichern oder bearbeiten kann.
* **MDVA-39229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, durch das nach der Aktualisierung der Staging-Update-Startzeit der Katalogregel der folgende Fehler angezeigt wird: *Cron Job staging_synchronize_entity_period hat einen Fehler: Die aktive Aktualisierung kann nicht gelöscht werden.*
* **MDVA-40619** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Änderungen an der CMS-Seitenhierarchie beim Versuch, eine Inline-Bearbeitung auf einer CMS-Seite durchzuführen, einen 500-Fehler verursachen.
* **MDVA-41061** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem der Lagerstatus beim Speichern eines Produkts über den Administrator auf &quot;Verkaufbar&quot;zurückgesetzt wird.
* **MDVA-31763** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Katalogpreisregeln bis zu einer manuellen Neuindizierung zurückgesetzt (oder nicht angewendet) werden.
* **MDVA-37748** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem eine GraphQL-Abfrage Produkte zurückgibt, die keinem freigegebenen Katalog zugewiesen sind.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können.
* **MDVA-40101** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.4.0*) - Behebung des Problems, bei dem Artikel nach einer erfolgreichen Bestellplatzierung nicht aus dem Mini-Warenkorb entfernt werden, indem [!DNL PayPal Express] Checkout.
* **MDVA-40401** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem sich der Verwendungswert des Gutscheins ändert, selbst wenn die Platzierung einer Bestellung fehlschlägt.
* **MDVA-40537** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Behebung des Problems, bei dem Benutzer beim Erstellen einer Store-Ansicht einen Fehler erhalten, wenn mehrere CMS-Seiten mit demselben URL-Schlüssel vorhanden sind.
* **MDVA-37725** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Behebung des Problems, bei dem von nicht standardmäßigen Websites gesendete asynchrone Bestellungen-E-Mails Logo-URLs von der Standardwebsite enthalten.
* **MDVA-39482** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem ein Produkt nicht mehr vorrätig ist, wenn es mit &quot;0&quot;importiert wurde, wenn Rückbestellungen aktiviert waren.
* **MDVA-40435** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.4*) - Behebt das Problem mit einem falschen Rabatt auf Bundle-Produkte mit dynamischen Preisen, wenn diese über GraphQL angewendet werden.
* **MC-42528** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Behebt das Problem, bei dem der `categoryList` Die GraphQL-Abfrage gibt sowohl zugewiesene als auch nicht zugewiesene Kategorien zurück.
* **MDVA-29400** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem mit duplizierten Bestellungen, die mit [!DNL PayPal Express Checkout].
* **MDVA-26005** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Behebung des Problems, bei dem es nicht möglich ist, eine Kategorie in einer Kategoriestruktur für die Regelbedingungen für den Warenkorbpreis auszuwählen.
* **MDVA-25631** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Verbessert die Leistung beim Bearbeiten und Speichern von Kundensegmenten, die eine große Anzahl von Kunden enthalten.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem GraphQL-Suchabfragen nicht in den beliebten Suchbegriffen in der Admin-Konsole angezeigt werden.
* **MDVA-40601** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem Benutzer beim Versuch, Informationen über die Kategorie zu erhalten, die durch eine geplante Aktualisierung über GraphQL geändert wurde, einen Fehler erhalten.
* **MDVA-37234** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem beim mehrfachen Hinzufügen eines Artikels zum Warenkorb (parallele Anfrage) für dieselbe SKU ein doppeltes Zeilenelement für dieselbe Warenkorb-ID erstellt wurde.
* **MDVA-33606** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Behebt das Problem, dass Benutzer eine *Eindeutige Einschränkungsverletzung* Fehler beim Speichern einer einer Hierarchie zugewiesenen CMS-Seite.
* **MDVA-31590** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Behebung des Problems, bei dem Benutzer Attribute nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisieren können.
* **MDVA-36309** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem die Produktsuche nach Attributen in den Admin Rastern langsam ist.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem die Rechnung mit FPT eine falsche Gesamtsumme anzeigt, wenn die Bestellung vom Store-Guthaben bezahlt wird.
* **MDVA-37364** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.3*) - Behebung des Problems, bei dem das benutzerdefinierte Kundenattribut des Datumstyps die Rasterbenutzeroberfläche des Kunden beschädigt.
* **MDVA-39195** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebt das Problem, bei dem *Zum Warenkorb hinzufügen* auf der Kategorieseite inaktiv war, wenn die Umleitung zum Warenkorb aktiviert war.
* **MDVA-37115** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebt das Problem, bei dem ein unnötiges *Nur 0 links* wird auf der konfigurierbaren Produktseite angezeigt.
* **MDVA-39521** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebung des Problems, bei dem der Benutzer keine Versandadressen über GraphQL im Warenkorb mit einer leeren Telefonnummer festlegen kann.
* **MDVA-39384** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Behebung des Problems, bei dem das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wurde.
* **MDVA-39043** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.3*) - Behebung des Problems, bei dem der Admin-Benutzer mit eingeschränktem Zugriff beim Versuch, die *Produkte* Widget zur CMS-Seite.
* **MDVA-39966** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem bei der Bereitstellung falscher Gebietsschemata.
* **MDVA-38852** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Behebung des Problems, bei dem der Katalog-Inventar von Design Tabellen für Aktualisierungen sperrt, die die Leistung bei mehreren parallelen Bestellungen erheblich reduzieren.
* **MDVA-39986** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebung des Problems, bei dem der Benutzer mit dem Safari-Browser keine Bestellung in der Admin-Konsole in MacOS aufgeben kann.
* **MDVA-38447** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt zwei Probleme: wobei *Nicht sichtbar* konfigurierbare untergeordnete Produkte werden in der GraphQL-Antwort zurückgegeben und die MySQL-Abfrage für die GraphQL-Produktabfrage mit Kategoriefilter optimiert.
* **MDVA-40134** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem GraphQL verwandte Produkte nicht zurückgibt, wenn der freigegebene Katalog aktiviert ist.
* **MDVA-39935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem GraphQL konfigurierbare untergeordnete Produkte zurückgibt, die auf Website-Ebene deaktiviert sind.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebt das Problem, bei dem der *Aufrufen einer Member-Funktion getId()* -Fehler wird auf der Seite mit den Bestelldetails in der Admin-Konsole angezeigt.
* **MDVA-34948** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem mit langwierigen Abfragen wie `GET_LOCK`.
* **MDVA-39305** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem registrierte Kunden sich nicht mit aktiviertem Google Captcha anmelden können.
* **MDVA-37897** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem mit einer falschen Umleitung, wenn ein Kunde versucht, Produkte mit Optionen aus dem Widget &quot;Kürzlich angesehen&quot;hinzuzufügen.

## v1.1.0 {#v1-1-0}

* Patch-Kategorien wurden eingeführt, um das Benutzererlebnis zu verbessern und die Suche nach erforderlichen Patches für Kunden zu erleichtern.
* Die `patches.json` wurde in `support-patches.json`.
* **MDVA-38799** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem herunterladbare Produkte nach dem Erstellen eines Staging-Updates nicht gespeichert wurden.
* **MDVA-37592** (*für Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebung des Problems, das beim Sortieren nach Preis bei Produkten mit einem Nullpreis, der dem freigegebenen Katalog zugewiesen ist, nicht ordnungsgemäß funktioniert.
* **MDVA-38827** (*für Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Behebung des Problems, bei dem Kunden eine E-Mail zum Versand einer Bestellung mit einer Fehlermeldung erhalten.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*für Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Behebt den Fehler beim Speichern von CMS-Seiten: *Element mit derselben ID PAGE_ID ist bereits vorhanden*.
* **MDVA-34680** (*für Adobe Commerce >=2.3.6 &lt;=2.3.7 | | >=2.4.1 &lt;2.4.3*) - Behebung des Problems, bei dem die Erstellungszeit des Kundenkontos im Kundenraster nicht korrekt gefiltert wurde.
* **MDVA-37068** (*für Adobe Commerce >=2.3.1 &lt;2.4.4*) - Behebung des Problems, bei dem der falsche Steuersatz angezeigt wird, wenn der Warenkorb nur virtuelle Produkte enthält.
* **MDVA-38608** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem temporäre Tabellen nicht gelöscht werden, wenn die Neuindizierung nicht erfolgreich abgeschlossen wurde.
* **MDVA-38308** (*für Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 | | >=2.4.2 &lt;2.4.4*) - Behebt Probleme beim Hinzufügen von [!DNL Vimeo] Videos zu Produkten.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*für Adobe Commerce >=2.3.6 &lt;2.4.3*) - Behebung des Problems, bei dem der Kunde bei Verwendung der [!DNL Paypal Payment Advanced] -Methode.
* **MDVA-37082** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems beim Speichern des benutzerdefinierten Lagers von gruppierten Produkten, das dazu führt, dass das Produkt im Frontend nicht vorrätig angezeigt wird.
* **MDVA-36572** (*für Adobe Commerce >=2.3.5 &lt;2.4.3*) - Behebt das Problem, wenn Aktualisierungen des Credit Memo nicht mehr zu doppelten Aktualisierungen der Produktreservierung in der Datenbank führen.
* **MDVA-38132** (*für Adobe Commerce >=2.3.3 &lt;2.4.3*) - Behebt das Problem, wenn das Admin-Bedienfeld aufgrund einer *zu viele Umleitungen* Fehler.
* **MDVA-38270** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebt das Problem mit fehlenden Gift-Karteninformationen in der Bestellsumme in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*für Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Behebung des Problems beim Hinzufügen eines konfigurierbaren Produkts zum Warenkorb über GraphQL, wenn die Website-ID nicht mit der Store-ID übereinstimmt.
* **MDVA-36832** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem Bilder auf Seiten dupliziert werden, wenn die Ansichtsbreite 768 Pixel beträgt.
* **MDVA-37874** (*für Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Behebt das Problem, bei dem *Fester Rabattbetrag für den ganzen Warenkorb* wird fälschlicherweise auf ein Bundle-Produkt angewendet, das mehr als eine Option enthält.
* **MDVA-37913** (*für Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Behebung des Problems, bei dem herunterladbare Links ausgeblendet werden, wenn das herunterladbare Produkt über die API aktualisiert wird.
* **MDVA-34330** (*für Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem Bestellungen im Raster Bestellungen nicht nach der Admin-Zeitzone gefiltert wurden.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*für Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Behebung des Problems, bei dem Adobe Commerce beim Erstellen einer Teilrechnung für Bestellungen, die bei der *Kontozahlung* Zahlungsmethode über die REST-API.
* **MDVA-37362** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem konfigurierbare Produktoptionenwerte und Variantenattributwerte in der GraphQL-Antwort leer waren.
* **MDVA-37288** (*für Adobe Commerce 2.4.2*) - Behebung des Problems, bei dem nach der GraphQL-Anfrage falsche Stufenpreise zurückgegeben wurden.
* **MDVA-37225** (*für Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem der Upload-Prozess während der Erstellung einer Schnellbestellung unterbrochen wird, wenn in importierten SKUs ein ganzzahliger Wert vorhanden ist.
* **MDVA-37224** (*für Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem Kunden für ein verhandelbares Angebot mit [!DNL PayFlow Pro] mit einem anderen Produkt im Warenkorb.
* **MDVA-36286** (*für Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem die Vorschau des Widget &quot;Seitenaufbau-Produkte&quot;beschädigt wird, wenn dieselbe SKU eine andere Position in Unterkategorien hat.
* **MDVA-30186** (*für Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem Attributoptionen in der GraphQL-Antwort nach Optionswert statt nach Attributelementanzahl sortiert werden.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*für Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Behebung des Problems, bei dem die alten benutzerdefinierten Optionen nach dem Ändern über die API beibehalten wurden.
* **MDVA-35773** (*für Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Behebung des Problems, bei dem die Gesamtsumme nicht als Null auf der Rechnung für Bestellungen mit 100 % Rabatt angezeigt wurde.
* **MDVA-36833** (*für Adobe Commerce 2.4.2*) - Behebung des Problems mit Suchergebnissen, die nach dem Ausschließen einiger Produkte aus dem freigegebenen Katalog eine zufällige Anzahl von Produkten pro Seite anzeigten.
* **MDVA-37182** (*für Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Behebt das Problem mit falschen Suchergebnissen in beiden [!DNL Elasticsearch] Version 6 und Version 7.
* **MDVA-36253** (*für Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Behebung des Problems, bei dem die falsche Zwischensumme nach dem Löschen des Artikels im Mini-Warenkorb angezeigt wurde.
* **MDVA-36853** (*für Adobe Commerce 2.4.2*) - Behebt das Problem, dass beim Laden großer Mediengalerien keine Bilder angezeigt werden.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*für Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Behebt das Problem mit fehlenden gebündelten Produkten auf Kategorieseiten.
* **MDVA-36615** (*für Adobe Commerce 2.4.2*) - Behebt das Problem mit der falschen Produktanzahl im Admin-Produktraster.
* **MDVA-36464** (*für Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Behebung des Problems, bei dem die E-Mail-Benachrichtigungskonfiguration auf Store-Ansichtsebene nicht funktioniert.
* **MDVA-36138** (*für Adobe Commerce ^2.3.2*) - Behebung des Problems, bei dem der Versandpreis nicht angepasst und der volle Versandpreis den Kunden angezeigt wird, wenn nicht alle Artikel im Warenkorb für die Regel des kostenlosen Versandwarenkorbs infrage kommen.
* **MDVA-36424** (*für Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Behebung des Problems, bei dem an Seitenaufbauelemente angehängte Medienbilder ausgeblendet werden, wenn der Inhalt wiederholt bearbeitet wird, wenn sich die Backend-Basis-URL von der Basis-URL des Storefront unterscheidet.
* **MDVA-35984** (*für Adobe Commerce ^2.4.0*) - Behebt das Problem mit falscher Produktmenge und verkaufbarer Menge, nachdem mehrere gleichzeitige Sendungen für dasselbe Produkt erstellt wurden.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermit wird das Problem behoben, dass die GraphQL-Abfrage nicht zwischenspeichert, indem das Kategorie-Cache-Tag verwendet wird.
* **MDVA-33168** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems beim Aktualisieren eines Produktattributs über die API, wenn alle anderen Attribute zu einem leeren Wert geändert werden.
* **MDVA-19640** (*für Adobe Commerce >=2.3.0*) - Behebt das Problem, bei dem [!DNL Advanced Reporting] zeigt keine Daten an.
* **MDVA-11189** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, wenn nach dem Import einer CSV-Datei zur Aktualisierung des Produktbestands Zeilen aus der `cataloginventory_stock` gelöscht.
* **MDVA-26639** (*für Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Behebung des Problems, bei dem bei der Erstellung einer neuen E-Mail-Vorlage zur Bestellbestätigung die Bestellelemente in der Bestellmail fehlen.
* **MDVA-15546** (*für Adobe Commerce >=2.3.0*) - Behebt das Problem, bei dem nach dem Erstellen einer Bestellung eine *Spalte entity_id , wobei Klausel mehrdeutig ist* im Ausnahmeprotokoll angezeigt.
* **MDVA-21095** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, wenn eine Abfrage `INSERT INTO search_tmp` endet nicht nach der Aktualisierung des Massenattributs.
* **MDVA-23845** (*für Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Behebung des Problems, bei dem E-Mail-Vorlagen nach der Aktivierung der JavaScript-Minimierung nicht in der Vorschau angezeigt werden können.
* **MDVA-22026** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebung des Problems, bei dem der Import von Produkten aus einer CSV-Datei, einschließlich Bildern aus externen URLs, fehlschlägt.
* **MDVA-22383** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Behebung des Problems, bei dem das Speichern eines Produkts lange dauert und die Seite unterbrochen wird.
* **MC-41359** (*für Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Behebt das Problem mit den falschen SameSite-Cookie-Parametern.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*für Adobe Commerce 2.4.1*) - Behebung des Problems, bei dem der Seitenaufbau den folgenden Fehler auslöst: *Beim Starten von Page Builder ist ein Fehler aufgetreten. Wenden Sie sich an Ihren technischen Support-Ansprechpartner.*
* **MDVA-35356** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Store-Kreditrendite nach teilweise fakturierter Auftragsstornierung.
* **MDVA-33289** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Behebung des Problems, bei dem während des Checkouts roher JavaScript-Code in der Benutzeroberfläche der Rechnungsadresse angezeigt wird, wenn [!DNL Google Tag Manager] aktiviert ist.
* **MDVA-35982** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Admin-Benutzer, die auf eine bestimmte Website beschränkt sind, keine Sendung für die auf derselben Website platzierte Bestellung erstellen können.
* **MDVA-35155** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem es nicht möglich ist, ein Paket-Produkt zu kaufen, wenn der Optionstitel geändert wurde.
* **MDVA-35910** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebung des Problems, bei dem es nicht möglich ist, ein neues Kundenkonto zu erstellen, nachdem die Funktion Als Kunde anmelden deaktiviert wurde.
* **MDVA-34474** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems beim Hinzufügen eines Produkts zur Anforderungsliste mithilfe der API.
* **MDVA-34591** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Rabattberechnung für Warenkorbregeln für *Maximaler Qty-Rabatt wird auf* und *Rabattschritt &quot;Menge&quot;(Kauf X)*.
* **MDVA-33704** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Behebt das Problem, bei dem der *In store pickup* Die Versandoption wird nicht angezeigt, obwohl sie so konfiguriert ist, dass sie verfügbar ist.
* **MDVA-34928** (*für Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Behebung des Problems, bei dem der Seitenlader unbegrenzt angezeigt wird, nachdem der Store-Guthaben aus der Zahlung entfernt wurde.
* **MDVA-35254** (*für Adobe Commerce >=2.3.1 &lt;2.4.3*) - Behebt die Probleme mit CAPTCHA beim Checkout.
* **MDVA-35569** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebt das Problem, bei dem der *feste Produktsteuern* -Feld wird in der GraphQL-Antwort nicht ausgefüllt, wenn der Status angegeben ist.
* **MDVA-35847** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebung des B2B-Problems, bei dem das Formular &quot;Firmenbenutzer&quot;fehlschlägt, wenn ein benutzerdefiniertes Kundenattribut verwendet wird.
* **MDVA-31307** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebt das Problem, bei dem *Nicht genügend Arbeitsspeicher* Fehler bei bestimmten Kategorien aufgrund von Problemen mit der dynamischen CSP-Whitelisting für zwischengespeicherte Blöcke.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt die falsche *in Bearbeitung* Nachrichtenstatus auf die richtige *complete* Nachricht für Verbraucher `quoteItemCleaner` nach dem Löschen mehrerer Produkte.
* **MDVA-34102** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Stellt fest, dass die Standardspeichermenge für deaktivierte Produkte auf den Seiten &quot;Produktraster&quot;und &quot;Produkt bearbeiten&quot;im Admin-Bereich null ist.
* **MDVA-35286** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem ein Fehler auftritt, wenn ein Kunde Produkte im Warenkorb gebündelt hat und zwischen dem Checkout für mehrere Adressen und dem Checkout für eine Seite wechselt.
* **MDVA-35312** (*für Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Behebt den Antwortcode 500 bei einer leeren GraphQL-Anfrage.
* **MDVA-34189** (*für Adobe Commerce >=2.3.4 &lt;2.4.3*) - Behebt die 503-Byte-Zeitüberschreitung bei [!DNL Visual Merchandiser] Abfragen beim Laden der Seite &quot;Admin-Kategorie&quot;.
* **MDVA-34695** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebt negative Korrekturen `children_count` nach dem Löschen von Kategorien.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*für Adobe Commerce >=2.3.1 &lt;2.4.3*) - Behebt das Problem, bei dem der *Standardwert verwenden* wird gelöscht, nachdem die geplanten Änderungen angewendet wurden. Das Problem wird angezeigt, sobald die geplanten Änderungen nicht mehr in Kraft sind.
* **MDVA-35064** (*für Adobe Commerce >=2.3.3 &lt;2.4.3*) - Behebung des Problems, bei dem URL-Neuschreibungen nicht für konfigurierbare Produkte generiert werden, die über API erstellt wurden.
* **MDVA-34943** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die Schnellbestellung die zuvor eingegebenen SKUs zwischenspeichert.
* **MDVA-35197** (*für Adobe Commerce >=2.3.5 &lt;2.4.0*) - Behebung des Problems, bei dem beim Hinzufügen zum Warenkorb mit GraphQL ein Fehler auftrat, wenn zuvor hinzugefügte Produkte nicht mehr vorrätig waren.
* **MDVA-34850** (*für Adobe Commerce >=2.3.1 &lt;2.4.0*) - Behebung des Problems, bei dem die nicht vorrätigen Optionen eines konfigurierbaren Produkts nicht angezeigt werden, anstatt als Durchsicht angezeigt zu werden.
* **MDVA-34867** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Werte für ein Bedingungsfeld, das für eine geplante Aktualisierung festgelegt wurde, nicht gespeichert werden.
* **MDVA-35092** (*für Adobe Commerce >=2.3.5 &lt;2.4.3*) - Behebung des Problems, bei dem Benutzer nicht hinzufügen können [!DNL Vimeo] Videos aufgrund veralteter Funktionen [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*für Adobe Commerce >=2.3.6 &lt;2.4.3*) - Behebung des Problems, bei dem die Vorschau des Inhaltstyps von Page Builder-Produkten beschädigt wird, wenn übereinstimmende Produkte für jede Website unterschiedliche Preise haben.
* **MDVA-32634** (*für Adobe Commerce ^2.3.1*) - Behebt das Problem, bei dem der `url_path` Die Kategorie, die allen Stores zugewiesen ist, bleibt nach dem Verschieben der Kategorie in der Hierarchie unverändert.
* **MDVA-33344** (*für Adobe Commerce ^2.3.0*) - Behebt das Problem, bei dem hartcodiert ist `rma_item` Die standardmäßige Entitätsattributsatz-ID wird anstelle des Werts aus der Datenbank verwendet.
* **MDVA-34192** (*für Adobe Commerce >=2.3.4 &lt;2.4.3*) - Behebung des Problems, bei dem es nicht möglich ist, das Geburtsdatum des Kunden im TT/MM/JJJJ-Format zu ändern/anzugeben.
* **MDVA-34847** (*für Adobe Commerce ^2.3.0*) - Behebt die Konvertierung des Stores-IDs-Typs in Integer für SQL-Bedingung in Admin-Sammlungen für Admin-Benutzer mit benutzerdefinierten Berechtigungen.
* **MDVA-34886** (*für Adobe Commerce ^2.3.2*) - Behebung des Problems, bei dem die Suche keine Ergebnisse zurückgibt, wenn *Gewichtung* Das Produktattribut ist als durchsuchbar konfiguriert.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem von [!DNL PayPal Payflow Pro] Zahlungsfehler mit Fehler beim Umleitungsparameter-Listenformat.
* **MDVA-34023** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem, bei dem der Fehler auftrat *Keine solche Entität mit addressId* in den Browsern der Besucher zufällig angezeigt.
* **MDVA-32759** (*für Adobe Commerce >=2.3.1 &lt;2.4.3 mit B2B-Erweiterung*) - Behebung des Problems, bei dem freigegebene Kataloge die vorhandenen Tier-Preise löschen.
* **MDVA-33482** (*für Adobe Commerce ^2.3.5*) - Behebung des Problems, bei dem das Generieren eines KreditMemos für eine Teilrechnung zu einer Steuer für die gesamte Bestellung anstelle der Steuer für diese Teilrechnung führt.
* **MDVA-33393** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt den Fehler *Die bereitgestellte countryId ist nicht vorhanden*.
* **MDVA-33632** (*für Adobe Commerce >=2.3.0 &lt;2.3.7*) - Stellt eine Fehlerbehebung bereit, bei der die Ausnahmemeldung *Dieses Produkt ist nicht vorrätig* wird nun einem Admin-Benutzer angezeigt, wenn er versucht, ein nicht vorrätiges Produkt neu zu bestellen.
* **MDVA-34469** (*für Adobe Commerce >=2.4.1 &lt;2.4.2*) - Behebung des Problems, bei dem GraphQL-Mutationen auf den Warenkorb eines Kunden bei der Verwendung mehrerer Store-Ansichten fehlschlugen.
* **MDVA-33976** (*für Adobe Commerce >=2.3.0 &lt;2.3.7*) - Behebung des Problems, bei dem das Bundle-Produkt auf der Storefront angezeigt wird, nachdem die zweite Option aus dem Bundle-Produkt entfernt wurde.
* **MDVA-33894** (*für Adobe Commerce >=2.4.0 &lt;2.4.1 mit B2B-Erweiterung*) - Behebt mehrere Probleme mit der Funktion &quot;Schnellbestellung&quot;, einschließlich Hinzufügen und Entfernen mehrerer Produkte und der SKU-Groß-/Kleinschreibung.
* **MDVA-27664** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem im Formular zur Kundenregistrierung, das zur Anzeige eines Fehlers führte: *FEHLER - Das Geburtsdatum sollte nicht größer sein als heute.*
* **MDVA-33970** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebung des Problems, bei dem das falsche Währungszeichen in der Kreditkarte vorhanden ist, wenn der Umfang des Preisattributs auf Website festgelegt ist.
* **MDVA-33992** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass die B2B-Sonderpreise beim Checkout falsch angezeigt werden.
* **MDVA-34100** (*für Adobe Commerce >=2.3.4 &lt;2.4.2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem ein Unternehmenskonto nicht über die Seite mit der Unternehmensstruktur erstellt werden kann.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*für Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Behebt das Problem mit duplizierten Bildern nach dem Produktimport aus einer CSV-Datei.
* **MDVA-33382** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt die Probleme mit der Invalidierung von Indexern nach dem Entfernen von Produkten aus einer Kategorie.
* **MDVA-28511** (*für Adobe Commerce >=2.3.5 &lt;2.3.6*) - Behebt das Problem, bei dem es nicht möglich ist, [!DNL PayPal] Checkout, wenn das Feld Name bestimmte Zeichen enthält (z. B. Großbuchstaben).
* **MDVA-31519** (*für Adobe Commerce >=2.3.5 &lt;2.3.6*) - Behebt das Problem mit Wartezeitüberschreitungen beim Gast-Checkout, wenn eine Site-weite Verkaufsregel verwendet wird.
* **MDVA-33281** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem, bei dem ein schwerwiegender Fehler in `inventory:reservation:list-inconsistencies` aufgrund eines falschen SKU-Parametertyps.
* **MDVA-24201** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebung des Problems, bei dem die Preise nicht die Preisregel des geplanten Warenkorbs widerspiegeln, bevor sie manuell neu indiziert wurden.
* **MDVA-32694** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 | | >= 2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem ein Admin-Benutzer ein Produkt nicht zu einem verhandelbaren Angebot hinzufügen kann, wenn es sich um einen nicht standardmäßigen Store handelt.
* **MDVA-33516** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem das Bearbeiten eines Bundle-Produkts in einer Anforderungsliste zu einem Fehler führt.
* **MDVA-33975** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebt mehrere Probleme im Zusammenhang mit der Preisberechnung in GraphQL-Anforderungen.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem mit [!DNL PayPal] Abwicklungsberichte sind nicht verfügbar unter **Berichte** > **Vertrieb** > **[!DNL PayPal]** Abrechnung wie erwartet.
* **MCP-87** (*für Adobe Commerce >=2.3.1 &lt;2.4.2*) - Verbesserte Indexierungszeit für Kategorieprodukt- und Bestandsindizes für große Profile.
* **MDVA-33106** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass die neu geplanten Produktänderungen nach dem Cron gelöscht werden. `run` ausgeführt wird.
* **MDVA-19391** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, bei dem `analytics_collect_data` gibt aufgrund von NULL-Beschreibungsdatensätzen im `catalog_category_entity_text` Tabelle.
* **MDVA-20376** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebt das Problem mit dem *Keine solche Entität mit customerId = 1* -Fehler im `exception.log` für angemeldete Kunden nach Bestellplatzierung.
* **MDVA-23764** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebt den Fehler in `JsFooterPlugin.php` die sich auf die Anzeige dynamischer Blöcke auswirkt.
* **MDVA-13203** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, bei dem der *Integrationsbeschränkung bei Verletzung der Tabelle search_tmp_* nach einer vollständigen Neuindizierung angezeigt.
* **MDVA-23426** (*für Adobe Commerce >=2.3.3 &lt;2.3.5*) - Behebung des Problems, bei dem Benachrichtigungs-E-Mails, die von Adobe Commerce gesendet werden, einen leeren Textkörper mit Inhalt als Anhang enthalten.
* **MDVA-22150** (*für Adobe Commerce >=2.3.1 &lt;2.3.4*) - Behebung des Problems, bei dem sich Kunden mit einem konfigurierbaren Produkt im Warenkorb und einem angewendeten Coupon nicht anmelden können, wenn dieses konfigurierbare Produkt in Admin deaktiviert ist.
* **MDVA-32545** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem Rechnungen nicht automatisch gesendet werden, wenn Bestellungen von einem Administrator erstellt werden.
* **MDVA-32714** (*für Adobe Commerce >=2.3.4 &lt;2.4.1*) - Behebung des Problems, bei dem der Kundengruppenpreis in der GraphQL-Produktabfrage nicht funktioniert.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Fügt die *Zwischensumme (inkl. Steuern)* Option zu Preisregelbedingungen.
* **MDVA-31236** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem Administratoren mit benutzerdefiniertem Ressourcenzugriff keine 2FA einrichten oder sich anmelden können.
* **MDVA-30845** (*für Adobe Commerce >=2.3.5 &lt;2.3.7*) - Behebt das Problem, bei dem der *Für diese Bestellung sind derzeit leider keine Angebote verfügbar* wird ein Fehler angezeigt, wenn keine Verbindung zu UPS XML/USPS/DHL hergestellt werden konnte und keine andere Versandmethode verfügbar ist.
* **MDVA-32133** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebt das Problem, dass die Mediensalerie in bestimmten Fällen nicht aus dem Seitenaufbau geladen wird.
* **MDVA-12304** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Erhöht die maximale Anzahl von Cookies von 50 auf 200.
* **MDVA-32632** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebung des Problems, bei dem Bestellungen im Zahlungssystem, aber nicht in Adobe Commerce angezeigt werden.
* **MDVA-32449** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0 || >=2.4.1 &lt;2.4.2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem der Auftragsverlauf sehr langsam geladen wird oder überhaupt nicht geladen wird.
* **MDVA-32739** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem durch die Aktivierung von asynchronen E-Mail-Benachrichtigungen alte E-Mails zum Verkauf gesendet werden.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*für Adobe Commerce 2.3.6, 2.4.1*) - Behebt das Problem, bei dem der *Konto erstellen* Schaltfläche bleibt deaktiviert, nachdem ungültige Daten im *Neues Kundenkonto erstellen* Formular.
* **MDVA-31006** (*für Adobe Commerce 2.3.0, 2.3.1*) - Behebung des Problems, bei dem duplizierte Bestellungen angezeigt werden, nachdem eine Bestellung mit [!DNL Paypal Express] Zahlung.
* **MDVA-25602** (*für Adobe Commerce 2.3.0*) - Behebt ein Problem mit [!DNL PayPal Payflow Pro] Zahlungsmethode und Behandlung von Cookies als `SameSite=Lax` Standardmäßig werden im Chrome 80-Browser und in der API-Antwort die Kunden-Anmeldeseite umgeleitet.

## v1.0.10 {#v1-0-10}

Kleinere Fehlerbehebungen für Patch-Versionen

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Behebung des Problems, bei dem die Warenkorbpreisregel mit Coupon nicht über GraphQL angewendet wird, wenn *Fester Rabatt auf den gesamten Warenkorb* -Aktion verwendet wird.
* **MDVA-30889** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem ein Fehler auftritt, nachdem ein Bundle mit virtuellen und einfachen Produkten als Optionen berechnet wurde.
* **MDVA-31791** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Verbessert die Leistung der Produktseite, wenn Zielregeln oder verknüpfte Produkte verwendet werden.
* **MDVA-31168** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die CSV-Datei für den Produktexport nicht angezeigt wird und ein Speicherzuordnungsfehler auftritt.
* **MDVA-32313** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Behebung des Problems, bei dem konfigurierbare Produkte zur Wunschliste mit den falschen Konfigurationsoptionen hinzugefügt werden konnten.
* **MDVA-31759** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem Produkte nicht aktualisiert wurden mit *Dropdown* und *textarea* -Attributwerte während des CSV-Imports.
* **MDVA-32012** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem Postleitzahlen in Korea und Argentinien nicht validiert werden können.
* **MDVA-31640** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 | | >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem ein Sonderpreis nicht über die REST-API aktualisiert werden kann.
* **MDVA-28651** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 | | >2.4.0 mit B2B-Erweiterung*) - Behebung des Problems, bei dem Leistungsprobleme beim Laden übertragbarer Anführungszeichen über die REST-API auftreten.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*für Adobe Commerce >=2.3.0 &lt;2.4.1 mit B2B-Erweiterung*) - Behebung des Problems, bei dem ein falsches Währungszeichen im Raster &quot;Credit Memo&quot;angezeigt wird.
* **MDVA-31295** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem Prämienpunkte nicht berechnet werden, wenn eine partielle Bestellung abgeschlossen und Artikel besteuert werden.
* **MDVA-30112** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebung des Problems, bei dem die Anzahl der Bestellungen die Anzahl der *Bounch-Größe* -Wert, berücksichtigt Adobe Commerce die Bestellungen mit *pending* Status als Inkonsistenzen.
* **MDVA-31150** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die Guthaben- und Geschenkkarten-Storekonten nicht vom GET Invoice Rest API-Aufruf zurückgegeben werden, wenn die Rechnung durch den Rest-API-Aufruf gepostet wurde und die Bestellung teilweise von Kredit- und Geschenkkartenkonten bezahlt wurde.
* **MDVA-30963** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Behebung des Problems, bei dem die Ergebnisse der Produktfilterung so eingestellt sind, dass sie nur die Werte enthalten, die für *Alle Store-Ansichten* im Admin-Bereich Produkte mit Werten einschließen, die auf der Ebene der Store-Ansicht überschrieben werden.
* **MDVA-29954** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0 | 2.4.2 mit B2B-Erweiterung*) - Behebt das Problem, bei dem der *Neue Anforderung zur Unternehmensregistrierung* und *Sie wurden mit einer Firma verbunden* E-Mails werden von der falschen Adresse gesendet.
* **MDVA-28357** (*für Adobe Commerce >=2.3.2 &lt;2.3.6 | | >=2.4.0 &lt;2.4.1*) - Ersetzt den Standard-Analyzer durch einen benutzerdefinierten Analyzer durch den Keyword-Tokenizer für das SKU-Feld im [!DNL ElasticSearch] Index , damit Platzhaltersuchabfragen mit SKUs funktionieren, die einen Bindestrich enthalten (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem der benutzerdefinierte Bestellstatus in geändert wurde *Verarbeitung* nach Teillieferung mit WebAPI.
* **MDVA-30428** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Behebung des Problems, bei dem Kunden ein Produkt nicht auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-30594** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem eine Bestellung mit mehreren Adressen beim Checkout nicht gespeichert werden konnte, wenn FPT konfiguriert wurde.
* **MDVA-29148** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem beim Erstellen eines Produkts über einen API-Aufruf, das benutzerdefinierte Produktattribut von `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (wie Multiselect) verwendet seinen Standardwert nicht, wenn in der Payload kein Wert angegeben wurde.
* **MDVA-30837** (*für Adobe Commerce >=2.3.1 &lt;2.3.5*) - Eine Konfigurationseinstellung wurde hinzugefügt. *Steuern auf Betrag einschließen: Ja/Nein* in der Konfiguration der Versandmethode &quot;Free Shipping&quot;. Wann *Steuern auf Betrag einschließen* auf *Ja*, wird der Mindestbestellbetrag als Zwischensumme + Steuer berechnet. Wann *Steuern auf Betrag einschließen* auf *Nein*, wird der Mindestauftragsbetrag als Zwischensumme berechnet
* **MDVA-25028** (*für Adobe Commerce >=2.3.2 &lt;2.3.3 | | >=2.3.5 &lt;2.3.6*) - Behebt das Problem bei Bestellungen, die mit [!DNL PayPal Payflow Pro] nicht auf den Status &quot;Betrug verdächtig&quot;gesetzt, wenn Betrugsfilter ausgelöst werden.
* **MDVA-31224** (*für Adobe Commerce >=2.3.3 &lt;2.3.5*) - verbessert die Leistung der `catalog_product_price` Neuindizierungsvorgang für Bundle-Produkte.
* **MDVA-31321** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebt eine leere Seite (Fehler) bei *Alle anzeigen* ausgewählt ist. [!DNL Elasticsearch] gibt eine große Liste von Produkt-IDs zurück. In diesem Szenario wird die Reihenfolge nach Klausel in ein falsches SQL-Format konvertiert.
* **MDVA-30815** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebung des Problems, bei dem Adobe Commerce eine leere Seite anzeigt, wenn Sie ändern, wie viele Suchergebnisse auf der Suchergebnisseite angezeigt werden sollen. [!DNL Elasticsearch] zeigt jetzt korrekt Ergebnisse aus Kategorieseiten an, wenn Sie die Anzahl der pro Seite angezeigten Suchergebnisse ändern.
* **MDVA-30782** (*für Adobe Commerce >=2.3.5 &lt;2.4.2*) - Behebung des Problems, bei dem der dynamische Block unabhängig von der Warenkorbregel angezeigt wird.
* **MDVA-31021** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, bei dem Leistungsprobleme in `module-catalog-import-export/Model/Import/Product/Option.php`. Wenn mehr als ~100.000 Datensätze in `catalog_product_option` -Tabelle verwenden, dauert die Validierung einer neuen CSV mit einem einzelnen Produkt weniger als 10 Sekunden.
* **MDVA-31007** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem benutzerdefinierte Adressattribute auf der Seite mit den Bestelldetails in meinem Kontobereich und im Backend nicht korrekt angezeigt werden.
* **MDVA-29389** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem mit der erweiterten Berichterstellung, bei dem die Variable `analytics_collect_data` cronjob sagt: *Der Port muss innerhalb des Host-Parameters konfiguriert werden (z. B. localhost:3306).*.
* **MDVA-31343** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem mit der entfernten Textklasse `page-layout-category-full-width` wenn eine Kategorie geplant ist.
* **MDVA-30945** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass Sie beim Aktualisieren von Warenkorb eine Fehlermeldung mit schwerwiegenden Folgen erhalten `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*für Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementiert die *Minimum sollte übereinstimmen* Funktionalität und Teilsuche nach [!DNL Elasticsearch] Motor. Löst Probleme mit Bindestrichen in Suchabfragen.
* **MDVA-30102** (*für Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Behebung des Problems, bei dem der Redis-Cache schnell wächst, da Layout-Caches keine TTL aufweisen.
* **MDVA-30599** (*für Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Behebung des Problems, bei dem mit der API erstellte Gastangebote fälschlicherweise als Anführungszeichen für angemeldete Kunden markiert wurden.
* **MDVA-29446** (*für Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Behebung des Problems, bei dem der Preis einer nicht anwendbaren Versandmethode beim Checkout als null angezeigt wird.
* **MDVA-30357** (*für Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Behebt das Problem, dass beim Generieren einer Sitemap durch Cron falsche Bild-URLs erstellt werden.
* **MDVA-30565** (*für Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Behebt das Problem, bei dem *Keine solche Entität mit cartid = 0* wird für Gastkunden beim Storefront-Checkout angezeigt, wenn der beständige Warenkorb aktiviert ist.
* **MDVA-29787** (*für Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Behebung des Problems, bei dem die Zielregel für verwandte Produkte nicht funktioniert, wenn *ist einer von* -Bedingung verwendet, um anzuzeigende Produkte zu definieren.
* **MDVA-30977** (*für Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Behebt das Problem mit zufälligen Produkten, die nach der Neuindizierung in Kategorien fehlen.
* **MDVA-28202** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Behebung des Problems, bei dem die Layered Navigation konfigurierbare Produkte bei Verwendung von MSI nicht korrekt filtert.
* **MDVA-28300** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem die GQL-Anfrage nicht die Preisänderungen aus den Katalogpreisregeln widerspiegelt.
* **MDVA-31006** (*für Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Behebung des Problems, bei dem duplizierte Bestellungen angezeigt werden, nachdem eine Bestellung mit [!DNL Paypal Express] Zahlung.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Behebt das Problem mit mehrschichtiger Navigation, bei dem die *Nein* Wert für boolesche Produktattribute wurde nicht in die mehrteilige Navigation einbezogen, wenn [!DNL Elasticsearch] wurde als Suchmaschine verwendet.
* **MDVA-28191** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem während der Bestellerstellung über den Administrator keine Zahlungsmethoden geladen wurden.
* **MDVA-29959** (*für Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 mit B2B-Erweiterung*) - Behebt das Problem, bei dem der eingeschränkte Admin-Benutzer mit *Unternehmen* -Berechtigungen dürfen das Unternehmenskonto nicht löschen.
* **MDVA-30265** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem der Versand-Tracking-Link nach der Rechnungserstellung nicht mehr funktioniert.
* **MDVA-28409** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Behebt das Problem, bei dem der `sales_clean_quotes` Cron-Auftrag schlägt fehl mit *Nicht genügend Arbeitsspeicher* Fehler, wenn die Anzahl der abgelaufenen Anführungszeichen in der Datenbank sehr groß ist.
* **MDVA-30593** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Behebung des Problems, bei dem Angebote, die gemäß der Einstellung Anführungszeitintervall abgelaufen sind, nicht bereinigt wurden.
* **MDVA-30107** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem der Store-Umschalter nicht wie erwartet funktioniert, wenn für Store-Ansichten verschiedene Basis-URLs verwendet werden.
* **MDVA-28763** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebung des Problems, bei dem das Produktbild dupliziert wird, nachdem Produktinformationen mehrmals mit der REST-API aktualisiert wurden.
* **MDVA-30284** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Indexer für die Katalogsuche aufgrund der folgenden Faktoren fehlschlägt *[!DNL Elasticsearch]error: -Grenze der Gesamtfelder im Index wurde überschritten.*
* **MDVA-29042** (*für Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem die Katalogberechtigungen geändert wurden in *Zulassen* automatisch, nachdem dem freigegebenen Katalog ein neues Produkt hinzugefügt wurde.
* **MDVA-30428** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem Kunden ein Produkt nicht auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-28661** (*für Adobe Commerce >=2.3.0 &lt;2.4.2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem im Abschnitt Unternehmensbenutzerkonto für Unternehmen ein Fehler ausgegeben wird, nachdem der Unternehmensadministrator geändert wurde.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*für Adobe Commerce 2.3.1 - 2.3.4-p2*) - Behebung des Problems, bei dem Cron-Aufträge fehlschlagen, wenn der Datenbankname zu lang ist, was dazu führt, dass Kategorien nicht auf der Vorderseite aktualisiert werden.
* **MDVA-30106** (*für Adobe Commerce ^2.3.0*) - Behebung eines Problems, bei dem während der Kassenvorgänge nicht mit *Die Eigenschaft &#39;length&#39; von null kann nicht gelesen werden* -Fehler in der JS-Konsole.
* **MDVA-28656** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 | | >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Bestellstatus geändert wird, wenn eine Bestellung ohne erforderliche Zahlungsinformationen aufgegeben wurde (z. B. mit 100 % Rabatt) und eine Rechnung für die Bestellung erstellt wurde. *Geschlossen* anstelle von Complete.
* **MDVA-30209** (*für Adobe Commerce 2.3.0 - 2.3.3-p1*) - Behebung des Problems, bei dem die Kundengruppe in die Standardeinstellung geändert wurde, wenn der Kunde seine Kontoinformationen aktualisierte.
* **MDVA-30123** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebung des Problems, bei dem Attributoptionen-Beschriftungen für GraphQL-Abfragen nicht korrekt übersetzt werden.
* **MDVA-29996** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem die Kategorieseite nach der Aktivierung der Kategorieberechtigungen nicht vom vollständigen Seiten-Cache zwischengespeichert wird.
* **MDVA-30164** (*für Adobe Commerce >=2.3.1 &lt;2.4.2*) - Behebung des Problems, bei dem Kundendatensätze nicht aus dem Kundenraster exportiert werden können, wenn benutzerdefinierte Kundenattribute vorhanden sind.
* **MDVA-30444** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebung des Problems, bei dem keine Bestätigungs-E-Mail für Bestellungen gesendet wird, die mit GraphQL aufgegeben wurden.
* **MDVA-30490** (*für Adobe Commerce 2.3.4 - 2.3.5-p2*) - Behebung des Problems, bei dem der Produktvergleich die Fehlerseite 500 auslöst, wenn eines der Produkte eine leere kurze Beschreibung enthält.
* **MDVA-30232** (*für Adobe Commerce >=2.3.1 &lt;2.4.1*) - Behebung des Problems, bei dem es nicht möglich ist, eine neue Bestellung vorzunehmen, wenn die ursprüngliche Bestellung eine Geschenkkarte enthält.
* **MDVA-29965** (*für Adobe Commerce >=2.3.3 &lt;2.4.0*) - Behebung des Problems, bei dem Kunden beim Hinzufügen eines Produkts zum Warenkorb einen Fehler wegen eines ungültigen Formularschlüssels erhalten.
* **MDVA-30008** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des B2B-Problems, bei dem es nicht möglich ist, über die Admin-API Bestellungen für ein Produkt zu tätigen, das sich in einem öffentlichen Katalog befindet.
* **MDVA-22469** (*für Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Behebung des Problems, bei dem nach der Aktualisierung auf Adobe Commerce 2.3.3 der Seitenaufbau im Admin-Bereich nicht funktioniert und einige JS- und CSS-Dateien nicht geladen werden.
* **MC-35984** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem Händler nach dem Erstellen einer Versandbeschriftung für eine Return Merchandise Authorization (RMA) nicht mit Seitenelementen auf der Rückgabeseite interagieren konnten.

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*für Adobe Commerce 2.3.0 - 2.3.4*) - Behebt das Problem mit [!DNL PayPal Payflow Pro] Zahlungsmethode und Behandlung von Cookies als `SameSite=Lax` Standardmäßig werden im Chrome 80-Browser und in der API-Antwort die Kunden-Anmeldeseite umgeleitet.
* **MDVA-26694** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0*) - Behebt das Problem, dass Produkt- und Katalogzwischenspeicher täglich ablaufen, obwohl geplant ist, dass sie anders ablaufen.
* **MDVA-27825** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebung des Problems, bei dem der Export großer Datenmengen aufgrund von Speicherleck fehlschlug.
* **MDVA-29085** (*für Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Behebung des B2B-Problems, bei dem keine neuen Unternehmens-E-Mails gesendet werden, wenn ein Unternehmen durch die API erstellt wird.
* **MDVA-29344** (*für Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Behebung des Problems, bei dem der Seitenaufbau hängen bleibt, nachdem Text aus einem Kopfzeilenelement in ein Textelement kopiert wurde.
* **MDVA-29835** (*für Adobe Commerce >2.3.1 &lt;2.4.2*) - Behebung des Problems, bei dem Bestellungen von Geschenkkarten zwei Codes anstelle eines enthielten.
* **MDVA-30052** (*für Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Behebung des Problems, bei dem private Inhalte (lokaler Speicher) nicht ordnungsgemäß ausgefüllt wurden, was zu Leistungsproblemen führte.
* **MDVA-30131** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Behebt das Problem mit mehrschichtiger Navigation, bei dem die *Nein* Wert für boolesche Produktattribute wurde nicht in die mehrteilige Navigation einbezogen, wenn [!DNL Elasticsearch] wurde als Suchmaschine verwendet.
* **MDVA-35514** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems beim Erstellen eines Versandtitels und Hinzufügen bestellter Produkte zu einem Paket im modalen Fenster Pakete erstellen .