---
title: Best Practices für Produktbeschränkungen
description: Erfahren Sie mehr über Best Practices zum Konfigurieren von Produkt Stock Keeping Units (SKUs), um die Site-Leistung zu maximieren.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e259f9b999566447469200c93db3bc4ba06434c0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Best Practices für die Produkt-SKU-Konfiguration

Um die Leistung zu maximieren, wird für effektive Bestandseinheiten (SKUs) eine maximale Anzahl von 242 Millionen empfohlen. Diese effektive Produkt-SKU-Obergrenze wird wie folgt berechnet:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Dabei gilt:

- N steht für die Anzahl der Artikel dieser Kategorie
- Kundengruppen enthalten freigegebene Kataloge, da sie eine zusätzliche Kundengruppe erstellen.

Wenn mehr als die maximale Anzahl effektiver SKUs vorhanden ist, wird der Abruf von Produktdaten verlangsamt und die Zeit zum Abschließen von Vorgängen oder Indizierungen im Admin-Bedienfeld erhöht.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Produkte (SKUs) zu reduzieren:

- Minimieren von Multiplikatoren—
   - Durch die Konsolidierung von Websites wird der Multiplikator reduziert. Wenn Sie 50.000 SKUs, zehn Websites und zehn Kundengruppen haben, beträgt die effektive Anzahl der SKUs 5 Millionen. Wenn fünf Kundengruppen entfernt werden, werden die effektiven SKUs auf 2,5 Millionen reduziert.
   - Verwenden Sie alternative Produktfunktionen für benutzerdefinierte Preise, um freigegebene Katalog- und Kundengruppen-Multiplikatoren zu ersetzen.
   - Sowohl Kundengruppen als auch freigegebene Kataloge fungieren als Multiplikatoren für die Anzahl der effektiven SKUs in einem Geschäft.
- Neustrukturierung des Katalogs—
   - Reduzieren Sie die Anzahl der den Kategorien zugewiesenen Produkte.
   - Verringern Sie die Anzahl der SKUs, indem Sie die Anzahl der Websites, Kundengruppen, freigegebenen Kataloge, die Anzahl der Produkte oder die Anzahl der konfigurierbaren Produktoptionen reduzieren.
- Stellen Sie mehr Produktvarianten bereit, indem Sie benutzerdefinierte Optionen verwenden, anstatt separate Produkte zu erstellen.
- Unter Berücksichtigung der Tatsache, dass eine effektive SKU eine Reihe potenzieller Preisveränderungen umfassen könnte, da die Preise je Geschäft oder Kundengruppe unterschiedlich angegeben werden können.
- Deaktivieren oder entfernen Sie nicht verwendete Systemkomponenten wie Module. (Siehe  [Module deinstallieren](../../../installation/tutorials/uninstall-modules.md).
- Verwalten Sie Produkte in einem externen Platform Management System (PMS).

## Zusätzliche Informationen

- [Produkt erstellen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Produktzuweisungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Arbeiten mit freigegebenen Katalogen](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Cloud-Infrastruktur: [Einrichten mehrerer Websites und Stores](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Vor Ort: [Mehrere Websites oder Stores](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce über Cloud-Infrastruktur: Best Practices für die Store-Konfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
