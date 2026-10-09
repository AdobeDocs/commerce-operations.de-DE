---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.58'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.58 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.58

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.58 verfügbaren Patches behoben wurden.

QPT v1.1.58 enthält die folgenden Patches:

1. **ACSD-48570**: Es wurde ein Problem behoben, bei dem die Seite zum Zurücksetzen des Kennworts nicht erreicht werden konnte, indem auf den Link zum Zurücksetzen des Kennworts [!UICONTROL Admin] geklickt wurde, wenn **Store-Code zu URLs hinzufügen** *aktiviert* war, was zuvor dazu führte, dass die Anmeldeseite oder eine 404-Seite angezeigt wurde.
1. **ACSD-62118**: Es wird ein Problem behoben, bei dem die `sales_order_tax_item`-Tabelle nicht vollständig aktualisiert wird, wenn [!DNL B2B] Bestellungen mit der Bestellmethode aufgegeben werden.
1. **ACSD-63067**: Es wird ein Problem behoben, bei dem alle Produktmengen falsch hervorgehoben sind und die *[!DNL Please specify the quantity of product(s).]* für alle Produkte in einem gruppierten Produkt angezeigt wird, wenn nur eine Menge falsch ist.
1. **ACSD-63090**: Es wird ein Problem behoben, bei dem Artikel aus dem Warenkorb entfernt werden, wenn ein Produkt gelöscht wird, nachdem es zum Warenkorb hinzugefügt wurde.
1. **ACSD-63182**: Es wird ein Problem behoben, bei dem beim Speichern eines doppelten Produktpakets mit **[!DNL MSI]** (*) ein Fehler*.
1. **ACSD-63283**: Es wird ein Problem behoben, bei dem das Bestellen von Artikeln aus der Geschenkregistrierung zu einer Ausnahme führt und bei dem Geschenkregistrierungs-Aktualisierungen Elemente enthalten, die nicht zur Registrierung gehören.
1. **ACSD-63299**: Es wird das Problem behoben, dass der Sonderpreis für ein konfigurierbares Produkt nicht in der Storefront angezeigt wird.
1. **ACSD-63325**: Es wird ein Problem behoben, bei dem beim Senden einer leeren [!DNL GraphQL]-Anfrage ein `Syntax Error: Unexpected <EOF>` auftritt.
1. **ACSD-63329**: Es wird das Problem behoben, dass die Standardwerte für Attribute mit **[!UICONTROL Date]** oder **[!UICONTROL Date and Time]** Eingabetypen beim Erstellen von Produkten über die [!DNL REST API] nicht festgelegt werden.
1. **ACSD-63572**: Es wird ein Problem behoben, bei dem die temporären Tabellen des `CatalogRule` Indexers nicht bereinigt werden, wenn der Indexerprozess beendet wird.
1. **ACSD-63578**: Es wird ein Problem behoben, durch das beim Klicken auf die Schaltfläche **[!UICONTROL Delete]** in **[!UICONTROL Add to Order by SKU]** im [!UICONTROL Admin] die [!DNL SKU] nicht entfernt wird.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
