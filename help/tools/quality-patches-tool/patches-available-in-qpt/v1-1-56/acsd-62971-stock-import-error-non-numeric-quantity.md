---
title: 'ACSD-62971: Der Import von Lagerbeständen mit nicht numerischen Mengenwerten führt dazu, dass die Menge auf 0 gesetzt wird'
description: Wenden Sie den Patch ACSD-62971 an, um das Adobe Commerce-Problem zu beheben, bei dem der Import von Lagerquellen mit nicht numerischen Werten in der Spalte „Menge“ dazu führt, dass die Menge auf 0 gesetzt wird.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
source-git-commit: 6803cf2bf27e99300f682308517011b73127fd94
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971: Der Import von Lagerbeständen mit nicht numerischen Mengenwerten führt dazu, dass die Menge auf 0 gesetzt wird

Der Patch ACSD-62971 behebt das Problem, dass der Import von Lagerquellen mit nicht numerischen Werten in der Spalte „Menge“ dazu führt, dass die Menge auf 0 gesetzt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62971. Das Problem wurde planmäßig in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es wurde das Problem behoben, bei dem der Import von Lagerquellen mit nicht numerischen Werten in der Spalte **[!UICONTROL Quantity]** dazu führte, dass die Menge auf 0 gesetzt wurde.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL Simple Product]** mit Menge=100 erstellen
1. Führen Sie einen **[!UICONTROL Stock Sources]** Import mit der Datei durch, die eine falsche Menge („abc„) aufweist

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Überprüfen Sie die Menge nach dem Import.

<u>Erwartete Ergebnisse</u>:
Die Validierung der Importdaten sollte fehlschlagen.

<u>Tatsächliche Ergebnisse</u>:
Die Menge des einfachen Produkts ist 0 geworden, und das Produkt wird wie [!UICONTROL Out of Stock] aktualisiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
