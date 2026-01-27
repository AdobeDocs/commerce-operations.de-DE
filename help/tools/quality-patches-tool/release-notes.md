---
title: Versionshinweise
description: Erfahren Sie mehr über die für Adobe Commerce verfügbaren Patches und die von ihnen gelösten Probleme.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
type: Troubleshooting
source-git-commit: a233f39557ef1cc4f27f3e4ce015de554941d676
workflow-type: tm+mt
source-wordcount: '30379'
ht-degree: 0%

---

# Versionshinweise

Die [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) stellt individuelle Patches bereit, die von Adobe und der Magento Open Source-Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce verfügbar sind, anwenden, zurücksetzen und anzeigen. Sie können Patches auf Adobe Commerce- und Magento Open Source-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.

>[!INFO]
>
>Anweisungen [&#x200B; Anwenden von Patches auf Ihre Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de#apply-individual-patches)Projekte finden Sie unter „Anwenden von Patches“. Siehe [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im Software-Update-Handbuch, um eine vollständige Liste der veröffentlichten Patches anzuzeigen.

>[!INFO]
>
>Informationen zu den von der Community für Magento Open Source erstellten [!DNL quality patches] finden Sie in den [Versionshinweisen](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.76 {#v1-1-76}

* **ACSD-67091** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt den Fehler der maximalen Writeset-Größe, um die Bereinigung des Katalogregelproduktindex sicherzustellen, indem zwei Löschstrategien basierend auf dem Datenvolumen implementiert werden.
* **ACSD-67370** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Behebt mehrere Probleme, bei denen falsche Preise für Bundle-Produkte auf PDP/PLP und der Warenkorbseite für Geschäfte mit mehreren Währungen angezeigt wurden.
* **ACSD-68410** (für Adobe Commerce, B2B >=1.3.3 &lt;1.5.3) - Es wird ein Problem behoben, bei dem durch die Bestellung eines verhandelbaren Angebots fälschlicherweise zusätzliche Warenkorbpositionen zum Angebot hinzugefügt oder zusammengeführt werden. Produkte werden jetzt korrekt zum Warenkorb hinzugefügt, nachdem der letzte Schritt des verhandelbaren Angebots-Checkouts verlassen wurde.
* **ACSD-69086** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass der Cron-Auftrag die Changelog-Tabellen nicht löscht, was bei der Verarbeitung großer Datenmengen zu Abstürzen des Galera-Clusters führt.
* **ACSD-69115** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Behebt ein Problem, bei dem Warenkorbfehler dem Admin-Benutzer beim Verwalten des Warenkorbs für einen Kunden, der einer nicht standardmäßigen Website zugewiesen wurde, nicht angezeigt wurden.
* **ACSD-69129** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7 || >=2.4.8 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem das Löschen der standardmäßigen Basis-Website und die Verwendung der sekundären Website als Standard zu einem Fehler führte, wenn versucht wurde, den Stufenpreis für die sekundäre Website über die REST-API zu aktualisieren.
* **ACSD-69203** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem das Widget „Produktliste“ falsche Ergebnisse zurückgab, wenn mehrere Kategorien in der Kategoriebedingung aufgelistet waren.
* **ACSD-69261** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem ein Warenkorbpreisregelcoupon, der für den einmaligen Gebrauch pro Kunde konfiguriert war, aufgrund einer falschen Handhabung des `times_used` in Szenarien mit Teilrechnung und Restmengenstornierung mehrfach wiederverwendet wurde.
* **ACSD-69308** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem Katalogpreisregeln nicht anwendbar waren, wenn `special_price` nur auf Website-Ebene festgelegt wurde (nicht in „Alle Store-Ansichten„). Nach der Fehlerbehebung gelten die Katalogpreisregeln korrekt, indem zunächst der Standardspeicher der Website überprüft wird.
* **ACSD-69319** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem Paketpreise nicht richtig indiziert wurden, wenn untergeordnete Produkte unter benutzerdefinierten Quellen vorrätig waren.
* **ACSD-69325** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Es wurde ein Problem behoben, durch das durch Änderung des SKU-Falls das Produkt in der Storefront nicht vorrätig erschien.
* **ACSD-69331** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem Ersteller von Inhalten in der Mediensammlung keine Ordner mit nur der Berechtigung `create_folder` erstellen konnten. Nach der Behebung können sie wie erwartet Ordner erstellen.
* **ACSD-69333** (für Adobe Commerce >=2.4.7 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem SKU-Änderungen für Produkte mit einem aktiven geplanten Update zulässig waren. Nach der Behebung werden SKU-Änderungen während aktiver Aktualisierungen verboten. Das Speichern schlägt mit einem eindeutigen Fehler fehl und das Feld „Admin SKU“ ist deaktiviert. Dadurch werden MSI-Inventarinkonsistenzen verhindert, die durch SKU-Änderungen während Staging-Rollbacks verursacht werden.
* **ACSD-69541** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem die Reduzierung der Produktmenge im Admin-Bereich auf weniger als die bereits im Warenkorb vorhandene Menge es unmöglich machte, die Produktmenge in diesem Warenkorb über GraphQL zu bearbeiten.
* Aktualisierte Versionen: **ACSD-46541**, **ACSD-53750**, **ACSD-66404**
* Patches ersetzt: **ACSD-66404**, **ACSD-68499**

## v1.1.75 {#v1-1-75}

* **ACSD-68289** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wird ein Problem behoben, bei dem die Volltextsuche jetzt übereinstimmende Produkte zurückgibt, wenn die Mindestbedingung für die Übereinstimmung für alle durchsuchbaren Felder gemeinsam erfüllt ist, anstatt dass die Bedingung durch ein einzelnes Feld erfüllt werden muss.
* **ACSD-68359** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wird ein Problem behoben, bei dem die Auswahl eines Shops während des Checkouts mit [!UICONTROL Pick in Store] aufgrund langer URLs nicht mehr fehlschlägt, wenn sich viele Produkte im Warenkorb befinden. Zuvor wurde ein *414-Fehler ausgelöst* der durch zu lange URLs verursacht wurde, die während der Store-Auswahl generiert wurden, sodass Kundinnen und Kunden das Auschecken nicht abschließen konnten.
* **ACSD-68451** (für Adobe Commerce, B2B >=1.5.2-p1 &lt;1.5.3) - Behebt ein Problem bei mehreren Websites, bei denen sich ein Unternehmensadministrator auf einer Website anmeldet, ein nicht verbundenes Unternehmen auf einer anderen Website erstellt, aber fälschlicherweise mit diesem nicht verbundenen Unternehmen verknüpft ist.
* **ACSD-68490** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass die Schaltfläche [!UICONTROL Add New Attribute] für Administratoren mit eingeschränkter Zugriffsberechtigung während der konfigurierbaren Produkterstellung angezeigt wird.
* **ACSD-68517** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt einen Fehler bei der erneuten Übermittlung von Formularen auf Katalogseiten und Katalogsuchseiten.
* **ACSD-68573** (für Adobe Commerce >=2.4.5 &lt;2.4.9) - Es wurde das Problem behoben, dass Kategorieberechtigungen nicht ordnungsgemäß auf Elemente der Kunden-Wunschliste angewendet wurden. Nach der Fehlerbehebung werden Elemente der Wunschliste sowohl im Web als auch in GraphQL ordnungsgemäß angezeigt und paginiert.
* **ACSD-68615** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, bei dem die CLI für die Ausgleichszahlung für Lagerreservierungen eine Ausnahme anzeigte, wenn die verarbeitete Kombination eine fehlende Auftrags-ID hatte.
* **ACSD-68793** (für Adobe Commerce, B2B >=1.5.1 &lt;1.5.3) - Es wurde ein Problem behoben, bei dem gültige Produkte fälschlicherweise zurückgewiesen wurden, wenn sie einem freigegebenen Katalog zugewiesen wurden.
* **ACSD-68925** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem die Antworten für GraphQL-Anfragen jetzt mit den GraphQL over HTTP-Spezifikationen übereinstimmen. Ein 4XX-Antwort-Code wird zurückgegeben, wenn die Anfrage nicht geparst werden kann, nicht autorisiert ist oder auf ein allgemeines Problem stößt. Wenn die Anfrage geparst wird und verarbeitet werden kann, wird ein Antwort-Code von 200 zurückgegeben.
* Aktualisierte Versionen: **MDVA-19640**, **ACSD-47910**, **ACSD-68040**, **ACSD-62965**
* Patches ersetzt: **ACSD-62577**, **ACSD-68011**

## v1.1.74 {#v1-1-74}

* **ACSD-68636** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Es wurde ein Problem behoben, bei dem der Name des Shopeigentümers nicht korrekt in den E-Mail-Kopfzeilen der Geschenkkarte angezeigt wird, wenn die Rechnung aus einem anderen Shop erstellt wurde.
* **ACSD-68430** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Es wird ein Problem behoben, bei dem das Speichern einer Kunden- oder Kundenadresse fehlschlägt, wenn der Datensatz mehrere Attributoptionen enthält, die aus der Attributkonfiguration gelöscht wurden.
* **ACSD-68499** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wird ein Problem behoben, bei dem die GraphQL-`updateCartItems`-Mutation eine falsche Erfolgsantwort zurückgibt, wenn Mengen aktualisiert werden, die die verfügbaren Lagerbestände überschreiten, was zu überhöhten Mengen und Gesamtwerten führt.
* **ACSD-68810** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wird ein Problem behoben, bei dem eine Bestellung einem Kunden zugewiesen wird, der trotz der **[!UICONTROL Customer Account Sharing]** auf einer anderen Website erstellt wurde.
* Aktualisierte Versionen: **ACSD-49737**, **ACSD-57003-V2**
* Patches ersetzt: **ACSD-61969**

## v1.1.73 {#v1-1-73}

* **ACSD-67171** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass B2B-Benutzende eine *[!UICONTROL Access Denied]* sehen, wenn ihre Sitzung abgelaufen ist oder während des Checkouts entfernt wurde.
* **ACSD-67908** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass JS-Dateien in Setups mit mehreren Speichern nicht ordnungsgemäß zusammengeführt werden können.
* **ACSD-68190** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass Rabatte nicht angewendet werden, angewendete Rabatte in der GraphQL-Warenkorbansicht nicht korrekt angezeigt werden und Nicht-Couponrabatte beim Entfernen eines Couponrabatts entfernt werden.
* **ACSD-68206** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Behebt den Fehler bei der Verwendung des GraphQL-Anwendungsservers mit der **[!UICONTROL Rate Limiting]**-Funktion, wobei die [!DNL PHP Redis]-Erweiterung installiert ist.
* **ACSD-68356** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, bei dem eine GraphQL-Warenkorbabfrage einen falschen Rabattbetrag für virtuelle Angebote zurückgab.
* **ACSD-68391** (für Adobe Commerce >=2.4.6-p10 &lt;2.4.9) - Es wurde das Problem behoben, dass kategoriespezifische Berechtigungen in **[!UICONTROL Quick Order]** und **[!UICONTROL Requisition Lists]** nicht korrekt angewendet wurden.
* **ACSD-68400** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass die Menge der virtuellen Geschenkkarte nicht korrekt in der Inventarreservierungstabelle wiedergegeben wurde.

## v1.1.72 {#v1-1-72}

* **ACSD-68040** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass die Leistung der Frontend-Suchseite auf [!DNL MariaDB] 10.6 und 11.4 mit vielen historischen Suchanfragen abnimmt.
* **ACSD-67941** (für Adobe Commerce und Magento Open Source >=2.4.7-p1 &lt;2.4.8) - Behebt das Problem, dass GraphQL-Anfragen mit unbekannten Filternamen PHP-Ausnahmeprotokolle verursachen.
* **ACSD-68064** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, dass das Erstellen geplanter Aktualisierungen zu doppelten Einträgen in Umgebungen mit einer hohen Anzahl verschachtelter Kategorien führt.
* **ACSD-66807** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass in der `report_viewed_product_index`-Tabelle eine falsche Anzahl von Produktseitenansichten angezeigt wurde.
* **ACSD-67383** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass die Verwendung von **[!UICONTROL Login as Customer]** mit zwei Unternehmensadministratorkonten in derselben Sitzung einen Fehler *Keine solche Entität mit cartId* verursacht.
* **ACSD-67518** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt das Problem, dass erweiterte Berichte doppelte Kopfzeilen generieren, wenn die Zeilenanzahl die Batch-Größe überschreitet.
* **ACSD-67639** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Das Erstellen einer Gutschrift schlägt für Bundle-Produkte fehl, wobei der **[!UICONTROL Dynamic Price]** auf &quot;*&quot;*.
* **ACSD-67696** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass `media_gallery` Einträge nach einer Cache-Leerung nicht im Warenkorb-GraphQL-Produktknoten zurückgegeben wurden.
* **ACSD-67946** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Es wurde das Problem behoben, bei dem bei Warenkorbaktualisierungen doppelte Fehlerbanner angezeigt wurden.
* **ACSD-68011** (für Adobe Commerce, B2B >=1.5.1 &lt;1.5.3) - Es wird das Problem behoben, bei dem nicht vorhandene SKUs über die `/V1/sharedCatalog/:id/assignProducts` [!DNL REST]-API einem freigegebenen Katalog zugewiesen werden können.
* **ACSD-68118** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.9) - Es wird das Problem behoben, bei dem die `customerCart` GraphQL-Abfrage Produktattributwerte zurückgibt, die nicht die Store-Kopfzeile widerspiegeln, was zu einer inkonsistenten Lokalisierung führt.
* **ACSD-68092** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt das Problem, dass gebündelte Produktoptionen nach mehreren Speichervorgängen aufgrund einer nicht ordnungsgemäßen Synchronisierung zwischen geplanten Updates und Basisproduktdaten verloren gehen.
* **ACSD-67424** (für Adobe Commerce, B2B >=1.5.0 &lt;1.5.3) - Es wird das Problem behoben, bei dem der `updated_at` in der `GET /carts/search` [!DNL REST] API-Antwort nicht mit dem in der **[!UICONTROL Admin panel]** angezeigten Wert übereinstimmt, wenn verhandelbare Anführungszeichen verwendet werden.
* **ACSD-67187** (für Adobe Commerce, B2B >=1.5.1 &lt;1.5.3) - Behebt das Problem, dass Admin-Benutzer, die auf nicht standardmäßige Websites beschränkt sind, den Fehler sehen, *Erstellen Sie mindestens einen öffentlichen freigegebenen Katalog, um fortzufahren* und nicht auf die Schaltfläche &quot;**[!UICONTROL Add New Company]**&quot; im Unternehmensraster zugreifen können.
* Aktualisierte Versionen: **ACSD-49737**, **ACSD-53750**, **ACSD-51819**, **ACSD-55566**, **ACSD-62965**, **63323** **ACSD-63406**, **ACSD-66139**, **ACSD-66404**, **ACSD-67659** **66301**,
* Ersetzte Patches: **ACSD-62577**, **ACSD-63325**, **ACSD-67102**

## v1.1.71 {#v1-1-71}

* **ACSD-60624** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass **[!UICONTROL Upload Image]** bei leeren Inhalten in [!UICONTROL Image]-, [!UICONTROL Banner]- und [!UICONTROL Slider]-Abschnitten in Page Builder nicht funktioniert.
* **ACSD-67089** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Paginierungsproblem in der `inventory/export-stock-salable-qty`-API, das `total_count` fälschlicherweise auf die Seitengröße beschränkt.
* **ACSD-67093** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, bei dem das Abrufen von Bestellungen über GraphQL mithilfe des Datumsbereichsfilters falsche Ergebnisse zurückgibt.
* **ACSD-67459** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.9) - Es wurde das Problem behoben, dass Produkte mit Beschreibungen, die länger als 65.536 Zeichen sind, nicht importiert werden können.
* **ACSD-67603** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Es wurde das Problem behoben, dass die Sitemap-Generierung für Produkte mit aktivierter Bildeinbindung zu langen Verarbeitungszeiten führte.
* **ACSD-67643** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wird das Problem behoben, bei dem doppelte Einträge bei geplanten Aktualisierungen in Umgebungen mit einer hohen Anzahl verschachtelter Kategorien erstellt werden.
* **ACSD-67652** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, dass der Bundle-Produktstatus in GraphQL-Aufrufen auch dann als nicht vorrätig zurückgegeben wird, wenn untergeordnete und übergeordnete Produkte vorrätig sind.
* **ACSD-67904** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, dass Bestellungen nicht aufgegeben werden können, wenn der Stadtname Ziffern (0-9), kaufmännisches Und-Zeichen (&amp;), Punkte (.) oder Klammern () enthält.
* Patches ersetzt: **ACSD-61322**, **ACSD-65848**

## v1.1.70 {#v1-1-70}

* **AC-15210** (für Adobe Commerce und Magento Open Source >=2.4.6-p3 &lt;2.4.9) - Migriert die USPS-Integration von den veralteten Web Tools-APIs zu den neuen RESTful USPS-APIs.
* **ACSD-67102** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass das Adobe Commerce-Backend sehr langsam geladen **[!UICONTROL Categories]**.
* **ACSD-66120** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass [!DNL GraphQL] Rabattprozentsätze und Grundpreise fälschlicherweise anzeigt, wenn Katalogpreise so konfiguriert sind, dass sie Steuern enthalten.
* **ACSD-66157** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.9) - Behebt das Problem, dass der Sonderpreis nicht für Websites gilt, die in verschiedenen Zeitzonen erstellt wurden.
* **ACSD-67659** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt ein Problem, bei dem übersetzte Fehlermeldungen einen UNDEFINIERTEN Fehler-Code zurückgeben.
* **ACSD-67166** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wird das Problem behoben, dass die `cataloginventory_stock_status` Abfrage beim Laden eines Angebots in der Storefront mehrmals ausgeführt wird, was zu redundanten Datenbankaufrufen führt.
* **ACSD-67289** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt das Problem, dass der reguläre Preis nicht angezeigt wird, wenn ein Sonderpreis angewendet wird.
* **ACSD-67686** (für Adobe Commerce und Magento Open Source >=2.4.4-p15 &lt;2.4.5 || >=2,4,5-p14 &lt;2,4,6 || >=2.4.6-p12 &lt;2.4.7) - Behebt das Problem, dass beim Senden einer leeren `Syntax Error: Unexpected <EOF>`-Anfrage ein [!DNL GraphQL] auftritt.
* **ACSD-67250** (für Adobe Commerce >=2.4.7-p4 &lt;2.4.8) - Es wurde das Problem behoben, dass beim **[!UICONTROL Shared Catalog]** Speichervorgang alle Elemente statt nur die betroffenen aktualisiert wurden, wodurch die Leistung verbessert wurde, indem unnötige Vorgänge vermieden wurden.
* **ACSD-67030** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Es wird das Problem behoben, bei dem die Zuweisung einfacher Produkte zu einem konfigurierbaren Produkt aufgehoben wird, wenn sie von einem Administrator mit eingeschränkter Rolle bearbeitet werden.
* Aktualisierte Versionen: **ACSD-54095**, **ACSD-51636**, **ACSD-51739**, **ACSD-66093**
* Patches ersetzt: **ACSD-62415**

## v1.1.69 {#v1-1-69}

* **AC-15223** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt ein Problem in der 2.4.8-Storefront, bei dem die Seite nach dem Wechsel des Stores aus dem Cache bereitgestellt wird und nicht den ausgewählten Store widerspiegelt.
* **ACP2E-3731** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass Produktexporte mit **[!UICONTROL Catalog, Search]** Sichtbarkeit fälschlicherweise Datensätze aus anderen Store-Ansichten in Multi-Store-Umgebungen enthalten.
* **ACP2E-3767** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass die letzte Bundle-Option in einem Bundle-Produkt nicht entfernt werden kann.
* **ACP2E-3964** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde ein Problem behoben, bei dem untergeordnete Produkte von konfigurierbaren Produkten nicht über die REST-API aufgelistet werden konnten, wenn ein Video in der Galerie festgelegt wurde.
* **ACP2E-3977** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass das **[!UICONTROL Cap Reward Points Balance At]** Feld beim Festlegen von [!UICONTROL Rewards Points Balance Redemption Threshold] nicht leer sein darf, was einen Validierungsfehler verursacht.
* **ACP2E-4050** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.8) - Behebt das Problem, dass die Regeln zum Warenkorbpreis nicht korrekt für Produkte mit mehreren Sendungen angewendet werden, wenn das Bundle-Produkt verwendet wird und Unterauswahlbedingungen mit aktiviertem kostenlosen Versand verwendet werden.
* **ACSD-56226** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, dass READ-Abfragen am Slave-Knoten veraltete Daten zurückgeben, wenn das `synchronous_replication`-Flag aktiviert ist.
* **ACSD-57477** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, bei dem die Verarbeitung von Verkaufsregeln bei Anfragen im Zusammenhang mit dem Warenkorb zu langsamer Leistung führt.
* **ACSD-58108** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Es wurde das Problem behoben, bei dem der fehlende Verknüpfungstabellenname in der ursprünglichen Abruftabelle zu Fehlern mit der benutzerdefinierten Modulerweiterung SQL im Reihenfolgen-Raster führte.
* **ACSD-65983** (für Adobe Commerce >=2.4.6-p10 &lt;2.4.9) - Es wird das Problem behoben, bei dem die Neukonfiguration eines gebündelten Produktangebots im Admin-Backend einen Fehler auslöst.
* **ACSD-66149** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass der IPN-Handler bei nicht unterstützten oder unbekannten IPN-Typen einen *500*-Fehler zurückgibt.
* **ACSD-66153** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass eine Seite einen *500*-Fehler zurückgibt, der auf die Zwischenspeicherung einer falschen Layout-Struktur zurückzuführen ist.
* **ACSD-66302** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt das Problem, dass Wunschlistenelemente fälschlicherweise nach Store-ID gefiltert werden, anstatt nach Website.
* **ACSD-66311** (für Adobe Commerce >=2.4.6-p9 &lt;2.4.9) - Behebt das Problem, dass das Unternehmensraster für Admin-Benutzende mit eingeschränktem Website-Zugriff langsam geladen wird.
* **ACSD-66404** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass der Cron-Auftrag die Changelog-Tabellen nicht löscht, was bei der Verarbeitung großer Datenmengen zu [!DNL Galera Cluster] führt.
* **ACSD-66952** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Behebt das Problem, dass der Cache bei jedem PLP- oder Warenkorbbesuch gelöscht wird, was zu Leistungsaufwand führt, wenn eine Zielregel festgelegt wird.
* **ACSD-67264** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass die Layouts von Bundles und herunterladbaren Produktseiten auf allen Geräten inkonsistent sind.
* **ACSD-67347** (für Adobe Commerce und Magento Open Source >=2.4.5-p11 &lt;2.4.6) - Behebt das Problem, dass die Bestellung mit dem Fehler *Es kann keine Sperre erworben werden* fehlschlägt, wenn Coupons mit Sonderzeichen verwendet werden und die Dateisperre aktiviert ist.
* Patches ersetzt: **ACP2E-3841**

## v1.1.68 {#v1-1-68}

