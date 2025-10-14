---
title: 'ACSD-66404: Cron-Auftrag kann Änderungsprotokolltabellen aufgrund von Größenbeschränkungen für  [!DNL Galera Cluster]  Transaktion nicht löschen'
description: Wenden Sie den Patch ACSD-66404 an, um das Adobe Commerce-Problem zu beheben, bei dem mit Cron-Auftrag keine Änderungsprotokolltabellen gelöscht  [!DNL Galera Cluster]  und Probleme bei großen Datenmengen in diesen Tabellen verursacht werden.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404: Cron-Auftrag kann Änderungsprotokolltabellen aufgrund [!DNL Galera Cluster] Transaktionsgrößenbeschränkungen nicht löschen

Mit dem Patch ACSD-66404 wird das Problem behoben, dass der Cron-Auftrag keine Changelog-Tabellen löscht, was bei der Verarbeitung großer Datenmengen zu [!DNL Galera Cluster] führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-66404. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6, 2.4.7-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Cron-Vorgang löscht keine Änderungsprotokolltabellen und verursacht [!DNL Galera Cluster] Probleme bei großen Datenmengen in diesen Tabellen.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie viele Produkte mithilfe von Leistungsprofilen.
1. Führen Sie eine Massenaktualisierung für alle Produkte im System durch, sodass es viele Einträge in `inventory_cl` DB-Tabelle gibt.
1. Führen Sie den `indexer_clean_all_changelogs` Cron-Auftrag aus.

<u>Erwartete Ergebnisse</u>:

Der `indexer_clean_all_changelogs` Cron-Auftrag kann eine Changelog-Bereinigung für ein großes Changelog (10+ GB) in mehreren Löschabfragen durchführen, ohne [!DNL Galera Cluster] zu verursachen.

<u>Tatsächliche Ergebnisse</u>:

Der `indexer_clean_all_changelogs` Cron-Auftrag führt eine Changelog-Bereinigung für ein großes Changelog (10+ GB) in einer einzigen Löschabfrage durch, was zu [!DNL Galera Cluster] führt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
