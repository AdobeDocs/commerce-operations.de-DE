---
title: 'ACP2E-3705: Die Cron-Ausführung von „indexer_update_all_views“ schlägt fehl, wenn „MAGE_INDEXER_THREADS_COUNT“ festgelegt ist'
description: Wenden Sie den ACP2E-3705-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Cron-Ausführung von „indexer_update_all_views“ fehlschlägt, wenn „MAGE_INDEXER_THREADS_COUNT“ festgelegt ist.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
source-git-commit: 7ef772510274bc8681c395656437d64f8b40e70a
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: `indexer_update_all_views` Cron-Ausführung schlägt fehl, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt wird

>[!NOTE]
>
>Dieser Patch ersetzt den [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) für die Versionen 2.4.7 und höher.

Mit dem Patch ACP2E-3705 wird das Problem behoben, dass die `indexer_update_all_views` Cron-Ausführung fehlschlägt, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID lautet ACP2E-3705. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `indexer_update_all_views` Cron-Ausführung schlägt fehl, wenn `MAGE_INDEXER_THREADS_COUNT` auf einen Wert größer als *2* festgelegt ist, was sich speziell auf den [!UICONTROL Customer Segments]-Indexer mit aktiviertem B2B auswirkt.

<u>Schritte zur Reproduktion</u>:

1. QPT-Patch anwenden [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. **[!UICONTROL Category Permissions]** aktivieren.
1. Stellen Sie die folgenden Indexer auf den **[!UICONTROL Update on Schedule]** ein:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Erstellen Sie einige Produkte und weisen Sie sie einer Kategorie zu.
1. Führt eine vollständige Neuindizierung durch.
1. Wechseln Sie zu einer Kategorie und legen Sie **[!UICONTROL Category Permissions]** fest.
1. Führen Sie `indexer_update_all_views` Cron-Auftrag mit `MAGE_INDEXER_THREADS_COUNT` auf *8* aus.

<u>Erwartete Ergebnisse</u>:

Die Neuindizierung wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Der `indexer_update_all_views` Cron-Vorgang stößt auf den folgenden Fehler:

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
