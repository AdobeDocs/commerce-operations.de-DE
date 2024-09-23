---
title: '"ACSD-51735: Bestellelementstatus falsch auf *[!UICONTROL Ordered]* gesetzt, wenn Produktbestand 0 ist'
description: Wenden Sie den Patch ACSD-51735 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt ist, wenn der Produktbestand 0 ist.
feature: Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: Bestellelementstatus falsch auf *[!UICONTROL Ordered]* gesetzt, wenn der Produktbestand 0 ist

Der Patch ACSD-51735 behebt das Problem, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt ist, wenn der Produktbestand 0 ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50895. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Bestellelementstatus wird fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt, wenn der Produktbestand 0 beträgt.

<u>Voraussetzungen</u>:

* Adobe Commerce Inventory management (MSI)-Module sind installiert.
* Rückorder sind in **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]** aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Lager.
1. Erstellen Sie eine neue Quelle.
1. Weisen Sie dem neuen Lager die Standardwebsite zu und weisen Sie die neue Quelle zu.
1. Erstellen Sie ein neues Produkt.

   * Legen Sie die Standardquellqualität auf 10 und die neue Quellqualität auf 0 fest.

1. Fügen Sie das Produkt dem Warenkorb auf der Storefront hinzu.
1. Beobachten Sie die Hintergrundwarnung beim Checkout und geben Sie an, dass das Produkt aus einer neuen Quelle stammt.
1. Platzieren Sie die Bestellung.
1. Öffnen Sie die Bestellung in Admin und überprüfen Sie den Status der Aufstockung.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge zeigt an, dass die Menge 1 in umgekehrter Reihenfolge angeordnet ist.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge zeigt, dass die Menge 1 geordnet ist, nicht umgekehrt.

>[!MORELIKETHIS]
>
>[Der Bestellelementstatus ist falsch auf *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)eingestellt

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
