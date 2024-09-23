---
title: "Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.35"
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.35 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.35

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.35 verfügbaren Patches behoben wurden.

QPT v1.1.35 enthält die folgenden Patches:

1. **ACSD-51899**: Behebung des Problems, bei dem die standardmäßige Versandadresse im Schritt zum Checkout-Versand automatisch mit einer zuvor ausgewählten In-Store-Abholadresse gefüllt wird.
1. **ACSD-52041**: Behebung des Problems, bei dem die Fehlermeldung *[ERROR] [!DNL Page Builder] 5 Sekunden lang gerendert wurde, ohne Sperren zu löschen*. wird beim Speichern von mit [!DNL Page Builder] bearbeitetem Inhalt im Browser [!DNL Chrome] angezeigt.
1. **ACSD-52095**: Behebung des Problems, bei dem der `manage_stock` -Wert in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt wurde.
1. **ACSD-51358**: Behebung des Problems, bei dem das Entfernen einer geplanten Aktualisierung ohne Enddatum dazu führt, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.
1. **ACSD-48070**: Behebung des Problems, bei dem beim Bearbeiten einer geplanten Aktualisierung eine Ausnahme Trigger wurde.
1. **ACSD-51890**: Behebung des Problems, bei dem die Schaltfläche [!UICONTROL Submit review] mehrmals ohne Überprüfung von [!DNL Google] reCAPTCHA v3 angeklickt werden kann.
1. **ACSD-51984**: Behebung des Problems, bei dem die Option *Standardwert verwenden und nicht standardmäßige Produktfeldwerte* nicht für die zweite Website-, Store- und Store-Ansicht gespeichert werden.
1. **ACSD-52398**: Behebt den Fehler *Die angeforderte Menge ist nicht verfügbar* , der auftritt, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren.
1. **ACSD-52786**: Behebung des Problems, bei dem eine SKU für Katalogregeln auf alle Produkte angewendet wird, die mit der angegebenen SKU beginnen.
1. **ACSD-52921**: Behebung des Problems, bei dem ein interner Fehler auftritt, wenn Warenkorbdetails von GraphQL angefordert werden, wenn ein nicht vorrätig konfigurierbares Produkt im Warenkorb vorhanden ist.
1. **ACSD-51683**: Behebung des Problems, bei dem eine anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
1. **ACSD-52133**: Behebung des Problems, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
1. **ACSD-52202**: Behebung des Problems, bei dem sich die verkaufbare Menge des Standardbestands fälschlicherweise auf 0 ändert, wenn ein nicht standardmäßiges Lager bei Bestellerfüllung auf 0 qty geändert wird.
1. **ACSD-51265**: Behebt das Problem mit der Neuindizierungsleistung von `catalog_product_price`, wenn zu viele gebündelte Produkte im System vorhanden sind.
1. **ACSD-52831**: Behebung des Problems, bei dem Kunden bei aktiviertem [!DNL Google reCAPTCHA v3 Invisible] keine umlauffähigen Anführungszeichenaufträge platzieren können.
1. **ACSD-51845**: Behebung des Problems, bei dem nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen nicht über die asynchrone Massen-REST-API aktualisiert werden können.
1. **ACSD-52815**: Behebung des Problems, bei dem die Eingabe für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu sechs Stellen unterstützt, im Gegensatz zu 8 für ein Standardbestand.
1. **ACSD-51149**: Behebt das Problem, bei dem [!UICONTROL Scheduled ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] Indexer invalidiert und dann durch Cron geleert wird.
1. **ACSD-50815**: Behebung des Problems, bei dem die Dezimalzahl für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann.
1. **ACSD-52399**: Behebung des Problems, bei dem die konfigurierbare Produktoption mit einer verkäuflichen Menge von 0 *Auf Lager* auf der Produktseite angezeigt wird.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
