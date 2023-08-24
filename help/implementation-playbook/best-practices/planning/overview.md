---
title: Umsetzungsplanung
description: Erfahren Sie mehr über die Best Practices für die Implementierung in der Planungsphase von Adobe Commerce-Projekten.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Planungsphase

Die Planungsphase umfasst die folgenden Aktivitäten:

- Anforderungserfassung
- Architektonisches Design
- Katalogdesign
- Projektumfang
- Kontobereitstellung
- Benutzerzugriff
- Erweiterungskauf

Die folgenden Abschnitte enthalten Informationen zu Best Practices für die Planungsphase.

## Anforderungserfassung

- **Anwendungskonfiguration**
   - [Best Practices zum Konfigurieren von Sites, Stores und Store-Ansichten (Cloud-Infrastruktur)](sites-stores-store-views.md)
   - [So verhindern - und beheben Sie die fünf häufigsten Konfigurationsprobleme für Adobe Commerce-Sites](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Best Practices für die Zwischenspeicherung](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Zwischenspeicherung auf einer vollständigen Seite](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache-Speichergröße](opcache-memory-size.md)
   - [Berichtskonfiguration](reporting-configuration.md)

- **Datenbankkonfiguration**
   - [Best Practices für die Datenbankkonfiguration für Cloud-Bereitstellungen &#x200B;](database-on-cloud.md)
   - [MySQL-&#x200B;](mysql-configuration.md)

- **Dienstkonfiguration**
   - [Schnelles Einrichten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Benachrichtigungskanäle konfigurieren](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Best Practices für die Konfiguration des Redis-Dienstes &#x200B;](redis-service-configuration.md)
   - [Best Practice für die Cache-Größe von realpath](realpath-cache-size.md)

## **Architektonisches Design**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Die globale Referenzarchitektur verstehen](../../../implementation-playbook/architecture/global-reference.md)

## **Katalogdesign**

In den folgenden Themen werden die Best Practices zur Leistungsoptimierung für die Konfiguration Ihres Adobe Commerce-Katalogs beschrieben, einschließlich der empfohlenen Höchstwerte für die Anzahl der Kategorien, produktwirksamen SKUs, Produktvarianten, Produktattribute und Optionen und mehr.

- [Kategoriekonfiguration](catalog-management.md#category-limits)
- [&#x200B; der Produktkonfiguration](catalog-management.md#product-sku-limits)
- [Konfiguration von Produktvarianten](catalog-management.md#product-variations)
- [Konfiguration der Produktoptionen](catalog-management.md#product-options)
- [&#x200B; der Produktattributkonfiguration](catalog-management.md#product-attributes)
- [Paginierungskonfiguration für Produktlisten](catalog-management.md#product-listing-pagination)

## **Vertrieb und Marketing**

- [Best Practices für die Beschränkung des Warenkorbs](catalog-management.md#cart-limits)
- [Best Practices zum Konfigurieren von Promotions](catalog-management.md#promotions)

## **Projektumfang**

- [Partnereskalationen](partner-escalation.md)
- [Verarbeitung der Zahlungsspeicherung](payment-processing-storage.md)

## **Kauferweiterungen**

- [Best Practices für die Verwendung von Erweiterungen von Drittanbietern in Adobe Commerce](extensions.md)
