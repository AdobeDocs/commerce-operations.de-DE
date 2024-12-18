---
title: Referenz zu personenbezogenen Daten von Kunden (Version 1.x)
description: Erfahren Sie mehr über Datenfluss- und Datenbankentitätszuordnungen für personenbezogene Kundeninformationen in Magento 1.x.
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Referenz zu personenbezogenen Daten von Kunden (Version 1.x)

>[!NOTE]
>
>Dies ist eines von mehreren Themen, die Adobe Commerce-Händlern und -Entwicklern dabei helfen, sich auf die Einhaltung von Datenschutzbestimmungen vorzubereiten. Beraten Sie sich mit Ihrem Rechtsbeistand, um zu bestimmen, ob und wie Ihr Unternehmen rechtliche Verpflichtungen erfüllen sollte.

Verwenden Sie die folgenden Datenflussdiagramme und Datenbankentitätszuordnungen als Referenz bei der Entwicklung von Compliance-Programmen für Datenschutzbestimmungen, z. B.:

- [DSGVO](gdpr.md)
- [CCPA](ccpa.md)

## Datenflussdiagramme

Die Datenflussdiagramme zeigen die Datentypen, die Kunden und Administratoren in die Storefront und in Admin eingeben und abrufen können.

### Frontend-Dateneinstiegspunkte

Ein Benutzer kann bei der Registrierung für ein Konto, während der Kasse und bei ähnlichen Ereignissen Kunden-, Adressen- und Zahlungsinformationen eingeben.

![Frontend-Dateneinstiegspunkte](../../assets/security-compliance/frontend-data-entry-points.svg)

### Frontend-Datenzugriffspunkte

Commerce lädt Kundeninformationen, wenn sich der Kunde anmeldet und mehrere verschiedene Seiten aufruft oder auscheckt.

![Frontend-Datenzugriffspunkte](../../assets/security-compliance/frontend-data-access-points.svg)

### Backend-Dateneinstiegspunkte

Ein Händler kann Kunden-, Adressen- und Zahlungsinformationen vom Administrator eingeben, um einen Kunden oder eine Bestellung zu erstellen.

![Backend-Dateneinstiegspunkte](../../assets/security-compliance/backend-data-entry-points.svg)

### Backend-Datenzugriffspunkte

Commerce lädt Kundeninformationen, wenn ein Händler mehrere Rastertypen anzeigt, auf ein Raster klickt, um detaillierte Informationen anzuzeigen, und verschiedene andere Aufgaben ausführt.

![Backend-Datenzugriffspunkte](../../assets/security-compliance/backend-data-access-points.svg)

## Datenbankentitäten

Magento 1 speichert Kundeninformationen in Kunden-, Verkaufs- und anderen Datenbanktabellen.

### Kundendaten

Magento 1 speichert Kundeninformationen in den `customer_entity` und `customer_address_entity`. Beide Tabellen verfügen über mehrere Referenztabellen, die benutzerdefinierte Kundenattribute enthalten können.

#### `customer_entity` und Referenztabellen

Die folgenden Spalten in der `customer_entity`Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --- | --- |
| `email` | varchar(255) |

Diese Tabellen verweisen auf `customer_entity` und können benutzerdefinierte Kundenattribute enthalten:

| Tabelle | Spalte | Datentyp |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | DECIMAL(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | Text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` und Referenztabellen

Die folgenden Tabellen verweisen auf `customer_address_entity` und können benutzerdefinierte Kundenattribute enthalten:

| Tabelle | Spalte | Datentyp |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | DECIMAL(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | Text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Bestelldaten

Die `sales_flat_order` und zugehörigen Tabellen enthalten den Namen des Kunden, die Rechnungs- und Versandadressen sowie zugehörige Informationen.

#### `sales_flat_order`

Die folgenden Spalten in der `sales_order` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address`

Die Tabelle `sales_flat_order_address` enthält die Adresse des Kunden.

| Spalte | Datentyp |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | Text |

#### `sales_flat_order_grid`

Die folgenden Spalten in der `sales_flat_order_grid` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment`

Die folgenden Spalten in der `sales_flat_order_payment` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### Anführungsdaten

Anführungszeichen enthalten den Namen, die E-Mail-Adresse, die Adresse und die zugehörigen Informationen eines Kunden.

#### `sales_flat_quote`

Die folgenden Spalten in der `sales_flat_quote` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | datetime |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address`

Die folgenden Spalten in der `sales_flat_quote_address` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### `sales_flat_quote_payment`

Die `sales_flat_quote_payment` Tabelle enthält Kreditkartenangaben und andere Transaktionsdaten.

| Spalte | Datentyp |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | Smallint(5) |
| `cc_exp_year` | Smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | Smallint(5) |
| `cc_ss_start_year` | Smallint(5) |

### Archivieren von Daten

Die folgenden Tabellen und Spalten enthalten Kundeninformationen:

| Tabelle | Spalte | Datentyp |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### Verkaufsdaten

Die folgenden Tabellen und Spalten enthalten Kundeninformationen:

| Tabelle | Spalte | Datentyp |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA-Daten

Die folgenden RMA-Tabellen und -Spalten enthalten Kundeninformationen:

| Tabelle | Spalte | Datentyp |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### Sonstige Daten

Die folgenden Tabellen und Spalten enthalten Kundeninformationen:

| Tabelle | Spalte | Datentyp |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | Text |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | Smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | Text |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

Andere Tabellen, die auf Kunden verweisen:

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