* **ACSD-58131** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, durch das das Vorhandensein eines 0-Byte-Bildes in der Mediensammlung verhinderte, dass alle Bilder im Verzeichnis angezeigt oder ausgewählt wurden.
* **ACSD-62415** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass Adobe Commerce-Backend-Kategorien sehr langsam lädt.
* **ACSD-66082** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.9) - Es wurde das Problem behoben, dass es nicht möglich war, das Musterbild eines Produkts durch Produktimport zu aktualisieren.
* **ACSD-66179** (für Adobe Commerce und Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6 || >=2,4,6-p8 &lt;2,4,7 || >=2.4.7-p3 &lt;2.4.9) - Es wurde das Problem behoben, bei dem die Stornierung einer Rechnung, die mit dem Zahlungstyp „Nicht erfasst“ erstellt wurde, zu einer 404-Fehlerseite führte.
* **ACSD-66865** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, durch das das Speichern von Katalogpreisregeln Indexer ungültig machte und eine Alternative zur Neuindizierung nur betroffener Produkte bot.
* **ACSD-66963** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, bei dem die `estimateTotals`-Mutation bei Rabatten null zurückgab, wenn ein Rabattcode auf einen Warenkorb mit virtuellen Produkten angewendet wurde.
* **ACSD-67039** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, bei dem Kundendatensätze aufgrund der Validierung des `rp_token` Systemattributs nicht gespeichert wurden und die Diakritik-Validierung jetzt nur mehr auf die resultierende Kunden-E-Mail angewendet wird.
* **ACSD-62146** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass die ausgewählte Rechnungsadresse auf der Kaufbestätigungsseite verschwindet, wenn die Adresssuche aktiviert ist und „Limit für Kundenadressen“ auf 1 gesetzt ist.
* **ACSD-65938** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass E-Mails mit Geschenkkarten auch dann gesendet wurden, wenn die Rechnungserstellung fehlgeschlagen war.
* **ACSD-66072** (für Adobe Commerce >=2.4.6 &lt;2.4.9) - Behebt das Problem, dass verwandte Produkte aufgrund eines internen Server-Fehlers bei der Konfiguration „Zugehörige Produktregeln“ nicht über GraphQL auf der Produktdetailseite zurückgegeben wurden.
* **ACSD-66233** (für Adobe Commerce >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, bei dem Admin-Benutzer aufgrund des fehlgeschlagenen Ladens des Popup-Fensters „Produkt hinzufügen“ keine Produkte zu einer Kategorie hinzufügen konnten.
* **ACSD-66889** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Korrigiert eine veraltete Code-Zeile mit der richtigen Struktur, um einen erfolgreichen Abschluss des Inventar-Indexerprozesses sicherzustellen.
* **ACSD-66965** (für Adobe Commerce B2B >=1.5.0 &lt;1.5.3) - Behebt das Problem mit der Druckoption „Anforderungsliste“, das einen Fehler verursacht hat.
* **ACSD-66506** (für Adobe Commerce B2B >=1.5.0 &lt;1.5.3) - Behebt den Backend-Fehler, der auftrat, wenn zuvor zugewiesene Produkte eines freigegebenen Katalogs gelöscht und neue Produkte zugewiesen wurden.
* **ACSD-66417** (für Braintree 4.6.1) - Es wurde ein Problem behoben, bei dem im Kundenauftragsraster ein Fehler ausgegeben wurde, wenn versucht wurde, Bestellungen nach Datum zu filtern.
* Aktualisierte Versionen: **ACSD-60590**, **ACP2E-3705**
* Patches ersetzt: **ACSD-57003**, **ACSD-66434**

## v1.1.67 {#v1-1-67}

* **ACSD-65935** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, bei dem die `customerOrders` GraphQL-Abfrage beim Löschen eines Produkts einen internen Server-Fehler zurückgab.
* **ACSD-66049** (für Adobe Commerce und Magento Open Source >=2.4.5-p3 &lt;2.4.6 || >=2.4.7 &lt;2.4.9) - Behebt das Problem, dass nicht englische Storefronts aufgrund der Version der ICU-Bibliothek falsche Preise anzeigen.
* **ACSD-66084** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.9) - Behebt das Problem, dass `row_total_incl_tax` in der API-Antwort für Bestellungen als Restwert nahe Null zurückgegeben wird, anstatt als 0,00 für vollständig reduzierte Elemente.
* **ACSD-66118** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass bei Aktualisierung des Code für die Store-Ansicht [!UICONTROL Design Configuration] Einstellungen gelöscht wurden, wenn der Konfigurations-Cache nicht aktualisiert wurde.
* **ACSD-66139** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, bei dem GraphQL-Aufrufe zum Aufgeben einer Bestellung für einen nicht vorhandenen oder inaktiven Warenkorb einen *UNDEFINED*-Fehlercode zurückgaben.
* **ACSD-66301** (für Adobe Commerce und Magento Open Source >=2.4.6-p9 &lt;2.4.7 || >=2.4.7-p4 &lt;2.4.8) - Es wird das Problem behoben, bei dem die Verschiebung von Produkten aus einer Bestellung zurück in den Warenkorb im Admin zu einer Mengenabweichung führt.
* **ACSD-66434** (für Adobe Commerce >=2.4.6-p8 &lt;2.4.9) - Es wurde das Problem behoben, dass in GraphQL-Abfragen des Unternehmens eine Kunden-ID fehlte.
* **ACSD-66441** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.8) - Behebt das Problem, dass die Storefront beim Indizieren konfigurierbarer Produkte für ein Multi-Store-Setup in der mehrschichtigen Navigation falsche Indexdaten anzeigt.
* **AC-14984** (für Adobe Commerce und Magento Open Source >=2,4,6-p10 &lt;2,4,7 || >=2.4.8 &lt;2.4.9) - Behebt den Fehler *Ungültiger Frame-Typ 21* bei der RabbitMQ-SSL-Verbindung.
* **AC-14985** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Behebt das Problem, dass E-Mails bei Verwendung des externen `smtp`-Servers mit aktiviertem TLS nicht gesendet werden.
* Aktualisierte Versionen: **MDVA-12304**, **ACSD-47920**, **ACSD-56447**, **ACSD-61845**, **ACSD-64118**

## v1.1.66 {#v1-1-66}

* **ACP2E-3789** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.9) - Es wurde das Problem behoben, dass beim Aktualisieren eines Produkts über [!DNL WebAPI] duplizierte Mediendateien eine Medien-ID bereitgestellt wurde.
* **ACP2E-3918** (für Adobe Commerce >=2.4.5 &lt;2.4.9) - Behebt das Problem, dass der Checkout für angemeldete Firmenkunden, die eine Abholung im Geschäft ohne standardmäßige Rechnungsadresse verwenden, fehlgeschlagen ist.
* **ACSD-65750** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Es wurde das Problem behoben, bei dem die GraphQL-`route`-Abfrage in den Inhaltstypen von Page Builder-Produkten Produkte in der falschen Reihenfolge zurückgab.
* **ACSD-65775** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, bei dem die Auftragsdetails der [!DNL REST]-API falsche `base_row_total` und `row_total` zurückgaben, wenn mehrere Mengen desselben Artikels bestellt wurden.
* **ACSD-65777** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wurde das Problem behoben, dass in der `types` GraphQL-Anfrage das Feld `MediaGallery` für Produktbildtypen fehlte.
* **ACSD-65848** (für Adobe Commerce und Magento Open Source >=2.4.8 &lt;2.4.9) - Es wird das Problem behoben, bei dem die Gesamtproduktzahl in einer Kategorie mithilfe einer Unterauswahl berechnet wurde, indem die Methode so umgestaltet wird, dass stattdessen ein Join verwendet wird.
* **ACSD-65913** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.9) - Es wurde das Problem behoben, bei dem [!DNL OpenSearch] einen Fehler *ILLEGAL_ARGUMENT_EXCEPTION* für Kategorien mit Produkten desselben Preises ausgegeben hat.
* **ACSD-66041** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass Postleitzahlen in Irland (IE) aufgrund eines fehlenden `CountryID` nicht nach Abholorten durchsucht werden konnten.
* **ACSD-66212** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.9) - Es wurde das Problem behoben, dass der doppelte Import einer Kunden-CSV-Datei beim zweiten und nachfolgenden Versuch zu Fehlern führte.
* Aktualisierte Versionen: **MDVA-12304**, **MDVA-19640**, **ACP2E-3841**, **ACSD-65100**, **ACSD-65787**, **ACP2E-3753**, **ACSD-65202**, **ACSD-65331**, **ACSD-65822**

## v1.1.65 {#v1-1-65}

* **ACP2E-3753** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass E-Mails zu Produktwarnungen in einer Multi-Store-Einrichtung immer mit dem Standard-Design gesendet wurden, unabhängig von der Store- oder Design-Konfiguration.
* **ACSD-64118** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wird das Problem behoben, bei dem gleichzeitige Anfragen zum Speichern und Aktualisieren desselben Produkts zu Dateninkonsistenz oder duplizierten Produkten führen.
* **ACSD-64813** (für Adobe Commerce >=2.4.4 &lt;2.4.9) - Es wird das Problem behoben, bei dem das Aufheben der Zuweisung von Kategorien aus einem [!DNL B2B] freigegebenen Katalog über [!DNL REST] API zu lange dauert oder bei großen Katalogen zu lange dauert.
* **ACSD-65202** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass auf der Seite „Mein Konto“ keine aktuellen Bestellungen aus anderen Store-Ansichten innerhalb desselben Stores angezeigt werden.
* **ACSD-65254** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass Kundinnen und Kunden keine E-Mail-Benachrichtigungen erhalten hatten, nachdem ihre E-Mail-Adressen in ihren Konten mithilfe der `updateCustomerEmail`-[!DNL GraphQL]-Mutation aktualisiert worden waren.
* **ACSD-65331** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass der ausgewählte Store in [!UICONTROL Pick in Store] gelöscht wurde, nachdem wiederholt zur Kaufbestätigungsseite navigiert wurde.
* **ACSD-65822** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass die Bundle- und konfigurierbaren Produktmengen im Warenkorbbereich unter &quot;[!UICONTROL Customer's Activities]&quot; nicht korrekt angezeigt wurden.
* **ACSD-66093** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass E-Mail-Adressen in die [!UICONTROL First Name]- und [!UICONTROL Last Name] des Gastkunden eingegeben werden konnten, was zu ungültigen E-Mails zur Bestellbestätigung führte.
* Aktualisierte Versionen: **ACSD-51291**
* Patches ersetzt: **ACSD-61522**

## v1.1.64 {#v1-1-64}

* **ACP2E-3838** (für Adobe Commerce und Magento Open Source >=2.4.4-p9 &lt;2.4.4-p13 || >=2,4,5-p8 &lt;2,4,5-p12 || >=2,4,6-p6 &lt;2,4,6-p10 || >=2.4.7 &lt;2.4.7-p5) - Es wird das Problem behoben, bei dem [!DNL Page Builder] CORS-Fehler das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus verhindern.
* **ACP2E-3841** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.8) - Behebt das Problem, dass Warenkorbpreisregeln für Produkte mit mehreren Versandarten nicht korrekt angewendet werden, wenn Bedingungen zur Unterauswahl verwendet werden und der kostenlose Versand aktiviert ist.
* **ACSD-63139** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, bei dem der Produktexport fehlschlägt, wenn Produktattribute Tausende von Optionswerten enthalten.
* **ACSD-65100** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, bei dem das Entfernen der Werte für [!UICONTROL Maximum Width] und [!UICONTROL Maximum Height] in der [!UICONTROL Media Gallery Image Optimization] einen Fehler während des Bildoptimierungsprozesses verursacht.
* **ACSD-65127** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, bei dem die Aktivierung der JavaScript-Minimierung im Produktionsmodus dazu führte, dass [!DNL TinyMCE] 6 Fehler in der Browser-Konsole generierte, die die Funktionalität und das Benutzererlebnis beeinträchtigten.
* **ACSD-65787** (für Adobe Commerce und Magento Open Source >=2.4.7-p5 &lt;2.4.8) - Behebt das Problem, dass die SchemaBuilder-Klasse bei der Schemaerstellung oder bei Aktualisierungen aufgrund eines nicht definierten Array-Schlüssels „column“ bei der Verarbeitung von Tabellendaten abstürzt.
* **ACSD-65223** (für Adobe Commerce, B2B 1.5.1) - Es wird das Problem behoben, bei dem manuell ausgewählte Bedingungen und Vereinbarungen für [!DNL B2B] Bestellungen zu einem Fehler führen.
* **ACSD-65540** (für Adobe Commerce, B2B 1.5.2) - Es wird das Problem behoben, bei dem ein SQL-Syntaxfehler auftritt, da die `REGEXP_LIKE` beim Aktualisieren der `company_structure` nicht vorhanden ist.
* **ACSD-65684** (für Adobe Commerce, B2B 1.5.2) - Behebt das Leistungsproblem, bei dem das Upgrade des `Magento_Company`-Moduls nach der Aktualisierung auf [!DNL B2B] 1.5.2 bei der Verarbeitung einer großen Anzahl von Datensätzen (~100.000+) in der `company_structure`-Tabelle übermäßig lange dauerte.
* Aktualisierte Versionen: **ACSD-48234**, **ACSD-51819**, **ACSD-57570**, **ACSD-56415**

## v1.1.63 {#v1-1-63}

* **ACSD-64627** (für Adobe Commerce >=2.4.6-p8 &lt;2.4.8) - Es wurde das Problem behoben, dass benutzerdefinierte Kundenattribute beim Hinzufügen oder Bearbeiten von Benutzern in der Unternehmensstruktur nicht gespeichert werden können.
* **ACSD-64753** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass der vorausgewählte Store in „Pick-up in Store“ nicht aktualisiert wird, wenn sich die Lieferadresse ändert, auch wenn er sich außerhalb des Ladenradius befindet.
* **ACSD-65195** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass die GraphQL-`createCompany` einen Fehler für ein Land ohne erforderliche Region auslöst.
* **LYNX-839** (für Adobe Commerce 2.4.8) - Die Offenlegung von Informationen zu Kundengruppen, Segmenten und Werberegeln über GraphQL wurde entfernt.
* Aktualisierte Versionen: **MDVA-12304**, **ACSD-48234**, **ACSD-58054**

## v1.1.62 {#v1-1-62}

* **ACSD-63406** (für Adobe Commerce und Magento Open Source >=2.4.4-p9 &lt;2.4.5 || >=2,4,5-p8 &lt;2,4,6 || >=2.4.6-p6 &lt;2.4.8) - Behebt das Problem, dass abgelaufene persistente Anführungszeichen von keinem Cron-Auftrag gelöscht werden, wenn der `persistent_clear_expired` Cron-Auftrag ausgeführt wird.
* **ACSD-63520** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, dass Bilder, die über **[!UICONTROL Configurations]** im Admin-Bedienfeld hinzugefügt wurden, nicht der maximalen Upload-Größenbeschränkung entsprechen.
* **ACSD-64523** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, dass es möglich war, neue Produkte ohne Namen über den Importvorgang (Admin oder API) zu erstellen, was die Admin-Benutzeroberfläche beschädigte und zu ungültigen Produkten führte.
* **ACSD-64532** (für Adobe Commerce und Magento Open Source >=2.4.6-p2 &lt;2.4.8) - Es wird das Problem behoben, bei dem eine auf „false“ gesetzte ENV-Variable als Zeichenfolge „false“ und nicht als boolescher Wert „false“ behandelt wird.
* **ACSD-64592** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass der Anforderungs-Link aus der E-Mail für eine Geschenkkarte in nicht standardmäßigen Geschäften den Geschenkkartenanspruch immer auf die Standard-Website umleitete.
* **ACSD-65164** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Behebt das Problem, bei dem die Fehlermeldung *Einige der ausgewählten Elementoptionen sind derzeit nicht verfügbar* auftritt, wenn ein konfigurierbares Produkt mit einer einzigen benutzerdefinierten Kontrollkästchenoption neu angeordnet wird.
* **ACSD-64732** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass Controller von Drittanbietern nicht korrekt mit Kundensegmenten zwischengespeichert wurden.

## v1.1.61 {#v1-1-61}

* **ACP2E-3689** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt mehrere Probleme mit der Anzeige der Kategoriestruktur auf tieferen Ebenen und spiegelt Anker-/Nicht-Anker-Beziehungen wider.
* **ACP2E-3705** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Behebt ein Problem, bei dem die `indexer_update_all_views` Cron-Ausführung fehlschlägt, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt ist.
* **ACSD-63883** (für Adobe Commerce >=2.4.4 &lt;2.4.7-p4) - Behebt das Problem, dass die Anforderungsliste in der GraphQL-Antwort einen falschen `items_count` zurückgibt.
* **ACSD-63974** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass das Laden der Anforderungslistenseite bei zu vielen Elementen zu viel Zeit in Anspruch nimmt, indem dem Anforderungslistenraster in der Storefront eine Paginierungsfunktion hinzugefügt wird, die nur Teile von Datensätzen anzeigt, die auf die Anzahl der Datensätze pro Seite beschränkt sind, anstatt alle Datensätze gleichzeitig.
* **ACSD-64178** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass die Seite zur Bearbeitung von Attributsätzen langsam geladen wird, wenn Tausende von Produktattributen vorhanden sind.
* **ACSD-64209** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass der Cron-Scheduler alle verhandelbaren Anführungszeichen abruft, ohne diejenigen mit dem Status &quot;**[!UICONTROL ordered]**&quot; auszuschließen, wodurch eine E-Mail oder E-Mails ausgelöst werden.
* **ACSD-64431** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Die `placeOrder` Mutation, die die Couponcode-Informationen in der Anfrage enthält, löst keinen internen Fehler mehr aus, sondern zeigt stattdessen an, dass die Bestellung erfolgreich aufgegeben wurde.
* **ACSD-64467** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer erscheint.
* **ACSD-64546** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass eine allgemeine Fehlermeldung in der Benutzeroberfläche auftritt und eine *Array-zu-String-Konvertierung*-Ausnahme während der Erstellung der UPS Versandkennzeichnung in den Protokollen gespeichert wird, sodass der tatsächliche Fehler in der Benutzeroberfläche angezeigt und die richtige Fehlermeldung in den Protokollen gespeichert wird.
* **ACSD-64684** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass beim Bearbeiten und Speichern einer Geschenkkarte mit einem Wert größer als *999* aufgrund eines Kommas (Tausendertrennzeichen) in der Zahl *1.000) ein Validierungsfehler auftritt*.
* Aktualisierte Versionen: **ACSD-49392**, **ACSD-50368**, **ACSD-51819**, **ACSD-54966-V2**, **ACSD-57003**, **ACSD-62979**, **ACSD-64112**
* Ersetzte Patches: **ACSD-49392**, **ACSD-58739**, **ACSD-62689**, **ACSD-64112**
* Veraltete Patches: **ACSD-46192**, **ACSD-52133**

## v1.1.60 {#v1-1-60}

* **ACSD-63323** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass die Option **[!UICONTROL Select All]** beim Hinzufügen von Produkten zu einer Kategorie nicht funktioniert. Darüber hinaus wird sichergestellt, dass die Paginierung und die Beschriftung der Datensatzanzahl korrekt funktionieren, wenn Produkte über das Popup-Raster zu einer Kategorie hinzugefügt werden.
* **ACSD-63992** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde ein Problem behoben, bei dem eine Warenkorbpreisregel mit einem Coupon und einer Bedingung, die auf einer Versandmethode basiert, nicht über die Admin-Benutzeroberfläche korrekt angewendet werden kann.
* **ACSD-64111** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, bei dem beim Festlegen verschachtelter Bedingungen für eine Produktkomponente in [!DNL Page Builder] ein Fehler auftritt.
* **ACSD-64137** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass die Suche nach Abholorten nach Postleitzahl bei der niederländischen Lokalisierung nicht richtig funktionierte.
* **ACSD-64149** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, dass ein Kundensegment mit einer Datumsbereichsbedingung gespeichert werden kann, wenn nur eines der Daten bearbeitet wird.
* Aktualisierte Versionen: **MDVA-12304**, **ACSD-45049**, **MDVA-43824**, **ACSD-46192**, **ACSD-50368**, **ACSD-47657**, **ACSD-51819**, **ACSD-V2**, **ACSD-V2, 52133** ACSD-**-ACSD-54966-ACSD-55628** **45049** **63242**,

## v1.1.59 {#v1-1-59}

* **ACSD-63454** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, bei dem der Standardwert für ein Dropdown-Attribut und Attribute mit Mehrfachauswahl nicht ordnungsgemäß in der Datenbank gespeichert wird.
* **ACSD-63574** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Es wurde das Problem behoben, bei dem das Hinzufügen einer Bundle-Produktliste zu einem Block über den Page Builder zu einem Fehler führte.
* **ACSD-63793** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Behebt das Problem, wenn sich Importprozesse auf verschiedenen Browser-Registerkarten gegenseitig beeinflussen.
* **ACSD-64113** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.8) - Behebt das Problem, das beim Hochladen von Bildern mit einer relativ geringen Breite im Vergleich zu ihrer Höhe (oder umgekehrt) über die Mediensammlung zu Fehlern in der Administratorliste führt.
* **ACSD-64212** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.8) - Behebt das Problem, dass eine Bestellung nicht mit einem Kundenkonto verknüpft ist, wenn das Konto nach der Bestellung über GraphQL erstellt wird.
* **ACSD-63469** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, dass Festbetragsrabatte für den gesamten Warenkorb nicht ordnungsgemäß angewendet wurden, wenn mehr als eine Regel angewendet wurde.
* **ACSD-63870** (für Adobe Commerce >=2.4.4 &lt;2.4.4-p11) - Behebt das Problem, dass ein Firmenkunde nicht ordnungsgemäß abgemeldet wurde, wenn sich der Unternehmensstatus während der aktiven Kundensitzung ändert.
* **ACSD-64112** (für Adobe Commerce >=2.4.5 &lt;2.4.8) - Behebt ein Problem, bei dem die `indexer_update_all_views` Cron-Ausführung fehlschlägt, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt ist.
* Aktualisierte Versionen: **ACSD-61622**
* Patches ersetzt: **ACSD-61553**
* Veraltete Patches: **ACSD-61199**

## v1.1.58 {#v1-1-58}

