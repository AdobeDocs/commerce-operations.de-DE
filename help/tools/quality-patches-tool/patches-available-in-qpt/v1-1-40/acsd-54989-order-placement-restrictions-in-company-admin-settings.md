---
title: 'ACSD-54989: Unternehmensadministrator kann keine Bestellung aufgeben, wenn [!UICONTROL Enable Purchase Orders] auf "Ja"und [!UICONTROL Purchase Order] auf "Nein"gesetzt ist'
description: Wenden Sie den Patch ACSD-54989 an, um das Adobe Commerce-Problem zu beheben, bei dem Unternehmensadministratoren keine Bestellungen aufgeben können, wenn [!UICONTROL Enable Purchase Orders] auf Ja und [!UICONTROL Purchase Order] auf Nein gesetzt ist.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-54989: Der Unternehmensadministrator kann keine Bestellung aufgeben, wenn *[!UICONTROL Enable Purchase Orders]* auf *Ja* und *[!UICONTROL Purchase Order]* auf *Nein* gesetzt ist

Der Patch ACSD-54989 behebt das Problem, dass Bestellungen nicht platziert werden können, wenn **[!UICONTROL Enable Purchase Orders]** auf *Ja* und **[!UICONTROL Purchase Order]** auf *Nein* gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54989. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Unternehmensadministratoren können keine Bestellungen aufgeben, wenn **[!UICONTROL Enable Purchase Orders]** auf *Ja* und **Bestellung** auf *Nein* gesetzt ist.

<u>Voraussetzungen</u>:

Installieren Sie die [!DNL B2B] -Module.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie Unternehmen und lassen Sie [!UICONTROL **Order Approval Configuration]* > **[!UICONTROL Purchase Order**] = *Nein*.
1. Erstellen Sie ein einfaches Produkt mit einem Preis von 100.
1. Erstellen Sie ein neues Unternehmen über den Administrator.
1. Setzen Sie [!UICONTROL **Kaufaufträge aktivieren**] auf *Ja*.
1. Melden Sie sich als Unternehmensadministrator an der Storefront an.
1. Fügen Sie das erstellte einfache Produkt zum Warenkorb hinzu.
1. Fahren Sie mit der Checkout-Seite fort und klicken Sie auf **[!UICONTROL Place Order]** , um den Kauf abzuschließen.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung erfolgreich aufgeben.

<u>Tatsächliche Ergebnisse</u>:

Die Seite **[!UICONTROL My Account]** wird geöffnet und die Bestellung wird nicht platziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
