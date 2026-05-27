---
title: Referenz zu B2B-Erweiterungskonfigurationspfaden
description: Erfahren Sie mehr über die Konfigurationspfade und Werte von B2B-Erweiterungen für Adobe Commerce. Entdecken Sie Unternehmens-, Zahlungs-, Angebots- und B2B-spezifische Konfigurationsoptionen.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Referenz zu B2B-Erweiterungskonfigurationspfaden

_Dies ist für Instanzen verfügbar, auf denen B2B für Adobe Commerce installiert ist._

In diesem Thema werden Konfigurationspfade für die Commerce Enterprise B2B-Erweiterung aufgelistet. Der [`magento app:config:dump` Befehl &#x200B;](../cli/export-configuration.md) diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Versionsverwaltung befinden sollte.

>[!INFO]
>
>Diese Referenz listet _nur_ Konfigurationspfade auf, die für B2B für Adobe Commerce eindeutig sind. Diese Erweiterung enthält alle Konfigurationspfade für Adobe Commerce.

Diese Konfigurationspfade finden Sie unter:

- [Pfade für Zahlungskonfigurationen](config-reference-payment.md)
- [Referenz zu sensiblen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)

Informationen dazu, wie Sie Konfigurationseinstellungen optional überschreiben oder vertrauliche Einstellungen festlegen können, finden Sie unter [Verwenden von Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen](override-config-settings.md#environment-variables).

## Allgemeine Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL General]** verfügbar sind.

### B2B-Funktionspfade

Diese Konfigurationswerte sind in der Admin-Liste unter **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** verfügbar.

| -Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensibel? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Firma aktivieren | `btob/website_configuration/company_active` | | | |
| Freigegebenen Katalog aktivieren | `btob/website_configuration/sharedcatalog_active` | | | |
| B2B-Angebot aktivieren | `btob/website_configuration/negotiablequote_active` | | | |
| Schnellbestellung aktivieren | `btob/website_configuration/quickorder_active` | | | |
| Anforderungsliste aktivieren | `btob/website_configuration/requisition_list_active` | | | |
| Anwendbare Zahlungsmethoden | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| Zahlungsmethoden | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## Kundenkategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** verfügbar sind.

### Konfigurationspfade des Unternehmens

Diese Konfigurationswerte sind in der Admin-Liste unter **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]** verfügbar.

| -Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|
| Unternehmensregistrierung von der Storefront aus zulassen | `company/general/allow_company_registration` | | | |
| E-Mail-Empfänger zur Firmenregistrierung | `company/email/company_registration` | | | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail zur Unternehmensregistrierung senden an | `company/email/company_registration_copy` | | | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopiermethode senden | `company/email/company_copy_method` | | | |
| Standardmäßige E-Mail zur Unternehmensregistrierung | `company/email/company_notify_admin_template` | | | |
| Kundenbezogene E-Mails | `company/email/heading_customer` | | | |
| Standardmäßige zugewiesene Vertriebsmitarbeiter-E-Mail | `company/email/customer_sales_representative_template` | | | |
| Standardmäßige E-Mail-Adresse zur Firmenzuweisung an Kunden | `company/email/customer_company_customer_assign_template` | | | |
| Standardmäßige E-Mail-Adresse zur Unternehmensverwaltung zuweisen | `company/email/customer_assign_super_user_template` | | | |
| Standardmäßige inaktive E-Mail für Unternehmensadministrator | `company/email/customer_inactivate_super_user_template` | | | |
| Standardfirma-Admin in Abonnenten-E-Mail geändert | `company/email/customer_remove_super_user_template` | | | |
| Standardmäßige aktive E-Mail für Kundenstatus | `company/email/customer_account_activated_template` | | | |
| Standardmäßige inaktive E-Mail für Kundenstatus | `company/email/customer_account_locked_template` | | | |
| Änderung des Unternehmensstatus | `company/email/heading_company_status` | | | |
| E-Mail-Empfänger zur Änderung des Unternehmensstatus | `company/email/company_status_change` | | | |
| E-Mail zur Änderung des Unternehmensstatus senden an | `company/email/company_status_change_copy` | | | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopiermethode senden | `company/email/company_status_copy_method` | | | |
| Standardmäßige Änderung des Unternehmensstatus in „Aktive 1 E-Mail“ | `company/email/company_status_pending_approval_to_active_template` | | | |
| Standardmäßige Änderung des Unternehmensstatus in „Aktive 2 E-Mail“ | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| Standardmäßige Änderung des Unternehmensstatus in „Abgelehnte E-Mail“ | `company/email/company_status_rejected_template` | | | |
| Standardmäßige Änderung des Unternehmensstatus in „Gesperrte E-Mail“ | `company/email/company_status_blocked_template` | | | |
| Standardmäßige Änderung des Unternehmensstatus in E-Mail mit ausstehender Genehmigung | `company/email/company_status_pending_approval_template` | | | |
| Unternehmenskredit | `company/email/heading_company_credit` | | | |
| Absender der E-Mail mit Kreditänderung des Unternehmens | `company/email/company_credit_change` |  | | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail zur Änderung des Firmenkredits senden an | `company/email/company_credit_change_copy` | | | |
| E-Mail-Kopiermethode senden | `company/email/company_credit_copy_method` | | | |
| Zugewiesene E-Mail-Vorlage | `company/email/credit_allocated_email_template` | | | |
| Aktualisierte E-Mail-Vorlage | `company/email/credit_updated_email_template` | | | |
| Vorlage für zurückerstattete E-Mails | `company/email/credit_reimbursed_email_template` | | | |
| E-Mail-Vorlage für Rückerstattung | `company/email/credit_refunded_email_template` | | | |
| Zurückgesetzte E-Mail-Vorlage | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### Anforderungslisten - Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Anforderungslisten** verfügbar.

| -Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensibel? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Anzahl Anforderungslisten | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## Umsatzkategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Configuration** > **Sales** verfügbar sind.

### Verkaufs-E-Mail-Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mails** verfügbar.

| -Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensibel? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktiviert | `sales_email/quote/enabled` | | | |
| Angebotsvorlage aktualisiert (an Käufer) | `sales_email/quote/updated_buyer_template` | | | |
| Vorlage für abgelehnte Angebote (an Käufer) | `sales_email/quote/declined_buyer_template` | | | |
| Neue Angebotsvorlage (an Verkäufer) | `sales_email/quote/new_seller_template` | | | |
| Angebotsvorlage aktualisiert (an Verkäufer) | `sales_email/quote/updated_seller_template` | | | |
| Angebotsablauf (in 48 Stunden) | `sales_email/quote/expire_two_days_template` | | | |
| Angebotsablauf (in 24 Stunden) | `sales_email/quote/expire_one_day_template` | | | |
| Zurücksetzen des Ablaufdatums | `sales_email/quote/expire_reset_template` | | | |
| Angebot per E-Mail senden an | `sales_email/quote/copy_to` | | | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopiermethode für Angebot senden | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### Angebotspfade

Diese Konfigurationswerte sind im Admin-Bereich unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Quotes** verfügbar.

| -Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensibel? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Mindestbetrag | `quote/general/minimum_amount` | | | |
| Nachricht für Mindestbetrag | `quote/general/minimum_amount_message` | | | |
| Standardgültigkeitszeitraum | `quote/general/default_expiration_period` | | | |
| Dateiformate zum Hochladen | `quote/attached_files/file_formats` | | | |
| Maximale Dateigröße | `quote/attached_files/maximum_file_size` | | | |
| Mindestbetrag | `quote/general/minimum_amount` | | | |
| Nachricht für Mindestbetrag | `quote/general/minimum_amount_message` | | | |
| Standardgültigkeitszeitraum | `quote/general/default_expiration_period` | | | |
| Dateiformate zum Hochladen | `quote/attached_files/file_formats` | | | |
| Maximale Dateigröße | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## Zahlungsmethoden-Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Zahlungsmethoden** verfügbar.

>[!INFO]
>
>Die verfügbaren Pfade werden durch Ihre Wahl des Handelslandes bestimmt.

| -Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensibel? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktiviert | `payment/au/companycredit/active` | | | |
| Titel | `payment/au/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/au/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/au/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/au/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/au/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/au/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/au/companycredit/sort_order` | | | |
| Aktiviert | `payment/es/companycredit/active` | | | |
| Titel | `payment/es/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/es/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/es/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/es/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/es/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/es/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/es/companycredit/sort_order` | | | |
| Aktiviert | `payment/companycredit/active` | | | |
| Titel | `payment/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/companycredit/sort_order` | | | |
| Aktiviert | `payment/nz/companycredit/active` | | | |
| Titel | `payment/nz/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/nz/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/nz/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/nz/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/nz/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/nz/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/nz/companycredit/sort_order` | | | |
| Aktiviert | `payment/us/companycredit/active` | | | |
| Titel | `payment/us/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/us/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/us/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/us/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/us/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/us/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/us/companycredit/sort_order` | | | |
| Aktiviert | `payment/gb/companycredit/active` | | | |
| Titel | `payment/gb/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/gb/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/gb/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/gb/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/gb/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/gb/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/gb/companycredit/sort_order` | | | |
| Aktiviert | `payment/de/companycredit/active` | | | |
| Titel | `payment/de/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/de/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/de/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/de/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/de/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/de/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/de/companycredit/sort_order` | | | |
| Aktiviert | `payment/other/companycredit/active` | | | |
| Titel | `payment/other/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/other/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/other/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/other/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/other/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/other/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/other/companycredit/sort_order` | | | |
| Aktiviert | `payment/ca/companycredit/active` | | | |
| Titel | `payment/ca/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/ca/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/ca/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/ca/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/ca/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/ca/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/ca/companycredit/sort_order` | | | |
| Aktiviert | `payment/hk/companycredit/active` | | | |
| Titel | `payment/hk/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/hk/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/hk/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/hk/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/hk/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/hk/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/hk/companycredit/sort_order` | | | |
| Aktiviert | `payment/jp/companycredit/active` | | | |
| Titel | `payment/jp/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/jp/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/jp/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/jp/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/jp/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/jp/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/jp/companycredit/sort_order` | | | |
| Aktiviert | `payment/fr/companycredit/active` | | | |
| Titel | `payment/fr/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/fr/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/fr/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/fr/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/fr/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/fr/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/fr/companycredit/sort_order` | | | |
| Aktiviert | `payment/it/companycredit/active` | | | |
| Titel | `payment/it/companycredit/title` | | | |
| Neuer Bestellstatus | `payment/it/companycredit/order_status` | | | |
| Zahlung aus den entsprechenden Ländern | `payment/it/companycredit/allowspecific` | | | |
| Zahlungen aus bestimmten Ländern | `payment/it/companycredit/specificcountry` | | | |
| Mindestbestellmenge | `payment/it/companycredit/min_order_total` | | | |
| Maximale Bestellsumme | `payment/it/companycredit/max_order_total` | | | |
| Sortierreihenfolge | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
