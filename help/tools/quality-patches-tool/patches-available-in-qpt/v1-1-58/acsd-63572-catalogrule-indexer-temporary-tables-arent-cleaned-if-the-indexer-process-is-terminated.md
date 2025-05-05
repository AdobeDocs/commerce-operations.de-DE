---
title: 'ACSD-63572: Temporäre Indexertabellen „catalogrule“ werden nicht bereinigt, wenn der Indexerprozess beendet wird'
description: Wenden Sie den Patch ACSD-63572 an, um das Adobe Commerce-Problem zu beheben, bei dem die Indexertabellen nicht bereinigt werden, wenn der Prozess aufgrund eines System-Upgrades oder -Stopps in [!UICONTROL CLI] beendet wurde.
feature: System
Role: Admin, Developers
source-git-commit: 588a543a8c0bfb8067f81e7131d0a53e5cdc340a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# ACSD-63572: `catalogrule` temporären Indexertabellen werden nicht bereinigt, wenn der Indexerprozess beendet wird

Mit dem Patch ACSD-63572 wird das Problem behoben, dass die temporären Indexertabellen nicht bereinigt werden, wenn der Prozess aufgrund eines System/Upgrades oder Anhaltens in [!UICONTROL CLI] beendet wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63572. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Temporäre Indexertabellen werden nicht bereinigt, wenn der Prozess aufgrund eines System-Upgrades oder eines Anhaltens in [!UICONTROL CLI] beendet wurde.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie [!UICONTROL CLI].
1. Befehl ausführen: `bin/magento indexer:reindex catalogrule_rule`.
1. Bricht den Prozess ab, bevor er abgeschlossen ist mit: `^C`.
1. Setzen Sie die Indexer zurück mit: `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Wiederholen Sie die vorherigen Schritte mehrmals.
1. Suchen Sie nach den folgenden temporären Tabellen, die in der Datenbank erstellt wurden:

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>Erwartete Ergebnisse</u>:

Die alten temporären Tabellen werden gelöscht, wenn sie nicht benötigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die alten temporären Tabellen werden nicht entfernt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
