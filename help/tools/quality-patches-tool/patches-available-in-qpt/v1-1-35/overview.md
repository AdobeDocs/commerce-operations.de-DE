---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.35  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin
exl-id: 5ffbade4-c95e-4b59-9262-1b141614c753
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.35

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.35 verfügbaren Patches behoben wurden.

QPT v1.1.35 enthält die folgenden Patches:

1. **ACSD-51899**: Es wird das Problem behoben, bei dem die standardmäßige Versandadresse im Schritt Versand zur Kasse automatisch mit einer zuvor ausgewählten Abholadresse im Geschäft ausgefüllt wird.
1. **ACSD-52041**: Es wurde das Problem behoben, dass die Fehlermeldung *[ERROR] 5 Sekunden lang gerendert [!DNL Page Builder], ohne Sperren zu*. wird [!DNL Chrome] Browser angezeigt, wenn mit [!DNL Page Builder] bearbeitete Inhalte gespeichert werden.
1. **ACSD-52095**: Es wurde ein Problem behoben, bei dem der `manage_stock` in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt wurde.
1. **ACSD-51358**: Es wird ein Problem behoben, durch das das Entfernen einer geplanten Aktualisierung ohne Enddatum dazu führt, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.
1. Trigger **ACSD-48070**: Es wurde ein Problem behoben, bei dem das Bearbeiten eines geplanten Updates zu einer Ausnahme führte.
1. **ACSD-51890**: Es wird das Problem behoben, dass die [!UICONTROL Submit review]-Schaltfläche mehrmals ohne [!DNL Google] reCAPTCHA v3-Validierung angeklickt werden kann.
1. **ACSD-51984**: Es wird das Problem behoben, dass deaktivierte *Standardwerte und nicht standardmäßige Produktfeldwerte verwenden* für die zweite Website-, Store- und Store-Ansicht nicht gespeichert werden.
1. **ACSD-52398**: Behebt den Fehler *Die angeforderte Menge ist nicht verfügbar* der auftritt, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb in der Storefront zu aktualisieren.
1. **ACSD-52786**: Es wird das Problem behoben, bei dem eine Katalogregel-Bedingungs-SKU auf alle Produkte angewendet wird, die mit der angegebenen SKU beginnen.
1. **ACSD-52921**: Es wird ein Problem behoben, bei dem ein interner Fehler auftritt, wenn Warenkorbdetails von GraphQL angefordert werden und ein nicht vorrätiges konfigurierbares Produkt im Warenkorb vorhanden ist.
1. **ACSD-51683**: Es wird das Problem behoben, dass eine anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
1. **ACSD-52133**: Es wurde ein Problem behoben, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden konnte.
1. **ACSD-52202**: Es wird das Problem behoben, dass die verkaufbare Menge des Standardaktienbestands fälschlicherweise auf 0 geändert wird, wenn ein nicht standardmäßiger Bestand bei Auftragserfüllung auf 0 Menge geändert wird.
1. **ACSD-51265**: Behebt das Problem mit `catalog_product_price` Neuindizierungsleistung, wenn das System zu viele gebündelte Produkte enthält.
1. **ACSD-52831**: Es wurde das Problem behoben, dass Kunden bei aktiviertem [!DNL Google reCAPTCHA v3 Invisible] keine verhandelbaren Angebotsaufträge aufgeben können.
1. **ACSD-51845**: Es wird das Problem behoben, dass nachfolgende Produkte mit Stufenpreisen und unterschiedlichen Attributsätzen nicht über die asynchrone Massen-REST-API aktualisiert werden können.
1. **ACSD-52815**: Es wird das Problem behoben, dass die Eingabe für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für einen Standardbestand.
1. **ACSD-51149**: Es wird das Problem behoben, dass [!UICONTROL Scheduled ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] Indexer ungültig macht und dann Leerungen nach Cron zwischenspeichert.
1. **ACSD-50815**: Es wird das Problem behoben, dass die Dezimalmenge für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann.
1. **ACSD-52399**: Es wurde ein Problem behoben, bei dem die konfigurierbare Produktoption mit einer skalierbaren Menge von 0 *Auf Lager* auf der Produktseite angezeigt wurde.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
