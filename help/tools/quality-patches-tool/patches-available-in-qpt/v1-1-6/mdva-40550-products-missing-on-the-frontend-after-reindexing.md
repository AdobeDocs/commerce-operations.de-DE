---
title: 'MDVA-40550: Produkte, die nach der Neuindizierung auf der Vorderseite fehlen'
description: Der Patch MDVA-40550 löst das Problem, dass die Neuindizierung dazu führt, dass einige oder alle Storefront-Kategorien Produkte fehlen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40550. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550: Produkte, die nach der Neuindizierung auf der Vorderseite fehlen

Der Patch MDVA-40550 löst das Problem, dass die Neuindizierung dazu führt, dass einige oder alle Storefront-Kategorien Produkte fehlen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40550. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt.
1. Wechseln Sie in den Indexer zu **Nach Zeitplan aktualisieren** .
   * Weisen Sie das Produkt einer Kategorie zu.
1. Aktivieren Sie xdebug und machen Sie xdebug zum Haltepunkt in `\Magento\Indexer\Model\Indexer::reindexAll` und `\Magento\Indexer\Model\IndexMutex::execute`.
1. Führen Sie eine **vollständige Neuindizierung** von `catalog_category_product` mit dem Befehl aus:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Warten Sie, bis die Ausführung am Haltepunkt `\Magento\Indexer\Model\Indexer::reindexAll` beendet wird.

1. Führen Sie in einer anderen Konsole parallel mit dem Befehl einen **partiellen Neuindizierungswert** aus:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Warten Sie, bis die Ausführung am Haltepunkt `\Magento\Indexer\Model\IndexMutex::execute` beendet wird. Dadurch wird der `catalog_category_product`-Indexer gesperrt.
1. Setzt die Ausführung der vollständigen Neuindizierung von `catalog_category_product` fort und wartet auf eine Sperrzeitüberschreitung (60 Sekunden).

<u>Erwartete Ergebnisse</u>:

Keine Fehlermeldungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

*Die Sperre für den Index konnte nicht erfasst werden: catalog_category_product.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
