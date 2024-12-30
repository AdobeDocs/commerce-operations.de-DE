---
title: Referenz zu personenbezogenen Daten von Kunden (Version 2.x)
description: Erfahren Sie mehr über Datenflussdiagramme und Datenbankentitätszuordnungen für personenbezogene Kundeninformationen in Adobe Commerce 2.x.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Referenz zu personenbezogenen Daten von Kunden (Version 2.x)

>[!NOTE]
>
>Dies ist eines von mehreren Themen, die Adobe Commerce-Händlern und -Entwicklern dabei helfen, sich auf die Einhaltung von Datenschutzbestimmungen vorzubereiten. Beraten Sie sich mit Ihrem Rechtsbeistand, um zu bestimmen, ob und wie Ihr Unternehmen rechtliche Verpflichtungen erfüllen sollte.

Verwenden Sie die folgenden Datenflussdiagramme und Datenbankentitätszuordnungen als Referenz bei der Entwicklung von Compliance-Programmen für Datenschutzbestimmungen, z. B.:

- [DSGVO](gdpr.md)
- [CCPA](ccpa.md)

## Datenflussdiagramme

Die Datenflussdiagramme zeigen die Datentypen, die Kundinnen und Kunden sowie Admins eingeben und von der Storefront und Admin abrufen können.

### Frontend-Dateneinstiegspunkte

Ein Benutzer kann bei der Registrierung für ein Konto, während der Kasse und bei ähnlichen Ereignissen Kunden-, Adressen- und Zahlungsinformationen eingeben.

![Frontend-Dateneinstiegspunkte](../../assets/security-compliance/frontend-data-entry-points.svg)

### Frontend-Datenzugriffspunkte

Adobe Commerce lädt Kundeninformationen, wenn sich der Kunde anmeldet und mehrere verschiedene Seiten aufruft oder auscheckt.

![Frontend-Datenzugriffspunkte](../../assets/security-compliance/frontend-data-access-points.svg)

### Backend-Dateneinstiegspunkte

Ein Händler kann beim Erstellen eines Kunden oder einer Bestellung über den Administrator Kundeninformationen, Adressdaten und Zahlungsdaten eingeben.

![Backend-Dateneinstiegspunkte](../../assets/security-compliance/backend-data-entry-points.svg)

### Backend-Datenzugriffspunkte

Adobe Commerce lädt Kundeninformationen, wenn ein Händler mehrere Rastertypen anzeigt, auf ein Raster klickt, um detaillierte Informationen anzuzeigen, und verschiedene andere Aufgaben ausführt.

![Backend-Datenzugriffspunkte](../../assets/security-compliance/backend-data-access-points.svg)

## Datenbankentitäten

Adobe Commerce speichert hauptsächlich kundenspezifische Informationen in Kunden-, Adressen-, Auftrags-, Angebots- und Zahlungstabellen. Andere Tabellen enthalten Verweise auf die Kunden-ID.

### Kundendaten

Adobe Commerce kann so konfiguriert werden, dass die folgenden Kundenattribute gespeichert werden:

- Geburtsdatum
- E-Mail
- Vorname
- Geschlecht
- Nachname
- Zweiter Vorname/Initial
- Namenspräfix
- Namensuffix

>[!NOTE]
>
>Im Einklang mit den aktuellen Best Practices für Sicherheit und Datenschutz sollten Sie sich vor der Erfassung oder Verarbeitung solcher Daten über mögliche rechtliche und Sicherheitsrisiken im Zusammenhang mit der Speicherung des vollständigen Geburtsdatums (Monat, Tag, Jahr) der Kundinnen und Kunden sowie anderer persönlicher Kennungen wie vollständiger Name im Klaren sein.

#### `customer_entity` und „customer_entity“-Verweise

Die folgenden Spalten in der `customer_entity` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | Datum |
| `gender` | Smallint(5) |

Diese Tabellen verweisen auf `customer_entity` und können benutzerdefinierte Kundenattribute enthalten:

| Tabelle | Spalte | Datentyp |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | DECIMAL(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | Text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat`

Die folgenden Spalten in der `customer_grid_flat` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| -------------------- | ------------ |
| `name` | Text |
| `email` | varchar(255) |
| `dob` | Datum |
| `gender` | int(11) |
| `shipping_full` | Text |
| `billing_full` | Text |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### Adressdaten

Adobe Commerce speichert die folgenden Kundenattribute:

- Stadt
- Firma
- Land
- Fax
- Vorname
- Nachname
- Zweiter Vorname/Initial
- Namenspräfix
- Namensuffix
- Telefonnummer
- Bundesland/Region
- Bundesland-/Regionskennung
- Adresse Straße
- Umsatzsteuer-Identifikationsnummer
- Postleitzahl

#### `customer_address_entity` und `customer_address_entity` Verweise

Die folgenden Spalten in der `customer_address_entity` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | Text |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Diese Tabellen verweisen auf `customer_address_entity` und können benutzerdefinierte Kundenattribute enthalten:

| Tabelle | Spalte | Datentyp |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | DECIMAL(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | Text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Bestelldaten

Die `sales_order` und zugehörigen Tabellen enthalten den Kundennamen, die Rechnungs- und Versandadressen sowie zugehörige Daten.

#### `sales_order`

Die folgenden Spalten in der `sales_order` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address`

Die Tabelle `sales_order_address` enthält die Adresse des Kunden.

| Spalte | Datentyp |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid`

Die folgenden Spalten in der `sales_order_grid` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Anführungsdaten

Anführungszeichen enthalten den Namen, die E-Mail-Adresse, die Adresse und die zugehörigen Informationen eines Kunden.

#### `quote`

Die folgenden Spalten in der `quote` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address`

Die folgenden Spalten in der `quote_address` Tabelle enthalten Kundeninformationen:

| Spalte | Datentyp |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### Zahlungsdaten

Die `sales_order_payment` Tabelle enthält Kreditkartenangaben und andere Transaktionsdaten.

| Spalte | Datentyp |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | Text |

### Einladungsdaten

Adobe Commerce kann so konfiguriert werden, dass Kunden Einladungen an private Verkäufe und Veranstaltungen senden können.

#### `magento_invitation`

Die Tabelle `magento_invitation` enthält die Kunden-ID, die E-Mail-Adresse und die Verweiskennung.

| Spalte | Datentyp |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track`

Die `magento_invitation_track` Tabelle enthält auch Kundeninformationen.

| Spalte | Datentyp |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Verschiedene Tabellen, die auf den Kunden verweisen

Die folgenden Tabellen enthalten eine `customer_id` Spalte:

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
