---
title: Referenz zu Dienstkonfigurationspfaden
description: Siehe eine Liste der Konfigurationswerte für Services.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
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
