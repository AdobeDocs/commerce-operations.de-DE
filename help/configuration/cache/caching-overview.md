---
title: Zwischenspeicherung konfigurieren
description: Erfahren Sie mehr über das Zwischenspeichern und wie Sie Cache-Mechanismen für die Adobe Commerce-Anwendung konfigurieren.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Zwischenspeicherung konfigurieren

[!DNL Commerce] ermöglicht es Ihnen, Alternativen zum standardmäßigen Dateisystem-Caching zu konfigurieren. In diesem Leitfaden werden einige dieser Alternativen erörtert:

- Richten Sie die folgenden Cache-Mechanismen im [!DNL Commerce] Konfiguration:

   - [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Dateisystem (Standard): Zur Verwendung der standardmäßigen Dateisystem-Zwischenspeicherung ist keine Konfiguration erforderlich.

- Richten Sie die [Varnisch](config-varnish.md) ohne die [!DNL Commerce] Konfiguration.

## Caching-Terminologie

[!DNL Commerce] verwendet die folgende Caching-Terminologie:

- **Frontend**—Ähnlich wie eine Schnittstelle oder ein Gateway zum Cache-Speicher, implementiert von [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cachetypen**—Kann einer der Typen sein, die mit [!DNL Commerce] oder [Erstellen eigener](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend**—Gibt Details zu [Cache-Speicher](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementiert von [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Zweistufiges Backend**—Speichert Cache-Datensätze in zwei Backends: einem schnelleren und einem langsameren.

  >[!INFO]
  >
  >Die Backend-Cache-Konfiguration mit zwei Ebenen überschreitet den Rahmen dieses Handbuchs.

## Konfigurationsoptionen

- Ändern der bereitgestellten `default` cache frontend—

  Sie ändern nur die `<magento_root>/app/etc/di.xml` -Datei, die globale Konfiguration für die Abhängigkeitsinjektion der Commerce-Anwendung.

- Benutzerdefiniertes Cache-Frontend konfigurieren -

  Sie ändern nur die `<magento_root>/app/etc/env.php` -Datei, da sie die entsprechende Konfiguration im `di.xml` -Datei.

>[!TIP]
>
>Für die Löschung sind keine Änderungen am [!DNL Commerce] Konfiguration. Siehe [Konfigurieren und Verwenden von Varnish](config-varnish.md).
