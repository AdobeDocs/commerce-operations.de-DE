---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.48 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.48

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.48 verfügbaren Patches behoben wurden.

QPT v1.1.48 enthält die folgenden Patches:

1. **ACSD-5566**: Behebung des Problems, bei dem der *[!UICONTROL mergeCart mutation]* mit einem *internen Serverfehler* in der GraphQL-Antwort fehlschlägt, wenn der Quell- und ZielWarenkorb dieselben gebündelten Elemente enthält.
1. **ACSD-56546**: Behebung des Problems, bei dem konfigurierbare und gebündelte Produkte auf der Storefront als *[!UICONTROL Out of Stock]* angezeigt werden, wenn die *[!UICONTROL Display Out of Stock Product]*-Konfiguration deaktiviert ist.
1. **ACSD-56635**: Behebung des Problems, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn für den Import der Wert [!UICONTROL Account Sharing] auf *[!UICONTROL Global]* festgelegt ist.
1. **ACSD-56741**: Fehlerbehebung für die Fehlermeldung *Versuch, auf den Array-Versatz vom Typ null zuzugreifen* , die während `setup:upgrade` angezeigt wird, wenn die Datenbank einen benutzerdefinierten MySQL-Trigger enthält, der nicht mit dem Indexierungsmechanismus und [!DNL MView] verknüpft ist.
1. **ACSD-57315**: Behebung des Problems, bei dem eine neue Transaktion in [!DNL PayPal Payflow Pro] erstellt wird, sobald auf dem Bildschirm &quot;Transaktionen anzeigen&quot;in [!UICONTROL Admin] auf die Schaltfläche **[!UICONTROL Fetch]** geklickt wird.
1. **ACSD-57337**: Behebung des Problems, bei dem ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im Raster *[!UICONTROL Companies]* sehen kann.
1. **ACSD-57394**: Behebt eine falsche Produktsortierung durch mehrere Sortierungsfelder in GraphQL.
1. **ACSD-57565**: Behebung des Problems, bei dem das *[!UICONTROL Order]*-Dashboard falsche Bestellinformationen anzeigt, bis der Zeitraum aktualisiert wurde. Das Dashboard zeigt nun beim ersten Laden die richtigen Bestellstatistiken an.
1. **ACSD-57854**: Behebung des Problems, bei dem GraphQL-Produktanfragen deaktivierte Kategorien in den Kategorieaggregationen zurückgeben.
1. **ACSD-58008**: Behebung des Problems, bei dem beim Aktualisieren einer geplanten Aktualisierung die vorherige Version des gestaffelten Elements entfernt wird, wenn kein Enddatum angegeben ist.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
