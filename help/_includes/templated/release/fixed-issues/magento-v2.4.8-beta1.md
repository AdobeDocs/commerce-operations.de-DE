---
source-git-commit: e55cd8bad0744a41fdaab4c2ed0048149f91828d
workflow-type: tm+mt
source-wordcount: '12044'
ht-degree: 0%

---
# Behobene Probleme mit Magento Open Sourcen (v2.4.8-beta1)

## Behobene Probleme

In Magento Open Source 2.4.8 des Core-Codes wurden 221 Probleme behoben. Eine Untergruppe der in dieser Version enthaltenen behobenen Probleme wird nachfolgend beschrieben.

### APIs

* _AC-10042_: /V1/transactions REST API gibt Fehler zurück, wenn parent_txn_id = txn_id
   * _FEHLER HINWEIS_: Das System verarbeitet nun korrekt die übergeordneten und untergeordneten Konzepttransaktionen, bei denen die übergeordnete Transaktions-ID mit der Transaktions-ID übereinstimmt. Dadurch wird verhindert, dass bei der Abfrage des REST-API-Endpunkts /V1/transactions eine Endlosschleife entsteht. Zuvor führte dieses Szenario zu einem schwerwiegenden Fehler, da die maximale Ausführungsdauer überschritten wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AKP2E-2927_: [REST API]: Die Verwendung des Standardwerts in der Store-Ansicht bleibt nach dem Hinzufügen von Konfigurationen für ein konfigurierbares Produkt nicht aktiviert
   * _Hinweis reparieren_: Das Problem wurde behoben, indem korrekte Datenbankeinträge für die anpassbaren Optionen für einen nicht standardmäßigen Store sichergestellt wurden. Das Kontrollkästchen für den benutzerdefinierten Store im Abschnitt &quot;Admin > Katalog > Produktbearbeitung > Anpassbare Optionen&quot;war zuvor aufgrund ungenauer Datenbankeinträge deaktiviert, selbst wenn der Optionstitel für den benutzerdefinierten Store derselbe blieb wie der Standardspeicher.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _AKP2E-3091_: [Cloud] Erstellen der doppelten Kundengruppe für Website-Gruppen in der Tier-Preise-API.
   * _Hinweis korrigieren_: Die Tier Price Rest API ermöglicht jetzt nicht, die Kundengruppe &quot;Website-Gruppe duplizieren&quot;zu erstellen.
Zuvor war es möglich, die Kundengruppe Website-Gruppe duplizieren in der Tier-Preise-API zu erstellen, die die Validierung beim Speichern des Produkts nicht in Admin übergab.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _AC-11878_: [GraphQL] Problem mit Typ in 2.4.7
   * _Hinweis korrigieren_: Das System verarbeitet jetzt beim Ausführen einer GraphQL-Abfrage die ganzzahligen Werte in der Funktion GetCustomSelectedOptionAttributes korrekt, wodurch Fehler im Zusammenhang mit Typen verhindert werden. Zuvor führte der Start einer GraphQL-Abfrage, bei der GetCustomSelectedOptionAttributes mit einem integer -Argument verwendet wurde, zu einem Typfehler.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38663>
* _AKP2E-3130_: Bestellkommentare mit Status können nicht über die REST-API hinzugefügt werden
   * _Hinweis korrigieren_: Das Problem wurde behoben, indem die Änderung des Status der Reihenfolge zugelassen wurde, wenn sie nur vom aktuellen Status stammt. Zuvor wurde der Bestellstatus nicht berücksichtigt und Änderungen am Bestellstatus verhindert, selbst wenn dieser vom selben Status stammte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _AKP2E-3079_: Aktualisierung der Kundenadresse bei Aktualisierung über die REST-API fehlgeschlagen, wenn &quot;validateDefaultAddress&quot;aktiviert ist
   * _Hinweis reparieren_: Der API-Endpunkt funktioniert jetzt wie beabsichtigt, nachdem das Problem mit dem ID-Schlüssel, der in der API-Payload fehlt, behoben wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _AKP2E-2969_: REST-API kann bei Verwendung von Oauth1 keine Anfragen mit Schrägstrich (/) in der SKU senden
   * _Hinweis reparieren_: Vor der Fehlerbehebung war es nicht möglich, einen erfolgreichen API-Aufruf für ein Produkt durchzuführen, dessen SKU &quot;/&quot;enthielt. Jetzt können Sie eine erfolgreiche API-GET-Anfrage für Produktdetails erstellen, obwohl die SKU einen Schrägstrich enthält.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Konto

* _AC-10782_: Das Formular für Kundenadressen ermöglicht zufälligen Code in den Namensfeldern
   * _Hinweis reparieren_: Das System validiert jetzt die Eingabe in die Felder &quot;Vorname&quot;und &quot;Nachname&quot;im Formular für Kundenadressen, wodurch die Verwendung von zufälligem Code verhindert wird. Zuvor ermöglichte das System die Verwendung von zufälligem Code in diesen Feldern, ohne dass ein Fehler ausgegeben wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38345>
* _AC-11999_: dev:di:info-Fehler in magento 2.4.7
   * _Hinweis reparieren_: Das System zeigt jetzt beim Ausführen des dev:di:info-Befehls die Konstruktorparameter korrekt an, sodass keine Fehler mehr auftreten. Zuvor führte die Ausführung dieses Befehls zu einem Fehler aufgrund einer Typabweichung im -Argument.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: Der Kunde ist angemeldet, zeigt jedoch den 404-Fehler im Frontend an.
   * _Hinweis reparieren_: Die Storefront-Kunden-Dashboard-Seite wird jetzt erwartungsgemäß geladen, wenn sich ein Kunde anmeldet. Zuvor konnten sich Kunden anmelden, aber auf dieser Seite wurde ein 404-Fehler angezeigt. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35838>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/36263>
* _AC-11919_: Admin: Seitenereignis-Schaltflächen schwebend links statt rechts
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub-Codebeitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>
* _AC-10990_: Absturz der Adresse zum Hinzufügen meines Kontos beim Speichern
   * _Hinweis korrigieren_: Das System speichert jetzt Kundenadressen korrekt, auch wenn das Feld &quot;region&quot;nicht angezeigt wird. Dadurch wird ein Absturz während des Speichervorgangs verhindert. Zuvor führte der Versuch, eine Adresse ohne angezeigtes Feld &quot;region&quot;hinzuzufügen oder zu bearbeiten, zu einem Ausnahmefehler.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38407>
* _AKP2E-2791_: Informationen zu Kundenattributen können nicht im Abschnitt &quot;Admin-Kunden bearbeiten&quot;gespeichert werden.
   * _Hinweis korrigieren_: Die Store-ID des Kunden wird jetzt für das Bearbeitungsformular des Admin-Kunden entsprechend dem Website-Umfang ordnungsgemäß implementiert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/488c1034>

### Admin-Benutzeroberfläche

* _AKP2E-3171_: CSB ist nicht für zugelassene spezifische Länder verfügbar
   * _FEHLER HINWEIS_: Jetzt ist die Zustellung per Nachnahme für zugelassene Länder verfügbar, wann immer dies erforderlich ist und   AC-3216 funktioniert erwartungsgemäß.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _AC-7700_: [Problem] Ablegen von Indexer-Änderungstabellen bei mview unsubscribe
   * _Hinweis korrigieren_: Das System entfernt jetzt automatisch nicht verwendete Änderungstabellen, wenn ein Index von &quot;planmäßig aktualisieren&quot;auf &quot;Beim Speichern aktualisieren&quot;umgestellt wird. Dadurch wird der Index als ungültig markiert, um sicherzustellen, dass keine Einträge fehlen. Zuvor führte der Wechsel eines Index zu &quot;Beim Speichern aktualisieren&quot;dazu, dass nicht verwendete Änderungstabellen im System verbleiben und alle geänderten Indizes als &quot;gültig&quot;markiert wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/25859>
* _AKP2E-3033_: Mehr als 200 Bestellungen können nicht exportiert werden
   * _Hinweis reparieren_: Die Serverbeschränkungen für die Anforderungsgröße von zuvor gesendeten ausgewählten IDs wurden vernachlässigt, indem die HTTP-Anforderung von GET zu POST geändert wurde, um das Problem zu beheben. Bisher wurde das Problem aufgrund der Serverbeschränkungen für die GET-Anforderungsgröße behoben.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _AKP2E-2787_: Apostroph im Namen der Store-Ansicht wird durch &quot;&quot;ersetzt.
   * _Hinweis korrigieren_: Die Speicheransichtsfilter des Rasters zeigen jetzt Apostrophe ordnungsgemäß an
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AKP2E-2978_: Wenn Sie ein Produkt durch einen Administrator mit einem anderen Rollenbereich speichern, werden vorhandene zugehörige Produktinformationen im Produkt überschrieben/gelöscht
   * _Hinweis reparieren_: Zuvor wurden die zugehörigen Produkte vor der Korrektur zurückgesetzt und leer gelassen, als der sekundäre Administrator auf die Schaltfläche zum Speichern klickte, ohne dass sich die zugehörigen Produkte änderten. Nach dieser Fehlerbehebung klickt der sekundäre Administrator auf die Schaltfläche &quot;Speichern&quot;. Das Produkt wird nicht zurückgesetzt und erfolgreich gespeichert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _AC-9843_: i18n:collect-phrases bricht die Integrität der Übersetzungen
   * _Hinweis korrigieren_: Der Befehl `bin/magento i18n:collect-phrases -o` erfasst jetzt korrekt und fügt neue Ausdrücke aus JavaScript- und .phtml-Dateien hinzu, um sicherzustellen, dass Übersetzungen in der Übersetzungsdatei korrekt wiedergegeben werden. Zuvor konnte das System mehrzeilige Übersetzungssätze aus JavaScript-Dateien und Ausdrücke aus .phtml-Dateien nicht in die Übersetzungsdatei aufnehmen, was zu unvollständigen oder falschen Übersetzungen führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AKP2E-2957_: Galerie in PageBuilder zeigt anstelle des neu hochgeladenen Bildes alte Miniaturansicht an
   * _Hinweis korrigieren_: Erstellen Sie eine Bildvorschau für Bilder, die gelöscht und neu hochgeladen wurden, mit demselben Namen über die Mediengalerie im Seitenaufbau-Inhalt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _AC-11588_: Die Datenvalidierung ist erfolgreich und während des Imports ist die Schaltfläche &quot;Importieren&quot;für Produkte mit Ersetzungsverhalten vorhanden
   * _Hinweis reparieren_: Das System validiert jetzt Daten korrekt und blendet die &quot;Import&quot;-Schaltfläche während des Produktimportierungsprozesses mit dem Verhalten &quot;Ersetzen&quot;aus, wodurch unbeabsichtigtes Ersetzen von Daten verhindert wird. Zuvor hat das System die Daten falsch validiert und die Schaltfläche &quot;Importieren&quot;angezeigt, was zu möglichen Dateninkonsistenzen führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AKP2E-3125_: Problem mit Vorlage zum Zurücksetzen des Kennworts für Admin-Benutzer
   * _Hinweis korrigieren_: Das Problem wurde behoben, indem der richtige Schlüssel verwendet wurde, der jetzt den Benutzernamen des Administrators in die E-Mail-Vorlage enthält und den Betreff ordnungsgemäß ausfüllt. Zuvor war das Problem auf einen veralteten Schlüssel zurückzuführen, der verwendet wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _AKP2E-3037_: Überprüfungsmeldung für die Checkout-Seite ist falsch.
   * _Hinweis reparieren_: Wenn ein erforderliches Feld leer gelassen wird, z. B. &quot;Adresse&quot;, wird die Meldung bei der serverseitigen Validierung nicht angezeigt. Die clientseitige Validierung stellt sicher, dass die erforderliche Feldfehlerbenachrichtigung mit der Meldung &quot;Dies ist ein erforderliches Feld&quot;angezeigt wird. Zuvor wurde zusätzlich zur clientseitigen Validierungsmeldung die Meldung &quot;Adresse ist erforderlich&quot;angezeigt, wenn ein erforderliches Feld leer gelassen wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _AKP2E-2847_: Favicon-Upload schlägt fehl, *.ico-Dateien zu validieren
   * _Hinweis korrigieren_: Der Fehler bei der Dateivalidierung wurde in &quot;File validation failed&quot;aktualisiert. Überprüfen Sie die Bildverarbeitungseinstellungen in der Speicherkonfiguration.&quot; Zuvor war es einfach &quot;Dateivalidierung fehlgeschlagen&quot;.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AC-12167_: [Fehler] Magento 2.4.7 lässt keine Produktefotos mit großgeschriebener Dateierweiterung zu.
   * _Hinweis korrigieren_: Das System akzeptiert jetzt Produktimages-Uploads mit Dateierweiterungen für Großbuchstaben, um eine reibungslose Produkterstellung zu gewährleisten. Zuvor wurden Bild-Uploads mit Dateierweiterungen für Großbuchstaben abgelehnt, was die Benutzer zwang, die Dateierweiterung in Kleinbuchstaben zu ändern.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8f87c25>

### Admin-Benutzeroberfläche, Leistung

* _AKP2E-3169_: Nach der Aktualisierung auf 2.4.5-p8 treten beim Erstellen einer Bestellung durch den Administrator 500 Fehler auf
   * _Hinweis korrigieren_: Beim Aktivieren der HTML-Minimierung konnte bisher keine Bestellung des Administrators platziert werden. Mit aktivierter HTML-Minimierung kann die Bestellung des Administrators erfolgreich platziert werden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin-Benutzeroberfläche, Versand

