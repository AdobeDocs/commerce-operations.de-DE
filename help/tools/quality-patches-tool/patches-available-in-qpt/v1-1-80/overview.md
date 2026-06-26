---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.80'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.80  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: f8a08611109d9c8e5e686e0c451b0a58ecc12e21
workflow-type: tm+mt
source-wordcount: 596
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.80

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.80 verfügbaren Patches behoben wurden.

QPT v1.1.80 enthält die folgenden Patches:

1. **ACP2E-4239**: Es wird das Problem behoben, dass Admin-Rasterfilter unter Verwendung von Datumsattributen falsche Ergebnisse aufgrund von Zeitzonenunterschieden zwischen dem ausgewählten Datum, gespeicherten UTC-Werten und der konfigurierten Speicherzeitzone zurückgeben.
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**: Es wird das Problem behoben, dass während des **[!UICONTROL Login as Customer]**-Flusses ein Nullanführungseintrag in der `quote`-Datenbanktabelle erstellt wird.
1. **ACP2E-4481**: Es wurde ein Problem behoben, bei dem die Verkaufsfähigkeit von Bundle-Produkten nach Stornierung einer Bestellung nicht korrekt neu berechnet wurde.
1. **[ACP2E-4488](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488.md)**: Es wird das Problem behoben, dass das Speichern oder Bearbeiten von Produkten in Admin bei Produkten mit großen Attributsätzen langsam ist.
1. **ACP2E-4493**: Es wurde ein Problem behoben, bei dem das Raster „Kundenauftragsarchiv“ einen falschen Bestellstatus anzeigt, wenn die asynchrone Indizierung aktiviert ist.
1. **ACP2E-4496**: Behebt das Problem, dass der Analytics-Cron-Auftrag während der Ausführung zu Leistungseinbußen führt, was zu einer verbesserten Gesamtsystemleistung führt.
1. **ACP2E-4533**: Behebt das Problem, dass Platzhalterbilder nicht in die Storefront geladen werden, wenn ein Store-Code in der URL enthalten ist.
1. **ACP2E-4552**: Behebt das Problem, dass der Unternehmensstatus in der GraphQL-Antwort nicht zurückgegeben wird.
1. **[ACP2E-4610](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4610.md)**: Behebt das Problem, dass der `sales_clean_quotes` Cron-Auftrag Leistungsprobleme aufweist.
1. **[ACP2E-4552](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552.md)**: Behebt das Problem, dass der Unternehmensstatus in der GraphQL-Antwort nicht zurückgegeben wird.
1. **[ACP2E-4496](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496.md)**: Behebt das Problem, dass der Analytics-Cron-Auftrag während der Ausführung zu Leistungseinbußen führt, was zu einer verbesserten Gesamtsystemleistung führt.
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**: Es wird das Problem behoben, dass Platzhalterbilder nicht in die Storefront geladen werden, wenn ein Store-Code in der URL enthalten ist.
1. **ACP2E-4610**: Behebt das Problem, dass der `sales_clean_quotes` Cron-Auftrag Leistungsprobleme aufweist.
1. **[ACP2E-4615](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4615.md)**: Behebt das Problem, dass die Rückerstattung von Online-Bestellungen mit einem PayPal-Fehler fehlschlägt, der besagt, dass *PayPal-Gateway die Anfrage ablehnt. Interner Fehler.*.
1. **[ACP2E-4626](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626.md)**: Es wird das Problem behoben, dass einige Storefront-JavaScript-Dateien zweimal angefordert und ausgeführt wurden, was zu zeitweiligen doppelten Ladevorgängen und instabilem Verhalten führt.
1. **ACP2E-4653**: Es wird das Problem behoben, dass der **[!UICONTROL Cart Price Rule]** Bedingungsattributbereich für **[!UICONTROL Category (Parent Only)]** und **[!UICONTROL Category (Children Only)]** beim Abrufen oder Aktualisieren von Regeln über die REST-API nicht offen gelegt wird.
1. **ACP2E-4808**: Es wird das Problem behoben, dass das Attribut „Gewichtung“ auf der Produktseite der Storefront nur einen unformatierten numerischen Wert im Abschnitt &quot;**[!UICONTROL Additional Information]**&quot; oder &quot;**[!UICONTROL More Information]**&quot; ohne die konfigurierte Maßeinheit (lbs oder kgs) anzeigt.
1. **[ACP2E-4813](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4813.md)**: Behebt das Problem, dass USPS Versandmethoden an der Kasse nicht verfügbar sind und Versandschätzungen für bestimmte Produkte falsch sind, einschließlich Bestellungen, die in mehrere Pakete aufgeteilt sind.
1. **ACP2E-4626**: Es wird das Problem behoben, dass einige Storefront-JavaScript-Dateien zweimal angefordert und ausgeführt wurden, was zu zeitweiligen doppelten Ladevorgängen und instabilem Verhalten führt.
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)**: Es wird das Problem behoben, dass der Attributbereich der Warenkorbpreisregel für **[!UICONTROL Category (Parent Only)]** und **[!UICONTROL Category (Children Only)]** beim Abrufen oder Aktualisieren von Regeln über die [!DNL REST]-API nicht offen gelegt wird.
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**: Es wird das Problem behoben, dass das Attribut „Gewichtung“ auf der Produktseite der Storefront nur einen unformatierten numerischen Wert im Abschnitt &quot;**[!UICONTROL Additional Information]**&quot; oder &quot;**[!UICONTROL More Information]**&quot; ohne die konfigurierte Maßeinheit (lbs oder kgs) anzeigt.
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**: Es wird das Problem behoben, dass die Validierung von Versandadressen in der [!DNL REST]-API nicht der in Admin definierten Attributkonfiguration entspricht.
1. **ACP2E-4813**: Behebt das Problem, dass USPS Versandmethoden an der Kasse nicht verfügbar sind und Versandschätzungen für bestimmte Produkte falsch sind, einschließlich Bestellungen, die in mehrere Pakete aufgeteilt sind.
1. **[ACSD-53502](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acsd-53502.md)**: Es wurde ein Problem behoben, bei dem **[!UICONTROL Add to Cart]** in der Storefront in iOS [!DNL Safari] aufgrund rekursiver Aufrufe des New Relic-Überwachungsskripts gelegentlich fehlschlägt, was zu Seitenneuladungen führt.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
