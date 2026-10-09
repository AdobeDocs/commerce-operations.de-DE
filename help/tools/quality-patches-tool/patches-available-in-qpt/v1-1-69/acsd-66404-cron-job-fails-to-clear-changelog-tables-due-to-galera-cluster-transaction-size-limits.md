---
title: 'ACSD-66404: Cron-Auftrag kann Änderungsprotokolltabellen aufgrund [!DNL Galera Cluster] Transaktionsgrößenbeschränkungen nicht löschen'
description: Wenden Sie den Patch ACSD-66404 an, um das Adobe Commerce-Problem zu beheben, bei dem mit Cron-Auftrag keine Changelog-Tabellen gelöscht werden und [!DNL Galera Cluster] Probleme bei großen Datenmengen in diesen Tabellen auftreten.
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: d7ad3b11-aee6-4a26-8892-369fbfe6932e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '382'
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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
