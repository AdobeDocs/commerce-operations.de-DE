---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.54 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.54

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.54 verfügbaren Patches behoben wurden.

QPT v1.1.54 umfasst die folgenden Patches:

1. **ACSD-60267**: Behebung des Problems, bei dem die FPT (Fixed Product Tax) ordnungsgemäß angewendet wird, wenn einfache Produkte mit FPT direkt zum Warenkorb hinzugefügt werden, aber bei der Auswahl dieser Produkte über konfigurierbare Produktoptionen fehlschlägt.
1. **ACSD-61103**: Behebung des Problems, bei dem die Fehleranzahl in der Tabelle `customer_entity` nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat.
1. **ACSD-61134**: Behebung des Problems, bei dem die Zahlungsmethode [!DNL Braintree Vault] im Checkout-Workflow automatisch deaktiviert wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert wird.
1. **ACSD-61199**: Behebung des Problems, bei dem die CMS-Registerkarte für die Seitenhierarchie beim Bearbeiten einer CMS-Seite mit einer vorhandenen Hierarchie keine ordnungsgemäße Baumstruktur anzeigt.
1. **ACSD-61200**: Behebung des Problems, bei dem bei den Berechnungen für *[!UICONTROL Total Amount]* und *[!UICONTROL Total Amount Actual]* im Umsatz die Werte *[!UICONTROL Discount Tax Compensation Amount]* und *[!UICONTROL Shipping Discount Tax Compensation Amount]* fehlen, was zu Diskrepanzen bei den Daten der Verkaufsaufträge führt.
1. **ACSD-61522**: Behebung des Problems, bei dem E-Mail-Adressen in die Felder *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* des Gastkunden eingegeben und ungültige E-Mails zur Bestellbestätigung gesendet werden können.
1. **ACSD-61756**: Verbessert die Leistung von `AdvancedSalesRule` Filtern.
1. **ACSD-61799**: Behebung des Problems, bei dem der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden.
1. **ACSD-61845**: Behebt den Fehler, der auftritt, wenn eine Anforderung nur mit der Überschrift *text/html* accept gesendet wird.
1. **ACSD-62056**: Behebung des Problems, bei dem das Hochladen von Bildern für ein konfigurierbares Produkt fehlschlägt, wenn MSI installiert ist.
1. **ACSD-62485**: Behebung des Problems, bei dem der `async.operations.all` -Verbraucher bei der Erstellung eines Unternehmens seine Arbeit beendet.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
