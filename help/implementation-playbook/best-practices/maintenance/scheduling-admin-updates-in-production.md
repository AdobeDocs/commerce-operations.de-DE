---
title: Planen von Admin-Updates auf Produktions-Sites
description: Erfahren Sie mehr über Best Practices für die Planung wichtiger Updates für Adobe Commerce, um eine langsame Leistung und Ausfälle zu verhindern.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
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

- [Best Practices für das Caching](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Privater Inhalt: Invalidierung privater Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Hardware-Empfehlungen: Caches](../../../performance/hardware.md#caches)
- [Erweitertes Setup: Einrichten von Redis](../../../performance/advanced-setup.md#set-up-redis)
