---
title: 'ACSD-61756: Leistungsbeeinträchtigung von „AdvancedSalesRule“-Filtern aufgrund fehlender Datenbankindizes'
description: Wenden Sie den Patch ACSD-61756 an, um das Adobe Commerce-Problem zu beheben, bei dem die Abfrage „magento_salesrule_filter“ eine vollständige Tabellenüberprüfung ohne Verwendung von Indizes durchführt, was bei der Verarbeitung großer Datensatzmengen zu Leistungseinbußen führt. Dieser Patch verbessert die Leistung, indem er die fehlenden Datenbankindizes für „AdvancedSalesRule“-Filter hinzufügt.
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
source-git-commit: 23e92bb9032001134d2696be498a4c384f323c36
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: Leistungsbeeinträchtigung von `AdvancedSalesRule` aufgrund fehlender Datenbankindizes

Wenden Sie den ACSD-61756-Patch an, um die Leistung der `AdvancedSalesRule` Filter zu verbessern, indem Sie fehlende Datenbankindizes hinzufügen. Dadurch wird das Problem behoben, dass die `magento_salesrule_filter`-Abfrage einen vollständigen Tabellenscan durchführt, ohne die Indizes zu verwenden, was zu Leistungseinbußen führt, wenn viele Datensätze in der Tabelle vorhanden sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61756. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `magento_salesrule_filter` Abfrage führt einen vollständigen Tabellenscan ohne Verwendung von Indizes durch, was zu Leistungseinbußen der `AdvancedSalesRule` führt, wenn viele Datensätze in der Tabelle vorhanden sind.

<u>Schritte zur Reproduktion</u>:

1. Checkout mit mehreren aktiven Verkaufsregeln.

<u>Erwartete Ergebnisse</u>:

Verbesserte Leistung der Verkaufsregeln.

<u>Tatsächliche Ergebnisse</u>:

Die Abfrage führt eine vollständige Tabellenüberprüfung durch und kann keine Indizes verwenden, was zu Leistungseinbußen führt, wenn viele Datensätze in der Tabelle vorhanden sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
