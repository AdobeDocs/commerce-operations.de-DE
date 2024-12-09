---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.56 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 88cc3a9b2582998812af196f9e59b93015098c52
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.56

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.56 verfügbaren Patches behoben wurden.

QPT v1.1.56 enthält die folgenden Patches:

1. **ACSD-63244**: Behebt die Probleme, bei denen ein JavaScript-Fehler verhindert, dass [!DNL Google Maps] korrekt gerendert wird und viele *Uncaught TypeError (Nicht abgefangener TypeError) vorliegen._each ist keine Fehler der Funktion* in der Konsole im Bedienfeld [!UICONTROL Admin].
1. **ACSD-63242**: Behebung des Problems mit der Langsamkeit beim Import beim Hinzufügen von Katalogprodukten mit mehr als 10.000 Einträgen.
1. **ACSD-63062**: Behebung des Problems, bei dem falsche Rabattberechnungen für den Warenkorb auftreten, wenn mehrere überlappende Regeln angewendet werden.
1. **ACSD-62979**: Behebung des Problems, bei dem die Verwendung des falschen [!UICONTROL Store ID] in der GraphQL-Kopfzeile einen schwerwiegenden Speicherfehler verursacht.
1. **ACSD-62971**: Behebung des Problems, bei dem beim Importieren von Lagerquellen mit nicht numerischen Werten in der Spalte *[!UICONTROL Quantity]* der Wert *quantity* auf *0* eingestellt wird.
1. **ACSD-62872**: Behebt das Problem mit der eindeutigen Attributvalidierung, bei der Zeitplanaktualisierungen falsch validiert werden.
1. **ACSD-62755**: Behebung des Problems, bei dem für [!DNL TinyMCE] 7 die Schriftgröße und -schrift speziell in den Initialisierungseinstellungen des Editors hinzugefügt werden muss.
1. **ACSD-62670**: Behebung des Problems, bei dem der [!UICONTROL Products Ordered] -Berichtexport nach CSV und XML einen Fehler zurückgibt.
1. **ACSD-62577**: Behebung des Problems mit der langsamen Leistung von Storefront-Suchabfragen durch Optimierung von Abfrage- und Tabellenindizes.
1. **ACSD-62475**: Behebung des Problems, bei dem die [!UICONTROL Gift Card] -Produkte im Warenkorb falsch zusammengeführt wurden.
1. **ACSD-62428**: Behebung des Problems, bei dem `is_out_of_stock` im Katalogsuchindex auf einen falschen Wert gesetzt ist, wenn [!DNL SKU] nicht als durchsuchbares Attribut festgelegt ist.
1. **ACSD-62355**: Erhöht die Ladezeit der konfigurierbaren Produktebearbeitungsseite, wenn das konfigurierbare Produkt auf vielen Attributen mit vielen Werten basiert.
1. **ACSD-61805**: Behebung des Problems, bei dem Produkte nach der Aktualisierung des Status der Rückbestellung über [!DNL REST API] nicht auf Lager sind.
1. **ACSD-60811**: Behebung des Problems, bei dem das Aktualisieren des Bestellstatus mit einem benutzerdefinierten Wert oder Kommentar nur möglich ist, wenn der aktuelle Status entweder *[!UICONTROL Processing]* oder *[!UICONTROL Fraud]* lautet.
1. **ACSD-62952**: Behebung des Problems, bei dem das [!UICONTROL Gift Registry] -Datum in der Storefront ungenau angezeigt wird.
1. **ACSD-55339**: Behebung des Problems, bei dem ein Produkt [!DNL SKU], das mit *0* beginnt (null), die *0* entfernt, sodass das Anführungszeichen nicht aktualisiert wird.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
