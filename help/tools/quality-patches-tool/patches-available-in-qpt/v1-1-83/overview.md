---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.83 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
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
source-git-commit: cbba2086ee177da6a26da84984153b54c725e1a8
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.83

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.83 verfügbaren Patches behoben wurden.

QPT v1.1.83 enthält die folgenden Patches:

1. **[AC-17975](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-17975.md)**: Es wurde ein Problem behoben, bei dem CLI-Befehle, Kategoriebearbeitung, Design-Konfiguration und die AJAX-Kundenanmeldung in Adobe Commerce 2.4.9 fehlschlugen, wenn PHP 8.5 verwendet wird.
1. **[ACP2E-4877](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4877.md)**: Es wurde das Problem behoben, dass mit Zahlung auf Konto aufgegebene Bestellungen in Admin nicht bearbeitet werden konnten, während sie sich im Status *Ausstehend* befanden.
1. **[AC-18096](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-18096.md)**: Es wird das Problem behoben, dass Datumsfelder in Sales GraphQL Datumsangaben in einem anderen Format als frühere Versionen zurückgeben, indem das Datumsformat von durch Schrägstrich (/) getrennt auf durch Bindestrich (-) getrennt zurückgesetzt wird.
1. **[AC-18128](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-18128.md)**: Es wird das Problem behoben, bei dem von GraphQL zurückgegebene Bestelldaten und Bestellkommentar-Zeitstempel falsche Kalenderdaten in nicht englischen Gebietsschemaeinstellungen anzeigen können.
1. **[ACP2E-4838](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4838.md)**: Es wurde das Problem behoben, dass ein Admin-Benutzer mit eingeschränkten Berechtigungen keine Kunden aus dem Raster Kunden löschen kann.
1. **[ACP2E-4639](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4639.md)**: Behebt das Problem, dass der Elementtyp der Anforderungsliste im GraphQL-Schema falsch geschrieben wurde. Das Feld „Ältere `items`&quot; und der `RequistionListItems` sind weiterhin verfügbar, werden aber nicht mehr unterstützt.
1. **ACP2E-4908**: Es wird das Problem behoben, dass große Kataloge zu übermäßiger Speichernutzung in Redis oder Valkey führen, da für jedes Produkt in jeder Shop-Ansicht separate Layout-Cache-Einträge erstellt wurden.
1. **[AC-16530](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-16530.md)**: Es wird ein Problem behoben, bei dem der Warenkorb geplante Aktualisierungen der Katalogpreisregeln nicht einheitlich widerspiegelte.
1. **[ACP2E-4977](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4977.md)**: Behebt das Problem, dass die Gesamtsummen der Rechnungen und Gutschriften für konfigurierbare Produkte keine feste Produktsteuer (Fixed Product Tax, FPT) enthalten, was zu Gesamtsummen führt, die niedriger als die Bestellsumme sind.
1. **[AC-12854](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-12854.md)**: Es wird ein Problem behoben, bei dem bei der Neuanordnung einer Bestellung im Administrator eine neue Bestellnummer mit einem `-1` Suffix erstellt wird, anstatt die nächste sequenzielle Bestellnummer zuzuweisen.
1. **[AC-11389](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-11389.md)**: Es wird das Problem behoben, bei dem Rabatte, Steuern und Bestellsummen in einigen Rundungsszenarien falsch berechnet werden.
1. **[ACP2E-5015](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5015.md)**: Es wird ein Problem behoben, durch das das Speichern eines freigegebenen Katalogs in der Admin unbeabsichtigt zugewiesene Produkte und Preise entfernen kann, wenn erforderliche Katalogdaten nicht verfügbar sind.
1. **[ACP2E-4998](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4998.md)**: Behebt das Problem, dass die `POST /V1/products/tier-prices` REST-API-Anfrage für die gesamte Anfrage fehlgeschlagen ist, wenn keine SKU in der Payload vorhanden war, was verhindert, dass gültige SKUs aktualisiert werden.
1. **[AC-14940](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-14940.md)**: Es wurde ein Problem behoben, bei dem durch Klicken auf [!UICONTROL Reset Password] für ein Kundenkonto im Administrator die E-Mail zum Zurücksetzen des Kennworts in einigen Fällen im Zusammenhang mit dem Store nicht gesendet wurde.
1. **[ACP2E-5101](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5101.md)**: Es wurde ein Problem behoben, bei dem die Installation des B2B-Moduls fehlgeschlagen ist, wenn Indexer auf **[!UICONTROL Update on Schedule]** gesetzt wurden.
1. **ACP2E-5205**: Behebt das Problem, wenn das Laden von Kategorien viel Zeit in Anspruch nimmt oder eine Zeitüberschreitung verursacht, wenn eine große Anzahl von Kategorien und Produkten betroffen ist. Außerdem wird die Produktanzahl jetzt für jedes Kategorieblatt korrekt angezeigt.
1. **[ACP2E-3211](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-3211.md)**: Es wird ein Problem behoben, durch das beim gleichzeitigen Hinzufügen desselben Produkts zum Warenkorb in der Storefront separate Artikel im Warenkorb für dieselbe SKU erstellt werden, anstatt sie in einem einzigen Artikel zu kombinieren.
1. **[ACP2E-5223](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5223.md)**: Es wird das Problem behoben, dass der **[!UICONTROL Catalog Permissions]**-Index Websites enthält, die aus einer Kundengruppe ausgeschlossen sind.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