* _AKP2E-2519_: Die Anzahl der Gutscheincodes wird im   Spalte &quot;Verwendete Zeit&quot;auf der Registerkarte Coupon-Codes verwalten , wenn eine Bestellung mit mehreren Sendungen aufgegeben wird.
   * _Hinweis reparieren_: Zuvor wurde bei einer Bestellung mit mehreren Sendungen die Anzahl der Couponcodes in der Spalte &quot;Verwendete Zeit&quot;auf der Registerkarte &quot;Couponcodes verwalten&quot;nicht aktualisiert. Jetzt wird die richtige Anzahl sowohl in der &quot;Verwendeten Zeit&quot;angezeigt, die die gewünschten Werte mit Mehrfachversand widerspiegelt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/4745100c>

### Analytics/Reporting

* _AKP2E-2570_: Vorangehender Bericht funktioniert nicht
   * _Hinweis korrigieren_: Das System unterstützt jetzt die Generierung von erweiterten Berichtsdatendateien für extra große Datensätze, indem Berichte in Stapeln von 10.000 geladen und geschrieben werden. Zuvor konnte das Modul &quot;Fortschrittliche Berichterstellung&quot;keine Datendateien für extra große Datensätze generieren, was während der Ausführung des Cron-Auftrags analytics_collect_data zu &quot;MySQL Server has away&quot;-Fehlern führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _AC-9922_: Google Analytics CSP-Fehler https://region1.analytics.google.com
   * _Hinweis reparieren_: Das System lässt jetzt korrekt Verbindungen zu &quot;https://region1.analytics.google.com&#39; zu, wenn Google Analytics aktiviert ist, was CSP-Fehler (Content Security Policy) verhindert. Früher führte die Aktivierung von Google Analytics und die Anzeige der Website aus der EU zu CSP-Konsolenfehlern, da die Verbindung zu &quot;https://region1.analytics.google.com&#39;&quot;verweigert wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38991>
* _AKP2E-3096_: Falsche Curl-Kopfzeilen, die den neuen &quot;:create:deploy-marker&quot; nicht verwenden
   * _Hinweis reparieren_: Das System formatiert jetzt die Curl-Kopfzeilen korrekt, sodass der neue lische :create:deploy-marker-Befehl erfolgreich eine Bereitstellungsmarke in New Relic erstellen kann. Zuvor wurde die Erstellung einer Implementierungsmarke in New Relic durch falsche curl-Header verhindert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _AKP2E-3080_: Problem mit der Sichtbarkeit des Datumsbereichs des Berichts &quot;Bestellte Produkte für Administratoren&quot;.
   * _Hinweis korrigieren_: Der Benutzer kann ein beliebiges Datum aus dem Bericht &quot;Bestellte Produkte&quot;auswählen. Zuvor wurde nach einer Tabellenaktualisierung durch Auswahl des Datums &quot;VON&quot;das Datum &quot;BIS&quot;zurückgesetzt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6f4805f8>

### Analytics/Reporting, B2B

* _AKP2E-2300_: B2B - Sitemap enthält Produkte/Kategorien, die nicht dem gemeinsamen Katalog zugeordnet sind
   * _Hinweis korrigieren_: Schränken Sie die Sitemap-generierten Kategorien und Produkte auf die Kategorien und Produkte ein, die nur dem öffentlich freigegebenen Katalog und / oder der Einrichtung der Katalogkategorie zugewiesen sind.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Reporting, Cloud

* _AKP2E-3067_: Magento verwirft die meisten New Relic-Cron-Transaktionen #34108
   * _Korrektur des Hinweises_: AC meldet ordnungsgemäß cron-auftragsbezogene Transaktionen an NewRelic. Zuvor wurden einige Cron-Auftrags-bezogene Transaktionen in NR als &quot;OtherTransaction/Action/unknown&quot;(Andere Transaktion/Aktion/Unbekannt) angezeigt
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _AKP2E-3044_: Unnötige Rahmen für den Abschnitt &quot;Meine Bestellungen&quot;
   * _Hinweis korrigieren_: Zuvor wurde ein zusätzlicher Container (Bestellverweise) erstellt, der zusätzliche CSS-Klassen anwendete, was dazu führte, dass unter der Bestellnummer im Abschnitt &quot;Meine Bestellungen&quot;unnötige Randlinien angezeigt wurden, was jetzt nicht sichtbar ist.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, Framework

* _AC-9607_: Das Filtern des Unternehmensrasters und das anschließende Erstellen eines CSV-Exports mit dem Raster schlagen fehl und lösen eine Ausnahme aus
   * _GitHub-Codebeitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>

### Warenkorb und Checkout

* _AKP2E-2664_: [Cloud] Parallele Produktanfragen zum Hinzufügen desselben Produkts zum Warenkorb führen zu zwei separaten Elementen in der Warenkorbabruf-API
   * _Hinweis reparieren_: Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzelnen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führten parallele Anfragen zum Hinzufügen desselben Produkts zum Warenkorb über die REST-API zu mehreren Zeileneinträgen für dieselbe SKU.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _AKP2E-2704_: Das Cookie kann nicht gesendet werden. Größe der &#39;Bildnachrichten&#39; beim Versuch, die Reihenfolge neu anzuordnen
   * _Hinweis korrigieren_: Der Neuanordnungsprozess erzeugt jetzt keine eigenen Fehler mehr. Dabei werden integrierte Elementprüfungen für die Warenkorbliste benötigt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _AC-11876_: [Problem] Regression der Verkaufsregeln in 2.4.7
   * _Hinweis reparieren_: Das System validiert jetzt die Verkaufsregeln ordnungsgemäß, wodurch die Anwendung eines Gutscheincodes auf einen Warenkorb verhindert wird, wenn die Produktbedingung mit keinem Produktnamen übereinstimmt. Zuvor konnte eine Verkaufsregel angewendet und ein Rabatt auf den Versandbetrag gewährt werden, selbst wenn die Produktbedingung keinem Produktnamen entsprach.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38671>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AKP2E-2798_: Die standardmäßige Versandadresse wird beim Checkout nicht ausgewählt
   * _Hinweis reparieren_: Die standardmäßige Versandadresse wird jetzt im Kontext der aktivierten Adressensuche ausgewählt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _AKP2E-2518_: Durch die Neuanordnung wird ein nicht zugewiesenes Produkt zum Warenkorb hinzugefügt.
   * _Hinweis korrigieren_: Zuvor können Produkte für die verschiedenen Stores aus dem anderen Store neu angeordnet werden. Nachdem diese Korrektur nur auf denselben Store angewendet wurde, kann dasselbe Scope-Produkt neu angeordnet werden, wenn die Kundenkontofreigabe aktiviert ist
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _AKP2E-2923_: Beim Checkout als neuer Kunde wurden dem Konto mehrere Adressen hinzugefügt.
   * _Hinweis reparieren_: Das System speichert jetzt eine neue Kundenadresse nur einmal, wenn die Bestellung nicht erstellt werden konnte. Dadurch wird verhindert, dass im Falle von Fehlern bei der Bestellplatzierung mehrere identische Adressen erstellt werden. Zuvor hat das System bei jedem Bestellplatzierungsversuch eine neue Adresse gespeichert, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _AKP2E-2897_: [CLOUD] graphql addProductsToCart API-Problem mit benutzerdefinierter Option
   * _Hinweis reparieren_: GraphQL fügt dasselbe Produkt mit verschiedenen benutzerdefinierten Optionen korrekt zum Warenkorb hinzu
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _AKP2E-2470_: Dauerhafter Warenkorb beim Checkout-Schritt gelöscht
   * _Hinweis reparieren_: Nach der Korrektur wird die persistente Sitzung nicht beendet, wenn die Zahlungsmethode beim Checkout ausgewählt wird, während sie nicht angemeldet ist.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _AC-11993_: [Problem] Der Lader blockiert die Versandmethoden, nachdem der Postcode geändert wurde, Validierungsregeln für Versandraten.
   * _FEHLER HINWEIS_: Das System handhabt jetzt benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandkosten und stellt sicher, dass der Lader die Versandmethoden nicht blockiert, nachdem die Postleitzahl während des Checkout in der Lieferadresse geändert wurde. Zuvor führte eine Änderung der Postleitzahl in der Lieferadresse während des Checkout dazu, dass der Ladevorgang die Versandmethoden blockierte und nicht verschwand, wenn benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten verwendet wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AKP2E-3025_: Admin-Benutzer mit eingeschränkten Rollenressourcen, der keine Warenkorb anzeigen kann
   * _Hinweis korrigieren_: Zuvor konnte der eingeschränkte Administrator den abgebrochenen Warenkorb nicht im Admin-Bedienfeld einer zugehörigen Website sehen. Nachdem diese Korrektur angewendet wurde, kann der eingeschränkte Administrator den abgebrochenen Warenkorb im Admin-Bedienfeld sehen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _AC-11641_: [Problem] [Checkout] Abhängige Anweisungen, die in der E-Mail-Vorlage für fehlgeschlagene Zahlungen aktualisiert wurden
   * _Hinweis reparieren_: Das System lässt die Versandadresse und die Versandmethode für virtuelle Produkte nun korrekt aus der fehlgeschlagenen E-Mail-Vorlage für Zahlungen aus, wodurch sichergestellt wird, dass nur relevante Informationen in der E-Mail enthalten sind. Zuvor enthielt die fehlgeschlagene E-Mail mit der Zahlung für virtuelle Produkte fälschlicherweise die Versandadresse und die Versandmethode.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32781>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/32511>
* _AC-10698_: GTag sendet keine Transaktionspreise und -summen.
   * _Fehlerbehebung_: Das System sendet jetzt die Transaktionspreise und -summen korrekt an das Google-Tag, wenn GTag aktiviert ist. Dadurch wird eine genaue Nachverfolgung der E-Commerce-Daten sichergestellt. Zuvor wurde die Währung fälschlicherweise als Teil der &quot;Alle&quot;-Bestellungen gesendet, anstatt mit der einzelnen Bestellung verknüpft zu sein.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37348>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AKP2E-2646_: [Cloud] Verkaufsregel, die nicht auf die erste Bestellung von Multi Shipping angewendet wird
   * _Hinweis reparieren_: Nach der Korrektur wird der Rabatt für jede Bestellung des gleichen Multi-Versandangebots korrekt angezeigt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _AKP2E-3004_: Die Neuanordnung der Kundenbestellung über das Formular für Gastbestellungen führt zu einem leeren Warenkorb
   * _Hinweis reparieren_: Zuvor wurde der Kunde beim Platzieren einer Neubestellung über die Seite &quot;Bestellungen und Rückgaben&quot;zur Anmeldeseite umgeleitet. Nachdem diese Korrektur angewendet wurde, wird der registrierte Kunde beim Platzieren einer Neubestellung korrekt zur Seite Warenkorb anzeigen weitergeleitet. Der Fluss funktioniert genauso wie bei Gastkunden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _AKP2E-2055_: Duplizieren Sie Bestellungen mit derselben Anführungszeichen-ID gleichzeitig mit wenigen Zeitunterschieden
   * _Hinweis korrigieren_: Problem behoben, das auftrat, wenn Adobe Commerce-Kunden doppelte Bestellungen mit derselben Quote-ID aufriefen
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _AKP2E-2620_: In Admin wird der &quot;Warenkorb&quot;auf der linken Seite nicht aktualisiert, wenn Sie die Artikel auswählen und &quot;Zum Warenkorb wechseln&quot;von der rechten Seite aus
   * _Hinweis reparieren_: Der &quot;Warenkorb&quot;auf der linken Seite wird aktualisiert, wenn Sie die Elemente auswählen, und &quot;Zum Warenkorb wechseln&quot;von der rechten Seite auf der Admin-Seite. Zuvor funktionierte diese Funktion nicht, da die umgewandelten Warenkorbelemente nicht aus der Sitzung gelöscht wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AC-10660_: Die Ausnahme wird beim Hinzufügen eines Produkts zum Warenkorb auf der Seite &quot;Vergleichsprodukt&quot;nicht ordnungsgemäß verarbeitet
   * _Hinweis reparieren_: Das System handhabt nun beim Hinzufügen eines Produkts zum Warenkorb von der Seite des Vergleichsprodukts ordnungsgemäß Ausnahmen und zeigt eine Meldung des Nachrichtenmanagers im Controller an. Zuvor führte eine Ausnahme dazu, dass eine JSON-kodierte Seite zurückgegeben wurde, anstatt ordnungsgemäß erfasst und verarbeitet zu werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38200>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-12170_: Die Funktion &quot;Couponcode&quot;funktioniert auf der Checkout-Seite auf Magento 2.4.7 nicht ordnungsgemäß
   * _Hinweis korrigieren_: Das System aktiviert jetzt das Eingabefeld für Rabattcode/Gutschein auf der Checkout-Seite für virtuelle und herunterladbare Produkte, sodass Benutzer wie erwartet Rabattcodes anwenden können. Zuvor war die Eingabe des Rabattcodes/Gutscheins deaktiviert und der Text des Schaltflächentitels wurde als &quot;Coupon abbrechen&quot;angezeigt, was Benutzer daran hinderte, Rabattcodes anzuwenden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/1bafc571>

### Warenkorb &amp; Auschecken, Auschecken/Auschecken einer Seite

* _AC-9386_: [Zufälliger BUG] Das E-Mail-Feld wird nicht gerendert oder es dauert lange, bis es auf der Checkout-Versand- oder Zahlungsseite angezeigt wird.
   * _Fix note_: Commerce rendert jetzt das **[!UICONTROL Email]** -Feld auf den Checkout-Versand- und Zahlungsseiten wie erwartet. Zuvor war dieses Feld entweder nicht vorhanden oder wurde langsam gerendert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/e1babcfd>

### Warenkorb &amp; Checkout, Bestellung