* **ACSD-48570** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Das Problem, dass die Seite zum Zurücksetzen des Kennworts nicht erreicht werden konnte, wurde behoben, indem auf den Link zum Zurücksetzen des Kennworts [!UICONTROL Admin] geklickt wurde, wenn **Store-Code zu URLs hinzufügen** *aktiviert* war, was zuvor dazu führte, dass die Anmeldeseite oder eine 404-Seite angezeigt wurde.
* **ACSD-62118** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Behebt das Problem, dass die `sales_order_tax_item` nicht vollständig aktualisiert wird, wenn [!DNL B2B] Bestellungen mit der Bestellmethode aufgegeben werden.
* **ACSD-63067** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass alle Produktmengen falsch hervorgehoben werden und die *[!DNL Please specify the quantity of product(s).]* für alle Produkte in einem gruppierten Produkt angezeigt wird, wenn nur eine Menge falsch ist.
* **ACSD-63090** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass Warenkorbartikel entfernt wurden, wenn ein Produkt gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde.
* **ACSD-63182** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, bei dem beim Speichern eines doppelten Bundles mit **[!DNL MSI]** (*) ein Fehler*.
* **ACSD-63283** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, bei dem die Bestellung von Artikeln aus der Geschenkregistrierung zu einer Ausnahme führt und bei dem Geschenkregistrierungs-Aktualisierungen Elemente enthalten, die nicht zur Registrierung gehören.
* **ACSD-63299** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass der Sonderpreis für ein konfigurierbares Produkt nicht in der Storefront angezeigt wird.
* **ACSD-63325** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, bei dem beim Senden einer leeren `Syntax Error: Unexpected <EOF>`-Anfrage ein [!DNL GraphQL] auftritt.
* **ACSD-63329** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, dass die Standardwerte für Attribute mit **[!UICONTROL Date]** oder **[!UICONTROL Date and Time]** Eingabetypen beim Erstellen von Produkten über die [!DNL REST API] nicht festgelegt werden.
* **ACSD-63572** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.8) - Behebt das Problem, dass die temporären `CatalogRule` Indexertabellen nicht bereinigt werden, wenn der Indexerprozess beendet wird.
* **ACSD-63578** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass durch Klicken auf die Schaltfläche **[!UICONTROL Delete]** in **[!UICONTROL Add to Order by SKU]** im [!UICONTROL Admin] das [!DNL SKU] nicht entfernt wurde.
* Aktualisierte Versionen: **MDVA-39305-V3**
* Patches ersetzt: **ACSD-56280**
* Veraltete Patches: **ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** (für Adobe Commerce >=2.4.4 &lt;2.4.4-p10) - Es wird das Problem behoben, dass ein Admin-Benutzer mit eingeschränktem Zugriff auf einen bestimmten Store nicht immer alle freigegebenen Kataloge sehen kann, denen die Produkte zugewiesen sind, noch Kunden sehen kann, die nicht gespeichert werden können, was zu Inkonsistenzen im System führt.
* **ACSD-58325** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass die Schaltfläche **[!UICONTROL Import]** auch nach einem Validierungsfehler verfügbar ist.
* **ACSD-59083** (für Adobe Commerce >=2.4.4 &lt;2.5.0) - Behebt das Problem, dass einige Datenbankaktualisierungsvorgänge zu einem Fehler *Basistabelle oder -ansicht nicht gefunden* führen, wenn das [!DNL mview] Update gleichzeitig ausgeführt wird.
* **ACSD-61622** (für Adobe Commerce und Magento Open Source >=2.4.6-p1 &lt;2.4.7) - Es wurde das Problem behoben, dass in der Antwort die kontospezifischen Raten von [!DNL FedEx] fehlen.
* **ACSD-61895** (für Adobe Commerce >=2.4.4 &lt;2.5.0) - Es wird das Problem behoben, bei dem die Kategorien [!DNL GraphQL] Abfrage Kategorien mit der Berechtigung **allow** zurückgeben, selbst wenn die Stammkategorie nicht über die Berechtigung **allow** verfügt.
* **ACSD-62212** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.5.0) - Behebt das Problem, dass der E-**-Inhalt** Kennwort vergessen nicht in die Sprache der Store-Ansicht übersetzt wird.
* **ACSD-62481** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.5.0) - Behebt das Problem, dass der Warenkorb des Kunden leer wird, selbst wenn **[!UICONTROL Persistence]** aktiviert ist.
* **ACSD-62629** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.5.0) - Es wird das Problem behoben, bei dem eine in **[!UICONTROL Widgets]** verwendete Produktliste die Kategoriebedingung nicht widerspiegelt.
* **ACSD-62635** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.5.0) - Behebt das Problem, dass Produkte, die mit mehreren Stores zusammenhängen, in der [!DNL GraphQL]-Produktabfrage nicht richtig angezeigt werden.
* **ACSD-62671** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.5.0) - Behebt das Problem, dass die [!DNL GraphQL] beim ersten Versuch keine aktuellen Adressinformationen zurückgibt.
* **ACSD-62689** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.5.0) - Es wurde das Problem behoben, dass der Kunde nach (**[!UICONTROL Related Product Rules and Widgets]** 4) keine Kategorien in *hinzufügen*.
* **ACSD-62708** (für Adobe Commerce und Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6-p2 || >=2.4.6-p8 &lt;2.4.7-p1) - Behebt das Problem, dass [!DNL TinyMCE] 7-Editor-Schriftgröße in der Admin-Liste *PT* und nicht *PX* anzeigt. Jetzt können Sie die Schriftgröße auch in &quot;*&quot;* &quot;*&quot;*.
* **ACSD-62758** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.5.0) - Behebt das Problem, dass Produktvideos auf der Detailseite des **[!UICONTROL Configurable Product]** nicht korrekt gerendert werden, wenn der [!DNL URL] ausgewählte Optionen enthält.
* **ACSD-62951** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.5.0) - Es wird das Problem behoben, bei dem die E-Mail mit der Gutschrift gesendet wird, ohne Elemente und Gesamtwerte einzuschließen.
* **ACSD-62965** (für Adobe Commerce >=2.4.7 &lt;2.5.0) - Behebt das Problem, dass in der Antwort auf die Bestellplatzierung `LocalizedException` eine [!DNL GraphQL] nicht enthalten ist.
* **ACSD-63286** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, dass Produkte, die einem freigegebenen Katalog über [!DNL API] zugewiesen sind, erst dann in der Storefront angezeigt werden, wenn eine manuelle Neuindizierung durchgeführt wird.
* **ACSD-63326** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.5.0) - Behebt das Problem, dass der [!UICONTROL Admin] nach einer Bestellung über das Backend auf eine fehlerhafte Seite umgeleitet wird.
* Aktualisierte Versionen: **ACSD-51739**
* Ersetzte Patches: **MDVA-43451**, **ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, bei dem ein [!DNL JavaScript] das korrekte Rendern von [!DNL Google Maps] verhindert. Es wurde das Problem behoben, bei dem es viele *Nicht erfasster TypeError: gibt._each ist keine Funktion* Fehler in der Konsole im [!UICONTROL Admin].
* **ACSD-63242** (für Adobe Commerce und Magento Open Source >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Behebt das Problem der verlangsamten Importe beim Hinzufügen von Katalogprodukten mit mehr als 10.000 Einträgen.
* **ACSD-63062** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, dass falsche Warenkorbabzinsberechnungen auftreten, wenn mehrere überlappende Regeln angewendet werden.
* **ACSD-62979** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, bei dem die Verwendung der falschen [!UICONTROL Store ID] in der [!DNL GraphQL]-Kopfzeile einen schwerwiegenden Speicherfehler verursacht.
* **ACSD-62971** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wird das Problem behoben, bei dem der Import von Lagerquellen mit nicht numerischen Werten in der Spalte **quantity** dazu führt, dass **quantity** auf *0* gesetzt wird.
* **ACSD-62872** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem der eindeutigen Attributvalidierung, bei dem Zeitplanaktualisierungen falsch validiert werden.
* **ACSD-62755** (für Adobe Commerce und Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6 || >=2,4,6-p8 &lt;2,4,7 || >=2.4.7-p3 &lt;2.4.8) - Es wird das Problem behoben, bei dem [!DNL TinyMCE] 7 erfordert, dass Schriftgröße und Schriftart in den Editor-Initialisierungseinstellungen speziell hinzugefügt werden.
* **ACSD-62670** (für Adobe Commerce und Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6 || >=2,4,6-p8 &lt;2,4,7 || >=2.4.7-p3 &lt;2.4.8) - Es wird das Problem behoben, bei dem der [!UICONTROL Products Ordered] Bericht nach [!DNL CSV] exportiert und [!DNL XML] einen Fehler zurückgibt.
* **ACSD-62577** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem der langsamen Leistung von Storefront-Suchabfragen, indem sowohl Abfrage- als auch Tabellenindizes optimiert werden.
* **ACSD-62475** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass die [!UICONTROL Gift Card] Produkte falsch im Warenkorb zusammengeführt werden.
* **ACSD-62428** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, bei dem `is_out_of_stock` im Katalogsuchindex auf einen falschen Wert eingestellt ist, wenn die [!DNL SKU] nicht als durchsuchbares Attribut festgelegt ist.
* **ACSD-62355** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Verbessert die Ladezeit der konfigurierbaren Produktbearbeitungsseite, wenn das konfigurierbare Produkt auf vielen Attributen mit vielen Werten basiert.
* **ACSD-61805** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass Produkte in der Storefront nicht vorrätig sind, nachdem der Auftragsstatus über die [!DNL REST API] aktualisiert wurde.
* **ACSD-60811** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, dass das Aktualisieren des Bestellstatus mit einem benutzerdefinierten Wert oder Kommentar nur möglich ist, wenn der aktuelle Status entweder *Verarbeitung* oder *Betrug* ist.
* **ACSD-62952** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass das [!UICONTROL Gift Registry] falsch in der Storefront angezeigt wird.
* **ACSD-55339** [!DNL SKU] (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass ein Produkt, das mit „0“ (Null) beginnt, die „0“ entfernt, was verhindert, dass das Angebot aktualisiert wird.
**
* Aktualisierte Patches: **ACSD-59514**
* Aktualisierte Versionen: **ACSD-60816**
* Patches ersetzt: **ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass durch die Ausgabe einer Rückerstattung über die [!DNL REST API] mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, doppelte Gutschriften erstellt wurden.
* **ACSD-58471** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass dynamischer Inhalt nicht auf der Produktdetailseite geladen werden kann, wenn die zugehörigen Katalogpreisregeln geplant wurden.
* **ACSD-58566** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Behebt das Problem, dass [!DNL GraphQL] bei der Abfrage des `created_at` in der `addPurchaseOrderComment`-Mutation einen internen Server-Fehler zurückgibt.
* **ACSD-58685** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass Verkaufs-E-Mails, die initiiert wurden, während die E-Mail-Kommunikation deaktiviert war, weiterhin gesendet wurden, sobald die E-Mail-Kommunikation erneut aktiviert wurde.
* **ACSD-58735** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass ein Admin mit eingeschränktem Administratorzugriff die abgebrochenen Warenkörbe auf der Seite „Kundenkonto“ im [!UICONTROL Admin] für eine zugehörige Website nicht anzeigen konnte.
* **ACSD-58828** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Es wird das Problem behoben, bei dem die Server-seitige Validierungsmeldung *address ist erforderlich* angezeigt wird, wenn ein erforderliches Feld neben der Client-seitigen Validierungsmeldung leer gelassen wird. Bei der Server-seitigen Validierung wird die Meldung für leere erforderliche Felder nicht angezeigt, und die Client-seitige Validierung verarbeitet die Fehlerbenachrichtigung mit dem Hinweis: *Dies ist ein erforderliches Feld.*
* **ACSD-60344** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass doppelte E-Mails zur Bestellbestätigung gesendet wurden, wenn ein **[!UICONTROL Purchase Order]** mit automatischer Genehmigung verwendet wurde.
* **ACSD-61348** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass Wunschlistenelemente in einer Umgebung mit mehreren Websites über [!DNL GraphQL], aber nicht in der Storefront angezeigt werden.
* **ACSD-61534** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, dass die Design-Konfiguration nicht mit dem Befehl `bin/magento config:set` festgelegt werden konnte und gesperrte Werte durch Formularbearbeitung geändert werden konnten. Jetzt können gesperrte Werte, die aus dem [!DNL CLI] mit `--lock-env` oder `--lock-conf` festgelegt wurden, nicht aktualisiert werden.
* **ACSD-61785** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass das Aktualisieren des `reward_warning_notification`-Attributs nicht über [!DNL GraphQL] Mutations- und [!DNL REST API]-Aufrufe möglich war, wodurch das Verhalten an `reward_update_notification` angepasst wurde.
* **ACSD-62591** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, dass das Design nicht richtig wechselt, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind.
* **ACSD-62793** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, bei dem `datetime` Attribute in exportierten Daten die Zeitkomponente nicht enthalten. Wenn **[!UICONTROL Fields Enclosure]** *aktiviert* ist, werden Attributwerte in der `additional_attributes` Spalte außerdem in doppelte Anführungszeichen gesetzt.
* **ACSD-62332** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass die Produktauflistung [!DNL GraphQL] die Abfrage auf eine `total_count` von 10.000 Produkten beschränkt war. Es wurde ein Problem behoben, bei dem [!DNL Live Search] bei der Abfrage über *die aktuelle Seite**statt Seite* 2[!DNL GraphQL] in den Suchkriterien setzte.
* Aktualisierte Versionen: **ACSD-46581**, **ACSD-49513**, **ACSD-52801**, **ACSD-59514**
* Patches ersetzt: **ACSD-52801**, **ACSD-55100**
* Veraltete Patches: **ACSD-52085**, **ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** (für Adobe Commerce und Magento Open Source 2.4.6-p8) - Stellt rückwärts inkompatible Änderungen der Platzierungsreihenfolge wieder her, die in 2.4.6-p8 enthalten sind.
* **ACSD-60267** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass die feste Produktsteuer (FPT) korrekt angewendet wird, wenn einfache Produkte mit FPT direkt zum Warenkorb hinzugefügt werden, aber bei der Auswahl dieser Produkte über konfigurierbare Produktoptionen fehlschlägt.
* **ACSD-61103** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass die Fehleranzahl in der `customer_entity` nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat.
* **ACSD-61134** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wird das Problem behoben, dass die Auswahl der [!DNL Braintree Vault] Zahlungsmethode im Checkout-Workflow automatisch aufgehoben wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem er das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert.
* **ACSD-61199** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass die Registerkarte &quot;CMS-Seitenhierarchie“ beim Bearbeiten einer CMS-Seite mit einer bestehenden Hierarchie keine ordnungsgemäße Baumstruktur anzeigt.
* **ACSD-61200** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass in den Berechnungen für *[!UICONTROL Total Amount]* und *[!UICONTROL Total Amount Actual]* im Vertrieb die *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* fehlen, was zu Diskrepanzen in den Kundenauftragsdaten führt.
* **ACSD-61522** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass es möglich ist, E-Mail-Adressen in die *[!UICONTROL First Name]*- und *[!UICONTROL Last Name]* des Gastkunden einzugeben und ungültige E-Mails zur Bestellbestätigung zu senden.
* **ACSD-61756** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Verbessert die Leistung `AdvancedSalesRule` Filter.
* **ACSD-61799** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebt das Problem, dass der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden.
* **ACSD-61845** (für Adobe Commerce und Magento Open Source >=2.4.7-p1 &lt;2.4.8) - Behebt den Fehler, der auftritt, wenn eine Anfrage nur mit dem Accept-Header *text/*) gesendet wird.
* **ACSD-62056** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass das Hochladen von Bildern für ein konfigurierbares Produkt fehlschlägt, wenn MSI installiert ist.
* **ACSD-62485** (für Adobe Commerce >=2.4.4 &lt;2.4.6-p8 || >=2.4.7 &lt;2.4.8) - Es wurde das Problem behoben, bei dem `async.operations.all` Verbraucher nach der Erstellung eines Unternehmens nicht mehr funktioniert.
* Aktualisierte Versionen: **ACSD-48661**, **ACSD-55100**, **ACSD-61553**
* Veraltete Patches: **ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, dass die Verschachtelung der Umgebungs-Emulation nicht zulässig ist. Die Emulation beginnt nun während des `send()`-Aufrufs, sobald die Emulation während des `getInfoBlockHtml()`-Aufrufs beendet wird.
* **ACSD-59930** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Verbessert die Performance der **[!UICONTROL Create]**, **[!UICONTROL Save]** und **[!UICONTROL Delete]** des Unternehmens.
* **ACSD-60584** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, dass ein für Benutzende auf einer Website erstelltes Zugriffstoken auf andere Websites zugreifen oder Kundeninformationen ändern darf.
* **ACSD-60804** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass das Bearbeiten eines Kunden, der mit einem gelöschten Unternehmen verknüpft ist, den Fehler *Aufruf einer Memberfunktion `getSuperUserId()` null* verursacht.
* **ACSD-61133** (für Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.8) - Es wurde das Problem behoben, dass der `sales_clean_quotes` [!DNL cron] Angebote aus nicht genehmigten Bestellungen löscht.
* **ACSD-61528** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Es wird das Problem behoben, bei dem das Abrufen von Rollen aus dem [!UICONTROL Admin] mithilfe von [!DNL GraphQL] keine Ergebnisse zurückgibt.
* **ACSD-61553** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, bei dem **[!UICONTROL Cart Price Rule]** Rabatte falsch berechnet werden, wenn mehrere Rabatte mit unterschiedlichen Prioritäten und **[!UICONTROL Maximum Qty Discount is Applied To]** auf das Produkt angewendet werden.
* **ACSD-61667** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Verbessert die Inventarleistung für die Versanderstellung bei vielen Quellen mit Abholung im Laden.
* **ACSD-61969** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass Benutzende einen Gutscheincode eingeben müssen, bei dem die Groß-/Kleinschreibung beachtet wird und der genau mit dem Gutscheincode übereinstimmt, der konfiguriert wurde.
* Aktualisierte Versionen: **ACSD-54989**, **ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** (für Adobe Commerce und Magento Open Source) - Fügt alle erforderlichen Felder hinzu, um die Anforderungen des 3DS-VISA-Mandats zu erfüllen, wenn [!DNL Braintree] als Zahlungs-Gateway verwendet wird.
* **ACSD-59366** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Behebt das Problem, dass beim Versuch, ein Team zu löschen, das deaktivierte Benutzende enthält, die nicht in der Teamliste sichtbar sind, ein Fehler auftritt.
* **ACSD-59865** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass ein [!UICONTROL Cart Price Rule] zuvor angewendete Regeln nicht aufhebt, wenn die Menge des Produkts im Warenkorb nicht ausreicht, um die Regeln anzuwenden.
* **ACSD-59925** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem beim Sortieren von Elementen in der [!UICONTROL Media Gallery] nach Position in GraphQL.
* **ACSD-59952** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass beim Erstellen eines [!UICONTROL Shared Catalog] mit einer Gruppen-ID, die einem bestehenden [!UICONTROL Shared Catalog] zugewiesen ist, ein Fehler auftritt.
* **ACSD-60590** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Verbessert die Leistung bei der Generierung von [!UICONTROL Bestsellers Aggregated Daily Reports] für eine große Anzahl aufgegebener Bestellungen.
* **ACSD-60673** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass die [!UICONTROL Cart Price Rule] für mehrere Zahlungsmethoden an der Kasse nicht angemessen auf die spezifische Zahlungsmethode angewendet wird.
* **ACSD-60684** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass die Sortierung von GraphQL-Produkten nach mehreren Feldern nicht wie erwartet funktioniert.
* **ACSD-60788** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, dass benutzerdefinierte Skripte für [!DNL Google Tag Manager] aufgrund von CSP-Fehlern (Content Security Policy) nicht ausgeführt werden.
* **ACSD-61322** (für Adobe Commerce >=2.4.6 &lt;2.4.8) - Behebt das Problem, dass [!UICONTROL Products/Categories], die nicht dem [!UICONTROL Shared Catalog] für die Standardgruppe (Allgemeine Gruppe) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind.
* **ACSD-61366** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass der `setup:static-content:deploy --jobs 4`-Befehl mit mehreren fehlgeschlagenen Aufträgen ausgeführt wird, wobei der *Port muss im Host-Parameter konfiguriert werden* Fehler auftritt, wenn der Port für die DB-Verbindung angegeben wird.
* Aktualisierte Patches: ACSD-51857, ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.8) - Es wurde das Problem behoben, bei dem GraphQL beim Abrufen einer Angebots-ID für ein abgelaufenes Angebot einen internen Server-Fehler zurückgibt.
* **ACSD-60234** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Behebt das Problem, dass bei der [!DNL PayPal] ein falscher Betrag angezeigt wird, wenn der Rabatt von der Zahlungsmethode angewendet wird.
* **ACSD-59967** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7-p2) - Behebt das Problem, dass ein JavaScript-Fehler [!DNL Google Maps] daran hindert, korrekt zu rendern.
* **ACSD-60326** (für Adobe Commerce >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, bei dem in der GraphQL-Abfrage für den Kundenrückgabestatus ein Fehler auftrat.
* **ACSD-60538** (für Adobe Commerce >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, dass, wenn ein Produkt in *[!UICONTROL All Store Views]* deaktiviert und nur in bestimmten Bereichen der Store-Ansicht aktiviert ist, die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt werden, was dazu führt, dass das Produkt nicht richtig angezeigt wird.
* **ACSD-60631** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, bei dem GraphQL einen Fehler zurückgibt, wenn dasselbe einfache Produkt mehreren konfigurierbaren Produkten zugewiesen wird.
* **ACSD-60632** (für Adobe Commerce und Magento Open Source >=2.4.5-p8 &lt;2.4.8) - Es wird das Problem behoben, dass bei jedem Versuch einer Auftragserteilung eine neue Adresse gespeichert wird, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht.
* **ACSD-60816** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass die vom APM-Agent injizierten [!DNL New Relic Browser Monitoring]-Skripte nicht mit CSP (Content Security Policy) konform sind und ihre Ausführung verhindern.
* **ACSD-61195** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt das Problem, dass auf der letzten Seite keine Artikel im Warenkorb für die GraphQL-Warenkorbanfrage zurückgegeben werden.
* Aktualisierte Patches: ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebt den Fehler *Aufruf an undefinierte Methode ReflectionUnionType::getName()* der bei der Installation von 2.4.4-pX-Versionen auftritt.
* **ACSD-45049** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6) - Es wurde das Problem behoben, dass eine Einstellung für das Kundenattribut *[!UICONTROL Is required]* gemäß Website-Umfang in Admin nicht ordnungsgemäß funktioniert.
* **ACSD-46938** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem mit der Performance der DB-Trigger-Neuerstellung während der `setup:upgrade`.
* **ACSD-48210** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wird das Problem behoben, bei dem durch die Aktualisierung eines *[!UICONTROL Website Scope]*-Attributs in einer bestimmten Store-Ansicht die Attributwerte im globalen Umfang überschrieben werden.
* **ACSD-54887** (für Adobe Commerce und Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2,4,5-p3 &lt;2,4,5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Behebt das Problem, dass der Warenkorb des Kunden nach Ablauf der Kundensitzung mit aktiviertem [!UICONTROL Persistent Shopping Cart] geleert wird.
* **ACSD-58141** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Es wurde das Problem behoben, dass PHPSESSID bei POST-Anfragen im Bereich der Storefront für einen angemeldeten Kunden neu generiert, wenn der [!DNL L2 Redis cache] aktiviert ist und der Kunde von „Admin“ aktualisiert wurde.
* **ACSD-58352** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Es wird das Problem behoben, bei dem Rückgabeattributbeschriftungen für die Standardspeicheransicht über die GraphQL-API zurückgegeben werden, wenn in der Anfragekopfzeile eine nicht standardmäßige Speicheransicht angegeben ist.
* **ACSD-58442** (für Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Es wurde das Problem behoben, dass Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt wurden, wodurch das Menü und die Kopfzeile in einer Mobilansicht anstelle eines Desktops geladen wurden.
* **ACSD-58790** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.8) - Fixes der Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobilansicht auf [!DNL Chrome].
* **ACSD-59036** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebt eine Ausnahme, die beim Laden von Produktpreisen mit unteren und oberen Grenzen gleich $0 auftritt.
* **ACSD-59229** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, dass Informationen zu Kundengruppen aufgrund des alten Wertes der X-Magento-Vary-Anfrage im falschen Segment gespeichert wurden.
* **ACSD-59378** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wurde das Problem behoben, bei dem URL-Neuschreibungen auf Store-Ebene beim Import fälschlicherweise aktualisiert wurden.
* **ACSD-59514** (für Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Behebt das Problem, dass Formulare im Admin-Bereich mit [!DNL Page Builder] den Fehler auslösten, den *[!DNL Page Builder]5 Sekunden lang gerendert hat, ohne Sperren freizugeben.nach dem Senden des Formulars in der Browser-Konsole* und Änderungen können nicht gespeichert werden.
* **ACSD-60303** (für Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2,4,5-p8 &lt;2,4,6 || >=2.4.6-p6 &lt;2.4.8) - Behebt das Problem, dass eine Bestellung vom Administrator nicht aufgegeben werden kann, wenn die HTML-Minimierung aktiviert ist.
* **ACSD-60441** (für Adobe Commerce und Magento Open Source 2.4.4-p9 || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Behebt das Problem bei der Aktualisierung von Kundinnen und Kunden über `V1/customers` [!DNL REST API]-Endpunkt bei Verwendung des vom Backend generierten Integrations-Zugriffstokens.
* Aktualisierte Patches: ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wurde das Problem behoben, dass Produktbilder nach dem Löschen eines Staging-Updates entfernt wurden.
* **ACSD-57086** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wurde das Problem behoben, dass Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen nicht korrekt verarbeitet wurden.
* **ACSD-57588** (für Adobe Commerce und Magento Open Source Trigger >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass beim Versand einer Bestellung an mehrere Adressen bei der Verarbeitung der Regions-ID ein Fehler auftrat.
* **ACSD-57643** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass Produkte mit benutzerdefinierten Optionen fälschlicherweise über GraphQL zum Warenkorb hinzugefügt wurden.
* **ACSD-57846** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass GraphQL-Produkte, die mit einem Filter nach Nullpreisen suchen, aufgrund einer Ausnahme keine Ergebnisse zurückgeben.
* **ACSD-57941** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, bei dem Produktoptionen fälschlicherweise dem Admin Store anstatt den jeweiligen Stores zugewiesen werden.
* **ACSD-58375** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass beim Hinzufügen eines *[!DNL YouTube API Key]* Videos auf Store-Ansichtsebene durch eine falsche [!DNL YouTube]-Konfiguration ein Fehler verursacht wird.
* **ACSD-58739** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Es wird das Problem behoben, bei dem eine partielle Neuindizierung einen Fehler auslöst.
* **ACSD-58446** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, dass beim Löschen eines Teams mit untergeordneten Benutzenden oder Teams unabhängig von deren Status (inaktiv) das System eine informative Fehlermeldung bereitstellt, die nicht mit der Benutzeroberfläche übereinstimmt.
* **ACSD-58054** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass es möglich ist, Kunden-Token für inaktive Kunden über die API zu generieren.
* **ACSD-58163** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass ein *[!UICONTROL Cart Price Rule]* ohne Couponcode keinen Rabatt für einen Gastkunden aus dem entsprechenden *[!UICONTROL Customer Segment]* anwendet.
* **ACSD-57045** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass URL-Neuschreibungen zu unendlicher Seitenschleife führen, nachdem *[!UICONTROL Website Root]* für *[!UICONTROL Hierarchy]* deaktiviert wurde.
* Aktualisierte Patches: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass die `mergeCart`-Mutation mit &quot;*Interner Server-Fehler*&quot; in der [!DNL GraphQL]-Antwort fehlschlägt, wenn Quell- und Zielkarten zusammengeführt werden, die dieselben Bundle-Elemente enthalten.
* **ACSD-56546** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass konfigurierbare und gebündelte Produkte in der Storefront als **Nicht vorrätig** angezeigt werden, wenn die **Nicht vorrätig anzeigen** *Deaktiviert*.
* **ACSD-56635** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn ein Import verwendet wird, wobei **Kontofreigabe** auf &quot;*Global*&quot; festgelegt ist.
* **ACSD-56741** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt die Fehlermeldung &quot;*Zugriff auf Array-Offset mit dem Wert vom Typ null*&quot;, die während der `setup:upgrade` angezeigt wird, wenn die Datenbank einen benutzerdefinierten [!DNL MySQL]-Trigger enthält, der nicht mit dem Indexierungsmechanismus und der [!DNL MView] in Zusammenhang steht.
* **ACSD-57315** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, wenn in [!DNL PayPal Payflow Pro] jedes Mal, wenn auf die [!UICONTROL Fetch]-Schaltfläche im Bildschirm &quot;**[!UICONTROL View transaction]**&quot; in Admin geklickt wird, eine neue Transaktion erstellt wird.
* **ACSD-57337** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Es wird das Problem behoben, dass ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im **[!UICONTROL Companies]** anzeigen kann.
* **ACSD-57394** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem der falschen Produktsortierung nach mehreren Sortierfeldern in [!DNL GraphQL].
* **ACSD-57565** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, dass im **[!UICONTROL Order]**-Dashboard falsche Bestellinformationen angezeigt werden, bis der Zeitraum aktualisiert wird. Das Dashboard zeigt jetzt die richtigen Bestellstatistiken beim ersten Laden an.
* **ACSD-57854** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass [!DNL GraphQL]-Anfragen in den Kategorieaggregationen deaktivierte Kategorien zurückgaben.
* **ACSD-58008** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, bei dem durch die Aktualisierung eines geplanten Updates die vorherige Version eines Staging-Elements entfernt wurde, wenn kein Enddatum angegeben wurde.
* Aktualisierte Patches: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wird das Problem behoben, bei dem *[!UICONTROL Used]*- und *[!UICONTROL Times Used]*-Attribute falsche Werte für generierte Coupons anzeigen, wenn sie während des Auscheckens mit mehreren Adressen verwendet werden.
* **ACSD-56760** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass ein Admin-Benutzer, der auf eine bestimmte Website beschränkt ist, keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat.
* **ACSD-56858** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, bei dem B2B-Unternehmensrollenberechtigungen für einen eingeschränkten Unternehmensadministrator falsch angezeigt werden.
* **ACSD-57074** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass das benutzerdefinierte Attribut *Ja/Nein* mit `attrbute_code`, das mit `price_` beginnt, bei der Indizierung nicht richtig funktioniert und Produkte mit solchen Attributen am Frontend nicht verfügbar sind.
* Aktualisierte Patches: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass die Kategorieseiten-Caches ungültig werden, wenn sich die Lagermenge ändert, auch wenn das Produkt noch auf Lager ist.
* **ACSD-54656** (für Adobe Commerce >=2.4.5 &lt;2.4.6) - Behebt das Problem, dass das unsichtbare reCAPTCHA beim Checkout fehlschlägt, was die Abgabe einer Bestellung verhindert.
* **ACSD-55100** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass GraphQL nicht mehr als 10.000 Produkte in den Suchergebnissen zurückgibt.
* **ACSD-56621** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass der aktualisierte Vor- und Nachname im Abschnitt Grußkopfzeile für den Benutzer „Unternehmensadmin“ nicht angezeigt wird.
* **ACSD-56842** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass die verzögerten Proxys und die verzögerten Proxy-Factories fehlen, nachdem `setup:di:compile` ausgeführt wurde.
* **ACSD-57003** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass der Bestellstatus in *[!UICONTROL Complete]* geändert wird, anstatt in *[!UICONTROL Processing]* geändert zu werden, wenn eine Bestellung teilweise zurückerstattet und teilweise versendet wird.
* Aktualisierte Patches: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wird das Problem behoben, dass ein konfigurierbares Produkt nicht mehr vorrätig ist, wenn eines von zwei untergeordneten Produkten durch ein geplantes Update deaktiviert wird.
* **ACSD-56616** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebt das Problem, dass gebündelte Produkte in der Storefront als vorrätig angezeigt werden, wenn ihre einfachen Produkte nicht vorrätig sind.
* **ACSD-56515** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Administrator mit Berechtigungen auf Website-Ebene keinen dynamischen Block hinzufügen oder bearbeiten kann.
* **ACSD-56447** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wird das Problem behoben, bei dem das Hinzufügen desselben Produkts zum Warenkorb über parallele REST-Web-API-Anfragen zu zwei separaten Artikeln im Warenkorb führt.
* **ACSD-56415** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass die Performance der partiellen Preisindizierung aufgrund einer `DELETE` Abfrage verlangsamt wird, wenn die Datenbank viele partielle Preisdaten zum Indizieren hat.
* **ACSD-54965** (für Adobe Commerce >=2.4.5 &lt;2.4.6) - Es wird das Problem behoben, dass im Visual Merchandising-Raster nicht der richtige Bestand angezeigt wird, wenn ein Produkt nur einem benutzerdefinierten Bestand zugewiesen wird.
* **ACSD-52824** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass die Schaltflächen PayPal Express, Google Pay und Apple Pay für Unternehmenskunden angezeigt werden, wenn solche Zahlungsmethoden in den Unternehmenseinstellungen deaktiviert sind.
* Aktualisierte Patches: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, bei dem Benutzende beim Sortieren von Kategorieprodukten mit der Option **Aus dem Lager nach unten** zum Admin-Dashboard umgeleitet werden und der `Invalid security or form key. Please refresh the page` oben auf dem Bildschirm angezeigt wird.
* **ACSD-56280** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Es wird das Problem behoben, bei dem die Bestellung von Artikeln aus einer Geschenkregistrierung zu einer Ausnahme führt.
* **ACSD-56246** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, bei dem Daten aus dem benutzerdefinierten Mehrfachauswahlattribut entfernt werden, wenn ein geplantes Update für ein Produkt aktiv wird.
* **ACSD-56193** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4) - Es wurde das Problem behoben, dass der Varnish/Fastly-Cache nicht aktualisiert wurde, wenn ein geplanter Block in der Kategoriebeschreibung mit Page Builder verwendet wurde.
* **ACSD-56158** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, bei dem die Abfrage „Warenkorb“ den Gesamtsteuerwert für jede Steuerregel zurückgibt.
* **ACSD-56023** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass Widget-Inhalte auf der CMS-Seite nicht aktualisiert werden, wenn der Cache aktiviert ist.
* **ACSD-55427** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, dass Admins die Zuweisung eines Produkts zu einem freigegebenen Katalog auf der Produktseite in Admin nicht aufheben können.
* **ACSD-55352** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wird das Problem behoben, dass nach dem Erstellen einer partiellen Gutschrift mit Belohnungspunkten für Kunden der Bestellstatus in „Geschlossen“ geändert wird und die Optionen für Gutschriften auf der Seite „Admin-Auftrag“ nicht mehr angezeigt werden.
* **ACSD-55231** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass Produkte nicht über die Schnellbestellungsfunktion zum Warenkorb hinzugefügt werden können.
* **ACSD-54283** (für Adobe Commerce >=2.4.3 &lt;2.4.4) - Es wird das Problem behoben, dass Produkte/Kategorien, die nicht dem freigegebenen Katalog für die Standardkategorie (allgemeine Gruppe) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind.
* Aktualisierte Patches: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass die kanonische Kategorie-URL nach dem Ändern der Kategorie-URL nicht aktualisiert wurde.
* **ACSD-53636** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5) - Behebt das Problem, dass der reguläre Preis auf Produktlistenseiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen nicht angezeigt wird.
* **ACSD-54885** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem mit dem Auschecken mehrerer Adressen, wenn der Administrator die Funktion *Als Kunde anmelden* verwendet.
* **ACSD-55610** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist.
* **ACSD-55334** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigiert Übersetzungen für Beschriftungen durch Übersetzungswörterbücher in der GraphQL-Antwort.
* **ACSD-54739** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, bei dem die Bedingung für den Produktbestandsstatus für zugehörige Produktregeln nicht angewendet wird.
* **ACSD-53925** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass der Administrator den CMS-Block nicht mit dem Produktkarussell speichern konnte, wenn `catalog_product_price` Dimensionsmodus auf &quot;*&quot;*.
* **ACSD-52714** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wird das Problem behoben, dass der Datumsfilter im Admin-Raster nicht funktioniert, wenn das Datumsformat auf *Y-m-d* festgelegt ist.
* **ACSD-55055** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Verbessert die Leistung beim Laden von Produktattributen in Warenkorbpreisregeln im Warenkorb.
* **ACSD-53790** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass mehrere RMAs für ein einzelnes Produkt über die REST-API erstellt werden können.
* **ACSD-56090** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5) - Es wird das Problem behoben, dass die GraphQL-Anfrage mit den Daten aller Stores und nicht mit den spezifisch angeforderten Store-Daten antwortet.
* **ACSD-54983** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass es nicht möglich war, die UID des Firmenbenutzers mit der GraphQL-Anfrage abzurufen, wenn der Benutzerstatus auf *[!UICONTROL Inactive]* gesetzt war.
* **ACSD-53309** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass bei Auswahl der anpassbaren Option im *[!UICONTROL Regular Price]*-Label keine Steuer vollständig angewendet wird.
* **ACSD-55305** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass das *[!UICONTROL Edit Company User]*-Popup auf der Seite **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** mit einem Lader auf dem Bildschirm einfriert.
* Aktualisierte Patches: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, bei dem *[!UICONTROL Recently Viewed]* Produktdaten in der Store-Ansicht nicht ordnungsgemäß aktualisiert wurden.
* **ACSD-54626** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass keine neue Bestellregel (`createPurchaseOrderApprovalRule`) mit dem `NUMBER_OF_SKUS`-Attribut über [!DNL GraphQL] erstellt werden kann.
* **ACSD-53845** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt das [!DNL MySQL] Verbindungs-Timeout-Problem, wenn `consumer max_messages` = 0 ist.
* **ACSD-54890** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt das Problem, bei dem `aggregate_sales_report_bestsellers_data` aufgrund [!DNL MySQL] Speicherplatzes `/tmp` verursacht.
* **ACSD-55112** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wird das Problem behoben, dass die Schaltfläche *[!UICONTROL Submit review]* mehrmals ohne [!DNL Google reCAPTCHA v3] Validierung angeklickt werden kann.
* **ACSD-54264** (für Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Behebt das Problem, dass die Fehlermeldung „Sie können das angeforderte Attribut nicht aktualisieren *Zeilenkennung: store_id“* wird angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Shop-Ansicht auszuchecken.
* **ACSD-54418** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wird das Problem behoben, bei dem fälschlicherweise ein fester Rabattbetrag auf jedes untergeordnete Produkt des dynamisch berechneten Bundles angewendet wird.
* **ACSD-55238** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fehlerbehebungen beim Speichern der leeren *[!UICONTROL Meta Description]*.
* **ACSD-54966** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Gutscheincode mit einer eingeschränkten Nutzung pro Kunde nicht wiederverwendet werden kann, wenn die vorherige Bestellung fehlgeschlagen ist.
* **ACSD-54060** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wird das Problem behoben, dass ein Admin mit Zugriffsbeschränkung ein Produkt nicht speichern kann, wenn es sich um ein untergeordnetes Produkt eines anderen Produkts handelt, das einem anderen Umfang zugewiesen wurde.
* **ACSD-48910** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wurde ein Problem behoben, bei dem ein Bündelprodukt, das mehreren Bezugsquellen zugewiesen ist, nach der Fakturierung und dem Versand einer Bestellung nicht mehr vorrätig ist, selbst wenn es noch eine Menge ungleich null aufweist.
* **ACSD-55381** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebt einen internen Server-Fehler bei der Abfrage von `configurable_product_option_uid`- und `configurable_product_option_value_uid` von Feldern aus einer [!DNL B2B] *[!UICONTROL Requisition list]* über [!DNL GraphQL].
* **ACSD-55628** (für Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Fehlerbehebungen beim Hochladen einer Datei auf dem Unternehmensregistrierungsformular und beim Ersetzen einer Datei durch ein Kundenattribut in der Storefront.
* Aktualisierte Patches: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebt das Problem, das im Warenkorb auftritt, wenn ein Produkt aus dem freigegebenen Katalog entfernt wird, nachdem es bereits zum Warenkorb hinzugefügt wurde.
* **ACSD-53722** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass der Preis für die gebündelten Produktoptionen auf $0 geändert wird, wenn geplante Updates für verschiedene Bereiche aktiv werden.
* **ACSD-53643** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass die Bestellung eine falsche Summe aufweist, wenn eine Bestellung mit deaktivierten oder nicht vorrätigen Produkten aufgegeben wird. Dies wird behoben, indem die Schaltfläche *[!UICONTROL Place Order]* für solche Bestellungen ausgeblendet wird.
* **ACSD-54067** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt das Problem, dass ein Produktvideo nicht auf einem Mobilgerät wiedergegeben wird.
* **ACSD-55414** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Verbessert die Leistung, wenn MariaDB versucht, die EAV-entity_id von der Zeichenfolge in eine Ganzzahl umzuwandeln.
* **ACSD-51819** (für Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Es wurde das Problem behoben, dass mehrere Bestellungen mit derselben Angebots-ID aufgegeben werden können.
* **ACSD-53118** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Es wird das Problem behoben, dass die *[!UICONTROL Cart Price Rule]* mithilfe des Couponcodes angewendet wird, während das Produkt ein leeres -Attribut aufweist, was hätte zur Invalidierung der Regel führen müssen.
* **ACSD-54324** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, dass die Anfrage &quot;GraphQL requirement_lists“ die Paginierungseinstellungen nicht berücksichtigt und alle Ergebnisse zurückgibt.
* Aktualisierte Patches: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (für Adobe Commerce >=2.4.0 &lt;2.4.6) - Behebt das Problem, dass es nicht möglich ist, ein B2B-Angebot zu verarbeiten, das für ein Produkt mit mehreren zugewiesenen Quellen eingereicht wurde.
* **ACSD-54040** (für Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Es wird das Problem behoben, bei dem das Feld *[!UICONTROL Created]* leer ist, um Details zur Reihenfolge anzuzeigen, wenn B2B-Module aktiviert sind.
* **ACSD-54319** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Es wurde das Problem behoben, bei dem der Produktpreis im *[!UICONTROL Product in Cart]* Bericht null anzeigt.
* **ACSD-53378** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Verbessert die Ladezeit der Kaufbestätigungsseite für Kunden mit großen Adressbüchern.
* **ACSD-52657** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, dass das Minicart im sekundären StoreReview, der eine Subdomain verwendet, nicht aktualisiert wird.
* **ACSD-53414** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Benutzer mit eingeschränktem Administratorzugriff CMS-Seiten außerhalb seines Berechtigungsbereichs sehen kann.
* **ACSD-54472** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass sich Kunden eines abgelehnten Unternehmens weiterhin authentifizieren können und Kunden eines blockierten und eines abgelehnten Unternehmens weiterhin Bestellungen aufgeben können. Der Patch fügt zusätzliche Validierungen für GraphQL-Endpunkte hinzu.
* **ACSD-52801** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fügt die Option für eine Teilübereinstimmung bei der Suche nach Produkten in GraphQL hinzu.
* **ACSD-55004** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass der Validator beim Hochladen einer Importdatei, die größer ist als der in `php.ini` konfigurierte Wert, abstürzte.
* **ACSD-54989** (für Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Behebt das Problem, dass ein Unternehmensadministrator keine Bestellung aufgeben kann, wenn *[!UICONTROL Enable Purchase Orders]* auf *[!UICONTROL Yes]* und *[!UICONTROL Purchase Order]* auf *[!UICONTROL No]* eingestellt ist.
* **ACSD-54007** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *„Undefined Array key „_scope“* beim Importieren von Kundendaten.
* **ACSD-55031** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebt den Fehler *Typ „gemischt“ kann nicht null sein* während der Kompilierung.
* **ACSD-54961** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Benutzer mit eingeschränktem Administratorzugriff den Status *Produktüberprüfung“ nicht* aktualisieren kann.
* **ACSD-55256** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass nur das erste Bild erfolgreich im Bildregler angezeigt wird.
* Aktualisierte Patches: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Behebt das Problem, dass der Belohnungspunktverlauf nach Ablauf der Belohnungspunkte falsch berechnet wird.
* **ACSD-53583** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Verbessert die partielle Neuindizierungsleistung für *Kategorieprodukte* und *Produktkategorien* Indexer.
* **ACSD-54026** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage für einen nicht autorisierten Benutzer.
* **ACSD-54106** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5) - Es wurde das Problem behoben, bei dem die Sortierung von Kategorieprodukten nach Namen für Zeichen mit türkischem Akzent falsch ist.
* **ACSD-52219** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass in Admin-Rastern gespeicherte Filter beim häufigen Wechsel zwischen Lesezeichenansichten nicht wie erwartet funktionieren.
* **ACSD-54342** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt eine falsche Fehlermeldung *Fehler in Datenstruktur: Werte werden gemischt* beim Importieren einer CSV-Datei ohne gültige Daten.
* **ACSD-54660** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Es wurde ein neues Eingabeattribut *sort* hinzugefügt, um Kundenaufträge in GraphQL nach `sort_field` und `sort_direction` zu sortieren.
* **ACSD-54776** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, dass nicht aktivierte *[!UICONTROL Use Default Value]*- und nicht standardmäßige Produktfeldwerte für die zweite Website-, Store- und Store-Ansicht nicht gespeichert werden.
* **ACSD-53998** (für Adobe Commerce und Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Behebt das Problem, dass ein auf einem **[!UICONTROL Dynamic Block]** basierendes **[!UICONTROL Customer Segment]** nach der Abmeldung von einem Kundenkonto nicht ordnungsgemäß funktioniert.
* **ACSD-53204** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Fehlerbehebungen *Das Produkt kann nicht gespeichert werden.* bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des `rest/V1/products/<sku>/media`-Endpunkts.
* **ACSD-47657** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde ein Zwischenspeicherungsmechanismus für AWS-Anmeldeinformationen hinzugefügt. Ein Anmeldedaten-Anbieter verwendet jetzt den Magento-Cache, um die von AWS für die EC2-Konfiguration abgerufenen Anmeldedaten zwischenzuspeichern.
* Aktualisierte Patches: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4) - Es wird das Problem behoben, dass Produkte, die einem freigegebenen Katalog zugewiesen sind, nicht in der Storefront angezeigt werden, wenn ein partieller Index ausgeführt wird.
* **ACSD-54018** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebt Leistungsprobleme mit dem [!UICONTROL Product List]-Widget, das in der Widget-Bedingung ein nicht-globales Attribut verwendet.
* **ACSD-54111** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebt das Problem, dass die Produktminiaturbilder nicht in der Storefront angezeigt werden, wenn das Seitenverhältnis des Wasserzeichenbildes nicht mit dem Produktbild übereinstimmt.
* **ACSD-47669** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Fehlerbehebungen *Integritätsbeschränkungsverletzung: 1452 Untergeordnete Zeile kann nicht hinzugefügt oder aktualisiert werden: Eine Fremdschlüsselbeschränkung schlägt fehl* Fehler beim Importieren von CSV-Produkten.
* **ACSD-53347** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass die Ausführung des Preisindexers zu viel Zeit in Anspruch nimmt.
* **ACSD-52287** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt das Problem mit dem falschen Bestellstatus im archivierten Bestellraster, wenn die asynchrone Rasterindizierung aktiviert ist.
* **ACSD-52929** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem mit redundanten Anfragen zur Neuindizierung von standardmäßigen Quellelementen, wenn der Inventar-Indexer im asynchronen Modus konfiguriert ist.
* **ACSD-53824** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, bei dem `UpdateMultiselectAttributesBackendTypes` Migrationsdaten-Patch während der `setup:upgrade` das Größenlimit für Datenbanktransaktionen überschritten hat.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass Caches und Indizes aktualisiert werden, selbst wenn von der REST-API keine Aktualisierungen an `Inventory_source` Elementen vorgenommen werden.
* **ACSD-51884** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, bei dem der Cache-Pfad für das Produktbild nach Ausführung des Befehls „resize“ falsch wird.
* **ACSD-53628** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, bei dem im CSV-Kundenauftragsbericht falsche Sonderzeichen angezeigt wurden.
* **ACSD-53148** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, bei dem zwei parallele Anfragen in GraphQL zum Hinzufügen desselben konfigurierbaren Produkts zum Warenkorb dazu führten, dass sich zwei separate Artikel im Warenkorb mit derselben Produkt-SKU befanden.
* **ACSD-52606** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt das Problem, dass die Fehlermeldung *Ihre Bestellung ist nicht abholbereit* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.
* **ACSD-51574** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass das Bild im Frontend nicht aktualisiert wird, nachdem es durch ein anderes Bild mit demselben Namen ersetzt wurde.
* **ACSD-53728** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass die Fertigstellung des EAV-Indexers des Produkts länger dauert.
* **ACSD-53979** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt das JS-Problem, das auf der Homepage auftritt, wenn die Begrüßungsnachricht ein einfaches Anführungszeichen enthält.
* **ACSD-52085** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass ein konfigurierbares Produkt mit einem Sonderpreis nicht im Karussell des Produkts sichtbar war.
* **ACSD-53795** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem mit dem ungültigen Datentyp in `indexer_update_all_views` Cron-Auftrag.
* **ACSD-52143** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass benutzerdefinierte Optionen nach dem Produktimport entfernt wurden.
* **ACSD-53750** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt den Fehler *Rohrbruch oder geschlossene Verbindung* während der Neuindizierung von Multithread-`catalog_product_price`.
* **ACSD-49843** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Behebt das Problem, dass der Link beim Produkt-Download nicht verfügbar ist, nachdem der bestellte Artikel mit der Online-Zahlungsmethode automatisch fakturiert wurde, wobei die Einstellung **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** aktiviert ist.
* **ACSD-47054** (für Adobe Commerce >=2.4.2 &lt;2.4.6) - Behebt das Problem, dass die Vorschau-Neuindizierung die Neuindizierung für alle Stores ausführt, was zu Langsamkeit führt.
* Es wurden neue Versionen für ACSD-46541, ACSD-47079 hinzugefügt.
* ACSD-49970-v3 durch ACSD-54095 ersetzt.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt; 2.4.6) - Behebt das Problem, dass der Inventar-Indexer alle Caches im Zeitplanmodus aktualisiert.
* **ACSD-50887** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wird das Problem behoben, bei dem die Produktattribut-Eigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* gesetzt werden kann, ohne dass die *[!UICONTROL Use in search]* auf *Ja* gesetzt ist.
* **ACSD-51846** (für Adobe Commerce und Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Behebt das *Interner Fehler*-Problem, das auftritt, weil nicht alle Ebenen der REST-API-Payload validiert werden.
* **ACSD-52906** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass das X-Magento-Vary-Cookie für angemeldete Kunden, die zum selben Kundensegment gehören, falsch gesetzt wird, was bei einigen Seiten zu einer fehlerhaften Zwischenspeicherung führt.
* **ACSD-52736** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebt das Problem, dass eine *Warenkorb-*, die Anforderungen für konfigurierbare Produktmengen enthält, nicht wie erwartet funktioniert.
* **ACSD-47875** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass Admin-Benutzer bei der Bestandsverwaltung ein Produkt nicht aus dem Admin-Bereich für einen bestimmten Store-Ansichtsumfang zu einem Warenkorb hinzufügen können.
* **ACSD-53176** (für Adobe Commerce >=2.3.7 &lt;2.4.5) - Es wurde das Problem behoben, bei dem *Zugehörige Produktregel* mit *eine der*-Bedingung nicht mit Produkten übereinstimmt.
* **ACSD-51666** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt den Fehler *Die Sitzung ist abgelaufen, bitte erneut anmelden.*, die nach dem Anmeldeversuch eines Kunden eintreten.
* Es wurden neue Versionen für MDVA-39305-v2 hinzugefügt.
* Die Anforderungen für ACSD-19640 wurden aktualisiert.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wird das Problem behoben, bei dem die standardmäßige Versandadresse im Checkout-Versandschritt automatisch mit einer zuvor ausgewählten Abholadresse im Geschäft ausgefüllt wird.
* **ACSD-52041** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, bei dem die Fehlermeldung: *[ERROR] [!DNL Page Builder] 5 Sekunden lang gerendert wurde, ohne Sperren freizugeben.* wird im Chrome-Browser angezeigt, wenn mit [!DNL Page Builder] bearbeitete Inhalte gespeichert werden.
* **ACSD-52095** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Es wurde das Problem behoben, bei dem der `manage_stock`-Wert in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt wurde.
* **ACSD-51358** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Das Entfernen eines geplanten Updates ohne Enddatum behebt das Problem, dass andere geplante Updates für dieselbe Entität entfernt werden.
* **ACSD-48070** (für Adobe Commerce Trigger >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, bei dem die Bearbeitung eines geplanten Updates zu einer Ausnahme führte.
* **ACSD-51890** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wurde das Problem behoben, dass die [!UICONTROL Submit review]-Schaltfläche mehrmals ohne [!DNL Google reCAPTCHA] v3-Validierung angeklickt werden kann.
* **ACSD-51984** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, dass nicht aktivierte *[!UICONTROL Use Default Value]*- und *[!UICONTROL non-default product field]* für die zweite Website-, Store- und Store-Ansicht nicht gespeichert werden.
* **ACSD-52398** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *Die angeforderte Menge ist nicht verfügbar* der beim Versuch auftritt, die Menge eines gebündelten Produkts im Warenkorb in der Storefront zu aktualisieren.
* **ACSD-52786** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wird das Problem behoben, bei dem eine Katalogregelbedingung (*SKU)* alle Produkte gilt, die mit der angegebenen SKU beginnen.
* **ACSD-52921** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, bei dem ein interner Fehler auftritt, wenn Warenkorbdetails von GraphQL angefordert werden, wenn sich ein nicht vorrätiges konfigurierbares Produkt im Warenkorb befindet.
* **ACSD-51683** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass eine anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
* **ACSD-52133** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Kundenkonto nach einem Upgrade nicht gespeichert werden konnte.
* **ACSD-52202** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass die verkaufsfähige Menge des Standardaktienbestands fälschlicherweise auf 0 geändert wird, wenn ein nicht standardmäßiger Bestand bei Auftragserfüllung auf 0 Menge geändert wird.
* **ACSD-51265** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem mit `catalog_product_price` Neuindizierungsleistung, wenn das System zu viele gebündelte Produkte enthält.
* **ACSD-52831** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass Kunden bei aktiviertem [!DNL Google reCAPTCHA v3 Invisible] keine verhandelbaren Angebotsbestellungen aufgeben können.
* **ACSD-51845** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wird das Problem behoben, dass nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen nicht über die asynchrone Massen-REST-API aktualisiert werden können.
* **ACSD-52815** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass die Eingabe für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für einen Standardbestand.
* **ACSD-51149** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass durch den geplanten ImportExport mit aktivierten Katalogberechtigungen Indexer ungültig gemacht und dann Cron-basierte Cache-Leerungen zwischengespeichert werden.
* **ACSD-50815** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wurde das Problem behoben, dass die Dezimalmenge für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann.
* Aktualisierte Versionen für ACSD-47803.
* Titel für ACSD-51892 aktualisiert.
* Aktualisierung von ACSD-51379.
* Aktualisierung von ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Administrator-Benutzer nicht ordnungsgemäß umgeleitet wird, nachdem er eine Store-Ansicht ausgewählt hatte, als er eine neue Bestellung in Admin erstellte.
* **ACSD-50813** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, bei dem der Administrator nicht in der Lage war, gebündelte Produkte mit einem Schrägstrich in der SKU mit der [!UICONTROL Add Products by SKU] Funktion zur Admin-Bestellung hinzuzufügen.
* **ACSD-51630** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wurde das Problem behoben, dass das Herunterladen von Administratorseiten durch eine große Anzahl von Systemmeldungen verlangsamt wurde.
* **ACSD-51853** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.7) - Es wurde das Problem behoben, dass kopierte Textstile bei Verwendung des [!UICONTROL Page Builder] nicht angewendet wurden.
* **ACSD-52160** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde das Problem behoben, bei dem das Produktvalidierungsergebnis für die Warenkorbpreisregel basierend auf der Regelbedingung „Wenn ein Artikel im Warenkorb GEFUNDEN/NICHT GEFUNDEN wurde und alle/eine dieser Bedingungen erfüllt ist“ nicht ordnungsgemäß bewertet wurde.
* **ACSD-51636** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass der Unternehmensadministrator bzw. die Unternehmensadministratorin keine neuen Benutzenden aus dem Abschnitt Kundenkonto hinzufügen kann, obwohl er bzw. sie über alle erforderlichen Rollen und Berechtigungen verfügt.
* **ACSD-51739** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebt das Problem, dass ein Fehler zurückgegeben wird, wenn der `structure_id` in einer CompanyTeam GraphQL-Anfrage angefordert wird.
* **ACSD-51857** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wurde das Problem behoben, bei dem die langsame Leistung des `aggregate_sales_report_bestsellers_data` Cron-Berichts bei großen Sales_Order- und `sales_order_item`-Datenbanktabellen auf die Art und Weise zurückzuführen war, wie die Hauptdatenabfrage geschrieben wurde.
* **ACSD-48448** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass während der Auftragsstornierungen ein Race-Condition-Problem auftritt, das zu einem doppelten Eintrag in der `inventory_reservation` führt.
* **ACSD-52689** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.6) - Es wurde das Problem behoben, dass Bilder nicht mit der REST-API in den Amazon S3-Speicher hochgeladen werden können.
* **B2B-2674** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Hinzufügen einer Caching-Funktion zur GraphQL-Abfrage 1customAttributeMetadata1.
* Es wurden neue Versionen für ACSD-44938 hinzugefügt.
* Es wurden Anforderungen für ACSD-46988 hinzugefügt.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5) - Behebt den Datenbankrollback-Befehl für einen Fall, in dem der DB-Dump Trigger und einen SQL-Befehl *Trennzeichen* enthält.
* **ACSD-50512** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebt den *Fehler: Der herunterladbare Link ist nicht mit dem Produkt verbunden. Überprüfen Sie den Link und versuchen Sie es erneut.* Fehler, der beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update auftritt.
* **ACSD-50949** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass der Preisfilter in der erweiterten Suche keine ordnungsgemäßen Ergebnisse zurückgibt, wenn er zusammen mit dem SKU-Filter verwendet wird.
* **ACSD-51645** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt den Fehler, der beim Speichern einer neuen Warenkorb-Preisregel ausgelöst wird, wenn die `Magento_OfflineShipping` deaktiviert ist.
* **ACSD-50895** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass [!DNL Google Analytics] 3 GTM-Tags nicht ausgelöst werden, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist.
* **ACSD-51102** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Es wird das Problem behoben, dass eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht korrekt indiziert wird, wenn die Regel durch ein geplantes Update aktiviert wird.
* **ACSD-50368** (für Adobe Commerce und Magento Open Source >= 2.4.3 &lt;2.4.5) - Behebt das Problem, dass die `group_id` des Kunden ignoriert wird, wenn ein Kunde über die Async REST-API oder die Async Bulk REST-API erstellt wird.
* **ACSD-51497** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Kunde eine Katalogseite nicht nach benutzerdefiniertem Attribut des Dropdown-Typs sortieren kann.
* **ACSD-51408** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt; 2.4.7) - Behebt das Problem, dass der Bestellartikelstatus fälschlicherweise auf *[!UICONTROL Backordered]* gesetzt wurde.
* **ACSD-51735** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebt das Problem, dass der Bestellartikelstatus fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt wird, wenn der Produktbestand *0*.
* **ACSD-51792** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebt das Problem, dass eine Seite das Impression-Ereignis nicht hat, wenn [!DNL Google Tag Manager] 4 aktiviert ist.
* **ACSD-51471** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Es wird das Problem behoben, dass ein Admin-Benutzer kein geplantes Update für ein gebündeltes Produkt speichern kann, das ein einfaches Produkt verwendet, das selbst ein geplantes Update hat.
* **ACSD-51700** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt den Fehler, der beim Wechseln der Store-Ansichten auf einer herunterladbaren Produktbearbeitungsseite in Admin passiert.
* **ACSD-51120** (für Adobe Commerce >=2.3.7 &lt;2.4.3) - Es wird das Problem behoben, dass der Cache für GraphQL GET-Anfragen für CMS-Seiten mit CMS-Blöcken, die über ein Staging-Update aktualisiert werden, nicht gelöscht wird.
* **ACSD-51240** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass die hochgeladene Datei fehlt, wenn die Registrierung über das Unternehmensregistrierungsformular erfolgt.
* **ACSD-51907** (für Adobe Commerce >=2.4.2 &lt;2.4.3) - Behebt das Problem, dass ein Benutzer mit eingeschränktem Administratorzugriff keine Gutschrift mit einer Offline-Rückerstattung erstellen kann.
* **ACSD-52148** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebt das Problem, dass die [!DNL Google V3 reCAPTCHA] Admin-Anmeldung gelegentlich fehlschlägt.
* **ACSD-51431** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, dass ein Indexerstatus *funktioniert* auch dann nicht auftritt, wenn im Änderungsprotokoll keine neuen Einträge vorhanden sind.
* **ACSD-51892** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt das Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden.
* Veraltete ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, bei dem der Administrator aufgrund [!UICONTROL Page Builder's] mehrerer Fehler ein Produkt ohne Inhaltsberechtigungen nicht speichern konnte.
* **ACSD-51305** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wird das Problem behoben, dass nicht vorrätige konfigurierbare untergeordnete Produkte in der GraphQL-Antwort nicht verfügbar sind.
* **ACSD-50621** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, dass [!UICONTROL Tier Prices] für verschiedene Websites im freigegebenen Katalog nicht angezeigt werden, wenn versucht wird, sie in einer Umgebung mit mehreren Websites zu bearbeiten.
* **ACSD-51041** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Verbessert die Leistung des Preisindexers.
* **ACSD-51379** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, dass Änderungen am Seitentext-Inhalt über [!UICONTROL Page Builder] nicht gespeichert werden.
* **ACSD-49480** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass nur eine Warenkorb-Preisregel auf den Warenkorb angewendet wird.
* **ACSD-51230** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass das Geschenkkartenkonto gelöscht wird, wenn eine teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird.
* **ACSD-51238** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt das Problem, dass die Inventarquelle entfernt wird, wenn konfigurierbare Produkte aktualisiert und der Preis bearbeitet wird.
* **ACSD-50794** (für Adobe Commerce >=2.4.1 &lt;2.4.7) - Es wird das Problem behoben, bei dem die Details zur Geschenknachricht oder Geschenkverpackung in der Datenbank nicht aktualisiert werden, wenn sie über GraphQL entfernt wird.
* **ACSD-51528** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass die Spalte *x_forwarded_for* in der Tabelle *sales_order* Nullwerte enthält.
* **ACSD-50849** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Es wird das Problem behoben, dass das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches dazu führt, dass die Positionen und Auswahlen der vorhandenen Produkte nicht übereinstimmen.
* **ACSD-51294** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass GTM/GA-Preis, -Menge, -Steuer, -Versand und -Umsatz als Zeichenfolge an [!DNL Google Analytics] und GTM gesendet werden.
* **ACSD-51204** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass ein vollständig verkauftes Produkt nach der Erstellung einer Gutschrift nicht wieder auf Lager ist.
* **ACSD-51291** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Es wurde das Problem behoben, durch das Administratoren mit eingeschränktem Zugriff auf eine Website dem Produkt Bilder/Videos hinzufügen können, die mehreren Websites zugewiesen wurden.
* Es wurden neue Versionen für ACSD-50336 hinzugefügt.
* Patches von ACSD-49970 ersetzt.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Behebt das Problem, dass reCAPTCHA v2 nach dem Senden einer fehlgeschlagenen Zahlung nicht neu geladen wird.
* **ACSD-50817** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Optimiert die `sales_clean_quotes` von Cron-Aufträgen für eine schnellere Ausführung.
* **ACSD-49392** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Behebt das Problem, dass sich der Bestellstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in „Geschlossen“ ändert.
* **ACSD-51036** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Es wird das Problem behoben, bei dem Racebedingungen während gleichzeitiger REST-API-Aufrufe zu einer Überschreibungen der Versandstatusinformationen in der [!UICONTROL Items Ordered] führen.
* **ACSD-50858** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Verbessert die Leistung beim Laden des Bannerinhalts.
* Es wurden neue Versionen für MDVA-39305-v2, ACSD-45169 hinzugefügt.
* Die Patches ACSD-50260-v2 wurden aktualisiert.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (für Adobe Commerce und Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Es wurde das Problem behoben, dass keine E-Mails zu Produktalarmen gesendet wurden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wurde.
* **ACSD-50367** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, dass der Export von Kundenadressen nicht funktioniert, wenn ein Attribut für eine Kundenadresse mit mehreren Auswahlen ohne Werte erstellt wird.
* **ACSD-49877** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass die automatische Videowiedergabe auf mobilen [!DNL Safari] nicht funktioniert, wenn das Video direkt mit einer Remote-Videodatei und nicht mit einem Streaming-Service verknüpft ist.
* **ACSD-50165** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *Die Datei kann nicht gelöscht werden. Warnung!Verknüpfung aufheben: Keine solche Datei oder*, wenn der JS/CSS-Cache vom Administrator geleert wird.
* **ACSD-49737** (für Adobe Commerce und Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Behebt das Problem, dass ein Coupon nach einer fehlgeschlagenen Kartenzahlung fälschlicherweise als verwendet gekennzeichnet wird.
* **ACSD-50814** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Administrator bzw. eine Administratorin keine Gutschrift erstellen konnte.
* **ACSD-50116** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Admin-Benutzer keine URL-Umschreibung für Unterkategorien der Ebene 3 oder darunter erstellen konnte.
* **ACSD-49513** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5) - Behebt das Problem, dass die Remote-Speichersynchronisierung aufgrund von 0-Byte-Dateien fehlschlägt.
* **ACSD-46683** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass der Versandpreis &quot;*noch nicht berechnet“*.
* **ACSD-49129** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Es wurde das Problem behoben, bei dem das *[!UICONTROL content]*-Attribut (base64-Bild-Code) nicht in `rest/V1/products/sku/media` Produktmedien-API-Antworten zurückgegeben wird.
* **ACSD-50276** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Es wird das Problem behoben, dass das Kundenregistrierungsformular in der Storefront nicht funktioniert, wenn ein Kundenattribut mit mehreren Auswahlen erstellt wird.
* **ACSD-50527** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt den Fehler, der beim Speichern einer Seite mit einem leeren dynamischen Block auftritt.
* **ACSD-49973** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Verbessert die Leistung beim Abrufen von gebündelten Produkten über GraphQL.
* **ACSD-51114** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass ein zufälliges Produkt aus großen Katalogen verschwindet, wenn die asynchrone Indizierung aktiviert ist. Verbessert die Leistung der asynchronen Neuindizierung für große Kataloge.
* **B2B-2598** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Hinzufügen einer Caching-Funktion zu den Abfragen von [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] und [!UICONTROL storeConfig] GraphQL.
* Es wurden neue Versionen für MDVA-42806, ACSD-48627, ACSD-46815 hinzugefügt.
* Die Patch-Metadaten für ACSD-49773, ACSD-47179, ACSD-48300 wurden aktualisiert.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Es wurde das Problem behoben, dass eine Abholbereitschafts-E-Mail von der API gesendet wurde, wenn die Bestellung nicht zur Abholung bereit ist.
* **ACSD-49822** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass Aktualisierungen auf der [!UICONTROL Requisition List] nicht auf der [!UICONTROL Print Requisition List] angezeigt wurden.
* **ACSD-48771** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem beim Aktualisieren des Inhaltstyps für Spaltenblöcke aus älteren [!DNL Page Builder]-Versionen behoben.
* **ACSD-49464** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass Rechnungen, Sendungen und Gutschriften nicht aus dem Archiv zurückverschoben werden, wenn die orderId unterschiedlich ist.
* **ACSD-49773** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebt das Problem, dass der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird.
* **ACSD-49748** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass keine Einladungen gesendet werden konnten.
* **ACSD-49502** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass der herunterladbare Link nach der Anwendung einer Staging-Aktualisierung auf das herunterladbare Produkt nicht ordnungsgemäß aktualisiert wird.
* **ACSD-49527** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass in Unternehmensrollen von GraphQL die Paginierung nicht korrekt angezeigt wird.
* **ACSD-49706** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, dass der Standardwert für ein visuelles Musterattribut gespeichert wird, wenn kein Wert ausgewählt ist.
* **ACSD-49835** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wird das Problem behoben, bei dem der Wert des Kontrollkästchens Standard verwenden auf Store-Ebene für ein Attribut mit Mehrfachauswahl nicht korrekt gespeichert wurde.
* **ACSD-49898** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass das Produktraster eine Ausnahme auslöst, wenn ein gebündeltes Produkt einen Sonderpreis von mehr als 1.000 aufweist.
* **ACSD-50234** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.5) - Behebt das Problem mit dem falschen Kundennamen in der Bestätigungs-E-Mail, wenn eine Bestellung bei [!DNL PayPal] aufgegeben wird.
* **ACSD-49960** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass das Filtern nach Datum für das Kundenauftragsraster nicht funktionierte.
* **ACSD-49849** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Es wurde das Problem behoben, bei dem Kunden-E-Mails durch [!DNL PayPal] E-Mail ersetzt wurden, wenn eine Bestellung über GraphQL bei [!DNL PayPal Express] aufgegeben wurde.
* **ACSD-49839** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass Shared Catalog Pricing and Structure einen Fehler in Admin auslöst, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.
* **ACSD-49970** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt die fehlerhafte Behandlung von GraphQL-Fehlern, wenn [!DNL New Relic] Berichte aktiviert sind.
* **ACSD-50260** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Es wurde das Problem behoben, dass GraphQL-Produktsuchergebnisse auf 10.000 Ergebnisse beschränkt waren.
* **ACSD-48813** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt das Problem, dass die Suche basierend auf der Suchgewichtung der Attribute keine relevanten Ergebnisse anzeigt.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.3) - Es wird das Problem behoben, bei dem eine auf der Grundlage des Attributs „Ja/Nein“ erstellte Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt.
* **ACSD-47704** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass das gebündelte Produkt nur den Preis der vorrätigen Produkte anzeigt.
* **ACSD-49370** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, bei dem das Produktattribut *Datum/Uhrzeit* im GraphQL-Schema einen *FilterMatchTypeInput*-Typ aufweist.
* **ACSD-48807** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.7) - Es wurde das Problem behoben, dass Kundenproduktbewertungen nicht nach Storeview über GraphQL gefiltert werden.
* **ACSD-49433** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt das Problem, bei dem der Standardbetrag als Zwischensumme im Warenkorb für Geschenkkarten mit einem offenen Betrag angezeigt wird.
* **ACSD-48866** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass beim Anfordern von RSS-Feeds für Kategorien ein Fehler auftritt.
* **ACSD-48784** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass die Segmentpreise für Kunden fälschlicherweise zwischen Kundengruppen zwischengespeichert werden.
* **ACSD-48857** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wurde das Problem behoben, dass Benutzende nach der Bearbeitung mit Page Builder keine Änderungen speichern konnten.
* **ACSD-49065** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass Angebotselemente im Admin nicht angezeigt werden, wenn sie nur dem benutzerdefinierten Lager zugewiesen waren.
* **ACSD-49179** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebt das Problem, dass im Bestellbericht falsche Beträge angezeigt werden, wenn für verschiedene Stores unterschiedliche Währungen verwendet werden.
* **ACSD-49286** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wird das Problem behoben, dass ein Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.
* **ACSD-49574** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Fügt Funktionen hinzu, um Produktaktualisierungen von Geschenkgutscheinen in einem Warenkorb über GraphQL zu unterstützen.
* Aktualisierter Patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (für Adobe Commerce >=2.4.1 &lt;2.4.7) - Behebt das Problem, dass bei einer Bestellung mit einem verhandelbaren Angebot die standardmäßige Versandadresse anstelle einer neuen verwendet wird.
* **ACSD-48059** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass Händler das &quot;[!UICONTROL Match product by rule]&quot; in der Kategorie nicht speichern konnten.
* **ACSD-48216** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Behebt das Problem, dass die [!UICONTROL AUTO_INCREMENT] der [!UICONTROL inventory_source_item]-Tabelle beim [!UICONTROL UPDATE]-Vorgang zunimmt.
* **ACSD-47908** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Behebt den Fehler „Ein Wert kleiner oder gleich 0 wird erwartet“ bei der Auswahl der Quelle und Menge im Versandschritt während des Checkouts.
* **ACSD-49497** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebt das Problem, dass eine Bestellung nach dem Versand im Verarbeitungsstatus verbleibt und eine Teilrückerstattung angewendet wird.
* **ACSD-48694** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Es wurde das Problem behoben, bei dem der Fehler „Ungültige Statusänderung angefordert“ einen Kunden daran hinderte, eine Bestellung aufzugeben.
* **ACSD-49013** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Es wird das Problem behoben, dass E-Mail-Bestätigungen beim Erstellen von Kunden, die die Bulk-API verwenden, nicht in das Gebietsschema der Website übersetzt werden.
* **ACSD-48164** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wurde das Problem behoben, dass ein Admin mit Zugriffsbeschränkung einen Wert auf Website-Ebene nicht speichern konnte.
* **ACSD-48404** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Es wurde das Problem behoben, bei dem „Paginierung der Kategorie erinnern = Ja“ einen Fehler verursachte, wenn die Zurück-Schaltfläche des Browsers gedrückt wurde.
* **ACSD-48634** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt JS-Fehler auf einer Staging-Aktualisierungsseite, wenn &quot;[!UICONTROL Google Analytics Content Experiments]&quot; aktiviert ist.
* **ACSD-49042** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Es wurde das Problem behoben, dass ein Produkt mit unendlicher Rückbestellung nicht über die Storefront bestellt werden kann.
* Aktualisierte Patches: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (für Adobe Commerce und Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Es wurde das Problem behoben, bei dem Preisabfallbenachrichtigungen aufgrund des Caching auf Anwendungsebene nicht immer gesendet werden.
* **ACSD-48661** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem, dass bei einem Kreditlimit des Unternehmens von mehr als 999 das Kommatrennzeichen das Speichern des Unternehmens aufgrund eines Validierungsfehlers verhindert.
* **ACSD-48773** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Es wurde das Problem behoben, dass die E-Mail-Vorlage für Belohnungspunkte aus dem falschen Speicher entnommen wurde.
* **ACSD-48587** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Es wird das Problem behoben, bei dem HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte verhindern, dass übereinstimmende Produkte angezeigt werden.
* **ACSD-48212** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Es wurde das Problem behoben, bei dem der Produktimport das Produkt der falschen Quelle zuordnet.
* **ACSD-47988** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Es wurde das Problem behoben, dass durch den Produktexport HTML-Tags aus der Page Builder-Produktbeschreibung gekürzt wurden.
* **ACSD-48366** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass das Produktbild nicht in der E-Mail-Vorlage „Zurück zur Lager“ angezeigt wird.
* **ACSD-48417** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebt das Problem, dass ein SQL-Fehler auftritt, nachdem eine Zeitplanänderung für ein Produkt erstellt und ein anderes Produkt gespeichert wurde.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wurde das Problem behoben, dass die Neuindizierung des Produktpreises nicht funktioniert, wenn das Bundle-Produkt keiner Website zugewiesen ist.
* **ACSD-48262** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebt das Problem, dass Produkte im Frontend nicht sichtbar sind, wenn die Einstellung „Alle Produkte pro Seite zulassen“ auf „Ja“ gesetzt ist.
* **ACSD-48293** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4) - Behebt das Problem, dass die zusammengesetzten Produkte nicht vorrätig sind, wenn die untergeordneten Produkte, die ausverkauft waren, wieder auf Lager sind.
* **ACSD-47520** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass Kunden bei der Erstellung einer Gutschrift Prämienpunkte verlieren.
* **ACSD-48044** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Es wurde das Problem behoben, dass das Anwenden mehrerer Geschenkgutscheine auf eine Bestellung mit Mehrfachversand die Bestellung verhindert.
* **ACSD-48300** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass keine Rückgabe erstellt werden kann, wenn das konfigurierbare Produkt entfernt wurde.
* **ACSD-47910** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem fehlender Bestellungen, Rechnungen, Lieferungen und Gutschriften in den entsprechenden Entitätsrastern.
* **ACSD-47292** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass nicht vorrätige gebündelte Produkte in der GraphQL-Antwort nicht verfügbar sind, wenn „Nicht vorrätige Produkte anzeigen“ auf „Ja“ gesetzt ist.
* **ACSD-48234** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wird das Problem behoben, bei dem das Katalogsuchergebnis eine falsche Anzahl von Kategorieelementen anzeigt, wenn die Option „Nicht vorrätig anzeigen“ aktiviert ist.
* **ACSD-48313** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5) - Es wird das Problem behoben, dass die Spalte „Configurable_variations“ nicht geparst wird, wenn der Attributwert ein Komma enthält. Derselbe Parsing-Algorithmus wird für „additional_attributes“ verwendet.
* **ACSD-48627** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wird das Problem behoben, bei dem das nicht vorrätige konfigurierbare Produkt einen Fehler verursacht, wenn eine GraphQL-Anfrage gesendet wird, um Warenkorbdetails abzurufen.
* Aktualisierter Patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Es wird das Problem behoben, dass SEO-freundliche URLs nicht für Produkte generiert werden, bei denen *url_key*-Attribute auf Store-Ansichtsebene überschrieben wurden.
* **ACSD-46865** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Es wurde das Problem behoben, dass das Raster „Sendung“ und „Gutschrift“ nicht ausgefüllt wird, wenn die asynchrone Indizierung aktiviert ist.
* **ACSD-47004** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Es wurde das Problem behoben, dass keine MwSt. auf eine Rechnungsadresse ohne MwSt.-Kennung angewendet wird.
* **ACSD-47803** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, bei dem nicht vorrätige konfigurierbare Produktmuster als verfügbar angezeigt wurden.
* **ACSD-47137** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Verbessert die Ladegeschwindigkeit der Bildergalerie, wenn der Pub/Media-Ordner sehr groß ist.
* **ACSD-46770** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass E-Mails zu Admin-Bestellungen gesendet wurden, selbst wenn die E-*-Bestellbestätigung* deaktiviert war.
* **ACSD-47955** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem, dass GraphQL den Warenkorbabschlag nicht korrekt anzeigt.
* **ACSD-46617** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebt das Problem, dass die Schaltfläche *Weiter zur Kasse* ausgegraut ist, selbst wenn die Zwischensumme größer als der konfigurierte *Mindestbestellbetrag* ist.
* **ACSD-47079** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebt das Problem, dass der Lagerstatus von zusammengesetzten Produkten (gebündelt, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus von Unterprodukten über REST API POST /rest/V1/inventory/source-items ändert.
* **ACSD-47336** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fehlerbehebungen (*ist schiefgelaufen.* beim Verwerfen von Benachrichtigungen in Commerce Admin.
* **ACSD-47559** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass der Bereich E-Mail-Vorschau-Vorlage nicht vollständig sichtbar war.
* **ACSD-47920** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass Bestellungen über die REST-API auch dann als Gastbenutzer aufgegeben werden können, wenn *Gast-Checkout zulassen* deaktiviert ist.
* Patches ersetzt: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass ein Administrator mit eingeschränktem Zugriff auf einen bestimmten Bereich keine Produktbewertungen löschen kann.
* **ACSD-47107** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5) - Es wurde das Problem behoben, bei dem der Rabatt für Katalogpreisregeln auf benutzerdefinierte Produktoptionen angewendet wurde.
* **ACSD-47232** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass Coupons mit Bedingungen für die Gesamtgewichtung nicht in der Admin angewendet werden können.
* **ACSD-46519** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.6) - Es wird das Problem behoben, bei dem die GraphQL categoryList-Anfrage eine falsche product_count für eine Ankerkategorie zurückgibt.
* **ACSD-47027** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebt eine langsame UpdateCompanyRole-GraphQL-Anfrage.
* **ACSD-47666** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass die Filterfunktion im Raster „Admin“ > „System“ > „Berechtigungen“ > „Benutzerrollen“ > „Rolle“ > „Benutzer“ nicht funktioniert.
* **ACSD-47497** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass die Registerkarte Services in der Konfiguration unter dem Administrator nicht angezeigt wurde.
* Aktualisierter Patch: ACSD-47743.
* Patches ersetzt: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3) - Behebt den Fehler _Zugriff auf Array-Offset beim Wert vom Typ bool_ beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4.
* **ACSD-47332** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebt das Problem, dass cron mit einem Fehler fehlschlägt, der nur gemeldet wird, wenn zwischen 00:00 und 00::59 UTC ausgeführt wird.
* **ACSD-47280** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass das Deaktivieren der Funktion für freigegebene Kataloge in einem bestimmten Bereich nicht ordnungsgemäß funktioniert.
* **ACSD-47106** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Es wurde das Problem behoben, dass ein Wert auf einer Unternehmenserstellungsseite nicht in einem neuen benutzerdefinierten Attribut gespeichert werden kann.
* Aktualisierter Patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Es wird das Problem behoben, bei dem Benutzende beim Zuweisen einer großen Anzahl von Produktquellen einen Fehler erhalten.
* **ACSD-46856** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Verbessert die Leistungsaktualisierung der Stufenpreise über „System“ > „Konfiguration“ > „Importieren“ > „Erweiterte Preise“.
* **ACSD-46541** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Es wurde das Problem behoben, dass ein Admin-Benutzer keine Gutschrift erstellen kann, wenn ein Auftragselement gelöscht wird.
* **ACSD-46581** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebt das Problem, dass die geschätzte Steuersumme nicht aktualisiert wird, nachdem ein Land im Warenkorb ausgewählt wurde.
* **ACSD-46618** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebt das Problem, dass das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt.
* **ACSD-46674** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Es wurde das Problem behoben, dass benutzerdefinierte Optionen eines Bildtyps in Kunden-E-Mails als HTML angezeigt wurden.
* **ACSD-46988** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Es wurde das Problem behoben, bei dem die GraphQL-API-Anfrage „currency“ NULL-Werte für eine benutzerdefinierte Währung zurückgibt.
* **ACSD-47076** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5) - Behebt das Problem, dass Vimeo-Videos nicht in der Storefront abgespielt werden können.
* **ACSD-45071** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4) - Es wird das Problem behoben, bei dem die Standardquelle dem Produkt während des Imports hinzugefügt wird.
* **AC-3023** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Aktualisieren des DHL-Schemas auf die neueste Version 10.0.
* Aktualisierte Patches: MDVA-42584.
* Patches ersetzt: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebt das Problem, dass ein Benutzer bei Rückerstattung über das Store-Guthaben einen falschen Bestellstatus erhält.
* **ACSD-46703** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6*) - Behebt das Problem, dass es nicht möglich ist, benutzerdefinierte Optionen per Drag-and-Drop auf eine Produktbearbeitungsseite zu ziehen.
* **ACSD-44851** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6*) - Es wurde das Problem behoben, dass eine Kategorie mit Unterkategorien nicht geöffnet oder erweitert werden kann.
* **ACSD-46815** (*für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6*) - Es wurde das Problem behoben, dass die Kategoriestrukturanforderung auf 20 Kategorien beschränkt war.
* **ACSD-45675** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6*) - Es wurde das Problem behoben, bei dem der Produktexport Kategorienamen aus dem *Standard-Store-Ansicht*-Bereich verwendet.
* **ACSD-46869** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6*) - Behebt das Problem, dass ein konfigurierbares Produkt in einem Warenkorb nicht über eine *PUT REST API* Anfrage aktualisiert wird, ohne die Produktmenge zu ändern.
* **MDVA-42768-V2** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Es wurde das Problem behoben, bei dem das konfigurierbare Produkt den regulären Preis als *0* anzeigt, wenn *Nicht vorrätig anzeigen* *Ja* ist.
* Aktualisierte Patches: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Veralteter Patch: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Es wurde das Problem behoben, dass die Kategoriestrukturanforderung auf 20 Kategorien beschränkt war.
* **ACSD-45781** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.2*) - Es wurde das Problem behoben, dass das Suchfeld „Storefront“ auf Mobilgeräten nicht angezeigt wird.
* **ACSD-46192** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;2.4.5*) - Behebt das Problem bei der Verwendung des `async/bulk/V1/configurable-products/bySku/options`-Endpunkts.
* **ACSD-46404** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Es wurde das Problem behoben, dass sich ein Admin-Benutzer nach dem Upgrade auf 2.4.4 nicht anmelden konnte.
* Aktualisierte Patches: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wird das Problem behoben, bei dem eine GraphQL-Produktmutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind.
* **ACSD-46146** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.6*) - Es wurde das Problem behoben, dass zwei E-Mails zur Bestellbestätigung versendet wurden, nachdem eine Bestellung vom Administrator aufgegeben wurde.
* **ACSD-45255** (*für Adobe Commerce >=2.4.3 &lt;2.4.6*) - Behebt eine Ausnahme auf der Seite „Low Stock Report“ für einen eingeschränkten Admin-Benutzer.
* **ACSD-45488** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6*) - Es wird das Problem behoben, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch an „Auf Lager“ zurückgegeben wird.
* **ACSD-45754** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.6*) - Es wird das Problem behoben, bei dem Belohnungspunkte nicht hinzugefügt werden, nachdem ein Coupon auf den Warenkorb angewendet wurde.
* **ACSD-45849** (*für Adobe Commerce >=2.4.3 &lt;2.4.4*) - Behebt das Problem, dass Videometadaten nach einer Staging-Aktualisierung verloren gehen.
* **ACSD-45257** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.4*) - Behebt das Problem, dass GraphQL den Warenkorbabschlag nicht korrekt anzeigt.
* **ACSD-44938** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Es wurde das Problem behoben, dass `VAT_ID` in einer GraphQL-Anfrage für einen Gastbenutzer nicht angewendet werden können.
* Aktualisierte Patches: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.4*) - Behebt das Problem, dass die Lagermenge für ein virtuelles Produkt nach der Erstellung einer Gutschrift falsch berechnet wird.
* **ACSD-43887** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, dass auf der Kassenzahlungsseite falsche Details angezeigt werden, wenn Bestellungen für Unternehmen aktiviert sind.
* **ACSD-45143** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem die `setShippingAddressesOnCart`-Mutation das Festlegen des numerischen Regionen-Codes als *Region* nicht zulässt.
* **ACSD-44591** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.6*) - Fehlerbehebung, die auftritt, wenn eine Bestellung ohne CAPTCHA-Bestätigung aufgegeben wird.
* **ACSD-45520** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.6*) - Es wird das Problem behoben, bei dem Farbfeldoptionen auf der Produktdetailseite nicht vorausgewählt sind, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet.
* **ACSD-45169** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.6*) - Behebt das Problem, dass [!DNL Visual Merchandiser] nach einer Staging-Aktualisierung den richtigen Lagerbestand und Preis für ein konfigurierbares Produkt nicht anzeigt.
* **ACSD-45424** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.6*) - Behebt das Problem, dass eine falsche Reservierungskompensation nach einer teilweisen Rückerstattung (Gutschrift) erstellt wird.
* **MDVA-42807** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.6*) - Behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird.
* Aktualisierte Patches: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem die Bestellsummen im Bericht Bestellungen für den Benutzer mit eingeschränktem Administratorzugriff falsch berechnet wurden.
* **MDVA-44940** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt den SQL-Fehler, der beim Speichern der Kategorie über den Administrator auftritt.
* **MDVA-44562** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Es wird das Problem behoben, bei dem die nicht standardmäßige Store-ID für Angebotselemente von der standardmäßigen Store-ID überschrieben wird, obwohl die GraphQL-Anfrage von der nicht standardmäßigen Store-Ansicht stammt.
* **MDVA-43167** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wurde das Problem behoben, dass die Massenaktion „Raster für Admin-Bestellungen“ nicht für mehrseitige Bestellungen gilt, wenn der Admin-Benutzer alle Bestellungen auswählt.
* **MDVA-44044** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Behebt das Problem, dass ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde.
* **MDVA-42509** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.4*) - Es wurde das Problem behoben, dass für eine Schnellbestellung keine CSV-Datei hochgeladen werden konnte, was zu einem Fehler *Cookie kann nicht gesendet werden* führte.
* Aktualisierte Patches: MDVA-41061, MDVA-42584.
* Das Präfix für die neuen [!DNL Quality Patches Tool]-Patches wird aufgrund *internen Prozessänderungen von MDVA* auf *ACSD* geändert.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt das Problem, dass ein zusätzlicher Artikel nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist.
* **MDVA-44887** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebt den Fehler *Nicht erfasste SyntaxError: Unerwarteter Token &#39;const&#39;* im Admin-Bereich.
* **MDVA-43718** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Fehlerbehebungen *Der Benutzer ist nicht berechtigt, auf %resources zuzugreifen.* Fehler, der beim Zugriff auf einen freigegebenen Katalog über eine benutzerdefinierte Integration angezeigt wird.
* **MDVA-44660** (*für Adobe Commerce und Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Es wurde das Problem behoben, dass der ``` ` ``` mit gravierendem Akzent nicht für den Vor- und Nachnamen eines Kunden verwendet werden konnte.
* **MDVA-40896** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt den *Fehler: TypeError: Argument 3 übergeben an Magento* Fehler in asynchroner Produkt-Bulk-API.
* **MDVA-38559** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt den */V1/customers/search API*-Fehler für Kunden mit mehr als einem Abonnement.
* **MDVA-44533** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem der Rabatt fälschlicherweise auf ein untergeordnetes Bundle-Produkt angewendet wurde.
* Aktualisierte Patches: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Es wird das Problem behoben, bei dem Produkte *einzeln nicht sichtbar* weiterhin in den Ergebnissen der erweiterten Katalogsuche angezeigt werden.
* **MDVA-44100** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebt das Problem, dass alle FPTs dem letzten Produkt im Warenkorb zugewiesen und für andere Produkte zurückgesetzt werden.
* **MDVA-43605** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Es wurde das Problem behoben, dass bei Verwendung der REST-API Bestelldaten negative Werte für Zeilensummen zurückgeben.
* **MDVA-43102** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebt das Problem, dass die verkaufsfähige Menge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt.
* **MDVA-43178** (*für Adobe Commerce und Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Es wurde das Problem behoben, dass ein Kunden-Token für einen benutzerdefinierten Store nicht in GraphQL abgerufen werden kann.
* **MDVA-43859** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, dass der Fehler *Keine solche Entität mit customerId =* protokolliert wird, wenn ein gelöschter Kunde versucht, sich anzumelden.
* **MDVA-44147** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Es wurde das Problem behoben, dass eine GraphQL-Anfrage keine Anforderungslisten zurückgibt.
* **MDVA-44505** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebt die Probleme, bei denen GraphQL durch Anwenden von Belohnungspunkten die Gesamtsumme nicht aktualisiert und bei denen Ladengutschriften während der Auftragserteilung mehrmals angewendet werden.
* Aktualisierte Patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Es wurde das Problem behoben, dass die Regel Zugehöriges Produkt nur funktioniert, wenn das Kundensegment auf &quot;*&quot;*.
* **MDVA-39605** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Es wurde das Problem behoben, dass die TTL (Ablaufdatum) des Redis-Caches einen falschen Wert hatte.
* **MDVA-43862** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.5*) - Behebt das Problem, dass der Kunde Warenkorbelemente aufgrund eines GraphQL-Fehlers (UpdateCartItems *Mutation) nicht* kann.
* **MDVA-43824** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Behebt das Problem, dass bei der Stornierung von Aufträgen mit einem Rabatt ein Fehler auftritt.
* **MDVA-43451** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebt das Problem, bei dem der Fehler *Der angeforderte Speicher wurde nicht gefunden. Überprüfen Sie den Store und versuchen Sie es erneut.* wird beim Konfigurieren eines freigegebenen Katalogs für eine bestimmte Website angezeigt.
* **MDVA-43491** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebt das Problem, dass das Basisbildlabel beim Importieren von Produkten für eine Website mit mehreren Stores nicht aktualisiert wird.
* **MDVA-43601** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem mit fehlenden Triggern nach vollständiger Neuindizierung.
* **MDVA-42046** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Es wird das Problem behoben, bei dem einem Produktattribut mit einem Datumseingabefeld beim Aktualisieren eines Produkts ein falscher Wert zugewiesen wird.
* **MDVA-43935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, dass Upsell-Produkte zweimal angezeigt werden.
* **MDVA-44188** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Es wurde das Problem behoben, dass vom System vergebene E-Mails mit `.-` in Adressen nicht gesendet wurden.
* **MDVA-42283** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem das Datums-/Uhrzeitformat im Administratorauftragsraster für das französische Gebietsschema ungültig ist.
* Aktualisierte Patches: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Es wurden Patches für Metadaten für die [!DNL Site-Wide Analysis Tool] hinzugefügt.

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Es wurde das Problem behoben, dass Benutzende die Startzeit für ein aktives geplantes Update bearbeiten konnten.
* **MDVA-42410** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wurde das Problem behoben, dass in Couponberichten nur die Standard-Basiswährung angezeigt wurde.
* **MDVA-41136** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wurde das Problem behoben, dass das Ablaufdatum des `mage-cache-sessid` nicht verlängert wurde, was zu einer Bereinigung der Kundendaten führte.
* **MDVA-39993** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Es wird das Problem behoben, bei dem Inventaränderungen, die über API vorgenommen wurden, nicht auf der Produktseite im Frontend widergespiegelt werden.
* **MDVA-42855** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebt das Problem, dass beim Checkout keine neue Kundenadresse im Adressbuch gespeichert wird.
* **MDVA-42645** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Es wurde das Problem behoben, dass der Administrator Prämienpunkte nicht zurückerstatten kann, wenn die Funktion „Gutschrift speichern“ deaktiviert ist.
* **MDVA-43414** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Behebt den schwerwiegenden PHP-Fehler, der beim Ausführen der `inventory.reservations.updateSalabilityStatus` Queue Consumer auf numerischen SKUs auftritt.
* **MDVA-41628** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Es wurde das Problem behoben, dass bestehende Administratoren mit Administratorrechten beim Hinzufügen neuer Module Zugriff auf die neuen Ressourcen erhielten.
* **MDVA-43348** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem die GraphQL-Anfrage für Geschenkgutscheine einen Fehler anzeigte, wenn `gift_card_options` *uid*.
* **MDVA-39546** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem das Startdatum für die Staging-Aktualisierung während der Bearbeitung auf ein früheres Datum als das aktuelle Datum gesetzt werden konnte.
* **MDVA-42950** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wurde das Problem behoben, dass Videos auf der Produktseite nicht wiedergegeben wurden.
* **MDVA-42689** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem Adobe Commerce beim Aktualisieren *Produktkategorien während des Imports einen* Integritätsbeschränkungsfehler) ausgibt.
* **MDVA-41229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem, dass im Backend verfügbare Bilder nach dem Import konfigurierbarer Produkte nicht im Frontend angezeigt werden.
* **MDVA-43731** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Es wurde das Problem behoben, dass *Suchsynonyme* nicht mehr funktionieren, wenn in *Mindestbedingungen für übereinstimmende Werte* wird.
* **MDVA-43232** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem das Sortieren von Produkten in [!DNL Visual Merchandiser] nach dem Sonderpreis Nach unten/oben einen Fehler beim Speichern der Kategorie verursachte.
* **MDVA-43726** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.3*) - Es wird das Problem behoben, bei dem die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer teilweisen Neuindizierung nicht angewendet werden kann.
* Aktualisierte Patches: MDVA-36464, MDVA-37478, MDVA-38608.
* Es wurden Patches für Metadaten für die [!DNL Site-Wide Analysis Tool] hinzugefügt.

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Es wurde das Problem behoben, dass Produktpreisattribute für eine bestimmte Website nicht über die REST-API aktualisiert werden können.
* **MDVA-41350** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wird das Problem behoben, bei dem eine Ausnahme ausgelöst wird, wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt außerhalb seines Rollenbereichs per SKU in einer Bestellung hinzufügt.
* **MDVA-42269** (*für Adobe Commerce und Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Behebt das Problem, dass ein Admin-Benutzer sich aufgrund des *TypeError: strtotime() nicht beim Admin anmelden kann und erwartet, dass Parameter 1 eine Zeichenfolge, null und* ist.
* **MDVA-40830** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem, dass bei der Auftragserteilung das Store-Guthaben mehrmals angewendet wird.
* **MDVA-42237** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Es wurde das Problem behoben, dass ein konfigurierbarer Sonderpreis für ein Produkt nach Änderungen im Unterproduktpreis nicht aktualisiert wurde.
* **MDVA-42520** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt das Problem, dass der Steuersatz zweimal angewendet wird, wenn *Grenzüberschreitenden Handel aktivieren* verwendet wird.
* Aktualisierte Patches: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Veralteter Patch: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.4.5*) - Es wurde das Problem behoben, dass bei einer Massenattribut-Aktualisierung eine URL-Umschreibung für den Default Store nur nach einer Änderung der *Produktsichtbarkeit*.
* **MDVA-43091** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt das Problem, dass die Bestellung eines Bundle-Produkts vom Administrator im Backend zu dem Fehler *Sie können für dieses Produkt keine Dezimalgröße verwenden*.
* **MDVA-40816** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wird das Problem behoben, bei dem verwandte Produktregeln Produkte aus Kategorien anzeigen, die in den Regelbedingungen nicht definiert sind.
* **MDVA-41305** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem die GraphQL-Mutation nach dem Hinzufügen zur Wunschliste keine konfigurierbaren Produktoptionen zurückgibt.
* **MDVA-39181** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Es wird das Problem behoben, bei dem verwandte Produktregeln Produkte aus Kategorien anzeigen, die in den Regelbedingungen nicht definiert sind.
* **MDVA-42584** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Es wurde das Problem behoben, dass der konfigurierbare Lagerstatus im Backend nach dem Ändern der Menge und des Lagerstatus über den Import oder die API nicht aktualisiert wurde.
* **MDVA-40175** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Es wurde ein Problem behoben, bei dem *Klicken, um die Versandmethode zu ändern* keine Optionsfelder anzeigt, um Versandmethoden während der Neubestellung im Admin-Bereich auszuwählen.
* **MDVA-42768** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Es wurde das Problem behoben, bei dem das konfigurierbare Produkt den regulären Preis als 0 anzeigt, wenn *Nicht vorrätig anzeigen* „Ja“ ist.
* **MDVA-43201** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, dass bei der Kundenanmeldung ein Fehler auftritt, wenn das DOB-Attribut mit bestimmten Gebietsschemata verwendet wird.
* Aktualisierte Patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Es wurde das Problem behoben, dass Datumsfilter nicht richtig funktionierten, wenn sich die Adobe Commerce-Zeitzone von der Zeitzone der lokalen Umgebung unterscheidet.
* **MDVA-42657** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Es wurde das Problem behoben, dass Admin-Benutzende in den Segmentbedingungen des Kunden keine Kategorien auswählen konnten.
* **MDVA-42806** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wird das Problem behoben, dass jedes Mal, wenn ein bestehendes Unternehmen über *REST-API aktualisiert wird, eine E-Mail* Neue Unternehmensregistrierung) gesendet wird.
* **MDVA-37984** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5* [!DNL Visual Merchandiser]) - Es wurde das Problem behoben, dass die Funktion *Match product by rule* Produkte nicht korrekt mit Staging-Updates filtert.
* **MDVA-40488** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wurde das Problem behoben, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in der richtigen Preisspanne angezeigt wurden.
* **MDVA-42507** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebt das Problem, dass der Vollseiten-Cache nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt wird.
* **MDVA-39163** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebt das Problem, dass keine Versandmethoden verfügbar sind, wenn ein neuer Benutzer registriert ist und Produkte im Warenkorb aus der Gastsitzung stammen.
* **MDVA-38626** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.5*) - Es wurde das Problem behoben, dass ein Administrator bzw. eine Administratorin nicht in der Lage war, über die [!DNL PayPal Payflow Pro] Bezahlung eine Bestellung im Backend aufzugeben.
* **MDVA-38666** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.3.6*) - Es wird das Problem behoben, bei dem Admin-Benutzende die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern können.
* **MDVA-38526** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Es wurde das Problem behoben, dass Admin-Benutzerinnen und -Benutzer nicht auf die [!DNL Site-Wide Analysis tool] zugreifen können.
* Aktualisierte Patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wird das Problem behoben, bei dem Benutzer den Fehler 500 erhalten, nachdem sie das Cookie *mage-messages* gesetzt haben, falls es bereits vorhanden ist, es jedoch keine neuen Nachrichten gibt.
* **MDVA-41139** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Es wird das Problem behoben, dass konfigurierbare Produkte nach dem Produktimport nicht mehr vorrätig sind, wenn die Menge eines einfachen Produkts für eine seiner Quellen = 0 ist.
* **MDVA-42326** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Es wird das Problem behoben, bei dem Kunden nach einem Sitzungs-Timeout einen Fehler beim Checkout erhalten, selbst wenn der persistente Warenkorb aktiviert ist.
* **MDVA-42341** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wird das Problem behoben, bei dem die `categoryList` GraphQL-Abfrage die Ergebnisse nicht filtert, wenn eine Anfrage die Store-Kopfzeile hat.
* **MDVA-38393** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wird das Problem behoben, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn dessen einfaches Produkt umbenannt wird.
* **MDVA-39153** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, dass ein Rabattbetrag bei der Neubestellung in der Admin falsch berechnet wird.
* Aktualisierte Patches: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.3*) - Es wurde das Problem behoben, dass Admin-Benutzer nach dem Löschen der Website nicht auf das Raster des Kunden zugreifen können.
* **MDVA-40311** (*für Adobe Commerce und Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem Admin-Benutzer die Fehlermeldung *Ungültiger Sicherheits- oder Formularschlüssel) erhalten. Bitte aktualisieren Sie die Seite* nachdem Sie sich beim Administrator angemeldet haben, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist.
* **MDVA-41631** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Es wird das Problem behoben, bei dem Benutzende einen Fehler erhalten, wenn sie versuchen, Bestellinformationen ohne einen optionalen *Telefon*-Wert über GraphQL abzurufen.
* **MDVA-27239** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Es wurde das Problem behoben, dass Crosssell-Produkte nicht angezeigt wurden.
* Aktualisierte Patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.*) - Behebt das Problem mit fehlenden Produkten im Frontend während der Neuindizierung.
* **MDVA-40120** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Es wurde das Problem behoben, dass die GraphQL-Sortierung nach DESC/ASC bei Produkten mit gleicher Relevanz oder demselben Preis nicht funktionierte.
* **MDVA-41399** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.2*) - Behebt das Problem, dass Admin-Benutzer nicht auf die Seite *Warenkorb verwalten* zugreifen können, wenn ein Kunde ein Produkt auf die Wunschliste setzt.
* **MDVA-40609** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebt das Problem, dass in der `cataloginventory_stock_status`-Indextabelle keine Daten zu deaktivierten Produkten vorhanden sind, sodass falsche deaktivierte Produktmengen angezeigt werden.
* **MDVA-39031** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Es wird das Problem behoben, dass das Hinzufügen eines Produkts zum Warenkorb über GraphQL möglich ist, selbst wenn es nicht der Ziel-Website zugewiesen ist.
* **MDVA-41597** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wird das Problem behoben, bei dem Benutzende einen Fehler erhalten, wenn mit GraphQL mehr als ein konfigurierbares Produkt zum Warenkorb hinzugefügt wird.
* **MDVA-27456** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.3.7*) - Es wird das Problem behoben, bei dem Benutzende beim Versuch, [!DNL Swagger] zu laden, einen Fehler erhalten.
* **MDVA-32776** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2*) - Behebt das Problem, dass der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versendet wird.
* **MDVA-30862** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.0*) - Behebt das Problem mit dem falschen Bestelldatum auf der gedruckten PDF-Rechnung.
* Die Indexseite für die [!DNL Quality Patch Tool] wurde verbessert. Es wurde eine bequeme Suche und Filterung nach [!DNL quality patches] auf der neuesten Version des Tools hinzugefügt.
* Aktualisierte Patches: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wird das Problem behoben, bei dem es nicht möglich ist, ein neues oder ein bestehendes geplantes Update für ein Produkt zu erstellen, wenn das Enddatum zuvor entfernt wurde.
* **MDVA-41046** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wurde das Problem behoben, dass einfache Produkte mit benutzerdefinierten Optionen für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind.
* **MDVA-40545** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wurde das Problem behoben, dass nur der erste Knoten für eine Seite abgerufen wurde, selbst wenn für dieselbe Seite mehr als ein Knoten vorhanden war.
* **MDVA-41164** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Es wurde das Problem behoben, dass ein Administrator bzw. eine Administratorin ein Unternehmen nicht mit einem benutzerdefinierten Kundenattribut vom Typ „Datei“ oder „Bild“ speichern oder bearbeiten konnte.
* **MDVA-39229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, das dazu führt, dass nach der Aktualisierung der Startzeit des Staging-Updates für Katalogregeln der folgende Fehler angezeigt wird: *Cron Job staging_synchronize_entities_period hat einen Fehler: Das aktive Update kann nicht gelöscht werden.*
* **MDVA-40619** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem Änderungen an der CMS-Seitenhierarchie einen 500-Fehler verursachten, wenn versucht wurde, eine CMS-Seite inline zu bearbeiten.
* **MDVA-41061** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Es wird das Problem behoben, bei dem der Lagerstatus auf „skalierbar“ zurückgesetzt wird, wenn ein Produkt vom Administrator gespeichert wird.
* **MDVA-31763** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem Katalogpreisregeln bis zur manuellen Neuindizierung zurückgesetzt (oder nicht angewendet) wurden.
* **MDVA-37748** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Es wird das Problem behoben, bei dem eine GraphQL-Abfrage Produkte zurückgibt, die keinem freigegebenen Katalog zugewiesen sind.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wurde das Problem behoben, dass Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können.
* **MDVA-40101** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.4.0*) - Behebt das Problem, dass Artikel nach einer erfolgreichen Bestellplatzierung über [!DNL PayPal Express] Checkout nicht aus dem Mini-Warenkorb entfernt werden.
* **MDVA-40401** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Es wird das Problem behoben, bei dem sich der Couponnutzungswert ändert, selbst wenn die Bestellung fehlschlägt.
* **MDVA-40537** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Behebt das Problem, dass beim Erstellen einer Store-Ansicht Benutzende einen Fehler erhalten, wenn mehrere CMS-Seiten mit demselben URL-Schlüssel vorhanden sind.
* **MDVA-37725** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Es wird das Problem behoben, bei dem E-Mails mit asynchroner Reihenfolge, die von nicht standardmäßigen Websites gesendet werden, Logo-URLs von der Standard-Website enthalten.
* **MDVA-39482** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Behebt das Problem, dass ein Produkt nicht vorrätig ist, wenn es mit der Menge „0“ importiert wird, wenn der Auftragsrückstand aktiviert ist.
* **MDVA-40435** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.4*) - Behebt das Problem mit einem falschen Rabatt auf Paketprodukte mit dynamischen Preisen, wenn sie über GraphQL angewendet werden.
* **MC-42528** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Behebt das Problem, dass die `categoryList` GraphQL-Abfrage sowohl zugewiesene als auch nicht zugewiesene Kategorien zurückgibt.
* **MDVA-29400** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem mit doppelten Bestellungen, die mit [!DNL PayPal Express Checkout] aufgegeben werden.
* **MDVA-26005** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Behebt das Problem, dass es nicht möglich ist, eine Kategorie in einer Kategoriestruktur für Warenkorbpreisregelbedingungen auszuwählen.
* **MDVA-25631** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Verbessert die Leistung beim Bearbeiten und Speichern von Kundensegmenten, die eine große Anzahl von Kunden enthalten.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Es wurde das Problem behoben, dass GraphQL-Suchabfragen in beliebten Suchbegriffen im Admin-Bereich nicht angezeigt wurden.
* **MDVA-40601** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Es wird ein Problem behoben, bei dem Benutzende einen Fehler erhalten, wenn sie versuchen, Informationen zur Kategorieänderung durch geplante Aktualisierung über GraphQL abzurufen.
* **MDVA-37234** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Behebt das Problem, dass durch mehrmaliges Hinzufügen eines Artikels zum Warenkorb (parallele Anfrage) für dieselbe SKU ein doppelter Zeileneintrag für dieselbe Warenkorb-ID erstellt wird.
* **MDVA-33606** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Behebt das Problem, dass beim Speichern einer CMS-Seite, die einer Hierarchie zugewiesen ist, *Fehler „Eindeutige Einschränkungsverletzung* angezeigt wird.
* **MDVA-31590** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Es wurde das Problem behoben, dass Benutzer Attribute nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisieren können.
* **MDVA-36309** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Es wurde das Problem behoben, bei dem die Produktsuche nach Attributen in den Admin-Rastern langsam ist.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, dass die Rechnung mit FPT eine falsche Gesamtsumme anzeigt, wenn die Bestellung über den Ladenkredit bezahlt wird.
* **MDVA-37364** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.3*) - Es wurde das Problem behoben, bei dem das benutzerdefinierte Kundenattribut des Datentyps die Rasterbenutzeroberfläche des Kunden beschädigte.
* **MDVA-39195** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Es wurde das Problem behoben, dass *Schaltfläche „Zum Warenkorb*&quot; auf der Kategorieseite inaktiv war, wenn die Umleitung zum Warenkorb aktiviert war.
* **MDVA-37115** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Es wurde das Problem behoben, dass ein unnötiger *Nur 0 verbleibend*-Hinweis auf der konfigurierbaren Produktseite angezeigt wurde.
* **MDVA-39521** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebt das Problem, dass Benutzende keine Versandadressen im Warenkorb mit einer leeren Telefonnummer über GraphQL festlegen können.
* **MDVA-39384** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Behebt das Problem, dass das benutzerdefinierte Kundenattribut für einen Firmenbenutzer nicht gespeichert wird.
* **MDVA-39043** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.3*) - Es wird das Problem behoben, bei dem Admin-Benutzende mit eingeschränktem Zugriff einen Fehler erhalten, wenn sie versuchen, das *Produkte*-Widget zur CMS-Seite hinzuzufügen.
* **MDVA-39966** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem bei der Bereitstellung falscher Gebietsschemata.
* **MDVA-38852** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Behebt das Problem, dass der Katalogbestand nach Design Tabellen für Aktualisierungen sperrt, die die Leistung in Fällen mit mehreren parallelen Bestellungen erheblich verringern.
* **MDVA-39986** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Es wurde das Problem behoben, dass Benutzende in der Admin auf MacOS keine Bestellung über den Safari-Browser aufgeben konnten.
* **MDVA-38447** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt zwei Probleme: Wenn die *Nicht einzeln sichtbar* konfigurierbaren untergeordneten Produkte in der GraphQL-Antwort zurückgegeben werden und die MySQL-Abfrage für GraphQL-Produktabfrage mit Kategoriefilter optimieren.
* **MDVA-40134** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Es wurde das Problem behoben, dass GraphQL keine verwandten Produkte zurückgibt, wenn der freigegebene Katalog aktiviert ist.
* **MDVA-39935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Es wurde das Problem behoben, bei dem GraphQL konfigurierbare untergeordnete Produkte zurückgibt, die auf Website-Ebene deaktiviert sind.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4*) - Behebt das Problem, dass der *Aufruf an eine Memberfunktion getId()* auf der Seite mit den Bestelldetails in Admin angezeigt wird.
* **MDVA-34948** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Behebt das Problem mit lang laufenden Abfragen wie `GET_LOCK`.
* **MDVA-39305** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Es wurde das Problem behoben, dass registrierte Kundinnen und Kunden sich nicht mit aktiviertem Google ReCaptcha anmelden können.
* **MDVA-37897** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem mit einer falschen Umleitung, wenn ein Kunde versucht, Produkte mit Optionen aus dem Widget „Kürzlich angezeigt“ hinzuzufügen.

