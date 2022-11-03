---
title: Best Practices für Produktbeschränkungen
description: Erfahren Sie mehr über Best Practices zum Konfigurieren von Produkt Stock Keeping Units (SKUs), um die Site-Leistung zu maximieren.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Best Practices für die Produkt-SKU-Konfiguration

Um die Leistung zu maximieren, wird für effektive Bestandseinheiten (SKUs) der empfohlene Höchstwert von 10 Millionen empfohlen. Dieser Produkthöchstwert wird wie folgt berechnet:

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

Wenn mehr als die maximale Anzahl effektiver SKUs vorhanden ist, wird der Abruf von Produktdaten verlangsamt und die Zeit zum Ausführen von Admin-Vorgängen erhöht.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Produkte (SKUs) zu reduzieren:

- Minimieren von Multiplikatoren—
   - Durch das Verschieben von Geschäften oder Websites wird der Multiplikator reduziert. Wenn Sie 50.000 SKUs, zehn Websites und zehn Kundengruppen haben, beträgt die effektive Anzahl der SKUs 5 Millionen. Wenn fünf Kundengruppen entfernt werden, werden die effektiven SKUs auf 2,5 Millionen reduziert.
   - Verwenden Sie alternative Produktfunktionen für benutzerdefinierte Preise, um freigegebene Katalog- und Kundengruppen-Multiplikatoren zu ersetzen.
- Neustrukturierung des Katalogs—
   - Reduzieren Sie die Anzahl der den Kategorien zugewiesenen Produkte.
   - Verringern Sie die Anzahl der SKUs, indem Sie die Anzahl der Stores, Websites, Kundengruppen oder Produkte verringern.
- Stellen Sie mehr Produktvarianten bereit, indem Sie benutzerdefinierte Optionen verwenden, anstatt separate Produkte zu erstellen.
- Deaktivieren oder entfernen Sie nicht verwendete Systemkomponenten wie Module. (Siehe  [Module deinstallieren](../../../installation/tutorials/uninstall-modules.md).
- Verwalten Sie Produkte in einem externen Platform Management System (PMS).

## Zusätzliche Informationen

- [Produkt erstellen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Produktzuweisungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- Cloud-Infrastruktur: [Einrichten mehrerer Websites und Stores](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Vor Ort: [Mehrere Websites oder Stores](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce über Cloud-Infrastruktur: Best Practices für die Store-Konfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
