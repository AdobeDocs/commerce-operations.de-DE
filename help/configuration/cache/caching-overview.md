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
source-git-commit: dbc1f6d0edff87130604d4762477ee5892a7aafc
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 0%

---

# Caching-Übersicht und Konfigurationsoptionen

Adobe Commerce stützt sich auf eine mehrschichtige Caching-Architektur, um die Datenbanklast zu reduzieren, redundante Verarbeitung zu minimieren und die Seitenbereitstellung zu beschleunigen. Auf Anwendungsebene verwaltet Commerce mehr als ein Dutzend [Cache-Typen](../cli/manage-cache.md#clean-and-flush-cache-types) wie Konfiguration, Layout, Block-HTML und Sammlungen, von denen Sie jede an ein dediziertes Speicher-Backend wie [Redis](config-redis.md) oder [Valkey](config-valkey.md) weiterleiten können. Für das Zwischenspeichern ganzer Seiten in lokalen Bereitstellungen empfiehlt Adobe dringend [Varnish](config-varnish.md). Commerce in Cloud-Bereitstellungen verwenden Fastly. Zusätzliche Ebenen wie [L2-Caching](level-two-cache.md) und [statisches Content-Signing](static-content-signing.md) verbessern die Leistung bei Bereitstellungen mit mehreren Knoten und hohem Traffic weiter.

In diesem Handbuch wird erläutert, wie die einzelnen Caching-Ebenen funktionieren und wie Sie Frontends, Backends und erweiterte Optionen entsprechend Ihren Bereitstellungsanforderungen konfigurieren.

## Caching von Frontends

Ein Cache-Frontend ist eine Schnittstelle zwischen Commerce und dem Cache-Speicher-Backend. Sie können mehrere Frontends mit jeweils unterschiedlichen Backend-Einstellungen definieren und dann jedem Frontend [Cache-Typen](../cli/manage-cache.md#clean-and-flush-cache-types) zuweisen.  Konfigurationsdetails finden Sie unter [Konfigurieren von Cache-Frontends](cache-types.md).

## Caching von Backends

Ein Cache-Backend ist der zugrunde liegende Speichermechanismus für zwischengespeicherte Daten. Commerce bietet ein standardmäßiges Dateisystem-Backend, aber Sie können auch andere Backends wie Redis oder Valkey konfigurieren, um die Leistung und Skalierbarkeit zu verbessern. Einzelheiten zu den verfügbaren Optionen finden Sie unter [Cache-Backend-Optionen](cache-options.md).

## Vollständige Seitenzwischenspeicherung mit Lack

[Varnish Cache](config-varnish.md) ist ein HTTP-Beschleuniger, der vollständige Seiten im Speicher zwischenspeichert. Für lokale Produktionsumgebungen empfiehlt Adobe dringend Varnish , da es deutlich schneller ist als der integrierte Vollseiten-Cache. Commerce in Cloud-Umgebungen verwenden [Fastly](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/fastly) für das Caching ganzer Seiten anstelle von „Varnish“.

>[!NOTE]
>
>Varnish fungiert als Reverse-Proxy vor Ihrem Webserver und erfordert keine Änderungen an der Commerce-Cache-Backend-Konfiguration.

## L2-Caching (auf zwei Ebenen)

[L2-Cache](level-two-cache.md) speichert Cache-Daten lokal auf jedem Web-Knoten, während ein Remote-Cache (Redis oder Valkey) als Datenquelle verwendet wird. Dadurch wird der Netzwerkverkehr zwischen Ihren Web-Knoten und dem Remote-Cache reduziert, was die Leistung für Sites mit hohem Traffic verbessert.

## Zwischenspeicherung statischer Inhalte

[Statische Inhaltssignierung](static-content-signing.md) Invalidiert den Browser-Cache für statische Ressourcen (CSS, JavaScript, Bilder), indem eine Bereitstellungsversion in Datei-URLs eingebettet wird.

## Caching-Terminologie

[!DNL Commerce] verwendet die folgende Caching-Terminologie:

- **Frontend** - Eine Schnittstelle oder ein Gateway zum Zwischenspeichern, implementiert von [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cache-Typen** - Einer der integrierten Typen, die mit [!DNL Commerce] (z. B. `config`, `layout`, `block_html`, `full_page`) oder einem [benutzerdefinierten Typ](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/) bereitgestellt werden.
- **Backend** - Gibt die Details des [Cache-Speichers](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) an, implementiert durch [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend).
- **Zwei-Ebenen-Backend** - Speichert Cache-Einträge in zwei Backends: einem lokalen (schnellen) Cache und einem Remote-Cache (gemeinsam genutzt). Siehe [L2-Cache-Konfiguration](level-two-cache.md).

## Konfigurationsoptionen

Für die Zuordnung von Frontend zu Typ und die Cache-Konfigurationssyntax:

**On-Premise** - Die Cache-Konfiguration wird in zwei Dateien gespeichert:

- `<magento_root>/app/etc/di.xml` - Die Konfiguration der globalen Injektion von Abhängigkeiten. Ändern Sie diese Datei, um das bereitgestellte `default`-Cache-Frontend zu ändern.
- `<magento_root>/app/etc/env.php` - Umgebungsspezifische Konfiguration. Ändern Sie diese Datei, um benutzerdefinierte Cache-Frontends zu konfigurieren. Diese Datei überschreibt die entsprechende Konfiguration in `di.xml`.

Weitere Informationen finden Sie unter:

- [Cache-Frontends konfigurieren](cache-types.md) - Ein Cache-Frontend mit bestimmten Cache-Typen verknüpfen
- [Cache-Backend-Optionen](cache-options.md) - Referenz zur Backend-Option

**Adobe Commerce in Cloud** - Konfigurieren Sie das Caching mit `CACHE_CONFIGURATION` in `.magento.env.yaml`. Siehe [Best Practices für die Konfiguration von Redis- und Valkey-Services](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md).
