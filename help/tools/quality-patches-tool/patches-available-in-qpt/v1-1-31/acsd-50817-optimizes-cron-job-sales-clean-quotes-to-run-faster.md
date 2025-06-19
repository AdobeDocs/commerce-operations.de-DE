---
title: 'ACSD-50817: Optimiert Cron-Auftrag sales_clean_quotes für eine schnellere Ausführung'
description: Wenden Sie den Patch ACSD-50817 an, um den Cron-Auftrag „sales_clean_quotes“ durch Hinzufügen eines zusammengesetzten Index für die Spalten „store_id“ und „updated_at“ in der Angebotstabelle zu optimieren und schneller zu laufen.
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817: Optimiert Cron-`sales_clean_quotes` für eine schnellere Ausführung

Der Patch ACSD-50817 optimiert die Ausführung des Cron-Job-`sales_clean_quotes`, indem ein zusammengesetzter Index für die `store_id` und `updated_at` Spalten in der Anführungszeichentabelle hinzugefügt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID ist ACSD-50817.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Cron-Job `sales_clean_quotes` ist zu langsam. Mit diesem Patch wurde er für eine schnellere Ausführung optimiert, indem ein zusammengesetzter Index für die `store_id` und `updated_at` Spalten in der Anführungszeichentabelle hinzugefügt wurde.

<u>Schritte zur Reproduktion</u>:

1. Generieren von 50-80 Millionen Angeboten, wobei die `updated_at` auf einen Zeitraum von &lt; 30 Tagen festgelegt ist.
1. Führen Sie den Cron-`sales_clean_quotes` oder die folgende Abfrage für die Angebotstabelle aus:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Erwartete Ergebnisse</u>

Cron Job `sales_clean_quotes` wurde optimiert, um schneller zu laufen, indem ein zusammengesetzter Index für die `store_id` und `updated_at` Spalten in der Anführungszeichentabelle hinzugefügt wurde.

<u>Tatsächliche Ergebnisse</u>

Die Abfrage ist zu langsam.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
