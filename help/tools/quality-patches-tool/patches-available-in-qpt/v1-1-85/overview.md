---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.85 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.85

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.85 verfügbaren Patches behoben wurden.

QPT v1.1.85 enthält die folgenden Patches:

1. **ACP2E-4929**: Es wird das Problem behoben, dass Attributbeschriftungen auf der **[!UICONTROL Compare Products]**-Seite Übersetzungen aus einer anderen Store-Ansicht anstelle der aktuellen Store-Ansicht anzeigen.
1. **ACP2E-5075**: Behebt das Problem, dass eine Regel mit einem festen Betrag im Warenkorb mit einer Kategoriebedingung fälschlicherweise einen Rabatt auf alle untergeordneten Elemente eines Dynamischer-Preis-Bundle-Produkts angewendet hat, wenn die Regel nur mit dem übergeordneten Bundle-Produkt übereinstimmt.
1. **ACP2E-5077**: Es wird das Problem behoben, dass gleichzeitige `customerCart` GraphQL-Abfragen oder `POST /V1/carts/mine` REST-Anfragen doppelte aktive Warenkörbe für Kunden erstellen, die noch keinen aktiven Warenkorb haben.
1. **ACP2E-5088**: Behebt das Problem, dass der beständige Warenkorb eines Kunden gelöscht wird, wenn seine Sitzung abläuft.
1. **ACP2E-3991**: Behebt das Problem, dass die Client-IP-Adresse nicht korrekt ermittelt wurde.
1. **ACP2E-5092**: Es wird ein Problem behoben, bei dem die Seite &quot;**[!UICONTROL Company Profile]**&quot; und die Seite „Admin-Kundenbearbeitung“ einen Fehler anzeigen, wenn einer Firmenadresse, die ohne eine Region gespeichert wurde, später eine Region zu ihrem Land hinzugefügt wurde.
1. **ACP2E-5124**: Behebt das Problem, dass die Schaltfläche **[!UICONTROL Import]** in den Validierungsergebnissen weiterhin verfügbar ist, wenn die Validierung fehlschlägt, wenn die **[!UICONTROL Validation Strategy]** auf **[!UICONTROL Stop on Error]** gesetzt ist.
1. **AC-17456**: Es wurde ein Problem behoben, bei dem die Bearbeitung des **[!UICONTROL Global]**-Bereichs auf der **[!UICONTROL Design Configuration]**-Seite im Admin-Bedienfeld einen *HTTP 500*-Fehler in PHP 8.4 und 8.5 zurückgab.
1. **ACP2E-5212**: Es wird das Problem behoben, dass **[!UICONTROL Quick Order]** Nicht-CSV-Dateien akzeptiert, die mit einer `.csv`-Erweiterung umbenannt wurden.
1. **ACP2E-5300**: Es wird das Problem behoben, dass Keywords nach mehreren durch Leerzeichen oder Kommas getrennten Ordnungsnummern im Admin Panel-**[!UICONTROL Orders]**-Raster keine übereinstimmenden Bestellungen zurückgeben.
1. **ACP2E-5354**: Es wird ein Problem behoben, durch das die Aktualisierung eines Kunden über die REST-API dazu führt, dass ein mit einem Unternehmenskonto verknüpfter Kunde mehrmals im Admin **[!UICONTROL Customers]**-Raster angezeigt wird.
1. **ACP2E-5208**: Es wird das Problem behoben, dass der **[!UICONTROL Requisition List]**-Abschnitt bei jeder Storefront-Seitennavigation neu geladen wird, selbst wenn keine Änderungen vorgenommen wurden.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
