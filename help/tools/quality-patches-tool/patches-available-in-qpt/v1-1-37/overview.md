---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.37 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.37

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.37 verfügbaren Patches behoben wurden.

QPT v1.1.37 enthält die folgenden Patches:

1. **ACSD-52613**: Behebung des Problems, bei dem Cache und Indizes aktualisiert werden, selbst wenn keine Aktualisierungen an `Inventory_source` -Elementen durch die Rest-API vorgenommen werden.
1. **ACSD-51884**: Behebung des Problems, bei dem der Pfad des Produktbild-Cache nach Ausführung des Größenbefehls fehlerhaft wird.
1. **ACSD-53628**: Behebung des Problems, bei dem der CSV-Verkaufsauftragsbericht falsche Sonderzeichen anzeigt.
1. **ACSD-49843**: Behebung des Problems, bei dem der Link beim Herunterladen des Produkts nicht verfügbar ist, nachdem das bestellte Element automatisch von der Online-Zahlungsmethode in Rechnung gestellt und die Einstellung *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* aktiviert wurde.
1. **ACSD-53148**: Behebung des Problems, bei dem zwei parallele Anfragen in GraphQL zum Hinzufügen desselben konfigurierbaren Produkts zum Warenkorb zu zwei separaten Artikeln mit derselben Produkt-SKU im Warenkorb führten.
1. **ACSD-47054**: Behebung des Problems, bei dem die Neuindizierung der Vorschau für alle Stores ausgeführt wird, was zu Langsamkeit führt.
1. **ACSD-52606**: Behebung des Problems, bei dem die Fehlermeldung *Ihre Bestellung ist nicht bereit für die Erfassung* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.
1. **ACSD-51574**: Behebung des Problems, bei dem das Bild nicht auf der Vorderseite aktualisiert wird, nachdem es durch ein anderes Bild mit demselben Namen ersetzt wurde.
1. **ACSD-53728**: Behebung des Problems, bei dem der Produkt-EAV-Indexer länger dauert.
1. **ACSD-53979**: Behebt das JS-Problem, das auf der Homepage auftritt, wenn die Willkommensnachricht ein einfaches Anführungszeichen enthält.
1. **ACSD-52143**: Behebung des Problems, bei dem benutzerdefinierte Optionen nach dem Produktimport entfernt werden.
1. **ACSD-53750**: Behebt den Fehler *Beschädigte Leitung oder geschlossene Verbindung* bei der Neuindizierung mehrerer Threads `catalog_product_price`.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
