---
title: 'ACSD-64178: [!UICONTROL Edit Attribute Set] Seite wird langsam mit Tausenden von Produktattributen geladen'
description: Wenden Sie den ACSD-64178-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Edit Attribute Set]-Seite langsam geladen wird, wenn Tausende von Produktattributen vorhanden sind.
feature: Catalog Management
role: Admin, Developer
source-git-commit: 42585380737774a78800876e262e43a806e93b77
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178: [!UICONTROL Edit Attribute Set] Seite wird langsam mit Tausenden von Produktattributen geladen

Mit dem Patch ACSD-64178 wird das Problem behoben, dass die **[!UICONTROL Edit Attribute Set]** Seite langsam geladen wird, wenn Tausende von Produktattributen vorhanden sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-64178. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die **[!UICONTROL Edit Attribute Set]** Seite wird langsam geladen, wenn Tausende von Produktattributen vorhanden sind.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie mindestens 4.200 Attribute, die keinem der Attributsätze zugewiesen sind.
1. Navigieren Sie in der Seitenleiste Admin zu **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**. Klicken Sie auf ein Attribut, das Sie bearbeiten möchten.

<u>Erwartete Ergebnisse</u>:

Die Seite wird in angemessener Zeit geladen.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert mehrere Minuten.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
