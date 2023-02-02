---
title: Entwicklungsumgebung - Recommendations
description: Erfahren Sie mehr über Leistungsempfehlungen zum Einrichten Ihrer lokalen Adobe Commerce- oder Magento Open Source-Entwicklungsumgebung.
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Empfehlungen zur Entwicklungsumgebung

Diese Seite enthält Empfehlungen für Commerce-Entwicklungsumgebungen.

## Entfernen Sie die Zwischenspeicher, anstatt sie zu deaktivieren.

Viele Entwickler neigen dazu, alle Caches auf ihren Entwicklerinstanzen zu deaktivieren. Es wird empfohlen, nur Caches zu reinigen, ohne alle Caches zu deaktivieren. [!DNL Commerce] effizienter arbeiten, wenn Sie [Caches bereinigen](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) anstatt sie vollständig zu deaktivieren. Die meisten Arten von Caches werden während der Entwicklung selten invalidiert.

Wenn Sie [Deaktivieren der Caches](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), empfehlen wir, nur die Seiten- und Blockierungszwischenspeicher in Entwicklungsinstanzen zu deaktivieren. Denken Sie daran, alle Caches während des Tests zu aktivieren.

## Befehle, die im Entwicklungsmodus vermieden werden sollen

Führen Sie im Entwicklungsmodus keine Befehle zur Kompilierung, Codegenerierung und statischen Inhaltsbereitstellung aus. Diese Befehle wurden nur für die Verwendung im Produktionsmodus erstellt.

**Nicht ausführen** Produktionsbefehle im Entwicklungsmodus:

* `setup:di:compile` generiert automatisch generierte Klassen und optimierte Konfigurations-Caches.

   ```bash
   bin/magento setup:di:compile
   ```

   Im Entwicklungsmodus führt Magento die Generierung On-Demand durch. Sie müssen es nicht ausführen. Wenn Sie eine Signatur einer Klasse geändert haben und deren automatisch generierte `factories/proxies/interceptors`, entfernen Sie diese Klassen oder die _generiert_ Ordner.

* `setup:static-content:deploy` stellt statische Inhalte für einen Store bereit.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   Im Entwicklungsmodus führt Magento ihn bei Bedarf aus. Sie müssen es nicht ausführen.

## Normale Seitenladezeit auf einem virtuellen Computer

Wenn Sie auf einer VM entwickeln und das Laden einer Magento-Seite länger als 2 Sekunden dauert, überprüfen Sie Ihre Umgebungseinstellungen.
