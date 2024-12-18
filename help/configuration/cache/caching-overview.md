---
title: Konfigurieren des Caching
description: Erfahren Sie mehr über das Caching und das Konfigurieren von Cache-Mechanismen für das Adobe Commerce-Programm.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Konfigurieren des Caching

[!DNL Commerce] können Sie Alternativen zum standardmäßigen Dateisystem-Caching konfigurieren. In diesem Handbuch werden einige dieser Alternativen erläutert, nämlich

- Richten Sie die folgenden Cache-Mechanismen in der [!DNL Commerce] ein:

   - [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Dateisystem (Standard): Es ist keine Konfiguration erforderlich, um das standardmäßige Dateisystem-Caching zu verwenden.

- Richten Sie den [Varnish](config-varnish.md) ein, ohne die [!DNL Commerce]-Konfiguration zu ändern.

## Caching-Terminologie

[!DNL Commerce] verwendet die folgende Caching-Terminologie:

- **Frontend** - Ähnlich wie eine Schnittstelle oder ein Gateway zum Zwischenspeichern, implementiert von [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cache-Typen** - Kann einer der mit [!DNL Commerce] bereitgestellten Typen sein oder Sie können [eigene erstellen](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend** - Gibt Details zum [Cache-Speicher](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) an, implementiert durch [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Backend mit zwei Ebenen** - Speichert Cache-Einträge in zwei Backends: einem schnelleren und einem langsameren.

  >[!INFO]
  >
  >Die Konfiguration des Backend-Cache auf zwei Ebenen sprengt den Rahmen dieses Handbuchs.

## Konfigurationsoptionen

- Ändern des bereitgestellten `default`-Cache-Frontends—

  Sie ändern nur die `<magento_root>/app/etc/di.xml`, die Konfiguration der globalen Injektion von Abhängigkeiten der Commerce-Anwendung.

- Konfigurieren Ihres eigenen benutzerdefinierten Cache-Frontends -

  Sie ändern nur die `<magento_root>/app/etc/env.php`, da sie die entsprechende Konfiguration in der `di.xml` überschreibt.

>[!TIP]
>
>Der Lack erfordert keine Änderungen an der [!DNL Commerce]. Siehe [Konfigurieren und Verwenden von ](config-varnish.md).
