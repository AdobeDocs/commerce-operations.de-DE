---
title: Cacheoptionen
description: Konfigurieren Sie den Zugriff auf den Cache-Speicher auf niedriger Ebene.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Optionen für den Cache auf niedriger Ebene

Die Commerce-Anwendung verwendet eine einfache [cache](https://glossary.magento.com/cache) [frontend](https://glossary.magento.com/frontend) und [Backend](https://glossary.magento.com/backend) , um Zugriff auf den Cache-Speicher zu gewähren.

## Frontend-Cache auf niedriger Ebene

Commerce-Erweiterungen [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) durch Umsetzung [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) Frontend-Cache.

## Backend-Cache auf niedriger Ebene

Im Allgemeinen arbeitet die Commerce-Anwendung mit jedem Backend-Cache, der [Zend_Cache-Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) unterstützt. Dieses Handbuch behandelt jedoch nur die folgenden Backend-Caches auf niedriger Ebene:

- [Redis](config-redis.md)
- [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Dateisystem (Standard): Zur Verwendung der Dateisystem-Zwischenspeicherung ist keine Konfiguration erforderlich.

[Varnisch](config-varnish.md) erfordert keine Einrichtung eines Backend-Backend mit Cache auf niedriger Ebene.
