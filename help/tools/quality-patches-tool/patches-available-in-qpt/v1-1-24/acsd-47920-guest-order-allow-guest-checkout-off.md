---
title: "ACSD-47920: Ein Gastbenutzer kann Bestellungen über die REST-API auch dann aufgeben, wenn [!UICONTROL Allow Guest Checkout] deaktiviert ist."
description: Wenden Sie den Patch ACSD-47920 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellungen auch dann über die REST-API als Gastbenutzer platziert werden können, wenn die [!UICONTROL Allow Guest Checkout] deaktiviert ist.
feature: REST, Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920: Ein Gastbenutzer kann über die REST-API Bestellungen aufgeben, selbst wenn **[!UICONTROL Allow Guest Checkout]** deaktiviert ist.

Der Patch ACSD-47920 behebt das Problem, dass Bestellungen auch dann über die REST-API als Gastbenutzer platziert werden können, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47920. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bestellungen können auch dann über die Rest-API als Gastbenutzer platziert werden, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > und setzen Sie die **[!UICONTROL Allow Guest Checkout]** auf _Nein_.
1. Verwenden Sie die REST-API, um einem Warenkorb ein Produkt hinzuzufügen und eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Die Auschecken-API gibt den Fehler *[!UICONTROL Sorry, guest checkout is not available]* zurück, wenn **[!UICONTROL Allow Guest Checkout]** auf _Nein_ gesetzt ist.

<u>Tatsächliche Ergebnisse</u>:

Mit der Gastkasse-API kann eine Bestellung platziert werden, selbst wenn **[!UICONTROL Allow Guest Checkout]** auf _Nein_ gesetzt ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
