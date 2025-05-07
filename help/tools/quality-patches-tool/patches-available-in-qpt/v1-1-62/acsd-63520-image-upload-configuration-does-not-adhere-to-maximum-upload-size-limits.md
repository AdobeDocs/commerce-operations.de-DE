---
title: 'ACSD-63520: Bilder, die über die Bild-Upload-Konfiguration hochgeladen wurden, überschreiten die konfigurierten Größenbeschränkungen'
description: Wenden Sie den Patch ACSD-63520 an, um das Adobe Commerce-Problem zu beheben, bei dem Bilder, die über die Bilduploadekonfiguration im Admin-Bedienfeld hochgeladen wurden, nicht den konfigurierten Maximalgrößen für den Upload entsprechen.
feature: Media, Products
role: Admin, Developer
source-git-commit: 987d335f03d552763f75adb73890787abf235e66
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-63520: Bilder, die über [!UICONTROL Image Upload Configuration] hochgeladen wurden, überschreiten die konfigurierten Größenbeschränkungen

Mit dem Patch „ACSD-63520“ wird ein Problem behoben, bei dem Bilder, die über die [!UICONTROL Images Upload Configuration] hochgeladen wurden, die konfigurierten maximalen Upload-Größenbeschränkungen nicht einhalten. Konfigurieren Sie dazu die [!UICONTROL Images Upload Configuration] im Bedienfeld [!UICONTROL Admin] . Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 installiert ist. Die Patch-ID ist ACSD-63520. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer [!DNL Adobe Commerce] Version kompatibel ist, aktualisieren Sie das `magento/quality-patches`-Paket auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bilder, die über die [!UICONTROL Images Upload Configuration] im [!UICONTROL Admin] hochgeladen wurden, entsprechen nicht der maximalen Upload-Größe.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei **[!UICONTROL Admin]** Panel an.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** und legen Sie Folgendes fest:
   * Qualität: 100
   * Frontend-Größenänderung aktivieren: Ja
   * Maximale Breite: 800
   * Maximale Höhe: 600
1. Erweitern Sie **[!UICONTROL Media Gallery Image Optimization]** und legen Sie fest:
   * Bildoptimierung aktivieren: Ja
   * Maximale Breite: 1000
   * Maximale Höhe: 1000
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**.
   1. **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** und **[!UICONTROL Price]** hinzufügen.
   1. Klicken Sie auf **[!UICONTROL Create Configurations]**, wählen Sie **[!UICONTROL Attributes]** aus und klicken Sie auf **[!UICONTROL Next]**.
   1. Wählen Sie Größen (S, M, L, XL), klicken Sie auf **[!UICONTROL Next]**.
   1. Wählen Sie unter **[!UICONTROL Images]** die Option **[!UICONTROL Apply single set of images to all SKUs]**.
   1. Laden Sie ein Bild hoch (mindestens 1024 x 1024) und klicken Sie auf **[!UICONTROL Next]**.
   1. Klicken Sie auf **[!UICONTROL Generate Product]**.
1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Bilder sollten den konfigurierten Upload-Größen- und Größenbeschränkungen folgen.

<u>Tatsächliche Ergebnisse</u>:

Die Größe der Bilder wird nicht geändert und überschreitet damit die konfigurierten Upload-Größenbeschränkungen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
