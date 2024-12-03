---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.53 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.53

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.53 verfügbaren Patches behoben wurden.

QPT v1.1.53 umfasst die folgenden Patches:

1. **ACSD-48318**: Behebung des Problems, bei dem eine Verschachtelung der Umgebung nicht zulässig ist. Jetzt beginnt die Emulation während des `send()` -Aufrufs, sobald die Emulation während des `getInfoBlockHtml()` -Aufrufs beendet wird.
1. **ACSD-59930**: Verbessert die Leistung der Flüsse *[!UICONTROL Create]*, *[!UICONTROL Save]* und *[!UICONTROL Delete]* des Unternehmens.
1. **ACSD-60584**: Behebung des Problems, bei dem ein Zugriffstoken, das für den Benutzer auf einer Website erstellt wurde, berechtigt ist, auf Kundeninformationen auf anderen Websites zuzugreifen oder diese zu ändern.
1. **ACSD-60804**: Behebung des Problems, bei dem beim Bearbeiten eines Kunden, der mit einem gelöschten Unternehmen verknüpft ist, der Fehler *Aufruf an eine Mitgliederfunktion `getSuperUserId()` bei null* auftritt.
1. **ACSD-61133**: Behebung des Problems, bei dem der `sales_clean_quotes`-Cron Anführungszeichen aus nicht genehmigten Bestellungen löscht.
1. **ACSD-61528**: Behebung des Problems, bei dem beim Abrufen von Rollen aus dem [!UICONTROL Admin] mit GraphQL keine Ergebnisse zurückgegeben werden.
1. **ACSD-61553**: Behebung des Problems, bei dem *[!UICONTROL Cart Price Rule]* -Rabatte falsch berechnet werden, wenn mehrere Rabatte mit unterschiedlichen Prioritäten und *[!UICONTROL Maximum Qty Discount is Applied To]* auf das Produkt angewendet werden.
1. **ACSD-61667**: Verbessert die Lagerbestandsleistung für die Erstellung des Versands bei vielen Quellen mit dem *In-Store-Abruf*.
1. **ACSD-61969**: Behebung des Problems, bei dem der Benutzer einen Gutscheincode eingeben muss, der genau mit dem konfigurierten Gutscheincode übereinstimmt.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
