---
title: Referenz zu allgemeinen Konfigurationspfaden
description: Sehen Sie sich eine Liste mit allgemeinen und erweiterten Konfigurationswerten an.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Referenz zu allgemeinen und erweiterten Konfigurationspfaden

Dieses Thema listet allgemeine und erweiterte Konfigurationspfade auf und _not_ [sensible und systemspezifische Werte](config-reference-sens.md). Die [`magento app:config:dump` command](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei, `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte.

Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](override-config-settings.md#environment-variables).

## Allgemeine Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein**.

### Allgemeine Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.

| Name | Konfigurationspfad | Nur Commerce? | Sensitiv? |
|--------------|--------------|--------------|--------------|
| Standardland | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Länder zulassen | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Postleitzahl ist optional für | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Länder der Europäischen Union | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Top-Ziele | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status erforderlich für | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status auswählen lassen, wenn es für Land optional ist | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Zeitzone | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Gebietsschema | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Gewichtseinheit | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Erster Wochentag | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Wochentage | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Zugriffsbeschränkung | `general/restriction/is_active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |
| Beschränkungsmodus | `general/restriction/mode` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |
| Startseite | `general/restriction/http_redirect` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |
| Landingpage | `general/restriction/cms_page` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |
| HTTP-Antwort | `general/restriction/http_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |
| Speichername | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Telefonnummer speichern | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Betriebsstunden im Speicher | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Land | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Region/Bundesland | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Postleitzahl | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Ort | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Straße | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Straße, Adresszeile 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| MwSt.-Nummer | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Einzelspeichermodus aktivieren | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style="table-layout:auto"}

### Webpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Web**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Hinzufügen von Store-Code zu URLs | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Umleitung zur Basis-URL | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Webserver-Neuschreibungen verwenden | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden sicherer URLs auf der Storefront | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden sicherer URLs im Admin | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren von HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unsichere Anforderungen aktualisieren | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Offloader-Kopfzeile | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS-Homepage | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS Keine Route-Seite | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seite &quot;Keine Cookies&quot;in CMS | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breadcrumbs für CMS-Seiten anzeigen | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie-Lebensdauer | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nur HTTP verwenden | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie-Einschränkungsmodus | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validieren Sie REMOTE_ADDR. | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validieren von HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validieren von HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validieren von HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SID auf Storefront verwenden | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umleiten zu CMS-Seite , wenn Cookies deaktiviert sind | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hinweis anzeigen, wenn JavaScript deaktiviert ist | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hinweis anzeigen, wenn der lokale Speicher deaktiviert ist | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Währungs-Einrichtungspfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Währungseinrichtung**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Basiswährung | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardanzeigewährung | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Währungen | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webdienst | `TBD` |  |
| Verbindungs-Timeout in Sekunden | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verbindungs-Timeout in Sekunden | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verbindungs-Timeout in Sekunden | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diensleistung | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Empfänger | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Absender | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Vorlage | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Kontaktpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Kontakte**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Kontaktaufnahme aktivieren | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mails an senden | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Sender | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email Template | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Berichtpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Berichte**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Start im Jahr | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktuelle Monatsstarts | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Content-Management-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Content Management**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Aktivieren des WYSIWYG-Editors | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden von statischen URLs für Medieninhalte in WYSIWYG für Katalog | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Hierarchiefunktion | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hierarchiemetadaten aktivieren | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardlayout für Hierarchiemenü | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### New Relic-Berichtspfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **New Relic Reporting**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| New Relic-Integration aktivieren | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic-Anwendungsname | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cron aktivieren | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Erweiterte Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert**.

### Admin-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Admin**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Kennwort-E-Mail-Vorlage vergessen | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender vergessen und zurücksetzen | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlage für Benutzerbenachrichtigungen | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startseite | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden der benutzerdefinierten Admin-URL | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerdefinierten Admin-Pfad verwenden | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kontofreigabe für Administratoren | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortrücksetzschutz | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ablaufzeitraum des Wiederherstellungslinks (Stunden) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl von Anforderungen zum Zurücksetzen von Passwörtern | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Min. Zeit zwischen Kennwortrücksetzanforderungen | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geheimen Schlüssel zu URLs hinzufügen | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bei der Anmeldung wird zwischen Groß- und Kleinschreibung unterschieden | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer der Admin-Sitzung (Sekunden) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anmeldefehler beim Sperren des Kontos | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sperrzeit (Minuten) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortlebensdauer (Tage) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortänderung | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diagramme aktivieren | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA in Admin aktivieren | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schriftart | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigemodus | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der fehlgeschlagenen Anmeldeversuche | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA-Zeitüberschreitung (Minuten) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der Symbole | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In CAPTCHA verwendete Symbole | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groß-/Kleinschreibung | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivierte Aktionen | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Systempfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Lebensdauer erfolgreicher Nachrichten | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nach dem Start laufende Nachrichten erneut versuchen | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer fehlgeschlagener Nachrichten | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer neuer Nachrichten | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle Zeitpläne erstellen | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorläufige Planung für | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehlt, wenn nicht ausgeführt in | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verlaufsbereinigung alle | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Erfolgsverlaufs | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Fehlerverlaufs | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separaten Prozess verwenden | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle Zeitpläne erstellen | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorläufige Planung für | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehlt, wenn nicht ausgeführt in | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verlaufsbereinigung alle | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Erfolgsverlaufs | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Fehlerverlaufs | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle Zeitpläne erstellen | `system/cron/staging/schedule_generate_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Vorläufige Planung für | `system/cron/staging/schedule_ahead_for` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Fehlt, wenn nicht ausgeführt in | `system/cron/staging/schedule_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verlaufsbereinigung alle | `system/cron/staging/history_cleanup_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Erfolgsverlaufs | `system/cron/staging/history_success_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Fehlerverlaufs | `system/cron/staging/history_failure_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Separaten Prozess verwenden | `system/cron/staging/use_separate_process` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Alle Zeitpläne erstellen | `system/cron/catalog/event/schedule_generate_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Vorläufige Planung für | `system/cron/catalog/event/schedule_ahead_for` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Fehlt, wenn nicht ausgeführt in | `system/cron/catalog/event/schedule_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verlaufsbereinigung alle | `system/cron/catalog/event/history_cleanup_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Erfolgsverlaufs | `system/cron/catalog/event/history_success_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Fehlerverlaufs | `system/cron/catalog/event/history_failure_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Separaten Prozess verwenden | `system/cron/catalog/event/use_separate_process` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Separaten Prozess verwenden | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kommunikation deaktivieren | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Festlegen des Rückkehrpfads | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path-E-Mail | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Installierte Währungen | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPS zum Abrufen des Feeds verwenden | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktualisierungshäufigkeit | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Letzte Aktualisierung | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplantes Backup aktivieren | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sicherungstyp | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wartungsmodus | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Log Entry Lifetime, Days | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Protokollarchivierungshäufigkeit | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Caching-Anwendung | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL für öffentliche Inhalte | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Übergangsphase | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exportkonfiguration | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Im Protokoll gespeicherte Tage | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Medienspeicher | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mediendatenbank auswählen | `system/media_storage_configuration/media_database` (nicht mehr unterstützt in Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktualisierungszeit der Umgebung | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Speichern von Dateien, Tage | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren der Bereinigung des geplanten Dateiverlaufs | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Vorlage | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Entwicklerpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler**.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Workflow-Typ | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symlinks zulassen | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML minimieren | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlagenpfadhinweise für Storefront aktivieren | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlagenpfadhinweise für Admin aktivieren | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Blocknamen zu Hinten hinzufügen | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Log to File | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Protokoll zu syslog | `dev/syslog/syslog_logging` |  |
| Aktiviert für Storefront | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Für Admin aktiviert | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zusammenführen von JavaScript-Dateien | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript-Bundling aktivieren | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimieren von JavaScript-Dateien | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Übersetzungsstrategie | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JS-Fehler im Sitzungsspeicher protokollieren | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zusammenführen von CSS-Dateien | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimieren von CSS-Dateien | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bildadapter | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Statische Dateien unterschreiben | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Asynchrone Indizierung | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerdefinierte Attribute zwischenspeichern | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
