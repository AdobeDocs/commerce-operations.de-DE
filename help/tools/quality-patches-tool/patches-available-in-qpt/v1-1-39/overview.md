---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.39 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
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
source-wordcount: '274'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.39

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.39 verfügbaren Patches behoben wurden.

QPT v1.1.39 enthält die folgenden Patches:

1. **ACSD-53704**: Es wird ein Problem behoben, bei dem der Belohnungspunktverlauf nach Ablauf der Belohnungspunkte falsch berechnet wird.
1. **ACSD-53583**: Verbessert die partielle Neuindizierungsleistung für *Kategorieprodukte* und *Produktkategorien* Indexer.
1. **ACSD-54026**: Behebt eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage für einen nicht autorisierten Benutzer.
1. **ACSD-54106**: Es wurde ein Problem behoben, bei dem die Sortierung nach Produktname für Zeichen mit türkischem Akzent falsch war.
1. **ACSD-52219**: Es wird das Problem behoben, dass in Admin-Rastern gespeicherte Filter nicht wie erwartet funktionieren, wenn häufig zwischen Lesezeichenansichten gewechselt wird.
1. **ACSD-54342**: Behebt eine falsche Fehlermeldung *Fehler in der Datenstruktur: Werte werden gemischt* wenn eine CSV-Datei ohne gültige Daten importiert wird.
1. **ACSD-54660**: Es wurde ein neues Eingabeattribut *sort* hinzugefügt, um Kundenaufträge in GraphQL nach `sort_field` und `sort_direction` zu sortieren.
1. **ACSD-54776**: Es wird das Problem behoben, dass nicht aktivierte *[!UICONTROL Use Default Value]*- und nicht standardmäßige Produktfeldwerte für die zweite Website-, Store- und Store-Ansicht nicht gespeichert werden.
1. **ACSD-53998**: Es wurde ein Problem behoben, bei dem eine auf einem **[!UICONTROL Customer Segment]** basierende **[!UICONTROL Dynamic Block]** nach der Abmeldung von einem Kundenkonto nicht korrekt funktionierte.
1. **ACSD-53204**: Fehlerbehebungen *Das Produkt kann nicht gespeichert werden.* Fehler bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des `rest/V1/products/<sku>/media`-Endpunkts.
1. **ACSD-47657**: Es wurde ein Zwischenspeicherungsmechanismus für AWS-Anmeldeinformationen hinzugefügt. Ein Anmeldedaten-Anbieter verwendet jetzt den Magento-Cache, um die von AWS für die EC2-Konfiguration abgerufenen Anmeldedaten zwischenzuspeichern.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