## v1.1.0 {#v1-1-0}

* Patch-Kategorien wurden eingeführt, um das Benutzererlebnis zu verbessern und die Suche nach erforderlichen Patches für Kunden zu erleichtern.
* Die `patches.json` wurde in `support-patches.json` umbenannt.
* **MDVA-38799** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert wurden.
* **MDVA-37592** (*für Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebt das Problem, wenn die Sortierung nach Preis bei Produkten mit einem Nullpreis, der dem freigegebenen Katalog zugewiesen ist, nicht korrekt funktioniert.
* **MDVA-38827** (*für Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Es wurde das Problem behoben, dass Kunden eine E-Mail mit einer Fehlermeldung erhalten, in der sie eine Bestellung per Versand erhielten.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*für Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Behebt den Fehler beim Speichern von CMS-Seiten: *Element mit derselben ID PAGE_ID ist bereits vorhanden*.
* **MDVA-34680** (*für Adobe Commerce >=2,3,6 &lt;=2,3,7 || >=2.4.1 &lt;2.4.3*) - Es wurde das Problem behoben, bei dem die Erstellungszeit des Kundenkontos im Kundenraster nicht korrekt gefiltert wurde.
* **MDVA-37068** (*für Adobe Commerce >=2.3.1 &lt;2.4.4*) - Behebt das Problem, dass der falsche Steuersatz angezeigt wird, wenn der Warenkorb nur virtuelle Produkte enthält.
* **MDVA-38608** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Es wird das Problem behoben, dass temporäre Tabellen nicht gelöscht werden, wenn die Neuindizierung nicht erfolgreich abgeschlossen wurde.
* **MDVA-38308** (*für Adobe Commerce >=2,3,5 &lt;=2,3,6-p1 || >=2,4,0 &lt;=2,4,1-p1 || >=2.4.2 &lt;2.4.4*) - Behebt die Probleme beim Hinzufügen von [!DNL Vimeo]-Videos zu Produkten.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*für Adobe Commerce >=2.3.6 &lt;2.4.3*) - Behebt das Problem, dass der Kunde bei Verwendung der [!DNL Paypal Payment Advanced] nicht zur Zahlungsbestätigungsseite weitergeleitet wird.
* **MDVA-37082** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem, dass beim Speichern des benutzerdefinierten Bestands an gruppierten Produkten das Produkt im Frontend nicht vorrätig angezeigt wird.
* **MDVA-36572** (*für Adobe Commerce >=2.3.5 &lt;2.4.3*) - Behebt das Problem, dass durch Aktualisierungen der Gutschrift keine doppelten Produktreservierungsaktualisierungen mehr in der Datenbank verursacht werden.
* **MDVA-38132** (*für Adobe Commerce >=2.3.3 &lt;2.4.3*) - Behebt das Problem, wenn das Admin-Bedienfeld aufgrund eines *zu viele Weiterleitungen*-Fehlers nicht erreichbar ist.
* **MDVA-38270** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebt das Problem mit fehlenden Geschenkkarteninformationen in der Bestellsumme in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*für Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Behebt das Problem beim Hinzufügen eines konfigurierbaren Produkts zum Warenkorb über GraphQL, wenn die Website-ID nicht mit der Store-ID übereinstimmt.
* **MDVA-36832** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Behebt das Problem, dass Bilder auf Seiten dupliziert werden, wenn die Ansichtsbreite 768 Pixel beträgt.
* **MDVA-37874** (*für Adobe Commerce >=2,3,6 &lt;=2,3,7 || >=2.4.1 &lt;=2.4.2-p1*) - Behebt das Problem, dass *Fester Rabattbetrag für den gesamten Warenkorb* fälschlicherweise auf ein Bundle-Produkt mit mehr als einer Option angewendet wird.
* **MDVA-37913** (*für Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Behebt das Problem, dass herunterladbare Links verschwinden, wenn das herunterladbare Produkt über die API aktualisiert wird.
* **MDVA-34330** (*für Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Es wurde das Problem behoben, dass Bestellungen im Bestellraster nicht nach der Admin-Zeitzone gefiltert wurden.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*für Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Behebt das Problem, dass Adobe Commerce beim Erstellen einer Teilrechnung für Bestellungen mit der Zahlungsmethode *Zahlung auf Konto* über die REST-API einen Fehler ausgibt.
* **MDVA-37362** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Es wurde das Problem behoben, bei dem konfigurierbare Produktoptionenwerte und Variantenattributwerte in der GraphQL-Antwort leer waren.
* **MDVA-37288** (*für Adobe Commerce 2.4.2*) - Es wurde das Problem behoben, bei dem nach einer GraphQL-Anfrage falsche Stufenpreise zurückgegeben wurden.
* **MDVA-37225** (*für Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Behebt das Problem, dass der Upload-Prozess bei der schnellen Bestellerstellung hängen bleibt, wenn in importierten SKUs ein ganzzahliger Wert vorhanden ist.
* **MDVA-37224** (*für Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Behebt das Problem, dass Kunden nicht für ein verhandelbares Angebot mit [!DNL PayFlow Pro] mit einem anderen Produkt im Warenkorb bezahlen können.
* **MDVA-36286** (*für Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebt das Problem, dass die Widget-Vorschau von Page Builder-Produkten unterbrochen wird, wenn dieselbe SKU in Unterkategorien eine andere Position einnimmt.
* **MDVA-30186** (*für Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Es wurde das Problem behoben, bei dem Attributoptionen in der GraphQL-Antwort nach Optionswert anstatt nach der Anzahl der Attributelemente sortiert wurden.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*für Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Behebt das Problem, dass die alten benutzerdefinierten Optionen nach der Änderung über die API erhalten bleiben.
* **MDVA-35773** (*für Adobe Commerce >=2,3,6 &lt;=2,3,6-p1 || >=2.4.1 &lt;=2.4.2*) - Behebt das Problem, dass die Gesamtsumme auf der Rechnung für Bestellungen mit 100 % Rabatt nicht als Null angezeigt wird.
* **MDVA-36833** (*für Adobe Commerce 2.4.2*) - Behebt das Problem, dass in Suchergebnissen nach dem Ausschließen einiger Produkte aus dem freigegebenen Katalog zufällig eine Anzahl von Produkten pro Seite angezeigt wird.
* **MDVA-37182** (*für Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Behebt das Problem, dass falsche Suchergebnisse sowohl in [!DNL Elasticsearch] 6 als auch in Version 7 abgerufen wurden.
* **MDVA-36253** (*für Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Behebt das Problem, dass nach dem Löschen des Artikels im Mini-Warenkorb die falsche Zwischensumme angezeigt wird.
* **MDVA-36853** (*für Adobe Commerce 2.4.2*) - Behebt das Problem, dass beim Laden großer Mediensammlungen keine Bilder angezeigt werden.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*für Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Behebt das Problem mit fehlenden gebündelten Produkten auf Kategorieseiten.
* **MDVA-36615** (*für Adobe Commerce 2.4.2*) - Behebt das Problem mit der falschen Produktzahl im Admin-Produktraster.
* **MDVA-36464** (*für Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Es wurde das Problem behoben, dass die E-Mail-Benachrichtigungskonfiguration auf Store-Ansichtsebene nicht funktioniert.
* **MDVA-36138** (*für Adobe Commerce ^2.3.2*) - Behebt das Problem, dass der Versandpreis nicht angepasst wird und der vollständige Versandpreis Kunden angezeigt wird, wenn nicht alle Artikel im Warenkorb für die Regel für den kostenlosen Warenkorb qualifiziert sind.
* **MDVA-36424** (*für Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Es wird das Problem behoben, bei dem an Page Builder-Elemente angehängte Medienbilder verschwinden, wenn der Inhalt wiederholt bearbeitet wird, wenn sich die Backend-Basis-URL von der Storefront-Basis-URL unterscheidet.
* **MDVA-35984** (*für Adobe Commerce ^2.4.0*) - Behebt das Problem mit der falschen Produktmenge und verkaufbaren Menge, nachdem mehrere gleichzeitige Sendungen für dasselbe Produkt erstellt wurden.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Dadurch wird das Problem behoben, dass die GraphQL-Abfrage mithilfe des Kategorie-Cache-Tags nicht zwischenspeichert.
* **MDVA-33168** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebt das Problem beim Aktualisieren eines Produktattributs über die API, wenn alle anderen Attribute in einen leeren Wert geändert werden.
* **MDVA-19640** (*für Adobe Commerce >=2.3.0*) - Behebt das Problem, dass [!DNL Advanced Reporting] keine Daten anzeigt.
* **MDVA-11189** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, wenn nach dem Import einer CSV-Datei zum Aktualisieren des Produktbestands Zeilen aus der `cataloginventory_stock` gelöscht werden.
* **MDVA-26639** (*für Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Behebt das Problem, dass bei der Erstellung einer neuen E-Mail-Vorlage für Bestellbestätigungen die Bestellartikel in der Bestellpost fehlen.
* **MDVA-15546** (*für Adobe Commerce >=2.3.0*) - Es wird das Problem behoben, dass nach dem Erstellen einer Bestellung *Column entity_id, bei dem die Klausel mehrdeutig ist* Fehler im Ausnahmeprotokoll angezeigt wird.
* **MDVA-21095** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, wenn ein `INSERT INTO search_tmp` nach der Aktualisierung des Massenattributs nicht beendet wird.
* **MDVA-23845** (*für Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Es wurde das Problem behoben, dass E-Mail-Vorlagen nach aktivierter JavaScript-Minimierung nicht in der Vorschau angezeigt werden können.
* **MDVA-22026** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebt das Problem, dass das Importieren von Produkten aus CSV-Dateien, einschließlich Bildern aus externen URLs, fehlschlägt.
* **MDVA-22383** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Es wurde das Problem behoben, dass das Speichern eines Produkts viel Zeit in Anspruch nimmt und die Seite beschädigt wurde.
* **MC-41359** (*für Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Behebt das Problem der falschen SameSite-Cookie-Parametereinstellungen.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*für Adobe Commerce 2.4.1*) - Es wurde das Problem behoben, bei dem Page Builder den folgenden Fehler ausgibt: *Beim Initiieren von Page Builder ist ein Fehler aufgetreten. Wenden Sie sich an Ihren Ansprechpartner beim technischen Support.*
* **MDVA-35356** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Store-Gutschriftsrückgabe nach teilweise fakturierter Auftragsstornierung.
* **MDVA-33289** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Es wurde das Problem behoben, dass während des Checkouts in der Rechnungsadressen-Benutzeroberfläche unformatierter JavaScript-Code angezeigt wird, wenn [!DNL Google Tag Manager] aktiviert ist.
* **MDVA-35982** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Es wird das Problem behoben, dass Admin-Benutzer, die auf eine bestimmte Website beschränkt sind, keine Sendung für die auf derselben Website aufgegebene Bestellung erstellen können.
* **MDVA-35155** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebt das Problem, dass es unmöglich ist, ein Bundle-Produkt zu kaufen, wenn der Optionstitel geändert wurde.
* **MDVA-35910** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Es wurde das Problem behoben, dass nach der Deaktivierung der Funktion „Als Kunde anmelden“ kein neues Kundenkonto erstellt werden konnte.
* **MDVA-34474** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem beim Hinzufügen eines Produkts zur Anforderungsliste mithilfe der -API.
* **MDVA-34591** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Warenkorb-Regelrabattberechnung für *Maximaler Mengenrabatt wird angewendet auf* und *Rabatt-Mengenschritt (Kaufen X)*.
* **MDVA-33704** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Behebt das Problem, dass die Versandoption *In-Store-* nicht angezeigt wird, obwohl sie so konfiguriert ist, dass sie verfügbar ist.
* **MDVA-34928** (*für Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Behebt das Problem, dass der Seitenlader auf unbestimmte Zeit angezeigt wird, nachdem das Speicherguthaben aus der Zahlung entfernt wurde.
* **MDVA-35254** (*für Adobe Commerce >=2.3.1 &lt;2.4.3*) - Behebt die Probleme mit CAPTCHA während des Checkouts.
* **MDVA-35569** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Es wird das Problem behoben, dass das Feld *Feste Produktsteuern* in der GraphQL-Antwort nicht ausgefüllt wird, wenn der Status angegeben ist.
* **MDVA-35847** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebt das B2B-Problem, bei dem das Formular „Company Users“ fehlschlägt, wenn ein benutzerdefiniertes Kundenattribut verwendet wird.
* **MDVA-31307** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebt das Problem, dass aufgrund von Problemen mit der dynamischen CSP-Whitelisting für zwischengespeicherte Blöcke *Speicherfehler)* bestimmten Kategorien auftreten.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigiert den falschen *In Bearbeitung* Nachrichtenstatus für die richtige *Abschließen* Nachricht für Verbraucher-`quoteItemCleaner` nach dem Löschen mehrerer Produkte.
* **MDVA-34102** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Legt fest, dass die Anzahl der Standardbestände für deaktivierte Produkte auf den Produktraster- und Produktseiten „Produkt bearbeiten“ im Admin-Bereich bei null liegt.
* **MDVA-35286** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebt das Problem, dass ein Fehler auftritt, wenn ein Kunde gebündelte Produkte im Warenkorb hat und vom Checkout mit mehreren Adressen zum Checkout mit einer Seite wechselt.
* **MDVA-35312** (*für Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Fehlerbehebung für Antwort-Code 500 bei einer leeren GraphQL-Anfrage.
* **MDVA-34189** (*für Adobe Commerce >=2.3.4 &lt;2.4.3*) - Behebt eine Zeitüberschreitung von 503 ersten Byte bei [!DNL Visual Merchandiser] Abfragen beim Laden der Seite mit der Administratorkategorie.
* **MDVA-34695** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebt negative `children_count` nach dem Löschen von Kategorien.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*für Adobe Commerce >=2.3.1 &lt;2.4.3*) - Es wird das Problem behoben, dass das Kontrollkästchen *Standardwert verwenden* nach Anwendung der geplanten Änderungen deaktiviert wird. Das Problem tritt auf, wenn die geplanten Änderungen nicht mehr wirksam sind.
* **MDVA-35064** (*für Adobe Commerce >=2.3.3 &lt;2.4.3*) - Es wird das Problem behoben, dass URL-Neuschreibungen für konfigurierbare Produkte, die über die API erstellt wurden, nicht generiert werden.
* **MDVA-34943** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass die zuvor eingegebenen SKUs in der Schnellbestellung zwischengespeichert werden.
* **MDVA-35197** (*für Adobe Commerce >=2.3.5 &lt;2.4.0*) - Behebt das Problem, dass beim Hinzufügen zum Warenkorb mit GraphQL ein Fehler auftritt, wenn zuvor hinzugefügte Produkte nicht mehr vorrätig sind.
* **MDVA-34850** (*für Adobe Commerce >=2.3.1 &lt;2.4.0*) - Behebt das Problem, dass die nicht vorrätigen Optionen eines konfigurierbaren Produkts nicht angezeigt werden, anstatt als durchgestrichen angezeigt zu werden.
* **MDVA-34867** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Es wird das Problem behoben, dass Werte für ein Bedingungsfeld, das für eine geplante Aktualisierung festgelegt wurde, nicht gespeichert werden.
* **MDVA-35092** (*für Adobe Commerce >=2.3.5 &lt;2.4.3*) - Es wurde das Problem behoben, dass Benutzende aufgrund der veralteten [!DNL Vimeo]-API keine [!DNL Vimeo] hinzufügen können.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*für Adobe Commerce >=2.3.6 &lt;2.4.3*) - Es wurde das Problem behoben, dass die Inhaltstyp-Vorschau von Page Builder-Produkten funktioniert, wenn übereinstimmende Produkte unterschiedliche Preise für jede Website haben.
* **MDVA-32634** (*für Adobe Commerce ^2.3.1*) - Es wird das Problem behoben, bei dem der `url_path` der allen Stores zugewiesenen Kategorie unverändert bleibt, nachdem die Kategorie in der Hierarchie verschoben wurde.
* **MDVA-33344** (*für Adobe Commerce ^2.3.0*) - Es wird das Problem behoben, bei dem die hartcodierte `rma_item` standardmäßige Entitätenattribut-Set-ID anstelle des Werts aus der Datenbank verwendet wird.
* **MDVA-34192** (*für Adobe Commerce >=2.3.4 &lt;2.4.3*) - Das Problem wurde behoben, dass es nicht möglich war, das Geburtsdatum des Kunden im Format TT/MM/JJJJ zu ändern/anzugeben.
* **MDVA-34847** (*für Adobe Commerce ^2.3.0*) - Korrigiert die Konvertierung des Store-IDs-Typs in eine Ganzzahl für die SQL-Bedingung in Admin-Sammlungen für Admin-Benutzer mit benutzerdefinierten Berechtigungen.
* **MDVA-34886** (*für Adobe Commerce ^2.3.2*) - Behebt das Problem, dass die Suche keine Ergebnisse zurückgibt, wenn *weight*-Produktattribut als durchsuchbar konfiguriert ist.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem, dass [!DNL PayPal Payflow Pro] Zahlung mit dem Formatierungsfehler der Umleitungsparameterliste fehlschlägt.
* **MDVA-34023** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem, bei dem der Fehler *Keine solche Entität mit addressId* zufällig im Browser der Besucher angezeigt wird.
* **MDVA-32759** (*für Adobe Commerce >=2.3.1 &lt;2.4.3 mit B2B-Erweiterung*) - Es wurde das Problem behoben, dass freigegebene Kataloge bestehende Preisstufen löschen.
* **MDVA-33482** (*für Adobe Commerce ^2.3.5*) - Behebt das Problem, dass das Generieren einer Gutschrift für eine Teilrechnung zu einer Steuer für die Gesamtbestellung führt, anstatt zu einer Steuer für diese Teilrechnung.
* **MDVA-33393** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fehlerbehebung *Bereitgestellte countryId existiert nicht*.
* **MDVA-33632** (*für Adobe Commerce >=2.3.0 &lt;2.3.7*) - Bietet eine Fehlerbehebung, bei der die Ausnahmemeldung *Dieses Produkt ist nicht vorrätig* einem Administrator angezeigt wird, wenn er versucht, ein nicht vorrätiges Produkt neu zu bestellen.
* **MDVA-34469** (*für Adobe Commerce >=2.4.1 &lt;2.4.2*) - Es wird das Problem behoben, bei dem GraphQL-Mutationen im Warenkorb eines Kunden bei Verwendung mehrerer Store-Ansichten fehlschlagen.
* **MDVA-33976** (*für Adobe Commerce >=2.3.0 &lt;2.3.7*) - Behebt das Problem, dass das Bundle-Produkt nicht vorrätig in der Storefront angezeigt wird, nachdem die zweite Option aus dem Bundle-Produkt entfernt wurde.
* **MDVA-33894** (*für Adobe Commerce >=2.4.0 &lt;2.4.1 mit B2B-Erweiterung*) - Behebt mehrere Probleme mit der Funktion „Schnellbestellung“, einschließlich des Hinzufügens und Entfernens mehrerer Produkte und der Unterscheidung zwischen Groß- und Kleinschreibung der SKU.
* **MDVA-27664** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem im Kundenregistrierungsformular, das dazu führt, dass ein Fehler angezeigt wird: *ERROR - Das Geburtsdatum sollte nicht nach heute liegen.*
* **MDVA-33970** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebt das Problem, dass das falsche Währungszeichen in der Gutschrift vorhanden ist, wenn der Umfang des Preisattributs auf „Website“ festgelegt ist.
* **MDVA-33992** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass B2B-Sonderpreise während des Checkouts falsch angezeigt werden.
* **MDVA-34100** (*für Adobe Commerce >=2.3.4 &lt;2.4.2 mit B2B-Erweiterung*) - Es wurde das Problem behoben, dass ein Unternehmenskonto nicht über die Seite „Unternehmensstruktur“ erstellt werden kann.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*für Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Behebt das Problem mit doppelten Bildern nach dem Produktimport aus einer CSV-Datei.
* **MDVA-33382** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt die Probleme mit der Invalidierung von Indexern, nachdem Produkte aus einer Kategorie entfernt wurden.
* **MDVA-28511** (*für Adobe Commerce >=2.3.5 &lt;2.3.6*) - Es wird das Problem behoben, bei dem es nicht möglich ist, [!DNL PayPal] Auschecken abzuschließen, wenn das Feld „Name“ bestimmte Zeichen (z. B. Großbuchstaben mit Akzenten) enthält.
* **MDVA-31519** (*für Adobe Commerce >=2.3.5 &lt;2.3.6*) - Behebt das Problem mit Wartezeitüberschreitungen beim Gast-Checkout, wenn eine Site-weite Vertriebsregel verwendet wird.
* **MDVA-33281** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem, bei dem in `inventory:reservation:list-inconsistencies` aufgrund eines falschen SKU-Parametertyps ein schwerwiegender Fehler auftritt.
* **MDVA-24201** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, dass Preise erst dann die Preisregel für den geplanten Warenkorb widerspiegeln, wenn sie manuell neu indiziert wurden.
* **MDVA-32694** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Es wird das Problem behoben, dass ein Admin-Benutzer ein Produkt nicht zu einem verhandelbaren Angebot hinzufügen kann, wenn es mit einem nicht standardmäßigen Store verbunden ist.
* **MDVA-33516** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Es wird ein Problem behoben, bei dem die Bearbeitung eines Produktpakets in einer Anforderungsliste zu einem Fehler führt.
* **MDVA-33975** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebt mehrere Probleme bei der Preisberechnung in GraphQL-Anfragen.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass [!DNL PayPal] Abrechnungsberichte nicht wie erwartet unter **Berichte** > **Verkauf** > **[!DNL PayPal]** Abrechnung verfügbar sind.
* **MCP-87** (*für Adobe Commerce >=2.3.1 &lt;2.4.2*) - Verbesserte Indexierungszeit für Produkt- und Aktienindizierer für große Profile.
* **MDVA-33106** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass die neu geplanten Produktänderungen nach Ausführung des Cron-`run` gelöscht werden.
* **MDVA-19391** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Es wird das Problem behoben, bei dem `analytics_collect_data` einen Fehler ausgibt, der auf NULL-Beschreibungseinträge in der `catalog_category_entity_text` zurückzuführen ist.
* **MDVA-20376** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebt das Problem mit dem Fehler *Keine solche Entität mit customerId = 1* in der `exception.log` für angemeldete Kunden nach der Auftragserteilung.
* **MDVA-23764** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebt den Fehler in `JsFooterPlugin.php`, der sich auf die Anzeige dynamischer Blöcke auswirkt.
* **MDVA-13203** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, bei dem der Fehler *Integritätsbeschränkung verletzt search_tmp_ table* nach einer vollständigen Neuindizierung angezeigt wurde.
* **MDVA-23426** (*für Adobe Commerce >=2.3.3 &lt;2.3.5*) - Es wird das Problem behoben, bei dem von Adobe Commerce gesendete Benachrichtigungs-E-Mails einen leeren Text enthalten, bei dem Inhalte als Anhang hinzugefügt werden.
* **MDVA-22150** (*für Adobe Commerce >=2.3.1 &lt;2.3.4*) - Behebt das Problem, dass sich Kunden mit einem konfigurierbaren Produkt im Warenkorb und angewendetem Coupon nicht anmelden können, wenn dieses konfigurierbare Produkt in Admin deaktiviert ist.
* **MDVA-32545** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass Rechnungen beim Erstellen von Bestellungen vom Administrator nicht automatisch versendet werden.
* **MDVA-32714** (*für Adobe Commerce >=2.3.4 &lt;2.4.1*) - Behebt das Problem, dass der Preis der Kundengruppe in der GraphQL-Produktabfrage nicht funktioniert.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Addiert die *Zwischensumme (einschl. Steuer)* Option zu den Preisregelbedingungen.
* **MDVA-31236** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Es wurde das Problem behoben, dass Administratoren mit benutzerdefiniertem Ressourcenzugriff keine 2FA einrichten oder sich anmelden konnten.
* **MDVA-30845** (*für Adobe Commerce >=2.3.5 &lt;2.3.7*) - Behebt das Problem, dass der *Leider sind derzeit keine Angebote für diese Bestellung verfügbar* Fehler angezeigt wird, wenn keine Verbindung zu UPS XML/USPS/DHL hergestellt werden kann und keine andere Versandmethode verfügbar ist.
* **MDVA-32133** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebt das Problem, dass die Mediensammlung in bestimmten Fällen nicht von Page Builder geladen wird.
* **MDVA-12304** (*für Adobe Commerce >=2.3.0*) - Erhöht die maximale Anzahl von Cookies von 50 auf 200.
* **MDVA-32632** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebt das Problem, dass Bestellungen im Zahlungssystem, aber nicht in Adobe Commerce angezeigt werden.
* **MDVA-32449** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || 2,4,0 || >=2.4.1 &lt;2.4.2 mit B2B-Erweiterung*) - Es wird das Problem behoben, bei dem der Auftragsverlauf sehr langsam oder gar nicht geladen wird.
* **MDVA-32739** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, bei dem durch die Aktivierung asynchroner E-Mail-Benachrichtigungen alte Verkaufs-E-Mails versendet wurden.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*für Adobe Commerce 2.3.6, 2.4.1*) - Es wird das Problem behoben, dass die Schaltfläche *Konto erstellen* nach der Korrektur ungültiger Daten im Formular *Neues Kundenkonto erstellen* deaktiviert bleibt.
* **MDVA-31006** (*für Adobe Commerce 2.3.0, 2.3.1*) - Es wurde das Problem behoben, dass doppelte Bestellungen nach der Bestellung mit [!DNL Paypal Express] Payment angezeigt wurden.
* **MDVA-25602** (*für Adobe Commerce 2.3.0*) - Behebt das Problem mit [!DNL PayPal Payflow Pro] Zahlungsmethode und behandelt Cookies standardmäßig im Chrome 80-Browser als `SameSite=Lax`. Die API-Antwort wird zur Kundenanmeldeseite weitergeleitet.

## v1.0.10 {#v1-0-10}

Kleinere Fehlerbehebungen für Patch-Versionen

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Behebt das Problem, dass die Warenkorb-Preisregel mit Coupon nicht über GraphQL gilt, wenn *Festbetragsrabatt für den gesamten Warenkorb* -Aktion verwendet wird.
* **MDVA-30889** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass nach der Fakturierung eines Bundles mit virtuellen und einfachen Produkten als Optionen ein Fehler auftritt.
* **MDVA-31791** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Verbessert die Leistung der Produktseite, wenn Zielregeln oder verknüpfte Produkte verwendet werden.
* **MDVA-31168** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wird das Problem behoben, bei dem die CSV-Datei für den Produktexport nicht angezeigt wird und ein Fehler bei der Speicherzuweisung vorliegt.
* **MDVA-32313** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Es wurde das Problem behoben, dass konfigurierbare Produkte mit falschen Konfigurationsoptionen auf die Wunschliste gesetzt werden konnten.
* **MDVA-31759** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass Produkte beim CSV-Import nicht mit *Dropdown*- und *textarea*-Attributwerten aktualisiert werden.
* **MDVA-32012** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, dass Postleitzahlen in Korea und Argentinien nicht validiert werden können.
* **MDVA-31640** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Behebt das Problem, dass ein Sonderpreis nicht über die REST-API aktualisiert werden kann.
* **MDVA-28651** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 mit B2B-Erweiterung*) - Behebt das Problem, dass beim Laden von verhandelbaren Anführungszeichen über die REST-API Leistungsprobleme auftreten.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*für Adobe Commerce >=2.3.0 &lt;2.4.1 mit B2B-Erweiterung*) - Behebt das Problem, dass im Credit Memo Grid ein falsches Währungszeichen angezeigt wird.
* **MDVA-31295** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass Belohnungspunkte nicht berechnet werden, wenn eine Teilbestellung abgeschlossen ist und Artikel besteuert werden.
* **MDVA-30112** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebt das Problem, dass Adobe Commerce Bestellungen mit dem Status *Ausstehend* als Inkonsistenzen betrachtet, wenn die Anzahl der Bestellungen den *Bunch-Size*-Wert überschreitet.
* **MDVA-31150** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, dass die Guthaben auf Geschäfts-, Kredit- und Geschenkkarten nicht vom GET Invoice Rest API-Aufruf zurückgegeben wurden, als die Rechnung durch einen REST API-Aufruf gebucht wurde und die Bestellung teilweise von Geschäfts-Kredit- und Geschenkkartenkonten bezahlt wurde.
* **MDVA-30963** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Es wird das Problem behoben, bei dem Produkte, für die Filterergebnisse eingestellt wurden, nur Werte enthalten, die für den Bereich *Alle Store-Ansichten* im Admin angegeben wurden, und Produkte mit Werten enthalten, die auf der Store-Ansichtsebene überschrieben wurden.
* **MDVA-29954** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || 2,4,0 || 2.4.2 mit B2B-Erweiterung*) - Es wird das Problem behoben, bei dem die *Neue Unternehmensregistrierungsanfrage* und *Sie wurden mit einem Unternehmen verknüpft* E-Mails von der falschen Adresse gesendet werden.
* **MDVA-28357** (*für Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Ersetzt den Standard-Analyzer durch einen benutzerdefinierten Analyzer mit einem Keyword-Tokenizer für das SKU-Feld im [!DNL ElasticSearch], damit Platzhaltersuchabfragen mit SKUs funktionieren, die einen Bindestrich (“-„) enthalten.

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, bei dem der benutzerdefinierte Bestellstatus nach der Erstellung eines *mit der WebApi in* Verarbeitung) geändert wurde.
* **MDVA-30428** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Es wird das Problem behoben, dass Kunden kein Produkt auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-30594** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, dass eine Bestellung mit mehreren Adressen beim Auschecken nicht gespeichert werden konnte, wenn FPT konfiguriert war.
* **MDVA-29148** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass beim Erstellen eines Produkts über einen API-Aufruf das benutzerdefinierte Produktattribut vom Typ `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (wie Multiselect) nicht seinen Standardwert verwendet, wenn in der Payload kein Wert angegeben wurde.
* **MDVA-30837** (*für Adobe Commerce >=2.3.1 &lt;2.3.5*) - hat eine Konfigurationseinstellung *Steuer in Betrag einbeziehen: Ja/Nein)* Konfiguration der Versandmethode hinzugefügt. Wenn *Steuer in Betrag einbeziehen* auf *Ja* gesetzt ist, wird der Mindestauftragsbetrag als Zwischensumme + Steuer berechnet. Wenn *Steuer in Betrag einbeziehen* auf &quot;*&quot; gesetzt*, wird der Mindestauftragsbetrag als Zwischensumme berechnet
* **MDVA-25028** (*für Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Behebt das Problem, dass Bestellungen, die mit [!DNL PayPal Payflow Pro] aufgegeben werden, nicht den Status „Verdächtiger Betrug“ erhalten, wenn Betrugsfilter ausgelöst werden.
* **MDVA-31224** (*für Adobe Commerce >=2.3.3 &lt;2.3.5*) - Verbessert die Leistung des Vorgangs zur `catalog_product_price` Neuindizierung für Bundle-Produkte.
* **MDVA-31321** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigiert eine leere Seite (Fehler), wenn *Alle anzeigen* ausgewählt ist. [!DNL Elasticsearch] gibt eine große Liste von Produkt-IDs zurück. In diesem Szenario wird die ORDER BY-Klausel in ein falsches SQL-Format konvertiert.
* **MDVA-30815** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Behebt das Problem, dass Adobe Commerce eine leere Seite anzeigt, wenn Sie ändern, wie viele Suchergebnisse auf der Suchergebnisseite angezeigt werden sollen. [!DNL Elasticsearch] zeigt jetzt die Ergebnisse aus Kategorieseiten korrekt an, wenn Sie die Anzahl der pro Seite angezeigten Suchergebnisse ändern.
* **MDVA-30782** (*für Adobe Commerce >=2.3.5 &lt;2.4.2*) - Behebt das Problem, dass der dynamische Block unabhängig von der Warenkorbregel angezeigt wird.
* **MDVA-31021** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass in `module-catalog-import-export/Model/Import/Product/Option.php` Leistungsprobleme auftritt. Wenn `catalog_product_option` Tabelle mehr als ~100.000 Datensätze enthält, dauert die Validierung einer neuen CSV mit einem einzelnen Produkt weniger als 10 Sekunden.
* **MDVA-31007** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Es wurde das Problem behoben, dass benutzerdefinierte Adressattribute auf der Seite mit den Bestelldetails im Bereich Mein Konto und im Backend nicht korrekt angezeigt wurden.
* **MDVA-29389** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem mit Advanced Reporting, wo der `analytics_collect_data` cronjob sagt: *Port muss innerhalb des Host-Parameters konfiguriert werden (wie localhost:3306)*.
* **MDVA-31343** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem mit der entfernten Hauptteilklasse `page-layout-category-full-width`, wenn eine Kategorie geplant ist.
* **MDVA-30945** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, dass beim Aktualisieren von `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` des Warenkorbs eine schwerwiegende Fehlermeldung angezeigt wurde.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*für Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementiert die *Minimum sollte übereinstimmen* Funktionalität und Teilsuche für [!DNL Elasticsearch] Engine. Löst Probleme mit Bindestrichen in Suchanfragen.
* **MDVA-30102** (*für Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Behebt das Problem, dass der Redis-Cache schnell anwächst, da Layout-Caches keine TTL haben.
* **MDVA-30599** (*für Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Es wurde das Problem behoben, bei dem mit der -API erstellte Gastzitate fälschlicherweise als Anführungszeichen für angemeldete Kunden markiert wurden.
* **MDVA-29446** (*für Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Behebt das Problem, dass der Preis für nicht anwendbare Versandmethode während des Checkouts als Null angezeigt wird.
* **MDVA-30357** (*für Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Behebt das Problem, dass beim Generieren einer Sitemap durch Cron falsche Bild-URLs erstellt werden.
* **MDVA-30565** (*für Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Behebt das Problem, dass *Keine solche Entität mit cartid = 0* für einen Gastkunden beim Checkout in der Storefront angezeigt wird, wenn der beständige Warenkorb aktiviert ist.
* **MDVA-29787** (*für Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Behebt das Problem, dass die Zielregel für verwandte Produkte nicht funktioniert, wenn *eine der Bedingungen*, um anzuzeigende Produkte zu definieren.
* **MDVA-30977** (*für Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Behebt das Problem, dass nach der Neuindizierung zufällige Produkte aus Kategorien fehlen.
* **MDVA-28202** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Behebt das Problem, dass die mehrschichtige Navigation konfigurierbare Produkte bei Verwendung von MSI nicht korrekt filtert.
* **MDVA-28300** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Es wurde das Problem behoben, dass die GQL-Anfrage die Preisänderungen aus den Katalogpreisregeln nicht widerspiegelt.
* **MDVA-31006** (*für Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Es wurde das Problem behoben, dass doppelte Bestellungen nach der Bestellung mit [!DNL Paypal Express] Payment angezeigt wurden.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Behebt das Problem mit der mehrschichtigen Navigation, bei der der Wert *Nein* für Produktattribute vom booleschen Typ nicht in die mehrschichtige Navigation aufgenommen wurde, wenn [!DNL Elasticsearch] als Suchmaschine verwendet wurde.
* **MDVA-28191** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebt das Problem, dass bei der Auftragserstellung über den Administrator keine Zahlungsmethoden geladen werden.
* **MDVA-29959** (*für Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 mit B2B-Erweiterung*) - Es wurde das Problem behoben, dass eingeschränkte Admin-Benutzende mit *Firmen*-Berechtigungen kein Unternehmenskonto löschen dürfen.
* **MDVA-30265** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Es wurde das Problem behoben, dass der Link zur Sendungsverfolgung nach der Rechnungserstellung nicht mehr funktioniert.
* **MDVA-28409** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Behebt das Problem, dass der `sales_clean_quotes` Cron-Auftrag mit *Speichermangel* fehlschlägt, wenn die Anzahl der abgelaufenen Anführungszeichen in der Datenbank sehr groß ist.
* **MDVA-30593** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Es wurde das Problem behoben, dass Anführungszeichen, die gemäß der Einstellung für die Angebotslebensdauer abgelaufen sind, nicht bereinigt wurden.
* **MDVA-30107** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Es wird das Problem behoben, bei dem der Store-Umschalter nicht wie erwartet funktioniert, wenn verschiedene Basis-URLs für Store-Ansichten verwendet werden.
* **MDVA-28763** (*für Adobe Commerce >=2.3.2 &lt;2.3.4*) - Es wurde das Problem behoben, dass ein Produktbild dupliziert wurde, nachdem Produktinformationen mithilfe der REST-API mehrmals aktualisiert wurden.
* **MDVA-30284** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Es wurde das Problem behoben, bei dem der Catalog Search-Indexer aufgrund des folgenden *[!DNL Elasticsearch]-Fehlers fehlschlägt: Die Gesamtanzahl der Indexfelder wurde überschritten.*
* **MDVA-29042** (*für Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 mit B2B-Erweiterung*) - Es wurde das Problem behoben, bei dem Katalogberechtigungen nach dem Hinzufügen eines neuen Produkts zum freigegebenen Katalog automatisch in *Zulassen* geändert wurden.
* **MDVA-30428** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Es wird das Problem behoben, dass Kunden kein Produkt auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-28661** (*für Adobe Commerce >=2.3.0 &lt;2.4.2 mit B2B-Erweiterung*) - Es wurde das Problem behoben, bei dem im Abschnitt „Unternehmenskonto für Firmenbenutzer“ ein Fehler ausgegeben wurde, nachdem der Unternehmensadministrator geändert wurde.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*für Adobe Commerce 2.3.1 - 2.3.4-p2*) - Behebt das Problem, dass Cron-Aufträge fehlschlagen, wenn der Datenbankname zu lang ist, was dazu führt, dass Kategorien im Frontend nicht aktualisiert werden.
* **MDVA-30106** (*für Adobe Commerce ^2.3.0*) - Es wurde ein Problem behoben, bei dem beim Auschecken Zahlungen nicht mit dem Fehler *Die Eigenschaft ‚length‘ von null kann nicht gelesen werden* in der JS-Konsole geladen wurden.
* **MDVA-28656** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2* *) - Behebt das Problem, dass sich der Bestellstatus in „Geschlossen“ anstelle von „Abgeschlossen“ ändert, wenn eine Bestellung ohne erforderliche Zahlungsinformationen (z. B. mit 100 % Rabatt) aufgegeben und eine Rechnung für* Bestellung erstellt wurde.
* **MDVA-30209** (*für Adobe Commerce 2.3.0 - 2.3.3-p1*) - Es wurde das Problem behoben, bei dem die Kundengruppe in den Standard geändert wurde, wenn Kunden ihre Kontoinformationen aktualisiert hatten.
* **MDVA-30123** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Es wurde das Problem behoben, dass Attributoptionenbeschriftungen für GraphQL-Abfragen nicht korrekt übersetzt wurden.
* **MDVA-29996** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Es wird das Problem behoben, dass nach der Aktivierung der Kategorienberechtigung die Kategorieseite nicht vom vollständigen Seiten-Cache zwischengespeichert wird.
* **MDVA-30164** (*für Adobe Commerce >=2.3.1 &lt;2.4.2*) - Es wurde das Problem behoben, dass Kundendatensätze nicht aus dem Kundenraster exportiert werden können, wenn benutzerdefinierte Kundenattribute vorhanden sind.
* **MDVA-30444** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Es wurde das Problem behoben, dass für Bestellungen, die mit GraphQL aufgegeben wurden, keine Bestätigungs-E-Mail gesendet wurde.
* **MDVA-30490** (*für Adobe Commerce 2.3.4 - 2.3.5-p2*) - Behebt das Problem, dass der Produktvergleich die Fehlerseite „500“ auslöst, wenn eines der Produkte eine leere Kurzbeschreibung aufweist.
* **MDVA-30232** (*für Adobe Commerce >=2.3.1 &lt;2.4.1*) - Behebt das Problem, dass es nicht möglich ist, neu zu bestellen, wenn die Originalbestellung eine Geschenkkarte enthält.
* **MDVA-29965** (*für Adobe Commerce >=2.3.3 &lt;2.4.0*) - Es wird das Problem behoben, bei dem Kunden beim Hinzufügen eines Produkts zum Warenkorb den Fehler „Ungültiger Formularschlüssel“ erhalten.
* **MDVA-30008** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das B2B-Problem, bei dem es nicht möglich ist, Bestellungen über die Admin-API für ein Produkt zu platzieren, das sich in einem öffentlichen Katalog befindet.
* **MDVA-22469** (*für Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Es wird das Problem behoben, dass Page Builder nach dem Upgrade auf Adobe Commerce 2.3.3 nicht im Admin-Bedienfeld funktioniert und einige JS- und CSS-Dateien nicht geladen werden.
* **MC-35984** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Es wurde das Problem behoben, dass Händler nach dem Erstellen eines Versandtitels für eine Rücksendeautorisierung (RMA) nicht mit Seitenelementen auf der Rückgabeseite interagieren konnten.

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*für Adobe Commerce 2.3.0 - 2.3.4*) - Behebt das Problem mit [!DNL PayPal Payflow Pro] Zahlungsmethode und behandelt Cookies standardmäßig im Chrome 80-Browser als `SameSite=Lax`. Die API-Antwort wird zur Kundenanmeldeseite weitergeleitet.
* **MDVA-26694** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Behebt das Problem, dass Produkt- und Katalog-Caches täglich ablaufen, obwohl sie planmäßig anders ablaufen.
* **MDVA-27825** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Es wurde das Problem behoben, dass der Export großer Datenmengen aufgrund von Speicherleck fehlschlug.
* **MDVA-29085** (*für Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Behebt das B2B-Problem, dass keine erforderlichen neuen Unternehmens-E-Mails gesendet werden, wenn ein Unternehmen durch eine API erstellt wird.
* **MDVA-29344** (*für Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Es wird das Problem behoben, dass Page Builder nach dem Kopieren von Text aus einem Kopfzeilenelement in ein Textelement hängt.
* **MDVA-29835** (*für Adobe Commerce >2.3.1 &lt;2.4.2*) - Es wurde das Problem behoben, dass Geschenkkartenbestellungen zwei Codes anstelle eines Codes enthielten.
* **MDVA-30052** (*für Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Behebt das Problem, dass private Inhalte (lokaler Speicher) nicht korrekt ausgefüllt werden, was zu Leistungsproblemen führte.
* **MDVA-30131** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Behebt das Problem mit der mehrschichtigen Navigation, bei der der Wert *Nein* für Produktattribute vom booleschen Typ nicht in die mehrschichtige Navigation aufgenommen wurde, wenn [!DNL Elasticsearch] als Suchmaschine verwendet wurde.
* **MDVA-35514** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebt das Problem beim Erstellen eines Versandtitels und beim Hinzufügen bestellter Produkte zu einem Paket im modalen Fenster Pakete erstellen .
