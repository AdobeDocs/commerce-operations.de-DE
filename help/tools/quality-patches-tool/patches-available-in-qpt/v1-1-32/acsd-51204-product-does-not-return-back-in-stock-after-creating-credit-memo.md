---
title: "ACSD-51204: Produkt kehrt nach Erstellung des Kreditmemo nicht wieder auf Lager zurück."
description: Wenden Sie den Patch ACSD-51204 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produkt nach dem Erstellen des Kreditmemo nicht wieder auf Lager ist.
feature: Orders, Products, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51204: Produkt wird nach der Erstellung des Kreditprotokolls nicht wieder auf Lager

Der Patch ACSD-51204 behebt das Problem, dass das Produkt nach dem Erstellen des Kreditmemo nicht wieder vorrätig ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51204. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das ausverkaufte Produkt wird nach der Erstellung des Kreditmemo nicht wieder vorrätig.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie **[!UICONTROL Adobe Commerce]** und aktivieren Sie die **[!UICONTROL Inventory Management Module]** nur mit der Standardquelle *source* und *stock*.
1. Fügen Sie eine **[!UICONTROL new product]** mit einer Menge von *10* hinzu.
1. Weisen Sie das Produkt dem **[!UICONTROL default stock]** zu.
1. Fügen Sie das Produkt auf der Storefront zum Warenkorb hinzu und bestellen Sie eine ganze verfügbare Menge von 10.
1. Generieren Sie im Admin-Bedienfeld eine *Rechnung* und eine *Sendung* für die Bestellung.
1. Erstellen Sie eine **[!UICONTROL Credit Memo]** mit dem Kontrollkästchen *Zurück zu Lager* , das für alle Elemente ausgewählt ist.
1. Überprüfen Sie die &quot;**[!UICONTROL Salable Quantity]**&quot; des Produkts in der Admin-Konsole.

<u>Erwartete Ergebnisse</u>:

Die verkaufbare Menge des Produkts muss auf *10* zurückgesetzt werden.

<u>Tatsächliche Ergebnisse</u>:

Die verkaufbare Menge des Produkts wird als *0* beibehalten.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