* _AKP2E-3097_: Datumsauswahl für ein Produkt mit mehreren anpassbaren Optionen, wobei Datumsfelder bei der Bestellung durch einen Administrator nicht funktionieren
   * _Hinweis korrigieren_: Das System zeigt jetzt beim Konfigurieren eines Produkts mit mehreren anpassbaren Datumsoptionen im Prozess zur Erstellung der Admin-Reihenfolge die Datumsauswahl für alle Datumsfelder korrekt an. Zuvor wurde die Datumsauswahl nur für das erste Datumsfeld angezeigt, wobei die übrigen Felder ohne Datumsauswahl blieben.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Warenkorb &amp; Checkout, Versand

* _AC-12119_: Sofortiger Kauf &quot;billigster Versand&quot;für konfigurierbare Produkte unterbrochen
   * _FEHLER HINWEIS_: Die Funktion &quot;Sofortiger Kauf&quot;hat fälschlicherweise die teurere Option &quot;In-Store-Versand&quot;für konfigurierbare Produkte anstelle der günstigsten Methode &quot;Pauschalpreis&quot;ausgewählt. Mit dieser Korrektur wird sichergestellt, dass die richtige Versandmethode basierend auf dem tatsächlichen Preis ausgewählt wird.&quot;
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38811>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Katalog

* _AKP2E-2871_: [Cloud] Der Händler hat Probleme mit der Anzahl der Wunschlisten
   * _FEHLER-Hinweis_: Das Hinzufügen eines Produkts zur Wunschliste in einem Store erhöht nicht mehr die Anzahl der Wunschlisten in anderen Geschäften, die im selben Browser geöffnet sind. Wenn zuvor beide Stores im selben Browser geladen wurden, stieg auch die Anzahl der Wunschlisten im anderen Store.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _AKP2E-2843_: Produkte an der Vorderseite verwenden Store-spezifische Daten, wenn der Einzelspeicher-Modus aktiviert ist.
   * _Hinweis korrigieren_: Bisher wurden die Änderungen nicht zum Bereich auf Website-Ebene migriert, wenn wir den Einzelspeichermodus für die standardmäßige Store-Ansicht aktiviert hatten. Nach der Anwendung dieser Korrektur werden die standardmäßigen Store-Ansichtsdaten mit spezifischen Daten auf Website-Ebene synchronisiert und die möglichen Konflikte für Produkte und Kategorien gelöst, wenn der Einzelspeichermodus aktiviert wird.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _AKP2E-2857_: &quot;Standardsortierung nach&quot;kann nicht in einer Kategorie mit der Rest-API festgelegt werden
   * _Hinweis reparieren_: Aktualisieren Sie default_sort_by für eine Kategorie über REST-/SOAP-API-Anfrage korrekt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _AC-10910_: Die Bereinigung der Datenbanktabelle cron_schedule bereinigt nicht vorhandene Aufträge nicht
   * _Hinweis reparieren_: Das System bereinigt jetzt automatisch die Datenbanktabelle cron_schedule und entfernt Einträge für Aufträge, die nicht mehr im System vorhanden sind. Dies gewährleistet eine optimale Leistung, indem eine minimale Anzahl von Zeilen in der Tabelle beibehalten wird. Zuvor wurden Einträge für Aufträge aus inaktiven oder entfernten Modulen nicht bereinigt, was zu einer unnötigen Datenakkumulation in der Tabelle cron_schedule führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38693>
* _AKP2E-3136_: [Cloud] Die Elemente der Unterkategorie werden in der Widget-Bearbeitung im Admin-Backend nicht angezeigt
   * _Hinweis korrigieren_: In der Kategorienstruktur auf der neuen Widget-Seite sollten keine Probleme mehr beim Laden von Kategorie-5+-Kategorien auftreten. Zuvor fehlten einige Kategorien beim Laden des Baums über Kategorie 5 hinaus.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _AC-10953_: Der Statuspreis wird nicht aus dem konfigurierbaren Produkt gelöscht
   * _Hinweis korrigieren_: Das System entfernt jetzt den Stufenpreis eines Produkts korrekt, wenn es von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wird, und gewährleistet so eine genaue Preisanzeige an der Vorderseite. Zuvor wurde der Stufenpreis eines konfigurierbaren Produkts nicht gelöscht, wenn ein Produkt aus einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wurde, was zu einer Diskrepanz beim angezeigten Preis führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38427>
* _AKP2E-3126_: [Cloud] Die GQL-Antwort der Produktmedien-Galerie wird nicht nach Bildposition sortiert
   * _Hinweis reparieren_: Das System sortiert Elemente in der Mediensalerie nun korrekt nach Position in der GraphQL-Antwort, wodurch eine genaue Anzeigereihenfolge gewährleistet wird. Zuvor wurden Elemente in der Mediengalerie nicht nach Position sortiert, was zu einer falschen Anzeigereihenfolge führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _AKP2E-3100_: [Cloud] Bilddatei ist nicht im New Relic-Fehlerprotokoll vorhanden
   * _FEHLER-Hinweis_: Das System synchronisiert jetzt benutzerdefinierte Platzhalterbilder mit dem lokalen Speicher, um sicherzustellen, dass sie bei Verwendung von Remote-Speicher wie AWS S3 korrekt dargestellt werden. Bisher konnten benutzerdefinierte Platzhalterbilder bei Verwendung von Remote-Speicher nicht gerendert werden, was zu einer fehlerhaften Bildanzeige und Fehlerprotokollen führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _AC-11804_: Kategoriebeschreibung WYSIWYG ist bei nicht standardmäßiger Storeüberprüfung leer
   * _Hinweis reparieren_: Das System speichert jetzt beim Bearbeiten einer Kategorie auf der Store-Ansichtsebene die Kategoriebeschreibung korrekt und zeigt sie im WYSIWYG-Editor an. Zuvor wurde der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf der Store-Ansichtsebene leer angezeigt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38622>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38623>
* _AC-12076_: [Problem] Korrektur des Wortlauts des Filterelements für die mehrteilige Navigation
   * _Hinweis korrigieren_: Das System verwendet nun die Wörter &quot;Element&quot;und &quot;Elemente&quot;im Navigationsfilterelement mit Ebenen korrekt, wodurch die Klarheit und Genauigkeit der Filterbeschreibungen verbessert wird. Zuvor wurden diese Wörter falsch verwendet, was zu Verwirrungen bei Benutzern führte, die in den Filteroptionen navigierten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Datum- und Uhrzeitformat für die benutzerdefinierte Option funktioniert nicht
   * _Hinweis reparieren_: Das System wendet jetzt das konfigurierte Datumsformat korrekt auf benutzerdefinierte Produktoptionen des Typs &quot;Datum&quot;an, um sicherzustellen, dass das Datumsformat korrekt auf dem Front-End angezeigt wird. Bisher wurden Änderungen an der Konfiguration des Datumsformats nicht am Front-End für benutzerdefinierte Produktoptionen des Typs Datum übernommen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38925>
* _AKP2E-3076_: Fehler beim Löschen von Bundle-Optionen
   * _Hinweis reparieren_: Das System löscht jetzt die Bundle-Optionen korrekt, ohne einen Fehler auszulösen oder die Seite nicht mehr responsiv zu machen. Zuvor führte der Versuch, Bundle-Optionen zu löschen, zu einem Fehler &quot;Seite nicht reagiert&quot;und verhinderte, dass das Produkt gespeichert wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _AKP2E-3069_: Kunden sehen Preise von anderen Kundengruppen
   * _Hinweis korrigieren_: Problem behoben, aufgrund dessen Informationen zur Kundengruppe aufgrund des alten Werts der X-Magento-Vary in der Anfrage in einem falschen Segment gespeichert wurden
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _AKP2E-3058_: Fehlende Beschriftung in LayeredNavigation mit Optionsname 0
   * _Hinweis reparieren_: Das Problem wurde behoben, indem eine leere Wertprüfungsmethode für den Attributwert 0 übersprungen wurde. Zuvor wurde es als leer betrachtet und verursachte das Problem.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _AC-6738_: Fehlender eindeutiger Schlüssel in der Tabelle eav_attribute_option_value
   * _Hinweis reparieren_: Das System enthält jetzt einen eindeutigen Schlüssel für die Spalten &quot;option_id&quot;und &quot;store_id&quot;in der Tabelle &quot;eav_attribute_option_value&quot;, wodurch die Möglichkeit ausgeschlossen wird, dass eine Option mehrere Werte für dieselbe Store-Ansicht hat. Zuvor konnte fehlerhafter Code dazu führen, dass eine Option mit mehreren Werten für dieselbe Store-Ansicht vorhanden war, was Probleme bei der Bearbeitung von Produkten oder Attributen verursachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/24718>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Problem] Verwenden Sie die Sichtbarkeitsklasse für den Kategorieproduktindex anstelle von fest codierten Werten.
   * _Hinweis korrigieren_: Das System verwendet jetzt die Sichtbarkeitsklasse für den Kategorieproduktindizierer anstelle von fest codierten Werten, wodurch die Modularität verbessert wird. Zuvor wurden im Kategorieproduktindex fest codierte Werte verwendet, was die Flexibilität und Anpassungsfähigkeit einschränkte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37200>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: Währungscode wird im neuen Produkt-Widget nicht geändert
   * _Hinweis reparieren_: Das System aktualisiert jetzt den Währungscode im Widget &quot;Neues Produkt&quot;korrekt, wenn die Währung im Frontend geändert wird, und stellt so sicher, dass die Währungsanzeige auf der gesamten Site einheitlich ist. Bisher hatte eine Änderung der Währung im Frontend keine Auswirkungen auf den Währungscode, der im Widget Neues Produkt angezeigt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37899>
* _AKP2E-3029_: [Cloud] Mobiles Problem nur mit Pinch-Gesten auf das PDP-Bild
   * _FEHLERBEHEBUNG_: Das System unterstützt jetzt Pinch-to-Zoom-Funktionen für Produktdetailseiten-Bilder in der Mobile-Ansicht in Chrome, wodurch das Benutzererlebnis für Mobilgeräte verbessert wird. Zuvor wurde das Bild beim Doppeltippen auf das Bild in der Mobile-Ansicht in Chrome nicht wie erwartet vergrößert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _AKP2E-2224_: Der reguläre Preis wird nicht auf PLP für konfigurierbare Produkte angezeigt
   * _FEHLER-Hinweis_: Der reguläre Preis wird jetzt auf Produktlistenseiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreis angezeigt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _AKP2E-2478_: Lagerinformationen werden nicht direkt im Visual Merchandising-Raster angezeigt
   * _Fixe Anmerkung_: Der Lagerbestand wird jetzt entsprechend dem ausgewählten Store angezeigt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _AKP2E-3009_: async.operations.all wurde ausgeführt und ein Fehler erstellt.
   * _Hinweis korrigieren_: Falsche Produktlinkdaten in REST-API-Aufrufen verursachen keine kritischen Fehler mehr.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _AKP2E-2621_: Der Widget-Inhalt wird auf der cms-Seite nicht aktualisiert
   * _Hinweis reparieren_: Das System aktualisiert jetzt den Widget-Inhalt auf einer CMS-Seite, wenn ein Produkt als neu und gespeichert festgelegt wird, und stellt sicher, dass auf der Seite die aktualisierte Produktsammlung angezeigt wird. Zuvor wurde die Seite aufgrund der falschen Cache-Identitäten, die für das Widget im Cache verwendet wurden, nicht aktualisiert, um das neue Produkt anzuzeigen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _AKP2E-2630_: Probleme, durch die erweiterte Preise für Bundle-Produkte gespart werden
   * _Hinweis reparieren_: Leistungsverbesserung beim Produktsparen im Paket.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _AKP2E-2652_: [On-Premise] Der Neuindizierungsprozess ist beim Erstellen von Katalogpreisregeln ineffizient.
   * _Hinweis korrigieren_: Beim Speichern der Katalogpreisregel werden Indexer jetzt nicht invalidiert. Stattdessen werden nur die betroffenen Produkte neu indiziert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _AKP2E-2964_: [Cloud] URL-Update nur für store_id=0
   * _Hinweis korrigieren_: Der &quot;URL-Pfad&quot;wird jetzt mit der richtigen Store-ID gespeichert. Zuvor war die Store-ID falsch, was dazu führte, dass beim Verschieben von Kategorien falsche URL-Pfade in der Datenbank verblieben.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _AKP2E-2679_: Aktualisieren der Zeit der Produktattribute vom Typ Datum und Uhrzeit über einen CSV-Import
   * _Hinweis reparieren_: Jetzt haben Datums-/Uhrzeitattribute eine Zeitunterteilung in exportierte Daten. Es ist auch möglich, die Zeit für solche Attribute mithilfe des Imports zu aktualisieren. Wenn &quot;Feldeinteilung&quot;aktiviert ist, werden die Attributwerte in der Spalte &quot;additional_attributes&quot;in doppelte Anführungszeichen gesetzt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38306>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _AKP2E-2689_: Keine geeignete Fehlermeldung, wenn die Website-ID in der Anfrage falsch ist
   * _Hinweis korrigieren_: Jetzt wurde die entsprechende Fehlermeldung hinzugefügt, die angezeigt wird, wenn die Website-ID in der Anfrage falsch ist. Zuvor gab es keine Validierung, wenn die Website-ID in der Anfrage falsch war.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AKP2E-2956_: YouTube-Fehler beim Hinzufügen von Videos
   * _Fehlerbehebung_: Produktbilder und Videos werden global konfiguriert. Da Sie kein Produktvideo in einem Bereich und nicht in einem anderen haben können, wurde die Einstellung des YouTube-API-Schlüssels auf den globalen Umfang gesetzt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _AKP2E-2950_: [Cloud] Bundle-Produkt: falsche Preise zur Bestellbestätigung
   * _Hinweis korrigieren_: Für Bundle-Optionen wird der richtige Betrag in der Reihenfolge auf der Storefront angezeigt, wenn eine andere Währung als die Basiswährung verwendet wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _AKP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice beim Bearbeiten von Bundle-Produkten
   * _Hinweis korrigieren_: Beim Löschen der Option aus dem Bundle-Produkt gibt es keinen JavaScript-Fehler in der Browser-Konsole.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _AKP2E-2905_: [Cloud] Anführungsthema in der Architektur mit mehreren Websites
   * _Korrektur des Hinweises_: Bisher konnte die Architektur mehrerer Websites mit unterschiedlichen Währungen und Kundengruppen Rabatte nicht ordnungsgemäß auf den Store anwenden. Nachdem diese Korrektur implementiert wurde, wird die Multi-Website-Architektur mit unterschiedlichen Preisnachlässen für Kundengruppen erfolgreich auf verschiedene Stores angewendet.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38506>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _AKP2E-2785_: Das Produktbild geht verloren, nachdem ein vorhandenes geplantes Update gelöscht wurde, das sich nicht auf das Bild auswirkt
   * _Hinweis korrigieren_: Produktbilder werden beim Löschen der Staging-Aktualisierung nicht entfernt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _AKP2E-2799_: [Cloud] Falscher Paket-Produktpreis bei Verwendung mit Tier-Preisen
   * _Hinweis korrigieren_: Bisher werden bei der Berechnung bestimmter auf 2 Dezimalstellen aufgerundeter prozentualer Rabatte unterschiedliche Endpreise für die Seite mit den Warenkorb- und Produktlistungsdetails generiert. Nach Anwendung dieser Korrektur ist der Endpreis für das Bundle-Produkt derselbe wie auf der Seite mit den Produktdetails, auf der Seite mit der Produktliste und auf der Mini-Warenkorbseite.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _AKP2E-2805_: Katalogförderungsregel funktioniert nicht mit dem Attribut quantity_and_stock_status
   * _Hinweis korrigieren_: Das Attribut quantity_and_stock_status wird jetzt von der Katalogförderungsregel berücksichtigt, die zuvor beim Generieren eines neuen Produkts von der Admin-Seite nicht berücksichtigt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35627>
   * _GitHub-Codebeitrag_: <https://github.com/magento/inventory/commit/cf34971d>
