---
title: "ACSD-53658: **[!UICONTROL Recently Viewed Product]** Daten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert."
description: Wenden Sie den Patch ACSD-53658 an, um das Adobe Commerce-Problem zu beheben, bei dem **[!UICONTROL Recently Viewed Product]**-Daten in der Store-Ansicht nicht ordnungsgemäß aktualisiert werden.
feature: CMS, Personalization
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** Daten wurden in der Store-Ansicht nicht ordnungsgemäß aktualisiert

Der Patch ACSD-53658 behebt das Problem, dass **[!UICONTROL Recently Viewed Product]** -Daten in der Store-Ansicht nicht ordnungsgemäß aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-53658. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die **[!UICONTROL Recently Viewed Product]** -Daten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Bedienfeld an.
1. Erstellen Sie eine zweite Store-Ansicht für die Standardwebsite.
1. Erstellen Sie ein einfaches Produkt.
1. Legen Sie einen anderen Produktnamen für die neue Store-Ansicht fest.
1. Erstellen Sie ein Widget **[!UICONTROL Recently Viewed Product]** .
1. Konfigurieren Sie dieses Widget für die Anzeige auf der Startseite.
1. Öffnen Sie die Produktseite in der Storefront in der standardmäßigen Store-Ansicht.
1. Öffnen Sie die Startseite.
1. Wechseln Sie mithilfe des Store-Switchers zur zweiten Store-Ansicht.

<u>Erwartete Ergebnisse</u>:

Der Produktname wird im Widget aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Der Produktname wird im Widget nicht aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
