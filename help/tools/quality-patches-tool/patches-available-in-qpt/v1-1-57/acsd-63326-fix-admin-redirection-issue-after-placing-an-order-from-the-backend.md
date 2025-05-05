---
title: 'ACSD-63326: Behebung eines Admin-Umleitungsproblems nach einer Bestellung über das Backend'
description: Wenden Sie den Patch „ACSD-63326“ an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator nach einer Bestellung über das Backend zu einer fehlerhaften Seite weitergeleitet wird.
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 47603deecdf5ac3e6be18efeef38cba52ec936ec
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326: Behebung eines Admin-Umleitungsproblems nach einer Bestellung über das Backend

Mit dem Patch ACSD-63326 wird das Problem behoben, dass der Administrator nach einer Bestellung über das Backend zu einer fehlerhaften Seite weitergeleitet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-63326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren werden zu einer Seite mit einem fehlerhaften Layout umgeleitet, nachdem sie erfolgreich eine Bestellung für einen Kunden über das Backend aufgegeben haben.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Abschnitt **[!UICONTROL Customers]** im Admin-Bedienfeld.
1. Wählen Sie einen beliebigen Kunden aus und klicken Sie auf **[!UICONTROL Edit]**.
1. Klicken Sie auf der Seite „Kundendetails“ im oberen Menü auf **[!UICONTROL Create Order]** .
1. Wählen Sie den [!UICONTROL FR French] Store aus und fügen Sie der Bestellung alle verfügbaren Produkte hinzu.
1. Füllen Sie an der Kasse die erforderlichen Details aus und klicken Sie auf **[!UICONTROL Get shipping methods and rates]**.
1. Klicken Sie **[Bestellung übermitteln]**, um die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Der Administrator wird zur Bestellbestätigungs- oder Dankeseite mit dem richtigen Layout weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator wird zu einer Seite mit fehlerhaftem Layout umgeleitet. Das Layout wird erst nach dem Aktualisieren der Seite korrigiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
