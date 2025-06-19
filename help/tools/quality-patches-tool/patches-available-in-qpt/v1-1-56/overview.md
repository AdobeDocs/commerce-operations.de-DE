---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.56  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.56

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.56 verfügbaren Patches behoben wurden.

QPT v1.1.56 enthält die folgenden Patches:

1. **ACSD-63244**: Behebt die Probleme, bei denen ein JavaScript-Fehler verhindert, dass [!DNL Google Maps] korrekt gerendert werden, und bei denen es viele „Nicht erfasster *TypeError: this._each ist keine Funktion* Fehler in der Konsole im [!UICONTROL Admin].
1. **ACSD-63242**: Es wurde das Problem der verlangsamten Importe beim Hinzufügen von Katalogprodukten mit mehr als 10.000 Einträgen behoben.
1. **ACSD-63062**: Es wird das Problem behoben, dass bei Anwendung mehrerer überlappender Regeln zu falschen Berechnungen des Warenkorbabschlags kommt.
1. **ACSD-62979**: Es wird ein Problem behoben, bei dem die Verwendung der falschen [!UICONTROL Store ID] in der GraphQL-Kopfzeile einen schwerwiegenden Speicherfehler verursacht.
1. **ACSD-62971**: Es wird ein Problem behoben, bei dem der Import von Lagerquellen mit nicht numerischen Werten in der *[!UICONTROL Quantity]* Spalte dazu führt, dass *Menge* auf *0 eingestellt*.
1. **ACSD-62872**: Es wurde das Problem mit der Validierung eindeutiger Attribute behoben, bei dem Zeitplanaktualisierungen falsch validiert wurden.
1. **ACSD-62755**: Es wird ein Problem behoben, bei dem [!DNL TinyMCE] 7 erfordert, dass Schriftgröße und Schriftart in den Editor-Initialisierungseinstellungen speziell hinzugefügt werden.
1. **ACSD-62670**: Es wird das Problem behoben, bei dem der Export des [!UICONTROL Products Ordered]-Berichts in CSV und XML einen Fehler zurückgibt.
1. **ACSD-62577**: Behebt das Problem der langsamen Leistung von Storefront-Suchabfragen, indem sowohl Abfrage- als auch Tabellenindizes optimiert werden.
1. **ACSD-62475**: Behebt das Problem, dass die [!UICONTROL Gift Card] Produkte falsch im Warenkorb zusammengeführt werden.
1. **ACSD-62428**: Es wird ein Problem behoben, bei dem `is_out_of_stock` im Katalogsuchindex auf einen falschen Wert eingestellt ist, wenn die [!DNL SKU] nicht als durchsuchbares Attribut festgelegt ist.
1. **ACSD-62355**: Verbessert die Ladezeit der konfigurierbaren Produktbearbeitungsseite, wenn das konfigurierbare Produkt auf vielen Attributen mit vielen Werten basiert.
1. **ACSD-61805**: Es wird ein Problem behoben, bei dem Produkte in der Storefront nicht vorrätig sind, nachdem der Status der Rückstandsbestellung über [!DNL REST API] aktualisiert wurde.
1. **ACSD-60811**: Es wird ein Problem behoben, bei dem das Aktualisieren des Bestellstatus mit einem benutzerdefinierten Wert oder Kommentar nur möglich ist, wenn der aktuelle Status entweder *[!UICONTROL Processing]* oder *[!UICONTROL Fraud]* ist.
1. **ACSD-62952**: Es wird ein Problem behoben, bei dem das [!UICONTROL Gift Registry] falsch in der Storefront angezeigt wird.
1. **ACSD-55339**: Es wird ein Problem behoben, bei dem ein [!DNL SKU], das mit *0* (Null) beginnt, die *0* entfernt und so verhindert, dass das Angebot aktualisiert wird.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
