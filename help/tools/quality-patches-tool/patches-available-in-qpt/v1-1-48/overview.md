---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.48  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '294'
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
