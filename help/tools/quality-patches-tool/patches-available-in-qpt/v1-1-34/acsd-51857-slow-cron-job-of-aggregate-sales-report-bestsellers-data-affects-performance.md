---
title: 'ACSD-51857: Langsamer Cron-Auftrag von "aggregate_sales_report_bestsellers_data"wirkt sich auf die Leistung aus'
description: Wenden Sie den Patch ACSD-51857 an, um das Adobe Commerce-Problem zu beheben, bei dem der langsame Cron-Auftrag "aggregate_sales_report_bestsellers_data"große Datenbanktabellen "sales_order"und "sales_order_item"betrifft.
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857: Langsamer Cron-Auftrag von `aggregate_sales_report_bestsellers_data` wirkt sich auf die Leistung aus

Der Patch ACSD-51857 behebt das Problem, dass der langsame Cron-Auftrag `aggregate_sales_report_bestsellers_data` große `sales_order` - und `sales_order_item` Datenbanktabellen betrifft. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-51857. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Leistung des Cron-Auftrags von `aggregate_sales_report_bestsellers_data` ist bei den Datenbanktabellen `sales_order` und `sales_order_item` langsam.

Um dies zu beheben, wurde die Hauptdatenabfrage, die Daten für den Bericht abruft, in ein effizienteres Formular umgeschrieben. Jetzt wird eine Unterabfrage verwendet, um die Datenuntergruppe zu bestimmen.

Damit die Unter-Abfrage so schnell wie möglich funktioniert, wurde ein neuer Index für die `sales_order`-Datenbanktabelle hinzugefügt: `SALES_ORDER_STORE_STATE_CREATED` basierend auf den Spalten `store_id`, `state` und `created_at`.

<u>Voraussetzungen</u>

Stellen Sie täglich eine große Anzahl von Bestellungen sicher.

<u>Zu reproduzierende Schritte</u>

1. Führen Sie den Cron-Auftrag `aggregate_sales_report_bestsellers_data` aus.
1. Überprüfen Sie die im Admin-Dashboard anzuzeigenden Daten auf der Registerkarte **[!UICONTROL Bestsellers]** .

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Quantity per source]* unter der Registerkarte **[!UICONTROL Configuration]** darf nicht leer sein.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL Quantity per source]* unter der Registerkarte **[!UICONTROL Configuration]** ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
