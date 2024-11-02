---
title: Planen von Admin-Aktualisierungen auf Produktions-Sites
description: Erfahren Sie mehr über Best Practices für die Planung kritischer Aktualisierungen an Adobe Commerce, um zu verhindern, dass die Leistung verlangsamt wird und Ausfälle auftreten.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# Best Practices für die Planung von Admin-Aktualisierungen auf Produktionssites

Planen Sie wichtige Aktualisierungen und Vorgänge auf Ihren Adobe Commerce-Sites außerhalb der Spitzenzeiten, um zu verhindern, dass die Leistung und der Ausfall von Produktionsstandorten verlangsamt werden.

Beispiele für kritische Aktionen:

- Änderungen der Admin-Konfiguration, z. B. Aktualisieren eines Produktattributs oder Verschieben einer Produkt-Unterkategorie in eine andere Kategorie
- Datenimport- oder -export-Vorgänge

Kritische Aktionen führen zu Cache-Invalidierungs- und Neuindizierungsvorgängen, die die Reaktionszeit erheblich erhöhen und Site-Ausfälle verursachen können.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Weitere Informationen

- [Best Practices für die Zwischenspeicherung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Privater Inhalt: Ungültiger privater Inhalt](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Hardware-Empfehlungen: Caches](../../../performance/hardware.md#caches)
- [Erweiterte Einrichtung: Redis einrichten](../../../performance/advanced-setup.md#set-up-redis)