* _AKP2E-2874_: Die Kategorieseite am Frontend zeigt bei Verwendung des Bundle-Produkts leere Slots an
   * _Hinweis korrigieren_: Bundle-Produkte, die im aktuellen Store-Kontext nicht verkäuflich sind, werden nicht mehr indiziert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/inventory/commit/bc37ec76>
* _AKP2E-2837_: Die Spaltenwerte der Produktidentität &quot;updated_at&quot;werden beim Aktualisieren des Preises über die REST-API nicht aktualisiert.
   * _Hinweis korrigieren_: Die Spalte &quot;Zuletzt aktualisiert am&quot;des Administrators enthält die richtige Datumszeit, während die vorhandenen Produkte über die REST-API aktualisiert werden. Zuvor wurde die Spalte &quot;zuletzt aktualisiert am&quot;nicht ordnungsgemäß aktualisiert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AKP2E-2840_: Es ist möglich, nicht eindeutige Werte über den Produktimport festzulegen.
   * _Hinweis reparieren_: Das System erzwingt jetzt beim Produktimport die Beschränkung eindeutiger Werte für eindeutige Produktattribute ordnungsgemäß, wodurch verhindert wird, dass für dieses Attribut doppelte Werte vorhanden sind. Zuvor war es möglich, nicht eindeutige Werte für Produktattribute festzulegen, die über den Produktimport so konfiguriert wurden, dass sie eindeutige Werte aufweisen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38445>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/7e0e5582>

### Katalog, Framework

* _AKP2E-2949_: [Cloud]Follow-up: Bei der Überprüfung, ob Daten Änderungen aufweisen, wird im Datenvergleich keine Übereinstimmung festgestellt
   * _Hinweis korrigieren_: Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für numerische Datenfelder wie int/float/double). Dadurch wird das Flag _hasDataChanges auf &quot;true&quot;Trigger und die Speicherfunktion aufgerufen. Außerdem werden die schwebenden Zahlen, die von einer Zeichenfolge eingekapselt sind, nicht überprüft. Nachdem diese Korrektur angewendet wurde, ruft die Speicherfunktion nur auf, wenn die Daten geändert wurden. Der Datenwert für int/float/doubleCheck mit dem Wert, der an die Funktion übergeben wird, und nimmt eine strikte Typübereinstimmung vor
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8931218>

### Katalog, GraphQL

* _AKP2E-3090_: Umgang mit Kategoriefiltern in GraphQL: includeDirectChildrenOnly und category_uid
   * _Hinweis korrigieren_: Beim Filtern nach category_uid werden nur die direkt untergeordneten Kategorien abgerufen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/93d50f8d>

### Katalog, Preise, Staging und Vorschau

* _AKP2E-2672_: [Cloud] Der API-Endpunkt für Sonderpreise gibt beim gleichzeitigen Aktualisieren einer großen Anzahl von Produkten einen Fehler zurück
   * _Hinweis reparieren_: Die Bulk-Update-API für spezielle Preise erstellt jetzt für jeden Datumsbereich eine einzige Kampagne anstelle mehrerer geplanter Aktualisierungen für jedes Produkt und jeden Datumsbereich. Außerdem unterstützt es gleichzeitige API-Anfragen für eine schnellere Verarbeitung einer großen Anzahl von SKUs.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/f89a447e>

### Katalog, Produkt

* _AC-7050_: Die Kategorieauswahlstruktur im bearbeiteten Produkt befindet sich nicht in der gleichen Reihenfolge wie unter Katalog->Kategorien
   * _Hinweis reparieren_: Das System zeigt nun die Kategorieauswahl im Produktbearbeitungsabschnitt korrekt in der unter Katalog->Kategorien festgelegten Reihenfolge an, wodurch die Produktverwaltung in großen Katalogen vereinfacht wird. Zuvor wurde die Kategorienstruktur im Produktbearbeitungsabschnitt in der Reihenfolge der Kategorienerstellung angezeigt, unabhängig von der Anzeigeposition unter Katalog->Kategorien.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/36104>

### Katalog, Suche

* _AKP2E-3053_: [Cloud] Elastischer Suchfehler auf bestimmten Kategorieseiten
   * _Hinweis reparieren_: Zuvor wurde mit dem erwähnten Konfigurationticket beim Festlegen des Preises 0 für mehrere Produkte eine Ausnahme auf der Frontend-Kategorieseite ausgegeben. Nach dieser Korrektur, die angewendet wird, wenn mehrere Produktpreise 0 und wir Kategorie-Seite an Frontend laden, wird keine Ausnahme ausgelöst und die Kategorieseite wird erfolgreich geladen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _AKP2E-2757_: Produkte, die nicht in Kategorie und Suche angezeigt werden, aber direkte Links funktionieren
   * _Hinweis korrigieren_: Zuvor funktionierte das benutzerdefinierte Attribut Ja/Nein mit dem Wert Preis_* Attribut_Code nicht mit der Indizierung. Nach dieser Korrektur funktioniert das benutzerdefinierte Attribut Ja/Nein erwartungsgemäß.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>

### Cloud

* _AKP2E-3010_: [Cloud] PHPSESSID ändert die einzelnen POST-Anfragen
   * _FEHLER-Hinweis_: PHPSESSID wird bei POST-Anforderungen im Frontend-Bereich für einen angemeldeten Kunden nicht mehr neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde vom Backend aktualisiert wurde
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6a185204>

### Inhalt

* _AC-9638_: [Problem] Problem beim Hochladen von Dateien im WYSIWYG-Editor auf der Produktseite
   * _Hinweis korrigieren_: Das System zeigt nun die Ordnerstruktur korrekt an und ermöglicht das Hochladen von Bildern im WYSIWYG-Editor auf der Produktseite, selbst wenn die Registerkarte &quot;Bilder und Videos&quot;zuerst erweitert wurde. Zuvor führte die Erweiterung der Registerkarte &quot;Bild und Videos&quot;zunächst dazu, dass die Ordnerstruktur nicht angezeigt wurde, und eine Fehlermeldung beim Versuch, ein Bild im WYSIWYG-Editor hochzuladen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38025>
* _AKP2E-3064_: Fehler im Seiten-Builder beim Bearbeiten des CMS-Blocks
   * _Hinweis korrigieren_: Das System speichert nun mithilfe von Page Builder vorgenommene Änderungen im Admin-Bereich korrekt, ohne den Fehler &quot;Page Builder hat 5 Sekunden lang gerendert, ohne Sperren freizugeben&quot;. in der Browser-Konsole. Zuvor trat dieser Fehler auf, wenn versucht wurde, Änderungen zu speichern, was die erfolgreiche Aktualisierung von Inhalten verhinderte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _AC-12283_: &quot;Gebietscode nicht festgelegt&quot;nach der Aktualisierung auf 2.4.5-p8
   * _Hinweis korrigieren_: Das System schließt jetzt den Prozess der Bereitstellung statischer Inhalte erfolgreich ab, wenn das Magento_CSP-Modul aktiviert ist und &quot;dev/js/translate_strategy&quot;auf &quot;embedded&quot;gesetzt ist, ohne den Fehler &quot;Area code not set&quot;auszulösen. Zuvor schlug der Prozess der Bereitstellung statischer Inhalte unter diesen Bedingungen mit dem Fehler &quot;Gebietscode nicht festgelegt&quot;fehl.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38845>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38922>
* _AKP2E-2392_: [On-PREM] Problem mit dynamischen Bausteinen
   * _Hinweis korrigieren_: Widgets werden jetzt ordnungsgemäß in dynamischen Blöcken gerendert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _AKP2E-3092_: [CLOUD] Keine Schaltflächen zum Auschecken oder Bearbeiten des Warenkorbs im Warenkorbabschnitt
   * _Hinweis reparieren_: Das Paket-Produkt wird jetzt über Widgets ohne Fehler zum Warenkorb hinzugefügt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _AC-10845_: Pagebuilder-Bannerbild in der Galerie nicht sichtbar
   * _Hinweis korrigieren_: Das System zeigt jetzt korrekt Bannerbilder an, die in neu erstellte Ordner in der Pagebuilder-Galerie hochgeladen wurden, sodass vorherige Konsolenfehler vermieden werden. Vor dieser Fehlerbehebung waren Bannerbilder nicht in der Galerie sichtbar, wenn sie in einen neuen Ordner hochgeladen wurden, was zu einem Konsolenfehler führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AKP2E-2970_: Alte Mediengalerie kann Bilder nicht rendern, wenn ein 0-Byte-Bild im Verzeichnis platziert wird
   * _FEHLER HINWEIS_: Das System verarbeitet jetzt 0-Byte-Bilder in der Mediengalerie, ohne die Funktionalität zu beeinträchtigen. Dadurch können andere Bilder im Verzeichnis erwartungsgemäß angezeigt und ausgewählt werden. Zuvor wurde durch das Vorhandensein eines 0-Byte-Bildes in der Mediengalerie verhindert, dass alle Bilder im Verzeichnis angezeigt oder ausgewählt wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _AKP2E-2842_: Wechseln in den Einzelspeichermodus - globaler Inhalt wird nicht mehr angezeigt
   * _Hinweis reparieren_: Das System synchronisiert beim Aktivieren des Einzelspeichermodus jetzt die Designkonfigurationen für Store-Ansichten mit den Websiteentwurfskonfigurationen, um sicherzustellen, dass Inhaltsaktualisierungen auf der Vorderseite sichtbar sind. Bisher konnte durch Wechseln zum Einzelspeichermodus verhindert werden, dass Inhaltsaktualisierungen auf der Storefront angezeigt wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _AKP2E-2836_: ACP2E-2836: [Cloud] Untersuchungsausnahme im Protokoll gefunden: InvalidArgumentException: Class does not exists in vendor/magento/module-rule/Model/ConditionFactory.php
   * _Hinweis reparieren_: Wenn Sie eine Bedingung in den Inhaltseinstellungen von PageBuilder-Produkten entfernen, wird keine Ausnahme mehr in den Protokolldateien aufgezeichnet. Zuvor führte das Entfernen einer Bedingung in den Einstellungen für den Produktinhalt von PageBuilder dazu, dass eine kritische Ausnahme in den Protokollen aufgezeichnet wurde, obwohl keine Probleme auf der Vorderseite auftraten.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _AKP2E-3127_: imagecreatetruecolor(): Argument #2 ($height) muss größer als 0 sein. Kann kein bestimmtes Bild hochladen
   * _Hinweis korrigieren_: Problem behoben, das beim Hochladen von Bildern mit einer Höhe von 0 über die Mediensalerie Fehler im Admin verursachte und die Asset-Synchronisierung mithilfe des Synchronisierungsbefehls erfolgreich abgeschlossen hatte. Bisher kann das Bild nicht über die Mediengalerie hochladen. Der Synchronisierungsbefehl schlägt auch fehl, wenn sich ein bestimmtes Bild in der Galerie befindet.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _AKP2E-3154_: Prototype.js Array.from im Konflikt mit der Google Maps-API
   * _Fix note_: Google Maps werden jetzt ordnungsgemäß im PageBuilder-Editor dargestellt. Zuvor wurde durch einen JavaScript-Fehler verhindert, dass Google Maps korrekt dargestellt werden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _AKP2E-2693_: [Cloud] Frontend wird aufgrund eines Problems in der Newsletter-Vorlage nicht geladen
   * _Hinweis korrigieren_: Das Hinzufügen von Bausteinen über den Inhaltsabschnitt der CMS-Seite führt nicht mehr zu einer Ausnahme
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _AC-10539_: [Problem] bei der Preisanzeige im Widget &quot;Kürzlich angesehen&quot;
   * _Hinweis reparieren_: Das System zeigt jetzt im Widget &quot;Zuletzt angezeigtes Produkt&quot;den Preis für nicht vorrätige einfache Produkte korrekt an, wodurch die Konsistenz aller Widgets und Produktlistenseiten sichergestellt wird. Zuvor wurde der Preis für nicht vorrätige einfache Produkte aufgrund einer Bedingung in den Vorlagen für Preisladevorgänge nicht im Widget &quot;Kürzlich angezeigtes Produkt&quot;angezeigt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38167>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problem] Korrektes Tippfehler und korrekte Grammatik in der Datei acl.xsd
   * _FEHLER HINWEIS_: Das System korrigiert jetzt einen Tippfehler und Grammatikfehler in der Datei &quot;acl.xsd&quot;, was die Klarheit und Genauigkeit der Dokumentation verbessert. Zuvor enthielt die Datei acl.xsd einen Tippfehler und eine falsche Grammatik, was möglicherweise zu Verwirrung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38061>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38046>
