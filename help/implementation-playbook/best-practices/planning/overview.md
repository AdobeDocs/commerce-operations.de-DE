---
title: Implementierungsplanung
description: Erfahren Sie mehr über Best Practices für die Implementierung in der Planungsphase von Adobe Commerce-Projekten.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# Planungsphase

Die Planungsphase umfasst die folgenden Aktivitäten:

- Architektonisches Design
- Katalogdesign
- Einkauf erweitern
- Projektumfang
- Anforderungserfassung
- Vertrieb und Marketing

Die folgenden Abschnitte enthalten Best Practice-Informationen für die Planungsphase.

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
    <td>Konfigurieren Sie Sites, Stores und Store-Ansichten, um die Site-Leistung zu maximieren.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Häufige Konfigurationsprobleme</a></td>
    <td>Beheben und verhindern Sie die fünf häufigsten Konfigurationsprobleme für Adobe Commerce Sites.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Caching</a></td>
    <td>Verwenden Sie die Cache-Management-Tools, um die Leistung Ihrer Site zu verbessern.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Vollständige Seitenzwischenspeicherung</a></td>
    <td>Erfahren Sie, wie Sie beim Implementieren der Zwischenspeicherung in Ihrer Adobe Commerce-Erweiterung mit öffentlichen Daten arbeiten.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OP-Cache-Speichergröße</a></td>
    <td>Vermeiden Sie Leistungseinbußen mit bestimmten Einstellungen für den OP-Cache-Speicherverbrauch.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Konfigurieren von Berichten</a></td>
    <td>Optimieren Sie die Site-Leistung, indem Sie das Reporting-Modul entfernen, wenn Sie es nicht verwenden.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Datenbankkonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Konfigurieren der Datenbank für Cloud-Bereitstellungen</a></td>
    <td>Konfigurieren Sie Datenbank- und Anwendungseinstellungen, um die Leistung bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturprojekten zu verbessern.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Konfigurieren von MySQL</a></td>
    <td>Erfahren Sie, wie MySQL-Trigger und Slave-Verbindungen die Site-Performance beeinflussen und wie Sie sie effektiv nutzen können.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Service-Konfiguration</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Schnell einrichten</a></td>
    <td>Konfigurieren Sie Fastly Services für Ihr Adobe Commerce in einem Cloud-Infrastrukturprojekt.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Konfigurieren von Benachrichtigungskanälen für New Relic</a></td>
    <td>Greifen Sie auf Ihr New Relic-Dashboard zu und analysieren Sie Daten aus Ihrem Adobe Commerce in einem Cloud-Infrastrukturprojekt.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Konfigurieren von Redis</a></td>
    <td>Verbessern Sie die Caching-Leistung durch die Verwendung der erweiterten Redis-Cache-Implementierung für Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">RealPath-Cachegröße</a></td>
    <td>Optimieren Sie die Leistung, indem Sie die Cache-Konfiguration „readpath“ von PHP so aktualisieren, dass sie die empfohlenen Einstellungen verwendet.</td>
  </tr>
</tbody>
</table>

## Katalogdesign

| Best Practice | Beschreibung |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Kategoriekonfiguration](catalog-management.md#category-limits) | Konfigurieren Sie Produktkategorien für optimale Leistung. |
| [Produktkonfiguration&#x200B;](catalog-management.md#product-sku-limits) | Produkt-SKUs für optimale Leistung konfigurieren. |
| [Konfiguration von Produktvarianten](catalog-management.md#product-variations) | Konfigurieren Sie Produktvarianten für optimale Leistung. |
| [Konfiguration von Produktoptionen](catalog-management.md#product-options) | Konfigurieren Sie Produktoptionen für eine optimale Leistung. |
| [Konfiguration von Produktattributen&#x200B;](catalog-management.md#product-attributes) | Konfigurieren Sie Produktattribute für eine optimale Leistung. |
| [Paginierungskonfiguration für Produktlisten](catalog-management.md#product-listing-pagination) | Konfigurieren Sie die Paginierung der Produktliste für eine optimale Leistung. |

## Erweiterungen

| Best Practice | Beschreibung |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Verwenden von Erweiterungen von Drittanbietern in Adobe Commerce](extensions.md) | Erfahren Sie, wie Sie Leistungsprobleme vermeiden können, die durch Adobe Commerce-Erweiterungen von Drittanbietern verursacht werden. |

## Projektumfang

| Best Practice | Beschreibung |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Partner-Eskalationen](partner-escalation.md) | Bereiten Sie sich auf die Eskalation eines Partnerproblems mit einem Adobe Account Team vor oder erfahren Sie, wie Sie eine Eskalation vermeiden können. |
| [Zahlungsverarbeitung](payment-processing-storage.md) | Sichere Verarbeitung und Speicherung von Zahlungsdetails. |

## Vertrieb und Marketing

| Best Practice | Beschreibung |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Limits für den Warenkorb](catalog-management.md#cart-limits) | Warenkorbbeschränkungen verwalten, um eine optimale Leistung zu erzielen. |
| [Konfigurieren von Promotions](catalog-management.md#promotions) | Konfigurieren Sie Verkäufe und Promotions für Artikel in einem Warenkorb. |
