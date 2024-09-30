---
title: "ACSD-51036: Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen führen zu einer Überschreiben des Versandstatus"
description: Wenden Sie den Patch ACSD-51036 an, um das Adobe Commerce-Problem zu beheben, bei dem es bei gleichzeitigen REST-API-Aufrufen zu Race-Bedingungen kommt, was zu einer Überschreiben des Versandstatus in der bestellten Tabelle führt.
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036: Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen führen zu einer Überschreiben des Versandstatus in der bestellten Tabelle

Der Patch ACSD-51036 behebt das Problem, dass die Wettlaufbedingungen bei gleichzeitigen REST-API-Aufrufen dazu führen, dass der Versandstatus in der bestellten Tabelle überschrieben wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID ist ACSD-51036. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen führen dazu, dass der Versandstatus in der bestellten Tabelle der Artikel überschrieben wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit zwei Elementen.
1. Rechnungselement A.
1. Senden Sie gleichzeitig eine Rückerstattungsanforderung für den Artikel A über die REST-API, während Sie eine Anfrage für den Posten B senden.
1. Wechseln Sie zur Bestellung in **[!UICONTROL Admin Panel]**.

<u>Erwartete Ergebnisse</u>

Der Status *[!UICONTROL Shipped 1]* sollte für Element B in der sortierten Tabelle *[!UICONTROL Items]* vorhanden sein.

<u>Tatsächliche Ergebnisse</u>

Der Status *[!UICONTROL Shipped 1]* ist für Element B in der sortierten Tabelle *[!UICONTROL Items]* nicht vorhanden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
