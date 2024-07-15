---
title: Referenz zu Kundenkonfigurationspfaden
description: Sehen Sie sich eine Liste der Konfigurationswerte für Kunden an.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Referenz zu Kundenkonfigurationspfaden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen im Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** verfügbar sind.

Der Befehl [`magento app:config:dump`](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte. Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Verwenden von Umgebungsvariablen zum Außerkraftsetzen von Konfigurationseinstellungen](override-config-settings.md#environment-variables). Bei diesem Thema werden _nicht_ vertrauliche und systemspezifische Werte [ aufgelistet.](config-reference-sens.md)

## Newsletter-Pfade

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Kunden** > **Newsletter** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Gastmitgliedschaft zulassen | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notwendigkeit zur Bestätigung | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Confirmation Email Sender | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestätigungs-E-Mail-Vorlage | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Success Email Sender | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erfolgs-E-Mail-Vorlage | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abmelde-E-Mail-Absender | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abmelde-E-Mail-Vorlage | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Benutzerkonfigurationspfade

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Kunden** > **Kundenkonfiguration** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Intervall für Online-Minuten | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Freigeben von Kundenkonten | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Zuweisung zur Kundengruppe aktivieren | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerberechnung auf der Grundlage | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardgruppe | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppe für gültige MwSt-ID - national | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppe für gültige MwSt-ID - Intra-Union | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppe für ungültige MwSt-ID | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validierungsfehlergruppe | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bei jeder Transaktion validieren | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardwert für &quot;Automatische Gruppenänderungen basierend auf der MwSt-ID deaktivieren&quot; | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| MwSt.-Nummer in Storefront anzeigen | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Willkommens-E-Mail | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Willkommens-E-Mail ohne Kennwort | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Sender | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestätigung von E-Mails erforderlich | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestätigungslink-E-Mail | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Willkommens-E-Mail | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerfreundliche Kunden-ID generieren | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortrücksetzschutz | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl von Anforderungen zum Zurücksetzen von Passwörtern | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Min. Zeit zwischen Kennwortrücksetzanforderungen | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage vergessen | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remind Email Template | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortvorlage zurücksetzen | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortvorlage E-Mail-Sender | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ablaufzeitraum des Wiederherstellungslinks (Stunden) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Vervollständigung bei Anmelde-/Kennwortformularen aktivieren | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der erforderlichen Zeichenklassen | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anmeldefehler beim Sperren des Kontos | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mindestlänge des Kennworts | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sperrzeit (Minuten) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der Zeilen in einer Straße | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Präfix anzeigen | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropdown-Optionen für Präfix | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorname anzeigen (initial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffix anzeigen | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffix-Dropdown-Optionen | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geburtsdatum anzeigen | `customer/address/dob_show`<br>Achten Sie in Übereinstimmung mit den aktuellen Best Practices für Sicherheit und Datenschutz darauf, dass Sie alle potenziellen rechtlichen und sicherheitstechnischen Risiken im Zusammenhang mit der Speicherung des vollständigen Geburtsdatums (Monat, Tag, Jahr) des Kunden sowie anderer persönlicher Kennungen wie vollständiger Name kennen, bevor Sie diese Daten erfassen oder verarbeiten. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuer-/MwSt-Nummer anzeigen | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschlecht anzeigen | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Funktion &quot;Store Credit&quot; | `customer/magento_customerbalance/is_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzeigen des Store-Kreditverlaufs für Kunden | `customer/magento_customerbalance/show_history` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Automatische Rückerstattungsgeschäfte | `customer/magento_customerbalance/refund_automatically` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Update der E-Mail-Adresse für Transaktionsnachrichten | `customer/magento_customerbalance/email_identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Vorlage zum Speichern von Guthaben | `customer/magento_customerbalance/email_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Umleiten des Kunden zum Konto-Dashboard nach der Anmeldung | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Text | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Text One Line | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Kundensegmentfunktion | `customer/magento_customersegment/is_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| CAPTCHA in Storefront aktivieren | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schriftart | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigemodus | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der fehlgeschlagenen Anmeldeversuche | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA-Zeitüberschreitung (Minuten) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der Symbole | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In CAPTCHA verwendete Symbole | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groß-/Kleinschreibung | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Listen-Pfade wünschen

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Kunden** > **Wunschliste** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktiviert | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren mehrerer Wunschlisten | `wishlist/general/multiple_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzahl der Wunschlisten | `wishlist/general/multiple_wishlist_number` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Email Sender | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl an gesendeten E-Mails | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Längenbeschränkung für E-Mail-Text | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zusammenfassung für Wunschlisten anzeigen | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Einladungspfade

Diese Konfigurationswerte sind im Admin unter **Speicher** > Einstellungen > **Konfiguration** > **Kunden** > **Einladungen** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktiviert die Einladungsfunktion | `magento_invitation/general/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladungen in Storefront aktivieren | `magento_invitation/general/enabled_on_front` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Referrer-Kundengruppe | `magento_invitation/general/registration_use_inviter_group` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrierung neuer Konten | `magento_invitation/general/registration_required_invitation` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunden erlauben, benutzerdefinierte Nachrichten zur Einladungs-E-Mail hinzuzufügen | `magento_invitation/general/allow_customer_message` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Anzahl an Einladungen, die gleichzeitig gesendet werden dürfen | `magento_invitation/general/max_invitation_amount_per_send` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladungs-E-Mail-Absender | `magento_invitation/email/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Vorlage für Einladungs-E-Mail für Kunden | `magento_invitation/email/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Trefferpunkte

Diese Konfigurationswerte sind im Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Belohnungspunkte** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Funktion für Rewards-Punkte aktivieren | `magento_reward/general/is_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren Sie die Funktion für Rewards-Punkte auf der Storefront. | `magento_reward/general/is_enabled_on_front` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunden können die Punkteverlauf anzeigen | `magento_reward/general/publish_history` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Schwellenwert für Rewards-Punkte | `magento_reward/general/min_points_balance` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Höchster Saldo der Ertragspunkte | `magento_reward/general/max_points_balance` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bonuspunkte laufen in (Tagen) ab | `magento_reward/general/expiration_days` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Berechnung des Ablaufs der Rewards-Punkte | `magento_reward/general/expiry_calculation` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Rückerstattungs-Prämienpunkte automatisch | `magento_reward/general/refund_automatically` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Absetzen von Prämienpunkten aus Erstattungsbetrag automatisch | `magento_reward/general/deduct_automatically` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Landingpage | `magento_reward/general/landing_page` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kauf | `magento_reward/points/order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrierung | `magento_reward/points/register` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Newsletter-Anmeldung | `magento_reward/points/newsletter` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Konvertieren der Einladung in den Kunden | `magento_reward/points/invitation_customer` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mengenbegrenzung für die Einladung zu Kundenkonversionen | `magento_reward/points/invitation_customer_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Konvertieren der Einladung in eine Bestellung | `magento_reward/points/invitation_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mengenbegrenzung für Einladung zur Bestellungsumrechnung | `magento_reward/points/invitation_order_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladung zur Konversion in Auftragsbelohnung | `magento_reward/points/invitation_order_frequency` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Übermittlungen überprüfen | `magento_reward/points/review` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mengenbegrenzung für belohnte Reviews | `magento_reward/points/review_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Email Sender | `magento_reward/notification/email_sender` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunden standardmäßig abonnieren | `magento_reward/notification/subscribe_by_default` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Bilanz-E-Mail | `magento_reward/notification/balance_update_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Warn-E-Mail zum Ablauf von Rewards-Punkten | `magento_reward/notification/expiry_warning_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verfallswarnung vor (Tage) | `magento_reward/notification/expiry_day_before` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Promotionpfade

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Kunden** > **Promotions** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Erinnerungsnachrichten aktivieren | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervall | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minute der Stunde | `promo/magento_reminder/minutes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Startzeit | `promo/magento_reminder/time` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale Anzahl an E-Mails pro Ausführung | `promo/magento_reminder/limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Schwellenwert für fehlgeschlagene E-Mail-Sendungen | `promo/magento_reminder/threshold` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Erinnerungsversand | `promo/magento_reminder/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Code-Länge | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeformat | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codepräfix | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Suffix | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle x Zeichen streichen | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Gift-Registrierungspfade

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Kunden** > **Geschenkregistrierung** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktivierung der Geschenkregistrierung | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max. Anzahl Registrierungen | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Sender | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Sender | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximaler Schwellenwert für gesendete E-Mails | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Sender | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Persistente Einkaufswagenpfade

Diese Konfigurationswerte sind im Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Persistenter Warenkorb** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktivieren der Persistenz | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer der Persistenz (Sekunden) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren Sie &quot;Angaben speichern&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardwert &quot;Angaben speichern&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Löschen der Persistenz beim Abmelden | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Warenkorb beibehalten | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wunschliste beibehalten | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kürzlich sortierte Elemente beibehalten | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktuell verglichene Produkte beibehalten | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verlauf des permanenten Vergleichs | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vor Kurzem aufgerufene Produkte beibehalten | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beibehalten der Kundengruppenmitgliedschaft und Segmentierung | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
