---
title: Caching-Übersicht und Konfigurationsoptionen
description: Erfahren Sie mehr über das Caching in Adobe Commerce, einschließlich Backend-Speicher, Frontend-Konfiguration und Vollseiten-Caching mit Varnish, Redis, Valkey und L2-Cache.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# Caching-Übersicht und Konfigurationsoptionen

Adobe Commerce verwendet mehrere Caching-Ebenen, um die wiederholte Verarbeitung zu reduzieren, die Datenbanklast zu reduzieren und die Antwortzeiten zu verbessern. Diese Ebenen arbeiten an verschiedenen Punkten der Anfrage- und Asset-Bereitstellung:

- **Anwendungs-Caching** speichert generierte oder verarbeitete Daten mithilfe von Commerce-Cache-Typen.
- **HTTP-Caching (vollständige Seite** speichert vollständige HTTP-Antworten, bevor sie das Commerce-Programm erreichen.
- **L2** Caching kann einen lokalen Cache auf jedem Web-Knoten vor dem freigegebenen Remote-Cache-Speicher hinzufügen.
- **Zwischenspeicherung statischer Inhalte** ermöglicht es Browsern, CSS, JavaScript, Bilder und andere statische Ressourcen wiederzuverwenden.

Diese Seite bietet einen konzeptionellen Überblick über diese Ebenen und Links zu ihren Konfigurationsanleitungen. Informationen zu Backend-Optionen, Implementierungsdetails und versionsspezifischen Einstellungen finden Sie unter [Cache-Backend-Optionen und Speicherreferenz](cache-options.md).

## Zwischenspeichern von Ebenen

### Anwendungs-Caching

Das Caching von Commerce-Anwendungen ist wie folgt organisiert:

>[!BEGINSHADEBOX]

Cache-Typ → Cache-Frontend → Cache-Backend

>[!ENDSHADEBOX]

Ein **Cache-Typ** identifiziert die Art der Daten, die zwischengespeichert werden, z. B. Konfiguration, Layout, HTML blockieren oder ganzseitige Inhalte. Ein **Cache-Frontend** verbindet einen oder mehrere Cache-Typen mit dem Speicher. Ein **Cache-Backend** stellt die -Speicherimplementierung bereit.

Sie können verschiedenen Frontends verschiedene Cache-Typen zuweisen, wenn separate Cache-Einstellungen oder Speicher erforderlich sind. Konfigurationsdetails finden Sie unter [Konfigurieren von Cache-Frontends und -Typen](cache-types.md).

### Vollständige HTTP-Zwischenspeicherung

Die vollständige HTTP-Seitenzwischenspeicherung speichert vollständige Antworten auf der HTTP- oder CDN-Ebene. Für Produktionsbereitstellungen:

- **Adobe Commerce On-Premises** - Adobe empfiehlt [Varnish](config-varnish.md) für das Caching ganzer Seiten. Varnish fungiert als Reverse-Proxy vor dem Webserver.
- **Adobe Commerce in der Cloud** Infrastruktur verwendet [Fastly](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"} für die Edge- und Vollseiten-Caching-Ebene. Die Cloud-Infrastruktur verwendet keinen separat verwalteten Lackdienst.

>[!NOTE]
>
>Beim Ändern des Cache-Backends der Commerce-Anwendung werden Varnish oder Fastly nicht konfiguriert. Die vollständige HTTP-Zwischenspeicherung von Seiten wird getrennt vom Anwendungscache auf niedriger Ebene konfiguriert und verwaltet.

### L2-Caching

L2-Caching (auf zwei Ebenen) fügt auf jedem Commerce-Web-Knoten einen lokalen Cache hinzu, während der freigegebene Remote-Cache-Speicher beibehalten wird. Häufig genutzte Daten können lokal bereitgestellt werden, wodurch die Kommunikation mit dem Remote-Cache in Bereitstellungen mit mehreren Knoten reduziert wird.

Die L2-Konfiguration und die unterstützten Implementierungen variieren je nach Commerce-Version und Bereitstellungstyp. Weitere Informationen finden Sie unter [L2-Cache-Konfiguration](level-two-cache.md).

### Zwischenspeicherung statischer Inhalte

Commerce kann die Browserzwischenspeicherung für statische Ressourcen wie CSS, JavaScript und Bilder verbessern, indem es eine Bereitstellungsversion zu ihren URLs hinzufügt. Wenn sich der Inhalt ändert, ändert sich die URL, sodass der Browser die neue Ressource anfordert, anstatt eine ältere zwischengespeicherte Kopie zu verwenden.

## Bereitstellungsspezifische Konfiguration

Die folgenden Konfigurationsaufgaben variieren je nach Bereitstellungstyp.

| Aufgabe | On-Premises | Cloud-Infrastruktur |
| --- | --- | --- |
| Anwendungs-Cache-Backends | [Cache-Backend-Optionen und Speicherreferenz](cache-options.md) | [Best Practices für die Konfiguration des Valkey- und Redis-Service](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| HTTP-Caching ganzer Seiten | [Lack konfigurieren](config-varnish.md) | [Fastly Services - Übersicht](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/cdn/fastly) |

Die folgenden Aufgaben gelten für alle Bereitstellungstypen:

- **Konfigurieren von Cache-Typen** Frontends[Konfigurieren von Cache-Frontends und -](cache-types.md), um Cache-Typen mit Cache-Frontends zu verknüpfen.
- **Konfigurieren von L2** Caching - [L2-Cache-Konfiguration](level-two-cache.md).
- **Browser-Cache-Invalidierung für statische Inhalte konfigurieren**—[Statische Inhaltssignierung und Browser-Cache-Invalidierung](static-content-signing.md).
