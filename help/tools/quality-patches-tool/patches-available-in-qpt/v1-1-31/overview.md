---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.31 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.31

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.31 verfügbaren Patches behoben wurden.

QPT v1.1.31 umfasst die folgenden Patches:

1. **ACSD-50817**: Optimiert die Ausführung des Cron-Auftrags `sales_clean_quotes`, indem ein zusammengesetzter Index für die Spalten `store_id` und `updated_at` in der Anführungszeichentabelle hinzugefügt wird.
1. **ACSD-50345**: Behebung des Problems, bei dem: [!DNL Google reCAPTCHA v2] nach Übermittlung einer fehlgeschlagenen Zahlung nicht neu geladen wird, [!DNL Google reCAPTCHA v3 Invisible] nicht am Checkout funktioniert und die Bestellung nicht platziert werden kann und das [!UICONTROL PlaceOrder] -Ereignis nicht ausgelöst wurde.
1. **ACSD-49392**: Behebung des Problems, bei dem der Auftragsstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt zu &quot;geschlossen&quot;geändert wurde.
1. **ACSD-51036**: Behebung des Problems, bei dem die Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen zu einem Überschreiben der Versandstatusinformationen in der Tabelle [!UICONTROL Items Ordered] führen.
1. **ACSD-50858**: Behebung des Problems, bei dem ein Gutschein fälschlicherweise als nach einer fehlgeschlagenen Kartenzahlung als verwendet markiert wurde.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
