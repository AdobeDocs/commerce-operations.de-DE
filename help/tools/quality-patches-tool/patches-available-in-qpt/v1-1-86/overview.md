---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.86'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.86 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7becdaa615e1ee4cd31454e65a6076de31717fd2
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.86

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.86 verfügbaren Patches behoben wurden.

QPT v1.1.86 enthält die folgenden Patches:


1. **[ACP2E-5046](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5046.md)**: Es wird das Problem behoben, dass beim Aktualisieren der Seite beim Erstellen einer Bestellung in Admin dieselbe SKU mehrmals hinzugefügt wird.
1. **[ACP2E-3094](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3094.md)**: Es wird das Problem behoben, dass das Anzeigen oder Bearbeiten von **[!UICONTROL Category Permissions]** für eine Kategorie mit vielen Berechtigungen dazu führen kann, dass der Browser nicht mehr reagiert.
1. **[ACP2E-5050](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5050.md)**: Es wird das Problem behoben, dass beim Anzeigen oder Speichern einer RMA in der Admin die RMA-Nummer nicht im **[!UICONTROL Action Logs]** angezeigt wird.
1. **ACP2E-5057**: Es wird das Problem behoben, dass [!DNL GraphQL] Abfragen für Bundle-Produkte globale Bundle-Optionspreise anstelle webseitenspezifischer Preise zurückgeben, wenn **[!UICONTROL Catalog Price Scope]** auf **[!UICONTROL Website]** gesetzt ist.
1. **[ACP2E-5061](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5061.md)**: Es wird das Problem behoben, dass eine Merchandising-Regel einer Kategorie UND-Bedingungen nicht mit einer Bedingung kombinieren kann, die einem von mehreren Werten entspricht.
1. **ACP2E-5071**: Es wird ein Problem behoben, bei dem die Nachricht Nicht verfügbar auf Lager nicht immer auf der Produktseite angezeigt wird, wenn der Warenkorb des Käufers bereits die volle verfügbare Menge enthält.
1. **ACP2E-5094**: Es wird das Problem behoben, dass das Laden von Seiten erheblich langsamer ist, wenn eine `MAGENTO_DC_*` Umgebungsvariable festgelegt wird.
1. **[ACP2E-5134](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5134.md)**: Es wird ein Problem behoben, durch das das Entfernen eines in einem Paket enthaltenen Produkts aus dem freigegebenen Katalog eines Unternehmens das Bundle-Produkt im Warenkorb lässt und einen Fehler im Warenkorb und während des Checkouts verursacht.
1. **[ACP2E-5118](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5118.md)**: Behebt das Problem, dass die [!DNL Page Builder]-Vorschau nicht gerendert wird, wenn der **[!UICONTROL Translations]**-Cache deaktiviert ist.
1. **ACP2E-5146**: Es wird ein Problem behoben, bei dem ein Admin-Benutzer, der auf bestimmte Websites beschränkt ist, keine Kunden löschen kann, wenn ein Kunde auf einer anderen Website dieselbe ID wie der Admin-Benutzer hat.
1. **ACP2E-5176**: Behebt das Problem, dass E-Commerce-Ereignisse, die an [!DNL Google Analytics 4] über gesendet werden, [!DNL Google Tag Manager] das [!DNL Universal Analytics]-Format verwenden und mehrere Checkout-Ereignisse auslassen.
1. **ACP2E-5185**: Es wird ein Problem behoben, bei dem beim Verschieben einer Kategorie in der Kategoriestruktur der `There was a category move error` angezeigt wird oder es mehrere Minuten dauert, bis er abgeschlossen ist, wenn der Store viele URL-Neuschreibungen aufweist.
1. **ACP2E-4191**: Behebt das Problem, dass bestimmte REST-API-Anfragen in eine Endlosschleife geraten, wenn der **[!UICONTROL EAV types and attributes]**-Cache deaktiviert ist.
1. **ACP2E-4973**: Es wird das Problem behoben, dass beim Wechsel von **[!UICONTROL In-Store Delivery]** zu einer anderen Versandmethode die zugehörige Speicheradresse nicht aus dem Warenkorb gelöscht wird.
1. **ACP2E-5221**: Behebt das Problem, dass der **[!UICONTROL Catalog Product Permissions]** Indexer erheblich länger dauert, wenn **[!UICONTROL Quick Order]** in Installationen mit vielen Stores und Kundengruppen aktiviert ist.
1. **ACP2E-5245**: Behebt das Problem, dass ein neu registrierter Kunde, der dieselbe Adresse für Versand und Rechnungsstellung bei der ersten Bestellung verwendet, diese Adresse während des nächsten Checkouts zweimal aufgeführt sieht.
1. **ACP2E-5248**: Es wurde das Problem behoben, dass Admin-Benutzer ohne die Berechtigung **[!UICONTROL Edit Product Status]** beim Öffnen der **[!UICONTROL Add Product]**-Seite in [!DNL PHP] 8.5 den Fehler &quot;`null as array offset` veraltet“ sehen.
1. **ACP2E-5254**: Behebt das Problem, dass Produkte, die zu einer Anforderungsliste hinzugefügt wurden, nicht angezeigt werden, wenn ein Kunde die Liste öffnet, bis der Cache gelöscht ist.
1. **ACP2E-5268**: Behebt das Problem, dass das Erstellen eines konfigurierbaren Produkts fehlschlägt, wenn **[!UICONTROL Enable Frontend Resize]** auf **[!UICONTROL No]** gesetzt ist.
1. **ACP2E-3752**: Es wird das Problem behoben, dass bei der Verarbeitung von Produktimporten die `Undefined array key "apply_to"` ausgibt, wenn viele Produktimportvorgänge erstellt werden.
1. **ACP2E-5280**: Behebt das Problem, dass Kundinnen und Kunden beim Anmelden einen Fehler erhalten, während die **[!UICONTROL Category Permissions]** aktiviert ist.
1. **ACP2E-5295**: Behebt das Problem, dass die parallele Neuindizierung von Produktpreisen mit dem Fehler `Fail in child process` fehlschlägt, wenn sie nach dem **[!UICONTROL Inventory]** Indexer im selben Prozess ausgeführt wird.
1. **ACP2E-5298**: Es wird das Problem behoben, dass Admin-Benutzer mit schreibgeschütztem Zugriff auf Warenkorbpreisregeln Gutscheincodes generieren oder löschen können.
1. **ACP2E-5333**: Es wird das Problem behoben, dass das Aktualisieren eines Kundensegments mit einer **[!UICONTROL Total Number of Orders]** Bedingung, die den **[!UICONTROL is not]** Operator verwendet, und einem Wert von einem oder mehreren mit der `Unknown operator specified` fehlschlägt.
1. **ACP2E-5425**: Es wird das Problem behoben, dass Kundinnen und Kunden doppelte Auftragsbestätigungs-E-Mails für dieselbe Bestellung erhalten.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
