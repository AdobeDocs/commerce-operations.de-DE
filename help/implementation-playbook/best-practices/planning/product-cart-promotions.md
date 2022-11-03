---
title: Best Practices zum Konfigurieren von Promotions
description: Erfahren Sie Best Practices zum Konfigurieren von Verkaufsregeln und Couponcodes zur Optimierung der Commerce-Store-Leistung.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Best Practices zum Konfigurieren von Promotions

Um eine optimale Leistung zu erzielen, befolgen Sie diese Best Practices, um Verkäufe und Promotions für Artikel in einem Warenkorb zu konfigurieren:

- **Verkaufsregeln (Regeln für Warenkorbpreise)**-Konfigurieren Sie nicht mehr als 1000 Warenkorbpreisregeln für alle Websites.
   - Nicht verwendete Regeln verwalten und entfernen
   - Fügen Sie strenge Regelbedingungen (wie Attribut- oder Kategoriefilter) hinzu, um eine optimale Übereinstimmung zu erzielen.
- **Coupons**—
   - Stellen Sie sicher, dass die Gesamtzahl der Gutscheine in der Datenbank unter 250.000 liegt.
   - Entfernen Sie nicht verwendete und abgelaufene Gutscheine.
   - Generieren Sie nur die Anzahl der Coupons, die zur Erfüllung der Kampagnenanforderungen erforderlich sind.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Mögliche Leistungseinbußen

Wenn Sie mehr als die empfohlene maximale Anzahl von Regeln oder Gutscheinen für den Warenkorbpreis haben, kann sich dies wie folgt auf die Site-Leistung auswirken:

- Die Reaktionszeit beim Hinzufügen von Produkten zum Warenkorb wurde verlängert.
- Die Zeit zum Laden und Rendern des Minicarts wurde verlängert.
- Die Zeit zum Rendern der Warenkorbseite wurde verlängert.
- Erhöhte Zeit zum Rendern der **Gesamt** auf der Checkout-Seite.
- Das Anwenden von Coupons kann mehr als 2 Sekunden dauern.

## Zusätzliche Informationen

- [Erläuterungen zu Marketing-Kampagnen und -Promotions](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Warenkorbpreisregeln](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutorial: Erstellen einer Preisregel für den Warenkorb](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Couponcodes](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce über Cloud-Infrastruktur: Best Practices für die Store-Konfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
