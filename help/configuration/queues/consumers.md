---
title: Nachrichtenwarteschlangen-Verbraucher
description: Erfahren Sie mehr über die Verbraucher von Adobe Commerce-Nachrichtenwarteschlangen, einschließlich der damit verbundenen Funktionen und Systemkonfigurationseinstellungen.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Nachrichtenwarteschlangen-Verbraucher

Die folgende Tabelle identifiziert alle Nachrichtenwarteschlangen-Verbraucher, beschreibt, was sie tun, und identifiziert die mit ihnen verbundenen Admin-Systemkonfigurationseinstellungen:

| Verbraucher und Beschreibung | Adobe Commerce | Adobe Commerce mit B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Erstellt Nachrichten für jede einzelne Aufgabe eines [Massenvorgangs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/) wie z. B. den Import oder Export von Artikeln, Preisänderungen im großen Maßstab und die Zuweisung von Produkten zu einem Lager. Erforderlich, wenn die Option [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) in den Admin-Systemkonfigurationseinstellungen auf **[!UICONTROL Run asynchronously]**gesetzt ist. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Asynchron generiert Coupons im Hintergrund. Erforderlich für die Verwendung der [Batch Coupon Generation](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons)-Funktion. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Sucht nach Ereignissen, die in [Adobe I/O-Ereignissen für Adobe Commerce als Priorität registriert ](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Verhindert Verbindungstimeouts beim [Export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) großer Datensätze (z. B. 200.000 Produkte). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Korrigiert asynchron den Aktienindex, nachdem eine Bestellung aufgegeben oder ein Produkt entfernt wurde. Erforderlich, wenn die Option [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) in den Admin-Konfigurationseinstellungen aktiviert ist. Siehe [Best Practices für die Leistung](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Löscht Quellelemente asynchron nach Produkt-SKU, wenn ein Produkt entfernt wird. Erforderlich, wenn die Option [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) Stock in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Verarbeitet asynchron alte Lagerartikel, aktualisiert alte Lagerartikel, aktualisiert standardmäßige Quellelemente und indiziert den Bestand für bestimmte Produkt-SKUs neu. Erforderlich, wenn der [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) Massenvorgang in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Löscht asynchron Reservierungen nach Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die Option [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) Stock in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Aktualisiert asynchron Reservierungen nach Produkt-SKU, nachdem ein Produkt entfernt wurde. Erforderlich, wenn die Option [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) Stock in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aktualisiert asynchron die verkaufbare Menge jedes Produkts, das einem Lager zugewiesen ist. Dieser Verbraucher sollte immer betriebsbereit sein, wenn Sie [!DNL Inventory Management] verwenden. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Indiziert Quellelemente asynchron neu. Erforderlich, wenn die [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) in den Admin-Systemkonfigurationseinstellungen auf &quot;[!UICONTROL asynchronous]&quot; eingestellt ist. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| indiziert Stock asynchron neu. Erforderlich, wenn die [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) in den Admin-Systemkonfigurationseinstellungen auf &quot;[!UICONTROL asynchronous]&quot; eingestellt ist. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Erstellt eine temporäre Datenbanktabelle, verschiebt jedes [Kundensegment](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) in diese, löscht alle Segmente, die mit der Segment-ID übereinstimmen, und kopiert sie unter Verwendung der Segment-ID als Indikator in die Kundensegmente. Dies geschieht alles in einer Transaktion, sodass die Transaktion bei einem Fehler auf den Stand vor der Ausführung zurückgesetzt wird. Nach einer Transaktion lässt der Verbraucher die temporäre Tabelle fallen. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Stellt sicher, dass Links zu zugewiesenen Medien für Produkte, Kategorien, CMS-Blöcke und CMS-Seiten korrekt dem Asset zugewiesen werden. Entfernt alte Assets, die nicht mehr verwendet werden. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Erzeugt und validiert Medien-Asset-Pfade. Der absolute Pfad zu einem Asset wird durch seine Position auf dem Server innerhalb des Medienverzeichnisses bestimmt. Die Größe der Bilder wird bei Bedarf geändert und in das Medienverzeichnis im generierten Pfad kopiert. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importiert Bilddateien in die `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [ändert](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) Katalogbilder asynchron |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Aktualisiert Preise für verhandelbare Angebote. Erforderlich, wenn die Option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Verarbeitet asynchron [Bestellungen](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), die Bestellungen als empfangen markieren, platziert sie in der Nachrichtenwarteschlange und verarbeitet sie als „first-in-first-out“. wurde als [Best Practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) für die Verbesserung der Anzahl der Bestellungen betrachtet, die verarbeitet werden können, da Kunden nicht auf den Abschluss von Backend-Prozessen warten müssen, bevor sie eine Erfolgsmeldung sehen. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Schreibt Änderungen an Produktattributen asynchron in die Datenbank, nachdem der Administrator verwendet wurde, um [Aktualisierungen vorzunehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Schreibt Änderungen an Produktattributen für eine bestimmte Store-Ansicht asynchron in die Datenbank, nachdem der Administrator verwendet wurde, um [Aktualisierungen vorzunehmen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Sendet Benachrichtigungs-E-Mails an Kundinnen und Kunden zu Produktpreis- und Bestandsänderungen. Erforderlich, wenn die Option Erforderlich, wenn die Option [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) in den Admin-Systemkonfigurationseinstellungen aktiviert ist. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Konvertiert eine Bestellung in [Bestellung](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Erforderlich, wenn die Option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Sendet E-Mails zu Bestellungen. Erforderlich, wenn die Option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Validiert eine Bestellung anhand der relevanten [Genehmigungsregeln](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules). Erforderlich, wenn die Option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Speichert asynchron Änderungen an der Speicherkonfiguration, indem Speicheraufträge in einer Nachrichtenwarteschlange abgelegt werden. Dies kann die Leistung bei Bereitstellungen mit einer großen Anzahl von Konfigurationen auf Speicherebene verbessern. Erforderlich für die Verwendung des [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Verhindert ein Problem, bei dem Gutscheine für den einmaligen Gebrauch mehrmals verwendet werden können. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Aktualisiert Kategorien, die einer freigegebenen Katalogkategorie zugewiesen sind. Erforderlich, wenn die Option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Aktualisiert den Preis für jedes Produkt in einem freigegebenen Katalog. Erforderlich, wenn die Option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Löscht ungültige oder inaktive Preisangebote, wenn ein Produkt aus dem Katalog gelöscht oder aus dem Warenkorb entfernt wird. Erforderlich, wenn die Option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) in den Konfigurationseinstellungen des Admin-Systems aktiviert ist. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Aktualisiert aktive Warenkörbe entsprechend den Änderungen der Warenkorbpreisregel. Erforderlich beim Aktualisieren von [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
