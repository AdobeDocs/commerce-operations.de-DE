---
title: 'ACSD-54111: Produktminiaturbild wird nicht angezeigt'
description: Wenden Sie den Patch ACSD-54111 an, um das Adobe Commerce-Problem zu beheben, bei dem alle Bilder durch das standardmäßige Produkt-Platzhalterbild ersetzt werden.
feature: Products
role: Admin, Developer
exl-id: 4615ebf6-aa68-4d49-8d91-e9756b3d4a05
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54111: Produktminiaturbild wird nicht angezeigt

Der Patch ACSD-54111 behebt das Problem, dass alle Bilder durch das standardmäßige Produkt-Platzhalterbild ersetzt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 installiert ist. Die Patch-ID ist ACSD-54111. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.2 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produktminiaturbild wird nicht angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Laden Sie das Bild mit einer Miniaturansicht hoch und legen Sie die Bildposition auf *[!UICONTROL Center]* fest.
1. Klicken Sie auf **[!UICONTROL Save Configuration]**.
1. Löschen Sie den Cache.
1. Gehen Sie als Gast/Kunde in die Storefront.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Führen Sie `bin/magento catalog:image:resize` über die Konsole aus.
1. Öffnen Sie den Mini-Warenkorb auf dem Frontend oder Produktraster am Backend, um zu sehen, ob die Miniaturansichten des Bildes sichtbar sind.

<u>Erwartete Ergebnisse</u>:

Produktbilder werden nicht durch das Platzhalterbild ersetzt.

<u>Tatsächliche Ergebnisse</u>:

Produktbilder werden durch das standardmäßige Produkt-Platzhalterbild ersetzt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
