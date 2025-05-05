---
title: 'ACSD-48366: Produktbild wird nicht in [!UICONTROL Back to Stock] E-Mail-Vorlage angezeigt'
description: Wenden Sie den Patch ACSD-48366 an, um das Adobe Commerce-Problem zu beheben, bei dem das Miniaturbild des Produkts nicht in der E-Mail mit der Warnmeldung des Produkts angezeigt wird.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366: Produktbild wird nicht in [!UICONTROL Back to Stock] E-Mail-Vorlage angezeigt

Mit dem Patch ACSD-48366 wird das Problem behoben, dass das Miniaturbild des Produkts nicht in der Stock-Benachrichtigungs-E-Mail des Produkts angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48366. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Produktbild wird nicht in der [!UICONTROL Back to Stock] E-Mail-Vorlage angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie *[!UICONTROL Product Alert]* für *[!UICONTROL Back in Stock]*, indem Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]* gehen.
1. Aktivieren Sie *[!UICONTROL Display Out of Stock Products]*, indem Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]* gehen.
1. Einfaches Produkt mit Menge = 0 erstellen.
1. Erstellen Sie eine Kundin oder einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Produktwarnungen zu erhalten, wenn es vorrätig ist.
1. Machen Sie das Produkt auf Lager.
1. Ausführen des Warnhinweiscron für das Produkt.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Starten Sie den Warnhinweis für das Produkt für den Kunden.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Überprüfen Sie die E-Mail. Die E-Mail mit den Meldebeständen sollte jetzt im E-Mail-Catcher verfügbar sein.

<u>Erwartete Ergebnisse</u>:

Das Produktbild wird in der E-Mail mit der Benachrichtigung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produktbild ist in der E-Mail mit der Stock-Benachrichtigung nicht verfügbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
