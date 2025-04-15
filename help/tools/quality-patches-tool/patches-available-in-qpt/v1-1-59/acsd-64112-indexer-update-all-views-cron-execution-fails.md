---
title: 'ACSD-64112: Die Cron-Ausführung von „indexer_update_all_views“ schlägt fehl, wenn „MAGE_INDEXER_THREADS_COUNT“ festgelegt ist'
description: Wenden Sie den Patch ACSD-64112 an, um das Adobe Commerce-Problem zu beheben, bei dem die Cron-Ausführung von „indexer_update_all_views“ fehlschlägt, wenn „MAGE_INDEXER_THREADS_COUNT“ festgelegt ist.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
source-git-commit: 0078cf5fb6d6c3a8650762d7cdf5556de642e201
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: `indexer_update_all_views` Cron-Ausführung schlägt fehl, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt ist

>[!NOTE]
>
>Dieser Patch wurde durch [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) für Adobe Commerce-Versionen über 2.4.7 ersetzt.

Der Patch ACSD-64112 behebt das Problem, dass die `indexer_update_all_views` Cron-Ausführung fehlschlägt, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-64112. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p10

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `indexer_update_all_views` Cron-Ausführung schlägt fehl, wenn `MAGE_INDEXER_THREADS_COUNT` auf einen Wert größer als 2 festgelegt ist, was sich speziell auf den [!UICONTROL Customer Segments]-Indexer mit aktiviertem B2B auswirkt.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Instanz mit B2B.
1. Aktivieren Sie **[!UICONTROL B2B Company]** und **[!UICONTROL Shared Catalog]**.
1. Erstellen Sie eine Kategorie.
1. Erstellen Sie einige Produkte und weisen Sie sie der Kategorie zu.
1. Führt eine vollständige Neuindizierung durch.
1. Stellen Sie die folgenden Indexer auf **[!UICONTROL Update on Schedule]** ein:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Wechseln Sie zum Backend und laden Sie die neu erstellte Kategorie.
1. Klicken Sie auf **[!UICONTROL Category Permissions]** und erstellen Sie eine **[!UICONTROL New Permission]** für eine bestehende Kundengruppe.
1. Stellen Sie sicher, dass der `catalogpermissions_category` Indexer einen Rückstand aufweist. Führen Sie den folgenden Befehl aus, um dies zu überprüfen:

   ```
   bin/magento indexer:status
   ```

1. Legen Sie die folgende Indexer-Thread-Anzahl in `env.php` fest:

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Cron-Auftrag ausführen:

   ```
   bin/magento cron:run
   ```

<u>Erwartete Ergebnisse</u>:

Der Cron-Auftrag sollte ohne Probleme ausgeführt werden.

<u>Tatsächliche Ergebnisse</u>:

Der `indexer_update_all_views` Cron-Vorgang stößt auf den folgenden Fehler:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Zusätzliche Schritte nach der Patch-Installation erforderlich

(Dieser Abschnitt ist optional. Nach der Anwendung des Patches sind möglicherweise einige Schritte erforderlich, um das Problem zu beheben.) 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
