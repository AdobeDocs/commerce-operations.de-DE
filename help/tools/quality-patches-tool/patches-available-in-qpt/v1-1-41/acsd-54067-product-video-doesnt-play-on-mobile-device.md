---
title: "ACSD-54067: Produktvideo wird nicht auf Mobilgeräten wiedergegeben"
description: Wenden Sie den Patch ACSD-54067 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produktvideo nicht auf einem Mobilgerät wiedergegeben wird.
feature: Media, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54067: Produktvideo wird nicht auf einem Mobilgerät wiedergegeben

Der Patch ACSD-54067 behebt das Problem, dass ein Produktvideo nicht auf einem Mobilgerät wiedergegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-54067. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Produktvideo wird nicht auf einem Mobilgerät wiedergegeben.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Führen Sie den Befehl aus:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Gehen Sie zur Seite **[!UICONTROL Admin product list]** und filtern Sie nach *[!UICONTROL SKU product_dynamic_120]*.
1. Öffnen Sie die Produktseite und gehen Sie zu &quot;**[!UICONTROL Images and Videos]**&quot;> &quot;Video hinzufügen&quot;> füllen Sie die URL aus: https://vimeo.com/347119375 und speichern Sie.
1. Gehen Sie zur Storefront und öffnen Sie die Produktseite für *[!UICONTROL product_dynamic_120]*.
1. Setzen Sie den Browser auf *Mobilgerät* mit einer Breite von *320px* und aktualisieren Sie ihn.
1. Wählen Sie im Galerie-Schieberegler das Video aus und klicken Sie auf , um es abzuspielen.

<u>Erwartete Ergebnisse</u>:

Das Produktvideo wird wiedergegeben.

<u>Tatsächliche Ergebnisse</u>:

Das Produktvideo wird nicht wiedergegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.