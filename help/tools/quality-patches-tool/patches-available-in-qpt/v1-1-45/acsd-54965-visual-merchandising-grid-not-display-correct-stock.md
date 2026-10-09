---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht den richtigen Bestand an'
description: Wenden Sie den Patch ACSD-54965 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!UICONTROL Visual Merchandising]-Raster nicht den richtigen Bestand anzeigt, wenn ein Produkt einem benutzerdefinierten Bestand zugewiesen wird.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '406'
ht-degree: 0%
---
# ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht den richtigen Bestand an

Mit dem Patch ACSD-54965 wird das Problem behoben, dass im [!UICONTROL Visual Merchandising] nicht der richtige Bestand angezeigt wird, wenn ein Produkt einem benutzerdefinierten Bestand zugewiesen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-54965. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das [!UICONTROL Visual Merchandising] zeigt nicht den richtigen Bestand an, wenn ein Produkt einem benutzerdefinierten Bestand zugewiesen wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Quelle.
1. Neues Lager erstellen.
1. Erstellen Sie zwei Produkte:
   * Nur ein Produkt mit dem benutzerdefinierten Lager.
   * Nur ein Produkt mit dem Standardlager.
1. Fügen Sie diese Produkte einer Kategorie hinzu.
1. Zum [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*) wechseln.

<u>Tatsächliche Ergebnisse</u>:

In den *[!UICONTROL All Store Views]* Bereichen zeigt das Produkt mit benutzerdefiniertem Lagerbestand keine Menge an. Nur wenn der *[!UICONTROL Default Store View]* ausgewählt ist, zeigt der benutzerdefinierte Bestand die Menge des Produkts an.

<u>Erwartete Ergebnisse</u>:

Das Raster zeigt alle Stock-Informationen an, wenn der Umfang *[!UICONTROL All Store Views]* ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
