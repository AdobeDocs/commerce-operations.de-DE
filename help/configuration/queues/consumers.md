---
title: Nachrichtenwarteschlangen-Verbraucher
description: Erfahren Sie mehr über die Verbraucher von Adobe Commerce und Magento Open Source Message Queues, einschließlich der damit verbundenen Funktionen und Systemkonfigurationseinstellungen.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Nachrichtenwarteschlangen-Verbraucher

Die folgende Tabelle identifiziert alle Nachrichtenwarteschlangen-Verbraucher, beschreibt, was sie tun, und identifiziert die mit ihnen verbundenen Admin-Systemkonfigurationseinstellungen:

| Verbraucher und Beschreibung | Adobe Commerce | Adobe Commerce mit B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Erstellt Nachrichten für jede einzelne Aufgabe eines [Massenvorgang](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), z. B. Import oder Export von Artikeln, Änderung von Preisen in großem Maßstab und Zuweisung von Produkten zu einem Lager. Erforderlich, wenn die [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) Option ist auf festgelegt **[!UICONTROL Run asynchronously]**in den Admin-Systemkonfigurationseinstellungen. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Erzeugt asynchron Gutscheine im Hintergrund. Erforderlich zur Verwendung des [Generieren von Batch-Coupons](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) Funktion. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Prüft auf Ereignisse, die in als Priorität registriert wurden. [Adobe I/O-Ereignisse für Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Verhindert Verbindungs-Timeouts während der [Export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) von großen Datensätzen (z. B. 200.000 Produkte) |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Korrigiert asynchron den Aktienindex, nachdem eine Bestellung aufgegeben oder ein Produkt entfernt wurde. Erforderlich, wenn die [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) ist in den Admin-Konfigurationseinstellungen aktiviert. Siehe [Best Practices für die Leistung](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Löscht Quellelemente asynchron nach Produkt-SKU, wenn ein Produkt entfernt wird. Erforderlich, wenn die [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) Die Stock-Option ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Asynchron verarbeitet alte Lagerartikel, aktualisiert alte Lagerartikel, aktualisiert standardmäßige Quellelemente und indiziert den Bestand für bestimmte Produkt-SKUs neu. Erforderlich, wenn die [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) Der Massenvorgang ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Löscht asynchron Reservierungen nach Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) Die Stock-Option ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Aktualisiert asynchron Reservierungen nach Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) Die Stock-Option ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aktualisiert asynchron die verkaufbare Menge jedes Produkts, das einem Lager zugewiesen ist. Dieser Verbraucher sollte immer betriebsbereit sein, wenn Sie Folgendes verwenden [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Indiziert Quellelemente asynchron neu. Erforderlich, wenn die [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) ist auf festgelegt[!UICONTROL asynchronous]&quot; in den Admin-Systemkonfigurationseinstellungen. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| indiziert Stock asynchron neu. Erforderlich, wenn die [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) ist auf festgelegt[!UICONTROL asynchronous]&quot; in den Admin-Systemkonfigurationseinstellungen. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Erstellt eine temporäre Datenbanktabelle und verschiebt jede [Kundensegment](https://docs.magento.com/user-guide/marketing/customer-segments.html) löscht alle Segmente, die mit der Segment-ID übereinstimmen, und kopiert sie mithilfe der Segment-ID als Indikator in die Kundensegmente. Dies geschieht alles in einer Transaktion, sodass die Transaktion bei einem Fehler auf den Stand vor der Ausführung zurückgesetzt wird. Nach einer Transaktion lässt der Verbraucher die temporäre Tabelle fallen. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Stellt sicher, dass Links zu zugewiesenen Medien für Produkte, Kategorien, CMS-Blöcke und CMS-Seiten dem Asset korrekt zugewiesen werden. Entfernt alte Assets, die nicht mehr verwendet werden. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Erzeugt und validiert Medien-Asset-Pfade. Der absolute Pfad zu einem Asset wird durch seine Position auf dem Server innerhalb des Medienverzeichnisses bestimmt. Die Größe der Bilder wird bei Bedarf geändert und in das Medienverzeichnis im generierten Pfad kopiert. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importiert Bilddateien in das `media_gallery_asset` Datenbanktabelle. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchron [Resize](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) Katalogbilder. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Aktualisiert Preise für verhandelbare Angebote. Erforderlich, wenn die [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asynchron [Verarbeitet Aufträge](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), die Bestellungen als eingegangen kennzeichnet, in die Warteschlange der Nachrichten stellt und sie beim First-in-First-out verarbeitet. Wird als [Best Practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) für die Verbesserung der Anzahl der Bestellungen, die verarbeitet werden können, da Kunden nicht auf den Abschluss von Backend-Prozessen warten müssen, bevor sie eine Erfolgsmeldung sehen. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Schreibt Änderungen an Produktattributen asynchron in die Datenbank, nachdem der Administrator verwendet wurde, um [Aktualisierungen vornehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Schreibt Änderungen an Produktattributen für eine bestimmte Store-Ansicht asynchron in die Datenbank, nachdem der Administrator verwendet wurde, um [Aktualisierungen vornehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Sendet Benachrichtigungs-E-Mails an Kundinnen und Kunden zu Produktpreis- und Bestandsänderungen. Erforderlich, wenn der Wert Erforderlich ist, wenn der [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Konvertiert eine Bestellung in [Reihenfolge](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Erforderlich, wenn die [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Sendet E-Mails zu Bestellungen. Erforderlich, wenn die [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Validiert eine Bestellung anhand relevanter Daten [Validierungsregeln](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Erforderlich, wenn die [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Speichert asynchron Speicherkonfigurationsänderungen, indem Speichervorgänge in einer Nachrichtenwarteschlange abgelegt werden. Dies kann die Leistung bei Bereitstellungen mit einer großen Anzahl von Konfigurationen auf Speicherebene verbessern. Erforderlich zur Verwendung des [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) Modul. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Verhindert das [Problem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) wobei Gutscheine für den einmaligen Gebrauch mehrmals verwendet werden können. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Aktualisiert Kategorien, die einer freigegebenen Katalogkategorie zugewiesen sind. Erforderlich, wenn die [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Aktualisiert den Preis für jedes Produkt in einem freigegebenen Katalog. Erforderlich, wenn die [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Löscht ungültige oder inaktive Preisangebote, wenn ein Produkt aus dem Katalog gelöscht oder aus dem Warenkorb entfernt wird. Erforderlich, wenn die [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) ist in den Konfigurationseinstellungen des Admin-Systems aktiviert. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Aktualisiert aktive Warenkörbe entsprechend den Änderungen der Warenkorbpreisregel. Erforderlich bei der Aktualisierung [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
