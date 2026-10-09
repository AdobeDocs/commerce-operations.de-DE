---
title: Planen von Admin-Updates auf Produktions-Sites
description: Erfahren Sie mehr über Best Practices für die Planung wichtiger Updates für Adobe Commerce, um eine langsame Leistung und Ausfälle zu verhindern.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%
---
# Best Practices für die Planung von Admin-Updates auf Produktions-Sites

Planen Sie wichtige Updates und Vorgänge auf Ihren Adobe Commerce-Sites außerhalb der Spitzenzeiten, um eine langsame Leistung und Ausfälle an Produktions-Sites zu verhindern.

Beispiele für kritische Aktionen:

- Änderungen an der Admin-Konfiguration, z. B. Aktualisieren eines Produktattributs oder Verschieben einer Produktunterkategorie in eine andere Kategorie
- Datenimport- oder -exportvorgänge

Kritische Aktionen führen zu Vorgängen zur Cache-Invalidierung und -Neuindizierung, die die Reaktionszeit erheblich verlängern und zu Site-Ausfällen führen können.

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Weitere Informationen

- [Best Practices für das Caching](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Privater Inhalt: Invalidierung privater Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [Hardware-Empfehlungen: Caches](../../../performance/hardware.md#caches)
- [Erweitertes Setup: Einrichten von Redis](../../../performance/advanced-setup.md#set-up-redis)
