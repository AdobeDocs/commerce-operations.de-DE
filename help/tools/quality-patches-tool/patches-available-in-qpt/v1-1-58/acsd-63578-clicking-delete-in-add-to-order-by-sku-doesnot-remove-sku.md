---
title: 'ACSD-63578: Durch Klicken auf das [!UICONTROL Delete] in [!UICONTROL Add to Order by SKU] wird die SKU nicht entfernt'
description: Wenden Sie den Patch „ACSD-63578“ an, um das Adobe Commerce-Problem zu beheben, bei dem durch Klicken auf das [!UICONTROL Delete]-Symbol in [!UICONTROL Add to Order by SKU] im Admin-Bereich die SKU nicht entfernt wird.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578: Durch Klicken auf das **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* wird die SKU nicht entfernt

Mit dem Patch „ACSD-63578“ wird das Problem behoben, dass beim Klicken auf das **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* im Administrator die SKU nicht entfernt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63578. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Durch Klicken auf das **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* in der Admin-Liste wird die SKU nicht aus der Bestellung entfernt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und klicken Sie auf **[!UICONTROL Create New Order]**.
1. Wählen Sie einen Kunden.
1. Klicken Sie auf **[!UICONTROL Add to Order by SKU]**.
   * Geben Sie eine SKU ein.
   * Klicken Sie auf die Schaltfläche **[!UICONTROL Add another]** .
1. Klicken Sie auf das Symbol **[!UICONTROL Delete]** .

<u>Erwartete Ergebnisse</u>:

* Produkte werden in der Admin-Liste hinzugefügt und aus einer Bestellung entfernt.

<u>Tatsächliche Ergebnisse</u>:

* Das **[!UICONTROL Delete]** funktioniert nicht.
* In der Konsole ist ein Fehler aufgetreten:

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
