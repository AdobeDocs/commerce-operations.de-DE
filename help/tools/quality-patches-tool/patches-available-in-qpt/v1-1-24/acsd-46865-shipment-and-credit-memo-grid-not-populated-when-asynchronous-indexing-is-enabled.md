---
title: 'ACSD-46865: [!UICONTROL shipment] und [!UICONTROL credit memo] nicht ausgefüllt, wenn [!UICONTROL asynchronous indexing] aktiviert ist'
description: Wenden Sie den Patch ACSD-46865 an, um das Adobe Commerce-Problem zu beheben, bei dem [!UICONTROL shipment]- und [!UICONTROL credit memo]-Raster nicht ausgefüllt werden, wenn [!UICONTROL asynchronous indexing] aktiviert ist.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] und [!UICONTROL credit memo] nicht ausgefüllt, wenn [!UICONTROL asynchronous indexing] aktiviert ist

Mit dem Patch ACSD-46865 wird das Problem behoben, dass [!UICONTROL shipment]- und [!UICONTROL credit memo]-Raster nicht ausgefüllt werden, wenn [!UICONTROL asynchronous indexing] aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-46865. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!UICONTROL Shipment]- und [!UICONTROL credit memo] werden bei aktiviertem [!UICONTROL asynchronous indexing] nicht ausgefüllt.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie im [!DNL Commerce] Admin zu **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *YES*.
2. Wechseln Sie erneut zu **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Konfigurationscache leeren.
4. Erteilen Sie eine neue Gastbestellung für ein einfaches Produkt.
5. Cron ausführen.
6. Öffnen Sie die Bestellung im [!UICONTROL Commerce] Admin, indem Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** wechseln und eine Rechnung und eine Gutschrift generieren.
7. Verschieben Sie die Bestellung nach [!UICONTROL Archive].
8. Erstellen Sie eine weitere Bestellung für ein einfaches Produkt.
9. Cron ausführen.
10. Wechseln Sie zur neuen Bestellung und erstellen Sie eine neue Lieferung, eine Rechnung und eine Gutschrift.
11. Cron ausführen.
12. Überprüfen Sie die [!UICONTROL shipments], [!UICONTROL invoices] und [!UICONTROL credit memo] Raster in der Admin-Liste.

<u>Erwartete Ergebnisse</u>:

Neue [!UICONTROL shipment], [!UICONTROL invoice] und [!UICONTROL credit memo] werden angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Neue [!UICONTROL shipment], [!UICONTROL invoice] und [!UICONTROL credit memo] werden nicht angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
