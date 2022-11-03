---
title: Best Practices für die Konfiguration von Produktoptionen
description: Optimieren Sie die Adobe Commerce-Leistung, indem Sie die Anzahl der Produktoptionen einschränken.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Best Practices für Produktoptionen

Konfigurieren Sie für optimale Leistung maximal 100 Produktoptionen pro Produkt.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Produktoptionen reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Produktoptionen zu reduzieren, um eine optimale Site-Leistung zu erzielen:

- Konfigurieren Sie komplexe Produkte und benutzerdefinierte Optionen als Quelle für Produktvarianten.
- Verwenden Sie anstelle der Erstellung globaler Produktvorlagen und Optionscontainer, die für alle Produkte gelten, Attributsätze, um spezifische Produktvorlagen mit Zielattributen und Optionen zu erstellen.
- Verwalten Sie Produktinformationen über ein externes Produktverwaltungssystem (PMS).

## Potenzielle Auswirkung auf die Leistung

Durch die Konfiguration vieler Produktoptionen erhöht sich die Datenmenge, die für jedes Produkt bei allen Lese- und Schreibvorgängen abgerufen wird. Dies führt zu Folgendem:

- Erhöhter SQL-Abfrageverkehr und schwerer `JOIN` -Vorgänge erhöhen den Datenbankdurchsatz.
- Erhöhte Größe für Adobe Commerce-Indizes und den Volltextsuchindex.

Die oben aufgeführten Steigerungen können sich auf die Site-Leistung wie folgt auswirken:

- Längere Reaktionszeiten für die meisten Storefront-Szenarien im Zusammenhang mit Produkten, die viele Optionen in Attributen enthalten.
- Deutliche Zeiteinsparungen beim Ausführen von Produktverwaltungsvorgängen in Admin, die zu Timeouts führen können, insbesondere bei Szenarien, die sich auf die Attributliste und den Abruf von Baumstrukturen einschließlich der Verwaltung von Promotion-Regeln beziehen.
- Kann Massenaktionen blockieren, die asynchrone Massenvorgänge wie Import und Export abschließen und benutzerdefinierte Preise mehreren Produkten in einem freigegebenen Katalog zuweisen.

## Zusätzliche Informationen

- [Produkt erstellen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Best Practices für die Produktattributkonfiguration](product-attributes-and-options.md)
- [Protokoll zu Massenaktionen](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API für Massenaktionen im Inventar](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Schulung: Verwalten von Katalogen und Produkten mit Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