* _AKP2E-2903_: Der Seitenaufbau ersetzt das Bild, wenn versucht wird, einen Link und andere Benutzerfreundlichkeitsfehler hinzuzufügen.
   * _Hinweis reparieren_: Beim Klicken auf ein Bild werden über Links im WYSIWYG-Editor im Textelement &quot;Page Builder&quot;die richtigen Daten im Bild- und Link-Konfigurationsdialogfeld geladen. Auch das Hinzufügen eines Links zu einem Bild im Editor funktioniert jetzt ordnungsgemäß. Zuvor wurde das Bild durch einen Link ersetzt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### Kunde/ Kunden

* _AC-12162_: Front End - Date of birth validation is failed in Customer creation page
   * _Hinweis reparieren_: Stellen Sie sicher, dass alle Überprüfungen nach der Aktualisierung der Systemabhängigkeit von &quot;Moment.js&quot;auf die neueste Nebenversion funktionieren.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Framework

* _AKP2E-2966_: In iPad mini werden das Menü und die Kopfzeile als mobil geladen. Stattdessen sollten sie als Desktop geladen werden.
   * _Hinweis reparieren_: Das System behandelt jetzt Geräte mit einer Breite von 768 Pixel als Desktop, um sicherzustellen, dass das Menü und die Kopfzeile ordnungsgemäß geladen werden. Zuvor wurden Geräte mit einer Breite von 768 px als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobile-Ansicht geladen wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _AC-10654_: V1/customer/password endpoint Frage/Problem
   * _Hinweis korrigieren_: Das System erfüllt jetzt die in der Verwaltungs-GUI festgelegten Einschränkungen, wenn Kennwortänderungsanfragen über die API verarbeitet werden, wodurch ein möglicher Missbrauch der Funktion zum Zurücksetzen des Kennworts verhindert wird. Zuvor konnte die API Anforderungen zum Ändern von Passwörtern außerhalb der in der Verwaltungs-Benutzeroberfläche definierten Regeln verarbeiten, was möglicherweise einen konstanten Stream von zurückgesetzten E-Mails ermöglichte, wenn gültige E-Mails bekannt waren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38238>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11489_: [Problem] Korrektur von PHPDocs für \Magento\Framework\Data\Collection::getItemById
   * _Hinweis korrigieren_: Die PHPDocs für die Methode \Magento\Framework\Data\Collection::getItemById wurden aktualisiert und enthalten nun Null als möglichen Rückgabetyp, der Probleme mit statischen Analyse-Tools behebt. Zuvor wurde in den PHPDocs der Methode kein Null als möglicher Rückgabetyp angegeben, was zu Warnungen oder Fehlern in der statischen Analyse führte, wenn die Methode in bedingten Anweisungen verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38439>
* _AC-9712_: Unterschied in der weniger kompilierten php- und nodejs-Bibliothek (grunt) mit komplizierten `calc` Ausdrücken
   * _Fix note_: Beheben Sie den Unterschied zwischen der weniger kompilierten php- und nodejs-Bibliothek (grunt).
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub-Codebeitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>
* _AC-11476_: [Problem] Behebung von Problemen mit Kundendaten, wenn das Formular ein Element mit dem Namen `method` enthält
   * _Hinweis reparieren_: Das System erkennt jetzt das Attribut &quot;method&quot;bei Formularübermittlungen korrekt, selbst wenn im Formular ein Element namens &quot;method&quot;vorhanden ist. Dadurch wird die genaue Verarbeitung von Kundendaten sichergestellt. Wenn ein Formularelement früher &quot;Methode&quot;hieß, würde dies die Identifizierung des Attributs &quot;Methode&quot;bei Formularübermittlungen beeinträchtigen und zu potenziellen Problemen bei der Verarbeitung von Kundendaten führen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38484>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38449>
* _AKP2E-2855_: Bei der Überprüfung, ob Daten Änderungen aufweisen, stimmt der Typ im Datenvergleich nicht überein
   * _Hinweis korrigieren_: Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für numerische Datenfelder wie int/float/double). Dadurch wird das Flag _hasDataChanges auf &quot;true&quot;Trigger und die Speicherfunktion aufgerufen. Nachdem diese Korrektur angewendet wurde, ruft die Speicherfunktion nur auf, wenn die Daten geändert wurden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, und nimmt eine strikte Typübereinstimmung vor.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _AC-12002_: [Problem] [Ansicht] Es wurde zusätzlicher Speicherplatz im Link- und Skript-Tag entfernt
   * _Hinweis reparieren_: Das System stellt nun sicher, dass keine zusätzlichen Leerzeichen in den Link- und Skript-Tags vorhanden sind, was saubereren und effizienteren Code ermöglicht. Zuvor konnten zwischen Attributen in den Link- und Skript-Tags doppelte Leerzeichen gefunden werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/32919>
* _AKP2E-2844_: Probleme nach der Aktualisierung von MariaDB auf 10.5.1 oder höher
   * _Hinweis reparieren_: Problem behoben, aufgrund dessen in einer DB Datums-/Uhrzeitwerte nach der Aktualisierung auf MySQL in 0000-00-00 00 konvertiert wurden:00:00
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _AC-10838_: Prozess zur Fehlerindexierung des Katalogsuchindex
   * _Fix note_: Das System schließt jetzt den Befehl re-index erfolgreich ab, ohne dass dabei Fehler auftreten, unabhängig von der mit PHP kompilierten libxml-Version. Zuvor führte die Ausführung des Befehls &quot;re-index&quot;zu einem &quot;Catalog Search Index Process Error during indexation process&quot; Fehler, wenn PHP mit bestimmten Versionen von libxml kompiliert wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12778_: [Problem] Geringfügige Bereinigung: Fehlerhafte Nutzung von Sprintf behoben, es dauert nur 2 Platzhalter hier und w..
   * _FEHLER-Hinweis_: Das System verwendet jetzt die Sprintf-Funktion ordnungsgemäß mit der entsprechenden Anzahl von Platzhaltern, wodurch die Code-Sauberkeit und -Konsistenz verbessert wird. Zuvor wurde die Sprintf-Funktion fälschlicherweise mit einem zusätzlichen Argument verwendet, was keine größeren Probleme verursachte, aber nicht die richtige Verwendung war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38628>
* _AKP2E-2692_: Fehler &quot;Basistabelle oder Ansicht nicht gefunden&quot;tritt auf, wenn eine partielle Indizierung ausgeführt wird
   * _Fix note_: Teilweise Neuindizierung funktioniert jetzt bei einer sekundären DB-Verbindung mit dem großen Changelog ordnungsgemäß
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _AC-12597_: [Problem] Entfernen Sie Verweise auf Dateien aus extjs, die in e1ccdb entfernt wurden...
   * _Hinweis reparieren_: Das System entfernt jetzt Verweise auf Dateien aus &quot;extjs&quot;, die zuvor entfernt wurden, wodurch Fehler in der Browserkonsole und in der Systemprotokolldatei beseitigt werden. Zuvor führten diese Verweise zu Fehlern, da die referenzierten Dateien nicht vorhanden waren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38960>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38951>
* _AC-11423_: Ausnahme: Warnung: Versuchen Sie, auf den Array-Offset in.. -> Calendar.php seit der Aktualisierung auf ICU 74.1 (PHP Intl) zuzugreifen
   * _Hinweis reparieren_: Commerce protokolliert nicht mehr die folgende Ausnahme in der Datei &quot;exception.log&quot;, wenn ein Käufer oder Händler die Storefront oder den Admin besucht: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38364>
* _AKP2E-2959_: [Cloud] import kann nicht mit directory var verwendet werden
   * _Fehlerbehebung_: Das Produkt kann unabhängig vom Dateinamen erfolgreich importiert werden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _AC-11651_: Magento versucht, schreibgeschützte Eigenschaft in der __wakeup-Methode von LoggerProxy zu ändern
   * _Hinweis reparieren_: Das System ermöglicht jetzt die Änderung von zuvor schreibgeschützten Eigenschaften in der __wakeup-Methode des LoggerProxy, wodurch ein reibungsloser Betrieb gewährleistet wird, ohne dass Benutzer gezwungen werden, eine Problemumgehung durchzuführen. Zuvor führte ein Versuch, den Wert einer schreibgeschützten Eigenschaft in der __wakeup -Methode des LoggerProxy neu zu ordnen, zu Problemen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-9630_: Durch die Aktualisierung der Magento wird &quot;general/region/state_required&quot;zurückgesetzt, wenn ein neues Land mit dem erforderlichen Bundesland/der erforderlichen Region hinzugefügt wird.
   * _Hinweis reparieren_: Das System fügt das geänderte Land jetzt nur dann zur Konfiguration &quot;general/region/state_required&quot;hinzu, wenn ein neues Land mit erforderlichen Status hinzugefügt wird. Dadurch wird verhindert, dass benutzerdefinierter Code gestört wird, bei dem davon ausgegangen wird, dass die Region deaktiviert ist. Zuvor wurde durch das Hinzufügen eines neuen Landes mit erforderlichen Status die Konfiguration &quot;general/region/state_required&quot;auf Standardländer mit einem erforderlichen Status zurückgesetzt, was den Shop möglicherweise beschädigte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38076>
* _AC-10991_: Zufällige Überflutung mit Abfragen aus verwandten/Upsell-/Crosssell-Blöcken und Preisindizierung
   * _Hinweis korrigieren_: Das System optimiert jetzt Abfragen von verwandten Blöcken, Upsell- und Cross-Sell-Blöcken, verbessert die Leistung und verhindert, dass die Site aufgrund übermäßiger Abfragen herunterfährt. Zuvor konnte das System mit Abfragen aus diesen Blöcken überlastet werden, was zu erheblichen Verlangsamungen und möglicherweise zu einem Rückgang der Site führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38050>
* _AC-8353_: [Problem] Verbotenes `@author`-Tag entfernen
   * _FEHLER HINWEIS_: Das System erfüllt nun die Kodierungsstandards, indem es das verbotene `@author` -Tag aus bestimmten Modulen entfernt und so saubereren und standardisierten Code gewährleistet. Zuvor war das Tag `@author` in einigen Modulen vorhanden, was den festgelegten Kodierungsstandards entsprach.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37253>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problem] Unzulässiges `@author` Tag aus `Magento_Customer` entfernen (Teil 2)
   * _Hinweis reparieren_: Das System hält jetzt den Kodierungsstandard ein, indem es das verbotene `@author` -Tag aus bestimmten Modulen entfernt und so einen saubereren und standardisierteren Code gewährleistet. Zuvor war das Tag `@author` in einigen Modulen vorhanden, was den festgelegten Kodierungsstandards entsprach.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37250>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37000>
* _AC-8358_: [Problem] Verbotenes `@author`-Tag entfernen
   * _Hinweis reparieren_: Das System erfüllt nun die Kodierungsstandards, indem es das verbotene `@author` -Tag aus bestimmten Modulen entfernt und dadurch die Codequalität und -konsistenz verbessert. Zuvor war das Vorhandensein dieses Tags in einigen Modulen gegen die festgelegten Kodierungsstandards verstoßen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37264>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37014>
* _AC-8360_: [Problem] Verbotenes `@author`-Tag entfernen
   * _FEHLER HINWEIS_: Das System erfüllt nun die Kodierungsstandards, indem es das verbotene `@author` -Tag aus bestimmten Modulen entfernt und so die Codequalität insgesamt verbessert. Zuvor war das Vorhandensein dieses Tags in einigen Modulen gegen die festgelegten Kodierungsstandards verstoßen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37261>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37011>
* _AC-8361_: [Problem] Verbotenes `@author`-Tag entfernen
   * _FEHLER HINWEIS_: Das System erfüllt jetzt die Kodierungsstandards, indem es das verbotene `@author` -Tag aus bestimmten Modulen entfernt und so saubereren und standardisierteren Code gewährleistet. Zuvor war das Vorhandensein dieses Tags in einigen Modulen gegen die festgelegten Kodierungsstandards verstoßen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37260>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37010>
* _AC-8400_: [Problem] Verbotenes `@author`-Tag entfernen
   * _FEHLER HINWEIS_: Das System erfüllt jetzt die Kodierungsstandards, indem es das verbotene `@author` -Tag aus bestimmten Modulen entfernt und so die Code-Qualität verbessert. Zuvor war das Vorhandensein dieses Tags in einigen Modulen gegen die festgelegten Kodierungsstandards verstoßen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37254>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37004>
