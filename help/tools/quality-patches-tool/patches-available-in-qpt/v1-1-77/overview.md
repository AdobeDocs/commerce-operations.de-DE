---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.77'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.77 verfügbaren Patches behoben wurden.
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.77

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.77 verfügbaren Patches behoben wurden.

QPT v1.1.77 enthält die folgenden Patches:

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**: Es wurde ein Problem behoben, bei dem falsche Preise angezeigt wurden, da [!DNL Redis] Cache nicht bereinigt werden konnte.
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**: Es wird ein Problem behoben, bei dem `X-Magento-Vary` Cookie beim Laden von PDP mehrmals gesetzt wird, wenn mehrere Kundensegmente im Store erstellt werden.
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**: Es wurde ein Problem behoben, bei dem die Checkout-Leistung mit zunehmender Anzahl der Kundensegmente nachließ.
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**: Es wurde ein Problem behoben, bei dem die Vorschau des geplanten Updates fehlschlug, wenn versucht wurde, Inhalte für Stores mit benutzerdefinierten Domains in der Vorschau anzuzeigen.
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**: Es wird ein Problem behoben, bei dem die Erstellung eines Kundenkontos bei Verwendung des arabischen Gebietsschemas fehlschlägt und das Attribut Geburtsdatum (DOB) auf der Storefront angezeigt wird.
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**: Es wird ein Problem behoben, bei dem zwischenspeicherbare Seiten nicht ordnungsgemäß gespeichert oder aus dem [!DNL Fastly]-Cache bereitgestellt werden, was zu inkonsistentem Caching-Verhalten und reduzierter Leistung führt.
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**: Es wurde ein Problem behoben, bei dem der Sonderpreis nicht für Websites gilt, die in verschiedenen Zeitzonen erstellt wurden.
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**: Es wird ein Problem behoben, bei dem ein konfigurierbares Produkt automatisch in [!DNL Page Builder] Produktkarusselllisten aufgenommen wird, wenn eines der untergeordneten Produkte die Filterbedingungen erfüllt.
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**: Es wurde ein Problem behoben, bei dem die Anzahl der Einträge, die über die `sales_*_async_insert` Cron-Aufträge verarbeitet und eingefügt werden können, auf *100* pro Ausführung begrenzt ist.
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**: Fehlerkorrektur: Es wird ein Problem mit der falschen Steuerberechnung in Gutschriften behoben, wenn eine teilweise Rückerstattung aus einer Rechnung erstellt wurde, wenn eine vorherige Gutschrift auf der Seite „Bestellansicht“ erstellt wurde.
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**: Es wird ein Problem behoben, bei dem Guthaben und Ablaufdaten von Geschenkgutscheinen nicht entsprechend dem zugewiesenen Website-Umfang angezeigt werden.
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**: Es wurde ein Problem mit den asynchronen Rückerstattungsvorgängen behoben, bei dem Rückerstattungsanfragen mit dem `is_online` Parameter nicht korrekt verarbeitet wurden.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
