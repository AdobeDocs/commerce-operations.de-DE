---
title: Referenz zu Speicherkonfigurationspfaden
description: Sehen Sie sich eine Liste der Verkaufskonfigurationswerte an.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# Referenz zu Speicherkonfigurationspfaden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb**.

Die [`magento app:config:dump` command](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei, `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte. Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](override-config-settings.md#environment-variables). Dieses Thema _not_ Liste [sensible und systemspezifische Werte](config-reference-sens.md).

## Verkaufswege

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Vertrieb**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Kunden-IP ausblenden | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zwischensumme | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rabatt | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuern | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Feste Produktsteuer | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gesamtsumme | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkkarten | `sales/totals_sort/giftcardaccount` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Store-Guthaben | `sales/totals_sort/customerbalance` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuanordnung zulassen | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo für PDF Print-outs (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo für HTML Print View | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adresse | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestbetrag | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuern auf Betrag einschließen | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beschreibung | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler beim Anzeigen im Warenkorb | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Jede Adresse separat in der Checkout-Funktion für mehrere Adressen validieren | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nachricht mit mehreren Adressen - Beschreibung | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler bei mehreren Adressen, der im Warenkorb angezeigt wird | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aggregierte Daten verwenden | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer der ausstehenden Zahlungsaufträge (Minuten) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkgutachten auf Bestellebene zulassen | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulassen von Geschenk-Nachrichten für Bestellelemente | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkverpackung auf Bestellebene zulassen | `sales/gift_options/wrapping_allow_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geschenkverpackung für Bestellartikel zulassen | `sales/gift_options/wrapping_allow_items` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geschenkgutschein zulassen | `sales/gift_options/allow_gift_receipt` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Drucken-Karte zulassen | `sales/gift_options/allow_printed_card` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Standardpreis für gedruckte Karte | `sales/gift_options/printed_card_price` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| MAP aktivieren | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tatsächlichen Preis anzeigen | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmäßige Popup-Textmeldung | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmäßige Textmeldung &quot;Was ist das?&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie &quot;Bestellung durch SKU&quot;für Mein Konto im Storefront | `sales/product_sku/my_account_enable` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schaltflächentext | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kundengruppen | `sales/product_sku/allowed_groups` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren der Archivierung | `sales/magento_salesarchive/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Erworbene Archivaufträge | `sales/magento_salesarchive/age` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zu archivierende Bestellstatus | `sales/magento_salesarchive/order_statuses` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA in Storefront aktivieren | `sales/magento_rma/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA auf Produktebene aktivieren | `sales/magento_rma/enabled_on_product` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Store-Adresse verwenden | `sales/magento_rma/use_store_address` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## E-Mail-Pfade für Vertrieb

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Verkaufs-E-Mails**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Asynchrones Senden | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer E-Mail-Absender für Auftragsbestätigungen | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Vorlage für Auftragsbestätigungen | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Vorlage für Bestellbestätigungen für Gastbenutzer | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode zum Kopieren einer E-Mail-Bestellung | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender für Bestellkommentare | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Bestellkommentare | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Bestellkommentare für Gastbenutzer | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für Bestellkommentare senden | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechnungsversand | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnung | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnung für Gastbenutzer | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode &quot;Rechnung senden&quot; | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechnungskommentar-E-Mail-Absender | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnungskommentare | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnungskommentare für Gastbenutzer | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für Rechnungskommentare senden | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand-E-Mail-Absender | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand-E-Mail-Vorlage | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand-E-Mail-Vorlage für Gast | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandversand-E-Mail-Kopiermethode | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentar-E-Mail-Absender | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentar-E-Mail-Vorlage | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentar-E-Mail-Vorlage für Gast | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentare-E-Mail-Kopiermethode senden | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credit Memo Email Sender | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email-Vorlage für Credit Memo | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email-Vorlage für Credit Memo für Gastbenutzer | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode &quot;Credit Memo senden&quot; | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credit Memo Kommentar E-Mail-Sender | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Kommentar zu Credit Memo | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Kommentar-Kommentar für Gastbenutzer | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für Credit Memo-Kommentare senden | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/magento_rma/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Email Sender | `sales_email/magento_rma/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Vorlage | `sales_email/magento_rma/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Vorlage für Gastbenutzer | `sales_email/magento_rma/guest_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Kopiermethode senden | `sales_email/magento_rma/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales_email/magento_rma_auth/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Authorization Email Sender | `sales_email/magento_rma_auth/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Authorization Email Template | `sales_email/magento_rma_auth/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Autorisierungs-E-Mail-Vorlage für Gastbenutzer | `sales_email/magento_rma_auth/guest_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Autorisierungs-E-Mail-Kopiermethode senden | `sales_email/magento_rma_auth/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales_email/magento_rma_comment/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Comment Email Sender | `sales_email/magento_rma_comment/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Comment Email Template | `sales_email/magento_rma_comment/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Kommentar-E-Mail-Vorlage für Gastbenutzer | `sales_email/magento_rma_comment/guest_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Kopiermethode senden | `sales_email/magento_rma_comment/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales_email/magento_rma_customer_comment/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Comment Email Sender | `sales_email/magento_rma_customer_comment/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Kommentar-E-Mail-Empfänger | `sales_email/magento_rma_customer_comment/recipient` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Comment Email Template | `sales_email/magento_rma_customer_comment/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Kopiermethode senden | `sales_email/magento_rma_customer_comment/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzeigen der Auftrags-ID in der Kopfzeile | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigen der Auftrags-ID in der Kopfzeile | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigen der Auftrags-ID in der Kopfzeile | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Steuerpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Steuern**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Steuerklasse für den Versand | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerklasse für Geschenkoptionen | `tax/classes/wrapping_tax_class` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Standardsteuerklasse für das Produkt | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardsteuerklasse für Kunden | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerberechnungsmethode basierend auf | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerberechnung auf der Grundlage | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Katalogpreise | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkosten | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kundensteuer anwenden | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rabatt auf Preise anwenden | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuern auf | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grenzüberschreitenden Handel aktivieren | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardland | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardstatus | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Postleitzahl | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigen von Produktpreisen im Katalog | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandpreise anzeigen | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigepreise | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zwischensumme anzeigen | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandbetrag anzeigen | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkpreise anzeigen | `tax/cart_display/gift_wrapping` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Preise für gedruckte Karten anzeigen | `tax/cart_display/printed_card` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Steuern in Bestellsumme einschließen | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vollständige Steuerübersicht anzeigen | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Untersumme ohne Steuern anzeigen | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigepreise | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zwischensumme anzeigen | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandbetrag anzeigen | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkpreise anzeigen | `tax/sales_display/gift_wrapping` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Preise für gedruckte Karten anzeigen | `tax/sales_display/printed_card` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Steuern in Bestellsumme einschließen | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vollständige Steuerübersicht anzeigen | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Untersumme ohne Steuern anzeigen | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT aktivieren | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigepreise in Produktlisten | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigepreise auf der Produktansichtsseite | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigepreise in Verkaufsmodulen | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigepreise in E-Mails | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuern auf FPT anwenden | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT in Zwischensumme einschließen | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Checkout-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Checkout**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktivieren des Einseitige Checkout | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gastauschecken zulassen | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechnungsadresse anzeigen auf | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nutzungsbedingungen aktivieren | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anführungszeitraum (Tage) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nach Hinzufügen einer Produktumleitung zum Warenkorb | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppiertes Produktbild | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konfigurierbares Produktbild | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorschau der Anführungszeichenlebensdauer (Minuten) | `checkout/cart/preview_quota_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Warenkorbzusammenfassung anzeigen | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symbolleiste des Warenkorbs anzeigen | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zuletzt hinzugefügte Elemente maximal anzeigen | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsfehler beim E-Mail-Absender | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsfehler beim E-Mail-Empfänger | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlage für Zahlung fehlgeschlagen | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorgang &quot;Send Payment Failed Email Copy&quot; | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Versandeinstellungspfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Versandeinstellungen**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Benutzerdefinierte Versandrichtlinie anwenden | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandpolitik | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Mehrere Einstellungspfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Multishipping-Einstellungen**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Versand an mehrere Adressen zulassen | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale zulässige Menge für den Versand an mehrere Adressen | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Versandmethoden-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Versandmethoden**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktiviert | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Name der Methode | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preis | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnete Bereitstellungsgebühr | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Name der Methode | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragsbetrag | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Name der Methode | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bedingung | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Virtual Products in Preisberechnung einbeziehen | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Export | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Import | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnete Bereitstellungsgebühr | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Kasse | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/ups/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| UPS-Typ | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modus | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Herkunft der Sendung | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gateway-URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandlungsraten aktivieren | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paketanforderungstyp | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Container | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseinheit | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zieltyp | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Paketgewichtung (Bitte konsultieren Sie Ihren Versandunternehmen für maximal unterstützte Versandgewichtung) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abnahmemethode | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestpaketgewichtung (Bitte konsultieren Sie Ihren Versandunternehmen für ein Mindestunterstütztes Versandgewicht) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnete Bereitstellungsgebühr | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendeter | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kostenlose Methode | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Kasse | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/usps/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Modus | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paketanforderungstyp | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Container | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Länge | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breite | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höhe | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mädchen | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Machbar | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Paketgewichtung (Bitte konsultieren Sie Ihren Versandunternehmen für maximal unterstützte Versandgewichtung) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnete Bereitstellungsgebühr | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendeter | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kostenlose Methode | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Kasse | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/fedex/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web-Services-URL (Produktion) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web-Services-URL (Sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paketanforderungstyp | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verpackung | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropoff | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseinheit | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Paketgewichtung (Bitte konsultieren Sie Ihren Versandunternehmen für maximal unterstützte Versandgewichtung) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnete Bereitstellungsgebühr | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendeter | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bereitstellung von Wohnraum | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hub-ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kostenlose Methode | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Kasse | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/dhl/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Typ | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berechnete Bereitstellungsgebühr | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendeter | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtung der Teilungsreihenfolge | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseinheit | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höhe | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiefe | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breite | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bereitstellungszeit | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kostenlose Methode | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kostenlose Methode | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in die betreffenden Länder | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schiff in bestimmte Länder | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierfolge | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Google-API**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktivieren | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kontotyp | `google/analytics/type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren von Inhaltsexperimenten | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Listeneigenschaft für die Katalogseite | `google/analytics/catalog_page_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für den Cross-Sell-Block | `google/analytics/crosssell_block_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für den Up-Sell-Block | `google/analytics/upsell_block_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für den zugehörigen Produktblock | `google/analytics/related_block_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für die Suchergebnisseite | `google/analytics/search_page_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| &#39;Interne Promotions&#39; für das Feld &quot;Promotions&quot;. | `google/analytics/promotions_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konversions-ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konversionssprache | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konvertierungsformat | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konvertierungsfarbe | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konversionsbezeichnung | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konversionswerttyp | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konversionswert | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Gift-Karten-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Geschenkkarten**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Benachrichtigungs-E-Mail-Absender von Geschenkkarten | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Benachrichtigungs-E-Mails zu Geschenkkarten | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ersetzen | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer (Tage) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenknachricht zulassen | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Länge der Geschenkmeldung | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gift-Kartenkonto erstellen, wenn Bestellelement | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gift Card Email Sender | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gift-Kartenvorlage | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Länge | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeformat | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codepräfix | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Suffix | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle x Zeichen streichen | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Poolgröße | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Niedriger Code-Pool-Schwellenwert | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
