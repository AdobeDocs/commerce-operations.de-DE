---
title: 'ACSD-49464: Rechnungen, Sendungen und Gutschriften werden nicht aus dem Archiv zurückverschoben'
description: Wenden Sie den Patch ACSD-49464 an, um das Adobe Commerce-Problem zu beheben, bei dem Rechnungen, Sendungen und Gutschriften nicht aus dem Archiv zurückverschoben werden, wenn die orderId unterschiedlich ist.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464: Rechnungen, Sendungen und Gutschriften werden nicht aus dem Archiv zurückverschoben

Der Patch ACSD-49464 behebt das Problem, dass Rechnungen, Sendungen und Gutschriften nicht aus dem Archiv zurückverschoben werden, wenn die orderId unterschiedlich ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49464. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Rechnungen, Lieferungen und Gutschriften werden nicht aus dem Archiv zurückverschoben, wenn die orderId unterschiedlich ist.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Archivierung von Bestellungen, Rechnungen, Lieferungen und Gutschriften.
1. Erstellen und Abschließen einer Bestellung, einschließlich Versand, Rechnung und Gutschrift.
1. Stellen Sie sicher, dass die Versand-, Rechnungs- und Gutschrift-IDs nicht mit der Bestellnummer übereinstimmen.
1. Verschiebt den Auftrag in das Archiv.
1. Stellen Sie die archivierte Bestellung in der Auftragsverwaltung wieder her.
1. Überprüfen Sie die Details zu Rechnungen, Versand und Gutschriften auf den entsprechenden [!UICONTROL Invoice]-, [!UICONTROL Shipping]- und [!UICONTROL Credit Memo].

<u>Erwartete Ergebnisse</u>:

Die ursprünglich verknüpften Datensätze werden wiederhergestellt, wenn die Bestellung aus der Archivliste in die Auftragsverwaltung verschoben wird.

<u>Tatsächliche Ergebnisse</u>:

* Keine Datensätze für Versand, Rechnung und Gutschriften, wenn alle Kennungen unterschiedlich sind.
* Wenn die Reihenfolge und die zugehörigen Datensätze dieselbe ID haben, werden die Datensätze zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
