---
title: Referenz zu Kundenkonfigurationspfaden
description: Erfahren Sie mehr über Vertriebskonfigurationspfade und Variablennamen in Adobe Commerce. Admin-Einstellungen für Checkout, Versand und Steuern kennenlernen.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# Referenz zu Kundenkonfigurationspfaden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Configuration** > **Sales** verfügbar sind.

Der [`magento app:config:dump` Befehl ](../cli/export-configuration.md) diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Versionsverwaltung befinden sollte. Informationen dazu, wie Sie Konfigurationseinstellungen optional überschreiben oder vertrauliche Einstellungen festlegen können, finden Sie unter [Verwenden von Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen](override-config-settings.md#environment-variables). In diesem _werden_ ([ und systemspezifische Werte) ](config-reference-sens.md).

## Vertriebspfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkauf** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Kunden-IP ausblenden | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zwischensumme | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rabatt | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lieferung | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuer | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| feste Produktsteuer | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gesamtsumme | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkkarten | `sales/totals_sort/giftcardaccount` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Warenkredit | `sales/totals_sort/customerbalance` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuanordnung zulassen | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo für PDF Print-outs (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo für HTML Druckansicht | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adresse | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestbetrag | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuer in Betrag einbeziehen | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beschreibungsnachricht | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler zum Anzeigen im Warenkorb | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Jede Adresse separat beim Multi-Address-Checkout validieren | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Multi-Address Description Message | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Multi-Address Error to Show in Shopping Cart | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden aggregierter Daten | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer ausstehender Zahlungsaufträge (Minuten) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenknachrichten auf Auftragsebene zulassen | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenknachrichten für Bestellartikel zulassen | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkverpackung auf Auftragsebene zulassen | `sales/gift_options/wrapping_allow_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geschenkverpackung für Bestellartikel zulassen | `sales/gift_options/wrapping_allow_items` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geschenkgutschein zulassen | `sales/gift_options/allow_gift_receipt` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Gedruckte Karte zulassen | `sales/gift_options/allow_printed_card` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Standardpreis für gedruckte Karte | `sales/gift_options/printed_card_price` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| MAP aktivieren | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tatsächlichen Preis anzeigen | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmäßige Popup-Textnachricht | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmäßige Textnachricht „Was ist das?“ | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestellung nach SKU in „Mein Konto“ in der Storefront aktivieren | `sales/product_sku/my_account_enable` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schaltflächentext | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kundengruppen | `sales/product_sku/allowed_groups` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Archivierung aktivieren | `sales/magento_salesarchive/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bestellungen archivieren | `sales/magento_salesarchive/age` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zu archivierende Bestellstatus | `sales/magento_salesarchive/order_statuses` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA in Storefront aktivieren | `sales/magento_rma/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA auf Produktebene aktivieren | `sales/magento_rma/enabled_on_product` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Store-Adresse verwenden | `sales/magento_rma/use_store_address` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Verkaufs-E-Mail-Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mails** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Asynchrones Senden | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer E-Mail-Absender zur Bestellbestätigung | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Vorlage für Bestellbestätigungen | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Vorlage zur Bestellbestätigung für Gast | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für Bestellung senden | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender für Kommentar bestellen | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Bestellkommentare | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Bestellkommentar für Gast | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für Kommentare zu Bestellungen senden | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Absender der Rechnungs-E-Mail | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnung | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Rechnungsvorlage für Gast | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode zum Kopieren der Rechnung per E-Mail senden | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender für Rechnungskommentar | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnungskommentare | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Rechnungskommentare für Gäste | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode zum Senden von Rechnungskommentaren | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand-E-Mail-Absender | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandvorlage E-Mail | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Versand für Gäste | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkopie-E-Mail senden | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentar E-Mail-Absender | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentar-E-Mail-Vorlage | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkommentar-E-Mail-Vorlage für Gast | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode Versandkommentare senden | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender für Gutschrift | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Gutschrift | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Gutschrift für Gast | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für Gutschrift senden | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender für Gutschriftskommentar | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Gutschriftskommentar | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Gutschriftskommentar für Gast | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode „Gutschriftskommentare senden“ | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `sales_email/magento_rma/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA Email Sender | `sales_email/magento_rma/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Vorlage | `sales_email/magento_rma/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Vorlage für Gast | `sales_email/magento_rma/guest_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Kopiermethode senden | `sales_email/magento_rma/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales_email/magento_rma_auth/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Autorisierungs-E-Mail-Absender | `sales_email/magento_rma_auth/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Autorisierungs-E-Mail-Vorlage | `sales_email/magento_rma_auth/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Autorisierungs-E-Mail-Vorlage für Gast | `sales_email/magento_rma_auth/guest_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Autorisierungs-E-Mail-Kopiermethode senden | `sales_email/magento_rma_auth/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales_email/magento_rma_comment/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Kommentar E-Mail Absender | `sales_email/magento_rma_comment/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Kommentar-E-Mail-Vorlage | `sales_email/magento_rma_comment/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Kommentar-E-Mail-Vorlage für Gast | `sales_email/magento_rma_comment/guest_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Kopiermethode senden | `sales_email/magento_rma_comment/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `sales_email/magento_rma_customer_comment/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Kommentar E-Mail Absender | `sales_email/magento_rma_customer_comment/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Kommentar-E-Mail-Empfänger | `sales_email/magento_rma_customer_comment/recipient` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-Kommentar-E-Mail-Vorlage | `sales_email/magento_rma_customer_comment/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| RMA-E-Mail-Kopiermethode senden | `sales_email/magento_rma_customer_comment/copy_method` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Auftrags-ID in der Kopfzeile anzeigen | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Auftrags-ID in der Kopfzeile anzeigen | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Auftrags-ID in der Kopfzeile anzeigen | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Steuerpfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Steuer** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Steuerklasse für den Versand | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerklasse für Geschenkoptionen | `tax/classes/wrapping_tax_class` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Standard-Steuerklasse für Produkt | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Steuerklasse für Debitor | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerberechnungsmethode basierend auf | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerberechnung basierend auf | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Katalogpreise | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkosten | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debitorensteuer anwenden | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rabatt auf Preise anwenden | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuer auf anwenden | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grenzüberschreitenden Handel ermöglichen | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardland | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardzustand | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Postleitzahl | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produktpreise im Katalog anzeigen | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandkosten anzeigen | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise anzeigen | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zwischenergebnis anzeigen | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lieferbetrag anzeigen | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise für Geschenkverpackungen anzeigen | `tax/cart_display/gift_wrapping` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Preise für gedruckte Karten anzeigen | `tax/cart_display/printed_card` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Steuer in Bestellsumme einbeziehen | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vollständige Steuerzusammenfassung anzeigen | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Null-Steuerzwischensumme anzeigen | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise anzeigen | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zwischenergebnis anzeigen | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lieferbetrag anzeigen | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise für Geschenkverpackungen anzeigen | `tax/sales_display/gift_wrapping` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Preise für gedruckte Karten anzeigen | `tax/sales_display/printed_card` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Steuer in Bestellsumme einbeziehen | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vollständige Steuerzusammenfassung anzeigen | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Null-Steuerzwischensumme anzeigen | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FTP aktivieren | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise in Produktlisten anzeigen | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise auf der Seite „Produktansicht“ anzeigen | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise anzeigen in Verkaufsmodulen | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preise in E-Mails anzeigen | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuer auf FTP anwenden | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FTP in Zwischensumme einschließen | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Checkout-Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Checkout** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Einseitigen Checkout aktivieren | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gast-Checkout zulassen | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechnungsadresse anzeigen für | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschäftsbedingungen aktivieren | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angebotslebensdauer (Tage) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nach dem Hinzufügen einer Produktumleitung zum Warenkorb | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppiertes Produktbild | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konfigurierbares Produktbild | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorschau der Angebotslebensdauer (Minuten) | `checkout/cart/preview_quota_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Warenkorbzusammenfassung anzeigen | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Warenkorb-Seitenleiste anzeigen | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl von kürzlich hinzugefügten Elementen anzeigen | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender mit fehlgeschlagener Zahlung | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Empfänger für fehlgeschlagene Zahlung | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlage für fehlgeschlagene Zahlungen | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kopiermethode für fehlgeschlagene Zahlung senden | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pfade für Versandeinstellungen

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Versandeinstellungen** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Benutzerdefinierte Versandrichtlinie anwenden | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schifffahrtspolitik | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pfade für Mehrversandeinstellungen

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Multishipping-Einstellungen** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Versand an mehrere Adressen zulassen | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal zulässige Menge für den Versand an mehrere Adressen | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pfade von Versandmethoden

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Liefermethoden** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktiviert | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methodenname | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preis | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr berechnen | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methodenname | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestbestellmenge | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methodenname | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bedingung | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Virtuelle Produkte in die Preisberechnung einbeziehen | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Export | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| importieren | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr berechnen | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Checkout | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/ups/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| USV-Typ | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modus | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Herkunft der Sendung | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gateway-URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ausgehandelte Tarife aktivieren | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anforderungstyp des Pakets | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Container | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseinheit | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zieltyp | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximales Paketgewicht (Bitte kontaktieren Sie Ihren Spediteur für das maximal unterstützte Versandgewicht) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aufnahmemethode | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestgewicht des Pakets (Bitte fragen Sie Ihren Spediteur nach dem unterstützten Mindestgewicht für den Versand) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr berechnen | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendet | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| freie Methode | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für Versandkosten | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Checkout | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/usps/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Modus | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anforderungstyp des Pakets | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Container | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| length | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breite | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höhe | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umfang | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| bearbeitbar | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximales Paketgewicht (Bitte kontaktieren Sie Ihren Spediteur für das maximal unterstützte Versandgewicht) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr berechnen | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendet | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| freie Methode | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für Versandkosten | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| DEBUG | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Checkout | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/fedex/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web-Services-URL (Produktion) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web-Services-URL (Sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anforderungstyp des Pakets | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verpackung | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abbruch | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseinheit | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximales Paketgewicht (Bitte kontaktieren Sie Ihren Spediteur für das maximal unterstützte Versandgewicht) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr berechnen | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendet | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hauslieferung | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hub-ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| freie Methode | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für Versandkosten | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| DEBUG | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für Checkout | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert für RMA | `carriers/dhl/active_rma` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Typ | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr berechnen | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Handhabung angewendet | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bearbeitungsgebühr | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordnungsgewichtung teilen | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseinheit | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höhe | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiefe | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breite | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Methoden | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bereitschaftszeit | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Angezeigte Fehlermeldung | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| freie Methode | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| freie Methode | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für kostenlosen Versand aktivieren | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwelle für Versandkosten | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in die entsprechenden Länder | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versand in bestimmte Länder | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode anzeigen, falls nicht zutreffend | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google-API-Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Google API verfügbar**.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktivieren | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kontotyp | `google/analytics/type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren von Inhaltsexperimenten | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Listeneigenschaft für die Katalogseite | `google/analytics/catalog_page_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für den Crosssell-Block | `google/analytics/crosssell_block_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für den Upsell-Block | `google/analytics/upsell_block_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für den Block „Verwandte Produkte“ | `google/analytics/related_block_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Listeneigenschaft für die Suchergebnisseite | `google/analytics/search_page_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| &#39;Interne Promotions&#39; für das Promotions-Feld &#39;Label&#39;. | `google/analytics/promotions_list_value` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konversions-ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sprache der Konversion | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konvertierungsformat | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Farbe für Konversion | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel der Konversion | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ des Konversionswerts | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umrechnungswert | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pfade für Geschenkkarten

Diese Konfigurationswerte sind im Admin-Bereich unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Geschenkgutscheine** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| E-Mail-Absender für Geschenkkartenbenachrichtigung | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Geschenkkartenbenachrichtigung | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| einlösbar | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer (Tage) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenknachricht zulassen | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Länge der Geschenknachricht | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkkartenkonto generieren, wenn Bestellartikel nicht verfügbar ist | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender der Geschenkkarte | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschenkkartenvorlage | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codelänge | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeformat | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Präfix | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Suffix | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Strich alle X Zeichen | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neue Poolgröße | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Niedriger Code-Pool-Schwellenwert | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
