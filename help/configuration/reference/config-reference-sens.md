---
title: Sensible und systemspezifische Pfade
description: Sehen Sie sich eine Liste systemspezifischer und sensibler Konfigurationswerte an.
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 0%

---


# Sensible und systemspezifische Einstellungen

In diesem Thema werden Konfigurationspfade für systemspezifische und vertrauliche Einstellungen aufgeführt:

- Die [`magento app:config:dump` command](../cli/export-configuration.md) schreibt systemspezifische Einstellungen in die systemspezifische Konfigurationsdatei, `app/etc/env.php`, die _not_ sich in der Quell-Code-Verwaltung befinden. Sie schreibt außerdem die freigegebene Konfiguration für alle Commerce-Instanzen in `app/etc/config.php`, diese Datei _sollte_ sich in der Quell-Code-Verwaltung befinden.
- Die [`magento config:sensitive:set` command](../cli/set-configuration-values.md) schreibt vertrauliche Einstellungen in `app/etc/env.php`.

   Sie können auch mithilfe von Konfigurationsvariablen sensible Werte festlegen, wie hier beschrieben: [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](../reference/override-config-settings.md#environment-variables).

Eine Liste anderer Konfigurationspfade finden Sie unter:

- [Alle Konfigurationspfade außer Zahlungen](../reference/config-reference-general.md)
- [Zahlungskonfigurationspfade](../reference/config-reference-payment.md).

>[!INFO]
>
>Alle in diesem Thema aufgeführten Konfigurationspfade sind vertraulich. Die `System-specific?` gibt an, welche Werte ebenfalls systemspezifisch sind.

## Allgemeine kategoriesensitive und systemspezifische Pfade

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Allgemein**.

### Webpfade - sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Web**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Basis-URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Basis-Link-URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Basis-URL für statische Ansichtsdateien | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Basis-URL für Benutzermediendateien | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sichere Basis-URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sichere Basis-Link-URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sichere Basis-URL für statische Ansichtsdateien | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sichere Basis-URL für Benutzermediendateien | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Standard-Web-URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Standard-URL ohne Route | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Cookie-Pfad | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Cookie-Domäne | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Cookie-Lebensdauer | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Nur HTTP verwenden | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Cookie-Einschränkungsmodus | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Währungseinrichtung - sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Währungseinrichtung**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### E-Mail-Adressen-sensible und systemspezifische Pfade speichern

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **E-Mail-Konfiguration** > **Allgemein** > **E-Mail-Adressen speichern**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Absendername | `trans_email/ident_general/name` |  |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absender-E-Mail | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absendername | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absender-E-Mail | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absendername | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absender-E-Mail | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absendername | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absender-E-Mail | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absendername | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Absender-E-Mail | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Kontaktaufnahme mit sensiblen und systemspezifischen Pfaden

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **Kontakte**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-Mails an senden | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Sender | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Template | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic meldet sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Allgemein** > **New Relic Reporting**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic-Konto-ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| New Relic-Anwendungs-ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| New Relic API-Schlüssel | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Insights-API-Schlüssel | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| New Relic API-URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Insights-API-URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Kunden haben kategoriesensitive und systemspezifische Pfade

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Kunden**.

### Vom Kunden konfigurationsabhängige und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Kunden** > **Kundenkonfiguration**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Standard-E-Mail-Domain | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Katalogkategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Katalog**.

### Vom Katalog abhängige und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Katalog**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| YouTube API-Schlüssel | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Hostname des Solr-Servers | `catalog/search/solr_server_hostname` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Solr Server Port | `catalog/search/solr_server_port` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Solr Server Username | `catalog/search/solr_server_username` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Solr Server Password | `catalog/search/solr_server_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Solr Server Path | `catalog/search/solr_server_path` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Hostname des Elasticsearch-Servers | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch-Server-Port | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch-Indexpräfix | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren der Elasticsearch-HTTP-Autorisierung | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-Benutzername | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Elasticsearch-HTTP-Kennwort | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Elasticsearch Server Timeout | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-Benutzername | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Elasticsearch-HTTP-Kennwort | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Elasticsearch Server Timeout | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Hostname des OpenSearch-Servers | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| OpenSearch-Server-Port | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| OpenSearch-Indexpräfix | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| OpenSearch HTTP Auth aktivieren | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch HTTP-Benutzername | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch HTTP-Kennwort | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch Server-Timeout | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>In Adobe Commerce 2.4.6 wurden OpenSearch-Einstellungen eingeführt.

### Bestandsbezogene und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Bestand**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google-API-Schlüssel | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML-Sitemap-sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **XML-Sitemap**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Verkaufskategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb**.

### Versandeinstellungen - sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Versandeinstellungen**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Land | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Region/Bundesland | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Postleitzahl | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Ort | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Straße | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Straße, Adresszeile 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-Konto | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### E-Mails für Vertrieb - sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Verkaufs-E-Mails**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-Mail-Kopie für Auftrag senden | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie für Bestellkommentar senden an | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie für Rechnung an senden | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie für Rechnungskommentar senden an | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Versand der E-Mail-Kopie an senden | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Versandkommentar-E-Mail-Kopie an senden | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie des Credit Memo an senden | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail-Kopie für Kommentar-Benachrichtigung an senden | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Abruf bereit-E-Mail-Kopie senden an | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Auschecken sensibler und systemspezifischer Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Checkout**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Zahlungsfehler bei E-Mail-Kopie an senden | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Von der Google API abhängige und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Google-API**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Container-ID | `google/analytics/container_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Versandmethoden - sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Versandmethoden**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Gateway-URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sichere Gateway-URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Titel | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Benutzer-ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Benutzer-ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffslizenznummer | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Tracking-XML-URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Gateway-XML-URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sendungsnummer | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Debuggen | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Konto-ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Schlüssel | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zähleranzahl | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffs-ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Debuggen | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Kontonummer | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Gateway-URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-Modus | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Verkaufssensitive und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Vertrieb**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Kontaktname | `sales/magento_rma/store_name` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Straße | `sales/magento_rma/address` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Straße | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Ort | `sales/magento_rma/city` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Bundesland/Provinz | `sales/magento_rma/region_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Postleitzahl | `sales/magento_rma/zip` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Land | `sales/magento_rma/country_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Senden der RMA-E-Mail-Kopie an | `sales_email/magento_rma/copy_to` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Senden der RMA-Autorisierungs-E-Mail-Kopie an | `sales_email/magento_rma_auth/copy_to` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| RMA-Kommentar-E-Mail-Kopie an senden | `sales_email/magento_rma_comment/copy_to` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| RMA-Kommentar-E-Mail-Kopie an senden | `sales_email/magento_rma_customer_comment/copy_to` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API-Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Google-API**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Kontonummer | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Erweiterte Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert**.

### Admin-sensible und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Admin**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Benutzerdefinierte Admin-URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Benutzerdefinierter Admin-Pfad | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Systembezogene und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fehler-E-Mail-Empfänger | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsliste | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Fehler-E-Mail-Absender | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Entwicklerbezogene und systemspezifische Pfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Zulässige IP-Adressen (durch Kommas getrennt) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Erweiterte Kategorie

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert**.

### Systempfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Port (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Backend-Host | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Backend-Port | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Entwicklerpfade

Diese Konfigurationswerte sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler**.

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| JS-Fehler beim Sitzungsspeicherschlüssel protokollieren | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Zahlungskritische und systemspezifische Pfade

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in Admin unter **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Zahlung**.

### Allgemeine Variable

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? |
|--------------|--------------|--------------|--------------|
| Handelsland | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>Ihre Auswahl für diese Variable bestimmt, welche [Internationale Pfade](#international-paths) können Sie verwenden.

### PayPal-sensible und systemspezifische Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Mit PayPal-Handelskonto verknüpfte E-Mail (optional) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant Account ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Herausgeber-ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Anmelden | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Hostname oder IP-Adresse des benutzerdefinierten Endpunkts | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-Modus | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Debug-Modus | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Debug-Modus | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| SFTP-Anmeldedaten | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro - sensible und systemspezifische Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Benutzer | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Benutzerdefinierter Pfad | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Benutzer | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Partner | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Proxy-Host | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Proxy-Port | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Debug-Modus | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| SFTP-Anmeldedaten | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Kreditkarteneinstellungen | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Link - sensible und systemspezifische Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Benutzer | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Passwort | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Proxy verwenden | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Proxy-Host | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Proxy-Port | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Debug-Modus | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| URL-Methode für Abbrechen der URL und Rückgabe-URL | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Debug-Modus | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| SFTP-Anmeldedaten | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro - sensible und systemspezifische Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API-Benutzername | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Passwort | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Signatur | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Zertifikat | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Proxy-Host | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Proxy-Port | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-Modus | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| SFTP-Anmeldedaten | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro Gehostete sensible und systemspezifische Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Debug-Modus | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| SFTP-Anmeldedaten | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintree- und systemspezifische Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Merchant-ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Öffentlicher Schlüssel | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Privater Schlüssel | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant Account ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-Name überschreiben | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Telefon | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Überprüfen/Money-Bestellpfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Prüfung senden an | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Internationale Pfade

| Name | Konfigurationspfad | Nur Commerce? | Verschlüsselt? | Systemspezifisch? | Sensitiv? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Transaktionsschlüssel | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_au/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_au/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_au/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_au/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_au/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_au/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-Modus | `payment_au/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_au/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_au/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_au/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_au/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_au/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_au/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_es/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_es/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_es/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_es/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_es/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_es/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_es/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Debuggen | `payment_es/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_es/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_es/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_es/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_es/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_es/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_es/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_es/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_nz/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_nz/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_nz/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_nz/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_nz/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_nz/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_nz/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_nz/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_nz/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Proxy-Host | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Proxy-Port | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Debug-Modus | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| URL-Methode für Abbrechen der URL und Rückgabe-URL | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_us/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_us/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_us/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_us/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_us/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_us/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_us/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_us/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_us/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_us/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_us/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_gb/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_gb/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_gb/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_gb/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_gb/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_gb/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_gb/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_gb/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_gb/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_de/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_de/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_de/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_de/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Transaktionsschlüssel | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zahlungsantwort-Passwort | `payment_de/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_de/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Debuggen | `payment_de/worldpay/debug` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_de/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_de/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_de/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_de/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_de/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_de/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_de/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Gateway-URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Transaktionsschlüssel | `payment_other/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_other/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_other/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Neuer Bestellstatus | `payment_other/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_other/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_other/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_other/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_other/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_other/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_other/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_other/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_other/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_other/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_other/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_other/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_ca/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_ca/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_ca/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Neuer Bestellstatus | `payment_ca/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_ca/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_ca/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Remote-Administratorberechtigungskennwort | `payment_ca/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_ca/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_ca/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_ca/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_ca/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_ca/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_ca/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_ca/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_ca/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_hk/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_hk/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_hk/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_hk/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zahlungsantwort-Passwort | `payment_hk/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_hk/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_hk/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Schlüssel | `payment_hk/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_hk/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_hk/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_hk/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_hk/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_hk/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_jp/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_jp/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_jp/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Neuer Bestellstatus | `payment_jp/cybersource/order_status` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_jp/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_jp/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_jp/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_jp/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_jp/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_jp/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_jp/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_jp/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_jp/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_jp/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_jp/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_fr/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_fr/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_fr/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_fr/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_fr/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_fr/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_fr/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_fr/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_fr/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_fr/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_fr/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_fr/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_fr/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_fr/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktions-Details-URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_it/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_it/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_it/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_it/cybersource/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Zahlungsantwort-Passwort | `payment_it/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_it/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_it/worldpay/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Sandbox-Modus | `payment_it/eway/sandbox_flag` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) |
| Live-API-Schlüssel | `payment_it/eway/live_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live-API-Passwort | `payment_it/eway/live_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Live Client-seitiger Verschlüsselungsschlüssel | `payment_it/eway/live_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Schlüssel | `payment_it/eway/sandbox_api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox-API-Passwort | `payment_it/eway/sandbox_api_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-seitiger Verschlüsselungsschlüssel | `payment_it/eway/sandbox_encryption_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Schlüssel | `fraud_protection/signifyd/api_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-URL | `fraud_protection/signifyd/api_url` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-spezifisch](/help/assets/configuration/cloud-env.png) | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_au/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_au/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_es/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_es/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_es/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten |
| SFTP-Anmeldedaten | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_nz/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_nz/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_nz/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_nz/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_nz/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_nz/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zahlungsantwort-Passwort | `payment_nz/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_nz/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_nz/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_nz/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_us/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_us/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_us/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_us/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zahlungsantwort-Passwort | `payment_us/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_us/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_us/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_us/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_gb/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_gb/cybersource/transaction_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_gb/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zugriffsschlüssel | `payment_gb/cybersource/access_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Geheimer Schlüssel | `payment_gb/cybersource/secret_key` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Transaktionsschlüssel | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_gb/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Zahlungsantwort-Passwort | `payment_gb/worldpay/response_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_gb/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote-Administratorberechtigungskennwort | `payment_gb/worldpay/auth_password` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_de/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_de/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_de/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Remote Admin Installation ID | `payment_de/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_de/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Neuer Bestellstatus | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_other/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_other/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_other/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_other/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_other/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Neuer Bestellstatus | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_ca/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_ca/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_ca/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_ca/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_ca/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_hk/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_hk/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_hk/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_hk/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_hk/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Signaturfelder | `payment_hk/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_jp/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_jp/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_jp/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |
| Remote Admin Installation ID | `payment_jp/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_jp/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Signaturfelder | `payment_jp/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_fr/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_fr/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_fr/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_fr/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_fr/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Signaturfelder | `payment_fr/worldpay/signature_fields` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| SFTP-Anmeldedaten | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Aktivieren Sie die Option Payable , um | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Prüfung senden an | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| API-Anmelde-ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Händler MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Email Customer | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| E-Mail des Händlers | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Merchant-ID | `payment_it/cybersource/merchant_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_it/cybersource/profile_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) | ![Verschlüsselt](/help/assets/configuration/cloud-enc.png) |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_it/worldpay/installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| Remote Admin Installation ID | `payment_it/worldpay/admin_installation_id` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |
| MD5-Geheimnis für Transaktionen | `payment_it/worldpay/md5_secret` | ![Nur Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensitiv](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
