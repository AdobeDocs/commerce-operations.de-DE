---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.53  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.53

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.53 verfügbaren Patches behoben wurden.

QPT v1.1.53 enthält die folgenden Patches:

1. **ACSD-48318**: Es wurde das Problem behoben, dass die Verschachtelung der Umgebungsemulation nicht zulässig ist. Die Emulation beginnt nun während des `send()`-Aufrufs, sobald die Emulation während des `getInfoBlockHtml()`-Aufrufs beendet wird.
1. **ACSD-59930**: Verbessert die Leistung der *[!UICONTROL Create]*-, *[!UICONTROL Save]*- und *[!UICONTROL Delete]*.
1. **ACSD-60584**: Es wird das Problem behoben, dass ein für den Benutzer auf einer Website erstelltes Zugriffstoken auf Kundeninformationen auf anderen Websites zugreifen oder diese ändern darf.
1. **ACSD-60804**: Es wird ein Problem behoben, bei dem das Bearbeiten eines Kunden, der mit einer gelöschten Firma verknüpft ist, den Fehler *Aufruf einer Memberfunktion `getSuperUserId()` auf null* verursacht.
1. **ACSD-61133**: Es wurde ein Problem behoben, bei dem `sales_clean_quotes` Cron Angebote aus nicht genehmigten Bestellungen löscht.
1. **ACSD-61528**: Es wird das Problem behoben, dass beim Abrufen von Rollen aus der [!UICONTROL Admin] mithilfe von GraphQL keine Ergebnisse zurückgegeben werden.
1. **ACSD-61553**: Es wird ein Problem behoben, bei dem *[!UICONTROL Cart Price Rule]* Rabatte falsch berechnet werden, wenn mehrere Rabatte mit unterschiedlichen Prioritäten und *[!UICONTROL Maximum Qty Discount is Applied To]* auf das Produkt angewendet werden.
1. **ACSD-61667**: Verbessert die Inventarleistung für die Versanderstellung bei vielen Quellen mit *In-Store-Abholung*.
1. **ACSD-61969**: Es wird ein Problem behoben, bei dem Benutzende einen Gutscheincode eingeben müssen, bei dem die Groß-/Kleinschreibung beachtet wird und der dem konfigurierten Gutscheincode genau entspricht.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
