---
title: 'ACSD-61756: Leistungsbeeinträchtigung von "AdvancedSalesRule"-Filtern aufgrund fehlender Datenbankindizes'
description: Wenden Sie den Patch ACSD-61756 an, um das Adobe Commerce-Problem zu beheben, bei dem die Abfrage "magento_salesrule_filter"eine vollständige Tabellenüberprüfung ohne Verwendung von Indizes durchführt, was zu einer Leistungsbeeinträchtigung bei großen Mengen von Datensätzen führt. Dieser Patch verbessert die Leistung, indem die fehlenden Datenbankindizes für "AdvancedSalesRule"-Filter hinzugefügt werden.
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
source-git-commit: 23e92bb9032001134d2696be498a4c384f323c36
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: Leistungsbeeinträchtigung von `AdvancedSalesRule` Filtern aufgrund fehlender Datenbankindizes

Wenden Sie den Patch ACSD-61756 an, um die Leistung der `AdvancedSalesRule`-Filter durch Hinzufügen fehlender Datenbankindizes zu verbessern. Dadurch wird das Problem behoben, bei dem die `magento_salesrule_filter`-Abfrage eine vollständige Tabellenüberprüfung durchführt, ohne die Indizes zu verwenden, was zu einer Leistungsbeeinträchtigung führt, wenn sich in der Tabelle viele Datensätze befinden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61756. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die `magento_salesrule_filter` -Abfrage führt eine vollständige Tabellenüberprüfung durch, ohne Indizes zu verwenden. Dies führt zu einer Leistungsbeeinträchtigung der `AdvancedSalesRule` -Filter, wenn sich in der Tabelle viele Datensätze befinden.

<u>Zu reproduzierende Schritte</u>:

1. Checkout mit mehreren aktiven Verkaufsregeln.

<u>Erwartete Ergebnisse</u>:

Verbesserte Leistung von Verkaufsregeln.

<u>Tatsächliche Ergebnisse</u>:

Die Abfrage führt eine vollständige Tabellenüberprüfung durch und verwendet keine Indizes, was zu einer Leistungsbeeinträchtigung führt, wenn sich in der Tabelle viele Datensätze befinden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
