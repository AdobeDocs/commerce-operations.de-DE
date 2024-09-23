---
title: "ACSD-55414: Schlechte Leistung, wenn MariaDB versucht, die entitys_ids zu übertragen."
description: Wenden Sie den Patch ACSD-55414 an, um das Adobe Commerce-Problem zu beheben, wenn die MariaDB versucht, "entitys_ids"aus Zeichenfolge in Ganzzahl zu konvertieren. Dadurch wird die Neuindizierung behindert.
feature: Attributes
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-55414: Schlechte Leistung, wenn MariaDB versucht, den `entitys_ids` zu spielen

Der Patch ACSD-55414 behebt das Problem, bei dem die Neuindizierung beeinträchtigt wird, wenn die MariaDB versucht, `entitys_ids` von der Zeichenfolge in die Ganzzahl zu konvertieren. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.41 installiert ist. Die Patch-ID ist ACSD-55414. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung wird behindert, wenn die MariaDB versucht, die `entitys_ids` von der Zeichenfolge in die Ganzzahl zu übertragen.

<u>Zu reproduzierende Schritte</u>:

1. Aktualisieren Sie `setup/performance-toolkit/profiles/ce/small.xml`, indem Sie einfache Produkte für *50000* einrichten.
1. Generieren Sie dieses Profil, indem Sie den Befehl `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml` ausführen.
1. Führen Sie reindex aus: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Erwartete Ergebnisse</u>:

Der Abschluss der Neuindizierung dauert vernünftig.

<u>Tatsächliche Ergebnisse</u>:

Der Abschluss der Neuindizierung dauert zu lange.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
