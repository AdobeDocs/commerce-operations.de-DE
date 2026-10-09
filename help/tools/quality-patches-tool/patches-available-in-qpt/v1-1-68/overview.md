---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.68'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.68 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 74094036-cb1b-419f-b287-ca24d351a448
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
source-wordcount: '278'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.68

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.68 verfügbaren Patches behoben wurden.

QPT v1.1.68 enthält die folgenden Patches:

1. **ACSD-58131** Die alte Mediensammlung kann Bilder aufgrund einer 0-Byte-Bilddatei nicht laden.
1. **ACSD-62146**: Die ausgewählte Rechnungsadresse verschwindet auf der Kaufbestätigungsseite, wenn die Adresssuche aktiviert ist und „Limit für Kundenadressen“ auf 1 gesetzt ist.
1. **ACSD-62415**: Das Adobe Commerce-Backend lädt Kategorien sehr langsam.
1. **ACSD-65938**: E-Mails zu Geschenkkarten wurden auch dann gesendet, wenn die Erstellung der Rechnung fehlgeschlagen war.
1. **ACSD-66072**: Verwandte Produkte werden aufgrund eines internen Server-Fehlers bei der [!UICONTROL Related Products Rule] nicht über GraphQL auf der Produktdetailseite zurückgegeben.
1. **ACSD-66082**: Das Musterbild eines Produkts kann nicht durch einen Produktimport aktualisiert werden.
1. **ACSD-66179**: Eine Stornierung einer Rechnung mit dem Zahlungstyp „Nicht erfasst“ führt zu einer 404-Fehlerseite.
1. **ACSD-66233**: Admin-Benutzer konnten keine Produkte zu Kategorien hinzufügen, da [!UICONTROL Add Product] Popup nicht geladen wurde.
1. **ACSD-66506**: Backend-Fehler tritt nach dem Löschen und Neuzuweisen von Shared Catalog-Produkten auf.
1. **ACSD-66865**: Durch Speichern eines **[!UICONTROL Catalog Price Rule]** werden Indexer ungültig gemacht. Dies bietet eine Alternative zur Neuindizierung nur betroffener Produkte.
1. **ACSD-66889**: Fehler bei der Neuindizierung des Bestands in CLI.
1. **ACSD-66963**: `estimateTotals` Mutation gibt *null* für Rabatte zurück, wenn ein Rabattcode auf einen Warenkorb mit virtuellen Produkten angewendet wird.
1. **ACSD-66965**: Die Option „Drucken“ auf der Seite „Anforderungsliste“ verursacht einen Fehler.
1. **ACSD-66965**: **[!UICONTROL Print]** Option auf **[!UICONTROL Requisition List]** Seite verursacht einen Fehler.
1. **ACSD-67039**: Kundendatensätze wurden aufgrund der Validierung des `rp_token` Systemattributs nicht gespeichert.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
