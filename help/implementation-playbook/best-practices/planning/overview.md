---
title: Umsetzungsplanung
description: Erfahren Sie mehr über Best Practices bei der Implementierung für die Planungsphase von Adobe Commerce-Projekten.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '245'
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
   - [MySQL-Slave-Verbindungskonfiguration &#x200B;](configure-mysql-slave-connection-on-cloud.md)
   - [Verwendung von MySQL-Triggern](mysql-triggers-usage.md)

- **Dienstkonfiguration**
   - [Schnelles Einrichten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Konfigurieren von Benachrichtigungskanälen](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Best Practices für die Konfiguration des Redis-Dienstes &#x200B;](redis-service-configuration.md)
   - [Best Practice für die Cache-Größe von realpath](realpath-cache-size.md)

## **Architektonisches Design**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Grundlegendes zur globalen Referenzarchitektur](../../../implementation-playbook/architecture/global-reference.md)

## **Katalogdesign**

In den folgenden Themen werden die Best Practices zur Leistungsoptimierung für die Konfiguration Ihres Adobe Commerce-Katalogs beschrieben, einschließlich der empfohlenen Höchstwerte für die Anzahl der Kategorien, produktwirksamen SKUs, Produktvarianten, Produktattribute und Optionen und mehr.

- [Kategoriekonfiguration](category-limits.md)
- [&#x200B; der Produktkonfiguration](product-sku-limits.md)
- [Konfiguration von Produktvarianten](product-variations.md)
- [Konfiguration der Produktoptionen](product-options.md)
- [&#x200B; der Produktattributkonfiguration](product-attributes-and-options.md)
- [Paginierungskonfiguration für Produktlisten](product-listing-pagination.md)

## **Vertrieb und Marketing**

- [Best Practices für die &#x200B; des Warenkorbs](product-cart.md)
- [Best Practices zum Konfigurieren von Promotions](product-cart-promotions.md)

## **Projektumfang**

- [Partnereskalationen](partner-escalation.md)

## **Kauferweiterungen**

- [Best Practices für die Verwendung von Erweiterungen von Drittanbietern in Adobe Commerce &#x200B;](extensions.md)