---
title: "Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.39"
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.39 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.39

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.39 verfügbaren Patches behoben wurden.

QPT v1.1.39 enthält die folgenden Patches:

1. **ACSD-53704**: Behebung des Problems, bei dem der Verlauf des Saldos von Bonuspunkten nach Ablauf der Bonuspunkte falsch berechnet wird.
1. **ACSD-53583**: Verbessert die partielle Neuindizierungsleistung für Indexer der Kategorien *Produkte der Kategorie* und *Produktkategorien*.
1. **ACSD-54026**: Behebt eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage für einen nicht autorisierten Benutzer.
1. **ACSD-54106**: Behebung des Problems, bei dem die Sortierung von Kategorieprodukten nach Namen für türkische Akzentzeichen falsch ist.
1. **ACSD-52219**: Behebung des Problems, bei dem gespeicherte Filter mit Admin-Rastern nicht wie erwartet funktionieren, wenn häufig zwischen Lesezeichenansichten gewechselt wird.
1. **ACSD-54342**: Behebt eine falsche Fehlermeldung *Fehler in der Datenstruktur: Werte werden gemischt*, wenn eine CSV-Datei ohne gültige Daten importiert wird.
1. **ACSD-54660**: Es wurde das neue Eingabedatum *sort* hinzugefügt, um Kundenaufträge in GraphQL nach `sort_field` und `sort_direction` zu sortieren.
1. **ACSD-54776**: Behebung des Problems, bei dem nicht aktivierte *[!UICONTROL Use Default Value]*- und nicht standardmäßige Produktfeldwerte nicht für die zweite Website-, Store- und Store-Ansicht gespeichert werden.
1. **ACSD-53998**: Behebung des Problems, bei dem ein auf einem **[!UICONTROL Customer Segment]** basierendes **[!UICONTROL Dynamic Block]** nach dem Abmelden von einem Kundenkonto nicht richtig funktioniert.
1. **ACSD-53204**: Fehlerbehebungen *Das Produkt kann nicht gespeichert werden.Fehler* bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des Endpunkts `rest/V1/products/<sku>/media`.
1. **ACSD-47657**: Es wurde ein Caching-Mechanismus für AWS-Anmeldeinformationen hinzugefügt. Ein Berechtigungsanbieter verwendet jetzt den Magento-Cache, um von AWS für die EC2-Konfiguration abgerufene Anmeldeinformationen zwischenzuspeichern.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
