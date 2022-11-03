---
title: Best Practices bei der Kategoriekonfiguration
description: Lernen Sie Best Practices kennen, um die Site-Leistung zu maximieren, indem Sie die Anzahl der Kategorien im Katalog einschränken.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Best Practices für Kategoriekonfiguration

Konfigurieren Sie für optimale Leistung nicht mehr als die maximal empfohlene Anzahl von Kategorien für Adobe Commerce-Sites.

- Konfigurieren Sie für Adobe Commerce-Version 2.4.2 und höher maximal 6000 Kategorien.
- Konfigurieren Sie für die Adobe Commerce-Versionen 2.3.x und 2.4.0 bis 2.4.1-p1 maximal 3000 Kategorien.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Kategorien zu reduzieren:

- Verwalten einzigartiger Produktfunktionen über Attribute und benutzerdefinierte Optionen
- Inaktive Kategorien entfernen
- Optimieren der Katalogtiefe in der Navigation

## Mögliche Leistungseinbußen

Eine höhere als die empfohlene maximale Anzahl von Kategorien kann die Site-Leistung auf folgende Weise beeinflussen:

- Deutliche Steigerung der Reaktionszeit für nicht zwischengespeicherte Katalogseiten
- Lange Ausführung und Timeouts bei der Verwaltung von Kategorien über den Administrator
- Vergrößerung der entsprechenden Datenbanktabellen
- Größere Indextabellen erhöhen die Zeit, die zum Ausführen von Indizierungsvorgängen für die `[category/product relation index\]`
- Erhöhte Verarbeitungszeit zum Abschließen der Kategoriestruktur, des Menüabrufs und der Kategorieregelverwaltung

## Zusätzliche Informationen

- [Kategorienübersicht](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Navigationsübersicht](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Produktzuweisungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce über Cloud-Infrastruktur: Best Practices für die Store-Konfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
