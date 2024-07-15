---
title: Umsetzungsplanung
description: Erfahren Sie mehr über die Best Practices für die Implementierung in der Planungsphase von Adobe Commerce-Projekten.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Planungsphase

Die Planungsphase umfasst die folgenden Aktivitäten:

- Architektonisches Design
- Katalogdesign
- Erweiterungskauf
- Projektumfang
- Anforderungserfassung
- Vertrieb und Marketing

Die folgenden Abschnitte enthalten Informationen zu Best Practices für die Planungsphase.

## Anforderungserfassung

<table>
<thead>
  <tr>
    <th>Best Practice</th>
    <th>Beschreibung</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Anwendungskonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Konfigurieren von Sites, Stores und Store-Ansichten</a></td>
    <td>Konfigurieren Sie Sites, Stores und Ansichten, um die Site-Leistung zu maximieren.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Allgemeine Konfigurationsprobleme</a></td>
    <td>Beheben und verhindern Sie die fünf häufigsten Konfigurationsprobleme für Adobe Commerce-Sites.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Zwischenspeicherung</a></td>
    <td>Verwenden Sie die Cache-Verwaltungstools, um die Leistung Ihrer Site zu verbessern.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Vollseitenzwischenspeicherung</a></td>
    <td>Erfahren Sie, wie Sie bei der Implementierung von Caching in Ihrer Adobe Commerce-Erweiterung mit öffentlichen Daten arbeiten.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache-Speichergröße</a></td>
    <td>Vermeiden Sie Leistungseinbußen mit bestimmten Einstellungen für den OPcache-Speicherverbrauch.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Reporting konfigurieren</a></td>
    <td>Optimieren Sie die Site-Leistung, indem Sie das Berichtsmodul entfernen, wenn Sie es nicht verwenden.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Datenbankkonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Konfigurieren der Datenbank für Cloud-Bereitstellungen</a></td>
    <td>Konfigurieren Sie Datenbank- und Anwendungseinstellungen, um die Leistung bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturprojekten zu verbessern.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">MySQL konfigurieren</a></td>
    <td>Erfahren Sie, wie MySQL-Trigger und Slave-Verbindungen die Site-Leistung beeinflussen und wie sie effektiv verwendet werden.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Dienstkonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Schnelles Einrichten</a></td>
    <td>Konfigurieren Sie die Fastly-Dienste für Ihr Adobe Commerce-Projekt in der Cloud-Infrastruktur.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Benachrichtigungskanäle für New Relic konfigurieren</a></td>
    <td>Greifen Sie auf Ihr New Relic-Dashboard zu und analysieren Sie Daten aus Ihrer Adobe Commerce in einem Cloud-Infrastrukturprojekt.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Konfigurieren von Redis</a></td>
    <td>Verbessern Sie die Cachingleistung durch Verwendung der erweiterten Redis-Cache-Implementierung für Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Cache-Größe für Realpath</a></td>
    <td>Optimieren Sie die Leistung, indem Sie die Cache-Konfiguration von PHP "readlpath"aktualisieren, um die empfohlenen Einstellungen zu verwenden.</td>
  </tr>
</tbody>
</table>

## Architektonisches Design

| Best Practice | Beschreibung |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [Globale Referenzarchitektur (GRA)](../../architecture/global-reference/examples.md) | Machen Sie sich mit den gängigen Methoden zur Organisation einer GRA-Codebasis vertraut. |

## Katalogdesign

| Best Practice | Beschreibung |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Kategoriekonfiguration](catalog-management.md#category-limits) | Konfigurieren Sie Produktkategorien für optimale Leistung. |
| [&#x200B; der Produktkonfiguration](catalog-management.md#product-sku-limits) | Konfigurieren Sie Produkt-SKUs für optimale Leistung. |
| [Konfiguration der Produktvarianten](catalog-management.md#product-variations) | Produktvarianten für optimale Leistung konfigurieren |
| [Konfiguration der Produktoptionen](catalog-management.md#product-options) | Konfigurieren Sie Produktoptionen für optimale Leistung. |
| [Konfiguration der Produktattribute &#x200B;](catalog-management.md#product-attributes) | Konfigurieren Sie Produktattribute für optimale Leistung. |
| [Paginierungskonfiguration für Produktlisten](catalog-management.md#product-listing-pagination) | Konfigurieren Sie die Paginierung der Produktliste für optimale Leistung. |

## Erweiterungen

| Best Practice | Beschreibung |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Verwenden von Drittanbietererweiterungen in Adobe Commerce](extensions.md) | Erfahren Sie, wie Sie Leistungsprobleme vermeiden, die durch Adobe Commerce-Erweiterungen von Drittanbietern verursacht werden. |

## Projektumfang

| Best Practice | Beschreibung |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Partner-Eskalationen](partner-escalation.md) | Bereiten Sie sich auf die Eskalation eines Partnerproblems mit einem Adobe-Account-Team vor oder lernen Sie, wie Sie eine Eskalation vermeiden können. |
| [Verarbeitung der Zahlungsspeicherung](payment-processing-storage.md) | Sichere Verarbeitung und Speicherung von Zahlungsdetails. |

## Vertrieb und Marketing

| Best Practice | Beschreibung |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Beschränkungen des Produktkartells](catalog-management.md#cart-limits) | Verwalten Sie Warenkorbbeschränkungen für optimale Leistung. |
| [Konfigurieren von Promotions](catalog-management.md#promotions) | Konfigurieren Sie Verkäufe und Promotions für Artikel in einem Warenkorb. |
