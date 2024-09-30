---
title: "ACSD-49464: Rechnungen, Sendungen und Kreditkarten, die nicht aus dem Archiv zurückgezogen wurden"
description: Wenden Sie den Patch ACSD-49464 an, um das Adobe Commerce-Problem zu beheben, bei dem Rechnungen, Sendungen und Credit Memos nicht aus dem Archiv verschoben werden, wenn die orderId unterschiedlich ist.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464: Rechnungen, Sendungen und Kreditkarten werden nicht aus dem Archiv zurückgezogen

Der Patch ACSD-49464 behebt das Problem, dass Rechnungen, Sendungen und Kreditkarten nicht aus dem Archiv zurückverschoben werden, wenn die orderId unterschiedlich ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49464. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Rechnungen, Sendungen und Credit Memos werden nicht aus dem Archiv verschoben, wenn die orderId unterschiedlich ist.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Archivierung von Bestellungen, Rechnungen, Sendungen und Kreditkarten.
1. Erstellen und schließen Sie eine Bestellung, einschließlich Versand, Rechnung und Kreditkarte.
1. Stellen Sie sicher, dass die Versand-, Rechnung- und Kreditnachrichten-IDs nicht mit der Bestellnummer übereinstimmen.
1. Verschieben Sie die Reihenfolge zum Archivieren.
1. Stellen Sie die archivierte Bestellung wieder her, um sie zu verwalten.
1. Überprüfen Sie die Details zu Rechnungen, Versand und Guthaben auf den entsprechenden Rasterseiten [!UICONTROL Invoice], [!UICONTROL Shipping] und [!UICONTROL Credit Memo].

<u>Erwartete Ergebnisse</u>:

Die ursprünglichen zugehörigen Datensätze werden wiederhergestellt, wenn die Bestellung aus der Archivliste in die Auftragsverwaltung verschoben wird.

<u>Tatsächliche Ergebnisse</u>:

* Keine Datensätze für Versand-, Rechnung- und Kreditkarten, wenn alle Kennungen unterschiedlich sind.
* Wenn die Reihenfolge und die zugehörigen Datensätze dieselbe ID aufweisen, werden die Datensätze zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
