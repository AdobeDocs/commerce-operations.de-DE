---
title: Cacheoptionen
description: Konfigurieren Sie den Zugriff auf den Cache-Speicher auf niedriger Ebene.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Optionen für den Cache auf niedriger Ebene

Die Commerce-Anwendung verwendet ein Cache-Frontend und -Backend niedriger Ebene, um Zugriff auf den Cache-Speicher zu gewähren.

## Frontend-Cache auf niedriger Ebene

Commerce-Erweiterungen [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) durch Umsetzung [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) Frontend-Cache.

## Backend-Cache auf niedriger Ebene

Im Allgemeinen arbeitet die Commerce-Anwendung mit jedem Backend-Cache, der [Zend_Cache-Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) unterstützt. Dieses Handbuch behandelt jedoch nur die folgenden Backend-Caches auf niedriger Ebene:

- [Redis](config-redis.md)
- [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Dateisystem (Standard): Zur Verwendung der Dateisystem-Zwischenspeicherung ist keine Konfiguration erforderlich.

[Varnisch](config-varnish.md) erfordert keine Einrichtung eines Backend-Backend mit Cache auf niedriger Ebene.
