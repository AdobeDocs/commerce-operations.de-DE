---
title: Planen von Admin-Aktualisierungen auf Produktions-Sites
description: Erfahren Sie mehr über Best Practices für die Planung kritischer Aktualisierungen an Adobe Commerce, um zu verhindern, dass die Leistung verlangsamt wird und Ausfälle auftreten.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Best Practices für die Planung von Admin-Aktualisierungen auf Produktions-Sites

Planen Sie wichtige Aktualisierungen und Vorgänge auf Ihren Adobe Commerce-Sites außerhalb der Spitzenzeiten, um zu verhindern, dass die Leistung und der Ausfall von Produktionsstandorten verlangsamt werden.

Beispiele für kritische Aktionen:

- Änderungen der Admin-Konfiguration, z. B. Aktualisieren eines Produktattributs oder Verschieben einer Produkt-Unterkategorie in eine andere Kategorie
- Datenimport- oder -export-Vorgänge

Kritische Aktionen führen zu Cache-Invalidierungs- und Neuindizierungsvorgängen, die die Reaktionszeit erheblich erhöhen und Site-Ausfälle verursachen können.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Zusätzliche Informationen

- [Best Practices für die Zwischenspeicherung](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Privater Inhalt: Invalidierung privater Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Hardware-Empfehlungen: Caches](../../../performance/hardware.md#caches)
- [Erweitertes Setup: Einrichten von Redis](../../../performance/advanced-setup.md#set-up-redis)

