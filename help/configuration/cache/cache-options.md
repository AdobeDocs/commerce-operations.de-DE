---
title: Cache-Optionen
description: Erfahren Sie mehr über Cache-Optionen auf niedriger Ebene und die Speicherkonfiguration in Adobe Commerce. Entdecken Sie das Frontend-, Backend- und Speicher-Setup für Redis und Datenbanken.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Cache-Optionen auf niedriger Ebene

Die Commerce-Anwendung verwendet ein Cache-Frontend und ein Backend auf niedriger Ebene, um Zugriff auf den Cache-Speicher zu gewähren.

## Low-Level-Frontend-Cache

Commerce erweitert [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) durch die Implementierung des [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) Frontend-Caches.

## Backend-Cache auf niedriger Ebene

Im Allgemeinen funktioniert die Commerce-Anwendung mit jedem Backend-Cache, den [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) unterstützt. Dieses Handbuch behandelt jedoch nur die folgenden Backend-Caches auf niedriger Ebene:

- [Redis](config-redis.md)
- [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Dateisystem (Standard): Es ist keine Konfiguration erforderlich, um das Dateisystem-Caching zu verwenden.

[Varnish](config-varnish.md) erfordert kein Einrichten eines Cache-Backends auf niedriger Ebene.
