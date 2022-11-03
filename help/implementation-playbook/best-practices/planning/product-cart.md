---
title: Best Practices für den Warenkorb
description: Erfahren Sie, wie Sie die Leistung von Adobe Commerce optimieren können, indem Sie die Anzahl der Produkte in einem Warenkorb begrenzen.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Best Practices für die Verwaltung von Warenkorb

Um eine optimale Leistung zu erzielen, sollten Sie die folgenden Richtlinien verwenden, um die Einschränkungen des Warenkorbs für Adobe Commerce und Magento Open Source zu verwalten:

- Für die Versionen 2.3.x - 2.4.2 dürfen maximal 100 Produkte in einem Warenkorb enthalten sein.
- In den Versionen 2.4.3 und höher wurde durch die Verbesserung der Funktionen für Verkaufsregeln der Warenkorb auf maximal 750 erhöht.


Für die Versionen 2.3.x - 2.4.2 lautet die erwartete Leistung basierend auf den Beschränkungen für Warenkorbartikel:

- Bis **100** Produkte in einem Warenkorb - das Produkt funktioniert, indem es Leistungsziele für die Reaktionszeit erfüllt.
- Bis **300** Produkte in einem Warenkorb - das Produkt funktioniert, aber die Reaktionszeit erhöht sich über den Zielwerten.
- Oben **500** Produkte in einem Warenkorb - der Warenkorb und die Checkout-Flüsse funktionieren nicht garantiert

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Anzahl der Artikel im Warenkorb reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Artikel im Warenkorb zu verwalten

- Aufteilen von Bestellungen in mehrere kleinere Bestellungen mit einer kleineren Anzahl von Zeilen mithilfe der [!UICONTROL Add Item by SKU] Funktion.
- Fügen Sie nur die benutzerdefinierte Logik und die Anpassung des Warenkorbs hinzu, die zum Laden einer Liste von Elementen erforderlich sind.

## Mögliche Leistungseinbußen

Wenn Sie mehr als die empfohlene maximale Anzahl von Produkten im Warenkorb haben, kann sich dies auf die Site-Leistung wie folgt auswirken:

- Erhöhte Reaktionszeit für Datenabruffunktionen, Validierung von Warenkorbelementen, Überprüfung der Anwendung von Preisregeln sowie Steuer- und Gesamtberechnungen.
- Erhöhte Reaktionszeit für Minicart-Rendering, einschließlich Rendering von Warenkorbansichten, Checkout-Fluss und Ausführung.
- Erhöhte Ladezeit für alle Seiten der Site, auf denen das Minicart vorhanden ist.

## Zusätzliche Informationen

- [Produktoptionen konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Warenkorb verwalten](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