* _AC-8659_: Leerzeichen in der EditorConfig-Syntax umbricht Regel für [{composer,auth}.json]
   * _Hinweis reparieren_: Das System wendet nun korrekt einen 4-Raum-Einzug auf die Composer- und auth.json-Dateien an, nachdem ein Syntaxfehler in der Editorconfig behoben wurde. Bisher wurden diese Dateien aufgrund eines Leerzeichens in der Syntax von editorconfig fälschlicherweise mit einem Einzug von 2 Leerzeichen formatiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37394>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37395>
* _AC-8714_: Varnish 7.3 - Links der Unterkategorien/Optionen der Kategorie &quot;Standard&quot;werden nicht auf der Startseite der Storefront angezeigt
   * _Hinweis korrigieren_: Auf den Storefront-Startseiten werden jetzt die standardmäßigen Kategorie-Unterkategorien wie erwartet angezeigt. Bisher konnten Käufer nur über URL auf Unterkategorien zugreifen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/d1c335aa>, &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>
* _AC-12594_: [Problem] Verwenden Sie die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration.
   * _Hinweis reparieren_: Das System verwendet jetzt die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration, wodurch die Netzwerkübertragung und der Overhead von Daten, die von einer bestimmten Codeversion abhängig sind, reduziert werden. Diese Änderung verhindert das Überschreiben des Caches in freigegebenen Instanzen während des Containertauschs, was zu verbesserter Stabilität und reduzierter Ausfallzeit führt. Zuvor verwendeten bestimmte Core-Klassen den gemeinsamen Konfigurationstyp, was aufgrund von Unterschieden in den Codeversionen auf mehreren Servern zum Überschreiben des Caches oder zum Ausfall der Anwendung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/29954>
* _AC-11905_: [Problem] Bereitstellung statischer Inhalte - Fehler Typ
   * _FEHLER-Hinweis_: Das System verarbeitet jetzt während der Bereitstellung statischer Inhalte leere LESS-Dateien ordnungsgemäß und zeigt die Fehlermeldung &quot;LESS file is empty&quot;an. Zuvor wurde bei einer leeren LESS-Datei während der Bereitstellung ein Fehler vom Typ &quot;Falsch&quot; ausgegeben.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38683>
* _AC-11852_: Ersetzen Sie die Übersetzung &quot;PayPal-Konto&quot;in token_list.phtml
   * _Hinweis korrigieren_: Das System kennzeichnet den Abschnitt für tokenisierbare Kontozahlungsmethoden jetzt als &quot;Konto&quot;anstelle von &quot;PayPal-Konto&quot;auf der Seite &quot;Gespeicherte Zahlungsmethoden&quot;, wodurch er für seine Funktion repräsentativer wird. Zuvor wurde dieser Abschnitt speziell als &quot;PayPal-Konto&quot;bezeichnet, was irreführend war, als andere tokenisierbare Kontozahlungsmethoden hinzugefügt wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35622>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37959>
* _AC-10941_: Hinzufügung der Filter created_at, status und grand_total zur Abfrage von Kundenbestellungen und Korrektur eines Fehlers bei mehreren Filtern.
   * _Hinweis reparieren_: Das System unterstützt jetzt die Verwendung von &quot;created_at&quot;-, &quot;status&quot;- und &quot;grand_total&quot;-Filtern in Abfragen von Kundenbestellungen und hat ein Problem behoben, bei dem mehrere Filter nicht korrekt angewendet wurden. Bisher hat das System diese Filter nicht unterstützt und es nicht möglich gemacht, alle Filter anzuwenden, wenn in einer Abfrage mehr als ein Filter verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/36949>
* _AC-11829_: [Problem] Behebung von Unstimmigkeiten bei der Handhabung von Ausnahmen zwischen Entwicklungs- und Produktionsmodi
   * _Hinweis reparieren_: Das System verarbeitet jetzt konsistent Ausnahmen zwischen Entwickler- und Produktionsmodi, wodurch eine unerwartete Weiterleitung zur Anmeldeseite verhindert wird, wenn eine Ausnahme ausgelöst wird. Zuvor konnte eine Inkonsistenz bei der Ausnahmebehandlung dazu führen, dass eine Umleitung zur Anmeldeseite im Produktionsmodus erfolgt, anstatt die Ausnahmemeldung anzuzeigen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38639>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37712>
* _AC-11819_: Der integrierte FPC-Cache ist in Version 2.4.7 für einige Konfigurationen fehlerhaft
   * _Hinweis reparieren_: Das System speichert jetzt Seiten korrekt zwischen, wenn der Parameter MAGE_RUN_CODE festgelegt ist, und sorgt so für eine optimale Leistung. Zuvor wurden Seiten unter diesen Bedingungen nicht zwischengespeichert, was zu potenziellen Leistungsproblemen führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38626>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11781_: [Problem] falsch benannte Variable umbenennen
   * _Hinweis reparieren_: Das System benennt nun die Variable korrekt, die den Geldbetrag enthält, der noch zurückerstattet werden kann, und verhindert so Verwirrung beim Debugging. Zuvor wurde diese Variable fälschlicherweise als totalRefund bezeichnet, was zu Missverständnissen für Entwickler führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38609>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/36205>
* _AC-11696_: ChangelogBatchWalker funktioniert nicht in mehreren Threads
   * _Hinweis korrigieren_: Das System unterstützt jetzt die Prozessabspaltung für die MView-Indizierung, wodurch Fehler während der Indexausführung bei der Arbeit mit mehreren Threads vermieden werden. Zuvor führte die Ausführung von ChangelogBatchWalker auf mehreren Threads zum Löschen von Tabellen, die von anderen Threads verwendet wurden, was während der Indexausführung zu einem Fehler führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38246>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38248>
* _AC-8984_: [Problem] Fügt der Ausgabe bestimmter Setup-CLI-Befehle einige weitere Farben hinzu
   * _Hinweis reparieren_: Das System fügt nun der Ausgabe bestimmter Befehle der Setup-Befehlszeilenschnittstelle (CLI) mehr Farben hinzu, wodurch Lesbarkeit und Benutzerfreundlichkeit verbessert werden. Zuvor war die Ausgabe dieser Befehle aufgrund fehlender Farbdifferenzierung schwieriger zu lesen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/29298>
* _AC-6754_: Tippfehler bei einer JS-Datei.
   * _FEHLER-Hinweis_: Das System verwendet nun den Begriff &quot;Abonnenten&quot;in der JavaScript-Datei korrekt, um sicherzustellen, dass die zugehörigen Funktionen ordnungsgemäß funktionieren. Zuvor führte ein typografischer Fehler in der JavaScript-Datei zur falschen Verwendung des Begriffs &quot;Abonnenten&quot;.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36163>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/36171>

### Framework, GraphQL

* _AC-7976_: [Problem] Neue Unterstützung für benutzerdefinierte Skalartypen für GraphQL-Schemata
   * _FEHLER-Hinweis_: Das System unterstützt jetzt benutzerdefinierte Skalartypen für das GraphQL-Schema, sodass Entwickler benutzerdefinierte Skalartypen und -Implementierungen definieren können. Diese Funktion kann besonders zum Ausdrücken von Werten nützlich sein, die überprüft werden müssen, z. B. HTML, E-Mails, URLs, Daten usw., sowie für erweiterte Fälle wie EAV-Attribute. Zuvor unterstützte das System die Verarbeitung benutzerdefinierter Skalartypen in GraphQL nicht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL

* _AKP2E-3190_: [Cloud] Produktdiagramm mit Fehler, wenn dasselbe einfache Produkt mehreren konfigurierbaren Produkten zugewiesen wurde
   * _Fix note_: Zuvor gab grapQL bei separaten konfigurierbaren Produkten mit demselben einfachen Produkt einen Fehler zurück. Nachdem diese Fehlerbehebung angewendet wurde, geben verschiedene konfigurierbare Produkte mit demselben einfachen Produkt grapQL das Ergebnis ohne Fehler zurück.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _AC-11729_: Magento_GraphQl führt die Header-Verarbeitung aus, selbst wenn der Header-Wert die Validierung nicht besteht
   * _Hinweis reparieren_: Das System stellt jetzt sicher, dass die Header-Verarbeitung nur einmal und nur dann ausgeführt wird, wenn der Header-Wert die Validierung besteht, was die Sicherheit erhöht und potenzielle Schwachstellen verhindert. Zuvor wurde die Header-Verarbeitung auch dann ausgeführt, wenn der Header-Wert die Validierung nicht bestanden hat, was aufgrund der doppelten Verarbeitung von Header-Werten zu potenziellen Sicherheitslücken und unerwartetem Verhalten führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: Die Optionen für &quot;Physical Giftcard&quot;haben nicht die richtige Sortierreihenfolge
   * _FEHLER-Hinweis_: Das System sortiert jetzt die Optionen von Geschenkgutkartenprodukten korrekt, wenn sie über GraphQL abgefragt werden, und stellt so eine konsistente Wiedergabe mit dem Luma-Design sicher. Zuvor war die Sortierreihenfolge aufgrund des Luma-Designs falsch, was zu einer fehlerhaften Anzeige und Reihenfolge von Optionen wie Absendername, Empfängername und Betrag führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [GraphQL] Resolver-Cache wird beim Erstellen/Bearbeiten/Verschieben/Löschen einer Staging-Aktualisierung ungültig gemacht
   * _Hinweis reparieren_: Das System stellt jetzt sicher, dass der Resolver-Cache beim Erstellen, Bearbeiten, Verschieben oder Löschen einer Staging-Aktualisierung nicht invalidiert wird, sondern nur, wenn die Staging-Aktualisierung auf die Entität angewendet wird. Zuvor wurde der Resolver-Cache vorzeitig invalidiert, selbst bevor das Staging-Update angewendet wurde, was zu unnötigen Cache-Invalidierungen führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AKP2E-2642_: Schneller Cache nicht gelöscht für Aktualisierung des Inhalts-Staging
   * _Hinweis korrigieren_: Der Antwort-Cache für GraphQL mit PageBuilder-Inhalten wird jetzt invalidiert, wenn die mit dem Inhalt verknüpften Entitäten von PageBuilder aktualisiert werden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _AKP2E-2653_: Deaktivieren der geschichteten Navigation - Die Aggregation wird nicht aus Graphql entfernt.
   * _Hinweis korrigieren_: Das Problem wurde behoben, nachdem die Prüfung angewendet wurde, während eine Produktsuche mit Kategorieaggregationen über eine GraphQL-Abfrage angefordert wurde, wenn die Administratorkonfigurationseinstellung &quot;Katalog > Ebenennavigation > Anzeigenkategoriefilter&quot;war.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _AKP2E-2928_: GraphQL Products-Aufruf mit dem Preisfilter {from:&quot;0&quot;} gibt kein Ergebnis zurück
   * _FEHLER HINWEIS_: Zuvor wurden bei der Suche nach grafischen Produkten mit Filter nach Nullpreisen aufgrund einer ausgelösten Ausnahme überhaupt keine Ergebnisse zurückgegeben. Jetzt gibt die Suche die Ergebnisse erwartungsgemäß zurück.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _AKP2E-3128_: [Cloud] Beschädigter GraphQL-Aufruf für getPurchaseOrder mit Knotenzitat
   * _Fix note_: Der GraphQL-Aufruf &quot;Purchase Order&quot;kann die Aufgabe ausführen, ohne dass interne Serverfehler auftreten.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _AKP2E-3184_: [Cloud] Konfigurierbare Produkte werden nicht auf der Produktions-Site angezeigt, wenn das Produkt in &quot;Alle Store-Ansichten&quot;nicht aktiviert ist
   * _Hinweis korrigieren_: Das System zeigt jetzt konfigurierbare Produkte auf der Site korrekt an, selbst wenn das Produkt nicht in &quot;Alle Store-Ansichten&quot;aktiviert ist, aber in bestimmten Bereichen der Store-Ansicht aktiviert ist.
Wenn ein Produkt zuvor in &quot;Alle Store-Ansichten&quot;deaktiviert und nur in bestimmten Speicheransichtsbereichen aktiviert war, wurden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, was dazu führte, dass das Produkt nicht ordnungsgemäß angezeigt wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/inventory/commit/3f300077>

### GraphQL, Bestand/MSI

* _AKP2E-2607_: Mutation &quot;MergeCart&quot;löst eine Ausnahme aus, wenn Quell- und ZielWarenkorb dieselben Bundle-Elemente aufweisen
   * _Fix note_: &#39;-
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Bestand/MSI, Leistung

* _AKP2E-1716_: Site nach dem Upgrade herunterfahren
   * _Fix note_: Die Leistung beim Abrufen von Bundle-Produkten über GraphQl wurde verbessert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Leistung

* _AC-9569_: [GraphQL Resolver] Kundenauflösungsdaten werden nicht vom Import ungültig gemacht
   * _Hinweis reparieren_: Der Cache des GraphQL-Kunden-Resolvers wird jetzt erwartungsgemäß invalidiert, wenn ein Kunde durch Importe bearbeitet oder gelöscht wird. Zuvor wurde der Cache nicht ungültig gemacht und Kundendaten konnten beim Import bearbeitet oder gelöscht werden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Suche

* _AKP2E-2809_: Die Sortierung der GraphQL-Produktliste nach mehreren Parametern funktioniert nicht
   * _Hinweis korrigieren_: Die Sortierung des Produkts nach mehreren Feldern in GraphQl funktioniert jetzt wie in der Dokumentation beschrieben.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c971859e>

### Import/Export

