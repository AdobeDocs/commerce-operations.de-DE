---
title: Referenz zu Dienstkonfigurationspfaden
description: Eine Liste der Dienstkonfigurationswerte anzeigen.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Referenz zu Dienstkonfigurationspfaden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen im Admin unter **Stores** > Einstellungen > **Konfiguration** > **Dienste** verfügbar sind.

Der Befehl [`magento app:config:dump`](../cli/export-configuration.md) schreibt diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Quell-Code-Verwaltung befinden sollte. Informationen zum optionalen Außerkraftsetzen von Konfigurationseinstellungen oder zum Festlegen sensibler Einstellungen finden Sie unter [Verwenden von Umgebungsvariablen zum Außerkraftsetzen von Konfigurationseinstellungen](override-config-settings.md#environment-variables). Bei diesem Thema werden _nicht_ vertrauliche und systemspezifische Werte [ aufgelistet.](config-reference-sens.md)

## Commerce Web API-Pfade

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Dienste** > **Web-API** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Standard-Antwortcharset | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anonymen Gastzugang zulassen | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth-Pfad

Diese Konfigurationswerte sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > **Dienste** > **OAuth** verfügbar.

| Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Lebensdauer des Kunden-Tokens (Stunden) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lebensdauer des Admin-Tokens (Stunden) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cleanup-Wahrscheinlichkeit | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ablaufzeitraum | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ablaufzeitraum | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth-Kundenanmeldeinformationen HTTP Post-Maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth-Kundenanmeldeinformationen HTTP Post-Zeitüberschreitung | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
