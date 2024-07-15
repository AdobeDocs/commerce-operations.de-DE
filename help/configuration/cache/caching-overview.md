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

Mit [!DNL Commerce] können Sie Alternativen zum standardmäßigen Dateisystem-Caching konfigurieren. In diesem Leitfaden werden einige dieser Alternativen erörtert:

- Richten Sie die folgenden Cache-Mechanismen in der [!DNL Commerce]-Konfiguration ein:

   - [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Dateisystem (Standard): Zur Verwendung der standardmäßigen Dateisystem-Zwischenspeicherung ist keine Konfiguration erforderlich.

- Richten Sie den [Varnish](config-varnish.md) ein, ohne die [!DNL Commerce] -Konfiguration zu ändern.

## Caching-Terminologie

[!DNL Commerce] verwendet die folgende Caching-Terminologie:

- **Frontend**: Ähnlich wie eine Schnittstelle oder ein Gateway zum Cache-Speicher, implementiert von [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cache-Typen**: Kann einer der mit [!DNL Commerce] bereitgestellten Typen sein, oder Sie können [Ihre eigenen ](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/) erstellen.
- **Backend** - Gibt Details zum [Cache-Speicher](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) an, implementiert von [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Zweistufiges Backend**: Speichert Cache-Datensätze in zwei Backends: einem schnelleren und einem langsameren.

  >[!INFO]
  >
  >Die Backend-Cache-Konfiguration mit zwei Ebenen überschreitet den Rahmen dieses Handbuchs.

## Konfigurationsoptionen

- Ändern des bereitgestellten Cache-Frontend `default` -

  Sie ändern nur die Datei &quot;`<magento_root>/app/etc/di.xml`&quot;, die globale Konfiguration für die Abhängigkeitsinjektion der Commerce-Anwendung.

- Benutzerdefiniertes Cache-Frontend konfigurieren -

  Sie ändern nur die Datei &quot;`<magento_root>/app/etc/env.php`&quot;, da sie die entsprechende Konfiguration in der Datei &quot;`di.xml`&quot;überschreibt.

>[!TIP]
>
>Für die Varianten sind keine Änderungen an der [!DNL Commerce] -Konfiguration erforderlich. Siehe [Konfigurieren und Verwenden von Varnish](config-varnish.md).
