---
title: 'ACSD-54067: Produktvideo wird auf Mobilgerät nicht wiedergegeben'
description: Wenden Sie den Patch ACSD-54067 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produktvideo nicht auf einem Mobilgerät wiedergegeben wird.
feature: Media, Products
role: Admin, Developer
exl-id: 023e7cf7-c344-4e86-850d-741b85df87a9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54067: Produktvideo wird nicht auf einem Mobilgerät wiedergegeben

Mit dem Patch ACSD-54067 wird das Problem behoben, dass ein Produktvideo nicht auf einem Mobilgerät wiedergegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-54067. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Produktvideo wird nicht auf einem Mobilgerät wiedergegeben.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce.
1. Führen Sie den Befehl aus:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Navigieren Sie zu **[!UICONTROL Admin product list]** Seite und filtern Sie nach *[!UICONTROL SKU product_dynamic_120]*.
1. Öffnen Sie die Produktseite und gehen Sie zu **[!UICONTROL Images and Videos]** > Video hinzufügen > Füllen Sie die URL https://vimeo.com/347119375 aus und speichern Sie.
1. Gehen Sie zur Storefront und öffnen Sie die Produktseite für *[!UICONTROL product_dynamic_120]*.
1. Setzen Sie den Browser auf *Mobilgerät* mit einer Breite von *320px* und aktualisieren Sie.
1. Wählen Sie im Galerie-Schieberegler das Video aus und klicken Sie, um es abzuspielen.

<u>Erwartete Ergebnisse</u>:

Das Produktvideo wird abgespielt.

<u>Tatsächliche Ergebnisse</u>:

Das Produktvideo wird nicht abgespielt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
