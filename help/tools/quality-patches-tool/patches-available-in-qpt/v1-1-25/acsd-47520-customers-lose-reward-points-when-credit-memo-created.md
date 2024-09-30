---
title: "ACSD-47520: Kunden verlieren Bonuspunkte, wenn ein Kreditmemo erstellt wird."
description: Wenden Sie den Patch ACSD-47520 an, um das Adobe Commerce-Problem zu beheben, bei dem Kunden bei der Erstellung eines Kreditmemo Punkte verlieren.
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47520: Kunden verlieren Bonuspunkte, wenn ein Kreditmemo erstellt wird

Der Patch ACSD-47520 behebt das Problem, dass Kunden bei der Erstellung eines Kreditmemo ihre Bonuspunkte verlieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-47520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden verlieren bei der Erstellung eines Credit Memos die Bonuspunkte.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Ändern Sie die Einstellung:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Ja_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Ja_
   * **[!UICONTROL Customers May See Reward Points History]** = _Ja_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Nein_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Ja_
1. Gehen Sie zu Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** und klicken Sie auf **[!UICONTROL Add New Rate]**.
1. Fügen Sie eine neue Rate hinzu (1:1) und leeren Sie den Cache.
1. Erstellen Sie einen Kunden und fügen Sie diesem Konto 10 Belohnungspunkte hinzu.
1. Gehen Sie zu Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Wählen Sie den im vorherigen Schritt erstellten Kunden aus.
1. Wählen Sie ein Produkt aus, dessen Preis größer als die Belohnungspunkte ist.
1. Bestellen Sie über jede Zahlungsmethode und die Bonuspunkte.
1. Erstellen Sie eine Rechnung für die Bestellung.
1. Erstellen Sie ein Kreditmemo, aber erstatten Sie nicht die Bonuspunkte.

<u>Erwartete Ergebnisse</u>:

* Der Administrator kann die Belohnungspunkte zurückerstatten.

* Der Bestellstatus wird geschlossen.

<u>Tatsächliche Ergebnisse</u>:

* Es gibt keine Möglichkeit, die Belohnungspunkte zurückzuerstatten.

* Der Bestellstatus lautet **[!UICONTROL Completed]**.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
