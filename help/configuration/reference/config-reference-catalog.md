---
title: Referenz zu Katalogkonfigurationspfaden
description: Eine Liste der Katalogkonfigurationswerte anzeigen.
feature: Configuration, Catalogs
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# Referenz zu Katalogkonfigurationspfaden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Katalog**.

Die [`magento app:config:dump` command](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei, `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte. Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](override-config-settings.md#environment-variables). Dieses Thema _not_ Liste [sensible und systemspezifische Werte](config-reference-sens.md).

## Katalogpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Katalog**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Maske für SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta-Titel maskieren | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maske für Meta-Keywords | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta-Beschreibung maskieren | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Listenmodus | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Werte für Produkte pro Seite im Raster | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardwert &quot;Produkte pro Seite im Raster&quot; | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkte pro Seite auf zulässigen Listenwerten | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkte pro Seite im Listenstandardwert | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortieren der Produktliste nach | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle Produkte pro Seite zulassen | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Einfache Katalogkategorie verwenden | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Einfache Katalogprodukte verwenden | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Farbfelder pro Produkt | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schreiben von Bewertungen | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Warnhinweis zulassen, wenn sich der Produktpreis ändert | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preiswarnungs-E-Mail-Vorlage | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Warnhinweis zulassen, wenn das Produkt wieder auf Lager ist | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stock Alert Email Template | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Warnhinweis-E-Mail-Absender | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Sender | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Vorlage | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktuell anzeigen | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardanzahl kürzlich angezeigter Produkte | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardanzahl kürzlich vergleichbarer Produkte | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grundlegendes Autostart-Video | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verknüpftes Video anzeigen | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Auto-Neustart | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Katalogpreisumfang | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardproduktpreis | `catalog/price/default_product_price` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Produktanzahl anzeigen | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnung des Preisnavigationsschritts | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schritt &quot;Standardpreisnavigation&quot; | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigen des Preisintervalls als 1 Preis | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höchstanzahl der Preisintervalle | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begrenzung der Intervallabteilung | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Tiefe | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimale Abfragelänge | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Abfragelänge | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suchmaschine | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr Server Timeout | `catalog/search/solr_server_timeout` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Indexierungsmodus | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suchvorschläge aktivieren | `catalog/search/search_suggestion_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzahl der Suchvorschläge | `catalog/search/search_suggestion_count` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Ergebnisanzahl für jeden Vorschlag anzeigen | `catalog/search/search_suggestion_count_results_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Search Recommendations aktivieren | `catalog/search/search_recommendations_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Recommendations-Anzahl durchsuchen | `catalog/search/search_recommendations_count` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Ergebnisanzahl für jede Empfehlung anzeigen | `catalog/search/search_recommendations_count_results_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestens passende Begriffe | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL-Neuschreibungen für &quot;Kategorie/Produkt&quot;generieren | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beliebte Suchbegriffe | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkt-URL-Suffix | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kategorie-URL-Suffix | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kategoriepfad für Produkt-URLs verwenden | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ständige Umleitung für URLs erstellen, wenn URL-Schlüssel geändert wurde | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seitentitel-Trennzeichen | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden des Canonical Link Meta Tags für Kategorien | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden des Canonical Link Meta Tags für Produkte | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren | `catalog/magento_catalogpermissions/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Browserkategorie zulassen | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kundengruppen | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Landingpage | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzeigen von Produktpreisen | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kundengruppen | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Hinzufügen zum Warenkorb zulassen | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kundengruppen | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Katalogsuche deaktivieren nach | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bestellelementstatus zum Aktivieren von Downloads | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmäßige maximale Anzahl von Downloads | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Teilbar | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmäßiger Beispieltitel | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Link-Titel | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Links in neuem Fenster öffnen | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Disposition verwenden | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Deaktivieren des Gastauscheckvorgangs, wenn der Warenkorb herunterladbare Elemente enthält | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript-Kalender verwenden | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reihenfolge der Datumsfelder | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeitformat | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Jahresbereich | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Funktion &quot;Katalogereignisse&quot; | `catalog/magento_catalogevent/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren des Widgets &quot;Katalogereignis&quot;auf der Storefront | `catalog/magento_catalogevent/lister_output` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzahl der Ereignisse, die im Widget &quot;Event Slider&quot;angezeigt werden | `catalog/magento_catalogevent/lister_widget_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Ereignisse zum Scroll pro Klick im Ereignis-Slider-Widget | `catalog/magento_catalogevent/lister_widget_scroll` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Anzahl von Produkten in der Liste &quot;Zugehörige Produkte&quot; | `catalog/magento_targetrule/related_position_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verwandte Produkte anzeigen | `catalog/magento_targetrule/related_position_behavior` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Rotationsmodus für Produkte in der zugehörigen Produktliste | `catalog/magento_targetrule/related_rotation_mode` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Anzahl von Produkten in der Produktliste für den Cross-Selling | `catalog/magento_targetrule/crosssell_position_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Cross-Selling-Produkte anzeigen | `catalog/magento_targetrule/crosssell_position_behavior` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Rotation Mode für Produkte in der Cross-Selling-Produktliste | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Anzahl der Produkte in der Upsell-Produktliste | `catalog/magento_targetrule/upsell_position_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Upsell-Produkte anzeigen | `catalog/magento_targetrule/upsell_position_behavior` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Rotationsmodus für Produkte in der Upsell-Produktliste | `catalog/magento_targetrule/upsell_rotation_mode` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Lagerpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Bestand**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Lagern bei Bestellung reduzieren | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Festlegen des Status von Elementen auf &quot;Auf Lager&quot;, wenn die Bestellung abgebrochen wird | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nicht vorrätige Produkte anzeigen | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nur X linke Schwelle | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produktverfügbarkeit auf Lager in Storefront anzeigen | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mit Katalog synchronisieren | `cataloginventory/options/synchronize_with_catalog` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verwalten von Lagern | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rückstände | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zurückgestellte Lageraktualisierung verwenden | `cataloginventory/item_options/use_deferred_stock_update` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale im Warenkorb zulässige Menge | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nicht vorrätiger Schwellenwert | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestens zulässige Menge im Warenkorb | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Für unten angegebene Menge benachrichtigen | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren von Qty-Schritten | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mengenerhöhungen | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Rückgabe des Credit Memo-Elements auf Lager | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Asynchron ausführen | `cataloginventory/bulk_operations/async` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Asynchrone Batch-Größe | `cataloginventory/bulk_operations/batch_size` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anbieter | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnungsmodus | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wert | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Visual Merchandising-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Visual Merchandiser**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Sichtbare Attribute für Kategorieregeln | `visualmerchandiser/options/smart_attributes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestwert-Schwelle | `visualmerchandiser/options/minimum_stock_threshold` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Farbattribut-Code | `visualmerchandiser/options/color_attribute_code` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Farbauftrag | `visualmerchandiser/options/color_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML-Sitemap-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **XML-Sitemap**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Häufigkeit | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorität | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorität | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bilder in Sitemap hinzufügen | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorität | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Sender | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Vorlage | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl von URLs pro Datei | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Dateigröße | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Übermittlung an Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS-Feed-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **RSS-Dienste**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| RSS aktivieren | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RSS aktivieren | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Produkte | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sonderprodukte | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gutscheine/Rabatte | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kategorie der obersten Ebene | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benachrichtigung zum Status von Kundenbestellungen | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Email an Freunde-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **E-Mail an einen Freund**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktiviert | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage auswählen | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gast erlauben | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max. Empfänger | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl an in 1 Stunde gesendeten Produkten | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Senden begrenzen nach | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
