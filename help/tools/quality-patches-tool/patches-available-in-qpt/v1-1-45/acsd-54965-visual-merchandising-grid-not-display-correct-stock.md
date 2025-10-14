---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht den richtigen Bestand an'
description: Wenden Sie den Patch ACSD-54965 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!UICONTROL Visual Merchandising]-Raster nicht den richtigen Bestand anzeigt, wenn ein Produkt einem benutzerdefinierten Bestand zugewiesen wird.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht den richtigen Bestand an

Mit dem Patch ACSD-54965 wird das Problem behoben, dass im [!UICONTROL Visual Merchandising] nicht der richtige Bestand angezeigt wird, wenn ein Produkt einem benutzerdefinierten Bestand zugewiesen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-54965. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
