---
title: Versionshinweise
description: Erfahren Sie mehr über die für Adobe Commerce verfügbaren Patches und die von ihnen gelösten Probleme.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: aa52895b45363ca0fb3585f603bfe66a73803427
workflow-type: tm+mt
source-wordcount: '13735'
ht-degree: 0%

---

# Versionshinweise

Die [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) bietet individuelle Patches, die von Adobe und der Magento Open Source Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce oder Magento Open Source verfügbar sind, anwenden, wiederherstellen und anzeigen. Sie können Patches auf Adobe Commerce- und Magento Open Source-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.

>[!INFO]
>
>Siehe [Anwenden von Patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) für Anweisungen zum Anwenden von Patches auf Ihre Adobe Commerce- oder Magento Open Source-Projekte. Siehe [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch für Softwareaktualisierungen , um eine vollständige Liste der veröffentlichten Patches zu lesen.

>[!INFO]
>
>Informationen zu [!DNL quality patches] , die von der Gemeinschaft zur Magento Open Source erstellt wurden, siehe [Versionshinweise](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die standardmäßige Versandadresse im Checkout-Versandschritt automatisch mit einer zuvor ausgewählten In-Store-Abholadresse gefüllt wird.
* **ACSD-52041** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem die Fehlermeldung angezeigt wird: *[FEHLER] [!DNL Page Builder] 5 Sekunden lang gerendert wurde, ohne Sperren freizugeben.* wird im Chrome-Browser angezeigt, wenn Inhalt gespeichert wird, der mit [!DNL Page Builder].
* **ACSD-52095** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem die `manage_stock` wurde in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt.
* **ACSD-51358** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem das Entfernen einer geplanten Aktualisierung ohne Enddatum dazu führt, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.
* **ACSD-48070** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem beim Bearbeiten einer geplanten Aktualisierung eine Ausnahme Trigger auftrat.
* **ACSD-51890** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die [!UICONTROL Submit review] -Schaltfläche kann mehrmals ohne [!DNL Google reCAPTCHA] Validierung von v3.
* **ACSD-51984** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem die Option deaktiviert war *[!UICONTROL Use Default Value]* und *[!UICONTROL non-default product field]* -Werte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert.
* **ACSD-52398** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *Die angeforderte Menge ist nicht verfügbar* tritt auf, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren.
* **ACSD-52786** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem eine Bedingung für Katalogregeln auftritt *SKU ist* gilt für alle Produkte, die mit der jeweiligen SKU beginnen.
* **ACSD-52921** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem ein interner Fehler auftritt, wenn von GraphQL Warenkorbdetails angefordert werden, wenn ein nicht vorrätig konfigurierbares Produkt im Warenkorb vorhanden ist.
* **ACSD-51683** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem eine anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
* **ACSD-52133** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
* **ACSD-52202** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem sich die verkaufbare Menge des Standardbestands fälschlicherweise auf 0 ändert, wenn ein nicht standardmäßiges Lager bei Bestellerfüllung auf 0 qty geändert wird.
* **ACSD-51265** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem mit `catalog_product_price` Neuindizierungsleistung bei zu vielen gebündelten Produkten im System.
* **ACSD-52831** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Kunden keine begebbaren Anführungsaufträge platzieren können, wenn [!DNL Google reCAPTCHA v3 Invisible] aktiviert ist.
* **ACSD-51845** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen nicht über die asynchrone Massen-REST-API aktualisiert werden können.
* **ACSD-52815** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die Eingabe für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für ein Standardbestand.
* **ACSD-51149** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem &quot;Geplanter ImportExport mit aktivierten Katalogberechtigungen&quot;Indexer ungültig macht und dann Cache-Leerungen nach Cron löscht.
* **ACSD-50815** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem die Dezimalzahl für ein einfaches Produkt nicht für eine neue Option &quot;Gebündeltes Produkt&quot;verwendet werden kann.
* Aktualisierte Versionen für ACSD-47803.
* Der Titel für ACSD-51892 wurde aktualisiert.
* ACSD-51379 aktualisiert.
* ACSD-49970-v2 wurde aktualisiert.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem ein Admin-Benutzer nach Auswahl einer Store-Ansicht beim Erstellen einer neuen Bestellung in Admin nicht ordnungsgemäß umgeleitet wird.
* **ACSD-50813** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem Admin keine gebündelten Produkte hinzufügen konnte, die einen Schrägstrich in der SKU enthielten, mit der [!UICONTROL Add Products by SKU] -Funktion auf die Admin-Bestellung hinzu.
* **ACSD-51630** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem eine große Anzahl von Systemnachrichten das Herunterladen von Administrationsseiten verlangsamt.
* **ACSD-51853** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.7) - Behebt das Problem, dass kopierte Textstile bei Verwendung der [!UICONTROL Page Builder].
* **ACSD-52160** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem das Ergebnis der Produktvalidierung für die Warenkorbpreisregel nicht ordnungsgemäß anhand der Regelbedingung &#39;Wenn ein Artikel im Warenkorb mit Alle/Beliebige dieser Bedingungen gefunden/NICHT GEFUNDEN wurde&#39; ausgewertet wurde.
* **ACSD-51636** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem der Unternehmensadministrator keine neuen Benutzer aus dem Abschnitt &quot;Kundenkonto&quot;hinzufügen kann, obwohl er über alle erforderlichen Rollen und Berechtigungen verfügt.
* **ACSD-51739** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem ein Fehler zurückgegeben wird, wenn die Variable `structure_id` wird in einer GraphQL-Anfrage von CompanyTeam angefordert.
* **ACSD-51857** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die langsame Leistung der `aggregate_sales_report_bestsellers_data` Cron-Bericht zu &quot;large sales_order&quot;und `sales_order_item` Datenbanktabellen waren auf die Art und Weise zurückzuführen, wie die Hauptdatenabfrage geschrieben wurde.
* **ACSD-48448** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass bei einem Race-Condition-Problem während der Auftragsabbrüche ein Fehler auftritt, der zu einem doppelten Eintrag in der `inventory_reservation` Tabelle.
* **ACSD-52689** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.6) - Behebung des Problems, bei dem Bilder nicht mit der REST-API in den Amazon S3-Speicher hochgeladen werden können.
* **B2B-2674** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fügen Sie der GraphQL-Abfrage 1customAttributeMetadata1 eine Caching-Funktion hinzu.
* Es wurden neue Versionen für ACSD-44938 hinzugefügt.
* Anforderungen für ACSD-46988 hinzugefügt.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5) - Behebt den Datenbankrollback-Befehl für einen Fall, in dem der DB-Dump Trigger und einen *delimiter* SQL-Befehl.
* **ACSD-50512** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebt die *Fehler: Der herunterladbare Link steht nicht im Zusammenhang mit dem Produkt. Überprüfen Sie den Link und versuchen Sie es erneut.* Fehler, der beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update auftritt.
* **ACSD-50949** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem der Preisfilter in der erweiterten Suche keine richtigen Ergebnisse zurückgibt, wenn er entlang des SKU-Filters verwendet wird.
* **ACSD-51645** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt den Fehler, der beim Speichern einer neuen Warenkorbpreisregel ausgegeben wird, wenn die Erweiterung `Magento_OfflineShipping` deaktiviert ist.
* **ACSD-50895** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert.
* **ACSD-51102** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht richtig indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.
* **ACSD-50368** (für Adobe Commerce und Magento Open Source >= 2.4.3 &lt;2.4.5) - Behebung des Problems, bei dem der `group_id` wird ignoriert, wenn ein Kunde über die asynchrone REST-API oder die asynchrone Bulk-REST-API erstellt wird.
* **ACSD-51497** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem ein Kunde eine Katalogseite nicht nach benutzerdefiniertem Attribut des Dropdown-Typs sortieren kann.
* **ACSD-51408** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt; 2.4.7) - Behebung des Problems, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Backordered]*.
* **ACSD-51735** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Ordered]* wenn der Produktbestand *0*.
* **ACSD-51792** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem eine Seite nicht über das Impressionsereignis verfügt, wenn [!DNL Google Tag Manager] 4 ist aktiviert.
* **ACSD-51471** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein Admin-Benutzer ein geplantes Update für ein gebündeltes Produkt, das ein einfaches Produkt verwendet, das selbst über eine geplante Aktualisierung verfügt, nicht speichern kann.
* **ACSD-51700** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt den Fehler, der beim Wechseln von Store-Ansichten auf einer herunterladbaren Produktebearbeitungsseite im Admin auftritt.
* **ACSD-51120** (für Adobe Commerce >=2.3.7 &lt;2.4.3) - Behebung des Problems, bei dem der GraphQL GET-Anforderungscache für CMS-Seiten mit CMS-Bausteinen, die über ein Staging-Update aktualisiert werden, nicht gelöscht wird.
* **ACSD-51240** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem die hochgeladene Datei fehlt, wenn die Registrierung über das Registrierungsformular für das Unternehmen erfolgt.
* **ACSD-51907** (für Adobe Commerce >=2.4.2 &lt;2.4.3) - Behebung des Problems, bei dem ein eingeschränkter Administrator kein Kreditmemo mit Offline-Rückerstattung erstellen kann.
* **ACSD-52148** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem die [!DNL Google V3 reCAPTCHA] Die Administratoranmeldung schlägt gelegentlich fehl.
* **ACSD-51431** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem der Indexstatus angezeigt wird *Arbeit* auch wenn es keine neuen Einträge in der changelog gibt.
* **ACSD-51892** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Leistungsproblems, bei dem Konfigurationsdateien mehrmals geladen werden.
* Veraltete ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die [!UICONTROL Page Builder's] mehrere Fehler verhindern, dass Administratoren ein Produkt ohne Inhaltsberechtigungen speichern.
* **ACSD-51305** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem konfigurierbare nicht vorrätige Kinderprodukte in der GraphQL-Antwort nicht verfügbar sind.
* **ACSD-50621** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem [!UICONTROL Tier Prices] für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn versucht wird, sie in einer Umgebung mit mehreren Websites zu bearbeiten.
* **ACSD-51041** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) - Verbessert die Leistung des Preisindexers.
* **ACSD-51379** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Änderungen am Seitentext über vorgenommen wurden [!UICONTROL Page Builder] nicht gespeichert werden.
* **ACSD-49480** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem nur eine Warenkorbpreisregel auf den Warenkorb angewendet wird.
* **ACSD-51230** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem das Konto für die Geschenkkarte gelöscht wird, wenn eine teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird.
* **ACSD-51238** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem die Inventarquelle beim Aktualisieren konfigurierbarer Produkte und Bearbeiten des Preises entfernt wird.
* **ACSD-50794** (für Adobe Commerce >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem die Geschenkgutachten oder Geschenkverpackungsdetails nicht in der Datenbank aktualisiert werden, wenn sie über GraphQL entfernt werden.
* **ACSD-51528** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem die *x_forwarded_for* -Spalte enthält Null-Werte in *sales_order* Tabelle.
* **ACSD-50849** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches zu einer Inkongruenz zwischen Positionen und Auswahl der vorhandenen Produkte führt.
* **ACSD-51294** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem GTM/GA-Preis, -Menge, -Steuer, -Versand und -Umsatz als Zeichenfolge an gesendet werden [!DNL Google Analytics] und GTM.
* **ACSD-51204** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein vollständig verkauftes Produkt nach der Erstellung eines Kreditmemos nicht wieder auf Lager ist.
* **ACSD-51291** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Behebung des Problems, bei dem eingeschränkte Administratoren mit Zugriff auf eine Website dem Produkt, das mehreren Websites zugewiesen ist, Bilder/Videos hinzufügen können.
* Es wurden neue Versionen für ACSD-50336 hinzugefügt.
* Ersetzt Patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4) || >=2.4.4-p1 &lt;2.4.6) - Behebung des Problems, bei dem Recaptcha v2 nach Übermittlung einer fehlgeschlagenen Zahlung nicht neu geladen wird.
* **ACSD-50817** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Optimiert den Cron-Auftrag `sales_clean_quotes` um schneller zu laufen.
* **ACSD-49392** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) - Behebt das Problem, bei dem der Auftragsstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt zu &quot;geschlossen&quot; wird.
* **ACSD-51036** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem die Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen zu einem Überschreiben der Versandstatusinformationen im [!UICONTROL Items Ordered] Tabelle.
* **ACSD-50858** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Verbessert die Leistung beim Laden von Bannerinhalten.
* Es wurden neue Versionen für MDVA-39305-v2, ACSD-45169 hinzugefügt.
* Aktualisierte Patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (für Adobe Commerce und Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Behebung des Problems, bei dem E-Mails zur Produktwarnung nicht gesendet werden, wenn ein Produkt wieder vorrätig ist oder der Preis geändert wird.
* **ACSD-50367** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem der Export von Kundenadressen nicht funktioniert, wenn ein Attribut mit mehreren ausgewählten Kundenadressen ohne Werte erstellt wird.
* **ACSD-49877** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die automatische Videowiedergabe auf einem Mobilgerät nicht funktioniert [!DNL Safari] wenn das Video direkt mit einer Remote-Videodatei und nicht mit einem Streaming-Dienst verknüpft ist.
* **ACSD-50165** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *Die Datei kann nicht gelöscht werden. Warning!unlink: No such file or directory* beim Leeren des JS/CSS-Cache vom Administrator.
* **ACSD-49737** (für Adobe Commerce und Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Behebung des Problems, bei dem ein Gutschein fälschlicherweise als nach einer fehlgeschlagenen Kartenzahlung als verwendet markiert wurde.
* **ACSD-50814** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem ein Admin-Benutzer kein Kreditmemo erstellen kann.
* **ACSD-50116** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem ein Admin-Benutzer keine URL-Neufassung für Unterkategorien der Stufe 3 oder niedriger erstellen kann.
* **ACSD-49513** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5) - Behebung des Problems, bei dem die Synchronisation von Remote-Speicher aufgrund von 0-Byte-Dateien fehlschlägt.
* **ACSD-46683** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem der Versandpreis anzeigt *Noch nicht berechnet*.
* **ACSD-49129** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem die *[!UICONTROL content]* -Attribut (Bildcode base64) wird nicht zurückgegeben in `rest/V1/products/sku/media` API-Antworten für Produktmedien.
* **ACSD-50276** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem das Formular zur Kundenregistrierung auf der Storefront nicht funktioniert, wenn ein Kundenattribut mit Mehrfachauswahl erstellt wird.
* **ACSD-50527** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt den Fehler, der beim Speichern einer Seite mit einem leeren dynamischen Block auftritt.
* **ACSD-49973** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Verbessert die Leistung beim Abrufen gebündelter Produkte über GraphQL.
* **ACSD-51114** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein zufälliges Produkt aus großen Katalogen verschwindet, wenn die asynchrone Indizierung aktiviert ist. Verbessert die Leistung der asynchronen Neuindizierung für große Kataloge.
* **B2B-2598** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Hinzufügen der Caching-Funktion zum [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], und [!UICONTROL storeConfig] GraphQL-Abfragen.
* Es wurden neue Versionen für MDVA-42806, ACSD-48627, ACSD-46815 hinzugefügt.
* Die Patchmetadaten für ACSD-49773, ACSD-47179, ACSD-48300 wurden aktualisiert.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem eine gebrauchsfertige E-Mail per API gesendet wird, wenn die Bestellung nicht abgeholt werden kann.
* **ACSD-49822** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Aktualisierungen in der [!UICONTROL Requisition List] nicht auf der Seite angezeigt werden. [!UICONTROL Print Requisition List].
* **ACSD-48771** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt das Problem mit der Aktualisierung des Spaltenblock-Inhaltstyps von älteren [!DNL Page Builder] Versionen.
* **ACSD-49464** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Rechnungen, Sendungen und Credit Memos nicht aus dem Archiv verschoben werden, wenn die orderId unterschiedlich ist.
* **ACSD-49773** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird.
* **ACSD-49748** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Einladungen nicht gesendet werden können.
* **ACSD-49502** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem der herunterladbare Link nach der Anwendung eines Staging-Updates auf das herunterladbare Produkt nicht ordnungsgemäß aktualisiert wird.
* **ACSD-49527** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die Seitenumbrüche in GraphQL-Unternehmensrollen nicht korrekt angezeigt werden.
* **ACSD-49706** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem der Standardwert für ein visuelles Farbfeldattribut gespeichert wird, wenn kein Wert ausgewählt ist.
* **ACSD-49835** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem der Wert des Kontrollkästchens &quot;Use default&quot;nicht ordnungsgemäß auf Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert wurde.
* **ACSD-49898** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem das Produktnetz eine Ausnahme auslöst, wenn ein gebündeltes Produkt einen Sonderpreis von mehr als 1000 aufweist.
* **ACSD-50234** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.5) - Behebt das Problem mit dem falschen Kundennamen in der Bestätigungs-E-Mail, wenn eine Bestellung mit [!DNL PayPal].
* **ACSD-49960** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem das Filtern nach Datum für das Kundenbestellungsraster nicht funktioniert.
* **ACSD-49849** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem die E-Mail von Kunden durch ersetzt wurde [!DNL PayPal] E-Mail beim Einfügen einer Bestellung mit [!DNL PayPal Express] über GraphQL.
* **ACSD-49839** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die gemeinsame Katalogpreisstruktur und -struktur in Admin einen Fehler auslöst, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU enthalten.
* **ACSD-49970** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt fehlerhafte Handhabung von GraphQL-Fehlern bei [!DNL New Relic] Die Berichterstellung ist aktiviert.
* **ACSD-50260** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem die GraphQL-Produktsuchergebnisse nur auf 10.000 Ergebnisse beschränkt sind.
* **ACSD-48813** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem bei der Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute angezeigt werden.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.3) - Behebung des Problems, bei dem eine auf dem Attribut Ja/Nein basierende Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt.
* **ACSD-47704** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem das gebündelte Produkt nur den Preis von in Lagerprodukten anzeigt.
* **ACSD-49370** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die *Datum/Uhrzeit* Das Produktattribut enthält *FilterMatchTypeInput* in das GraphQL-Schema ein.
* **ACSD-48807** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem Kundenproduktüberprüfungen nicht durch die Storeübersicht über GraphQL gefiltert werden.
* **ACSD-49433** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem der Standardbetrag als Zwischensumme im Warenkorb für Geschenkkarten mit einem offenen Betrag angezeigt wird.
* **ACSD-48866** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem ein Fehler auftritt, wenn RSS-Dienste für Kategorien angefordert werden.
* **ACSD-48784** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die Kundensegmentpreise fälschlicherweise zwischen Kundengruppen zwischengespeichert wurden.
* **ACSD-48857** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein Benutzer nach der Bearbeitung mit Page Builder keine Änderungen speichern kann.
* **ACSD-49065** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Anführungselemente im Admin nicht sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.
* **ACSD-49179** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem im Bestellbericht falsche Beträge angezeigt werden, wenn verschiedene Währungen für verschiedene Geschäfte verwendet werden.
* **ACSD-49286** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein Produkt einem Warenkorb zweimal hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.
* **ACSD-49574** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Fügt Funktionen hinzu, um GitCard-Produktupdates in einem Warenkorb über GraphQL zu unterstützen.
* Aktualisierter Patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (für Adobe Commerce >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem beim Platzieren einer Bestellung mit einem verhandelbaren Angebot anstelle einer neuen Versandadresse die standardmäßige Versandadresse verwendet wird.
* **ACSD-48059** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Händler die &quot;[!UICONTROL Match product by rule]&quot; in der Kategorie.
* **ACSD-48216** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem [!UICONTROL AUTO_INCREMENT] des [!UICONTROL inventory_source_item] -Tabelle erhöht sich auf [!UICONTROL UPDATE] Vorgang.
* **ACSD-47908** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) - Behebt den Fehler &quot;Ein Wert kleiner oder gleich 0 wird erwartet&quot;bei der Auswahl der Quelle und der Menge im Versandschritt während des Checkout.
* **ACSD-49497** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem eine Bestellung nach dem Versand im Verarbeitungsstatus verbleibt und eine teilweise Rückerstattung erfolgt.
* **ACSD-48694** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem der Fehler &quot;Ungültige Statusänderung angefordert&quot;verhindert, dass ein Kunde eine Bestellung aufgibt.
* **ACSD-49013** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem die E-Mail-Bestätigung beim Erstellen von Kunden mit Bulk API nicht in das Gebietsschema der Website übersetzt wird.
* **ACSD-48164** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem ein eingeschränkter Administrator keinen Wert auf Website-Ebene speichern kann.
* **ACSD-48404** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem &quot;Kategoriepaginierung speichern = Ja&quot;beim Drücken der Zurück-Taste des Browsers einen Fehler verursacht.
* **ACSD-48634** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt JS-Fehler auf einer Staging-Aktualisierungsseite, wenn &quot;[!UICONTROL Google Analytics Content Experiments]&quot; aktiviert ist.
* **ACSD-49042** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann.
* Aktualisierte Patches: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (für Adobe Commerce und Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabbruchbenachrichtigungen gesendet werden.
* **ACSD-48661** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem das Kreditlimit des Unternehmens größer als 999 ist und das Kommatrennzeichen die Speicherung des Unternehmens aufgrund eines Validierungsfehlers verhindert.
* **ACSD-48773** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die E-Mail-Vorlage für die Punkte, die belohnt werden, aus dem falschen Speicher stammt.
* **ACSD-48587** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte-Widgets verhindern, dass sie übereinstimmende Produkte anzeigen.
* **ACSD-48212** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem der Produktimport das Produkt der falschen Quelle zuordnet.
* **ACSD-47988** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem beim Produktexport HTML-Tags aus der Produktbeschreibung des Seitenaufbaus entfernt werden.
* **ACSD-48366** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem das Produktbild nicht in der E-Mail-Vorlage &quot;Zurück zu Lager&quot;angezeigt wird.
* **ACSD-48417** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem ein SQL-Fehler angezeigt wird, nachdem eine Produktplanänderung erstellt und ein anderes Produkt gespeichert wurde.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem die Neuindizierung des Produktpreises nicht funktioniert, wenn das Bundle-Produkt keiner Website zugewiesen ist.
* **ACSD-48262** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem Produkte nicht auf der Vorderseite sichtbar sind, wenn die Einstellung &quot;Alle Produkte pro Seite zulassen&quot;auf &quot;Ja&quot;gesetzt ist.
* **ACSD-48293** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4) - Behebung des Problems, bei dem die zusammengesetzten Produkte nicht mehr vorrätig sind, wenn die ausverkauften Kindprodukte wieder vorrätig sind.
* **ACSD-47520** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem Kunden bei der Erstellung eines Kreditmemo Punkte verlieren.
* **ACSD-48044** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem das Anwenden mehrerer Geschenkkarten auf eine Bestellung mit mehreren Sendungen verhindert, dass Bestellungen aufgegeben werden.
* **ACSD-48300** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem eine Rückgabe nicht erstellt werden kann, wenn das konfigurierbare Produkt entfernt wird.
* **ACSD-47910** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt die Frage fehlender Bestellungen, Rechnungen, Sendungen und Kreditkarten in den jeweiligen Entitätsrasten.
* **ACSD-47292** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem nicht vorrätige gebündelte Produkte nicht in der GraphQL-Antwort verfügbar sind, wenn &quot;Nicht vorrätige Produkte anzeigen&quot;auf &quot;Ja&quot;eingestellt ist.
* **ACSD-48234** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem das Katalogsuchergebnis eine falsche Kategorieelementanzahl anzeigt, wenn die Option &quot;Nicht auf Lager anzeigen&quot;aktiviert ist.
* **ACSD-48313** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5) - Behebung des Problems, bei dem die Spalte &quot;konfigurierbare Varianten&quot;nicht analysiert wird, wenn der Attributwert ein Komma enthält. Derselbe Parsing-Algorithmus wird für &quot;additional_attributes&quot;verwendet.
* **ACSD-48627** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem das konfigurierbare nicht vorrätige Produkt beim Senden einer GraphQL-Anfrage zum Abrufen von Warenkorbdetails einen Fehler verursacht.
* Aktualisierter Patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem SEO-freundliche URLs nicht für Produkte generiert werden, die *url_key* -Attribute auf der Store-Ansichtsebene überschrieben werden.
* **ACSD-46865** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem das Raster Versand und Credit Memo bei Aktivierung der asynchronen Indizierung nicht gefüllt wird.
* **ACSD-47004** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem die MwSt nicht auf eine Rechnungsadresse ohne MwSt-ID angewendet wird.
* **ACSD-47803** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem konfigurierbare nicht vorrätige Produktmuster als verfügbar angezeigt werden.
* **ACSD-47137** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Erhöht die Ladegeschwindigkeit der Bildergalerie, wenn der Ordner pub/media sehr groß ist.
* **ACSD-46770** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem E-Mails mit Administratorbestellungen gesendet werden, selbst wenn die Variable *Bestätigung der E-Mail-Bestellung* deaktiviert ist.
* **ACSD-47955** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem GraphQL den Rabatt nicht korrekt anzeigt.
* **ACSD-46617** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem die *Weiter zum Checkout* Schaltfläche ist grau ausgeblendet, auch wenn die Zwischensumme größer als die konfigurierte ist *Mindestauftragsbetrag*.
* **ACSD-47079** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus von Unterprodukten über die REST-API-POST /rest/V1/inventory/source-items ändert.
* **ACSD-47336** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fehlerbehebungen *Etwas ist schiefgelaufen.* Fehler beim Verwerfen von Benachrichtigungen in Commerce Admin.
* **ACSD-47559** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem der Bereich &quot;E-Mail-Vorlage in der Vorschau&quot;nicht vollständig sichtbar ist.
* **ACSD-47920** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem Bestellungen auch dann über die Rest-API als Gastbenutzer aufgegeben werden können, wenn die *Gastauschecken zulassen* deaktiviert ist.
* Ersetzte Patches: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem ein Administrator mit eingeschränktem Zugriff auf einen bestimmten Bereich Produktüberprüfungen nicht löschen kann.
* **ACSD-47107** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5) - Behebung des Problems, bei dem der Rabatt auf die Katalogpreisregel auf benutzerdefinierte Produktoptionen angewendet wird.
* **ACSD-47232** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem Gutscheine mit Gesamtgewichtsbedingungen nicht im Admin angewendet werden können.
* **ACSD-46519** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.6) - Behebung des Problems, bei dem die GraphQL-categoryList-Anfrage eine falsche product_count für eine Ankerkategorie zurückgibt.
* **ACSD-47027** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebt eine langsame GraphQL-Anfrage updateCompanyRole .
* **ACSD-47666** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem die Filterfunktion im Raster Admin > System > Berechtigungen > Benutzerrollen > Rolle > Rollenbenutzer nicht funktioniert.
* **ACSD-47497** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem die Registerkarte &quot;Dienste&quot;nicht in der Konfiguration unter dem Admin angezeigt wird.
* Aktualisierter Patch: ACSD-47743.
* Ersetzte Patches: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3) - Behebt die _Versuch, auf den Array-Versatz für den Wert des Typs &quot;bool&quot;zuzugreifen_ Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte auf PHP 7.4.
* **ACSD-47332** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem Cron mit einem Fehler fehlschlägt, der nur bei Ausführung zwischen 00:00 und 00:59 UTC gemeldet wird.
* **ACSD-47280** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem das Deaktivieren der Funktion für freigegebene Kataloge in einem bestimmten Bereich nicht ordnungsgemäß funktioniert.
* **ACSD-47106** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden kann.
* Aktualisierter Patch: ACSD-45143.

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
* Aktualisiert: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Veralteter Patch: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem die Kategoriebaumanfrage auf 20 Kategorien beschränkt ist.
* **ACSD-45781** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.2*) - Behebt das Problem, dass das Feld für die Vorderseite des Stores nicht auf einem Mobilgerät angezeigt wird.
* **ACSD-46192** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;2.4.5*) - Behebt das Problem mit der Verwendung des `async/bulk/V1/configurable-products/bySku/options` -Endpunkt.
* **ACSD-46404** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebung des Problems, bei dem sich ein Admin-Benutzer nach einem Upgrade auf 2.4.4 nicht anmelden kann.
* Aktualisiert: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

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
* **MDVA-44562** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Behebung des Problems, bei dem die nicht standardmäßige Store-ID für Anführungszeichen-Elemente von der standardmäßigen Store-ID überschrieben wird, obwohl die GraphQL-Anforderung aus der nicht standardmäßigen Store-Ansicht stammt.
* **MDVA-43167** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem die Massenaktion des Administrationsnetzwerks nicht für mehrere Seiten gilt, wenn der Admin-Benutzer alle Bestellungen auswählt.
* **MDVA-44044** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Behebung des Problems, bei dem ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde.
* **MDVA-42509** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.4*) - Behebung des Problems, bei dem eine CSV-Datei nicht für eine schnelle Bestellung hochgeladen werden konnte, was zu einem *Cookie kann nicht gesendet werden* Fehler.
* Aktualisierte Patches: MDVA-41061, MDVA-42584
* Das Präfix für das neue [!DNL Quality Patches Tool] Patches werden geändert von *MDVA* nach *ACSD* aufgrund interner Prozessänderungen.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem ein zusätzliches Element nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist.
* **MDVA-44887** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebt die *Uncaught SyntaxError: Unerwartetes Token &#39;const&#39;* im Admin-Bereich angezeigt.
* **MDVA-43718** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Fehlerbehebungen *Der Verbraucher ist nicht berechtigt, auf %resources zuzugreifen.* Fehler, der beim Zugriff auf einen freigegebenen Katalog von einer benutzerdefinierten Integration angezeigt wird.
* **MDVA-44660** (*für Adobe Commerce und Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Behebt das Problem, bei dem das Zeichen für Gravis ``` ` ``` konnte nicht für den Vor- und Nachnamen eines Kunden verwendet werden.
* **MDVA-40896** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt die *Fehler: TypeError: Argument 3 an Magento übergeben* Fehler in der asynchronen Produkt-Bulk-API.
* **MDVA-38559** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt die */V1/Customers/search-API* Fehler bei Kunden mit mehr als einem Abonnement.
* **MDVA-44533** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.4*) - Behebung des Problems, bei dem der Rabatt fälschlicherweise auf ein untergeordnetes Bundle-Produkt angewendet wird.
* Aktualisierte Patches: MDVA-41061, MDVA-42269

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, bei dem Produkte *Individuell nicht sichtbar* weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt.
* **MDVA-44100** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem alle FPTs dem letzten Produkt im Warenkorb zugewiesen und für andere Produkte zurückgesetzt wurden.
* **MDVA-43605** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebung des Problems, bei dem Bestelldaten bei Verwendung der Rest-API negative Werte für Zeilensummen zurückgeben.
* **MDVA-43102** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebung des Problems, bei dem die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt.
* **MDVA-43178** (*für Adobe Commerce und Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Behebung des Problems, bei dem ein Kunden-Token für einen benutzerdefinierten Store nicht in GraphQL abgerufen werden kann.
* **MDVA-43859** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, bei dem der Fehler auftrat *Keine solche Entität mit customerId =* wird protokolliert, wenn ein gelöschter Kunde versucht, sich anzumelden.
* **MDVA-44147** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem eine GraphQL-Anfrage keine Anforderungslisten zurückgibt.
* **MDVA-44505** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebt die Probleme, bei denen GraphQL beim Anwenden von Rewards-Punkten die Gesamtsumme nicht aktualisiert und bei denen während der Bestellplatzierung mehrmals eine Speichergutschrift angewendet wird.
* Aktualisierte Patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-3993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebung des Problems, bei dem die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf *Alle*.
* **MDVA-39605** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebung des Problems, bei dem Redis cache TTL (Ablaufdatum) einen falschen Wert hat.
* **MDVA-43862** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Kunde aufgrund einer GraphQL keine Warenkorbelemente aktualisieren kann *UpdateCartItems-Mutation* Fehler.
* **MDVA-43824** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p3 | | >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem beim Abbrechen von Bestellungen mit einem Rabatt ein Fehler angezeigt wird.
* **MDVA-43451** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebt das Problem, bei dem der Fehler auftrat *Der Laden, der angefordert wurde, wurde nicht gefunden. Überprüfen Sie den Speicher und versuchen Sie es erneut.* angezeigt, während Sie einen freigegebenen Katalog für eine bestimmte Website konfigurieren.
* **MDVA-43491** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebung des Problems, bei dem die Beschriftung des Basisbilds beim Importieren von Produkten für eine Website mit mehreren Stores nicht aktualisiert wird.
* **MDVA-43601** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem mit fehlenden Triggern nach vollständiger Neuindizierung.
* **MDVA-42046** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2 | | >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem einem Produktattribut mit einem Datumseingabefeld beim Aktualisieren eines Produkts ein falscher Wert zugewiesen wurde.
* **MDVA-43935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem Upsell-Produkt zweimal angezeigt wird.
* **MDVA-44188** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem vom System ausgegebene E-Mails mit `.-` in -Adressen nicht gesendet werden.
* **MDVA-42283** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Datums-/Uhrzeitformat im Raster der Admin-Reihenfolge für das französische Gebietsschema ungültig ist.
* Aktualisiert: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Hinzugefügte Patchmetadaten für die [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem der Benutzer die Startzeit für eine aktive geplante Aktualisierung bearbeiten kann.
* **MDVA-42410** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem Gutscheinberichte nur die Standardgrundwährung anzeigten.
* **MDVA-41136** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem, bei dem das Ablaufdatum der `mage-cache-sessid` nicht erweitert wird, was zu einer Bereinigung der Kundendaten führt.
* **MDVA-39993** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Behebung des Problems, bei dem Bestandsänderungen, die über die API vorgenommen wurden, nicht auf der Produktseite am Frontend übernommen wurden.
* **MDVA-42855** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem eine neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wurde.
* **MDVA-42645** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Administrator keine Bonuspunkte zurückgeben kann, wenn die Funktion zum Speichern von Guthaben deaktiviert ist.
* **MDVA-43414** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Behebt den schwerwiegenden PHP-Fehler, der beim Ausführen der `inventory.reservations.updateSalabilityStatus` Warteschlangen-Consumer für numerische SKUs.
* **MDVA-41628** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem bestehende eingeschränkte Admin-Benutzer Zugriff auf die neuen Ressourcen erhalten, wenn neue Module hinzugefügt werden.
* **MDVA-43348** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, dass bei der Anforderung der Geschenkkarte GraphQL ein Fehler angezeigt wird, wenn `gift_card_options` contain *uid*.
* **MDVA-39546** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Startdatum für die Staging-Aktualisierung während der Bearbeitung auf ein früheres Datum als das aktuelle Datum festgelegt werden konnte.
* **MDVA-42950** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem Videos nicht auf der Produktseite wiedergegeben werden.
* **MDVA-42689** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, bei dem Adobe Commerce eine *Verletzung von Integrationsbeschränkungen* Fehler beim Aktualisieren der Produktkategorien während des Imports.
* **MDVA-41229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem im Backend verfügbare Bilder nach einem konfigurierbaren Produktimport nicht im Frontend angezeigt werden.
* **MDVA-43731** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt das Problem, bei dem *Synonyme suchen* funktioniert nicht mehr, wenn ein Wert in *Mindestens passende Begriffe*.
* **MDVA-43232** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebt das Problem, dass Produkte in [!DNL Visual Merchandiser] durch &quot;Special Price To Bottom/Top&quot;verursacht beim Speichern der Kategorie einen Fehler.
* **MDVA-43726** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.3*) - Behebung des Problems, bei dem die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer partiellen Neuindizierung nicht angewendet werden konnte.
* Aktualisierte Patches: MDVA-36464, MDVA-37478, MDVA-38608
* Hinzugefügte Patchmetadaten für die [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem Produktpreisattribute für eine bestimmte Website nicht über die REST-API aktualisiert werden können.
* **MDVA-41350** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem eine Ausnahme ausgelöst wird, wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt in einer Bestellung außerhalb seines Aufgabenbereichs durch die SKU hinzufügt.
* **MDVA-42269** (*für Adobe Commerce und Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Behebung des Problems, bei dem sich ein Admin-Benutzer aufgrund der *TypeError: strtotime() erwartet, dass der Parameter 1 eine Zeichenfolge ist, null wird angegeben* Fehler.
* **MDVA-40830** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Store-Guthaben während der Bestellplatzierung mehrmals angewendet wird.
* **MDVA-42237** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem ein konfigurierbarer Produktspezialpreis nach Änderungen am Unterproduktpreis nicht aktualisiert wird.
* **MDVA-42520** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem der Steuersatz zweimal angewendet wird, wenn *Grenzüberschreitenden Handel aktivieren* verwendet.
* Aktualisiert: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Veraltetes Patch: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.4.5*) - Behebung des Problems, bei dem durch die Aktualisierung eines Massenattributs nur nach einer Änderung eine URL-Neufassung für den Standardspeicher erstellt wird *Produktsichtbarkeit*.
* **MDVA-43091** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem bei der Bestellung eines Bundle-Produkts vom Admin im Backend der Fehler auftritt *Für dieses Produkt kann keine Dezimalzahl verwendet werden*.
* **MDVA-40816** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem verwandte Produktregeln Produkte aus nicht in den Regelbedingungen definierten Kategorien anzeigen.
* **MDVA-41305** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem die GraphQL-Mutation nach dem Hinzufügen zur Wunschliste keine konfigurierbaren Produktoptionen zurückgibt.
* **MDVA-39181** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem verwandte Produktregeln Produkte aus nicht in den Regelbedingungen definierten Kategorien anzeigen.
* **MDVA-42584** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem der konfigurierbare Lagerstatus im Backend nicht aktualisiert wird, nachdem Menge und Lagerstatus über Import oder API geändert wurden.
* **MDVA-40175** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt das Problem, bei dem *Klicken Sie auf die Versandmethode ändern .* zeigt keine Optionsfelder an, mit denen Versandmethoden im Admin während der Neuanordnung ausgewählt werden können.
* **MDVA-42768** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebung des Problems, bei dem für konfigurierbares Produkt der reguläre Preis 0 angezeigt wurde, wenn *Nicht auf Lager anzeigen* ist Ja.
* **MDVA-43201** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem bei der Kundenanmeldung bei der Verwendung des DOB-Attributs mit bestimmten Gebietsschemata ein Fehler auftritt.
* Aktualisiert: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem Datumsfilter nicht ordnungsgemäß funktionierten, wenn sich die Adobe Commerce-Zeitzone von der lokalen Zeitzone der Umgebung unterscheidet.
* **MDVA-42657** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem der Admin-Benutzer nicht in der Lage ist, Kategorien in den Kundensegmentbedingungen auszuwählen.
* **MDVA-42806** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, bei dem ein *Registrierung neuer Unternehmen* E-Mail wird jedes Mal gesendet, wenn ein bestehendes Unternehmen über die REST-API aktualisiert wird.
* **MDVA-37984** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, bei dem der [!DNL Visual Merchandiser] *Produkt nach Regel abgleichen* -Funktion Produkte nicht korrekt mit Staging-Updates filtert.
* **MDVA-40488** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden.
* **MDVA-42507** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem der vollständige Seiten-Cache nach dem Anwenden eines Staging-Updates für die Warenkorbregel bereinigt wird.
* **MDVA-39163** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebung des Problems, bei dem Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert wird und Produkte im Warenkorb aus der Gastsitzung stammen.
* **MDVA-38626** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Administrator mithilfe der [!DNL PayPal Payflow Pro] Zahlung.
* **MDVA-38666** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.3.6*) - Behebung des Problems, bei dem der Admin-Benutzer die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern kann.
* **MDVA-38526** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem der Administrator nicht auf die [!DNL Site-Wide Analysis tool].
* Aktualisierte Patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Benutzer den 500-Fehler erhalten, nachdem die *image-messages* -Cookie, wenn es bereits vorhanden ist, aber keine neuen Nachrichten vorhanden sind.
* **MDVA-41139** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebung des Problems, bei dem konfigurierbare Produkte nach dem Produktimport aus &quot;Nicht auf Lager&quot;werden, wenn die Menge eines einfachen Produkts = 0 für eine seiner Quellen beträgt.
* **MDVA-42326** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem Kunden nach einem Sitzungs-Timeout beim Checkout einen Fehler erhalten, selbst wenn der beständige Warenkorb aktiviert ist.
* **MDVA-42341** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, bei dem der `categoryList` GraphQL-Abfrage filtert keine Ergebnisse, wenn eine Anforderung die Kopfzeile Store enthält.
* **MDVA-38393** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wurde.
* **MDVA-39153** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem ein Rabattbetrag bei der Neubestellung in der Admin-Konsole falsch berechnet wurde.
* Aktualisierte Patches: MDVA-28993, MDVA-41061, MDVA-35984

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Admin-Benutzer nach dem Löschen der Website nicht auf das Raster des Kunden zugreifen können.
* **MDVA-40311** (*für Adobe Commerce und Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Behebung des Problems, bei dem Admin-Benutzer die Fehlermeldung erhalten *Ungültige Sicherheit oder Formularschlüssel. Aktualisieren Sie die Seite* nach der Anmeldung beim Administrator, wenn der benutzerdefinierte Admin-Pfad konfiguriert und der geheime Schlüssel aktiviert ist.
* **MDVA-41631** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem Benutzer beim Versuch, Bestellinformationen ohne optionale *Telefonnummer* -Wert über GraphQL.
* **MDVA-27239** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem Crosssell-Produkte nicht angezeigt werden.
* Aktualisiert: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-317 1.

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
* Aktualisierte Patches: MDVA-3382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem es nicht möglich ist, eine neue zu erstellen oder eine vorhandene geplante Aktualisierung für ein Produkt zu bearbeiten, wenn das Enddatum zuvor entfernt wurde.
* **MDVA-41046** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem einfache Produkte mit benutzerdefinierten Optionen für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind.
* **MDVA-40545** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem nur der erste Knoten für eine Seite abgerufen wurde, selbst wenn mehr als ein Knoten für dieselbe Seite vorhanden war.
* **MDVA-41164** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Behebung des Problems, bei dem ein Admin-Benutzer ein Unternehmen mit einem benutzerdefinierten Kundenattribut vom Typ Datei oder Bild nicht speichern oder bearbeiten kann.
* **MDVA-39229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, durch das nach der Aktualisierung der Staging-Update-Startzeit der Katalogregel der folgende Fehler angezeigt wird: *Cron Job staging_synchronize_entity_period hat einen Fehler: Das aktive Update kann nicht gelöscht werden.*
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

* **MDVA-40262** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebung des Problems, bei dem GraphQL-Suchabfragen nicht in gängigen Suchbegriffen in der Admin-Konsole angezeigt werden.
* **MDVA-40601** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem Benutzer beim Versuch, Informationen über die durch geplante Aktualisierung über GraphQL geänderte Kategorie zu erhalten, einen Fehler erhalten.
* **MDVA-37234** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem beim mehrfachen Hinzufügen eines Artikels zum Warenkorb (parallele Anfrage) für dieselbe SKU ein doppeltes Zeilenelement für dieselbe Warenkorb-ID erstellt wurde.
* **MDVA-33606** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Behebt das Problem, dass Benutzer eine *Eindeutige Einschränkungsverletzung* Fehler beim Speichern einer einer Hierarchie zugewiesenen CMS-Seite.
* **MDVA-31590** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Behebung des Problems, bei dem Benutzer Attribute nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisieren können.
* **MDVA-36309** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem die Produktsuche nach Attributen in den Admin Rastern langsam ist.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem die Rechnung mit FPT eine falsche Gesamtsumme anzeigt, wenn die Bestellung vom Store-Guthaben bezahlt wird.
* **MDVA-37364** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.3*) - Behebung des Problems, bei dem das benutzerdefinierte Kundenattribut des Datumstyps die Rasterbenutzeroberfläche des Kunden beschädigt.
* **MDVA-39195** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebt das Problem, bei dem *Zum Warenkorb hinzufügen* auf der Kategorieseite inaktiv war, wenn die Umleitung zum Warenkorb aktiviert war.
* **MDVA-37115** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebt das Problem, bei dem ein unnötiges *Nur 0 links* wird auf der konfigurierbaren Produktseite angezeigt.
* **MDVA-39521** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebung des Problems, bei dem der Benutzer keine Versandadressen über GraphQL auf den Warenkorb mit einer leeren Telefonnummer setzen kann.
* **MDVA-39384** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Behebung des Problems, bei dem das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wurde.
* **MDVA-39043** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.3*) - Behebung des Problems, bei dem der Administrator mit eingeschränktem Zugriff beim Versuch, die *Produkte* Widget zur CMS-Seite.
* **MDVA-39966** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem bei der Bereitstellung falscher Gebietsschemata.
* **MDVA-38852** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Behebung des Problems, bei dem der Katalog-Inventar von Design Tabellen für Aktualisierungen sperrt, die die Leistung bei mehreren parallelen Bestellungen erheblich reduzieren.
* **MDVA-39986** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebung des Problems, bei dem der Benutzer mit dem Safari-Browser keine Bestellung in der Admin-Konsole in MacOS aufgeben kann.
* **MDVA-38447** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt zwei Probleme: bei denen das *Nicht sichtbar* konfigurierbare untergeordnete Produkte werden in der GraphQL-Antwort zurückgegeben und die MySQL-Abfrage für die GraphQL-Produktabfrage mit Kategoriefilter optimiert.
* **MDVA-40134** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem GraphQL verwandte Produkte nicht zurückgibt, wenn der freigegebene Katalog aktiviert ist.
* **MDVA-39935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem der GraphQL konfigurierbare untergeordnete Produkte zurückgibt, die auf Website-Ebene deaktiviert sind.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebt das Problem, bei dem der *Aufrufen einer Member-Funktion getId()* -Fehler wird auf der Seite mit den Bestelldetails in der Admin-Konsole angezeigt.
* **MDVA-34948** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem mit langwierigen Abfragen wie `GET_LOCK`.
* **MDVA-39305** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem registrierte Kunden sich nicht mit aktiviertem Google Captcha anmelden können.
* **MDVA-37897** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem mit einer falschen Umleitung, wenn ein Kunde versucht, Produkte mit Optionen aus dem Widget &quot;Kürzlich angesehen&quot;hinzuzufügen.

## v1.1.0 {#v1-1-0}

* Patch-Kategorien wurden eingeführt, um das Benutzererlebnis zu verbessern und die Suche nach erforderlichen Patches für Kunden zu erleichtern.
* Die `patches.json` wurde in `support-patches.json`.
* **MDVA-38799** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem herunterladbare Produkte nach dem Erstellen eines Staging-Updates nicht gespeichert wurden.
* **MDVA-37592** (*für Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebung des Problems, das beim Sortieren nach Preis nicht ordnungsgemäß für Produkte mit einem Nullpreis funktionierte, der dem freigegebenen Katalog zugewiesen war.
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
* **MDVA-37288** (*für Adobe Commerce 2.4.2*) - Behebung des Problems, bei dem nach GraphQL-Anfrage falsche Stufenpreise zurückgegeben wurden.
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
* **MDVA-36424** (*für Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Behebung des Problems, bei dem an Seitenaufbauelemente angehängte Medienbilder ausgeblendet werden, wenn der Inhalt wiederholt bearbeitet wird, wenn sich die Backend-Basis-URL von der Store-Basis-URL unterscheidet.
* **MDVA-35984** (*für Adobe Commerce ^2.4.0*) - Behebt das Problem mit falscher Produktmenge und verkaufbarer Menge, nachdem mehrere gleichzeitige Sendungen für dasselbe Produkt erstellt wurden.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermit wird das Problem behoben, dass die GraphQL-Abfrage nicht zwischenspeichert, indem das Kategorie-Cache-Tag verwendet wird.
* **MDVA-33168** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems beim Aktualisieren eines Produktattributs über die API, wenn alle anderen Attribute zu einem leeren Wert geändert werden.
* **MDVA-19640** (*für Adobe Commerce >=2.3.0*) - Behebt das Problem, bei dem [!DNL Advanced Reporting] zeigt keine Daten an.
* **MDVA-11189** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, wenn nach dem Import einer CSV-Datei zur Aktualisierung des Produktbestands Zeilen aus der `cataloginventory_stock` -Tabelle gelöscht.
* **MDVA-26639** (*für Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Behebung des Problems, bei dem bei der Erstellung einer neuen E-Mail-Vorlage zur Bestellbestätigung die Bestellelemente in der Bestellmail fehlen.
* **MDVA-15546** (*für Adobe Commerce >=2.3.0*) - Behebt das Problem, bei dem nach dem Erstellen einer Bestellung eine *Spalte entity_id , wobei Klausel mehrdeutig ist* im Ausnahmeprotokoll angezeigt.
* **MDVA-21095** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem bei Abfragen `INSERT INTO search_tmp` endet nicht nach der Aktualisierung des Massenattributs.
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
* **MDVA-34474** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem beim Hinzufügen eines Produkts zur Anforderungsliste mithilfe der API.
* **MDVA-34591** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Berechnung des Rabatts für Warenkorbregeln für *Maximaler Qty-Rabatt wird auf* und *Rabattschritt &quot;Menge&quot;(Kauf X)*.
* **MDVA-33704** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Behebt das Problem, bei dem der *In store pickup* Die Versandoption wird nicht angezeigt, obwohl sie so konfiguriert ist, dass sie verfügbar ist.
* **MDVA-34928** (*für Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Behebung des Problems, bei dem der Seitenlader unbegrenzt angezeigt wird, nachdem der Store-Guthaben aus der Zahlung entfernt wurde.
* **MDVA-35254** (*für Adobe Commerce >=2.3.1 &lt;2.4.3*) - Behebt die Probleme mit CAPTCHA beim Checkout.
* **MDVA-35569** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebt das Problem, bei dem der *feste Produktsteuern* -Feld wird in der GraphQL-Antwort nicht ausgefüllt, wenn der Status angegeben ist.
* **MDVA-35847** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebung des B2B-Problems, bei dem das Formular &quot;Firmenbenutzer&quot;fehlschlägt, wenn ein benutzerdefiniertes Kundenattribut verwendet wird.
* **MDVA-31307** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebt das Problem, bei dem *Nicht genügend Arbeitsspeicher* Fehler bei bestimmten Kategorien aufgrund von Problemen mit der dynamischen CSP-Whitelisting für zwischengespeicherte Blöcke.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt die falsche *Gestartet* Nachrichtenstatus auf die richtige *complete* Nachricht für Verbraucher `quoteItemCleaner` nach dem Löschen mehrerer Produkte.
* **MDVA-34102** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Stellt fest, dass die Standardspeichermenge für deaktivierte Produkte auf den Seiten &quot;Produktraster&quot;und &quot;Produkt bearbeiten&quot;im Admin-Bereich null ist.
* **MDVA-35286** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem ein Fehler auftritt, wenn ein Kunde Produkte im Warenkorb gebündelt hat und zwischen dem Checkout für mehrere Adressen und dem Checkout für eine Seite wechselt.
* **MDVA-35312** (*für Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Behebt den Antwortcode 500 bei einer leeren GraphQL-Anforderung.
* **MDVA-34189** (*für Adobe Commerce >=2.3.4 &lt;2.4.3*) - Behebt die 503-Byte-Zeitüberschreitung bei [!DNL Visual Merchandiser] Abfragen beim Laden der Seite &quot;Admin-Kategorie&quot;.
* **MDVA-34695** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Fehlerbehebungen negativ `children_count` nach dem Löschen von Kategorien.

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
* **MDVA-33344** (*für Adobe Commerce ^2.3.0*) - Behebt das Problem, bei dem hartcodiert wurde. `rma_item` Die standardmäßige Entitätsattributsatz-ID wird anstelle des Werts aus der Datenbank verwendet.
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
* **MDVA-34469** (*für Adobe Commerce >=2.4.1 &lt;2.4.2*) - Behebung des Problems, bei dem GraphQL-Mutationen auf dem Warenkorb eines Kunden fehlschlagen, wenn mehrere Store-Ansichten verwendet werden.
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
* **MDVA-12304** (*für Adobe Commerce >=2.3.0*) - Erhöht die maximale Anzahl von Cookies von 50 auf 200.
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
* **MDVA-31150** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die Guthaben- und Geschenkkarten-Storekonten nicht vom GET Invoice Rest API-Aufruf zurückgegeben werden, wenn die Rechnung per REST API-Aufruf gepostet wurde und die Bestellung teilweise von den Konto- und Geschenkgutscheinen bezahlt wurde.
* **MDVA-30963** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Behebung des Problems, bei dem die Ergebnisse der Produktfilterung so eingestellt sind, dass sie nur die Werte enthalten, die für *Alle Store-Ansichten* im Admin-Bereich Produkte mit Werten einschließen, die auf der Ebene der Store-Ansicht überschrieben werden.
* **MDVA-29954** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0 | 2.4.2 mit B2B-Erweiterung*) - Behebt das Problem, bei dem der *Neue Anforderung zur Unternehmensregistrierung* und *Sie wurden mit einer Firma verbunden* E-Mails werden von der falschen Adresse gesendet.
* **MDVA-28357** (*für Adobe Commerce >=2.3.2 &lt;2.3.6 | | >=2.4.0 &lt;2.4.1*) - Ersetzt den Standard-Analyzer durch einen benutzerdefinierten Analyzer durch den Keyword-Tokenizer für das SKU-Feld im [!DNL ElasticSearch] Index , damit Platzhaltersuchabfragen mit SKUs funktionieren, die einen Bindestrich enthalten (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem der benutzerdefinierte Bestellstatus in geändert wurde *Verarbeitung* nach Teillieferung mit WebAPI.
* **MDVA-30428** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Behebung des Problems, bei dem Kunden ein Produkt nicht auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-30594** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem eine Bestellung mit mehreren Adressen beim Checkout nicht gespeichert werden konnte, wenn FPT konfiguriert wurde.
* **MDVA-29148** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem beim Erstellen eines Produkts über einen API-Aufruf, das benutzerdefinierte Produktattribut von `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (wie Multiselect) verwendet seinen Standardwert nicht, wenn in der Payload kein Wert angegeben wurde.
* **MDVA-30837** (*für Adobe Commerce >=2.3.1 &lt;2.3.5*) - Eine Konfigurationseinstellung wurde hinzugefügt. *Steuern auf Betrag einbeziehen: ja/nein* in der Konfiguration der Versandmethode &quot;Free Shipping&quot;. Wann *Steuern auf Betrag einschließen* auf *Ja*, wird der Mindestbestellbetrag als Zwischensumme + Steuer berechnet. Wann *Steuern auf Betrag einschließen* auf *Nein*, wird der Mindestauftragsbetrag als Zwischensumme berechnet
* **MDVA-25028** (*für Adobe Commerce >=2.3.2 &lt;2.3.3 | | >=2.3.5 &lt;2.3.6*) - Behebt das Problem bei Bestellungen, die mit [!DNL PayPal Payflow Pro] nicht auf den Status &quot;Betrug verdächtig&quot;gesetzt, wenn Betrugsfilter ausgelöst werden.
* **MDVA-31224** (*für Adobe Commerce >=2.3.3 &lt;2.3.5*) - Verbessert die Leistung der `catalog_product_price` Neuindizierungsvorgang für Paket-Produkte.
* **MDVA-31321** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebt eine leere Seite (Fehler) bei *Alle anzeigen* ausgewählt ist. [!DNL Elasticsearch] gibt eine große Liste von Produkt-IDs zurück. In diesem Szenario wird die Reihenfolge nach Klausel in ein falsches SQL-Format konvertiert.
* **MDVA-30815** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebung des Problems, bei dem Adobe Commerce eine leere Seite anzeigt, wenn Sie ändern, wie viele Suchergebnisse auf der Suchergebnisseite angezeigt werden sollen. [!DNL Elasticsearch] zeigt jetzt korrekt Ergebnisse aus Kategorieseiten an, wenn Sie die Anzahl der pro Seite angezeigten Suchergebnisse ändern.
* **MDVA-30782** (*für Adobe Commerce >=2.3.5 &lt;2.4.2*) - Behebung des Problems, bei dem der dynamische Block unabhängig von der Warenkorbregel angezeigt wird.
* **MDVA-31021** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, bei dem Leistungsprobleme in `module-catalog-import-export/Model/Import/Product/Option.php`. Wenn mehr als ~100.000 Datensätze in `catalog_product_option` -Tabelle verwenden, dauert die Validierung einer neuen CSV mit einem einzelnen Produkt weniger als 10 Sekunden.
* **MDVA-31007** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem benutzerdefinierte Adressattribute nicht korrekt auf der Seite mit den Bestelldetails in meinem Kontobereich und im Backend angezeigt werden.
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
* **MDVA-29959** (*für Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 mit B2B-Erweiterung*) - Behebt das Problem, bei dem der eingeschränkte Administrator mit *Unternehmen* -Berechtigungen dürfen das Unternehmenskonto nicht löschen.
* **MDVA-30265** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem der Versand-Tracking-Link nach der Rechnungserstellung nicht mehr funktioniert.
* **MDVA-28409** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Behebt das Problem, bei dem der `sales_clean_quotes` Cron-Auftrag schlägt fehl mit *Nicht genügend Arbeitsspeicher* Fehler, wenn die Anzahl der abgelaufenen Anführungszeichen in der Datenbank sehr groß ist.
* **MDVA-30593** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Behebung des Problems, bei dem Angebote, die gemäß der Einstellung Anführungszeitintervall abgelaufen sind, nicht bereinigt wurden.
* **MDVA-30107** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem der Store-Umschalter nicht wie erwartet funktioniert, wenn für Store-Ansichten verschiedene Basis-URLs verwendet werden.
* **MDVA-28763** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebung des Problems, bei dem das Produktbild dupliziert wird, nachdem Produktinformationen mehrmals mit der REST-API aktualisiert wurden.
* **MDVA-30284** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Indexer für die Katalogsuche aufgrund der folgenden Faktoren fehlschlägt *[!DNL Elasticsearch]error: Die maximale Anzahl der Felder im Index wurde überschritten.*
* **MDVA-29042** (*für Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem die Katalogberechtigungen geändert wurden in *Zulassen* automatisch, nachdem dem freigegebenen Katalog ein neues Produkt hinzugefügt wurde.
* **MDVA-30428** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem Kunden ein Produkt nicht auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-28661** (*für Adobe Commerce >=2.3.0 &lt;2.4.2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem im Abschnitt Unternehmensbenutzerkonto für Unternehmen ein Fehler ausgegeben wird, nachdem der Unternehmensadministrator geändert wurde.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*für Adobe Commerce 2.3.1 - 2.3.4-p2*) - Behebung des Problems, bei dem Cron-Aufträge fehlschlagen, wenn der Datenbankname zu lang ist, was dazu führt, dass Kategorien nicht auf der Vorderseite aktualisiert werden.
* **MDVA-30106** (*für Adobe Commerce ^2.3.0*) - Behebung eines Problems, bei dem während der Kassenvorgänge nicht mit *Die Eigenschaft &#39;length&#39; von null kann nicht gelesen werden* -Fehler in der JS-Konsole.
* **MDVA-28656** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 | | >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Bestellstatus geändert wird, wenn eine Bestellung ohne erforderliche Zahlungsinformationen aufgegeben wurde (z. B. mit 100 % Rabatt) und eine Rechnung für die Bestellung erstellt wurde *Geschlossen* anstelle von Complete.
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
