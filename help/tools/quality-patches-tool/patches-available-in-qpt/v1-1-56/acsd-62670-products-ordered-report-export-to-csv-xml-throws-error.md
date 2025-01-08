---
title: 'ACSD-62670: [!UICONTROL Ordered Products Report] Export in CSV und XML löst einen Fehler aus'
description: Wenden Sie den Patch ACSD-62670 an, um das Adobe Commerce-Problem zu beheben, bei dem das Exportieren der [!UICONTROL Ordered Products Report] in CSV und XML einen Fehler auslöst.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
source-git-commit: 0f26c762ee0cce3a415689b5196bfa564516e766
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# ACSD-62670: *[!UICONTROL Ordered Products Report]* Export in CSV und XML löst einen Fehler aus

Der Patch ACSD-62670 behebt das Problem, dass beim Exportieren der *[!UICONTROL Ordered Products Report]* in CSV und XML ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62670. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Export der *[!UICONTROL Ordered Products Report]* in CSV und XML löst einen Fehler aus.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zum Bedienfeld *Admin* und navigieren Sie zu **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Versuchen Sie, entweder CSV- oder Excel-Dateien zu exportieren.

<u>Erwartete Ergebnisse</u>:

Berichte werden fehlerfrei exportiert.

<u>Tatsächliche Ergebnisse</u>:

Der Export der *[!UICONTROL Ordered Products Report]* führt zu Fehler 404.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
