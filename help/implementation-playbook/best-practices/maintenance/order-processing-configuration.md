---
title: Best Practices für die Auftragsverarbeitung konfigurieren
description: Erfahren Sie mehr über die Best Practices bei der Konfiguration, um die Leistung bei der Kasse- und Auftragsverarbeitung zu verbessern.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Best Practices für die Auftragsverarbeitung konfigurieren

Da das Auftragsvolumen auf Ihren Commerce-Sites zunimmt, können Sie die Leistung des Auscheckens und die Auftragsverarbeitung optimieren, indem Sie die folgenden Speicherkonfigurationsoptionen aktivieren:

- **[!UICONTROL Asynchronous indexing]**—Aktivieren Sie diese Option, um Datenbanksperren und eine verlangsamte Verarbeitung zu verhindern, die auftreten können, wenn eine große Anzahl von Bestellungen gleichzeitig aufgegeben wird.
- **[!UICONTROL Asynchronous email notifications]**—Aktivieren Sie diese Option, um die Leistung beim Checkout zu beschleunigen, indem Sie E-Mail-Benachrichtigungen zum Checkout senden und bestellen, anstatt sie sofort zu senden.
- **[!UICONTROL Enable Archiving]**—Aktivieren Sie diese Option, um Bestellungen zu archivieren und Datenbankspeicherplatz für eine schnellere Auftragsverarbeitung freizugeben. Siehe [Aktivieren der Archivierung](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Aktivieren der asynchronen Bestellverarbeitung

Die Schritte zum Aktivieren der asynchronen Bestellverarbeitung hängen vom Bereitstellungsmodus ab:

- Verwenden Sie für Adobe Commerce in der Cloud-Infrastruktur und lokalen Sites im Produktionsmodus den folgenden Magento-CLI-Befehl, um die asynchrone Indizierung zu aktivieren:

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- Aktivieren Sie bei lokalen Adobe Commerce-Sites im Standard- oder Produktionsmodus die asynchrone Indizierung, indem Sie die Konfiguration der Rastereinstellungen in Admin aktualisieren.

   Siehe [Geplante Rasteraktualisierungen und Neuindizierungen aktivieren](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >Testen Sie Konfigurationsänderungen immer in der Staging-Umgebung, bevor Sie die Produktionsumgebung aktualisieren.

## Zusätzliche Informationen

- [Best Practices bei der Konfiguration](../../../performance/configuration.md)
- [Referenz zu allgemeinen und erweiterten Konfigurationspfaden](../../../configuration/reference/config-reference-general.md)
- [Verarbeitung hoher Durchsatzaufträge](../../../performance/high-throughput-order-processing.md)