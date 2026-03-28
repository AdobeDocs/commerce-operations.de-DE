---
title: Sensible und systemspezifische Pfade
description: Erfahren Sie mehr über vertrauliche und systemspezifische Konfigurationspfade für Adobe Commerce. Erkunden Sie die sichere Konfiguration und Verwaltung von Umgebungsvariablen.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# Sensible und systemspezifische Einstellungen

In diesem Thema werden Konfigurationspfade für systemspezifische und vertrauliche Einstellungen aufgelistet:

- Mit dem [`magento app:config:dump` Befehl &#x200B;](../cli/export-configuration.md) systemspezifische Einstellungen in die systemspezifische Konfigurationsdatei `app/etc/env.php` geschrieben, die sich _in_ Versionsverwaltung befinden sollte. Außerdem wird die freigegebene Konfiguration für alle Commerce-Instanzen in `app/etc/config.php` geschrieben. Diese Datei _sollte_ in der Quell-Code-Verwaltung sein.
- Der Befehl [`magento config:sensitive:set`](../cli/set-configuration-values.md) schreibt vertrauliche Einstellungen in `app/etc/env.php`.

  Sie können vertrauliche Werte auch mithilfe von Konfigurationsvariablen festlegen, wie unter [Verwenden von Umgebungsvariablen zum Überschreiben der Konfigurationseinstellungen](../reference/override-config-settings.md#environment-variables) beschrieben.

Eine Liste der anderen Konfigurationspfade finden Sie unter:

- [Alle Konfigurationspfade außer Zahlungen](../reference/config-reference-general.md)
- [Zahlungskonfigurationspfade](../reference/config-reference-payment.md).

>[!INFO]
>
>Alle in diesem Thema aufgeführten Konfigurationspfade sind vertraulich. Die Spalte `System-specific?` zeigt an, welche Werte ebenfalls systemspezifisch sind.

## Allgemeine kategorieabhängige und systemspezifische Pfade

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Configuration** > **General** verfügbar sind.

### Web-Pfade Sensitive und systemspezifische Pfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Web** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Basis-URL | `web/unsecure/base_url` |  | | systemspezifisch | |
| Basis-Link-URL | `web/unsecure/base_link_url` |  | | systemspezifisch | |
| Basis-URL für statische Ansichtsdateien | `web/unsecure/base_static_url` |  | | systemspezifisch | |
| Basis-URL für Benutzer-Mediendateien | `web/unsecure/base_media_url` |  | | systemspezifisch | |
| Secure Base URL | `web/secure/base_url` |  | | systemspezifisch | |
| URL für sicheren Basislink | `web/secure/base_link_url` |  | | systemspezifisch | |
| Sichere Basis-URL für statische Ansichtsdateien | `web/secure/base_static_url` |  | | systemspezifisch | |
| Sichere Basis-URL für Benutzer-Mediendateien | `web/secure/base_media_url` |  | | systemspezifisch | |
| Standard-Web-URL | `web/default/front` |  | | systemspezifisch | |
| Standard-URL ohne Route | `web/default/no_route` |  | | systemspezifisch | |
| Cookie-Pfad | `web/cookie/cookie_path` |  | | systemspezifisch | |
| Cookie-Domäne | `web/cookie/cookie_domain` |  | | systemspezifisch | |
| Cookie-Lebensdauer | `web/cookie/cookie_lifetime` |  | | systemspezifisch | |
| Nur HTTP verwenden | `web/cookie/cookie_httponly` |  | | systemspezifisch | |
| Cookie-Beschränkungsmodus | `web/cookie/cookie_restriction` |  | | systemspezifisch | |

{style="table-layout:auto"}

### Sensible und systemspezifische Pfade bei der Währungseinrichtung

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Währungseinstellungen** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
| --- | --- | --- | --- | --- | --- |
| Fehler-E-Mail-Empfänger | `currency/import/error_email` |  | | | Sensibel |

{style="table-layout:auto"}

### Speichern von E-Mail-Adressen unter sensiblen und systemspezifischen Pfaden

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **E-Mail-** > **Allgemein** > **E-Mail-Adressen speichern** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Name des Absenders | `trans_email/ident_general/name` | | | | Sensibel |
| Absender-E-Mail | `trans_email/ident_general/email` |  | | | Sensibel |
| Name des Absenders | `trans_email/ident_sales/name` |  | | | Sensibel |
| Absender-E-Mail | `trans_email/ident_sales/email` |  | | | Sensibel |
| Name des Absenders | `trans_email/ident_support/name` |  | | | Sensibel |
| Absender-E-Mail | `trans_email/ident_support/email` |  | | | Sensibel |
| Name des Absenders | `trans_email/ident_custom1/name` |  | | | Sensibel |
| Absender-E-Mail | `trans_email/ident_custom1/email` |  | | | Sensibel |
| Name des Absenders | `trans_email/ident_custom2/name` |  | | | Sensibel |
| Absender-E-Mail | `trans_email/ident_custom2/email` |  | | | Sensibel |

{style="table-layout:auto"}

### Kontaktpfade und systemspezifische Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Kontakte** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-Mails senden an | `contact/email/recipient_email` |  | | | Sensibel |
| E-Mail-Absender | `contact/email/sender_email_identity` |  | | | Sensibel |
| E-Mail-Vorlage | `contact/email/email_template` |  | | | Sensibel |

{style="table-layout:auto"}

### Berichterstellung für sensible und systemspezifische Pfade in New Relic

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **New Relic-Berichte**.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic-Konto-ID | `newrelicreporting/general/account_id` |  | | | Sensibel |
| New Relic-Anwendungs-ID | `newrelicreporting/general/app_id` |  | | | Sensibel |
| New Relic-API-Schlüssel | `newrelicreporting/general/api` |  | verschlüsselt | | Sensibel |
| Insights-API-Schlüssel | `newrelicreporting/general/insights_insert_key` |  | verschlüsselt | | Sensibel |
| New Relic-API-URL | `newrelicreporting/general/api_url` |  | | systemspezifisch | Sensibel |
| Insights-API-URL | `newrelicreporting/general/insights_api_url` |  | | systemspezifisch | Sensibel |

{style="table-layout:auto"}

## Kategoriesensitive und systemspezifische Pfade von Kunden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** verfügbar sind.

### Sensible und systemspezifische Pfade für die Kundenkonfiguration

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Kundenkonfiguration** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Standard-E-Mail-Domain | `customer/create_account/email_domain` |  | | systemspezifisch | |

{style="table-layout:auto"}

## Katalogkategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Katalog** verfügbar sind.

### Katalogsensible und systemspezifische Pfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Katalog** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `catalog/productalert_cron/error_email` |  | | | Sensibel |
| YouTube-API-Schlüssel | `catalog/product_video/youtube_api_key` |  | | | Sensibel |
| Solr-Server-Hostname | `catalog/search/solr_server_hostname` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Solr-Server-Port | `catalog/search/solr_server_port` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Solr-Server-Benutzername | `catalog/search/solr_server_username` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Solr-Serverkennwort | `catalog/search/solr_server_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Solr-Serverpfad | `catalog/search/solr_server_path` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Hostname des Elasticsearch-Servers | `catalog/search/elasticsearch_server_hostname` |  | | systemspezifisch | Sensibel |
| Elasticsearch-Server-Port | `catalog/search/elasticsearch_server_port` |  | | systemspezifisch | Sensibel |
| Elasticsearch-Indexpräfix | `catalog/search/elasticsearch_index_prefix` |  | | systemspezifisch | Sensibel |
| Elasticsearch HTTP-Authentifizierung aktivieren | `catalog/search/elasticsearch_enable_auth` |  | | systemspezifisch | |
| Elasticsearch HTTP-Benutzername | `catalog/search/elasticsearch_username` |  | | systemspezifisch | |
| Elasticsearch HTTP-Kennwort | `catalog/search/elasticsearch_password` |  | | systemspezifisch | |
| Elasticsearch-Server-Zeitüberschreitung | `catalog/search/elasticsearch_server_timeout` |  | | systemspezifisch | |
| Elasticsearch HTTP-Benutzername | `catalog/search/elasticsearch_username` | | | systemspezifisch | |
| Elasticsearch HTTP-Kennwort | `catalog/search/elasticsearch_password` | | | systemspezifisch | |
| Elasticsearch-Server-Zeitüberschreitung | `catalog/search/elasticsearch_server_timeout` | | | systemspezifisch | |
| Hostname des OpenSearch-Servers | `catalog/search/opensearch_server_hostname` | | | systemspezifisch | Sensibel |
| OpenSearch-Server-Port | `catalog/search/opensearch_server_port` | | | systemspezifisch | Sensibel |
| OpenSearch-Indexpräfix | `catalog/search/opensearch_index_prefix` | | | systemspezifisch | Sensibel |
| OpenSearch-HTTP-Authentifizierung aktivieren | `catalog/search/opensearch_enable_auth` | | | systemspezifisch | |
| HTTP-Benutzername suchen | `catalog/search/opensearch_username` | | | systemspezifisch | |
| OpenSearch-HTTP-Kennwort | `catalog/search/opensearch_password` | | | systemspezifisch | |
| OpenSearch-Server-Zeitüberschreitung | `catalog/search/opensearch_server_timeout` | | | systemspezifisch | |

{style="table-layout:auto"}

>[!NOTE]
>
>Die OpenSearch-Einstellungen wurden in Adobe Commerce 2.4.6 eingeführt.

### Inventar- und systemspezifische Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Inventar** verfügbar.

| Name | Konfigurationspfad | Unterstützung der Commerce-Version | Verschlüsselt? | Systemspezifisch? | Sensibel? | |
|--------------|--------------|--------------|--------------|--------------|--------------| |
| Google-API-Schlüssel | `cataloginventory/source_selection_distance_based_google/api_key` | | Verschlüsselte | | Sensitive |

### Sensible und systemspezifische Pfade für XML-Sitemaps

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **XML-Sitemap** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `sitemap/generate/error_email` |  | | | Sensibel |

{style="table-layout:auto"}

## Umsatzkategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Configuration** > **Sales** verfügbar sind.

### Sensible und systemspezifische Pfade für Versandeinstellungen

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Versandeinstellungen** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Land | `shipping/origin/country_id` |  | | | Sensibel |
| Region/Staat | `shipping/origin/region_id` |  | | | Sensibel |
| Postleitzahl | `shipping/origin/postcode` |  | | | Sensibel |
| Stadt | `shipping/origin/city` |  | | | Sensibel |
| Adresse Straße | `shipping/origin/street_line1` |  | | | Sensibel |
| Straße, Zeile 2 | `shipping/origin/street_line2` |  | | | Sensibel |
| Live-Konto | `carriers/ups/is_account_live` |  | | systemspezifisch | |

{style="table-layout:auto"}

### Sensible und systemspezifische Pfade für Verkaufs-E-Mails

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mails** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Bestellungs-E-Mail senden an | `sales_email/order/copy_to` |  | | | Sensibel |
| Kommentar-E-Mail an senden | `sales_email/order_comment/copy_to` |  | | | Sensibel |
| Rechnungs-E-Mail senden an | `sales_email/invoice/copy_to` |  | | | Sensibel |
| Rechnungskommentar per E-Mail senden an | `sales_email/invoice_comment/copy_to` |  | | | Sensibel |
| Versandnachricht senden an | `sales_email/shipment/copy_to` |  | | | Sensibel |
| Versandkommentar per E-Mail senden an | `sales_email/shipment_comment/copy_to` |  | | | Sensibel |
| E-Mail mit Gutschrift senden an | `sales_email/creditmemo/copy_to` |  | | | Sensibel |
| Gutschriftskommentar per E-Mail senden an | `sales_email/creditmemo_comment/copy_to` |  | | | Sensibel |
| Abholbereite E-Mail senden an | `sales_email/temando_pickup/copy_to` |  | | | Sensibel |

{style="table-layout:auto"}

### Checkout sensibler und systemspezifischer Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Checkout** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehlgeschlagene Zahlung per E-Mail senden an | `checkout/payment_failed/copy_to` |  | | | Sensibel |

{style="table-layout:auto"}

### Sensible und systemspezifische Pfade der Google-API

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Google API verfügbar**.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Container-ID | `google/analytics/container_id` | Nur Commerce Enterprise | | | Sensibel |

{style="table-layout:auto"}

### Sensible und systemspezifische Pfade von Versandmethoden

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Liefermethoden** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Gateway-URL | `carriers/usps/gateway_url` |  | | | Sensibel |
| Sichere Gateway-URL | `carriers/usps/gateway_secure_url` |  | | | Sensibel |
| Titel | `carriers/usps/title` |  | | | |
| Benutzer-ID | `carriers/usps/userid` |  | verschlüsselt | | Sensibel |
| Kennwort | `carriers/usps/password` |  | verschlüsselt | | Sensibel |
| Benutzer-ID | `carriers/ups/username` |  | verschlüsselt | | Sensibel |
| Kennwort | `carriers/ups/password` |  | verschlüsselt | | Sensibel |
| Lizenznummer aufrufen | `carriers/ups/access_license_number` |  | verschlüsselt | | Sensibel |
| Tracking-XML-URL | `carriers/ups/tracking_xml_url` |  | | | Sensibel |
| Gateway XML URL | `carriers/ups/gateway_xml_url` |  | | | Sensibel |
| Liefernummer | `carriers/ups/shipper_number` |  | | | Sensibel |
| DEBUG | `carriers/ups/debug` |  | | | Sensibel |
| Konto-ID | `carriers/fedex/account` |  | verschlüsselt | | Sensibel |
| Schlüssel | `carriers/fedex/key` |  | verschlüsselt | | Sensibel |
| Zählernummer | `carriers/fedex/meter_number` |  | verschlüsselt | | Sensibel |
| Kennwort | `carriers/fedex/password` |  | verschlüsselt | | Sensibel |
| Zugriffs-ID | `carriers/dhl/id` |  | verschlüsselt | | Sensibel |
| Kennwort | `carriers/dhl/password` |  | verschlüsselt | | Sensibel |
| DEBUG | `carriers/dhl/debug` |  | | | |
| Kontonummer | `carriers/dhl/account` |  | | | Sensibel |
| Gateway-URL | `carriers/dhl/gateway_url` |  | | | Sensibel |
| Sandbox-Modus | `carriers/fedex/sandbox_mode` |  | | | Sensibel |

{style="table-layout:auto"}

### Vertriebssensitive und systemspezifische Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkauf** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Kontaktname | `sales/magento_rma/store_name` | Nur Commerce Enterprise | | | Sensibel |
| Adresse Straße | `sales/magento_rma/address` | Nur Commerce Enterprise | | | Sensibel |
| Adresse Straße | `sales/magento_rma/address1` |  | | | Sensibel |
| Stadt | `sales/magento_rma/city` | Nur Commerce Enterprise | | | Sensibel |
| Bundesland/Region | `sales/magento_rma/region_id` | Nur Commerce Enterprise | | | Sensibel |
| Postleitzahl | `sales/magento_rma/zip` | Nur Commerce Enterprise | | | Sensibel |
| Land | `sales/magento_rma/country_id` | Nur Commerce Enterprise | | | Sensibel |
| RMA-E-Mail-Kopie senden an | `sales_email/magento_rma/copy_to` | Nur Commerce Enterprise | | | Sensibel |
| RMA-Autorisierungs-E-Mail senden an | `sales_email/magento_rma_auth/copy_to` | Nur Commerce Enterprise | | | Sensibel |
| RMA-Kommentar-E-Mail senden an | `sales_email/magento_rma_comment/copy_to` | Nur Commerce Enterprise | | | Sensibel |
| RMA-Kommentar-E-Mail senden an | `sales_email/magento_rma_customer_comment/copy_to` | Nur Commerce Enterprise | | | Sensibel |

{style="table-layout:auto"}

### Google-API-Pfade

Diese Konfigurationswerte sind in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Google API verfügbar**.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Kontonummer | `google/analytics/account` |  | | | Sensibel |

{style="table-layout:auto"}

## Kategorie „Erweitert“

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** verfügbar sind.

### Sensible und systemspezifische Pfade für Administratoren

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Admin** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Benutzerdefinierte Admin-URL | `admin/url/custom` |  | | | Sensibel |
| Benutzerdefinierter Administratorpfad | `admin/url/custom_path` |  | | | Sensibel |

{style="table-layout:auto"}

### Systemabhängige und systemspezifische Pfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `system/magento_scheduled_import_export_log/error_email` |  | | | Sensibel |
| Auf Liste zugreifen | `system/full_page_cache/varnish/access_list` |  |  | | Sensibel |
| Fehler beim Absender der E-Mail | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | Sensibel |

{style="table-layout:auto"}

### Sensible und systemspezifische Pfade für Entwickler

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Zulässige IPs (durch Kommata getrennt) | `dev/restrict/allow_ips` |  | | systemspezifisch | Sensibel |

{style="table-layout:auto"}

## Kategorie „Erweitert“

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** verfügbar sind.

### Systempfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` |  | | systemspezifisch | Sensibel |
| Port (25) | `system/smtp/port` |  | | systemspezifisch | Sensibel |
| Backend-Host | `system/full_page_cache/varnish/backend_host` |  | | systemspezifisch | Sensibel |
| Backend-Port | `system/full_page_cache/varnish/backend_port` |  | | systemspezifisch | Sensibel |

{style="table-layout:auto"}

### Entwicklerpfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler** verfügbar.

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| JS-Fehler in Sitzungsspeicherschlüssel protokollieren | `dev/js/session_storage_key` | ![Nicht nur Commerce](/help/assets/configuration/red-x.png) | | systemspezifisch | |

{style="table-layout:auto"}

## Zahlungssensible und systemspezifische Pfade

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Zahlung** verfügbar sind.

### Allgemeine Variable

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Handelsland | `paypal/general/merchant_country` |  | Sensibel |

{style="table-layout:auto"}

>[!INFO]
>
>Ihre Auswahl für diese Variable bestimmt, welche [internationalen Pfade](#international-paths) Sie verwenden können.

### PayPal-sensible und systemspezifische Pfade

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-Mail, die mit dem PayPal-Händlerkonto verknüpft ist (optional) | `paypal/general/business_account` |  | | | Sensibel |
| Händlerkonto-ID | `payment/paypal_express/merchant_id` |  | | | Sensibel |
| Veröffentlicher-ID | `payment/paypal_express_bml/publisher_id` |  | | | Sensibel |
| Kennwort | `paypal/fetch_reports/ftp_password` |  | verschlüsselt | | Sensibel |
| Login | `paypal/fetch_reports/ftp_login` |  | verschlüsselt | | Sensibel |
| Benutzerdefinierter Endpunkt-Hostname oder IP-Adresse | `paypal/fetch_reports/ftp_ip` |  | | systemspezifisch | Sensibel |
| Sandbox-Modus | `paypal/fetch_reports/ftp_sandbox` |  | | systemspezifisch | |
| Debug-Modus | `payment/paypal_express/debug` |  | | systemspezifisch | |
| Debug-Modus | `payment/paypal_billing_agreement/debug` |  | | systemspezifisch | |
| SFTP-Anmeldedaten | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |

{style="table-layout:auto"}

### PayPal Payflow Pro - sensible und systemspezifische Pfade

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Benutzer | `payment/payflow_advanced/user` |  | verschlüsselt | | Sensibel |
| Kennwort | `payment/payflow_advanced/pwd` |  | verschlüsselt | | Sensibel |
| Benutzerdefinierter Pfad | `paypal/fetch_reports/ftp_path` |  | | systemspezifisch | Sensibel |
| Benutzer | `payment/payflowpro/user` |  | verschlüsselt | | Sensibel |
| Kennwort | `payment/payflowpro/pwd` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment/payflowpro/sandbox_flag` |  | | systemspezifisch | |
| Teilhaber | `payment/payflowpro/partner` |  | | | Sensibel |
| Proxy-Host | `payment/payflowpro/proxy_host` |  | | systemspezifisch | Sensibel |
| Proxy-Port | `payment/payflowpro/proxy_port` |  | | systemspezifisch | Sensibel |
| Debug-Modus | `payment/payflowpro/debug` |  | | systemspezifisch | |
| SFTP-Anmeldedaten | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | systemspezifisch | |
| Kreditkarteneinstellungen | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | Sensibel |

{style="table-layout:auto"}

### PayPal Payflow Link-sensible und systemspezifische Pfade

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Benutzer | `payment/payflow_link/user` |  | verschlüsselt | | Sensibel |
| Kennwort | `payment/payflow_link/pwd` |  | verschlüsselt | | Sensibel |
| Testmodus | `payment/payflow_link/sandbox_flag` |  | | systemspezifisch | |
| Proxy verwenden | `payment/payflow_link/use_proxy` |  | | systemspezifisch | |
| Proxy-Host | `payment/payflow_link/proxy_host` |  | | systemspezifisch | |
| Proxy-Port | `payment/payflow_link/proxy_port` |  |  | systemspezifisch | |
| Debug-Modus | `payment/payflow_link/debug` |  | | systemspezifisch | |
| URL-Methode für Abbruch-URL und Rückgabe-URL | `payment/payflow_link/url_method` |  | | systemspezifisch | |
| Debug-Modus | `payment/payflow_express/debug` |  | | systemspezifisch | |
| SFTP-Anmeldedaten | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensibel |

{style="table-layout:auto"}

### PayPal Payments Pro sensible und systemspezifische Pfade

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API-Benutzername | `paypal/wpp/api_username` |  | verschlüsselt | | Sensibel |
| API-Kennwort | `paypal/wpp/api_password` |  | verschlüsselt | | Sensibel |
| API-Signatur | `paypal/wpp/api_signature` |  | verschlüsselt | | Sensibel |
| API-Zertifikat | `paypal/wpp/api_cert` |  | | | Sensibel |
| Proxy-Host | `paypal/wpp/proxy_host` |  | | systemspezifisch | Sensibel |
| Proxy-Port | `paypal/wpp/proxy_port` |  | | systemspezifisch | Sensibel |
| Sandbox-Modus | `paypal/wpp/sandbox_flag` |  | | systemspezifisch | |
| SFTP-Anmeldedaten | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |

{style="table-layout:auto"}

### PayPal Payments Pro Gehostete sensible und systemspezifische Pfade

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Debug-Modus | `payment/hosted_pro/debug` |  | | systemspezifisch | |
| SFTP-Anmeldedaten | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |

{style="table-layout:auto"}

### Sensible und systemspezifische Pfade für Braintree

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Händler-ID | `payment/braintree/merchant_id` |  | | | Sensibel |
| Öffentlicher Schlüssel | `payment/braintree/public_key` |  | verschlüsselt | | Sensibel |
| Privater Schlüssel | `payment/braintree/private_key` |  | verschlüsselt | | Sensibel |
| Händlerkonto-ID | `payment/braintree/merchant_account_id` |  | | | Sensibel |
| Händler-ID bereitstellen | `payment/braintree/kount_id` |  | | | Sensibel |
| Merchant-Namen überschreiben | `payment/braintree_paypal/merchant_name_override` |  | | | Sensibel |
| Telefon | `payment/braintree/descriptor_phone` |  | | | Sensibel |
| URL | `payment/braintree/descriptor_url` |  | | systemspezifisch | |

{style="table-layout:auto"}

### Scheck-/Zahlungspfade

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Check senden an | `payment/checkmo/mailing_address` |  | | | Sensibel |
| Check senden an | `payment_us/checkmo/mailing_address` |  | | | Sensibel |

{style="table-layout:auto"}

### Internationale Wege

| -Name | Konfigurationspfad | Commerce-Versionsunterstützung | Verschlüsselt? | Systemspezifisch? | Sensibel? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Transaktionsschlüssel | `payment_au/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_au/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_au/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_au/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_au/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_au/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_au/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_au/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_au/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_au/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Sandbox-Modus | `payment_au/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_au/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_au/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_au/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_au/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_au/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_au/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_es/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_es/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_es/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_es/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_es/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_es/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_es/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_es/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_es/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_es/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_es/worldpay/md5_secret` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| DEBUG | `payment_es/worldpay/debug` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_es/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_es/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_es/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_es/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_es/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_es/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_es/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_nz/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_nz/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_nz/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Testmodus | `payment_nz/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Testmodus | `payment_nz/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_nz/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_nz/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_nz/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_nz/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_nz/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Sandbox-API-Kennwort | `payment_nz/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_nz/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment/payflow_advanced/sandbox_flag` |  | | systemspezifisch | |
| Proxy-Host | `payment/payflow_advanced/proxy_host` |  | | systemspezifisch | Sensibel |
| Proxy-Port | `payment/payflow_advanced/proxy_port` |  | | systemspezifisch | |
| Debug-Modus | `payment/payflow_advanced/debug` |  | | systemspezifisch | |
| URL-Methode für Abbruch-URL und Rückgabe-URL | `payment/payflow_advanced/url_method` |  | | systemspezifisch | |
| Testmodus | `payment_us/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_us/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_us/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_us/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_us/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_us/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Testmodus | `payment_us/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_us/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_us/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_us/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_us/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_us/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_us/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_us/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | |
| Testmodus | `payment_gb/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Testmodus | `payment_gb/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_gb/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Testmodus | `payment_gb/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_gb/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_gb/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_gb/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_gb/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_gb/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_gb/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_gb/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_de/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_de/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_de/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_de/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Transaktionsschlüssel | `payment_de/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_de/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_de/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_de/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Passwort für Zahlungsantwort | `payment_de/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_de/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| DEBUG | `payment_de/worldpay/debug` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_de/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_de/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_de/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_de/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_de/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_de/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_de/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_other/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_other/authorizenet_directpost/test` |  | | systemspezifisch | Sensibel |
| Gateway-URL | `payment_other/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_other/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | |
| Transaktionsschlüssel | `payment_other/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_other/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_other/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Neuer Bestellstatus | `payment_other/cybersource/order_status` | Nur Commerce Enterprise | | systemspezifisch | |
| Testmodus | `payment_other/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_other/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_other/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Testmodus | `payment_other/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_other/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_other/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_other/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_other/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_other/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_other/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_other/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_ca/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_ca/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_ca/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_ca/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_ca/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_ca/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Neuer Bestellstatus | `payment_ca/cybersource/order_status` | Nur Commerce Enterprise | | | |
| Testmodus | `payment_ca/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_ca/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | |
| Remote-Admin-Autorisierungskennwort | `payment_ca/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Testmodus | `payment_ca/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_ca/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_ca/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_ca/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_ca/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_ca/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Sandbox-API-Kennwort | `payment_ca/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_ca/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_hk/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_hk/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_hk/authorizenet_directpost/cgi_url` |  | | | Sensibel |
| Transaktionsdetails-URL | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_hk/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_hk/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_hk/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_hk/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Passwort für Zahlungsantwort | `payment_hk/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_hk/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Testmodus | `payment_hk/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Live API-Schlüssel | `payment_hk/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Live API-Kennwort | `payment_hk/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_hk/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_hk/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_hk/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_hk/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_jp/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_jp/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_jp/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_jp/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_jp/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_jp/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Neuer Bestellstatus | `payment_jp/cybersource/order_status` | Nur Commerce Enterprise | | systemspezifisch | |
| Testmodus | `payment_jp/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_jp/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_jp/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Testmodus | `payment_jp/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_jp/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_jp/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_jp/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_jp/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_jp/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_jp/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_jp/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_fr/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_fr/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_fr/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_fr/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_fr/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_fr/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_fr/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_fr/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_fr/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Testmodus | `payment_fr/worldpay/sandbox_flag` | Nur Commerce Enterprise |  | systemspezifisch | |
| Sandbox-Modus | `payment_fr/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_fr/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_fr/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_fr/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_fr/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_fr/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_fr/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_it/authorizenet_directpost/trans_key` |  | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_it/authorizenet_directpost/test` |  | | systemspezifisch | |
| Gateway-URL | `payment_it/authorizenet_directpost/cgi_url` |  | | systemspezifisch | Sensibel |
| Transaktionsdetails-URL | `payment_it/authorizenet_directpost/cgi_url_td` |  | | systemspezifisch | Sensibel |
| Transaktionsschlüssel | `payment_it/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Zugriffsschlüssel | `payment_it/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Geheimer Schlüssel | `payment_it/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Testmodus | `payment_it/cybersource/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Passwort für Zahlungsantwort | `payment_it/worldpay/response_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_it/worldpay/auth_password` | Nur Commerce Enterprise | | systemspezifisch | Sensibel |
| Testmodus | `payment_it/worldpay/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Sandbox-Modus | `payment_it/eway/sandbox_flag` | Nur Commerce Enterprise | | systemspezifisch | |
| Live API-Schlüssel | `payment_it/eway/live_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Live API-Kennwort | `payment_it/eway/live_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Live-Verschlüsselungsschlüssel | `payment_it/eway/live_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Schlüssel | `payment_it/eway/sandbox_api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Sandbox-API-Kennwort | `payment_it/eway/sandbox_api_password` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| Client-seitiger Sandbox-Verschlüsselungsschlüssel | `payment_it/eway/sandbox_encryption_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| API-Schlüssel | `fraud_protection/signifyd/api_key` | Nur Commerce Enterprise | verschlüsselt | systemspezifisch | Sensibel |
| API-URL | `fraud_protection/signifyd/api_url` | Nur Commerce Enterprise |  | systemspezifisch | Sensibel |
| SFTP-Anmeldedaten | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibel |
| API-Anmelde-ID | `payment_au/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_au/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_au/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_au/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_au/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Check senden an | `payment_es/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_es/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_es/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_es/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_es/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_es/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Remote-Admin-Installations-ID | `payment_es/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | | | | | |
| SFTP-Anmeldedaten | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibel |
| API-Anmelde-ID | `payment_nz/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_nz/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_nz/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_nz/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Transaktionsschlüssel | `payment_nz/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_nz/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Zugriffsschlüssel | `payment_nz/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Geheimer Schlüssel | `payment_nz/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_nz/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Passwort für Zahlungsantwort | `payment_nz/worldpay/response_password` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_nz/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_nz/worldpay/auth_password` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_nz/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensibel |
| API-Anmelde-ID | `payment_us/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Transaktionsschlüssel | `payment_us/authorizenet_directpost/trans_key` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_us/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_us/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_us/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Transaktionsschlüssel | `payment_us/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_us/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_us/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Passwort für Zahlungsantwort | `payment_us/worldpay/response_password` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_us/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_us/worldpay/auth_password` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_us/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensibel |
| SFTP-Anmeldedaten | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Check senden an | `payment_gb/checkmo/mailing_address` |  | | | Sensibel |
| Händler-ID | `payment_gb/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Transaktionsschlüssel | `payment_gb/cybersource/transaction_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_gb/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Zugriffsschlüssel | `payment_gb/cybersource/access_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Geheimer Schlüssel | `payment_gb/cybersource/secret_key` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| API-Anmelde-ID | `payment_gb/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Transaktionsschlüssel | `payment_gb/authorizenet_directpost/trans_key` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_gb/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | Sensibel |
| Installations-ID | `payment_gb/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Passwort für Zahlungsantwort | `payment_gb/worldpay/response_password` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_gb/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Autorisierungskennwort | `payment_gb/worldpay/auth_password` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_de/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_de/checkmo/mailing_address` |  | | | Sensibel |
| Händler-ID | `payment_de/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_de/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| API-Anmelde-ID | `payment_de/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_de/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_de/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Installations-ID | `payment_de/worldpay/installation_id` | Nur Commerce Enterprise | | | |
| Remote-Admin-Installations-ID | `payment_de/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_de/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensibel |
| SFTP-Anmeldedaten | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_other/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_other/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_other/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| Neuer Bestellstatus | `payment_other/authorizenet_directpost/order_status` |  | | | Sensibel |
| E-Mail des Händlers | `payment_other/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_other/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_other/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_other/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_other/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_other/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_ca/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_ca/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_ca/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| Neuer Bestellstatus | `payment_ca/authorizenet_directpost/order_status` |  | | | Sensibel |
| E-Mail-Kunde | `payment_ca/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_ca/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_ca/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_ca/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_ca/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_ca/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_ca/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | Sensibel |
| SFTP-Anmeldedaten | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_hk/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_hk/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_hk/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_hk/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_hk/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_hk/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_hk/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_hk/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_hk/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_hk/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| Signaturfelder | `payment_hk/worldpay/signature_fields` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_jp/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_jp/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_jp/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_jp/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_jp/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_jp/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_jp/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_jp/worldpay/installation_id` | Nur Commerce Enterprise | | | |
| Remote-Admin-Installations-ID | `payment_jp/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_jp/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| Signaturfelder | `payment_jp/worldpay/signature_fields` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_fr/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_fr/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_fr/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_fr/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_fr/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_fr/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_fr/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_fr/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_fr/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_fr/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |
| Signaturfelder | `payment_fr/worldpay/signature_fields` | Nur Commerce Enterprise | | | Sensibel |
| SFTP-Anmeldedaten | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibel |
| SFTP-Anmeldedaten | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibel |
| Scheck zahlbar machen an | `payment_it/checkmo/payable_to` |  | | | Sensibel |
| Check senden an | `payment_it/checkmo/mailing_address` |  | | | Sensibel |
| API-Anmelde-ID | `payment_it/authorizenet_directpost/login` |  | verschlüsselt | | Sensibel |
| Händler MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | verschlüsselt | | Sensibel |
| E-Mail-Kunde | `payment_it/authorizenet_directpost/email_customer` |  | | | Sensibel |
| E-Mail des Händlers | `payment_it/authorizenet_directpost/merchant_email` |  | | | Sensibel |
| Händler-ID | `payment_it/cybersource/merchant_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Profil-ID | `payment_it/cybersource/profile_id` | Nur Commerce Enterprise | verschlüsselt | | Sensibel |
| Installations-ID | `payment_it/worldpay/installation_id` | Nur Commerce Enterprise | | | Sensibel |
| Remote-Admin-Installations-ID | `payment_it/worldpay/admin_installation_id` | Nur Commerce Enterprise | | | Sensibel |
| MD5-Geheimnis für Transaktionen | `payment_it/worldpay/md5_secret` | Nur Commerce Enterprise | | | Sensibel |

{style="table-layout:auto"}
