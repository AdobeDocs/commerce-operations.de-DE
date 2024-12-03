---
title: 'ACSD-48366: Produktbild wird nicht in der E-Mail-Vorlage [!UICONTROL Back to Stock] angezeigt'
description: Wenden Sie den Patch ACSD-48366 an, um das Adobe Commerce-Problem zu beheben, bei dem das Miniaturbild des Produkts nicht in der Warn-E-Mail mit dem Lagerbestand des Produkts angezeigt wird.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366: Produktbild wird nicht in der E-Mail-Vorlage [!UICONTROL Back to Stock] angezeigt

Der Patch ACSD-48366 behebt das Problem, dass das Miniaturbild des Produkts nicht in der Warn-E-Mail für Lagerbestände des Produkts angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48366. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produktbild wird nicht in der E-Mail-Vorlage [!UICONTROL Back to Stock] angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie *[!UICONTROL Product Alert]* für *[!UICONTROL Back in Stock]*, indem Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]* gehen.
1. Aktivieren Sie *[!UICONTROL Display Out of Stock Products]*, indem Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]* gehen.
1. Erstellen Sie ein einfaches Produkt mit qty = 0.
1. Erstellen Sie einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Warnungen zu Produkten zu erhalten, wenn sie auf Lager sind.
1. Nehmen Sie das Produkt auf Lager.
1. Führen Sie den Warnhinweis-Cron für das Produkt aus.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Starten Sie den Produktwarnungen für den Kunden.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Prüfen Sie die E-Mail. Eine E-Mail mit einem Stock-Warnhinweis sollte jetzt im E-Mail-Fänger verfügbar sein.

<u>Erwartete Ergebnisse</u>:

Das Produktbild wird in der E-Mail mit der Lagerwarnung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produktbild ist nicht in der E-Mail mit der Lagerwarnung verfügbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
