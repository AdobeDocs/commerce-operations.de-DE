---
title: Kunden-Konfigurationspfade - Referenz
description: Erfahren Sie mehr über Kundenkonfigurationspfade und -werte in den Adobe Commerce Admin-Einstellungen. Entdecken Sie die Optionen für Newsletter, Kontoverwaltung und Kundendienst.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Kunden-Konfigurationspfade - Referenz

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** verfügbar sind.

Der [`magento app:config:dump` Befehl &#x200B;](../cli/export-configuration.md) diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Versionsverwaltung befinden sollte. Informationen dazu, wie Sie Konfigurationseinstellungen optional überschreiben oder vertrauliche Einstellungen festlegen können, finden Sie unter [Verwenden von Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen](override-config-settings.md#environment-variables). In diesem _werden_ ([&#x200B; und systemspezifische Werte) &#x200B;](config-reference-sens.md).

## Newsletter-Pfade

Diese Konfigurationswerte sind im Admin-Bereich unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Newsletter** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Gastabonnement zulassen | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zu bestätigen | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender bestätigen | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestätigungs-E-Mail-Vorlage | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender erfolgreich | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erfolgs-E-Mail-Vorlage | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abmelde-E-Mail-Absender | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage für Abmeldung | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Kundenkonfigurationspfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Kundenkonfiguration** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Online-Minutenintervall | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kundenkonten freigeben | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Zuordnung zur Kundengruppe aktivieren | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuerberechnung basierend auf | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardgruppe | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppe für gültige MwSt.-Kennung - Inland | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppe für gültige MwSt.-ID - Innerhalb der Union | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppe für ungültige MwSt.-ID | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validierungsfehlergruppe | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bei jeder Transaktion validieren | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardwert für „Automatische Gruppenänderungen basierend auf MwSt.-ID deaktivieren“ | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| MwSt.-Nummer auf Storefront anzeigen | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Begrüßungs-E-Mail | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Begrüßungs-E-Mail ohne Passwort | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Bestätigung verlangen | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestätigungs-E-Mail | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Willkommens-E-Mail | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generieren einer benutzerfreundlichen Kunden-ID | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ des Kennwortrücksetzschutzes | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl von Anfragen zum Zurücksetzen des Kennworts | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Min. Zeit zwischen Anfragen zum Zurücksetzen des Passworts | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage vergessen | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage erinnern | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortvorlage zurücksetzen | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender für Kennwortvorlage | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gültigkeitszeitraum des Wiederherstellungs-Links (Stunden) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Vervollständigung bei Anmelde-/Kennwortformularen aktivieren | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der erforderlichen Zeichenklassen | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl an Anmeldefehlern beim Sperren des Kontos | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimale Kennwortlänge | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sperrzeit (Minuten) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der Zeilen in einer Straßenadresse | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Präfix anzeigen | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropdown-Optionen für Präfixe | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zweiter Vorname anzeigen (anfänglich) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffix anzeigen | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropdown-Optionen für Suffixe | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geburtsdatum anzeigen | `customer/address/dob_show`<br>In Übereinstimmung mit den aktuellen Best Practices für Sicherheit und Datenschutz sollten Sie sich vor der Erfassung oder Verarbeitung solcher Daten über mögliche rechtliche und Sicherheitsrisiken im Zusammenhang mit der Speicherung des vollständigen Geburtsdatums (Monat, Tag, Jahr) der Kunden zusammen mit anderen persönlichen IDs wie vollständigem Namen im Klaren sein. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Steuer-/MwSt.-Nummer anzeigen | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geschlecht anzeigen | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Funktion „Gutschrift speichern“ aktivieren | `customer/magento_customerbalance/is_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Shop-Kreditverlauf für Kunden anzeigen | `customer/magento_customerbalance/show_history` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Store-Guthaben automatisch zurückerstatten | `customer/magento_customerbalance/refund_automatically` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Absender der E-Mail zur Gutschriftenaktualisierung speichern | `customer/magento_customerbalance/email_identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Vorlage für Guthabenaktualisierung speichern | `customer/magento_customerbalance/email_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunden nach der Anmeldung zum Konto-Dashboard weiterleiten | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Text | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Text einzeilig | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Funktion „Kundensegment“ | `customer/magento_customersegment/is_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivieren von CAPTCHA in der Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schriftart | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigemodus | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl erfolgloser Anmeldeversuche | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA-Zeitüberschreitung (Minuten) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der Symbole | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In CAPTCHA verwendete Symbole | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von Schreibweise abhängig | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pfade der Wunschliste

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Wunschliste** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktiviert | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mehrere Wunschlisten aktivieren | `wishlist/general/multiple_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Anzahl mehrerer Wunschlisten | `wishlist/general/multiple_wishlist_number` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Absender | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max. zulässige E-Mails | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Längenlimit für E-Mail-Text | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zusammenfassung der Wunschlisten anzeigen | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Einladungspfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Einladungen** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Einladungsfunktion aktivieren | `magento_invitation/general/enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladungen für Storefront aktivieren | `magento_invitation/general/enabled_on_front` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Empfohlene Kundengruppe | `magento_invitation/general/registration_use_inviter_group` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrierung neuer Konten | `magento_invitation/general/registration_required_invitation` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Hinzufügen benutzerdefinierter Nachrichten zur Einladungs-E-Mail durch Kunden zulassen | `magento_invitation/general/allow_customer_message` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximal zulässige Einladungen gleichzeitig gesendet | `magento_invitation/general/max_invitation_amount_per_send` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Absender der Kundeneinladung | `magento_invitation/email/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Vorlage für Kundeneinladung | `magento_invitation/email/template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Pfade für Belohnungspunkte

Diese Konfigurationswerte sind im Admin-Bereich unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Belohnungspunkte** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Funktion für Belohnungspunkte aktivieren | `magento_reward/general/is_enabled` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Belohnungspunkte-Funktion in der Storefront aktivieren | `magento_reward/general/is_enabled_on_front` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunden können den Verlauf der Prämienpunkte sehen | `magento_reward/general/publish_history` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Schwelle für die Einlösung des Prämienpunktesaldos | `magento_reward/general/min_points_balance` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Obergrenze für Punktestand bei | `magento_reward/general/max_points_balance` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Prämienpunkte laufen in (Tagen) ab | `magento_reward/general/expiration_days` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Berechnung des Ablaufs von Prämienpunkten | `magento_reward/general/expiry_calculation` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Rewards-Punkte automatisch zurückerstatten | `magento_reward/general/refund_automatically` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Prämienpunkte automatisch vom Erstattungsbetrag abziehen | `magento_reward/general/deduct_automatically` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Landingpage | `magento_reward/general/landing_page` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kauf | `magento_reward/points/order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrierung | `magento_reward/points/register` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Newsletter-Anmeldung | `magento_reward/points/newsletter` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladung in Kunde konvertieren | `magento_reward/points/invitation_customer` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mengenbegrenzung für Einladungen zu Kundenumrechnungen | `magento_reward/points/invitation_customer_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladung in Bestellung konvertieren | `magento_reward/points/invitation_order` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mengenbegrenzung für Konversionen von Aufträgen | `magento_reward/points/invitation_order_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einladung zur Konversion zur Belohnung der Bestellung | `magento_reward/points/invitation_order_frequency` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Einreichung überprüfen | `magento_reward/points/review` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Mengenbeschränkung für die Einreichung von Reviews mit Belohnung | `magento_reward/points/review_limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Absender | `magento_reward/notification/email_sender` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunden standardmäßig abonnieren | `magento_reward/notification/subscribe_by_default` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail zur Saldoaktualisierung | `magento_reward/notification/balance_update_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail mit Ablaufwarnung für Prämienpunkte | `magento_reward/notification/expiry_warning_template` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Ablaufwarnung vor (Tagen) | `magento_reward/notification/expiry_day_before` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Promotions-Pfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Promotions** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Erinnerungsnachrichten aktivieren | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervall | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minute der Stunde | `promo/magento_reminder/minutes` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Startzeit | `promo/magento_reminder/time` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximale E-Mails pro Durchgang | `promo/magento_reminder/limit` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Fehlerschwellenwert für E-Mail-Versand | `promo/magento_reminder/threshold` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| E-Mail-Absender erinnern | `promo/magento_reminder/identity` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Codelänge | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeformat | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Präfix | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code-Suffix | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Strich alle X Zeichen | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pfade zur Geschenkregistrierung

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Geschenkregistrierung** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Geschenkregistrierung aktivieren | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal registrierte Personen | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schwellenwert für maximal gesendete E-Mails | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Persistente Warenkorbpfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Persistenter Warenkorb** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Persistenz aktivieren | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistenz-Lebensdauer (Sekunden) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| „Angaben speichern“ aktivieren | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardwert für „Angaben speichern“ | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistenz beim Abmelden löschen | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Warenkorb beibehalten | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wunschliste beibehalten | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zuletzt bestellte Artikel beibehalten | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beibehalten aktuell vergleichbarer Produkte | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vergleichsverlauf beibehalten | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zuletzt angezeigte Produkte beibehalten | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kundengruppenmitgliedschaft und Segmentierung beibehalten | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
