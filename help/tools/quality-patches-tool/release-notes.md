---
title: Versionshinweise
description: Erfahren Sie mehr über die verfügbaren Patches für Adobe Systems Commerce und die damit behobenen Probleme.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 7c294a9450be46049090c78074d4fbe722a75119
workflow-type: tm+mt
source-wordcount: '20855'
ht-degree: 0%

---

# Versionshinweise

Das [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) liefert Kontakt Patches, die von Adobe Systems und dem Magento Open Source Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce verfügbar sind, anwenden, wiederherstellen und anzeigen. Sie können Patches auf Adobe Commerce- und Magento Open Source-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.

>[!INFO]
>
>Anweisungen zum Anwenden von Patches auf Adobe Commerce-Projekte finden Sie unter [Anwenden von Patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) . Siehe [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch für Software-Updates, um eine vollständige Liste der veröffentlichten Patches zu überprüfen.

>[!INFO]
>
>Informationen zu [!DNL quality patches], die von der Community zur Magento Open Source erstellt wurden, finden Sie in den [Versionshinweisen](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem Produktbilder nach dem Löschen eines Staging-Updates entfernt werden.
* **ACSD-57086** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen nicht korrekt verarbeitet wurden.
* **ACSD-57588** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem beim Versand einer Bestellung an mehrere Adressen-Trigger ein Fehler während der Verarbeitung der Regions-ID auftrat.
* **ACSD-57643** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem Produkte mit benutzerdefinierten Optionen fälschlicherweise über GraphQL zum Warenkorb hinzugefügt werden.
* **ACSD-57846** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem GraphQL-Produkte, die nach Nullpreisen suchen, keine Ergebnisse aufgrund einer Ausnahme zurückgeben.
* **ACSD-57941** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem Produktoptionen fälschlicherweise dem Admin Store und nicht den zugehörigen Stores zugewiesen wurden.
* **ACSD-58375** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die falsche *[!DNL YouTube API Key]* -Konfiguration beim Hinzufügen eines [!DNL YouTube] -Videos auf der Store-Ansichtsebene einen Fehler verursacht.
* **ACSD-58739** (für Adobe Commerce und Magento Open Source >=2.4.7 &lt;2.4.8) - Behebung des Problems, bei dem bei der partiellen Neuindizierung ein Fehler ausgegeben wurde.
* **ACSD-58446** (for Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where when deleting a team with child users or teams irrespective of their status (inactive), the system provides an uninformative error message not consistent with the UI.
* **ACSD-58054** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem Kunden-Token für inaktive Kunden über API generiert werden können.
* **ACSD-58163** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein *[!UICONTROL Cart Price Rule]* für einen Gastkunden keinen Rabatt auf den entsprechenden *[!UICONTROL Customer Segment]* Warenkorb ohne Couponcode anwendet.
* **ACSD-57045** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem URL-Neuschreibungen dazu führen, dass unendliche Seitenschleifen nach *[!UICONTROL Website Root]* von *[!UICONTROL Hierarchy]* deaktiviert wird.
* Aktualisierte Patches: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-5566** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem die `mergeCart`-Mutation mit einem &quot;*Interner Serverfehler*&quot;in der Antwort [!DNL GraphQL] fehlschlägt, wenn Quell- und ZielWarenkorb mit denselben Bundle-Elementen zusammengeführt werden.
* **ACSD-56546** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem konfigurierbare und Bundle-Produkte als **Nicht auf Lager** angezeigt werden, wenn die **Nicht in der Produktkonfiguration anzeigen** *deaktiviert* ist.
* **ACSD-56635** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn ein Import mit **Kontofreigabe** auf *Global* eingestellt ist.
* **ACSD-56741** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebt die Fehlermeldung &quot;*Versuchen, auf den Array-Versatz vom Typ null zuzugreifen*&quot;, die während `setup:upgrade` angezeigt wird, wenn die Datenbank einen benutzerdefinierten [!DNL MySQL]-Trigger enthält, der nicht mit dem Indexierungsmechanismus und [!DNL MView] verknüpft ist.
* **ACSD-57315** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue when a new transaction is created in [!DNL PayPal Payflow Pro] each time the [!UICONTROL Fetch] button is clicked on the **[!UICONTROL View transaction]** screen in the Admin.
* **ACSD-57337** (für Adobe Commerce >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im Raster **[!UICONTROL Companies]** anzeigen kann.
* **ACSD-57394** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue of incorrect product sorting by multiple sort fields in [!DNL GraphQL].
* **ACSD-57565** (für Adobe Systems Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the **[!UICONTROL Order]** Dashboard zeigt falsche bestellen-Informationen an, bis die Zeitraum aktualisiert wurde. Das Dashboard zeigt nun beim ersten Laden die korrekte bestellen Statistik an.
* **ACSD-57854** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue when product [!DNL GraphQL] Anfragen gaben deaktivierte Kategorien in den Kategorie Aggregationen zurück.
* **ACSD-58008** (für Adobe Systems Commerce >=2.4.5) &lt;2.4.7) - Fixes the issue where updating a scheduled update removed the previous version of a staged item, if no end date was specified.
* Aktualisierte Patches: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die Attribute *[!UICONTROL Used]* und *[!UICONTROL Times Used]* falsche Werte für generierte Gutscheine anzeigen, wenn diese beim Checkout mit mehreren Adressen verwendet werden.
* **ACSD-56760** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem ein auf eine bestimmte Website beschränkter Admin-Benutzer keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt.
* **ACSD-56858** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem Rollenberechtigungen für B2B-Unternehmen fälschlicherweise für einen eingeschränkten Unternehmensadministrator angezeigt werden.
* **ACSD-57074** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem das benutzerdefinierte Attribut *Ja/Nein* mit `attrbute_code`, beginnend mit `price_`, nicht ordnungsgemäß mit der Indizierung funktioniert und Produkte mit solchen Attributen nicht auf der Vorderseite verfügbar sind.
* Aktualisierte Patches: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem die Kategorieseite invalidiert, wenn sich die Bestandsmenge ändert, selbst wenn das Produkt noch auf Lager ist.
* **ACSD-54656** (für Adobe Commerce >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem das unsichtbare Recaptcha beim Checkout fehlschlägt, wodurch verhindert wird, dass eine Bestellung aufgegeben wird.
* **ACSD-55100** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem GraphQL nicht mehr als 10.000 Produkte in den Suchergebnissen zurückgibt.
* **ACSD-56621** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem der aktualisierte Vor- und Nachname nicht im Grußkopfbereich für den Unternehmensadministrator angezeigt wird.
* **ACSD-56842** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die verzögerten Proxys und die verzögerten Proxy-Factories nach Ausführung von `setup:di:compile` fehlen.
* **ACSD-57003** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem der Auftragsstatus in *[!UICONTROL Complete]* geändert wird, anstatt in *[!UICONTROL Processing]* geändert zu werden, wenn eine Bestellung teilweise zurückgezahlt und teilweise versendet wird.
* Aktualisierte Patches: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem ein konfigurierbares Produkt nicht mehr vorrätig ist, wenn eines von zwei untergeordneten Produkten durch eine geplante Aktualisierung deaktiviert wird.
* **ACSD-56616** (für Adobe Systems Commerce und Magento Open Source >=2.4.5) &lt;2.4.6) - Fixes the issue where bundled products display as in stock on the storefront when their simple products are out of stock.
* **ACSD-56515** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem Admin mit Berechtigungen auf Website-Ebene keinen dynamischen Block hinzufügen oder bearbeiten kann.
* **ACSD-56447** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem das Hinzufügen desselben Produkts zum Warenkorb durch parallele REST-Web-API-Anfragen zu zwei separaten Elementen im Warenkorb führte.
* **ACSD-56415** (für Adobe Systems Commerce und Magento Open Source >=2,4,5 &lt;2.4.7) - Fixes the issue where the performance of the partial price indexing is slowed down due to a `DELETE` Abfrage, wenn die Datenbank viele Teilpreisdaten enthält, die indiziert werden müssen.
* **ACSD-54965** (für Adobe Systems Commerce >=2.4.5 &lt;2.4.6) - Fixes the issue where the Visual Merchandising grid does not display the correct stock when a product is assigned to custom stock only.
* **ACSD-52824** (für Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where PayPal Express, Google Pay, and Apple Pay buttons are displayed for company customers when such payment methods are disabled in company settings.
* Aktualisierte Patches: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (für Adobe Systems Commerce und Magento Open Source > = 2,4,6 &lt;2.4.7) - Fixes the issue where a user is redirected to the Admin Dashboard when sorting category products using the **Verschieben von Stock nach unten** Option und der `Invalid security or form key. Please refresh the page` Fehler wird oben auf dem Bildschirm angezeigt.
* **ACSD-56280** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem das Sortieren von Artikeln aus einer Geschenkregistrierung zu einer Ausnahme führt.
* **ACSD-56246** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem Daten aus dem benutzerdefinierten Mehrfachauswahlattribut entfernt werden, wenn ein geplantes Update für ein Produkt aktiv wird.
* **ACSD-56193** (für Adobe Systems Commerce und Magento Open Source >=2.4.2) &lt;2.4.4) - Fixes the issue where the Varnish/Fastly cache is not updated when a scheduled block is used in the category description using Page Builder.
* **ACSD-56158** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the &quot;cart&quot; query returns the total tax value for each tax rule.
* **ACSD-56023** (für Adobe Systems Commerce und Magento Open Source >=2.4.2) &lt;2.4.7) - Fixes the issue where widget content is not updating on the CMS page when cache is enabled.
* **ACSD-55427** (für Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the admin user cannot unassign a product from a shared catalog from the product page in the Admin.
* **ACSD-55352** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where after creating a partial credit memo with customer reward points, the order status changes to Closed and credit memo options disappear from the Admin order page.
* **ACSD-55231** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem Sie mit der Funktion für schnelle Bestellungen keine Produkte zu einem Warenkorb hinzufügen können.
* **ACSD-54283** (für Adobe Commerce >=2.4.3 &lt;2.4.4) - Behebung des Problems, bei dem Produkte/Kategorien, die nicht dem freigegebenen Katalog für den Standard (Allgemeine Gruppe) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind.
* Aktualisierte Patches: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die kanonische Kategorie-URL nach dem Ändern der Kategorie-URL nicht aktualisiert wird.
* **ACSD-53636** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5) - Behebung des Problems, bei dem der reguläre Preis nicht auf Produktlistenseiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen angezeigt wird.
* **ACSD-54885** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems beim Checkout mit mehreren Adressen, wenn der Admin-Benutzer die Funktion *Als Kunde anmelden* verwendet.
* **ACSD-55610** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist.
* **ACSD-55334** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebt Übersetzungen für Beschriftungen durch Übersetzungswörterbücher in der GraphQL-Antwort.
* **ACSD-54739** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem die Bedingung für den Produktstatus nicht auf verwandte Produktregeln angewendet wird.
* **ACSD-53925** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem der Administrator den CMS-Block nicht mit dem Produktkarussell speichern kann, wenn `catalog_product_price` dimensions-mode auf *website* festgelegt ist.
* **ACSD-52714** (für Adobe Systems Commerce und Magento Open Source >=2,4,2 &lt;2.4.7) - Fixes the issue where the date filter is not working in the admin grid when the date format is set as *Y-m-d*.
* **ACSD-55055** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Improves performance of loading product attributes in cart price rules in the shopping cart.
* **ACSD-53790** (für Adobe Systems Commerce >=2.4.6) &lt;2.4.7) - Fixes the issue where Multiple RMAs for a single product can be created via REST API.
* **ACSD-56090** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.5) - Fixes the issue where the GraphQL request is responding with all stores&#39; data rather than the specifically requested store data.
* **ACSD-54983** (für Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where getting the company user UID with GraphQL request is not possible when the user status is set to *[!UICONTROL Inactive]*.
* **ACSD-53309** (für Adobe Systems Commerce- und Magento Open Source >=2.4.2-Beschriftung &lt;2.4.7) - Fixes the issue where tax is not fully applied in the *[!UICONTROL Regular Price]* , wenn die anpassbare Option ausgewählt ist.
* **ACSD-55305** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem das Popup *[!UICONTROL Edit Company User]* auf der Seite **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** mit einem Lader auf dem Bildschirm friert.
* Aktualisierte Patches: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where *[!UICONTROL Recently Viewed]* Produktdaten werden im Geschäft Ansicht nicht ordnungsgemäß aktualisiert.
* **ACSD-54626** (für Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where you can&#39;t create a new purchase order rule (`createPurchaseOrderApprovalRule`) mit dem `NUMBER_OF_SKUS` Attribut über [!DNL GraphQL].
* **ACSD-53845** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the [!DNL MySQL] Verbindungs-Timeout-Problem, wenn `consumer max_messages` = 0.
* **ACSD-54890** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where `aggregate_sales_report_bestsellers_data` verursacht Fehler aufgrund [!DNL MySQL] von `/tmp` Speicherplatzmangel auf der Festplatte.
* **ACSD-55112** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Submit review]* Button kann mehrmals angeklickt werden, ohne [!DNL Google reCAPTCHA v3] Tauglichkeitsprüfung.
* **ACSD-54264** (für Adobe Systems Commerce >=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 &lt;2.4.6 ||=&quot;&quot;>=2.4.6-p2 &lt;2.4.7) - Fixes the issue where the error message *&quot;Sie können das angeforderte Attribut nicht aktualisieren. &lt;/2.4.6>&lt;/2.4.5> Zeilen-ID: Geschäft_id&quot;* wird angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot von einer anderen Geschäft Ansicht auszuchecken.
* **ACSD-54418** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a fixed amount of discount is incorrectly applied to each child product of the dynamically priced bundle.
* **ACSD-55238** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes saving the empty product *[!UICONTROL Meta Description]*.
* **ACSD-54966** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem ein Couponcode mit begrenzter Verwendung pro Kunde nicht wiederverwendet werden kann, wenn die vorherige Bestellung fehlgeschlagen ist.
* **ACSD-54060** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.
* **ACSD-48910** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Es wurde ein Problem behoben, bei dem ein mehreren Quellen zugewiesenes Bundle-Produkt nach der Fakturierung und dem Versand einer Bestellung nicht mehr vorrätig ist, selbst wenn es noch eine Nicht-Nullmenge aufweist.
* **ACSD-55381** (für Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes an internal server error when querying `configurable_product_option_uid` und `configurable_product_option_value_uid` Felder aus einer [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (für Adobe Systems Commerce >=2,4,4-p2 &lt; 2.4.5 || >=2,4,5-p1 &lt; 2.4.6) - Fixes uploading a file on the company registration form and replacing a file for a customer attribute on the storefront.
* Aktualisierte Patches: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (für Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue that occurs in the shopping cart when a product is removed from the shared catalog after it has already been added to the cart.
* **ACSD-53722** (für Adobe Commerce >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem der Preis für die gebündelten Produktoptionen auf 0 USD geändert wird, wenn geplante Aktualisierungen für verschiedene Bereiche aktiv werden.
* **ACSD-53643** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem die Bestellung bei der Bestellung mit deaktivierten oder nicht vorrätigen Produkten einen falschen Gesamtwert aufweist. Dieses Problem wird behoben, indem die Schaltfläche *[!UICONTROL Place Order]* für solche Bestellungen ausgeblendet wird.
* **ACSD-54067** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem ein Produktvideo nicht auf einem Mobilgerät wiedergegeben wird.
* **ACSD-55414** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Verbessert die Leistung, wenn die MariaDB versucht, die EAV-entity_id von der Zeichenfolge in die Ganzzahl zu konvertieren.
* **ACSD-51819** (für Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Behebung des Problems, bei dem mehrere Bestellungen mit derselben Angebots-ID platziert werden können.
* **ACSD-53118** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die *[!UICONTROL Cart Price Rule]* mit dem Couponcode angewendet wird, während das Produkt über ein leeres Attribut verfügt.
* **ACSD-54324** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem die GraphQL-Anforderung &quot;Requisition_lists&quot;keine Paginierungseinstellungen berücksichtigt und alle Ergebnisse zurückgibt.
* Aktualisierte Patches: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (für Adobe Systems Commerce >=2.4.0 &lt;2.4.6) - Fixes the issue where it is not possible to process a B2B Quote submitted for a product with Multiple Assigned Sources.
* **ACSD-54040** (für Adobe Systems Commerce-Feld >=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 &lt;2.4.6) - Fixes the issue where the *[!UICONTROL Created]* ist in Bestelldetails leer, wenn B2B Module aktiviert sind.&lt;/2.4.5>
* **ACSD-54319** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem der Produktpreis im Bericht *[!UICONTROL Product in Cart]* null anzeigt.
* **ACSD-53378** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Verbessert die Ladezeit der Kasse-Seite für Kunden mit großen Adressbüchern.
* **ACSD-52657** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem der Minicart nicht im sekundären Speicher aktualisiert wird, der eine Subdomain verwendet.
* **ACSD-53414** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem eingeschränkte Administratoren CMS-Seiten außerhalb ihres Berechtigungsbereichs anzeigen können.
* **ACSD-5472** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem Kunden eines abgelehnten Unternehmens sich weiterhin authentifizieren können und Kunden eines blockierten Unternehmens und eines abgelehnten Unternehmens weiterhin Bestellungen aufgeben können. Der Patch fügt zusätzliche Validierungen für GraphQL-Endpunkte hinzu.
* **ACSD-52801** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fügt die Option hinzu, eine partielle Übereinstimmung bei der Produktsuche in GraphQL vorzunehmen.
* **ACSD-55004** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem der Validator beim Hochladen einer Importdatei abstürzt, die größer ist als der in `php.ini` konfigurierte Wert.
* **ACSD-54989** (für Adobe Systems Commerce >=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 &lt;2.4.6 ||=&quot;&quot;>=2.4.6-p2 &lt;2.4.7) - Fixes the issue where a company admin cannot place an order when *[!UICONTROL Enable Purchase Orders]* auf *[!UICONTROL Yes]* und *[!UICONTROL Purchase Order]* auf *[!UICONTROL No]* gesetzt.&lt;/2.4.6>&lt;/2.4.5>
* **ACSD-54007** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *&quot;Undefinierter Array-Schlüssel &quot;_Umfang&quot;&quot;* beim Import von Kundendaten.
* **ACSD-55031** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebt den Fehler *Typ &quot;gemischt&quot;kann während der Kompilierung nicht null* sein.
* **ACSD-54961** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem ein eingeschränkter Administrator den Status *Produktprüfung* nicht gebündelt aktualisieren kann.
* **ACSD-55256** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem im Bildregler nur das erste Bild erfolgreich angezeigt wurde.
* Aktualisierte Patches: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem der Bilanzverlauf für Punkte, die belohnt werden, nach Ablauf der Belohnungspunkte falsch berechnet wird.
* **ACSD-53583** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Verbessert die partielle Neuindizierungsleistung für Indizes mit den Kategorien *Kategorieprodukte* und *Produktkategorien*.
* **ACSD-54026** (für Adobe Commerce >=2.4.6 &lt;2.4.7) - behebt eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage für einen nicht autorisierten Benutzer.
* **ACSD-54106** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5) - Behebung des Problems, bei dem die Sortierung von Kategorieprodukten nach Namen für türkische Zeichen mit Akzentzeichen falsch ist.
* **ACSD-52219** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem gespeicherte Admin-Raster-Filter beim häufigen Wechseln zwischen Lesezeichenansichten nicht wie erwartet funktionieren.
* **ACSD-54342** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - behebt eine falsche Fehlermeldung *Fehler in der Datenstruktur: Werte werden beim Import einer CSV-Datei ohne gültige Daten gemischt*.
* **ACSD-54660** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Es wurde das neue Eingabedatum *sort* hinzugefügt, um Kundenaufträge in GraphQL nach `sort_field` und `sort_direction` zu sortieren.
* **ACSD-54776** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem nicht aktivierte *[!UICONTROL Use Default Value]*- und nicht standardmäßige Produktfeldwerte nicht für die zweite Website-, Store- und Store-Ansicht gespeichert werden.
* **ACSD-53998** (für Adobe Commerce und Magento Open Source >=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7) - Behebung des Problems, bei dem ein auf einem **[!UICONTROL Customer Segment]** basierendes **[!UICONTROL Dynamic Block]** nach dem Abmelden von einem Kundenkonto nicht richtig funktioniert.
* **ACSD-53204** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes *The product can&#39;t be saved.* error when making concurrent requests to add images to the product gallery using the `rest/V1/products/<sku>/media` endpoint.
* **ACSD-47657** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Es wurde ein Caching-Mechanismus für AWS-Anmeldeinformationen hinzugefügt. Ein Berechtigungsanbieter verwendet jetzt den Magento-Cache, um von AWS für die EC2-Konfiguration abgerufene Anmeldeinformationen zwischenzuspeichern.
* Aktualisierte Patches: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4) - Behebung des Problems, bei dem Produkte, die einem freigegebenen Katalog zugeordnet sind, nicht auf der Storefront angezeigt werden, wenn ein partieller Index ausgeführt wird.
* **ACSD-54018** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - behebt die Leistungsprobleme mit dem Widget [!UICONTROL Product List] , das in der Widget-Bedingung ein nicht globales Attribut verwendet.
* **ACSD-54111** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem die Produktminiaturbilder nicht auf der Storefront angezeigt werden, wenn das Seitenverhältnis des Wasserzeichenbilds nicht mit dem Produktbild übereinstimmt.
* **ACSD-47669** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - behebt den Fehler *Integrity constraint: 1452 Untergeordnete Zeile kann nicht hinzugefügt oder aktualisiert werden: Eine Fremdschlüsseleinschränkung schlägt beim Import von Produkt-CSV fehl*.
* **ACSD-53347** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die Ausführung des Preisindexers zu viel Zeit in Anspruch nimmt.
* **ACSD-52287** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebt das Problem mit dem falschen Bestellstatus im archivierten Bestellraster, wenn die asynchrone Rasterindizierung aktiviert ist.
* **ACSD-52929** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt das Problem mit redundanten Anforderungen zur Neuindizierung von Standardquellelementen, wenn der Inventarindex im asynchronen Modus konfiguriert ist.
* **ACSD-53824** (für Adobe Systems Commerce und Magento Open Source > = 2.4.4 &lt;2.4.7) - Fixes the issue where `UpdateMultiselectAttributesBackendTypes` Migrationsdaten Patch überschreitet die maximale Datenbanktransaktionsgröße während `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (für Adobe Systems Commerce- und Magento Open Source >=2.4.6-Elemente &lt;2.4.7) - Fixes the issue where caches and indexes are refreshed even when no updates are made to `Inventory_source` per REST-API.
* **ACSD-51884** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the product image cache path becomes incorrect after running the resize command.
* **ACSD-53628** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the CSV sales order report shows incorrect special characters.
* **ACSD-53148** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem zwei parallele Anfragen in GraphQL zum Hinzufügen desselben konfigurierbaren Produkts zum Warenkorb zu zwei separaten Artikeln mit derselben Produkt-SKU im Warenkorb führten.
* **ACSD-52606** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die Fehlermeldung *Ihre Bestellung ist nicht bereit zum Aufheben* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.
* **ACSD-51574** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the image is not updated on the frontend after replacing it with another image with the same name.
* **ACSD-53728** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the product EAV indexer is taking longer to complete.
* **ACSD-53979** (für Adobe Systems Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the JS issue that occurs on the homepage if the welcome message contains a single quote.
* **ACSD-52085** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem ein konfigurierbares Produkt mit einem Sonderpreis im Karussell des Produkts nicht sichtbar ist.
* **ACSD-53795** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems mit dem ungültigen Datentyp im cron-Auftrag `indexer_update_all_views`.
* **ACSD-52143** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem benutzerdefinierte Optionen nach dem Produktimport entfernt werden.
* **ACSD-53750** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebt den Fehler *Beschädigtes Rohr oder geschlossene Verbindung* bei der Neuindizierung mehrerer Threads `catalog_product_price`.
* **ACSD-49843** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem der Link beim Herunterladen des Produkts nicht verfügbar ist, nachdem das bestellte Element automatisch von der Online-Zahlungsmethode in Rechnung gestellt wurde und die Einstellung **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** aktiviert war.
* **ACSD-47054** (für Adobe Commerce >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem die Neuindizierung der Vorschau für alle Stores ausgeführt wird, was zu Langsamkeit führt.
* Added new versions for ACSD-46541, ACSD-47079.
* ACSD-49970-v3 wurde durch ACSD-54095 ersetzt.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt; 2.4.6) - Behebung des Problems, bei dem der Inventarindex alle Caches im Modus &quot;Auf Zeitplan aktualisieren&quot;löscht.
* **ACSD-50887** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die Produktattributeigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* gesetzt werden kann, ohne dass die Option *[!UICONTROL Use in search]* auf *Ja* gesetzt ist.
* **ACSD-51846** (für Adobe Systems Commerce und Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Fixes the *Internal Fehler* tritt auf, weil nicht alle Ebenen der REST-API-Payload validiert werden.
* **ACSD-52906** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem das X-Magento-Vary-Cookie für angemeldete Kunden, die zum selben Kundensegment gehören, falsch gesetzt wurde und bei einigen Seiten zu einer Zwischenspeicherung führte.
* **ACSD-52736** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem eine *Warenkorbpreisregel* mit Anforderungen für konfigurierbare Produktmengen nicht wie erwartet funktioniert.
* **ACSD-47875** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where admin users are not able to add a product to a customer cart from the Admin for a particular store view scope with inventory management.
* **ACSD-53176** (for Adobe Commerce >=2.3.7 &lt;2.4.5) - Fixes the issue where *Related Product Rule* with *is one of* condition does not match products.
* **ACSD-51666** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the error *The session has expired, please login again.* Dies geschieht, nachdem ein Kunde versucht hat, sich anzumelden.
* Neue Versionen für MDVA-39305-v2 wurden hinzugefügt.
* Die Anforderungen für ACSD-19640 wurden aktualisiert.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem die standardmäßige Versandadresse im Checkout-Versandschritt automatisch mit einer zuvor ausgewählten In-Store-Abholadresse gefüllt wird.
* **ACSD-52041** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem die Fehlermeldung *[ERROR] [!DNL Page Builder] 5 Sekunden lang gerendert wurde, ohne Sperren zu veröffentlichen.* wird beim Speichern Inhalte Bearbeiten mit [!DNL Page Builder]Chrom Browser angezeigt.
* **ACSD-52095** (für Adobe Systems Commerce und der Wert Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where the `manage_stock` wurde in der CSV Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt.
* **ACSD-51358** (für Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where removing a scheduled update without an end date leads to removing other scheduled updates for the same entity.
* **ACSD-48070** (für Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where editing a scheduled update triggers an exception.
* **ACSD-51890** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Submit review] Button kann mehrmals angeklickt werden, ohne [!DNL Google reCAPTCHA] dass v3 Tauglichkeitsprüfung.
* **ACSD-51984** (für Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where unchecked *[!UICONTROL Use Default Value]* und *[!UICONTROL non-default product field]* Werte werden nicht für die zweite Website, Geschäft und Geschäft Ansicht gespeichert.
* **ACSD-52398** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *Die angeforderte Menge ist nicht verfügbar* , der auftritt, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren.
* **ACSD-52786** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem eine Katalogregelbedingung *SKU* für alle Produkte gilt, die mit der angegebenen SKU beginnen.
* **ACSD-52921** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem ein interner Fehler auftritt, wenn von GraphQL Warenkorbdetails angefordert werden, wenn ein nicht vorrätig konfigurierbares Produkt im Warenkorb vorhanden ist.
* **ACSD-51683** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem eine anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
* **ACSD-52133** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
* **ACSD-52202** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem die verkaufbare Menge des Standardbestands fälschlicherweise auf 0 geändert wird, wenn ein nicht standardmäßiges Lager bei Auftragserfüllung auf 0 qty geändert wird.
* **ACSD-51265** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - behebt das Problem mit der Neuindizierungsleistung von `catalog_product_price`, wenn zu viele gebündelte Produkte im System vorhanden sind.
* **ACSD-52831** (für Adobe Systems Commerce ist >=2.3.7 &lt;2.4.7) - Fixes the issue where customers cannot place negotiable quote orders when [!DNL Google reCAPTCHA v3 Invisible] aktiviert.
* **ACSD-51845** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where subsequent products with tier prices and different attribute sets cannot be updated via asynchronous bulk REST API.
* **ACSD-52815** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the input for the quantity field of a non-default source supports only up to 6 digits, unlike 8 for a default stock.
* **ACSD-51149** (für Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where Scheduled ImportExport with enabled Catalog Permissions invalidates indexers and then cache flushes by cron.
* **ACSD-50815** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where decimal quantity for a simple product cannot be used for a new Bundled product option.
* Aktualisierte Versionen für ACSD-47803.
* Der Titel für ACSD-51892 wurde aktualisiert.
* ACSD-51379 aktualisiert.
* ACSD-49970-v2 wurde aktualisiert.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem ein Admin-Benutzer nach Auswahl einer Store-Ansicht beim Erstellen einer neuen Bestellung in Admin nicht ordnungsgemäß umgeleitet wird.
* **ACSD-50813** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem Admin keine gebündelten Produkte hinzufügen konnte, die einen Schrägstrich in der SKU enthielten, wobei die Funktion [!UICONTROL Add Products by SKU] zur Admin-Bestellung hinzugefügt wurde.
* **ACSD-51630** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem eine große Anzahl von Systemnachrichten das Herunterladen von Administrationsseiten verlangsamt.
* **ACSD-51853** (für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem kopierte Textstile bei Verwendung von [!UICONTROL Page Builder] nicht angewendet werden.
* **ACSD-52160** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Behebung des Problems, bei dem das Ergebnis der Produktvalidierung für die Warenkorbpreisregel nicht ordnungsgemäß anhand der Regelbedingung &#39;Wenn ein Artikel im Warenkorb mit Alle/Jede dieser Bedingungen gefunden/NICHT GEFUNDEN wurde&#39; ausgewertet wurde.
* **ACSD-51636** (für Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the company admin cannot add new users from the customer account section despite having all necessary roles and permissions.
* **ACSD-51739** (für Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where an error is returned when the `structure_id` wird in einem CompanyTeam GraphQL-Anfrage angefordert.
* **ACSD-51857** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the slow performance of the `aggregate_sales_report_bestsellers_data` Cron-Bericht zu großen Verkäufen_bestellen- und `sales_order_item` Datenbanktabellen war auf die Art und Weise zurückzuführen, wie die Hauptdaten Abfrage geschrieben wurden.
* **ACSD-48448** (für Adobe Systems Commerce- und Magento Open Source >=2.4.2-Tabelle &lt;2.4.7) - Fixes the issue where there is a race condition issue happening during the order cancellations, which causes a duplicated entry in the `inventory_reservation` .
* **ACSD-52689** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.6) - Behebung des Problems, bei dem Bilder nicht mit der REST-API in den Amazon S3-Speicher hochgeladen werden können.
* **B2B-2674** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fügen Sie der GraphQL-Abfrage 1customAttributeMetadata1 eine Caching-Funktion hinzu.
* Es wurden neue Versionen für ACSD-44938 hinzugefügt.
* Anforderungen für ACSD-46988 hinzugefügt.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.5) - Fixes the database rollback command for a case when the DB dump contains triggers and a *Trennzeichen-SQL-Befehl* ).
* **ACSD-50512** (für Adobe Systems Commerce >=2,4,5 &lt;2.4.7) - Fixes the *Fehler: Die herunterladbare verknüpfen bezieht sich nicht auf das Produkt. Überprüfen Sie die verknüpfen und versuchen Sie es erneut.* Fehler, der auftritt, wenn das Beginn Datum für ein herunterladbares Produkt-Staging-Update aktualisiert wird.
* **ACSD-50949** (für Adobe Systems Commerce und Magento Open Source >=2.4.2) &lt;2.4.7) - Fixes the issue where the price filter in Advanced search doesn&#39;t return proper results when used along the SKU filter.
* **ACSD-51645** (für Adobe Systems Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the error thrown when saving a new Cart Price Rule if the extension `Magento_OfflineShipping` ist deaktiviert.
* **ACSD-50895** (für Adobe Commerce >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem [!DNL Google Analytics] 3 GTM-Tags nicht ausgelöst werden, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist.
* **ACSD-51102** (für Adobe Commerce >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht richtig indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.
* **ACSD-50368** (für Adobe Commerce und Magento Open Source >= 2.4.3 &lt;2.4.5) - Behebung des Problems, bei dem die `group_id` des Kunden ignoriert wird, wenn ein Kunde über die asynchrone REST-API oder asynchrone Bulk-REST-API erstellt wird.
* **ACSD-51497** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem ein Kunde eine Katalogseite nicht nach benutzerdefiniertem Attribut des Dropdown-Typs sortieren kann.
* **ACSD-51408** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt; 2.4.7) - Behebung des Problems, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Backordered]* festgelegt ist.
* **ACSD-51735** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Ordered]* festgelegt ist, wenn der Produktbestand *0* ist.
* **ACSD-51792** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem eine Seite kein Impressionsereignis aufweist, wenn [!DNL Google Tag Manager] 4 aktiviert ist.
* **ACSD-51471** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein Admin-Benutzer keine geplante Aktualisierung für ein gebündeltes Produkt speichern kann, das ein einfaches Produkt verwendet, das selbst über eine geplante Aktualisierung verfügt.
* **ACSD-51700** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the error that happens when switching store views on a downloadable product edit page in the admin.
* **ACSD-51120** (für Adobe Systems Commerce >=2,3,7 &lt;2.4.3) - Fixes the issue where GraphQL GET requests cache is not cleared for CMS pages that contain CMS blocks that are updated via a staging update.
* **ACSD-51240** (für Adobe Systems Commerce >=2.4.4) &lt;2.4.6) - Fixes the issue where the uploaded file is missing if the registration is done via the company registration form.
* **ACSD-51907** (für Adobe Commerce >=2.4.2 &lt;2.4.3) - Behebung des Problems, bei dem ein eingeschränkter Administrator kein Kreditmemo mit Offline-Rückerstattung erstellen kann.
* **ACSD-52148** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem die [!DNL Google V3 reCAPTCHA] Admin-Anmeldung gelegentlich fehlschlägt.
* **ACSD-51431** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem der Indexstatus *working* lautet, selbst wenn im Changelog keine neuen Einträge vorhanden sind.
* **ACSD-51892** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Leistungsproblems, bei dem Konfigurationsdateien mehrmals geladen werden.
* Veraltete ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem die [!UICONTROL Page Builder's] Mehrfachfehler das Speichern eines Produkts ohne Inhaltsberechtigungen durch den Administrator verhindern.
* **ACSD-51305** (für Adobe Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Behebung des Problems, bei dem konfigurierbare nicht vorrätige untergeordnete Produkte in der GraphQL-Antwort nicht verfügbar sind.
* **ACSD-50621** (für Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where [!UICONTROL Tier Prices] für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar, wenn versucht wird, sie in einer Umgebung mit mehreren Websites zu bearbeiten.
* **ACSD-51041** (für Adobe Systems Commerce und Magento Open Source >=2,3,7 &lt;2.4.0 ||=&quot;&quot;>=2,4,1&lt;2.4.6) - Improves performance of price indexer.&lt;/2.4.0>)
* **ACSD-51379** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where changes made to page text content via [!UICONTROL Page Builder] werden nicht gespeichert.
* **ACSD-49480** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where only one cart price rule is applied to the cart.
* **ACSD-51230** (für Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where the gift card account is deleted when a partial refund of a simple product is processed from an order.
* **ACSD-51238** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the inventory source is removed when updating configurable products and editing the price.
* **ACSD-50794** (für Adobe Systems Commerce >=2.4.1) &lt;2.4.7) - Fixes the issue where the gift message or gift wrapping details are not updated in the database when removing it through GraphQL.
* **ACSD-51528** (für Adobe Systems Commerce und Magento Open Source >=2,4,5 &lt;2.4.7) - Fixes the issue where the *x_forwarded_for* Spalte enthält NULL-Werte in der *Sales_bestellen-Tabelle* .
* **ACSD-50849** (für Adobe Systems Commerce >=2.4.4 &lt;2.4.6) - Fixes the issue where adding a new product to the category after clearing the cache results in a mismatch of positions and selections of the  existing products.
* **ACSD-51294** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where GTM/GA price, quantity, tax, shipping, and revenue are sent as a string to [!DNL Google Analytics] und GTM.
* **ACSD-51204** (für Adobe Systems Commerce und Magento Open Source >=2.4.3) &lt;2.4.7) - Fixes the issue where a fully sold product doesn&#39;t return back in stock after creating a credit memo.
* **ACSD-51291** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.4-p4 ||=&quot;&quot;>=2.4.5 &lt;2.4.5-p3) - Fixes the issue where restricted admin with access to one website can add images/videos to the product assigned to multiple websites.&lt;/2.4.4-p4>
* Neue Versionen für ACSD-50336 wurden hinzugefügt.
* Patches ACSD-49970 ersetzt.

## Version 1.1.31 {#v1-1-31}

* **ACSD-50345** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.4 ||=&quot;&quot;>=2.4.4-p1 &lt;2.4.6) - Fixes the issue where Recaptcha v2 does not reload after submitting a failed payment.&lt;/2.4.4>
* **ACSD-50817** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Optimizes Cron job `sales_clean_quotes` für eine schnellere Ausführung.
* **ACSD-49392** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem der Auftragsstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt zu &quot;geschlossen&quot;geändert wurde.
* **ACSD-51036** (für Adobe Systems Commerce- und Magento Open Source >=2.4.4-Tabelle &lt;2.4.5) - Fixes the issue where race conditions during concurrent REST API calls result in an overwrite of shipping status information in the [!UICONTROL Items Ordered] .
* **ACSD-50858** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Improves performance for loading banners contents.
* Neue Versionen für MDVA-39305-v2, ACSD-45169 hinzugefügt.
* Aktualisierte Patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (für Adobe Commerce und Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Behebung des Problems, bei dem E-Mails zur Produktwarnung nicht gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird.
* **ACSD-50367** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem der Export von Kundenadressen bei der Erstellung eines aus mehreren Markierungen bestehenden Kundenadressattributs ohne Werte nicht funktioniert.
* **ACSD-49877** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem die automatische Videowiedergabe auf einem Mobilgerät nicht funktioniert [!DNL Safari], wenn das Video direkt mit einer Remote-Videodatei und nicht mit einem Streaming-Dienst verknüpft ist.
* **ACSD-50165** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebt den Fehler *Die Datei kann nicht gelöscht werden. Warnung!unlink: Keine solche Datei oder kein Verzeichnis* beim Löschen des JS/CSS-Cache vom Administrator.
* **ACSD-49737** (für Adobe Systems Commerce und Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Fixes the issue where a coupon is incorrectly marked as used after a failed card payment.
* **ACSD-50814** (für Adobe Systems Commerce und Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where an admin user is not able to create a credit memo.
* **ACSD-50116** (für Adobe Systems Commerce und Magento Open Source >=2.3.7) &lt;2.4.7) - Fixes the issue where an admin user cannot create a URL rewrite for subcategories level 3 or lower.
* **ACSD-49513** (für Adobe Systems Commerce und Magento Open Source >=2.4.3) &lt;2.4.5) - Fixes the issue where remote storage synchronization fails because of 0-byte files.
* **ACSD-46683** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the shipping price shows *Noch nicht berechnet*.
* **ACSD-49129** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem das Attribut *[!UICONTROL content]* (base64-Bildcode) in den API-Antworten für Produktmedien nicht zurückgegeben wird.`rest/V1/products/sku/media`
* **ACSD-50276** (für Adobe Commerce >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem das Formular zur Kundenregistrierung auf der Storefront nicht funktioniert, wenn ein Kundenattribut mit mehreren Auswahlen erstellt wird.
* **ACSD-50527** (for Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the error that occurs when saving a page with an empty dynamic block.
* **ACSD-49973** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5) - Improves performance of fetching bundled products through GraphQL.
* **ACSD-51114** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a random product disappears from large catalogs when asynchronous indexing is enabled. Verbessert die Leistung der asynchronen Neuindizierung für große Kataloge.
* **B2B-2598** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.7) - Fügen Sie den GraphQL-Abfragen [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] und [!UICONTROL storeConfig] eine Zwischenspeicherungsfunktion hinzu.
* Es wurden neue Versionen für MDVA-42806, ACSD-48627, ACSD-46815 hinzugefügt.
* Die Patchmetadaten für ACSD-49773, ACSD-47179, ACSD-48300 wurden aktualisiert.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem eine gebrauchsfertige E-Mail von der API gesendet wird, wenn die Bestellung nicht abgeholt werden kann.
* **ACSD-49822** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Aktualisierungen auf der Seite [!UICONTROL Requisition List] nicht auf dem [!UICONTROL Print Requisition List] angezeigt werden.
* **ACSD-48771** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue with upgrading the column-block content type from older [!DNL Page Builder] versions.
* **ACSD-49464** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Rechnungen, Sendungen und Credit Memos nicht aus dem Archiv verschoben werden, wenn die orderId unterschiedlich ist.
* **ACSD-49773** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird.
* **ACSD-49748** (für Adobe Commerce >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Einladungen nicht gesendet werden können.
* **ACSD-49502** (für Adobe Commerce >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem der herunterladbare Link nicht ordnungsgemäß aktualisiert wird, nachdem eine Staging-Aktualisierung auf das herunterladbare Produkt angewendet wurde.
* **ACSD-49527** (für Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL company roles don&#39;t display pagination correctly.
* **ACSD-49706** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem der Standardwert für ein visuelles Musterattribut gespeichert wird, wenn kein Wert ausgewählt ist.
* **ACSD-49835** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the Use default checkbox value is not saved correctly on a store level for a multi-select attribute.
* **ACSD-49898** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the products grid throws an exception when a bundled product has a special price that exceeds 1000.
* **ACSD-50234** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.5) - Fixes the issue with the wrong customer name in the confirmation email if placing an order with [!DNL PayPal].
* **ACSD-49960** (für Adobe Systems Commerce und Magento Open Source >=2.4.5) &lt;2.4.7) - Fixes the issue where filtering by date does not work for the customer order grid.
* **ACSD-49849** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where customer email was replaced with [!DNL PayPal] E-Mails, wenn eine bestellen über GraphQL platziert wird [!DNL PayPal Express] .
* **ACSD-49839** (für Adobe Systems Commerce > = 2,3,7 &lt;2.4.7) - Fixes the issue where Shared Catalog Pricing and structure throws an error in Admin when products have single or double quotes in SKU.
* **ACSD-49970** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes incorrect handling of GraphQL errors when [!DNL New Relic] Berichte ist aktiviert.
* **ACSD-50260** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where GraphQL product search results are limited to 10,000 results only.
* **ACSD-48813** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the search is not showing relevant results based on the search weight of the attributes.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (für Adobe Systems Commerce und Magento Open Source >=2.3.7) &lt;2.4.3) - Fixes the issue where a catalog price rule created based on the Yes/No attribute does not consider the selected scope.
* **ACSD-47704** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem das gebündelte Produkt nur den Preis für Lagerprodukte anzeigt.
* **ACSD-49370** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the *Datum Zeit* Produktattribut hat einen *FilterMatchTypeInput-Typ* in GraphQL Schema.
* **ACSD-48807** (für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.7) - Fixes the issue where customer Product Reviews are not filtered by storeview via GraphQL.
* **ACSD-49433** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the default amount is shown as subtotal in the cart for gift card with an open amount.
* **ACSD-48866** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where an error occurs when requesting RSS feed for categories.
* **ACSD-48784** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the customer segment prices are incorrectly cached between customer groups.
* **ACSD-48857** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a user is unable to save changes after editing with Page Builder.
* **ACSD-49065** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem Anführungselemente im Admin nicht sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.
* **ACSD-49179** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Behebung des Problems, bei dem im Bestellbericht falsche Beträge angezeigt werden, wenn verschiedene Währungen für verschiedene Geschäfte verwendet werden.
* **ACSD-49286** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem ein Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.
* **ACSD-49574** (für Adobe Systems Commerce >=2.4.4 &lt;2.4.7) - Adds functionality to support Gift Card product updates in a cart via GraphQL.
* Aktualisiert Patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (für Adobe Systems Commerce >=2.4.1 &lt;2.4.7) - Fixes the issue where the default shipping address is used instead of a new one when placing an order using a negotiable quote.
* **ACSD-48059** (für Adobe Systems Commerce >= 2,3,7 &lt;2.4.7) - Fixes the issue where merchants cannot save the &quot;[!UICONTROL Match product by rule]&quot; im Kategorie.
* **ACSD-48216** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Behebung des Problems, bei dem [!UICONTROL AUTO_INCREMENT] der Tabelle [!UICONTROL inventory_source_item] beim [!UICONTROL UPDATE] -Vorgang zunimmt.
* **ACSD-47908** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Behebt den Fehler &quot;Ein Wert kleiner oder gleich 0 wird erwartet&quot;bei der Auswahl der Quelle und der Menge im Versandschritt beim Checkout.
* **ACSD-49497** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem eine Bestellung nach dem Versand im Verarbeitungsstatus verbleibt und eine teilweise Rückerstattung erfolgt.
* **ACSD-48694** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Behebung des Problems, bei dem der Fehler &quot;Ungültige Statusänderung angefordert&quot;verhindert, dass ein Kunde eine Bestellung aufgibt.
* **ACSD-49013** (für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.7) - Behebung des Problems, bei dem die E-Mail-Bestätigung beim Erstellen von Kunden mit Bulk API nicht in das Gebietsschema der Website übersetzt wird.
* **ACSD-48164** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebung des Problems, bei dem ein eingeschränkter Administrator keinen Wert auf Website-Ebene speichern kann.
* **ACSD-48404** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem &quot;Kategoriepaginierung merken = Ja&quot;beim Drücken der Zurück-Schaltfläche des Browsers einen Fehler verursacht.
* **ACSD-48634** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Behebt JS-Fehler auf einer Staging-Aktualisierungsseite, wenn &quot;[!UICONTROL Google Analytics Content Experiments]&quot; aktiviert ist.
* **ACSD-49042** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann.
* Aktualisierte Patches: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (für Adobe Systems Commerce und Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Fixes the issue where price drop notifications are not always sent due to application-level caching.
* **ACSD-48661** (für Adobe Systems Commerce und Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where if the company&#39;s credit limit is larger than 999, the comma separator prevents the saving of the company due to a validation error.
* **ACSD-48773** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the reward points email template is taken from the wrong store.
* **ACSD-48587** (für Adobe Systems Commerce und Magento Open Source >=2.3.7) &lt;2.4.7) - Fixes the issue where HTML special characters in the products widget matching rules prevent them from displaying matching products.
* **ACSD-48212** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem der Produktimport das Produkt der falschen Quelle zuordnet.
* **ACSD-47988** (für Adobe Commerce und Magento Open Source >=2.3.7 &lt;2.4.6) - Behebung des Problems, bei dem beim Produktexport HTML-Tags aus der Produktbeschreibung des Seitenaufbaus entfernt werden.
* **ACSD-48366** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem das Produktbild nicht in der E-Mail-Vorlage &quot;Zurück zu Lager&quot;angezeigt wird.
* **ACSD-48417** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.7) - Behebung des Problems, bei dem ein SQL-Fehler angezeigt wird, nachdem eine Produktplanänderung erstellt und ein anderes Produkt gespeichert wurde.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (für Adobe Systems Commerce und Magento Open Source >=2.4.5) &lt;2.4.6) - Fixes the issue where product price reindex is not working if the bundle product is not assigned to any website.
* **ACSD-48262** (für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where products are not visible on the frontend when &quot;Allow All Products Per Page&quot; setting is set to Yes.
* **ACSD-48293** (für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.4) - Fixes the issue where the composite products go out of stock when the child products that were sold out are returned to stock.
* **ACSD-47520** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where customers lose reward points when a credit memo is created.
* **ACSD-48044** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where applying multiple gift cards to a single order with multi-shipping prevents orders from being placed.
* **ACSD-48300** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem eine Rückgabe nicht erstellt werden kann, wenn das konfigurierbare Produkt entfernt wird.
* **ACSD-47910** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebt das Problem fehlender Bestellungen, Rechnungen, Sendungen und Kreditkarten im jeweiligen Entitätsraster.
* **ACSD-47292** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem nicht vorrätige gebündelte Produkte in der GraphQL-Antwort nicht verfügbar sind, wenn &quot;Nicht vorrätige Produkte anzeigen&quot;auf &quot;Ja&quot;gesetzt ist.
* **ACSD-48234** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem das Katalogsuchergebnis eine falsche Kategorieelementanzahl anzeigt, wenn die Option &quot;Nicht auf Lager anzeigen&quot;aktiviert ist.
* **ACSD-48313** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5) - Behebung des Problems, bei dem die Spalte &quot;konfigurierbare Varianten&quot;nicht analysiert wird, wenn der Attributwert ein Komma enthält. Derselbe Parsing-Algorithmus wird für &quot;additional_attributes&quot;verwendet.
* **ACSD-48627** (für Adobe Commerce und Magento Open Source >=2.4.5 &lt;2.4.6) - Behebung des Problems, bei dem das konfigurierbare Produkt &quot;Nicht vorrätig&quot;beim Senden einer GraphQL-Anfrage zum Abrufen von Details zum Warenkorb einen Fehler verursacht.
* Aktualisierter Patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Behebung des Problems, bei dem SEO-freundliche URLs nicht für Produkte generiert werden, bei denen die Attribute *url_key* auf der Store-Ansichtsebene überschrieben wurden.
* **ACSD-46865** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem das Raster &quot;Versand&quot;und &quot;Credit Memo&quot;bei Aktivierung der asynchronen Indizierung nicht gefüllt wird.
* **ACSD-47004** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where VAT is not applied to a billing address without a VAT ID.
* **ACSD-47803** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where out-of-stock configurable product swatches are displayed as available.
* **ACSD-47137** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Improves the loading speed of the image gallery when the pub/media folder is very big.
* **ACSD-46770** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where admin order emails are sent even when the *E-Mail-bestellen-Bestätigung* ist deaktiviert.
* **ACSD-47955** (für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where GraphQL does not display the cart discount correctly.
* **ACSD-46617** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem die Schaltfläche *Weiter zum Checkout* ausgegraut ist, selbst wenn die Zwischensumme größer ist als der konfigurierte *Mindestauftragsbetrag*.
* **ACSD-47079** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5) - Behebung des Problems, bei dem der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus von Unterprodukten über die REST-API-POST /rest/V1/inventory/source-items ändert.
* **ACSD-47336** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fehlerbehebungen *Etwas ist schiefgelaufen.* -Fehler beim Verwerfen von Benachrichtigungen in Commerce Admin.
* **ACSD-47559** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the Preview Email Template area is not fully visible.
* **ACSD-47920** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where orders can be placed via Rest API as a guest user even when the *Gast-Checkout* zulassen ist deaktiviert.
* Ersetzte Patches: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where an admin with restricted access to a specific scope cannot delete product reviews.
* **ACSD-47107** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.5) - Fixes the issue where the Catalog Price Rule discount is applied to custom product options.
* **ACSD-47232** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where coupons with total weight conditions cannot be applied in the Admin.
* **ACSD-46519** (für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.6) - Fixes the issue where the GraphQL categoryList request returns an incorrect product_count for an anchor category.
* **ACSD-47027** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes a slow updateCompanyRole GraphQL request.
* **ACSD-47666** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) -=&quot;&quot; fixes=&quot;&quot; the=&quot;&quot; issue=&quot;&quot; where=&quot;&quot; the=&quot;&quot; filter=&quot;&quot; function=&quot;&quot; does=&quot;&quot; not=&quot;&quot; work=&quot;&quot; in=&quot;&quot; the=&quot;&quot; admin=&quot;&quot;> Systemberechtigungen >> Benutzerrollen > einem Rolle > Rollenbenutzerraster.&lt;/2.4.6)>
* **ACSD-47497** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the Services tab is not visible in the Configuration under the Admin.
* Aktualisiert Patch: ACSD-47743.
* Ersetzte Patches: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.3) - Fixes the _Der Versuch, auf den Array-Offset beim Wert des Typs bool_ error zuzugreifen, wenn auf bestimmte nicht existierende Kategorie Pfade für bekannte Produkte unter PHP 7.4 zugegriffen wird.
* **ACSD-47332** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where cron fails with an error that is only reported when running between 00:00 and 00:59 UTC.
* **ACSD-47280** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem das Deaktivieren der freigegebenen Katalogfunktion in einem bestimmten Bereich nicht ordnungsgemäß funktioniert.
* **ACSD-47106** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden kann.
* Aktualisiert Patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where a user gets an error when assigning a large number of product sources.
* **ACSD-46856** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) -=&quot;&quot; improves=&quot;&quot; performance=&quot;&quot; updating=&quot;&quot; tier=&quot;&quot; prices=&quot;&quot; via=&quot;&quot; system=&quot;&quot;> Konfiguration > Importieren > Erweitert Preise.&lt;/2.4.6)>
* **ACSD-46541** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4) - Behebung des Problems, bei dem ein Admin-Benutzer kein Credit Memo erstellen kann, wenn ein Bestellelement gelöscht wird.
* **ACSD-46581** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem die geschätzte Steuersumme nach Auswahl eines Landes im Warenkorb nicht aktualisiert wird.
* **ACSD-46618** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem das Produktlisten-Widget falsche Preise im Cache für einen angemeldeten Kunden anzeigt.
* **ACSD-46674** (für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Behebung des Problems, bei dem benutzerdefinierte Optionen eines Bildtyps als HTML in E-Mails von Kunden angezeigt werden.
* **ACSD-46988** (für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6) - Behebung des Problems, bei dem die GraphQL-API-Anfrage &quot;currency&quot;NULL-Werte für eine benutzerdefinierte Währung zurückgibt.
* **ACSD-47076** (für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.5) -  Fixes the issue where Vimeo videos cannot be played on the storefront.
* **ACSD-45071** (für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4) - Fixes the issue where the default source is added to the product during import.
* **AC-3023** (für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.6) - Update DHL scheme to latest version 10.0.
* Aktualisierte Patches: MDVA-42584.
* Ersetzte Patches: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem ein Benutzer einen falschen Bestellstatus erhält, wenn er mithilfe des Store-Guthabens zurückerstattet wird.
* **ACSD-46703** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6*) - Behebung des Problems, bei dem es nicht möglich ist, benutzerdefinierte Optionen auf eine Produktbearbeitungsseite zu ziehen und dort abzulegen.
* **ACSD-44851** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6*) - Behebung des Problems, bei dem eine Kategorie mit Unterkategorien weder geöffnet noch erweitert werden kann.
* **ACSD-46815** (*für Adobe Systems Commerce und Magento Open Source >=2.4.5 &lt;2.4.6*) - Behebt das Problem, dass Kategorie Baum-Anfrage auf 20 Kategorien beschränkt ist.
* **ACSD-45675** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.6*) - Behebung des Problems, bei dem beim Produktexport Kategorienamen aus dem Bereich *Standardspeicheransicht* verwendet werden.
* **ACSD-46869** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.6*) - Behebung des Problems, bei dem ein konfigurierbares Produkt in einem Warenkorb nicht über eine *PUT REST API* -Anfrage aktualisiert wird, ohne die Produktmenge zu ändern.
* **MDVA-42768-V2** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem für konfigurierbares Produkt der Regelpreis als *0* angezeigt wird, wenn *Nicht auf Lager anzeigen* *Ja* ist.
* Aktualisiert: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Veraltete Patch: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) – Behebt das Problem, dass Kategorie Baum-Anfrage auf 20 Kategorien beschränkt ist.
* **ACSD-45781** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.2*) - Behebt das Problem, dass das Feld Geschäft vorderen suchen auf Mobilgeräten nicht angezeigt wird.
* **ACSD-46192** (*für Adobe Systems Commerce und Magento Open Source >=2.3.6*&lt;2.4.5) – Behebt das Problem bei der Verwendung des `async/bulk/V1/configurable-products/bySku/options` Endpunktes.
* **ACSD-46404** (*für Adobe Systems Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebt das Problem, dass sich ein Administrator nach dem Upgrade auf 2.4.4 User nicht anmelden kann.
* Aktualisierte Patches: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, dass eine GraphQL-Produktmutation für eine bestimmte Geschäft alle konfigurierbaren Varianten zurückgibt, einschließlich derjenigen, die nicht dem angeforderten Geschäft zugewiesen sind.
* **ACSD-46146** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.6*) - Behebt das Problem, bei dem zwei bestellen Bestätigungs-E-Mails gesendet werden, nachdem eine bestellen vom Administrator platziert wurde.
* **ACSD-45255** (*für Adobe Systems Commerce >=2.4.3 &lt;2.4.6*) – Behebt eine Ausnahme auf der Low-Stock Melden Seite für eine eingeschränkte Admin-User.
* **ACSD-45488** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.6*) – Behebt das Problem, bei dem ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch an In Stock zurückgegeben wird.
* **ACSD-45754** (*für Adobe Systems Commerce und Magento Open Source >=2.3.1 &lt;2.4.6*) - Behebt das Problem, dass Prämienpunkte nicht hinzugefügt werden, nachdem ein Coupon auf die Warenkorb angewendet wurde.
* **ACSD-45849** (*für Adobe Systems Commerce >=2.4.3 &lt;2.4.4*) – Behebt das Problem, bei dem Video Metadaten nach dem Aufspielen eines Staging-Updates verloren geht.
* **ACSD-45257** (*für Adobe Systems Commerce und Magento Open Source >=2.3.4 &lt;2.4.4*) - Behebt das Problem, dass GraphQL einen Warenkorb Rabatt nicht korrekt anzeigt.
* **ACSD-44938** (*für Adobe Systems Commerce und Magento Open Source >=2.4.0*&lt;2.4.4) - Behebt das Problem, dass `VAT_ID` es in einem GraphQL-Anfrage für eine Gast User nicht angewendet werden kann.
* Aktualisierte Patches: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*für Adobe Systems Commerce und Magento Open Source >=2.3.5 &lt;2.4.4*) - Behebt das Problem, dass der Anzahl für ein virtuelles Produkt nach der Erstellung einer Gutschrift falsch berechnet wird.
* **ACSD-43887** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, dass falsche Details auf der Checkout Zahlungs Seite angezeigt werden, wenn Bestellungen für Unternehmen aktiviert sind.
* **ACSD-45143** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem die `setShippingAddressesOnCart`-Mutation das Festlegen des numerischen Regionscodes als *region* nicht zulässt.
* **ACSD-44591** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.6*) - Behebt den Fehler, der auftritt, wenn eine Bestellung ohne CAPTCHA-Bestätigung platziert wird.
* **ACSD-45520** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.6*) - Behebt das Problem, dass Farbfeld Optionen in den Produktdetails nicht vorausgewählt sind Seite, wenn ein User konfigurierbare Produkte aus dem Warenkorb bearbeitet.
* **ACSD-45169** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1*&lt;2.4.6 ) - Behebt das Problem, dass [!DNL Visual Merchandiser] nach dem Anwenden eines Staging-Updates nicht der richtige Bestand und Preis für ein konfigurierbares Produkt angezeigt wird.
* **ACSD-45424** (*für Adobe Systems Commerce und Magento Open Source >=2.3.4 &lt;2.4.6*) - Behebt das Problem, dass nach einer teilweisen Rückerstattung (Gutschrift) eine falsche Reservierungsentschädigung erstellt wird.
* **MDVA-42807** (*für Adobe Systems Commerce und Magento Open Source >=2.3.1 &lt;2.4.6*) - Behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Vorderseite des Geschäft angezeigt wird.
* Aktualisierte Patches: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4.3}) - Behebung des Problems, bei dem die Bestellsummen im Bericht &quot;Bestellungen&quot;für den eingeschränkten Admin-Benutzer falsch berechnet wurden.*
* **MDVA-44940** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4*) - Behebt den SQL-Fehler, der beim Speichern der Kategorie aus dem Admin auftritt.
* **MDVA-44562** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Behebung des Problems, bei dem die nicht standardmäßige Store-ID für Anführungselemente von der standardmäßigen Store-ID überschrieben wird, trotz der GraphQL-Anfrage aus der nicht standardmäßigen Store-Ansicht.
* **MDVA-43167** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, dass die Admin- bestellen Rastermassenaktion nicht für Multi-Seite gilt, wenn der Admin-User alle Bestellungen auswählt.
* **MDVA-44044** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Behebt das Problem, dass ein Produkt nicht auf der Kategorie Seite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde.
* **MDVA-42509** (*für Adobe Systems Commerce und Magento Open Source >=2.3.3*&lt;2.4.4) - Behebt das Problem, dass ein CSV für einen kurzen bestellen nicht hochgeladen werden konnte, was zu einem *Fehler führte, dass die Cookie* nicht gesendet werden konnte.
* Aktualisierte Patches: MDVA-41061, MDVA-42584.
* Das Präfix für die neuen [!DNL Quality Patches Tool] Patches wird aufgrund interner Prozessänderungen von *MDVA* in *ACSD* geändert.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4.3}) - Behebung des Problems, bei dem ein zusätzlicher Artikel nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist.*
* **MDVA-44887** (*für Adobe Commerce und Magento Open Source >=2.4.4 &lt;2.4.5*) - Behebt den Fehler *Uncaught SyntaxError: Unerwartetes Token &#39;const&#39;* im Admin-Bedienfeld.
* **MDVA-43718** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Fehlerbehebungen *Der Benutzer ist nicht berechtigt, auf %resources zuzugreifen.* -Fehler, der beim Zugriff auf einen freigegebenen Katalog von einer benutzerdefinierten Integration angezeigt wird.
* **MDVA-44660** (*für Adobe Commerce und Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Behebung des Problems, bei dem das Gravis-Zeichen ``` ` ``` nicht für den Vor- und Nachnamen eines Kunden verwendet werden konnte.
* **MDVA-40896** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4.3}) - Behebt den Fehler* Error: TypeError: Argument 3, das in der asynchronen Produkt-Bulk-API an Magento *übergeben wird.*
* **MDVA-38559** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt den Fehler */V1/customer/search API* für Kunden mit mehr als einem Abonnement.
* **MDVA-44533** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.4*) - Behebung des Problems, bei dem der Rabatt fälschlicherweise auf ein untergeordnetes Bundle-Produkt angewendet wird.
* Aktualisierte Patches: MDVA-41061, MDVA-42269

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem Produkte *Nicht einzeln sichtbar* weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden.
* **MDVA-44100** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem alle FPTs dem letzten Produkt im Warenkorb zugewiesen und für andere Produkte zurückgesetzt werden.
* **MDVA-43605** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebung des Problems, bei dem Bestelldaten bei Verwendung der Rest-API negative Werte für Zeilensummen zurückgeben.
* **MDVA-43102** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;2.4.5*) - Behebung des Problems, bei dem die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt.
* **MDVA-43178** (*für Adobe Commerce und Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Behebung des Problems, bei dem ein Kundentoken für einen benutzerdefinierten Store nicht in GraphQL abgerufen werden kann.
* **MDVA-43859** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem der Fehler *Keine Entität mit customerId =* protokolliert wird, wenn ein gelöschter Kunde versucht, sich anzumelden.
* **MDVA-44147** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem eine GraphQL-Anfrage keine Anforderungslisten zurückgibt.
* **MDVA-44505** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebt die Probleme, bei denen beim Anwenden von Belohnungspunkten auf GraphQL die Gesamtsumme nicht aktualisiert wird und bei denen während der Bestellplatzierung mehrmals eine Speichergutschrift angewendet wird.
* Aktualisierte Patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-3993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) – Behebt das Problem, dass die Regel für zugehörige Produkte nur funktioniert, wenn &quot;Kunden Segment&quot; auf *&quot;Alle*&quot; festgelegt ist.
* **MDVA-39605** (*für Adobe Systems Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) – Behebt das Problem, dass die Redis-Cache-TTL (Gültigkeit-Datum) einen falschen Wert hat.
* **MDVA-43862** (*für Adobe Systems Commerce und Magento Open Source >=2.3.3*&lt;2.4.5) - Behebt das Problem, bei dem der Kunde Warenkorb Elemente aufgrund eines GraphQL *UpdateCartItems-Mutationsfehlers* nicht aktualisieren kann.
* **MDVA-43824** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem beim Abbrechen von Bestellungen mit einem Rabatt ein Fehler angezeigt wird.
* **MDVA-43451** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Fehler *Der angeforderte Speicher nicht gefunden wurde. Überprüfen Sie den Speicher und versuchen Sie es erneut.* wird beim Konfigurieren eines freigegebenen Katalogs für eine bestimmte Website angezeigt.
* **MDVA-43491** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebung des Problems, bei dem die Basisbildbeschriftung beim Importieren von Produkten für eine Website mit mehreren Stores nicht aktualisiert wird.
* **MDVA-43601** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem mit fehlenden Triggern nach vollständiger Neuindizierung.
* **MDVA-42046** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem einem Produktattribut mit einem Datumseingabefeld beim Aktualisieren eines Produkts ein falscher Wert zugewiesen wurde.
* **MDVA-43935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebung des Problems, bei dem Upsell-Produkt zweimal angezeigt wird.
* **MDVA-44188** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem vom System ausgegebene E-Mails mit `.-` in Adressen nicht gesendet werden.
* **MDVA-42283** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Datums-/Uhrzeitformat im Admin-Reihenfolgenraster für das französische Gebietsschema ungültig ist.
* Aktualisiert: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Es wurden Patchmetadaten für den [!DNL Site-Wide Analysis Tool] hinzugefügt.

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Behebt das Problem, dass der User die Beginn Zeit für ein aktives geplantes Update bearbeiten kann.
* **MDVA-42410** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) – Behebt das Problem, dass Coupon Berichten nur die Standardbasiswährung anzeigen.
* **MDVA-41136** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0*&lt;2.4.5) - Behebt das Problem, dass das Gültigkeit Datum der `mage-cache-sessid` nicht verlängert wird, was zu einer Bereinigung der Kundendaten führt.
* **MDVA-39993** (*für Adobe Systems Commerce und Magento Open Source >=2.3.5 &lt;=2.3.7-p2 ||=&quot;&quot;>=2.4.0 &lt;2.4.4*) – Behebt das Problem, dass Warenbestand Änderungen, die über die API vorgenommen werden, sich nicht auf die Produktseite im Frontend auswirken.&lt;/=2.3.7-p2>
* **MDVA-42855** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem beim Checkout keine neue Kundenadresse im Adressbuch gespeichert wurde.
* **MDVA-42645** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem der Administrator keine Bonuspunkte zurückgeben kann, wenn die Funktion zum Speichern von Guthaben deaktiviert ist.
* **MDVA-43414** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Behebt den schwerwiegenden PHP-Fehler, der beim Ausführen des `inventory.reservations.updateSalabilityStatus` -Warteschlangen-Consumer auf numerischen SKUs auftritt.
* **MDVA-41628** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.5*) - Behebung des Problems, bei dem eingeschränkte Admin-Benutzer beim Hinzufügen neuer Module Zugriff auf die neuen Ressourcen erhalten.
* **MDVA-43348** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem bei der GraphQL-Anforderung für die Geschenkkarte ein Fehler angezeigt wird, wenn `gift_card_options` *uid* enthält.
* **MDVA-39546** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem, dass das Beginn Datum für das Staging-Update während der Bearbeitung auf ein früheres Datum als das aktuelle Datum gesetzt werden konnte.
* **MDVA-42950** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) – Behebt das Problem, dass Videos nicht auf dem Produktseite abgespielt werden.
* **MDVA-42689** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0*&lt;2.4.4) - Behebt das Problem, bei dem Adobe Systems Commerce beim Aktualisieren von Produktkategorien während des Imports einen *Fehler wegen Verletzung* der Integrität Begrenzung ausgibt.
* **MDVA-41229** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem, dass im Backend verfügbare Bilder nach dem Import konfigurierbarer Produkte nicht im Frontend angezeigt werden.
* **MDVA-43731** (*für Adobe Systems Commerce und Magento Open Source >=2.4.3*&lt;2.4.4) - Behebt das Problem, dass *Search Synonyme nicht mehr funktionieren, wenn der Wert in* Minimal zu vergleichenden *Begriffen* hinzugefügt wird.
* **MDVA-43232** (*für Adobe Systems Commerce und Magento Open Source >=2.3.4*&lt;2.4.5) - Behebt das Problem, dass das Sortieren von Produkten nach [!DNL Visual Merchandiser] Sonderpreis nach unten/oben einen Fehler beim Speichern der Kategorie verursacht.
* **MDVA-43726** (*für Adobe Systems Commerce und Magento Open Source >=2.3.3 &lt;2.4.3*) - Behebt das Problem, dass der Katalog Regel preis, der auf der Attributübereinstimmung auf Geschäft-Ebene basiert, nach einer teilweisen Neuindizierung nicht angewendet wird.
* Aktualisierte Patches: MDVA-36464, MDVA-37478, MDVA-38608.
* Es wurden Patches Metadaten für .[!DNL Site-Wide Analysis Tool]

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) - Behebung des Problems, bei dem Produktpreisattribute für eine bestimmte Website nicht über die REST-API aktualisiert werden können.
* **MDVA-41350** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem eine Ausnahme ausgelöst wird, wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt in einer Reihenfolge außerhalb des Rollenbereichs durch die SKU hinzufügt.
* **MDVA-42269** (*für Adobe Commerce und Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Behebung des Problems, bei dem sich ein Admin-Benutzer aufgrund des *TypeError: strtotime() erwartet, dass der Parameter 1 eine Zeichenfolge ist, wobei der Fehler &quot;null&quot;angezeigt wird.*
* **MDVA-40830** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem das Speichergutschrift mehrmals bei der Bestellplatzierung angewendet wird.
* **MDVA-42237** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebung des Problems, bei dem ein konfigurierbarer Produktspezialpreis nach Änderungen des Produktpreises nicht aktualisiert wird.
* **MDVA-42520** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4.3}) - Behebung des Problems, bei dem der Steuersatz zweimal angewendet wird, wenn* Grenzüberschreitenden Handel aktivieren *verwendet wird.*
* Aktualisierte Patches: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Veraltete Patch: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*für Adobe Systems Commerce und Magento Open Source >=2.3.2*&lt;2.4.5 ) - Behebt das Problem, dass die Massenattributaktualisierung URL Umschreibung für Standardmäßig Shop erst erstellt, nachdem die Produktsichtbarkeit *geändert* wurde.
* **MDVA-43091** (*für Adobe Systems Commerce und Magento Open Source >=2.4.3*&lt;2.4.4) - Behebt das Problem, bei dem die Bestellung eines Paket Produkts beim Administrator im Backend den Fehler *Sie können für dieses Produkt* keine Dezi Anzahl malzahlen verwenden.
* **MDVA-40816** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebung des Problems, bei dem verwandte Produktregeln Produkte aus nicht in den Regelbedingungen definierten Kategorien anzeigen.
* **MDVA-41305** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.5*) - Behebt das Problem, dass die GraphQL-Mutation nach dem Hinzufügen zur Wunschliste keine konfigurierbaren Produktoptionen zurückgibt.
* **MDVA-39181** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, bei dem zugehörige Produktregeln Produkte aus Kategorien anzeigen, die nicht in den Regel Bedingungen definiert sind.
* **MDVA-42584** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebt das Problem, dass der konfigurierbare Lagerstatus im Backend nach der Änderung der Menge und des Bestandsstatus über Importieren oder API nicht aktualisiert wird.
* **MDVA-40175** (*für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;2.4.3*) - Behebt das Problem, dass *Klicken, um die Versandart* zu ändern, während der Neubestellung keine Optionsfelder zur Auswahl der Versandart im Admin anzeigt.
* **MDVA-42768** (*für Adobe Systems Commerce und Magento Open Source >=2.3.4 &lt;2.4.5*) - Behebt das Problem, dass das konfigurierbare Produkt den regulären Preis als 0 anzeigt, wenn *Anzeigen Out-of-Stock* Ja ist.
* **MDVA-43201** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, bei dem ein Fehler in der Kunden Log-in auftritt, wenn das DOB-Attribut mit bestimmten Gebietsschemas verwendet wird.
* Aktualisierte Patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.5*) - Behebt das Problem, dass Datums-Filter nicht ordnungsgemäß funktionieren, wenn sich die Adobe Systems Commerce-Zeitzone von der lokalen Umgebung-Zeitzone unterscheidet.
* **MDVA-42657** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.5*) - Behebt das Problem, dass der Admin-User keine Kategorien in den Kunden Segment Bedingungen auswählen kann.
* **MDVA-42806** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) – Behebt das Problem, dass jedes Mal, wenn ein vorhandenes Firma über die REST-API aktualisiert wird, eine *Neu Firma registrierung-E-Mail* gesendet wird.
* **MDVA-37984** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1*&lt;2.4.5 ) – Behebt das Problem, dass die [!DNL Visual Merchandiser] *Match product by Regel* Funktionen Produkte mit Staging-Updates nicht korrekt filtert.
* **MDVA-40488** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) – Behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in der richtigen Preisspanne angezeigt werden.
* **MDVA-42507** (*für Adobe Systems Commerce und Magento Open Source >=2.4.3 &lt;2.4.5*) – Behebt das Problem, dass der vollständige Seite-Cache nach dem Anwenden des Staging-Updates für die Warenkorb Regel bereinigt wird.
* **MDVA-39163** (*für Adobe Systems Commerce und Magento Open Source >=2.3.5 &lt;2.4.5*) - Behebt das Problem, dass Versandmethoden nicht verfügbar sind, wenn ein neues User registriert wird und Produkte in der Warenkorb aus der Gastsitzung stammen.
* **MDVA-38626** (*für Adobe Systems Commerce und Magento Open Source >=2.3.3*&lt;2.4.5) - Behebt das Problem, dass der Admin-User nicht in der Lage ist, mit der [!DNL PayPal Payflow Pro] Zahlung einen bestellen im Backend zu platzieren.
* **MDVA-38666** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.3.6*) - Behebung des Problems, bei dem der Admin-Benutzer die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern kann.
* **MDVA-38526** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4.3}) - Behebung des Problems, bei dem der Administratorbenutzer nicht auf den [!DNL Site-Wide Analysis tool] zugreifen kann.*
* Aktualisierte Patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4.3}) - Behebung des Problems, bei dem Benutzer den 500-Fehler erhalten, nachdem sie das Cookie* mage-messages *gesetzt haben, sofern er bereits vorhanden ist, aber keine neuen Nachrichten vorhanden sind.*
* **MDVA-41139** (*für Adobe Commerce und Magento Open Source >=2.4.3 &lt;2.4.4.3}) - Behebung des Problems, bei dem konfigurierbare Produkte nach dem Produktimport zu &quot;Nicht auf Lager&quot;werden, wenn die Menge eines einfachen Produkts = 0 für eine seiner Quellen beträgt.*
* **MDVA-42326** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem Kunden beim Checkout nach einem Sitzungs-Timeout einen Fehler erhalten, selbst wenn der beständige Warenkorb aktiviert ist.
* **MDVA-42341** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4.3}) - Behebung des Problems, bei dem die `categoryList` GraphQL-Abfrage keine Ergebnisse filtert, wenn eine Anfrage die Store-Kopfzeile aufweist.*
* **MDVA-38393** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4.3}) - Behebung des Problems, bei dem Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wird.*
* **MDVA-39153** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4.3}) - Behebung des Problems, bei dem ein Rabattbetrag bei der Neuanordnung im Admin falsch berechnet wurde.*
* Aktualisierte Patches: MDVA-28993, MDVA-41061, MDVA-35984

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Admin-Benutzer nach dem Löschen der Website nicht auf das Kundenraster zugreifen können.
* **MDVA-40311** (*für Adobe Commerce und Magento Open Source >=2.4.2-p2 &lt;2.4.4.3}) - Behebung des Problems, bei dem Administratoren die Fehlermeldung* Ungültige Sicherheit oder Formularschlüssel erhalten. *Aktualisieren Sie die Seite* nach der Anmeldung beim Administrator, wenn der benutzerdefinierte Admin-Pfad konfiguriert und der geheime Schlüssel aktiviert ist.
* **MDVA-41631** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4.3}) - Behebung des Problems, bei dem Benutzer beim Versuch, Bestellinformationen ohne optionalen* Telefonwert *über GraphQL abzurufen, einen Fehler erhalten.*
* **MDVA-27239** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem Querverkaufsprodukte nicht angezeigt werden.
* Aktualisiert: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-317 1.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.4*) - Behebt das Problem mit fehlenden Produkten auf der Vorderseite während der Neuindizierung.
* **MDVA-40120** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4.3}) - Behebung des Problems, bei dem die GraphQL-Sortierung nach DESC/ASC nicht mit Produkten mit derselben Relevanz oder demselben Preis funktioniert.*
* **MDVA-41399** (*für Adobe Commerce und Magento Open Source >=2.3.3 &lt;2.4.2*) - Behebung des Problems, bei dem Admin-Benutzer nicht auf die Seite *Warenkorb verwalten* zugreifen können, wenn ein Kunde ein Produkt auf die Wunschliste setzt.
* **MDVA-40609** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2*&lt;2.4.3) - Behebt das Problem, dass Daten zu deaktivierten Produkten in der `cataloginventory_stock_status` Indextabelle fehlen und falsche Mengen für deaktivierte Produkte angezeigt werden.
* **MDVA-39031** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.4*) - Behebt das Problem, dass das Hinzufügen eines Produkts zur Warenkorb über GraphQL möglich ist, Linear wenn es nicht der Target-Komponente Website zugewiesen ist.
* **MDVA-41597** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4.3}) - Behebung des Problems, bei dem Benutzer beim Hinzufügen von mehr als einem konfigurierbaren Produkt zum Warenkorb mit GraphQL einen Fehler erhalten.*
* **MDVA-27456** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.3.7*) - Behebung des Problems, bei dem Benutzer beim Laden von [!DNL Swagger] einen Fehler erhalten.
* **MDVA-32776** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versandt wird.
* **MDVA-30862** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.0*) - Behebt das Problem mit dem falschen Bestelldatum auf der gedruckten PDF-Rechnung.
* Die Indexseite für die [!DNL Quality Patch Tool] wurde verbessert. Es wurde eine praktische Suche und Filterung nach [!DNL quality patches] in der neuesten Version des Tools hinzugefügt.
* Aktualisierte Patches: MDVA-3382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4.3}) - Behebung des Problems, bei dem es nicht möglich ist, ein neues oder ein vorhandenes geplantes Update für ein Produkt zu erstellen, wenn das Enddatum zuvor entfernt wurde.*
* **MDVA-41046** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem einfache Produkte mit benutzerdefinierten Optionen für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind.
* **MDVA-40545** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4.3}) - Behebung des Problems, bei dem nur der erste Knoten für eine Seite abgerufen wurde, selbst wenn mehrere Knoten für dieselbe Seite vorhanden waren.*
* **MDVA-41164** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Behebung des Problems, bei dem ein Admin-Benutzer ein Unternehmen mit einem benutzerdefinierten Kundenattribut vom Typ &quot;Datei&quot;oder &quot;Bild&quot;nicht speichern oder bearbeiten kann.
* **MDVA-39229** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4.3}) - Behebt das Problem, das nach der Aktualisierung der Startzeit der Katalogregel-Staging-Update-Zeit den folgenden Fehler verursacht:* Cron Job staging_synchronize_entity_period hat einen Fehler: Die aktive Aktualisierung kann nicht gelöscht werden **
* **MDVA-40619** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4.3}) - Behebung des Problems, bei dem Änderungen an der CMS-Seitenhierarchie beim Versuch, eine Inline-Bearbeitung auf einer CMS-Seite durchzuführen, einen 500-Fehler verursachen.*
* **MDVA-41061** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem der Lagerstatus beim Speichern eines Produkts vom Administrator auf &quot;verkäuflich&quot;zurückgesetzt wird.
* **MDVA-31763** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebung des Problems, bei dem Katalogpreisregeln bis zur manuellen Neuindizierung zurückgesetzt (oder nicht angewendet) werden.
* **MDVA-37748** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem eine GraphQL-Abfrage Produkte zurückgibt, die keinem freigegebenen Katalog zugeordnet sind.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.4.3}) - Behebung des Problems, bei dem Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können.*
* **MDVA-40101** (*für Adobe Commerce und Magento Open Source >=2.3.2 &lt;2.4.0*) - Behebung des Problems, bei dem Artikel nach einer erfolgreichen Bestellplatzierung mit [!DNL PayPal Express] Checkout nicht aus dem Mini-Warenkorb entfernt werden.
* **MDVA-40401** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem sich der Couponverwendungswert ändert, selbst wenn die Bestellung fehlschlägt.
* **MDVA-40537** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Behebung des Problems, bei dem Benutzer beim Erstellen einer Store-Ansicht einen Fehler erhalten, wenn mehrere CMS-Seiten mit demselben URL-Schlüssel vorhanden sind.
* **MDVA-37725** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Behebung des Problems, bei dem von nicht standardmäßigen Websites gesendete asynchrone Bestellungen-E-Mails Logo-URLs von der Standardwebsite enthalten.
* **MDVA-39482** (*für Adobe Commerce und Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Behebung des Problems, bei dem ein Produkt nicht mehr vorrätig ist, wenn es mit &quot;0&quot;importiert wurde, wenn Rückstände aktiviert waren.
* **MDVA-40435** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;2.4.4*) - Behebung des Problems mit einem falschen Rabatt auf Bundle-Produkte mit dynamischen Preisen, wenn sie über GraphQL angewendet werden.
* **MC-42528** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Fixes the issue where the `categoryList` GraphQL query returns both assigned and unassigned categories.
* **MDVA-29400** (*für Adobe Commerce und Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Behebung des Problems mit duplizierten Bestellungen, die mit [!DNL PayPal Express Checkout] aufgegeben wurden.
* **MDVA-26005** (*für Adobe Systems Commerce und Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Behebt das Problem, dass es unmöglich ist, eine Kategorie in einem Kategorie Baum für Warenkorbpreis Regel Bedingungen auszuwählen.
* **MDVA-25631** (*für Adobe Systems Commerce und Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) – Verbessert die Leistung beim Bearbeiten und Speichern von Kundensegmenten, die eine große Anzahl von Kunden enthalten.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt das Problem, dass GraphQL-suchen-Abfragen nicht in beliebten suchen-Begriffen im Admin angezeigt werden.
* **MDVA-40601** (*für Adobe Systems Commerce und Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Behebt das Problem, bei dem Benutzer eine Fehlermeldung erhalten, wenn sie versuchen, Informationen über die Kategorie abzurufen, die durch ein geplantes Update über GraphQL geändert wurden.
* **MDVA-37234** (*für Adobe Commerce und Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem beim mehrfachen Hinzufügen eines Artikels zum Warenkorb (parallele Anfrage) für dieselbe SKU ein doppeltes Zeilenelement für dieselbe Warenkorb-ID erstellt wird.
* **MDVA-33606** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Behebt das Problem, bei dem Benutzer beim Speichern einer einer einer Hierarchie zugewiesenen CMS-Seite den Fehler *Eindeutige Einschränkungsverletzung* erhalten.
* **MDVA-31590** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Behebung des Problems, bei dem Benutzer Attribute nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisieren können.
* **MDVA-36309** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem die Produktsuche nach Attributen in den Admin-Rastern langsam ist.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem, dass die Rechnung mit FPT einen falschen Grand Gesamt anzeigt, wenn die bestellen vom Geschäft Guthaben bezahlt wird.
* **MDVA-37364** (*für Adobe Systems Commerce und Magento Open Source >=2.4.0 &lt;=2.4.3*) - Behebt das Problem, bei dem das benutzerdefinierte Kundenattribut des Datumstyps die Raster UI des Kunden unterbricht.
* **MDVA-39195** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebt das Problem, dass *hinzufügen zum Warenkorb* Button auf der Kategorie Seite inaktiv war, wenn Redirect aktiviert Warenkorb.
* **MDVA-37115** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Behebung des Problems, bei dem auf der konfigurierbaren Produktseite ein unnötiger Hinweis &quot;*Nur 0 links*&quot;angezeigt wird.
* **MDVA-39521** (*für Adobe Commerce und Magento Open Source >=2.4.0 &lt;2.4.4.3}) - Behebung des Problems, bei dem der Benutzer Versandadressen nicht über GraphQL mit einer leeren Telefonnummer auf den Warenkorb setzen kann.*
* **MDVA-39384** (*für Adobe Commerce und Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Behebung des Problems, bei dem das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wurde.
* **MDVA-39043** (*für Adobe Commerce und Magento Open Source >=2.3.4 &lt;=2.4.3*) - Behebung des Problems, bei dem der Admin-Benutzer mit eingeschränktem Zugriff beim Versuch, das Widget *Products* zur CMS-Seite hinzuzufügen, einen Fehler erhält.
* **MDVA-39966** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2 ||=&quot;&quot;>=2.4.0 &lt;=2.4.0-p1*) – behebt das Problem durch die Bereitstellung falscher Gebietsschemas.&lt;/=2.3.5-p2>
* **MDVA-38852** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Behebt das Problem, dass der von Design Warenbestand Katalog Tabellen für Updates sperrt, die die Leistung in Fällen mit mehreren parallelen Bestellungen erheblich verringern.
* **MDVA-39986** (*für Adobe Systems Commerce und Magento Open Source >=2.4.1 &lt;2.4.3*) - Behebt das Problem, dass der User unter MacOS mit dem Safari-Browser keine bestellen im Admin platzieren kann.
* **MDVA-38447** (*für Adobe Systems Commerce und Magento Open Source >=2.4.2 &lt;2.4.4*) - Behebt zwei Probleme: wobei die *Nicht sichtbare, individuell* konfigurierbare untergeordnete Produkte in der GraphQL-Antwort zurückgegeben werden und die MySQL-Abfrage für GraphQL-Produkte Abfrage mit Kategorie Filter optimieren.
* **MDVA-40134** (*für Adobe Commerce und Magento Open Source >=2.4.2 &lt;2.4.3*) - Behebung des Problems, bei dem GraphQL keine verwandten Produkte zurückgibt, wenn der freigegebene Katalog aktiviert ist.
* **MDVA-39935** (*für Adobe Commerce und Magento Open Source >=2.4.1 &lt;2.4.4.3}) - Behebung des Problems, bei dem der GraphQL konfigurierbare untergeordnete Produkte zurückgibt, die auf Website-Ebene deaktiviert sind.*

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*für Adobe Systems Commerce und Magento Open Source >=2.4.0*&lt;2.4.4) - Behebt das Problem, bei dem der *Fehler Aufruf einer Memberfunktion getId()* auf der Bestelldetails Seite im Admin angezeigt wird.
* **MDVA-34948** (*for Adobe Commerce and Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Fixes the issue with long-running queries, like `GET_LOCK`.
* **MDVA-39305** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Fixes the issue where registered customers are not able to log in with enabled Google ReCaptcha.
* **MDVA-37897** (*für Adobe Systems Commerce und Magento Open Source >=2.3.0 &lt;2.4.4*) - Behebt das Problem mit einer falschen Redirect, wenn ein Kunde versucht, Produkte mit Optionen aus dem Widget &quot;Zuletzt angesehen&quot; hinzuzufügen.

## v1.1.0 {#v1-1-0}

* Patch-Kategorien wurden eingeführt bestellen um die User Experience zu verbessern und den Kunden die Suche nach benötigten Patches zu erleichtern.
* Die `patches.json` Datei wurde umbenannt in `support-patches.json`.
* **MDVA-38799** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem herunterladbare Produkte nach dem Erstellen eines Staging-Updates nicht gespeichert wurden.
* **MDVA-37592** (*für Adobe Systems Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebt das Problem, dass die Sortierung nach Preis für Produkte mit einem Nullpreis, der dem freigegebenen Katalog zugewiesen ist, nicht korrekt funktioniert.
* **MDVA-38827** (*für Adobe Systems Commerce >=2.3.3-p1 &lt;2.4.4*) - Behebt das Problem, dass Kunden eine E-Mail mit einer bestellen Sendung mit einer Fehlermeldung erhalten.

## v1.0.26 {#v1-0-26}

* **MDVA-38468 (für Adobe Systems Commerce >=2.3.2 *&lt;=2.3.5-p2 ) - Behebt den Fehler beim Speichern von CMS-Seiten:*Element mit der gleichen ID PAGE_ID bereits vorhanden *.***
* **MDVA-34680** (*für Adobe Systems Commerce >=2.3.6 &lt;=2.3.7 ||=&quot;&quot;>=2.4.1 &lt;2.4.3*) - Behebt das Problem, dass die Erstellungszeit des Kundenkontos im Kundenraster nicht korrekt gefiltert wird.&lt;/=2.3.7>
* **MDVA-37068** (*für Adobe Systems Commerce >=2.3.1 &lt;2.4.4*) - Behebt das Problem, dass der falsche Steuersatz angezeigt wird, wenn die Warenkorb nur virtuelle Produkte hat.
* **MDVA-38608** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem temporäre Tabellen nicht gelöscht werden, wenn die Neuindizierung nicht erfolgreich abgeschlossen wurde.
* **MDVA-38308** (*für Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Behebt die Probleme beim Hinzufügen von [!DNL Vimeo] Videos zu Produkten.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*für Adobe Commerce >=2.3.6 &lt;2.4.3*) - Behebung des Problems, bei dem der Kunde bei Verwendung der [!DNL Paypal Payment Advanced] -Methode nicht zur Zahlungsbestätigungsseite geleitet wird.
* **MDVA-37082** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems beim Speichern des benutzerdefinierten Lagers für gruppierte Produkte, das dazu führt, dass das Produkt im Frontend nicht vorrätig angezeigt wird.
* **MDVA-36572** (*für Adobe Commerce >=2.3.5 &lt;2.4.3*) - Behebung des Problems, bei dem Aktualisierungen des Credit Memo nicht mehr zu doppelten Aktualisierungen der Produktreservierung in der Datenbank führen.
* **MDVA-38132** (*für Adobe Commerce >=2.3.3 &lt;2.4.3*) - Behebung des Problems, bei dem das Admin-Bedienfeld aufgrund eines *zu vielen Umleitungen* -Fehlers nicht erreichbar ist.
* **MDVA-38270** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebung des Problems mit fehlenden Geschenkkarteninformationen in der Bestellsumme in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*für Adobe Commerce >=2.4.2 &lt;=2.4.4.3}) - Behebung des Problems beim Hinzufügen eines konfigurierbaren Produkts zum Warenkorb über GraphQL, wenn die Website-ID nicht mit der Store-ID übereinstimmt.*
* **MDVA-36832** (*für Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Behebung des Problems, bei dem Bilder auf Seiten dupliziert werden, wenn die Anzeigebreite 768 px beträgt.
* **MDVA-37874** (*für Adobe Systems Commerce >=2,3,6 &lt;=2.3.7 ||=&quot;&quot;>=2,4,1 &lt;=2.4.2-p1*) - Behebt das Problem, bei dem *Fest Rabattbetrag für die ganze Warenkorb* fälschlicherweise auf ein Paket Produkt angewendet wird, das mehr als eine Option enthält.&lt;/=2.3.7>
* **MDVA-37913** (*für Adobe Systems Commerce >=2.3.0 &lt;=2.4.0-p1*) – Behebt das Problem, bei dem herunterladbare Links verschwinden, wenn das herunterladbare Produkt über API aktualisiert wird.
* **MDVA-34330** (*für Adobe Systems Commerce >=2.3.1 &lt;=2.4.2-p1*) - Behebt das Problem, bei dem Bestellungen im Auftragsraster nicht gemäß der Admin-Zeitzone gefiltert werden.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*für Adobe Systems Commerce >=2.3.0&lt;=2.3.7*) - Behebt das Problem, bei dem Adobe Systems Commerce einen Fehler ausgibt, wenn eine Teilrechnung für Bestellungen erstellt wird, die mit der Zahlungsmethode Zahlung auf Rechnung *über die* REST-API aufgegeben wurden.
* **MDVA-37362** (*für Adobe Systems Commerce >=2.3.4 &lt;=2.4.2-p1*) - Behebt das Problem, bei dem konfigurierbare Produktoptionswerte und Variantenattributwerte in der GraphQL-Antwort leer waren.
* **MDVA-37288** (*für Adobe Systems Commerce 2.4.2*) - Behebt das Problem, dass nach der GraphQL-Anfrage falsche Stufenpreise zurückgegeben wurden.
* **MDVA-37225** (*für Adobe Systems Commerce >=2.4.1 &lt;=2.4.2-p1*) – Behebt das Problem, dass der Upload-Prozess während der schnellen bestellen-Erstellung hängen bleibt, wenn ein ganzzahliger Wert in importierten SKUs vorhanden ist.
* **MDVA-37224** (*für Adobe Systems Commerce >=2.3.3*&lt;=2.4.2-p1) - Behebt das Problem, dass Kunden nicht für ein verhandelbares Angebot mit [!DNL PayFlow Pro] einem anderen Produkt in der Warenkorb bezahlen können.
* **MDVA-36286** (*für Adobe Systems Commerce >=2.3.6 &lt;=2.4.2-p1*) - Behebt das Problem, dass Page Builder Produkt-Widget Vorschau kaputt geht, wenn dieselbe Produktnummer eine andere Position in den Unterkategorien hat.
* **MDVA-30186** (*für Adobe Systems Commerce >=2.3.4 &lt;=2.3.5-p2,>=2.4.0 &lt;=2.4.0-p1,>=2.4.2 &lt;=2.4.2-p1*) - Behebt das Problem, bei dem Attributoptionen in der GraphQL-Antwort nach dem Optionswert und nicht nach der Anzahl der Attributelemente sortiert werden.&lt;/=2.4.0-p1,>&lt;/=2.3.5-p2,>

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*für Adobe Systems Commerce >=2.3.0 &lt;=2.4.2*) - Behebt das Problem, bei dem die alten benutzerdefinierten Optionen erhalten bleiben, nachdem sie per API geändert wurden.
* **MDVA-35773** (*für Adobe Systems Commerce >=2.3.6 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.1 &lt;=2.4.2*) - Behebt das Problem, dass der Grand Gesamt auf der Rechnung für Bestellungen mit 100% Rabatt nicht als Null angezeigt wird.&lt;/=2.3.6-p1>
* **MDVA-36833** (*für Adobe Systems Commerce 2.4.2*) - Behebt das Problem mit suchen Ergebnissen, die eine zufällige Anzahl von Produkten pro Seite anzeigen, nachdem einige Produkte aus dem freigegebenen Katalog ausgeschlossen wurden.
* **MDVA-37182** (*für Adobe Systems Commerce >=2.4.1*&lt;=2.4.2) - Behebt das Problem, dass sowohl in Version 6 als auch [!DNL Elasticsearch] in Version 7 falsche suchen Ergebnisse angezeigt werden.
* **MDVA-36253** (*für Adobe Systems Commerce >=2.4.0 &lt;=2.4.1-p1*) - Behebt das Problem, dass nach dem Löschen von Elementen die falsche Zwischensumme in der Mini-Warenkorb angezeigt wird.
* **MDVA-36853** (*für Adobe Systems Commerce 2.4.2*) - Behebt das Problem, dass beim Laden großer Medien Galerien keine Bilder angezeigt werden.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*für Adobe Systems Commerce >=2.3.4 &lt;=2.3.4-p2*) - Behebt das Problem mit fehlenden gebündelten Produkten auf Kategorie Seiten.
* **MDVA-36615** (*für Adobe Systems Commerce 2.4.2*) – Behebt das Problem mit der falschen Produktanzahl im Admin-Produktraster.
* **MDVA-36464** (*für Adobe Systems Commerce >=2.4.0 &lt;=2.4.2*) - Behebt das Problem, dass die E-Mail-Benachrichtigung-Konfiguration auf Geschäft-Ansicht-Ebene nicht funktioniert.
* **MDVA-36138** (*für Adobe Commerce ^2.3.2*) - Behebung des Problems, bei dem der Versandpreis nicht angepasst wird und der vollständige Versandpreis den Kunden angezeigt wird, wenn nicht alle Artikel im Warenkorb für die Regel des kostenlosen Warenkorbs infrage kommen.
* **MDVA-36424** (*für Adobe Systems Commerce >=2.3.0 &lt;=2.3.3-p1 ||=&quot;&quot;>=2.0.0 &lt;2.2.0*) - Behebt das Problem, dass Medien Bilder, die an Seite Builder-Elementen angehängt sind, verschwinden, wenn die Inhalte wiederholt bearbeitet wird, wenn sich die Backend-Basis URL von der Storefront-Basis URL unterscheidet.&lt;/=2.3.3-p1>
* **MDVA-35984** (*für Adobe Systems Commerce ^2.4.0*) - Behebt das Problem mit falschen Produkt-Anzahl und verkaufsfähigen Anzahl, nachdem mehrere gleichzeitige Sendungen für dasselbe Produkt erstellt wurden.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermit wird das Problem behoben, dass die GraphQL-Abfrage nicht zwischenspeichert, indem das Kategorie-Cache-Tag verwendet wird.
* **MDVA-33168** (*für Adobe Commerce >=2.3.3 &lt;2.4.2*) - Behebung des Problems beim Aktualisieren eines Produktattributs über die API, wenn alle anderen Attribute zu einem leeren Wert geändert werden.
* **MDVA-19640** (*für Adobe Commerce >=2.3.0*) - Behebung des Problems, bei dem [!DNL Advanced Reporting] keine Daten anzeigt.
* **MDVA-1189** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebt das Problem, wenn nach dem Import einer CSV-Datei zur Aktualisierung des Produktbestands Zeilen aus der `cataloginventory_stock`-Tabelle gelöscht werden.
* **MDVA-26639** (*für Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Behebung des Problems, bei dem bei der Erstellung einer neuen E-Mail-Vorlage zur Bestellbestätigung die Bestellelemente in der Bestellmail fehlen.
* **MDVA-15546** (*für Adobe Commerce >=2.3.0*) - Behebung des Problems, bei dem nach dem Erstellen einer Bestellung ein Fehler vom Typ *Spaltenentität_ID angezeigt wird, bei dem der Fehler &quot;clause is ambiuous*&quot;im Ausnahmeprotokoll angezeigt wird.
* **MDVA-21095** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebung des Problems, bei dem eine Abfrage `INSERT INTO search_tmp` nach der Aktualisierung des Massenattributs nicht beendet wird.
* **MDVA-23845** (*für Adobe Systems Commerce >=2.3.2-p2 &lt;2.3.5*) – Behebt das Problem, dass E-Mail-Vorlagen nicht in der Vorschau angezeigt werden können, nachdem JavaScript Minimierung aktiviert wurde.
* **MDVA-22026** (*für Adobe Systems Commerce >=2.3.2 &lt;2.3.4*) - Behebt das Problem, bei dem das Importieren von Produkten aus CSV Datei, einschließlich Bildern von externen URLs, fehlschlägt.
* **MDVA-22383** (*für Adobe Systems Commerce >=2.3.0 &lt;2.3.4*) - Behebt das Problem, dass das Speichern eines Produkts lange dauert und die Seite unterbrochen wird.
* **MC-41359** (*für Adobe Systems Commerce >=2.3.6-p1 &lt;2.3.7,>=2.4.2 &lt;2.4.3*) - Behebt das Problem der falschen Einstellungen der SameSite-Cookie-Parameter.&lt;/2.3.7,>

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*für Adobe Commerce 2.4.1*) - Behebung des Problems, bei dem der Seitenaufbau den folgenden Fehler auslöst: *Beim Initiieren von Page Builder ist ein Fehler aufgetreten. Wenden Sie sich an Ihren Ansprechpartner beim technischen Support.*
* **MDVA-35356** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Store-Kreditrendite nach teilweise fakturierter Auftragsstornierung.
* **MDVA-33289** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Behebung des Problems, bei dem während des Checkouts der JavaScript-Rohcode in der Benutzeroberfläche der Rechnungsadresse angezeigt wird, wenn [!DNL Google Tag Manager] aktiviert ist.
* **MDVA-35982** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Admin-Benutzer, die auf eine bestimmte Website beschränkt sind, keine Sendung für die auf derselben Website platzierte Bestellung erstellen können.
* **MDVA-35155** (*für Adobe Commerce >=2.3.0 &lt;2.3.6*) - Behebung des Problems, bei dem es nicht möglich ist, ein Bundle-Produkt zu kaufen, wenn der Optionstitel geändert wurde.
* **MDVA-35910** (*für Adobe Systems Commerce >=2.4.1 &lt;2.4.3*) - Behebt das Problem, dass es unmöglich ist, einen neuen Kunden Konto zu erstellen, nachdem der Anmeldung als Kunden Funktionen deaktiviert wurde.
* **MDVA-34474** (*für Adobe Systems Commerce >=2.3.0 &lt;2.4.3*) – Behebt das Problem beim Hinzufügen eines Produkts zur Anforderung Liste mithilfe der API.
* **MDVA-34591** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt das Problem mit einer falschen Berechnung des Rabatts für Warenkorbregeln für *Der maximale Rabatt wird auf* und *Rabattschritt &quot;Menge&quot;(Kauf X)* angewendet.
* **MDVA-33704** (*für Adobe Commerce >=2.4.0 &lt;2.4.3*) - Behebung des Problems, bei dem die Versandoption *In store pickup* nicht angezeigt wird, obwohl sie so konfiguriert ist, dass sie verfügbar ist.
* **MDVA-34928** (*für Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Behebung des Problems, bei dem das Laden der Seite unbegrenzt angezeigt wird, nachdem das Store-Guthaben aus der Zahlung entfernt wurde.
* **MDVA-35254** (*für Adobe Commerce >=2.3.1 &lt;2.4.3*) - Behebt die Probleme mit CAPTCHA beim Checkout.
* **MDVA-35569** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebung des Problems, bei dem das Feld *feste Produktsteuern* in der GraphQL-Antwort nicht ausgefüllt wird, wenn ein Status angegeben ist.
* **MDVA-35847** (*für Adobe Commerce >=2.4.1 &lt;2.4.3*) - Behebt das B2B-Problem, bei dem die von den Unternehmensbenutzern ausgehenden Daten fehlschlagen, wenn ein benutzerdefiniertes Kundenattribut verwendet wird.
* **MDVA-31307** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebt das Problem, dass bei bestimmten Kategorien Fehler wegen Problemen mit der dynamischen CSP-Whitelisting für zwischengespeicherte Blöcke *Fehler wegen ungenügenden Arbeitsspeichers* auftreten.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebt den falschen Status der *in progress*-Nachricht auf die richtige *complete* -Meldung für den Verbraucher `quoteItemCleaner`, nachdem mehrere Produkte gelöscht wurden.
* **MDVA-34102** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Legt fest, dass die Standardspeichermenge für deaktivierte Produkte auf den Produktraster- und Produktseiten im Admin-Bereich null ist.
* **MDVA-35286** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem ein Fehler auftritt, wenn ein Kunde Produkte im Warenkorb gebündelt hat und von &quot;Multiple Addresses Checkout&quot;zum &quot;Onepage Checkout&quot;wechselt.
* **MDVA-35312** (*für Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Behebt den Antwortcode 500 bei einer leeren GraphQL-Anforderung.
* **MDVA-34189** (*für Adobe Commerce >=2.3.4 &lt;2.4.3*) - Behebt die 503-Byte-Zeitüberschreitung bei [!DNL Visual Merchandiser] -Abfragen beim Laden der Seite &quot;Admin-Kategorie&quot;.
* **MDVA-34695** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebt negative `children_count` nach dem Löschen von Kategorien.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*for Adobe Commerce >=2.3.1 &lt;2.4.3*) - Fixes the issue where the *Use default value* checkbox gets cleared after the scheduled changes are applied. Das Problem wird angezeigt, sobald die geplanten Änderungen nicht mehr in Kraft sind.
* **MDVA-35064** (*für Adobe Commerce >=2.3.3 &lt;2.4.3*) - Behebung des Problems, bei dem URL-Neuschreibungen nicht für konfigurierbare Produkte generiert werden, die über API erstellt wurden.
* **MDVA-34943** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die Schnellbestellung die zuvor eingegebenen SKUs zwischenspeichert.
* **MDVA-35197** (*für Adobe Commerce >=2.3.5 &lt;2.4.0*) - Behebung des Problems, bei dem beim Hinzufügen zum Warenkorb mit GraphQL ein Fehler auftrat, wenn zuvor hinzugefügte Produkte nicht mehr vorrätig waren.
* **MDVA-34850** (*für Adobe Commerce >=2.3.1 &lt;2.4.0*) - Behebung des Problems, bei dem die nicht vorrätigen Optionen eines konfigurierbaren Produkts nicht angezeigt werden, anstatt als Durchschlag angezeigt zu werden.
* **MDVA-34867** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem Werte für ein Bedingungsfeld, das für eine geplante Aktualisierung festgelegt wurde, nicht gespeichert werden.
* **MDVA-35092** (*für Adobe Commerce >=2.3.5 &lt;2.4.3*) - Behebung des Problems, bei dem Benutzer aufgrund der veralteten [!DNL Vimeo] -API keine [!DNL Vimeo]-Videos hinzufügen können.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*for Adobe Commerce >=2.3.6 &lt;2.4.3*) - Fixes the issue where Page Builder Products content type preview breaks if matching products have different prices for each website.
* **MDVA-32634** (*for Adobe Commerce ^2.3.1*) - Fixes the issue where the `url_path` of the category assigned to all store remains unchanged after moving the category in the hierarchy.
* **MDVA-33344** (*für Adobe Systems Commerce ^2.3.0*) - Behebt das Problem, bei dem hartcodiert Standardattributsatz-ID der `rma_item` Entität anstelle des Werts aus der Datenbank verwendet wird.
* **MDVA-34192** (*für Adobe Systems Commerce >=2.3.4 &lt;2.4.3*) - Behebt das Problem, dass es nicht möglich ist, das Geburtsdatum des Kunden im Format TT/MM/JJJJ zu ändern/anzugeben.
* **MDVA-34847** (*für Adobe Systems Commerce ^2.3.0*) - Korrigiert Geschäft IDs vom Typ Konversion zu Ganzzahl für SQL-Bedingung in Admin-Sammlungen für Admin-Benutzer mit benutzerdefinierten Berechtigungen.
* **MDVA-34886** (*für Adobe Systems Commerce ^2.3.2*) - Behebt das Problem, dass suchen keine Ergebnisse zurückgibt, wenn *Gewichtung* Produktattribut als durchsuchbar konfiguriert ist.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*für Adobe Systems Commerce >=2.3.0*&lt;2.4.3) - Behebt das Problem, dass [!DNL PayPal Payflow Pro] Zahlungen mit Redirect Parameter- Liste Formatfehler fehlschlagen.
* **MDVA-34023** (*für Adobe Commerce >=2.3.0 &lt;2.4.3*) - Behebung des Problems, bei dem der Fehler *Keine Entität mit addressId* zufällig auf den Browsern der Besucher angezeigt wird.
* **MDVA-32759** (*für Adobe Commerce >=2.3.1 &lt;2.4.3 mit B2B-Erweiterung*) - Behebung des Problems, bei dem freigegebene Kataloge die vorhandenen Ebenen-Preise löschen.
* **MDVA-33482** (*for Adobe Commerce ^2.3.5*) - Fixes the issue where generating a Credit Memo against a partial invoice results in tax for the total order instead of tax for that partial invoice.
* **MDVA-33393** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the error *Provided countryId does not exist*.
* **MDVA-33632** (*für Adobe Systems Commerce >=2.3.0*&lt;2.3.7) - Stellt eine Lösung bereit, bei der die Ausnahmemeldung *&quot;Dieses Produkt ist nicht vorrätig*&quot; jetzt einem Admin-User angezeigt wird, wenn versucht wird, ein nicht vorrätiges Produkt erneut bestellen.
* **MDVA-34469** (*für Adobe Systems Commerce >=2.4.1 &lt;2.4.2*) - Behebt das Problem, bei dem GraphQL-Mutationen auf der Warenkorb eines Kunden fehlschlagen, wenn mehrere Geschäft Ansichten verwendet werden.
* **MDVA-33976** (*für Adobe Commerce >=2.3.0 &lt;2.3.7*) - Behebung des Problems, bei dem das Bundle-Produkt auf der Storefront angezeigt wird, nachdem die zweite Option aus dem Bundle-Produkt entfernt wurde.
* **MDVA-33894** (*für Adobe Commerce >=2.4.0 &lt;2.4.1 mit B2B-Erweiterung*) - Behebt mehrere Probleme mit der Funktion &quot;Schnelle Bestellung&quot;, einschließlich des Hinzufügens und Entfernen mehrerer Produkte sowie der Groß-/Kleinschreibung von SKUs.
* **MDVA-27664** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem im Anmeldeformular für Kunden, das einen Fehler verursachte: *FEHLER - Das Geburtsdatum sollte nicht größer als heute sein.*
* **MDVA-33970** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebung des Problems, bei dem das falsche Währungszeichen im Credit Memo vorhanden ist, wenn der Umfang des Preisattributs auf die Website festgelegt ist.
* **MDVA-33992** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - behebt das Problem der B2B-Sonderpreise, die beim Checkout falsch angezeigt werden.
* **MDVA-34100** (*for Adobe Commerce >=2.3.4 &lt;2.4.2 with B2B extension*) - Fixes the issue where a company account cannot be created from the company structure page.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*für Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Behebt das Problem mit duplizierten Bildern nach dem Produktimport aus einer CSV-Datei.
* **MDVA-33382** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt die Probleme mit der Invalidierung von Indexern, nachdem Produkte aus einer Kategorie entfernt wurden.
* **MDVA-28511** (*für Adobe Commerce >=2.3.5 &lt;2.3.6*) - Behebung des Problems, bei dem es nicht möglich ist, [!DNL PayPal] Checkout abzuschließen, wenn das Feld &quot;Name&quot;bestimmte Zeichen enthält (z. B. Großbuchstaben).
* **MDVA-31519** (*für Adobe Commerce >=2.3.5 &lt;2.3.6*) - Behebt das Problem mit Wartezeitüberschreitungen beim Checkout beim Gast, wenn eine Site-weite Verkaufsregel verwendet wird.
* **MDVA-33281** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebung des Problems, bei dem in `inventory:reservation:list-inconsistencies` aufgrund eines falschen SKU-Parametertyps ein schwerwiegender Fehler aufgetreten ist.
* **MDVA-24201** (*für Adobe Systems Commerce >=2.3.0 &lt;2.3.5*) – Behebt das Problem, dass Preise nicht den geplanten Warenkorb Preis widerspiegeln, der Regel wird, bis die manuelle Neuindizierung erfolgt.
* **MDVA-32694** (*für Adobe Systems Commerce >=2.3.0 &lt;2.3.6 ||=&quot;&quot;>= 2.4.0 &lt;2.4.2*) – Behebt das Problem, dass ein Administrator ein Produkt User nicht zu einem verhandelbaren Angebot hinzufügen kann, wenn es sich auf eine nicht standardmäßige Geschäft bezieht.&lt;/2.3.6>
* **MDVA-33516** (*for Adobe Commerce >=2.3.0 &lt;2.3.6*) - Fixes the issue where editing a bundle product in a requisition list leads to an error.
* **MDVA-33975** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) - Fixes multiple issues related to price calculation in GraphQL requests.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*für Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass [!DNL PayPal] Abrechnungsberichte nicht wie erwartet unter **Berichte** > **Verkäufe** > **[!DNL PayPal]** Abrechnung verfügbar sind.
* **MCP-87** (*für Adobe Systems Commerce >=2.3.1 &lt;2.4.2*) - Verbesserte Indexierungszeit für Kategorie Produkt- und Aktienindexierer für große Profile.
* **MDVA-33106** (*für Adobe Systems Commerce >=2.3.0*&lt;2.4.2) - Behebt das Problem, dass die neu geplanten Produktänderungen nach der Ausführung des Cron-Befehls `run` gelöscht werden.
* **MDVA-19391** (*für Adobe Commerce >=2.3.0 &lt;2.3.5*) - Behebung des Problems, bei dem `analytics_collect_data` einen Fehler aufgrund von NULL-Beschreibungsdatensätzen in der Tabelle `catalog_category_entity_text` ausgibt.
* **MDVA-20376** (*für Adobe Systems Commerce >=2.3.2*&lt;2.3.4) - Behebt das Problem mit dem *Fehler &quot;Keine solche Entität mit customerId = 1*&quot; im `exception.log` Fehler für angemeldete Kunden nach bestellen Platzierung.
* **MDVA-23764** (*für Adobe Systems Commerce >=2.3.2*&lt;2.3.5 ) - Behebt den Fehler in `JsFooterPlugin.php` der Anzeige von dynamischen Blöcken.
* **MDVA-13203** (*für Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, bei dem der *Integritäts- beschränken Verletzung suchen_tmp_ table* error nach einer vollständigen Neuindizierung angezeigt wird.
* **MDVA-23426** (*für Adobe Systems Commerce >=2.3.3 &lt;2.3.5*) - Behebt das Problem, dass Benachrichtigung von Adobe Systems Commerce gesendeten E-Mails einen leeren Text mit Inhalte als Anhang enthalten.
* **MDVA-22150** (*für Adobe Systems Commerce >=2.3.1 &lt;2.3.4*) - Behebt das Problem, dass Kunden mit einem konfigurierbaren Produkt in Warenkorb und einem angewendeten Coupon nicht Log-in können, wenn dieses konfigurierbare Produkt im Admin deaktiviert ist.
* **MDVA-32545** (*für Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem, dass Rechnungen nicht automatisch versendet werden, wenn Bestellungen vom Administrator erstellt werden.
* **MDVA-32714** (*für Adobe Commerce >=2.3.4 &lt;2.4.1*) - Behebung des Problems, bei dem der Kundengruppenpreis in der GraphQL-Produktabfrage nicht funktioniert.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Fügt die Zwischensumme *hinzu (inkl. Tax)* -Option, um Preisregelbedingungen festzulegen.
* **MDVA-31236** (*für Adobe Commerce >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem Administratoren mit benutzerdefiniertem Ressourcenzugriff nicht in der Lage sind, 2FA einzurichten oder sich anzumelden.
* **MDVA-30845** (*für Adobe Commerce >=2.3.5 &lt;2.3.7*) - Behebung des Problems, bei dem der Fehler *Entschuldigung, dass derzeit keine Anführungszeichen für diese Bestellung verfügbar sind* angezeigt wird, wenn keine Verbindung zu UPS XML/USPS/DHL hergestellt werden kann und keine andere Versandmethode verfügbar ist.
* **MDVA-32133** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem die Mediengalerie in bestimmten Fällen nicht aus dem Seitenaufbau geladen wird.
* **MDVA-12304** (*für Adobe Commerce >=2.3.0*) - Erhöht die maximale Anzahl von Cookies von 50 auf 200.
* **MDVA-32632** (*für Adobe Commerce >=2.3.2 &lt;2.3.5*) - Behebung des Problems, bei dem Bestellungen im Zahlungssystem, aber nicht in Adobe Commerce angezeigt werden.
* **MDVA-32449** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || 2,4,0 || >=2.4.1 &lt;2.4.2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem der Auftragsverlauf sehr langsam geladen wird oder überhaupt nicht geladen wird.
* **MDVA-32739** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem durch die Aktivierung von asynchronen E-Mail-Benachrichtigungen alte E-Mails zum Vertrieb gesendet werden.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*für Adobe Systems Commerce 2.3.6, 2.4.1*) - Behebt das Problem, dass die *Erstellen eines Kontos* Button deaktiviert bleibt, nachdem ungültig Daten im *Erstellen Neu Kundenkonto-Formular* korrigiert wurden.
* **MDVA-31006** (*für Adobe Commerce 2.3.0, 2.3.1*) - Behebung des Problems, bei dem duplizierte Bestellungen nach der Bestellung mit [!DNL Paypal Express] Bezahlung angezeigt wurden.
* **MDVA-25602** (*für Adobe Commerce 2.3.0*) - Behebt ein Problem mit der [!DNL PayPal Payflow Pro] -Zahlungsmethode und behandelt Cookies standardmäßig im Chrome 80-Browser und die API-Antwort leitet zur Kundenanmeldeseite um.`SameSite=Lax`

## v1.0.10 {#v1-0-10}

Kleinere Fehlerbehebungen für Patch-Versionen

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*für Adobe Commerce >=2.3.2 &lt;2.4.2*) - Behebung des Problems, bei dem die Preisregel für Warenkorb mit Coupon nicht über GraphQL angewendet wird, wenn die Aktion *Fester Rabatt für den gesamten Warenkorb* verwendet wird.
* **MDVA-30889** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem ein Fehler auftritt, nachdem ein Bundle mit virtuellen und einfachen Produkten als Optionen berechnet wurde.
* **MDVA-31791** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Verbessert die Leistung der Produktseite, wenn Zielregeln oder verknüpfte Produkte verwendet werden.
* **MDVA-31168** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die CSV-Datei für den Produktexport nicht angezeigt wird und ein Speicherzuordnungsfehler auftritt.
* **MDVA-32313** (*für Adobe Commerce >=2.3.0 &lt;2.3.4*) - Behebung des Problems, bei dem konfigurierbare Produkte zur Wunschliste mit den falschen Konfigurationsoptionen hinzugefügt werden konnten.
* **MDVA-31759** (*für Adobe Systems Commerce >=2.3.0&lt;2.4.2*) - Behebt das Problem, dass Produkte während CSV Importvorgangs nicht mit ** Dropdown- und *Textarea-Attributwerten* aktualisiert werden.
* **MDVA-32012** (*für Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) – behebt das Problem, dass Postleitzahlen in Korea und Argentinien nicht überprüft werden können.
* **MDVA-31640** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem ein Sonderpreis nicht über die REST-API aktualisiert werden kann.
* **MDVA-28651** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 mit B2B-Erweiterung*) - Behebung des Problems, bei dem Leistungsprobleme beim Laden übertragbarer Anführungszeichen über die REST-API auftreten.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*für Adobe Commerce >=2.3.0 &lt;2.4.1 mit B2B-Erweiterung*) - Behebung des Problems, bei dem ein falsches Währungszeichen im Credit Memo-Raster angezeigt wird.
* **MDVA-31295** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die Punkte, die belohnt werden, nicht berechnet werden, wenn eine Teilbestellung abgeschlossen und die Gegenstände besteuert werden.
* **MDVA-30112** (*für Adobe Commerce >=2.3.4 &lt;2.4.2*) - Behebung des Problems, bei dem die Anzahl der Bestellungen den Wert *bunch-size* übersteigt, Adobe Commerce die Bestellungen mit dem Status *ausstehend* als Inkonsistenzen betrachtet.
* **MDVA-31150** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem die Speicher-Kredit- und Geschenkkartenguthaben nicht vom GET Invoice Rest API-Aufruf zurückgegeben werden, wenn die Rechnung durch den Rest-API-Aufruf gepostet wurde und die Bestellung teilweise von Kredit- und Geschenkartenkonten bezahlt wurde.
* **MDVA-30963** (*für Adobe Systems Commerce >=2.3.2*&lt;2.4.2) - Behebt das Problem, dass die Produktfilterergebnisse so eingestellt sind, dass sie nur Werte enthalten, die für *Alle Geschäft Ansichten*, die im Admin Umfang sind, enthalten Produkte mit Werten, die auf der Geschäft Ansicht Ebene überschrieben sind.
* **MDVA-29954** (*für Adobe Systems Commerce >=2.3.0*&lt;2.3.6 || 2.4.0 || 2.4.2 with B2B extension) - Behebt das Problem, dass die *Neu Firmenregistrierungsanfrage* und *Sie wurden mit einer Firma* verknüpft E-Mails von der falschen Adresse gesendet werden.
* **MDVA-28357 (für Adobe Systems Commerce >=2.3.2 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.1 *) – Ersetzt den Standard-Analyzer durch einen benutzerdefinierten Analyzer mit Keyword Tokenizer für das Produktnummer Feld im [!DNL ElasticSearch] Index, damit Platzhalter-suchen-Abfragen mit SKUs funktionieren, die einen Bindestrich (&quot;-&quot;) enthalten.&lt;/2.3.6>***

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem der benutzerdefinierte Bestellstatus nach der Erstellung eines Teilversands mit WebAPI in *Verarbeitung* geändert wurde.
* **MDVA-30428** (*für Adobe Commerce >=2.3.4 &lt;2.3.5*) - Behebung des Problems, bei dem Kunden kein Produkt auf die Wunschliste setzen können, wenn dieses Produkt einer benutzerdefinierten Inventarquelle zugewiesen ist.
* **MDVA-30594** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem eine Bestellung mit mehreren Adressen beim Checkout nicht gespeichert werden konnte, wenn FPT konfiguriert wurde.
* **MDVA-29148** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems beim Erstellen eines Produkts über einen API-Aufruf. Das benutzerdefinierte Produktattribut vom Typ `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (wie Multiselect) verwendet seinen Standardwert nicht, wenn in der Payload kein Wert angegeben wurde.
* **MDVA-30837** (*für Adobe Commerce >=2.3.1 &lt;2.3.5*) - Es wurde eine Konfigurationseinstellung hinzugefügt, die *Steuern auf Betrag einschließen: Ja/Nein* in der Konfiguration der kostenlosen Versandmethode festlegt. Wenn *Steuern auf Betrag einschließen* auf *Ja* gesetzt ist, wird der Mindestbestellbetrag als Zwischensumme + Steuer berechnet. Wenn *Steuern auf Betrag einbeziehen* auf *NEIN* gesetzt ist, wird der Mindestbestellbetrag als Zwischensumme berechnet
* **MDVA-25028** (*für Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Behebung des Problems, bei dem Bestellungen, die mit [!DNL PayPal Payflow Pro] aufgegeben werden, nicht auf den Status &quot;Verdächtiger Betrug&quot;gesetzt werden, wenn Betrugsfilter ausgelöst werden.
* **MDVA-31224** (*für Adobe Commerce >=2.3.3 &lt;2.3.5*) - Verbessert die Leistung des Neuindizierungsvorgangs von `catalog_product_price` für Bundle-Produkte.
* **MDVA-31321** (*für Adobe Systems Commerce >=2.3.2 &lt;2.3.5*) - Behebt einen leeren Seite (Fehler), wenn *Alle anzeigen* ausgewählt wird. [!DNL Elasticsearch] Gibt eine große Liste von Produkt-IDs zurück. In diesem Szenario wird die bestellen by-Klausel in ein falsches SQL-Format konvertiert.
* **MDVA-30815** (*für Adobe Systems Commerce >=2.3.2 &lt;2.3.4*) – Behebt das Problem, dass beim Ändern der Anzahl der suchen Ergebnisse, die auf der suchen Ergebnis-Seite angezeigt werden sollen, Adobe Systems Commerce eine leere Seite anzeigt. [!DNL Elasticsearch] zeigt Ergebnisse aus Kategorie Seiten nun korrekt an, wenn Sie die Anzahl der suchen pro Seite angezeigten Ergebnisse ändern.
* **MDVA-30782** (*für Adobe Systems Commerce >=2.3.5 &lt;2.4.2*) - Behebt das Problem, bei dem der dynamische Block unabhängig von Warenkorb Regel angezeigt wird.
* **MDVA-31021** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem Leistungsprobleme in `module-catalog-import-export/Model/Import/Product/Option.php` auftreten. Wenn die Tabelle `catalog_product_option` mehr als etwa 100.000 Datensätze enthält, dauert die Validierung einer neuen CSV mit einem einzelnen Produkt weniger als 10 Sekunden.
* **MDVA-31007** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem benutzerdefinierte Adressattribute auf der Seite mit Bestelldetails in meinem Kontobereich und im Backend nicht korrekt angezeigt werden.
* **MDVA-29389** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebt das Problem mit der erweiterten Berichterstellung, bei dem der `analytics_collect_data`-Cronjob lautet: *Port muss innerhalb des Host-Parameters konfiguriert werden (z. B. localhost:306)*.
* **MDVA-31343** (*für Adobe Commerce >=2.3.4 &lt;2.3.6*) - Behebt das Problem mit der entfernten Textklasse `page-layout-category-full-width`, wenn eine Kategorie geplant ist.
* **MDVA-30945** (*für Adobe Commerce >=2.3.0 &lt;2.4.2*) - Behebung des Problems, bei dem beim Aktualisieren von Warenkörben `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` eine schwerwiegende Fehlermeldung angezeigt wird.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*für Adobe Systems Commerce >=2.3.4&lt;2.4.0*) - Implementiert, dass die *Minimal mit Funktionen und teilweisen suchen für [!DNL Elasticsearch] die Engine übereinstimmen* sollte. Behebt Probleme mit Bindestrichen in suchen Abfragen.
* **MDVA-30102** (*für Adobe Systems Commerce >=2.3.2 &lt;=2.4.0*) – Behebt das Problem, dass der Redis-Cache schnell anwächst, da Layout-Caches keine TTL haben.
* **MDVA-30599** (*für Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Behebung des Problems, bei dem mit der API erstellte Gastangebote fälschlicherweise als Anführungszeichen für angemeldete Kunden markiert wurden.
* **MDVA-29446** (*für Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Behebung des Problems, bei dem der Preis der nicht zutreffenden Versandmethode beim Checkout als null angezeigt wird.
* **MDVA-30357** (*für Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Behebt das Problem, dass beim Generieren einer Sitemap durch Cron falsche Bild-URLs erstellt werden.
* **MDVA-30565** (*für Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Behebung des Problems, bei dem für Gastkunden beim Storefront-Checkout der Fehler *Keine Entität mit Warenkorb = 0* angezeigt wird, wenn der beständige Warenkorb aktiviert ist.
* **MDVA-29787** (*für Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Behebung des Problems, bei dem die Zielregel für verwandte Produkte nicht funktioniert, wenn *eine der* -Bedingungen verwendet wird, um anzuzeigende Produkte zu definieren.
* **MDVA-30977** (*für Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Behebt das Problem mit zufälligen Produkten, die nach der Neuindizierung aus Kategorien fehlen.
* **MDVA-28202** (*für Adobe Systems Commerce >=2.3.4 &lt;=2.4.2*) - Behebt das Problem, dass Layered Navigation konfigurierbare Produkte nicht korrekt filtert, wenn MSI verwendet wird.
* **MDVA-28300** (*für Adobe Systems Commerce >=2.3.0 &lt;2.3.6*) - Behebt das Problem, dass GQL-Anfrage die Preisänderungen aus den Katalogpreisregeln nicht widerspiegelt.
* **MDVA-31006** (*für Adobe Systems Commerce >=2.3.2*&lt;=2.4.2) - Behebt das Problem, dass duplizierte Bestellungen angezeigt werden, nachdem eine bestellen per [!DNL Paypal Express] Zahlung aufgegeben wurde.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*für Adobe Systems Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Behebt das Problem mit mehrschichtigen Navigation, bei denen der *Kein* Wert für Produktattribute vom booleschen Typ nicht in Navigation mit Ebenen enthalten war, wenn [!DNL Elasticsearch] sie als Suchmaschine verwendet wurde.
* **MDVA-28191** (*für Adobe Systems Commerce >=2.3.3 &lt;2.4.2*) - Behebt das Problem, dass während bestellen der Erstellung über den Admin keine Zahlungsmethoden geladen werden.
* **MDVA-29959** (*für Adobe Systems Commerce >=2.3.0 &lt;=2.3.3-p1 with B2B extension*) – Behebt das Problem, dass eingeschränkte Administrator-User mit *Unternehmensberechtigungen* keine Firma Konto löschen dürfen.
* **MDVA-30265** (*für Adobe Systems Commerce >=2.3.3 &lt;2.4.2*) - Behebt das Problem, dass der Versand nach der Rechnungserstellung Tracking verknüpfen nicht mehr funktioniert.
* **MDVA-28409** (*für Adobe Systems Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Behebt das Problem, dass der `sales_clean_quotes` Cron-Job mit *einem Out-of-Memory-Fehler* fehlschlägt, wenn die Anzahl der abgelaufenen Anführungszeichen in der Datenbank sehr groß ist.
* **MDVA-30593** (*für Adobe Systems Commerce >=2.3.0 &lt;2.3.4*) - Behebt das Problem, dass Angebote, die gemäß der Einstellung für die Lebensdauer von Kursen abgelaufen sind, nicht bereinigt werden.
* **MDVA-30107** (*für Adobe Systems Commerce >=2.3.0 &lt;2.3.6*) – Behebt das Problem, dass Geschäft Umschalter nicht wie erwartet funktioniert, wenn verschiedene Basis-URLs für Geschäft Ansichten verwendet werden.
* **MDVA-28763** (*für Adobe Systems Commerce >=2.3.2 &lt;2.3.4*) - Behebt das Problem, dass das Produktbild dupliziert wird, nachdem Produktinformationen mehr als einmal mithilfe der REST-API aktualisiert wurden.
* **MDVA-30284** (*für Adobe Systems Commerce >=2.3.0*&lt;2.4.2) – Behebt das Problem, bei dem der Indexer für Katalog-Search aufgrund des folgenden *[!DNL Elasticsearch]Fehlers fehlschlägt: Die maximale Anzahl der Felder insgesamt im Index wurde überschritten.*
* **MDVA-29042 (für Adobe Systems Commerce >=2.3.3 *&lt;=2.3.4-p2 with B2B extension) - Behebt das Problem, bei dem Katalogberechtigungen automatisch in Zulassen* geändert wurden, *nachdem ein neues Produkt zum freigegebenen Katalog hinzugefügt wurde.***
* **MDVA-30428** (*für Adobe Systems Commerce >=2.3.3 &lt;2.4.2*) - Behebt das Problem, dass Kunden ein Produkt nicht zur Wunschliste hinzufügen können, wenn dieses Produkt einer benutzerdefinierten Warenbestand Quelle zugewiesen ist.
* **MDVA-28661** (*für Adobe Commerce >=2.3.0 &lt;2.4.2 mit B2B-Erweiterung*) - Behebung des Problems, bei dem im Abschnitt Unternehmensbenutzerkonto für Unternehmen ein Fehler ausgegeben wird, nachdem der Unternehmensadministrator geändert wurde.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*für Adobe Commerce 2.3.1 - 2.3.4-p2*) - Behebung des Problems, bei dem Cron-Aufträge fehlschlagen, wenn der Datenbankname zu lang ist, sodass Kategorien nicht auf der Vorderseite aktualisiert werden.
* **MDVA-30106** (*für Adobe Commerce ^2.3.0*) - Behebung eines Problems, bei dem während der Kassenauszahlungen nicht mit dem Fehler *Eigenschaft &#39;length&#39; von null* gelesen werden kann, wenn in der JS-Konsole kein Fehler ausgegeben wurde.
* **MDVA-28656** (*für Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Behebung des Problems, bei dem der Bestellstatus zu *Geschlossen* statt Complete geändert wird, wenn eine Bestellung ohne Zahlungsinformationen (z. B. mit 100 % Rabatt) und eine Rechnung für die Bestellung erstellt wurde.
* **MDVA-30209** (*für Adobe Systems Commerce 2.3.0 - 2.3.3-p1*) - Behebt das Problem, dass die Kunden Gruppe auf die Standardwerte geändert wurde, wenn der Kunde seine Konto Informationen aktualisierte.
* **MDVA-30123** (*für Adobe Systems Commerce >=2.3.4 &lt;2.4.2*) - Behebt das Problem, dass Attributoptionsbeschriftungen für GraphQL-Abfragen nicht korrekt übersetzt werden.
* **MDVA-29996** (*für Adobe Systems Commerce >=2.3.3 &lt;2.4.2*) - Behebt das Problem, dass nach dem Aktivieren von Kategorie Berechtigung der Kategorie Seite nicht vom Voll Seite-Cache zwischengespeichert wird.
* **MDVA-30164** (*für Adobe Systems Commerce >=2.3.1 &lt;2.4.2*) - Behebt das Problem, bei dem Kundendatensätze nicht aus dem Kundenraster exportiert werden können, wenn benutzerdefinierte Kundenattribute vorhanden sind.
* **MDVA-30444** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebung des Problems, bei dem keine Bestätigungs-E-Mail für Bestellungen gesendet wird, die mit GraphQL aufgegeben wurden.
* **MDVA-30490** (*für Adobe Commerce 2.3.4 - 2.3.5-p2*) - Behebung des Problems, bei dem der Produktvergleich die Fehlerseite 500 ausgibt, wenn eines der Produkte eine leere Kurzbeschreibung aufweist.
* **MDVA-30232** (*für Adobe Commerce >=2.3.1 &lt;2.4.1*) - Behebung des Problems, bei dem eine Neubestellung nicht möglich ist, wenn die ursprüngliche Bestellung eine Geschenkkarte enthält.
* **MDVA-29965** (*for Adobe Commerce >=2.3.3 &lt;2.4.0*) - Fixes the issue where customers get Invalid Form Key error when adding a product to the cart.
* **MDVA-30008** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the B2B issue where it is not possible to place orders through Admin API for a product which is in a public catalog.
* **MDVA-22469** (*für Adobe Systems Commerce 2.3.2-p2 - 2.3.3-p1*) - Behebt das Problem, dass nach dem Upgrade auf Adobe Systems Commerce 2.3.3 Page Builder im Admin-Panel nicht funktioniert und einige JS- und CSS-Dateien nicht geladen werden.
* **MC-35984** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems, bei dem Händler nach dem Erstellen einer Versandbeschriftung für eine Return Merchandise Authorization (RMA) nicht mit Seitenelementen auf der Rückgabeseite interagieren konnten.

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*für Adobe Commerce 2.3.0 - 2.3.4*) - Behebt das Problem mit der [!DNL PayPal Payflow Pro] -Zahlungsmethode und behandelt Cookies standardmäßig im Chrome 80-Browser und die API-Antwort leitet zur Kundenanmeldeseite weiter.`SameSite=Lax`
* **MDVA-26694** (*für Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Behebt das Problem mit Produkt- und Katalogcaches, die täglich ablaufen, obwohl geplant ist, dass sie anders ablaufen.
* **MDVA-27825** (*für Adobe Commerce >=2.3.0 &lt;2.4.1*) - Behebung des Problems, bei dem der Export großer Datenmengen aufgrund von Speicherleck fehlgeschlagen ist.
* **MDVA-29085** (*für Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Behebung des B2B-Problems, bei dem keine neuen Unternehmens-E-Mails gesendet werden, wenn ein Unternehmen durch die API erstellt wird.
* **MDVA-29344** (*für Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Behebung des Problems, bei dem der Seitenaufbau hängen bleibt, nachdem Text aus einem Kopfzeilenelement in ein Textelement kopiert wurde.
* **MDVA-29835** (*für Adobe Commerce >2.3.1 &lt;2.4.2*) - Behebung des Problems, bei dem Bestellungen von Geschenkkarten zwei Codes anstelle eines enthielten.
* **MDVA-30052** (*für Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Behebung des Problems, bei dem private Inhalte (lokaler Speicher) nicht ordnungsgemäß ausgefüllt wurden, was zu Leistungsproblemen führte.
* **MDVA-30131** (*für Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Behebt das Problem mit der mehrschichtigen Navigation, bei dem der Wert *Nein* für boolesche Produktattribute nicht in der mehrstufigen Navigation enthalten war, wenn [!DNL Elasticsearch] als Suchmaschine verwendet wurde.
* **MDVA-35514** (*für Adobe Commerce >=2.4.0 &lt;2.4.1*) - Behebung des Problems beim Erstellen einer Versandbeschriftung und Hinzufügen bestellter Produkte zu einem Paket im modalen Fenster &quot;Pakete erstellen&quot;.
