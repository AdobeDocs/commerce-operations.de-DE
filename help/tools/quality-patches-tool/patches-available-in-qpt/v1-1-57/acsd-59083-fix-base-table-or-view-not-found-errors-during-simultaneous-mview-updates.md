---
title: 'ACSD-59083: Fehler bei Basistabelle oder Ansicht nicht gefunden bei gleichzeitigen Aktualisierungen der Ansicht'
description: Wenden Sie den ACSD-59083-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem bestimmte Datenbankaktualisierungsvorgänge mit dem Fehler „Basistabelle oder Ansicht nicht gefunden“ fehlschlagen.
feature: System
role: Admin, Developer
exl-id: a0fa2ac9-e61f-43d5-81ff-edf178b1abc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083: *Basistabelle oder -ansicht nicht gefunden* Fehler bei gleichzeitigen `mview`

Der Patch ACSD-59083 behebt das Problem, dass bestimmte Datenbankaktualisierungsvorgänge mit dem Fehler „Basistabelle oder Ansicht nicht gefunden“ fehlschlagen, wenn `mview` Aktualisierungen gleichzeitig ausgeführt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-59083. Beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bestimmte Datenbankaktualisierungsvorgänge führen zu Fehlern der Art „Basistabelle oder Ansicht nicht gefunden“, wenn `mview` Aktualisierungen gleichzeitig ausgeführt werden.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie den Indexermodus auf **[!UICONTROL Update on Schedule]**.
1. Fügen Sie Datensätze mithilfe der folgenden SQL-Befehle in `cl` Tabellen ein:

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. Installieren Sie das `setup/performance-toolkit/profiles/ce/small.xml`.
1. Fügen Sie einen Haltepunkt in der Datei `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` in Zeile 72 hinzu.
1. Löschen Sie den Cache.
1. Klicken Sie auf ein beliebiges Produkt **[!UICONTROL Add to Cart]**.
1. Starten Sie den Cron-Vorgang, wenn die Ausführung den Breakpoint erreicht.
1. Setzen Sie den Prozess nach dem Starten des Cron-Auftrags fort.

<u>Erwartete Ergebnisse</u>:

Die Datenbankvorgänge werden ohne Fehler erfolgreich ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

Bei der Ausführung tritt ein Fehler auf:

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
