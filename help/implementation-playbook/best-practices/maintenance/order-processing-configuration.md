---
title: Best Practices für die Konfiguration der Bestellverarbeitung
description: Erfahren Sie mehr über Best Practices für die Konfiguration, um die Leistung bei der Kasse und der Bestellverarbeitung zu verbessern.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%
---
# Best Practices für die Konfiguration der Bestellverarbeitung

Da das Bestellvolumen auf Ihren Commerce-Sites zunimmt, können Sie die Checkout-Leistung und die Bestellverarbeitung optimieren, indem Sie die folgenden Store-Konfigurationsoptionen aktivieren:

- **[!UICONTROL Asynchronous indexing]** - Aktivieren Sie diese Option, um Datenbanksperren und eine verlangsamte Verarbeitung zu verhindern, die auftreten können, wenn eine große Anzahl von Bestellungen gleichzeitig aufgegeben wird.
- **[!UICONTROL Asynchronous email notifications]** - Aktivieren Sie diese Option, um die Kaufleistung zu beschleunigen, indem Sie E-Mail-Benachrichtigungen zur Kasse und Bestellabwicklung in festgelegten Intervallen senden, anstatt sie sofort zu senden.
- **[!UICONTROL Enable Archiving]** - Aktivieren Sie diese Option, um die Leistung von Bestellungen, Rechnungen, Lieferungen und Gutschriften zu verbessern und Ihren Arbeitsbereich frei von unnötigen Informationen zu halten, sodass Sie sich auf Ihr aktuelles Geschäft konzentrieren können. Siehe [Aktivieren der Archivierung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Asynchrone Bestellverarbeitung aktivieren

Die Schritte zum Aktivieren der asynchronen Ordnungsverarbeitung hängen vom Bereitstellungsmodus ab:

- Verwenden Sie für Adobe Commerce in der Cloud-Infrastruktur und lokale Sites im Produktionsmodus den folgenden Magento-CLI-Befehl, um die asynchrone Indizierung zu aktivieren:

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Aktivieren Sie bei lokalen Adobe Commerce-Sites im Standard- oder Produktionsmodus die asynchrone Indizierung, indem Sie die Konfiguration der Rastereinstellungen in der Admin Console aktualisieren.

  Siehe [Aktivieren geplanter Rasteraktualisierungen und -neuindizierungen](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Testen Sie immer Konfigurationsänderungen in der Staging-Umgebung, bevor Sie die Produktionsumgebung aktualisieren.

## Weitere Informationen

- [Best Practices für die Konfiguration](../../../performance/configuration.md)
- [Referenz zu allgemeinen und erweiterten Konfigurationspfaden](../../../configuration/reference/config-reference-general.md)
- [Auftragsverarbeitung mit hohem Durchsatz](../../../performance/high-throughput-order-processing.md)
