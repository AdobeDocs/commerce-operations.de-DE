---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.37 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
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
source-wordcount: '300'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.37

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.37 verfügbaren Patches behoben wurden.

QPT v1.1.37 enthält die folgenden Patches:

1. **ACSD-52613**: Es wird das Problem behoben, dass Caches und Indizes aktualisiert werden, selbst wenn von der REST-API keine Aktualisierungen an `Inventory_source` Elementen vorgenommen werden.
1. **ACSD-51884**: Es wurde ein Problem behoben, bei dem der Cache-Pfad für das Produktbild nach Ausführung des Befehls resize falsch angezeigt wurde.
1. **ACSD-53628**: Es wird ein Problem behoben, bei dem im CSV-Kundenauftragsbericht falsche Sonderzeichen angezeigt werden.
1. **ACSD-49843**: Es wurde ein Problem behoben, bei dem der Link zum Produktdownload nicht verfügbar war, nachdem der bestellte Artikel automatisch über die Online-Zahlungsmethode fakturiert wurde, wobei die Einstellung *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* aktiviert war.
1. **ACSD-53148**: Es wurde ein Problem behoben, bei dem zwei parallele Anfragen in GraphQL zum Hinzufügen desselben konfigurierbaren Produkts zum Warenkorb dazu führten, dass zwei separate Artikel im Warenkorb mit derselben Produkt-SKU vorhanden waren.
1. **ACSD-47054**: Es wird das Problem behoben, dass bei der Vorschau-Neuindizierung eine Neuindizierung für alle Stores ausgeführt wird, was zu Langsamkeit führt.
1. **ACSD-52606**: Es wird ein Problem behoben, bei dem die Fehlermeldung *Ihre Bestellung ist nicht abholbereit* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.
1. **ACSD-51574**: Es wird ein Problem behoben, bei dem das Bild im Frontend nicht aktualisiert wird, nachdem es durch ein anderes Bild mit demselben Namen ersetzt wurde.
1. **ACSD-53728**: Es wurde ein Problem behoben, bei dem die Fertigstellung des EAV-Indexers des Produkts länger dauert.
1. **ACSD-53979**: Behebt das JS-Problem, das auf der Homepage auftritt, wenn die Begrüßungsnachricht ein einfaches Anführungszeichen enthält.
1. **ACSD-52143**: Es wird das Problem behoben, dass benutzerdefinierte Optionen nach dem Produktimport entfernt werden.
1. **ACSD-53750**: Behebt den Fehler *Rohrbruch oder geschlossene Verbindung* während der Neuindizierung von Multithread-`catalog_product_price`.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
