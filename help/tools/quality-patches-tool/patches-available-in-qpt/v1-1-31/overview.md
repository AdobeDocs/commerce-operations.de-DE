---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.31 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '173'
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
