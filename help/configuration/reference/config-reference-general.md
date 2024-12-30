---
title: Referenz zu allgemeinen Konfigurationspfaden
description: Hier finden Sie eine Liste der allgemeinen und erweiterten Konfigurationswerte.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Referenz zu allgemeinen und erweiterten Konfigurationspfaden

In diesem Thema werden allgemeine und erweiterte Konfigurationspfade sowie _nicht_ [ und systemspezifische Werte](config-reference-sens.md) aufgeführt. Der [`magento app:config:dump` Befehl ](../cli/export-configuration.md) diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Versionsverwaltung befinden sollte.

Informationen dazu, wie Sie Konfigurationseinstellungen optional überschreiben oder vertrauliche Einstellungen festlegen können, finden Sie unter [Verwenden von Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen](override-config-settings.md#environment-variables).

## Allgemeine Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Configuration** > **General** verfügbar sind.

### Allgemeine Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? | Sensibel? |
|--------------|--------------|--------------|--------------|
| Standardland | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| Länder zulassen | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| Postleitzahl ist optional für | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| Länder der Europäischen Union | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![sensitiv](/help/assets/configuration/cloud-sens.png) |
| Top-Ziele | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status ist erforderlich für | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status auswählen, wenn dies für das Land optional ist | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Zeitzone | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Gebietsschema | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Gewichtseinheit | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Erster Wochentag | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Wochenendtage | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Zugriffsbeschränkung | `general/restriction/is_active` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | |
| Beschränkungsmodus | `general/restriction/mode` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | |
| Startseite | `general/restriction/http_redirect` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | |
| Landingpage | `general/restriction/cms_page` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | |
| HTTP-Antwort | `general/restriction/http_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | |
| Name speichern | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Telefonnummer speichern | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Geschäftszeiten speichern | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Land | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Region/Staat | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Postleitzahl | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Stadt | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Adresse Straße | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Straße, Zeile 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Umsatzsteuer-Identifikationsnummer | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Einzelspeichermodus aktivieren | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |

{style="table-layout:auto"}

### Webpfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Web** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Store-Code zu URLs hinzufügen | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische Umleitung zur Basis-URL | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Webserver-Neuschreibungen verwenden | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sichere URLs in der Storefront verwenden | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden sicherer URLs im Admin-Bereich | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren von HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Upgrade unsicherer Anfragen | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ablade-Kopfzeile | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS-Startseite | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS - Keine Routenseite | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS - Keine Cookies | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breadcrumbs für CMS-Seiten anzeigen | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie-Lebensdauer | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nur HTTP verwenden | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie-Beschränkungsmodus | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| REMOTE_ADDR validieren | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validieren von HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validate HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_USER_AGENT validieren | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SID für Storefront verwenden | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zur CMS-Seite umleiten, wenn Cookies deaktiviert sind | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hinweis anzeigen, wenn JavaScript deaktiviert ist | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hinweis anzeigen, wenn lokaler Speicher deaktiviert ist | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Pfade für Währungseinrichtung

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Währungseinstellungen** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Basiswährung | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardanzeigewährung | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zulässige Währungen | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` | |
| Fixer.io | `TBD` | |
| WebServices | `TBD` | |
| Verbindungs-Timeout in Sekunden | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verbindungs-Timeout in Sekunden | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verbindungs-Timeout in Sekunden | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiviert | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Service | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Empfänger | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler beim Absender der E-Mail | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Vorlage | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Pfade der Kontakte

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Kontakte** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Kontakt zu uns aktivieren | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mails senden an | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Vorlage | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Berichtspfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Berichte** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Jahresbeginn bis dato | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktueller Monat beginnt | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Content Management Paths

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Content-Management** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| WYSIWYG-Editor aktivieren | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden von statischen URLs für Medieninhalte in WYSIWYG for Catalog | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hierarchiefunktion aktivieren | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren von Hierarchie-Metadaten | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standard-Layout für das Hierarchie-Menü | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Berichtswege für New Relic

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **New Relic-Berichte**.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| New Relic-Integration aktivieren | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic-Anwendungsname | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cron aktivieren | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Kategorie „Erweitert“

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** verfügbar sind.

### Administratorpfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Admin** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| E-Mail-Vorlage für vergessenes Kennwort | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Absender vergessen und zurückgesetzt | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerbenachrichtigungsvorlage | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startseite | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerdefinierte Admin-URL verwenden | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerdefinierten Administratorpfad verwenden | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Admin-Kontofreigabe | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ des Kennwortrücksetzschutzes | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gültigkeitszeitraum des Wiederherstellungs-Links (Stunden) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl von Anfragen zum Zurücksetzen des Kennworts | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Min. Zeit zwischen Anfragen zum Zurücksetzen des Passworts | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hinzufügen eines geheimen Schlüssels zu URLs | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bei der Anmeldung wird zwischen Groß- und Kleinschreibung unterschieden | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer der Admin-Sitzung (Sekunden) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale Anzahl an Anmeldefehlern beim Sperren des Kontos | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sperrzeit (Minuten) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennwortlebensdauer (Tage) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Passwortänderung | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diagramme aktivieren | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivieren von CAPTCHA in der Admin Console | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schriftart | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzeigemodus | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl erfolgloser Anmeldeversuche | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA-Zeitüberschreitung (Minuten) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anzahl der Symbole | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In CAPTCHA verwendete Symbole | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Von Schreibweise abhängig | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivierte Aktionen | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Systempfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Lebensdauer erfolgreicher Nachrichten | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nachrichten in Bearbeitung wiederholen nach | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer fehlgeschlagener Nachrichten | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer neuer Nachrichten | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeitpläne generieren alle | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planen Sie im Voraus für | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehlgeschlagen, wenn nicht innerhalb von ausgeführt | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verlaufsbereinigung alle | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Erfolgsverlaufs | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Fehlerverlaufs | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separaten Prozess verwenden | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeitpläne generieren alle | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planen Sie im Voraus für | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehlgeschlagen, wenn nicht innerhalb von ausgeführt | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verlaufsbereinigung alle | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Erfolgsverlaufs | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Fehlerverlaufs | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeitpläne generieren alle | `system/cron/staging/schedule_generate_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Planen Sie im Voraus für | `system/cron/staging/schedule_ahead_for` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Fehlgeschlagen, wenn nicht innerhalb von ausgeführt | `system/cron/staging/schedule_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verlaufsbereinigung alle | `system/cron/staging/history_cleanup_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Erfolgsverlaufs | `system/cron/staging/history_success_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Fehlerverlaufs | `system/cron/staging/history_failure_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Separaten Prozess verwenden | `system/cron/staging/use_separate_process` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Zeitpläne generieren alle | `system/cron/catalog/event/schedule_generate_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Planen Sie im Voraus für | `system/cron/catalog/event/schedule_ahead_for` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Fehlgeschlagen, wenn nicht innerhalb von ausgeführt | `system/cron/catalog/event/schedule_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Verlaufsbereinigung alle | `system/cron/catalog/event/history_cleanup_every` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Erfolgsverlaufs | `system/cron/catalog/event/history_success_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Lebensdauer des Fehlerverlaufs | `system/cron/catalog/event/history_failure_lifetime` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Separaten Prozess verwenden | `system/cron/catalog/event/use_separate_process` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Separaten Prozess verwenden | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail-Kommunikation deaktivieren | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rückgabepfad festlegen | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail mit Rückgabepfad | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Installierte Währungen | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verwenden von HTTPS für den Feed | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktualisierungshäufigkeit | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Letzte Aktualisierung | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplante Sicherung aktivieren | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sicherungstyp | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wartungsmodus | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Protokolleintrags, Tage | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit der Protokollarchivierung | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Caching-Anwendung | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL für öffentliche Inhalte | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Karenzzeit | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konfiguration exportieren | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tage im Protokoll gespeichert | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Medienspeicher | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mediendatenbank auswählen | `system/media_storage_configuration/media_database` (in Commerce 2.4.3 nicht mehr unterstützt) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umgebungsaktualisierungszeit | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dateien speichern, Tage | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zeitgesteuerte Bereinigung des Dateiverlaufs aktivieren | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Startzeit | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Häufigkeit | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fehler-E-Mail-Vorlage | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Entwicklerpfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Workflow-Typ | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symlinks zulassen | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML minimieren | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlagenpfadhinweise für Storefront aktivieren | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vorlagenpfadhinweise für Admin aktivieren | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Blocknamen zu Hinweisen hinzufügen | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In Datei protokollieren | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In syslog protokollieren | `dev/syslog/syslog_logging` |  |
| Aktiviert für Storefront | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Für Admin aktiviert | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zusammenführen von JavaScript-Dateien | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript-Bundle aktivieren | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimieren von JavaScript-Dateien | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Übersetzungsstrategie | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JS-Fehler in Sitzungsspeicher protokollieren | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zusammenführen von CSS-Dateien | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimieren von CSS-Dateien | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bildadapter | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Signieren von statischen Dateien | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Asynchrone Indizierung | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzerdefinierte Attribute zwischenspeichern | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
