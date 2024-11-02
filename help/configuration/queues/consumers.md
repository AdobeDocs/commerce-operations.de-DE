---
title: Verbraucher in der Nachrichtenwarteschlange
description: Erfahren Sie mehr über die Kunden von Adobe Commerce-Nachrichtenwarteschlangen, einschließlich der ihnen zugeordneten Funktionen und Systemkonfigurationseinstellungen.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Verbraucher in der Nachrichtenwarteschlange

In der folgenden Tabelle werden alle Verbraucher in der Nachrichtenwarteschlange aufgeführt, ihre Funktionsweise beschrieben und die mit ihnen verbundenen Konfigurationseinstellungen des Admin-Systems identifiziert:

| Verbraucher und Beschreibung | Adobe Commerce | Adobe Commerce mit B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Erstellt Nachrichten für jede einzelne Aufgabe eines [Massenvorgangs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), z. B. den Import oder Export von Artikeln, die Preisänderung in großem Maßstab und die Zuweisung von Produkten zu einem Lager. Erforderlich, wenn die Option [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) in den Konfigurationseinstellungen des Admin-Systems auf **[!UICONTROL Run asynchronously]**gesetzt ist. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Generiert asynchron Gutscheine im Hintergrund. Erforderlich für die Verwendung der Funktion [Batch-Gutscheingenerierung](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Prüft nach Ereignissen, die als Priorität in [Adobe I/O-Ereignissen für Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) registriert wurden. |
| `exportProcessor` | + | + | + |
| Verhindert Verbindungszeitüberschreitungen beim [Export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) großer Datensätze (z. B. 200.000 Produkte). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Korrigiert den Aktienindex asynchron, nachdem eine Bestellung platziert oder ein Produkt entfernt wurde. Erforderlich, wenn die Option [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) in den Admin-Konfigurationseinstellungen aktiviert ist. Siehe [Best Practices für die Leistung](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Löscht asynchron Quellelemente nach Produkt-SKU, wenn ein Produkt entfernt wird. Erforderlich, wenn die Option [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) stock in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Asynchron verarbeitet veraltete Lagerpositionen, aktualisiert veraltete Lagerpositionen, aktualisiert Standardquellelemente und führt Neuindizierungen für bestimmte Produkt-SKUs durch. Erforderlich, wenn der Massenvorgang [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Löscht asynchron die Reservierungen durch die Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die Option [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) stock in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Aktualisiert asynchron die Reservierungen nach der Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die Option [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) stock in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aktualisiert asynchron die Verkaufsmenge jedes einem Lager zugewiesenen Produkts. Dieser Verbraucher sollte immer betriebsbereit sein, wenn Sie [!DNL Inventory Management] verwenden. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Fügt die Quellelemente asynchron neu ein. Erforderlich, wenn [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) in den Konfigurationseinstellungen des Admin-Systems auf &quot;[!UICONTROL asynchronous]&quot;festgelegt ist. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Fügt Stock asynchron neu ein. Erforderlich, wenn [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) in den Konfigurationseinstellungen des Admin-Systems auf &quot;[!UICONTROL asynchronous]&quot;festgelegt ist. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Erstellt eine temporäre Datenbanktabelle, verschiebt jedes [Kundensegment](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) in sie, löscht alle Segmente, die mit der Segment-ID übereinstimmen, und kopiert sie mithilfe der Segment-ID in die Kundensegmente. Dies geschieht alles in einer Transaktion, sodass bei einem Fehlschlagen die Transaktion auf den Wert zurückgesetzt wird, der vor der Ausführung bestanden hat. Nach einer Transaktion verlässt der Kunde die temporäre Tabelle. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Stellt sicher, dass dem Asset Links zu zugewiesenen Medien für Produkte, Kategorien, CMS-Blöcke und CMS-Seiten korrekt zugewiesen sind. Entfernt nicht mehr verwendete alte Assets. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Erstellt und validiert Medien-Asset-Pfade. Der absolute Pfad zu einem Asset wird durch die Position des Assets auf dem Server aus dem Medienverzeichnis bestimmt. Die Größe von Bildern wird (bei Bedarf) geändert und in das Medienverzeichnis innerhalb des generierten Pfads kopiert. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importiert Bilddateien in die Datenbanktabelle `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchron [ändert die Größe von](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) Katalogbildern. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Aktualisiert die Preise für verhandelbare Kurse. Erforderlich, wenn die Option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asynchron verarbeitet [ Bestellungen](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), die Bestellungen als empfangen markieren, sie in die Nachrichtenwarteschlange stellen und sie in einer &quot;First-in-First-out&quot;-Basis verarbeiten. Als [Best Practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) zur Verbesserung der Anzahl der Bestellungen betrachtet, die verarbeitet werden können, da Kunden nicht warten müssen, bis Backend-Prozesse abgeschlossen sind, bevor eine Erfolgsmeldung angezeigt wird. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| schreibt asynchron Änderungen an Produktattributen in der Datenbank, nachdem der Administrator auf [make updates](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html) gesetzt wurde. |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Schreibt asynchron Änderungen an Produktattributen für eine bestimmte Store-Ansicht in der Datenbank, nachdem der Administrator [Aktualisierungen vornehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html) verwendet hat. |                |                         |                     |
| `product_alert` | + | + | + |
| Sendet Benachrichtigungs-E-Mails über Produktpreise und Bestandsänderungen an Kunden. Erforderlich, wenn die Option [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Konvertiert die Bestellung in [order](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Erforderlich, wenn die Option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Sendet Bestellungs-E-Mails. Erforderlich, wenn die Option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Validiert die Bestellung anhand der relevanten [Validierungsregeln](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules). Erforderlich, wenn die Option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Speichert asynchron Änderungen an der Speicherkonfiguration, indem Speicheraufträge in eine Nachrichtenwarteschlange gestellt werden, was die Leistung bei Bereitstellungen mit einer großen Anzahl von Konfigurationen auf Store-Ebene verbessern kann. Erforderlich für die Verwendung des [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save)-Moduls. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Verhindert das [Problem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html), bei dem Einzelbenutzercoupons mehrmals verwendet werden können. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Aktualisiert Kategorien, die einer freigegebenen Katalogkategorie zugewiesen sind. Erforderlich, wenn die Option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Aktualisiert den Preis für jedes Produkt in einem freigegebenen Katalog. Erforderlich, wenn die Option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Löscht ungültige oder inaktive Preisangebote, wenn ein Produkt aus dem Katalog gelöscht oder aus dem Warenkorb entfernt wird. Erforderlich, wenn die Option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Aktualisiert aktive Warenkörbe, um die Änderungen der Preisregel für den Warenkorb widerzuspiegeln. Erforderlich beim Aktualisieren von [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
