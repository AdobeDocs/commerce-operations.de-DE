---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.48 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
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
source-wordcount: '296'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.48

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.48 verfügbaren Patches behoben wurden.

QPT v1.1.48 enthält die folgenden Patches:

1. **ACSD-55566**: Es wird ein Problem behoben, bei dem der *[!UICONTROL mergeCart mutation]* mit einem &quot;*Server-Fehler“* der GraphQL-Antwort fehlschlägt, wenn Quell- und Zielkarten dieselben gebündelten Elemente zusammenführen.
1. **ACSD-56546**: Es wird das Problem behoben, dass konfigurierbare und gebündelte Produkte als *[!UICONTROL Out of Stock]* in der Storefront angezeigt werden, wenn die *[!UICONTROL Display Out of Stock Product]* deaktiviert ist.
1. **ACSD-56635**: Es wird ein Problem behoben, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import verwendet wird und [!UICONTROL Account Sharing] auf *[!UICONTROL Global]* gesetzt ist.
1. **ACSD-56741**: Behebt die Fehlermeldung *Zugriff auf Array-Offset für Wert vom Typ null* die während der `setup:upgrade` angezeigt wird, wenn die Datenbank einen benutzerdefinierten MySQL-Trigger enthält, der nicht mit dem Indexierungsmechanismus und der [!DNL MView] in Verbindung steht.
1. **ACSD-57315**: Es wird kein Fehler mehr behoben, durch den bei jedem Klicken auf die Schaltfläche **[!UICONTROL Fetch]** im Bildschirm Transaktion anzeigen im [!UICONTROL Admin] eine neue Transaktion in [!DNL PayPal Payflow Pro] erstellt wird.
1. **ACSD-57337**: Es wird das Problem behoben, dass ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im *[!UICONTROL Companies]* sehen kann.
1. **ACSD-57394**: Korrigiert eine falsche Produktsortierung nach mehreren Sortierfeldern in GraphQL.
1. **ACSD-57565**: Es wird ein Problem behoben, bei dem im *[!UICONTROL Order]*-Dashboard falsche Bestellinformationen angezeigt werden, bis der Zeitraum aktualisiert wird. Das Dashboard zeigt jetzt beim ersten Laden die richtigen Bestellstatistiken an.
1. **ACSD-57854**: Es wird das Problem behoben, bei dem GraphQL-Anfragen für Produkte deaktivierte Kategorien in den Kategorieaggregationen zurückgeben.
1. **ACSD-58008**: Es wird ein Problem behoben, bei dem durch die Aktualisierung einer geplanten Aktualisierung die vorherige Version des Staging-Elements entfernt wird, wenn kein Enddatum angegeben ist.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
