---
title: 'ACSD-58325: Schaltfläche "[!UICONTROL Import]" auch nach einem Validierungsfehler verfügbar'
description: Wenden Sie den ACSD-58325-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Schaltfläche [!UICONTROL Import] auch nach einem Validierungsfehler verfügbar ist.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
source-git-commit: c50fa066d02c04a08c28730afffe4508019a93aa
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325: Schaltfläche &quot;[!UICONTROL Import]&quot; auch nach einem Validierungsfehler verfügbar

Mit dem Patch ACSD-58325 wird das Problem behoben, dass die Schaltfläche **[!UICONTROL Import]** auch nach einem Validierungsfehler verfügbar ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-58325. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Schaltfläche [!UICONTROL Import] ist auch nach einem Validierungsfehler verfügbar.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie die CSV-Datei für den Produktimport mit einem falschen Bildnamen in der Datei.
1. Erstellen Sie einen geplanten Produktimport mit der erstellten CSV-Datei.
1. Warten Sie, bis der geplante Import durchgeführt wurde.
1. Überprüfen Sie [!UICONTROL Last outcome] in **[!UICONTROL Scheduled Imports/Exports]** Raster.

<u>Erwartete Ergebnisse</u>:

[!UICONTROL Last outcome] sollte [!UICONTROL Failed] werden.

<u>Tatsächliche Ergebnisse</u>:

[!UICONTROL Last outcome] ist [!UICONTROL Successful].

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