* _AKP2E-2990_: Datum des Kunden &quot;created_at&quot;Nicht konvertiert beim Export in Zeitzone speichern
   * _Hinweis reparieren_: Ein Datumswert für die Spalte &quot;created_at&quot;wird basierend auf der Zeitzone im CSV-Abschnitt zum Kundenexport in das richtige Datumsformat konvertiert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _AKP2E-2902_: Import für Produkte hinzufügen/aktualisieren, die anpassbare Optionen duplizieren
   * _Hinweis korrigieren_: Das Problem wurde behoben, indem den Produktoptionen bei CSV-Importen der Produktoptionen der richtige Store zugewiesen wurde.
Zuvor wurde dem Admin Store anstelle des entsprechenden Stores zugewiesen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _AC-12172_: Problem beim Produktimport, wenn der benutzerdefinierte Options-Typ bereitgestellt wird: Datei (Erstelltes Produkt enthält keinen Preis für benutzerdefinierte Optionen und zeigt nur die erste bereitgestellte Dateityperweiterung an)
   * _Hinweis reparieren_: Das System importiert nun Produktdaten korrekt mit benutzerdefinierten Optionen des Typs &quot;Datei&quot;, um sicherzustellen, dass alle bereitgestellten Dateierweiterungen angezeigt werden und der Preis für die benutzerdefinierte Option eingeschlossen ist. Wenn zuvor beim Produktimport eine benutzerdefinierte Option des Typs &quot;Datei&quot;mit mehr als einer Dateierweiterung bereitgestellt wurde, wurde nur die erste Erweiterung angezeigt und der Preis für die benutzerdefinierte Option fehlte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38805>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38926>
* _AKP2E-2737_: Duplizieren Sie Kunden, die mit derselben E-Mail-Adresse erstellt wurden, indem Sie Importe verwenden.
   * _Hinweis reparieren_: Der Import des Kunden, während die Kontofreigabe auf &quot;Global&quot;gesetzt ist, wird der importierte Kunde, der im System vorhanden ist, aktualisiert.
Zuvor importierte Kunden wurden dupliziert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _AKP2E-2710_: Falsche Ausführungszeit für Import-Vorgang im Raster &quot;Importverlauf&quot;
   * _Hinweis korrigieren_: Die Ausführungszeit des Importberichts wird korrekt unabhängig vom Gebietsschema des Administrators angezeigt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Installieren und Verwalten

* _AKP2E-2102_: Schaltfläche &quot;Export VCL for Varnish 7&quot;im Admin-Bedienfeld
   * _Korrektur des Hinweises_: Die Schaltfläche &quot;Export VCL for Varnish 7&quot;wurde zum Admin-Bedienfeld hinzugefügt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestand/MSI

* _AC-11593_: Google Google API-Schlüssel funktioniert nicht beim Hinzufügen von Map mit Attributen
   * _Fehlerbehebung_: Das System unterstützt jetzt die neueste Version der Google Maps-API 3.56, sodass Benutzer erfolgreich einen Inhaltsbaustein vom PageBuilder-Menü zur Bühne hinzufügen können, ohne dass dabei Fehler auftreten. Bisher konnten Benutzer aufgrund von Kompatibilitätsproblemen mit der Google Maps-API-Version keinen Inhaltsbaustein hinzufügen, was zu einer Fehlermeldung führte, dass etwas nicht funktioniert hatte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AKP2E-2794_: [Cloud] Kritisches Problem bei der Produktliste mit leeren Platzierungen
   * _FEHLER-Hinweis_: Das System zeigt Produktlisten jetzt korrekt ohne Leerzeichen an, wenn Produkte auf &quot;Nicht auf Lager&quot;gesetzt sind. Dadurch wird eine konsistente und genaue Anzeige der verfügbaren Produkte sichergestellt. Zuvor führte die Einstellung eines Produkts auf &quot;Nicht auf Lager&quot;dazu, dass in der Produktliste ein leerer Bereich angezeigt wurde, was das Layout beeinträchtigte und Kunden möglicherweise verwirrte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Bestellung

* _AKP2E-3002_: [CLOUD] E-Mails von der Admin-Benutzeroberfläche können nicht deaktiviert werden, da die Entwicklungsdokumente anzeigen
   * _Hinweis reparieren_: Das System verhindert nun korrekt, dass E-Mails zum Verkauf gesendet werden, wenn die E-Mail-Kommunikation deaktiviert ist. Diese E-Mails werden nicht mehr gesendet, wenn die E-Mail-Kommunikation wieder aktiviert ist. Zuvor wurden Verkaufs-E-Mails, die bei deaktivierter E-Mail-Kommunikation initiiert wurden, weiterhin gesendet, sobald die E-Mail-Kommunikation wieder aktiviert wurde.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _AC-12462_: Benutzerdefinierter Zwischenstatus in Admin kann nicht mit Kommentarformular hinzufügen geändert werden
   * _Hinweis reparieren_: Das System aktualisiert jetzt den Bestellstatus korrekt auf &quot;Bereit für Abruf&quot;, wenn es vom Formular &quot;Kommentar hinzufügen&quot;im Admin-Bedienfeld geändert wird, um eine genaue Verfolgung des Bestellfortschritts sicherzustellen. Zuvor blieb der Bestellstatus als &quot;Gesendet&quot;, selbst wenn versucht wurde, ihn über das Formular &quot;Kommentar hinzufügen&quot;in &quot;Bereit für Abruf&quot;zu ändern.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38917>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38923>
* _AC-10828_: Übersichtsbildschirm zur Backend-Bestellung: Rücksortierte Menge auf Bestellartikelebene nicht sichtbar
   * _Hinweis reparieren_: Das System zeigt jetzt die Anzahl der rücksortierten Elemente in der Spalte &quot;Menge&quot;auf dem Bildschirm mit der Übersicht der Backend-Reihenfolge an. Dadurch wird sichergestellt, dass Benutzer den Status aller Elemente in einer Bestellung genau verfolgen können. Zuvor zeigte die Spalte &quot;Menge&quot;nur die Anzahl der bestellten, in Rechnung gestellten und versandten Artikel an, zeigte jedoch nicht die Anzahl der rücksortierten Artikel an.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38320>
* _AKP2E-2622_: Änderungen an der Telefonnummer können nicht in vorhandenen Bestelldetails gespeichert werden.
   * _Hinweis reparieren_: Jetzt kann der Benutzer das internationale Präfix 00 im Telefonfeld der Bestelladresse hinzufügen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38201>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _AC-11798_: [Ausgabe] Versandpreis, der im gedruckten PDF-Format einen anderen Wert anzeigt
   * _FEHLER-Hinweis_: Das System zeigt jetzt die Versandpreise in gedruckten PDF gemäß den Steuerkonfigurationseinstellungen korrekt an, wodurch die Konsistenz zwischen der Seite mit der Darstellung der Verkaufsbestellungen auf der Rechnung und der gedruckten Rechnung gewährleistet wird. Zuvor war der auf der gedruckten PDF angezeigte Versandpreis ohne Steuern, unabhängig von der Steuerkonfiguration.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AKP2E-2756_: [Cloud] Auftragsstatus geändert, um abgeschlossen zu werden, wenn ein teilweise versendeter Auftrag teilweise zurückerstattet wird
   * _Hinweis reparieren_: Beim Versenden eines Kreditmemo wird der Auftragsstatus nicht mehr in &quot;abgeschlossen&quot;geändert, wenn Artikel vorhanden sind, die noch nicht versandt wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _AC-10994_: [Problem] Falsche Store-ID, die im Auftragsadressen-Renderer verwendet wird
   * _Hinweis korrigieren_: Das System verwendet jetzt beim Rendern der Bestelladresse die Store-ID, die einer Bestellung zugeordnet ist, korrekt, und stellt sicher, dass die Adressen entsprechend ihrer jeweiligen Store-ID korrekt formatiert sind. Zuvor verwendete das System fälschlicherweise die aktuelle Store-ID, was zu einer fehlerhaften Adressformatierung führen konnte, wenn mehrere Bestellungs-E-Mails aus verschiedenen Stores gesendet werden mussten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37932>
* _AKP2E-3045_: Bestellung ohne Rückzahlung abgeschlossen
   * _Fix note_: Das System behält jetzt den Bestellstatus ordnungsgemäß als &quot;Verarbeitung&quot;und den Rechnungsstatus als &quot;Ausstehend&quot;bei, wenn eine Bestellung mit einer nicht erfassten Zahlung eine Sendung erstellt hat. Dadurch wird sichergestellt, dass Bestellungen erst nach vollständiger Rückerstattung als &quot;geschlossen&quot;gekennzeichnet werden. Zuvor wurde durch die Erstellung einer Sendung für eine Bestellung mit einer ausstehenden Rechnung der Auftragsstatus fälschlicherweise auf &quot;Geschlossen&quot;geändert.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _AKP2E-2734_: E-Mails können nicht gesendet werden
   * _Hinweis korrigieren_: Das System enthält jetzt eine Konfigurationsoption async_sending_versucht, die Anzahl der Versuche anzugeben, eine E-Mail vor dem Anhalten zu senden. Dies verbessert die Verarbeitung fehlgeschlagener E-Mail-Sendungen bei Aktivierung des asynchronen Versands. Wenn eine E-Mail bisher nicht gesendet werden konnte, versuchte das System ständig, sie erneut zu senden, was zu einer endlosen Schleife von Fehlermeldungen im Systemprotokoll führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>

### Reihenfolge, Rückgabe

* _AKP2E-2982_: Die Auftragsrückerstattung führt zu doppelten Kreditkarten
   * _Hinweis korrigieren_: Wenn Sie die Rückerstattung über die REST-API vornehmen, wenn zwei identische Anforderungen gleichzeitig ausgeführt wurden, werden keine doppelten Credit Memos mehr erstellt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestellung, Steuern

* _AKP2E-3003_: [CLOUD] Falsche base_row_total in RESTFUL-Bestell-API bei der Aktivierung grenzüberschreitender Transaktionen und Anwendung von Coupon-Rabatten
   * _Hinweis korrigieren_: Jetzt wird der korrekte base_row_total von der RESTFUL-Bestell-API zurückgegeben, wenn eine grenzüberschreitende Transaktion aktiviert ist und ein Coupon-Rabatt angewendet wird.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/9af794a4>

### Andere Entwicklertools

* _AC-12571_: Das Navigieren in der Kategorienstruktur führt zu Fehlern in Redis: &quot;Redis session exceeded concurrent connections&quot;
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38851>
   * _GitHub-Codebeitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>
* _AC-10658_: [Problem] Korrektur des HTML-Syntaxfehlers in visual.phtml
   * _Hinweis reparieren_: Das System schließt jetzt das Start-Tag korrekt in der Datei visual.phtml, wodurch eine ordnungsgemäße HTML-Syntax gewährleistet ist. Zuvor wurde das Start-Tag nicht ordnungsgemäß geschlossen, was zu einem HTML-Syntaxfehler führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38247>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problem] Änderung von &quot;aktiv&quot;zu &quot;aktiviert&quot;in &quot;bin/magento maintenance:status command
   * _Hinweis reparieren_: Das System stellt nun genauere Statusmeldungen für den Wartungsmodus-Befehl bereit, wobei der Status von &quot;aktiv&quot;zu &quot;aktiviert&quot;und von &quot;nicht aktiv&quot;zu &quot;deaktiviert&quot;geändert wird. Zuvor wurde die Statusmeldung für den Wartungsmodus-Befehl als &quot;aktiv&quot;oder &quot;nicht aktiv&quot;angezeigt, was zu Verwirrung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38486>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38410>

### Zahlungen

* _AKP2E-2841_: Der Payflow erstellt jedes Mal eine neue Transaktion, wenn wir auf die Schaltfläche &quot;Abruf&quot;auf dem Bildschirm &quot;Transaktionen anzeigen&quot;klicken
   * _Hinweis korrigieren_: Das System ruft jetzt Transaktionsinformationen korrekt ab, ohne jedes Mal, wenn auf dem Bildschirm &quot;Transaktionen anzeigen&quot;auf die Schaltfläche &quot;Abrufen&quot;geklickt wird, eine neue Zahlungstransaktion zu erstellen. Zuvor wurde durch Klicken auf die Schaltfläche Abruf fälschlicherweise eine neue Zahlungsaktion für eine bereits bezahlte Bestellung erstellt.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _AKP2E-3028_: Die Meldung &quot;Paylater&quot;wird in der PDP für das kanadische Paypal-Händlerkonto nicht angezeigt
   * _FEHLER-Hinweis_: Das System zeigt nun die PayLater-Nachricht für kanadische PayPal-Handelskonten auf der Produktdetailseite (PDP) korrekt an, wenn das Land des Käufers anhand der Rechnungsadresse oder des Versands des Kontos bestimmt werden kann. Zuvor wurde die PayLater-Nachricht aufgrund eines fehlenden Parameters nicht angezeigt, was zu einem Fehler in der Browser-Konsole führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/6a185204>

### Leistung

* _AKP2E-2494_: Leistungsproblem beim Laden von Produktattributen in Warenkorbregeln
   * _Hinweis korrigieren_: Verbesserte Abfrageleistung für Verkaufsregeln - von etwa 150 ms auf einstellige ms.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _AKP2E-2910_: Die Ausführung des Aufrufs der REST-API für Bestellungen dauert lange
   * _Hinweis reparieren_: Das System führt jetzt den REST-API-Aufruf für Aufträge innerhalb eines angemessenen Zeitraums aus und verbessert so die Leistung beim Abrufen einer großen Anzahl von Bestellungen. Zuvor dauerte die Ausführung des Aufrufs der Order REST API lange, was beim Abrufen einer großen Anzahl von Bestellungen zu Verzögerungen führte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/001e5188>
* _AKP2E-2850_: Bestellungen werden bei der Einrichtung mehrerer Stores bei der Verwendung der Verarbeitung asynchroner Bestellungen und der Geschäftsbedingungen abgelehnt
   * _Hinweis korrigieren_: Die Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden jetzt verarbeitet.
