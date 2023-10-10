---
title: Verbraucher in der Nachrichtenwarteschlange
description: Erfahren Sie mehr über die Kunden von Adobe Commerce- und Magento Open Source-Nachrichten-Warteschlangen, einschließlich der damit verbundenen Funktionen und Systemkonfigurationseinstellungen.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 11ccc59230a7a0d1768c043c39df43c7df031efd
workflow-type: tm+mt
source-wordcount: '1014'
ht-degree: 0%

---

# Verbraucher in der Nachrichtenwarteschlange

In der folgenden Tabelle werden alle Verbraucher in der Nachrichtenwarteschlange aufgeführt, ihre Funktionsweise beschrieben und die mit ihnen verbundenen Konfigurationseinstellungen des Admin-Systems identifiziert:

| Verbraucher und Beschreibung | Adobe Commerce | Adobe Commerce mit B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Erstellt Nachrichten für jede einzelne Aufgabe eines [Massenvorgang](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), wie z. B. die Ein- oder Ausfuhr von Waren, die Änderung der Preise in großem Maßstab und die Zuteilung von Erzeugnissen an ein Lager. Erforderlich, wenn die [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) ist auf **[!UICONTROL Run asynchronously]**in den Konfigurationseinstellungen des Admin-Systems. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Generiert asynchron Gutscheine im Hintergrund. Erforderlich für die Verwendung der [Batch-Gutscheingenerierung](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) Funktion. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Prüft die Ereignisse, die als Priorität in [Adobe I/O von Ereignissen für Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Verhindert Verbindungszeitüberschreitungen während der [export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) große Datensätze (z. B. 200.000 Produkte). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Korrigiert den Aktienindex asynchron, nachdem eine Bestellung platziert oder ein Produkt entfernt wurde. Erforderlich, wenn die [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) in den Admin-Konfigurationseinstellungen aktiviert ist. Siehe [Best Practices für die Leistung](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Löscht asynchron Quellelemente nach Produkt-SKU, wenn ein Produkt entfernt wird. Erforderlich, wenn die [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) Die Option stock ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Asynchron verarbeitet veraltete Lagerpositionen, aktualisiert veraltete Lagerpositionen, aktualisiert Standardquellelemente und führt Neuindizierungen für bestimmte Produkt-SKUs durch. Erforderlich, wenn die [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) Der Massenvorgang ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Löscht asynchron die Reservierungen durch die Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) Die Option stock ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Aktualisiert asynchron die Reservierungen nach der Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) Die Option stock ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aktualisiert asynchron die Verkaufsmenge jedes einem Lager zugewiesenen Produkts. Dieser Kunde sollte immer aktiv sein, wenn Sie [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Fügt die Quellelemente asynchron neu ein. Erforderlich, wenn die [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) auf &quot;[!UICONTROL asynchronous]&quot;in den Konfigurationseinstellungen des Admin-Systems. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Fügt Stock asynchron neu ein. Erforderlich, wenn die [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) auf &quot;[!UICONTROL asynchronous]&quot;in den Konfigurationseinstellungen des Admin-Systems. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Erstellt eine temporäre Datenbanktabelle, verschiebt jede [Kundensegment](https://docs.magento.com/user-guide/marketing/customer-segments.html) löscht alle Segmente, die mit der Segment-ID übereinstimmen, und kopiert sie mithilfe der Segment-ID in die Kundensegmente. Dies geschieht alles in einer Transaktion, sodass bei einem Fehlschlagen die Transaktion auf den Wert zurückgesetzt wird, der vor der Ausführung bestanden hat. Nach einer Transaktion verlässt der Kunde die temporäre Tabelle. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Stellt sicher, dass dem Asset Links zu zugewiesenen Medien für Produkte, Kategorien, CMS-Blöcke und CMS-Seiten korrekt zugewiesen sind. Entfernt nicht mehr verwendete alte Assets. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Erstellt und validiert Medien-Asset-Pfade. Der absolute Pfad zu einem Asset wird durch die Position des Assets auf dem Server aus dem Medienverzeichnis bestimmt. Die Größe von Bildern wird (bei Bedarf) geändert und in das Medienverzeichnis innerhalb des generierten Pfads kopiert. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importiert Bilddateien in die `media_gallery_asset` Datenbanktabelle. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchron [Größenanpassung](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) Katalogbilder. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Aktualisiert die Preise für verhandelbare Kurse. Erforderlich, wenn die [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asynchron [Prozessaufträge](https://developer.adobe.com/commerce/php/module-reference/module-async-order/): Markiert Bestellungen als empfangen, platziert sie in die Nachrichtenwarteschlange und verarbeitet sie in einer &quot;first-in-first-out&quot;-Phase. Als [Best Practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) zur Verbesserung der Anzahl der Bestellungen, die verarbeitet werden können, da Kunden nicht warten müssen, bis Backend-Prozesse abgeschlossen sind, bevor eine Erfolgsmeldung angezeigt wird. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| schreibt asynchron Änderungen an Produktattributen in der Datenbank, nachdem der Administrator in [Aktualisierungen vornehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| schreibt asynchron Änderungen an Produktattributen für eine bestimmte Store-Ansicht in der Datenbank, nachdem der Administrator auf [Aktualisierungen vornehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Sendet Benachrichtigungs-E-Mails über Produktpreise und Bestandsänderungen an Kunden. Erforderlich, wenn erforderlich, wenn die Variable [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Konvertiert eine Bestellung in [bestellen](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Erforderlich, wenn die [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Sendet Bestellungs-E-Mails. Erforderlich, wenn die [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Validiert die Bestellung für relevante [Validierungsregeln](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Erforderlich, wenn die [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `saveConfigProcessor` [!BADGE 2.4.7-Beta]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Nur in 2.4.7-Beta verfügbar"} | + |                         | + |
| Speichert asynchron Änderungen an der Speicherkonfiguration, indem Speicheraufträge in eine Nachrichtenwarteschlange gestellt werden, was die Leistung bei Bereitstellungen mit einer großen Anzahl von Konfigurationen auf Store-Ebene verbessern kann. Erforderlich für die Verwendung der [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) -Modul. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Verhindert die [Problem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) wobei Einzelbenutzercoupons mehrmals verwendet werden können. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Aktualisiert Kategorien, die einer freigegebenen Katalogkategorie zugewiesen sind. Erforderlich, wenn die [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Aktualisiert den Preis für jedes Produkt in einem freigegebenen Katalog. Erforderlich, wenn die [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Löscht ungültige oder inaktive Preisangebote, wenn ein Produkt aus dem Katalog gelöscht oder aus dem Warenkorb entfernt wird. Erforderlich, wenn die [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Aktualisiert aktive Warenkörbe, um die Änderungen der Preisregel für den Warenkorb widerzuspiegeln. Erforderlich für die Aktualisierung [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
