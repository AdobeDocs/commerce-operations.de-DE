---
title: Best Practices für die Paginierung von Produktauflistungen
description: Erfahren Sie, wie Sie die Leistung von Adobe Commerce optimieren können, indem Sie die Anzahl der Produkte verwalten, die auf jeder Seite des Storefront-Katalogs angezeigt werden.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Best Practices für die Paginierung von Produktauflistungen

Um die beste Leistung zu erzielen, zeigen Sie maximal 48 Produkte pro Seite an.

Sie können Adobe Commerce so konfigurieren, dass Käufer alle Kategorieprodukte auf einer Seite anzeigen können. Wenn die Anzahl der Kategorieprodukte deutlich über 48 Produkte liegt, aktualisieren Sie die Katalogkonfiguration für die Steuerelemente für die Storefront-Paginierung.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Aktualisieren der Produktlistenkonfiguration

Wenn Sie mehr als 48 Produkte in einer Kategorie haben, aktualisieren Sie die Storefront-Katalogkonfiguration, um die Option **Alle Produkte pro Seite zulassen**.

Nachdem Sie diese Option deaktiviert haben, verwendet Adobe Commerce die Steuerelemente für die Storefront-Paginierung, um die Anzahl der Produkte zu verwalten, die in Storefront-Komponenten angezeigt werden. Anweisungen finden Sie unter [Paginierungssteuerelemente konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Zusätzliche Informationen

- [Produktlisten konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)