Bevor sie automatisch abgelehnt wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _AC-12000_: [Problem] Code-Bereinigung, Hinzufügen neuer kritischer Kopfblöcke und Verschieben kritischer CSS vor Assets
   * _Hinweis korrigieren_: Das System enthält jetzt einen neuen kritischen Kopfblock und verschiebt kritische CSS vor Assets, wodurch eine stärkere Anpassung und Leistungsoptimierung im Frontend ermöglicht wird. Zuvor wurde das kritische CSS nicht vor den Assets positioniert, was Anpassungs- und Optimierungsmöglichkeiten einschränkte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/35580>
* _AKP2E-2673_: Leistung bei partieller Preisindizierung
   * _Hinweis korrigieren_: Die Leistung bei partieller Indizierung des Preises wurde verbessert, indem einige der im Indizierungsprozess verwendeten Löschabfragen optimiert wurden.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _AC-12176_: Die Design-Kompilierung bricht ab, wenn der mysql-Host Port-Informationen enthält
   * _Hinweis reparieren_: Das System verarbeitet jetzt ordnungsgemäß die MySQL-Host-Konfiguration, die Port-Informationen enthält, und stellt so eine erfolgreiche Designkompilierung sicher. Zuvor schlug die Designkompilierung fehl, wenn die MySQL-Hostkonfiguration in der Datenbankverbindung Port-Informationen enthielt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38842>

### Produkt

* _AKP2E-2944_: [Cloud] addFilterToMap-Funktion funktioniert für bestimmte Spalten nicht
   * _Hinweis reparieren_: Jetzt kann das benutzerdefinierte Modul im Sortierungsraster verwendet werden. Bei der Verwendung eines benutzerdefinierten Moduls traten bisher Fehler auf.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _AC-10947_: Die ProductRepository-Funktion GetById erstellt nicht den richtigen Cache-Schlüssel
   * _Fix note_: Das System erstellt jetzt korrekt einen Cache-Schlüssel in der Funktion GetById des ProductRepository, unabhängig davon, ob die Store-ID als Zeichenfolge oder Ganzzahl übergeben wird. Dadurch wird sichergestellt, dass das Produkt bei nachfolgenden Aufrufen aus dem Speicher abgerufen wird, was die Leistung verbessert. Zuvor konnte das System das Produkt jedes Mal, wenn die Funktion aufgerufen wurde, aus der Datenbank abrufen, selbst mit denselben Parametern, da der Cache-Schlüssel falsch erstellt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38384>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38433>
* _AC-10535_: Sonderzeichen im konfigurierbaren verknüpften Produktnamen werden in HTML-Entitäten konvertiert.
   * _Hinweis reparieren_: Beim Bearbeiten eines konfigurierbaren Produkts behält das System jetzt beim Bearbeiten Sonderzeichen in den Namen der verknüpften HTML-Produkte bei, wodurch verhindert wird, dass diese in Entitäten umgewandelt werden. Zuvor wurden Sonderzeichen in verknüpften Produktnamen bei der Bearbeitung des konfigurierbaren Produkts in HTML-Entitäten konvertiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38146>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38447>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) muss vom Typ int sein, angegebene Zeichenfolge
   * _Hinweis korrigieren_: Das System Trigger nun E-Mails mit Produktwarnungen ordnungsgemäß, indem sichergestellt wird, dass die Store-Kennung den richtigen Datentyp aufweist. Zuvor wurden E-Mails mit Produktanzeigen aufgrund einer Typabweichung in der Store-Kennung nicht gesendet.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35602>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11992_: [Problem] [MFTF] AdminClickAddOptionForBundleItemsActionGroup hinzugefügt
   * _Hinweis reparieren_: Das System enthält jetzt die AdminClickAddOptionForBundleItemsActionGroup, wodurch die Funktionalität des Admin-Bedienfelds verbessert wird. Zuvor war diese Aktionsgruppe nicht verfügbar.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/30857>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/30838>

### Promotion

* _AKP2E-2811_: [Cloud] Neuindizierung Catalog Rule Product Indexer gibt SQLSTATE[HY000] aus: Allgemeiner Fehler: MySQL Server 2006 wurde entfernt.
   * _FEHLER HINWEIS_: Das System verarbeitet jetzt den benutzerdefinierten &quot;batchCount&quot;-Wert in der Datei &quot;di.xml&quot;für &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;korrekt, wodurch SQL-Fehler wie &quot;Allgemeiner Fehler: 2006 MySQL Server ist weg&quot;während der Neuindizierung des Katalogregel-Produktindexes aufgrund der falschen Stapelgröße bei großen Katalogen verhindert werden
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _AKP2E-2602_: Kundenattribut beim Erstellen eines Kontos aus einer Einladung nicht sichtbar
   * _Hinweis korrigieren_: Kundenattribute sind beim Erstellen eines Kontos aus der Einladung verfügbar.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AKP2E-2627_: Couponcode mit Verwendungsmöglichkeiten pro Couponlimit wird nicht für die Zahlung freigegeben. Der Couponcode schlägt mit einer Stornierung der Bestellung fehl
   * _Hinweis reparieren_: Das System aktualisiert jetzt die Couponnutzung sofort, wenn eine Bestellung erstellt oder abgebrochen wird, und fügt Regelverwendungen zu einer Warteschlange hinzu, um potenzielle Deadlocks zu verhindern. Dadurch wird sichergestellt, dass ein Couponcode mit der Beschränkung &quot;Nutzung pro Coupon&quot;veröffentlicht und wiederverwendet werden kann, wenn eine Bestellung aufgrund einer fehlgeschlagenen Zahlung storniert wird. Zuvor hat das System den Gutscheincode nicht zur Wiederverwendung freigegeben, was zu einer Fehlermeldung führte, dass der Gutscheincode ungültig war.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/c971859e>

### SEO

* _AKP2E-2641_: Multi Store Falsch Kategorie url-rewrite für Kategorie der dritten Ebene
   * _Hinweis korrigieren_: Richtige URL-Neuschreibungen für untergeordnete Elemente mit übergeordnetem benutzerdefinierten Scoped-URL-Schlüssel generieren
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _AKP2E-2770_: Doppelbytezeichen (Sonderzeichen) im Feld &quot;Produktname&quot;blockieren die Produkterstellung im Backend
   * _Hinweis korrigieren_: Es wurde eine neue Einstellung hinzugefügt, mit der Sie die Transliteration auf die Produkt-URL anwenden können. Die Einstellung ist hier verfügbar: Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung: &quot;Anwenden der Transliteration für Produkt-URL&quot;
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _AC-11907_: Das Hinzufügen von URL-Neuschreibungen mit einem Akzent führt zum unendlichen Laden
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38692>
   * _GitHub-Codebeitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>

### Sicherheit

* _AC-11855_: [Problem] Fehlendes Schriftart-CSP-Paylater-Popup
   * _Hinweis korrigieren_: Das System ermöglicht jetzt das Laden der Schriftart &quot;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;&quot;, ohne die Richtlinie zur Inhaltssicherheit zu verletzen, und stellt sicher, dass die richtige Anzeige des SeitenPopup angezeigt wird. Zuvor wurde das Laden der Schriftart aufgrund eines Verstoßes gegen die Richtlinie zur Inhaltssicherheit abgelehnt, was Anzeigeprobleme mit dem SeitenPopup verursachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/37401>

### Versand

* _AKP2E-2765_: MFTF-Test AdminCreatingShippingLabelTest schlägt fehl, da Anmeldeinformationen in der Jenkins-Umgebung nicht hinzugefügt wurden
   * _Fix note_: mftf test fix
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _AC-10757_: [Problem] Tippfehler in tracking.phtml behoben - umbenannt in JS-Funktionen &quot;currier&quot;in &quot;carrier&quot;.
   * _FEHLER HINWEIS_: Das System verwendet jetzt korrekt den Begriff &quot;carrier&quot;anstelle des falsch geschriebenen &quot;currier&quot;in den in der Bestellverfolgungsvorlage verwendeten JavaScript-Handler-Funktionen, um eine ordnungsgemäße Funktionsbenennung und Codeklarheit sicherzustellen. Zuvor wurde der falsch geschriebene Begriff &quot;currier&quot;verwendet, was zu potenzieller Verwirrung und Inkonsistenz in der Codebasis führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/33414>
* _AKP2E-2763_: Tabellenzahlen, die auch bei Anwendung des kostenlosen Versands angezeigt werden
   * _Hinweis reparieren_: Die Versandmethode für Tabellenraten wird jetzt angezeigt, auch wenn der kostenlose Versand nach Anwendung des Gutscheins verfügbar wird
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _AKP2E-2738_: Tracking-Fenster mit falschem erwarteten Bereitstellungsdatum
   * _Hinweis korrigieren_: Zeigt das richtige Bereitstellungsdatum für den Fedex-Netzbetreiber an.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _AC-11938_: UPS REST &quot;Eine Sendung darf nicht als Maßeinheit eine KGS/IN-, LBS/CM- oder OZS/CM-Lieferung haben&quot;
   * _Hinweis korrigieren_: Stellen Sie sicher, dass die UPS-Raten beim Checkout und im Warenkorb angezeigt werden sollen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38618>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/493e01f5>

### Targeting

* _AC-9432_: [Problem] Verwendung von CIDR-Bereichen in der Zulassungsliste der Wartung zulassen
   * _Hinweis reparieren_: Das System unterstützt jetzt die Verwendung von CIDR-Bereichen im Wartungsmodus, die IP-Listen zulassen, sodass eine Reihe von IP-Adressen den Wartungsmodus umgehen kann. Zuvor war es im Wartungsmodus nur möglich, dass die IP-Liste einzelne IP-Adressen den Wartungsmodus umgeht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37943>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/30699>

### Test-Framework

* _AC-11654_: Fehler beim Integrationstest test testDbSchemaUpToDate aufgrund des JSON-Spaltentyps
   * _Hinweis korrigieren_: Das System erkennt jetzt JSON-Spaltentypen im Datenbankschema bei Integrationstests korrekt, wodurch Testfehler aufgrund einer Inkongruenz zwischen dem Datenbankschema und dem deklarativen Schema verhindert werden. Zuvor hat das System JSON-Spaltentypen in MariaDB fälschlicherweise als LONGTEXT identifiziert, was dazu führte, dass Integrationstests fehlschlugen.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/ef81f5a2>

### UI-Framework

* _AC-12189_: Grunt Weniger verwendet pub/ prefix für Quellemaps
   * _Hinweis reparieren_: Das System generiert jetzt weniger/css-Quellemaps ohne das /pub-Präfix für Pfade bei Verwendung von grunt, sodass keine Problemumgehung in der Webserver-Konfiguration erforderlich ist. Zuvor war für die Verwendung des /pub-Präfixes in Quellemaps-Pfaden eine bestimmte Konfiguration auf dem Webserver erforderlich, um ordnungsgemäß zu funktionieren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/38840>
* _AKP2E-3061_: [Cloud] Code der Konfusionsbibliothek in der Effect-drop.js von AC 2.4.4-p8
   * _Hinweis reparieren_: Das System implementiert jetzt die Bibliothek &quot;Effect-drop.js&quot;ordnungsgemäß, um sicherzustellen, dass die jQuery-UI-Effekte ordnungsgemäß funktionieren. Zuvor wurde die Bibliothek &quot;Effect-drop.js&quot;fälschlicherweise mit der Bibliothek &quot;Effect-clip.js&quot;überschrieben, was potenzielle Probleme mit jQuery-UI-Effekten verursachte.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _AC-1306_: Statischer Inhalt wird für deaktivierte Module bereitgestellt
   * _Hinweis korrigieren_: Das System schließt CSS für deaktivierte Module jetzt aus den endgültigen CSS-Ausgabedateien aus, sodass unnötige Stile nicht geladen werden. Zuvor war CSS für deaktivierte Module in den endgültigen CSS-Ausgabedateien enthalten, was zum Laden zusätzlicher, unnötiger Stile führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [Problem] Laden Sie den Backend-Blockkontext nicht auf dem Frontend
   * _Hinweis reparieren_: Das System stellt jetzt sicher, dass der Backend-Blockkontext nicht auf das Frontend geladen wird, was die Erstellung unnötiger Backend-Sitzungen und potenzieller Sitzungssperren verhindert. Zuvor hat das System fälschlicherweise den Backend-Blockkontext auf dem Frontend geladen, was zur Erstellung von Backend-Sitzungen und potenziellen Sitzungssperren führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37617>
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/pull/36368>
* _AKP2E-2729_: [CLARIFICATION] Funktionsanforderung ADA-Compliance
   * _Hinweis reparieren_: Das System stellt jetzt die ADA-Compliance sicher, indem nicht unterstützte CSS-Eigenschaften entfernt und in der Datei print.css durch unterstützte ersetzt werden. Zuvor führte die Verwendung nicht unterstützter CSS-Eigenschaften zu Problemen mit der Browserkompatibilität.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _AKP2E-2529_: Ausnahme bei der Überprüfung des Guthabenkartensaldos bei aktiviertem Recaptcha
   * _Hinweis reparieren_: Benutzer können den Restbetrag der Geschenkkarte im Bildschirm zum Anzeigen und Bearbeiten des Warenkorbs abrufen. Bisher wurden diese Details nicht angezeigt, während reCAPTCHA aktiviert war.
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _AC-12128_: [Cloud] Sicherheitslücke vom Typ Prototype.js CVE-2020-27511
   * _Hinweis reparieren_: Sicherheitslücke CVE-2020-27511 sollte behoben werden
   * _GitHub-Codebeitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
