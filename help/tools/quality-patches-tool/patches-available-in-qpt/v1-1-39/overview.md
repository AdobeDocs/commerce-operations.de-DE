---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.39  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '270'
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
1. **ACSD-53998**: Es wurde ein Problem behoben, bei dem eine auf einem **[!UICONTROL Dynamic Block]** basierende **[!UICONTROL Customer Segment]** nach der Abmeldung von einem Kundenkonto nicht korrekt funktionierte.
1. **ACSD-53204**: Fehlerbehebungen *Das Produkt kann nicht gespeichert werden.* bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des `rest/V1/products/<sku>/media`-Endpunkts.
1. **ACSD-47657**: Es wurde ein Zwischenspeicherungsmechanismus für AWS-Anmeldeinformationen hinzugefügt. Ein Anmeldedaten-Anbieter verwendet jetzt den Magento-Cache, um die von AWS für die EC2-Konfiguration abgerufenen Anmeldedaten zwischenzuspeichern.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
