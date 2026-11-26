---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.85 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-11-18T22:14:27.542Z'
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a1cc81ee1a8d0bbcbea322558da75a31e65d66a4
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%
---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.85

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.85 verfügbaren Patches behoben wurden.

QPT v1.1.85 enthält die folgenden Patches:

1. **[ACP2E-4929](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-4929.md)**: Es wird das Problem behoben, dass Attributbeschriftungen auf der Seite Produkte vergleichen Übersetzungen aus einer anderen Store-Ansicht anstelle der aktuellen Store-Ansicht anzeigen.
1. **ACP2E-5075**: Behebt das Problem, dass eine Regel mit einem festen Betrag im Warenkorb mit einer Kategoriebedingung fälschlicherweise einen Rabatt auf alle untergeordneten Elemente eines Dynamischer-Preis-Bundle-Produkts angewendet hat, wenn die Regel nur mit dem übergeordneten Bundle-Produkt übereinstimmt.
1. **ACP2E-5077**: Es wird das Problem behoben, dass gleichzeitige `customerCart` GraphQL-Abfragen oder `POST /V1/carts/mine` REST-Anfragen doppelte aktive Warenkörbe für Kunden erstellen, die noch keinen aktiven Warenkorb haben.
1. **ACP2E-5088**: Behebt das Problem, dass der beständige Warenkorb eines Kunden gelöscht wird, wenn seine Sitzung abläuft.
1. **[ACP2E-3991](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-3991.md)**: Behebt das Problem, dass die Client-IP-Adresse nicht korrekt ermittelt wurde.
1. **ACP2E-5092**: Es wird ein Problem behoben, bei dem die Seite &quot;**[!UICONTROL Company Profile]**&quot; und die Seite „Admin-Kundenbearbeitung“ einen Fehler anzeigen, wenn einer Firmenadresse, die ohne eine Region gespeichert wurde, später eine Region zu ihrem Land hinzugefügt wurde.
1. **ACP2E-5124**: Behebt das Problem, dass die Schaltfläche **[!UICONTROL Import]** in den Validierungsergebnissen weiterhin verfügbar ist, wenn die Validierung fehlschlägt, wenn die **[!UICONTROL Validation Strategy]** auf **[!UICONTROL Stop on Error]** gesetzt ist.
1. **AC-17456**: Es wurde ein Problem behoben, bei dem die Bearbeitung des **[!UICONTROL Global]**-Bereichs auf der **[!UICONTROL Design Configuration]**-Seite im Admin-Bedienfeld einen *HTTP 500*-Fehler in PHP 8.4 und 8.5 zurückgab.
1. **ACP2E-5212**: Es wird das Problem behoben, dass **[!UICONTROL Quick Order]** Nicht-CSV-Dateien akzeptiert, die mit einer `.csv`-Erweiterung umbenannt wurden.
1. **ACP2E-5300**: Es wird das Problem behoben, dass Keywords nach mehreren durch Leerzeichen oder Kommas getrennten Ordnungsnummern im Admin Panel-**[!UICONTROL Orders]**-Raster keine übereinstimmenden Bestellungen zurückgeben.
1. **ACP2E-5354**: Es wird ein Problem behoben, durch das die Aktualisierung eines Kunden über die REST-API dazu führt, dass ein mit einem Unternehmenskonto verknüpfter Kunde mehrmals im Admin **[!UICONTROL Customers]**-Raster angezeigt wird.
1. **ACP2E-5208**: Es wird das Problem behoben, dass der **[!UICONTROL Requisition List]**-Abschnitt bei jeder Storefront-Seitennavigation neu geladen wird, selbst wenn keine Änderungen vorgenommen wurden.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
