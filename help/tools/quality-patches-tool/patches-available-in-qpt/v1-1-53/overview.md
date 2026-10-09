---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.53 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
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
source-wordcount: '243'
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
