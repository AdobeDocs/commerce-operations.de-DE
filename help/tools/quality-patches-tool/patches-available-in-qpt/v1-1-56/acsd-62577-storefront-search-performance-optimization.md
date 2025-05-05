---
title: 'ACSD-62577: Leistungsoptimierung der Storefront-Suche'
description: Wenden Sie den Patch ACSD-62577 an, um das Adobe Commerce-Problem zu beheben, bei dem die Storefront-Suchleistung aufgrund der langsamen Abfrageausführung beeinträchtigt wird, die durch eine große Tabelle „search_query“ verursacht wird.
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
source-git-commit: 6803cf2bf27e99300f682308517011b73127fd94
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577: Leistungsoptimierung der Storefront-Suche

Der Patch ACSD-62577 behebt das Problem der langsamen Leistung von Storefront-Suchanfragen, indem sowohl Abfrage- als auch Tabellenindizes optimiert werden. Dieser Patch ist ab dem [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 verfügbar. Die Patch-ID ist ACSD-62577. Das Problem wurde planmäßig in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6, 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Große `search_query`-Tabellen verlangsamen die Storefront-Suche erheblich und erhöhen die Frontend-Antwortzeiten aufgrund ineffizienter Abfragen und fehlender optimierter Tabellenindizes.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie Adobe Commerce Developer mithilfe des Performance Toolkit-`small.xml` ein.
1. Greifen Sie auf die SQL-Befehlszeile zu und löschen Sie die `search_query` mithilfe der folgenden Befehle:

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Füllen Sie die `search_query` mit einer großen Anzahl von Datensätzen, z. B.: 4 Millionen Datensätze.
1. Neuindizierung von Triggern und Leeren von Caches.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Debug-Protokolle für die Datenbank aktivieren:

   ```
   bin/magento dev:query-log:enable  
   ```

1. Suchen Sie einen Begriff in der Suchleiste der Storefront, z. B.
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Überprüfen Sie die `db.log` für die Abfrageausführungszeit für die folgende SQL:

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>Erwartete Ergebnisse</u>:

Die Abfrageausführungszeit wird optimiert, was zu einer weniger signifikanten Verlängerung der Antwortzeit bei der Verarbeitung großer `search_query` führt.

<u>Tatsächliche Ergebnisse</u>:

Die Ausführungszeit der Abfrage nimmt aufgrund der ineffizienten Verarbeitung der großen `search_query` erheblich zu:

```
TIME: 10.8520 seconds  
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
