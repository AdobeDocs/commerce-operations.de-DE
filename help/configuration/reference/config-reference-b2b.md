---
title: Referenz zu Konfigurationspfaden für B2B-Erweiterungen
description: Siehe eine Liste der B2B-bezogenen Konfigurationswerte.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# Referenz zu Konfigurationspfaden für B2B-Erweiterungen

_Dies ist für Instanzen verfügbar, bei denen B2B für Adobe Commerce installiert ist._

Dieses Thema listet Konfigurationspfade für Commerce Enterprise B2B Extension auf. Die [`magento app:config:dump` command](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei, `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte.

>[!INFO]
>
>Diese Referenzliste _only_ eindeutige Konfigurationspfade für B2B für Adobe Commerce. Diese Erweiterung umfasst alle Konfigurationspfade für Adobe Commerce.

Informationen zu diesen Konfigurationspfaden finden Sie unter:

- [Zahlungskonfigurationspfade](config-reference-payment.md)
- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)

Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](override-config-settings.md#environment-variables).

## Allgemeine Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B-Funktionspfade

Diese Konfigurationswerte sind in Admin verfügbar in **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Unternehmen aktivieren | `btob/website_configuration/company_active` |  |  |  |
| Freigegebenen Katalog aktivieren | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| B2B-Angebot aktivieren | `btob/website_configuration/negotiablequote_active` |  |  |  |
| Schnellbestellung aktivieren | `btob/website_configuration/quickorder_active` |  |  |  |
| Anforderungsliste aktivieren | `btob/website_configuration/requisition_list_active` |  |  |  |
| Anwendbare Zahlungsmethoden | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| Zahlungsmethoden | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Kundenkategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Unternehmenskonfigurationspfade

Diese Konfigurationswerte sind in Admin verfügbar in **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|
| Zulassung der Firmenregistrierung über die Storefront | `company/general/allow_company_registration` |  |  |  |
| Empfänger der E-Mail-Registrierung für Unternehmen | `company/email/company_registration` |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie zur Firmenregistrierung senden an | `company/email/company_registration_copy` |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Copy-Methode senden | `company/email/company_copy_method` |  |  |  |
| Standard-E-Mail zur Firmenregistrierung | `company/email/company_notify_admin_template` |  |  |  |
| Kundenbezogene E-Mails | `company/email/heading_customer` |  |  |  |
| Standard-E-Mail für Vertriebsmitarbeiter | `company/email/customer_sales_representative_template` |  |  |  |
| Standardeinstellung &quot;Unternehmen der Kunden-E-Mail zuweisen&quot; | `company/email/customer_company_customer_assign_template` |  |  |  |
| Standardmäßige E-Mail für Unternehmensadministratorin zuweisen | `company/email/customer_assign_super_user_template` |  |  |  |
| Inaktive E-Mail für Standard-Unternehmensadministrator | `company/email/customer_inactivate_super_user_template` |  |  |  |
| Standardmäßiger Unternehmensadministrator geändert in Mitglieds-E-Mail | `company/email/customer_remove_super_user_template` |  |  |  |
| Standardmäßige aktive E-Mail zum Kundenstatus | `company/email/customer_account_activated_template` |  |  |  |
| Standard-Kundenstatus - Inaktive E-Mail | `company/email/customer_account_locked_template` |  |  |  |
| Änderung des Unternehmensstatus | `company/email/heading_company_status` |  |  |  |
| E-Mail-Empfänger zur Änderung des Firmenstatus | `company/email/company_status_change` |  |  |  |
| E-Mail-Kopie zum Ändern des Firmenstatus an senden | `company/email/company_status_change_copy` |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Copy-Methode senden | `company/email/company_status_copy_method` |  |  |  |
| Standardänderung des Firmenstatus in aktive 1 E-Mail | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| Standardänderung des Firmenstatus in aktive 2 E-Mail | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| Standardänderung des Firmenstatus in zurückgewiesene E-Mail | `company/email/company_status_rejected_template` |  |  |  |
| Standardänderung des Firmenstatus in blockierte E-Mail | `company/email/company_status_blocked_template` |  |  |  |
| Standardänderung des Firmenstatus in ausstehende Genehmigung - E-Mail | `company/email/company_status_pending_approval_template` |  |  |  |
| Firmenguthaben | `company/email/heading_company_credit` |  |  |  |
| E-Mail-Absender der Firmenkreditänderung | `company/email/company_credit_change` |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie für Firmenkreditänderung an senden | `company/email/company_credit_change_copy` |  |  |  |
| Email Copy-Methode senden | `company/email/company_credit_copy_method` |  |  |  |
| Zugewiesene E-Mail-Vorlage | `company/email/credit_allocated_email_template` |  |  |  |
| Aktualisierte E-Mail-Vorlage | `company/email/credit_updated_email_template` |  |  |  |
| Kostenerstattete E-Mail-Vorlage | `company/email/credit_reimbursed_email_template` |  |  |  |
| Zurückerstattete E-Mail-Vorlage | `company/email/credit_refunded_email_template` |  |  |  |
| Zurückgegebene E-Mail-Vorlage | `company/email/credit_reverted_email_template` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Pfade für Anforderungslisten

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Anforderungslisten**.

| Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Anzahl der Anforderungslisten | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Verkaufskategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb**.

### Pfade für Verkaufs-E-Mails

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Verkaufs-E-Mails**.

| Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktiviert | `sales_email/quote/enabled` |  |  |  |
| Aktualisierte Angebotsvorlage (für Käufer) | `sales_email/quote/updated_buyer_template` |  |  |  |
| Vorlage für deklarierte Angebote (an Käufer) | `sales_email/quote/declined_buyer_template` |  |  |  |
| Neue Anführungsvorlage (an Verkäufer) | `sales_email/quote/new_seller_template` |  |  |  |
| Aktualisierte Angebotsvorlage (an Verkäufer) | `sales_email/quote/updated_seller_template` |  |  |  |
| Anführungszeitablauf (in 48 Stunden) | `sales_email/quote/expire_two_days_template` |  |  |  |
| Anführungszeitablauf (in 24 Stunden) | `sales_email/quote/expire_one_day_template` |  |  |  |
| Ablaufdatum zurücksetzen | `sales_email/quote/expire_reset_template` |  |  |  |
| Anführungszeichen als E-Mail-Kopie senden | `sales_email/quote/copy_to` |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Anführungsmethode für E-Mail-Kopie senden | `sales_email/quote/copy_method` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Anführungspfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Anführungszeichen**.

| Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Mindestbetrag | `quote/general/minimum_amount` |  |  |  |
| Mindestbetrag | `quote/general/minimum_amount_message` |  |  |  |
| Standardgültigkeitszeitraum | `quote/general/default_expiration_period` |  |  |  |
| Dateiformate für den Upload | `quote/attached_files/file_formats` |  |  |  |
| Maximale Dateigröße | `quote/attached_files/maximum_file_size` |  |  |  |
| Mindestbetrag | `quote/general/minimum_amount` |  |  |  |
| Mindestbetrag | `quote/general/minimum_amount_message` |  |  |  |
| Standardgültigkeitszeitraum | `quote/general/default_expiration_period` |  |  |  |
| Dateiformate für den Upload | `quote/attached_files/file_formats` |  |  |  |
| Maximale Dateigröße | `quote/attached_files/maximum_file_size` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Zahlungsmethodenpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden**.

>[!INFO]
>
>Die verfügbaren Pfade werden durch Ihre Wahl des Handelslandes bestimmt.

| Name | Konfigurationspfad | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktiviert | `payment/au/companycredit/active` |  |  |  |
| Titel | `payment/au/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/au/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/au/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/au/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/au/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/au/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/au/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/es/companycredit/active` |  |  |  |
| Titel | `payment/es/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/es/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/es/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/es/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/es/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/es/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/es/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/companycredit/active` |  |  |  |
| Titel | `payment/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/nz/companycredit/active` |  |  |  |
| Titel | `payment/nz/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/nz/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/nz/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/nz/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/nz/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/nz/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/nz/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/us/companycredit/active` |  |  |  |
| Titel | `payment/us/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/us/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/us/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/us/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/us/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/us/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/us/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/gb/companycredit/active` |  |  |  |
| Titel | `payment/gb/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/gb/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/gb/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/gb/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/gb/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/gb/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/gb/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/de/companycredit/active` |  |  |  |
| Titel | `payment/de/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/de/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/de/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/de/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/de/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/de/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/de/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/other/companycredit/active` |  |  |  |
| Titel | `payment/other/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/other/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/other/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/other/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/other/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/other/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/other/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/ca/companycredit/active` |  |  |  |
| Titel | `payment/ca/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/ca/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/ca/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/ca/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/ca/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/ca/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/ca/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/hk/companycredit/active` |  |  |  |
| Titel | `payment/hk/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/hk/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/hk/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/hk/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/hk/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/hk/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/hk/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/jp/companycredit/active` |  |  |  |
| Titel | `payment/jp/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/jp/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/jp/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/jp/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/jp/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/jp/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/jp/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/fr/companycredit/active` |  |  |  |
| Titel | `payment/fr/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/fr/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/fr/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/fr/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/fr/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/fr/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/fr/companycredit/sort_order` |  |  |  |
| Aktiviert | `payment/it/companycredit/active` |  |  |  |
| Titel | `payment/it/companycredit/title` |  |  |  |
| Neuer Bestellstatus | `payment/it/companycredit/order_status` |  |  |  |
| Zahlung aus den betreffenden Ländern | `payment/it/companycredit/allowspecific` |  |  |  |
| Zahlungen aus bestimmten Ländern | `payment/it/companycredit/specificcountry` |  |  |  |
| Mindestauftragssumme | `payment/it/companycredit/min_order_total` |  |  |  |
| Maximale Bestellsumme | `payment/it/companycredit/max_order_total` |  |  |  |
| Sortierreihenfolge | `payment/it/companycredit/sort_order` |  |  |  |

{style=&quot;table-layout:auto&quot;}
