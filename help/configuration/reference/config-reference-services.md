---
title: Referenz zu Dienstkonfigurationspfaden
description: Erfahren Sie mehr über Dienstkonfigurationspfade und -werte in den Adobe Commerce Admin-Einstellungen. Entdecken Sie Konfigurationsoptionen für Web-API, OAuth und Service-Integration.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%
---
# Referenz zu Dienstkonfigurationspfaden

In diesem Abschnitt werden Variablennamen und Konfigurationspfade aufgelistet, die für Optionen in der Admin unter **Stores** > Einstellungen > **Konfiguration** > **Services** verfügbar sind.

Der [`magento app:config:dump` Befehl ](../cli/export-configuration.md) diese Werte in die freigegebene Konfigurationsdatei `app/etc/config.php`, die sich in der Versionsverwaltung befinden sollte. Informationen dazu, wie Sie Konfigurationseinstellungen optional überschreiben oder vertrauliche Einstellungen festlegen können, finden Sie unter [Verwenden von Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen](override-config-settings.md#environment-variables). In diesem _werden_ ([ und systemspezifische Werte) ](config-reference-sens.md).

## Commerce Web-API-Pfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Services** > **Web API** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Charset der Standardantwort | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anonymen Gastzugriff zulassen | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth-Pfade

Diese Konfigurationswerte sind in der Admin-Liste unter **Stores** > Einstellungen > **Konfiguration** > **Services** > **OAuth** verfügbar.

| -Name | Konfigurationspfad | Nur Commerce? |
|--------------|--------------|--------------|
| Lebensdauer des Kunden-Tokens (Stunden) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Admin-Token-Lebensdauer (Stunden) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bereinigungswahrscheinlichkeit | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verfallszeit | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verfallszeit | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth Consumer Credentials HTTP Post maxRedirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP-Post-Timeout für OAuth-Verbraucheranmeldeinformationen | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
