---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.54 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
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
# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.54

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.54 verfügbaren Patches behoben wurden.

QPT v1.1.54 enthält die folgenden Patches:

1. **ACSD-60267**: Es wird das Problem behoben, dass die feste Produktsteuer (FPT) korrekt angewendet wird, wenn einfache Produkte mit FPT direkt zum Warenkorb hinzugefügt werden, aber bei der Auswahl dieser Produkte über konfigurierbare Produktoptionen fehlschlägt.
1. **ACSD-61103**: Es wird ein Problem behoben, bei dem die Fehleranzahl in der `customer_entity`-Tabelle nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat.
1. **ACSD-61134**: Es wird ein Problem behoben, bei dem die [!DNL Braintree Vault] Zahlungsmethode im Checkout-Workflow automatisch deaktiviert wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem er das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert.
1. **ACSD-61199**: Es wird ein Problem behoben, bei dem die Registerkarte &quot;CMS-Seitenhierarchie“ beim Bearbeiten einer CMS-Seite mit einer bestehenden Hierarchie keine richtige Baumstruktur anzeigt.
1. **ACSD-61200**: Es wird ein Problem behoben, bei dem in den Berechnungen für *[!UICONTROL Total Amount]* und *[!UICONTROL Total Amount Actual]* im Verkauf die *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* fehlen, was zu Diskrepanzen in den Auftragsdaten führt.
1. **ACSD-61522**: Es wurde das Problem behoben, bei dem es möglich war, E-Mail-Adressen in die *[!UICONTROL First Name]*- und *[!UICONTROL Last Name]* des Gastkunden einzugeben und ungültige E-Mails zur Bestellbestätigung zu senden.
1. **ACSD-61756**: Verbessert die Leistung von `AdvancedSalesRule`.
1. **ACSD-61799**: Es wird ein Problem behoben, bei dem der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden.
1. **ACSD-61845**: Behebt den Fehler, der auftritt, wenn eine Anfrage nur mit der Accept *Kopfzeile „text/*&quot; gesendet wird.
1. **ACSD-62056**: Es wird das Problem behoben, dass das Hochladen von Bildern für ein konfigurierbares Produkt fehlschlägt, wenn MSI installiert ist.
1. **ACSD-62485**: Es wird das Problem behoben, dass `async.operations.all` Verbraucher nicht mehr funktioniert, wenn ein Unternehmen erstellt wird.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
