---
title: Referenz zu Zahlungskonfigurationspfaden
description: Sehen Sie sich eine Liste der konfigurierbaren Werte für Zahlungsmethoden an.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Referenz zu Zahlungskonfigurationspfaden

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden**.

Die [`magento app:config:dump` command](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei, `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte. Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](override-config-settings.md#environment-variables). Dieses Thema _not_ Liste [sensible und systemspezifische Werte](config-reference-sens.md).

Die Einstellungen werden weiter nach Zahlungsmethode organisiert.

## PayPal-Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Diese Lösung aktivieren | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren des kontextbezogenen Checkout-Erlebnisses | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-Guthaben aktivieren | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-Guthaben aktivieren | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeige | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeige | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeige | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeige | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Größe | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigen auf der Seite &quot;Produktdetails&quot; | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeige im Warenkorb | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeileneinträge aus Warenkorb übertragen | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schritt zur Überprüfung der Bestellung überspringen | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeileneinträge aus Warenkorb übertragen | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Versandoptionen übertragen | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tastenkombinationen Geschmack | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren des PayPal-Gastscheckens | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechnungsadresse des Kunden anfordern | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unterzeichnung des Abrechnungsabkommens | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeileneinträge aus Warenkorb übertragen | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Assistent für Abrechnungsvereinbarung zulassen | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisches Abrufen aktivieren | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeitplan | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tageszeit | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-Produktlogo | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seitenformat | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kopfzeilenbild-URL | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hintergrundfarbe der Kopfzeile | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rahmenfarbe für Kopfzeilen | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hintergrundfarbe der Seite | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diese Lösung aktivieren | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-Guthaben für Sortierreihenfolge | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigen auf der Seite &quot;Produktdetails&quot; | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ehrenzeitraum der Genehmigung (Tage) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gültigen Zeitraum der Bestellung (Tage) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der untergeordneten Berechtigungen | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeige im Warenkorb | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payments Pro

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| API-Authentifizierungsmethoden | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API verwendet Proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Vereinigtes Königreich)

Diese Optionen sind nur verfügbar, wenn Sie das Vereinigte Königreich als [Handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Diese Lösung aktivieren | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Express-Checkout im Schritt Zahlungsinformationen anzeigen | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Vault aktiviert | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vault-Titel | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Kreditkartentypen | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-Einstieg erforderlich | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Street stimmt nicht überein mit | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS-ZIP stimmt nicht überein mit | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Internationaler AVS-Indikator stimmt nicht überein mit | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kartensicherheitscode stimmt nicht überein mit | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anbieter | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proxy verwenden | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partner | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anbieter | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proxy verwenden | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diese Lösung aktivieren | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-Eintrag ist bearbeitbar | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-Einstieg erforderlich | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Bestätigung senden | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal-Payflow-Link

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Partner | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anbieter | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren des Payflow-Links | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Express Checkout aktivieren | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-Guthaben für Sortierreihenfolge | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beantragte Zahlung | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von den Ländern beantragte Zahlung | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-Verifizierung aktivieren | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-Eintrag ist bearbeitbar | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-Einstieg erforderlich | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Bestätigung senden | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Null Zwischensummen Checkout-Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Aktiviert | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Cash on Delivery Payment Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Aktiviert | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Zahlungspfade für Banküberweisungen

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Aktiviert | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Überprüfen oder Money Order Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Aktiviert | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie die Option Payable , um | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Bestellpfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Aktiviert | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Internationale Pfade

>[!INFO]
>
>Die verfügbaren Pfade werden durch Ihre Auswahl an [Handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| SFTP-Anmeldedaten | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diese Lösung aktivieren | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkarteneinstellungen | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie die Option Payable , um | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prüfung senden an | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_nz/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_nz/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_nz/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_nz/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_nz/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_nz/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_nz/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_nz/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_nz/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_nz/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_nz/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_nz/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_nz/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_nz/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_nz/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_nz/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_nz/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_nz/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_nz/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_nz/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_nz/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_nz/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_nz/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_nz/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_nz/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_nz/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_nz/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_nz/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_nz/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_nz/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_hk/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_hk/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_hk/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_hk/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_hk/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_hk/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_hk/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_hk/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_hk/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_hk/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_hk/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_hk/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_hk/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_hk/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_hk/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_hk/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_hk/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_hk/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_hk/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_hk/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_hk/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_hk/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_hk/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sandbox-Modus | `payment_hk/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_hk/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_hk/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_hk/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_hk/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_hk/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_hk/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie die Option Payable , um | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_es/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_es/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Profil-ID | `payment_es/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |
| Neuer Bestellstatus | `payment_es/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_es/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_es/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_es/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_es/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_es/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_es/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_es/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_es/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Installations-ID | `payment_es/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Remote Admin Installation ID | `payment_es/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_es/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_es/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_es/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_es/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_es/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_es/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_es/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_es/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_es/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_es/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_es/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_es/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_es/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_es/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_es/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_es/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_es/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_es/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_es/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_it/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_it/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_it/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_it/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_it/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_it/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_it/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_it/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_it/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_it/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_it/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_it/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_it/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_it/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_it/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_it/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_it/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_it/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_it/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_it/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_it/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_it/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_it/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_it/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_it/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_it/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_it/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_it/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_it/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_it/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_fr/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_fr/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_fr/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_fr/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_fr/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_fr/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_fr/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_fr/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_fr/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_fr/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_fr/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_fr/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_fr/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_fr/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_fr/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_fr/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_fr/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_fr/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_fr/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_fr/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_fr/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_fr/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_fr/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_fr/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_fr/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_fr/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_fr/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_fr/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_fr/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_jp/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_jp/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_jp/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_jp/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_jp/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_jp/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_jp/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_jp/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_jp/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_jp/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_jp/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_jp/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_jp/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_jp/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_jp/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_jp/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_jp/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_jp/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_jp/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_jp/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_jp/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_jp/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_jp/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_jp/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_jp/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_jp/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_jp/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_jp/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkarteneinstellungen | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie die Option Payable , um | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prüfung senden an | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_au/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_au/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Merchant-ID | `payment_au/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |
| Profil-ID | `payment_au/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |
| Neuer Bestellstatus | `payment_au/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_au/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_au/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_au/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_au/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_au/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_au/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_au/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_au/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Installations-ID | `payment_au/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_au/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_au/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_au/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_au/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_au/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_au/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_au/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_au/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_au/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_au/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_au/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_au/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_au/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_au/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_au/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_au/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_au/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_au/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_au/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_au/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diese Lösung aktivieren | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkarteneinstellungen | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkarteneinstellungen | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_ca/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_ca/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_ca/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_ca/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_ca/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_ca/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_ca/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_ca/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_ca/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_ca/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_ca/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_ca/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_ca/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_ca/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_ca/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_ca/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_ca/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_ca/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_ca/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_ca/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_ca/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_ca/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_ca/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_ca/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_ca/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_ca/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_ca/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_ca/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_ca/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Customer | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_other/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_other/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_other/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_other/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_other/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_other/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_other/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_other/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_other/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_other/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_other/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_other/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_other/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_other/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_other/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_other/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_other/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_other/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_other/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_other/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_other/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_other/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_other/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_other/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_other/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_other/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_other/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_other/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_other/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_de/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_de/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_de/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_de/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_de/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_de/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_de/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_de/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_de/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_de/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_de/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_de/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_de/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_de/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_de/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_de/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_de/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_de/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_de/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_de/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_de/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_de/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_de/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_de/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_de/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_de/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_de/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_de/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_de/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie die Option Payable , um | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_gb/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_gb/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_gb/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_gb/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_gb/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_gb/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_gb/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_gb/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_gb/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_gb/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| MD5-Geheimnis für Transaktionen | `payment_gb/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_gb/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_gb/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_gb/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_gb/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_gb/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_gb/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_gb/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_gb/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_gb/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_gb/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_gb/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_gb/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_gb/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_gb/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_gb/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_gb/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_gb/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_gb/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_gb/eway/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Geplantes Abrufen | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkarteneinstellungen | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-Guthaben aktivieren | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkarteneinstellungen | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transaktion zurückweisen, wenn: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Abrufen | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch alle Elemente einrechnen | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anweisungen | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie die Option Payable , um | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungsaktion | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Neuer Bestellstatus | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Akzeptierte Währung | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debuggen | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenarten | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkartenüberprüfung | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlung aus den betreffenden Ländern | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zahlungen aus bestimmten Ländern | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestauftragssumme | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Bestellsumme | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortierreihenfolge | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `payment_us/cybersource/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_us/cybersource/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/cybersource/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Neuer Bestellstatus | `payment_us/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_us/cybersource/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_us/cybersource/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_us/cybersource/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_us/cybersource/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mindestauftragssumme | `payment_us/cybersource/min_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Bestellsumme | `payment_us/cybersource/max_order_total` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_us/cybersource/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_us/worldpay/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/worldpay/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bearbeitung von Kontaktinformationen zulassen | `payment_us/worldpay/fix_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kontaktinformationen ausblenden | `payment_us/worldpay/hide_contact` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Signaturfelder | `payment_us/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_us/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion für Test | `payment_us/worldpay/test_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_us/worldpay/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus den betreffenden Ländern | `payment_us/worldpay/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_us/worldpay/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug für CVV&quot; | `payment_us/worldpay/cvv_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Festlegen des Bestellstatus auf &quot;Verdächtiger Betrug&quot;für Postcode AVS | `payment_us/worldpay/avs_fraud_case` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_us/worldpay/sort_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktiviert | `payment_us/eway/active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verbindungstyp | `payment_us/eway/connection_type` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/eway/title` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungsaktion | `payment_us/eway/payment_action` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Debuggen | `payment_us/eway/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kreditkartenarten | `payment_us/eway/cctypes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlung aus den betreffenden Ländern | `payment_us/eway/allowspecific` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zahlungen aus bestimmten Ländern | `payment_us/eway/specificcountry` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Sortierreihenfolge | `payment_us/eway/sort_order` |  |

{style="table-layout:auto"}
