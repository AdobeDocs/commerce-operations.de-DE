---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.31  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.31

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.31 verfügbaren Patches behoben wurden.

QPT v1.1.31 umfasst die folgenden Patches:

1. **ACSD-50817**: Optimiert die `sales_clean_quotes` von Cron-Aufträgen für eine schnellere Ausführung, indem ein zusammengesetzter Index für `store_id` und `updated_at` Spalten in der Anführungszeichentabelle hinzugefügt wird.
1. **ACSD-50345**: Es wurde ein Problem behoben, bei dem: [!DNL Google reCAPTCHA v2] nach dem Senden einer fehlgeschlagenen Zahlung nicht neu geladen wurde, [!DNL Google reCAPTCHA v3 Invisible] an der Kasse nicht funktioniert und die Bestellung nicht aufgegeben werden kann und [!UICONTROL PlaceOrder] Ereignis nicht ausgelöst wurde.
1. **ACSD-49392**: Es wurde ein Problem behoben, bei dem sich der Bestellstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in „Geschlossen“ ändert.
1. **ACSD-51036**: Es wird das Problem behoben, bei dem Race-Bedingungen während gleichzeitiger REST-API-Aufrufe zu einer Überschreibungen der Versandstatusinformationen in der [!UICONTROL Items Ordered]-Tabelle führen.
1. **ACSD-50858**: Es wurde ein Problem behoben, bei dem ein Coupon fälschlicherweise als verwendet nach einer fehlgeschlagenen Kartenzahlung gekennzeichnet wurde.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
