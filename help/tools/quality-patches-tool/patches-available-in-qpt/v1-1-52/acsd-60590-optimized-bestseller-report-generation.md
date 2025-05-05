---
title: 'ACSD-60590: Leistungssteigerung bei der Erstellung aggregierter täglicher Bestseller-Berichte'
description: Wenden Sie den Patch ACSD-60590 an, um das Adobe Commerce-Problem zu beheben, bei dem die Erstellung des aggregierten Tagesberichts für Bestseller bei einer großen Anzahl von aufgegebenen Bestellungen viel Zeit in Anspruch nimmt.
feature: Reporting
role: Admin, Developer
exl-id: 3b2b92eb-d4fc-4cd7-a117-a2c1caac72ec
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-60590: Leistungssteigerung bei der Erstellung aggregierter täglicher Bestseller-Berichte

Mit dem Patch ACSD-60590 wird das Problem behoben, dass die Erstellung des aggregierten Tagesberichts für Bestseller bei einer großen Anzahl von aufgegebenen Bestellungen viel Zeit in Anspruch nimmt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60590. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der aggregierte Tagesbericht zu Bestsellern benötigt erhebliche Zeit, um für eine große Anzahl an aufgegebenen Bestellungen zu generieren.

<u>Voraussetzungen</u>

Eine große Anzahl von Bestellungen (z. B.: *500k*).

<u>Schritte zur Reproduktion</u>:

1. Führen Sie den folgenden Befehl aus:

   `update sales_order set created_at = DATE(DATE_SUB(NOW(), INTERVAL ROUND(RAND()*3650) DAY))  ;`

1. Führen Sie den `aggregate_sales_report_bestsellers_data` aus.

<u>Erwartete Ergebnisse</u>:

Der Vorgang ist in weniger als 30 Sekunden beendet.

<u>Tatsächliche Ergebnisse</u>:

Die Abfrage dauert für jeden Store etwa 10 Minuten für `created_at` Daten.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
