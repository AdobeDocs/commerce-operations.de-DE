---
title: 'ACSD-46770: Bestellbestätigungs-E-Mail wird gesendet, auch wenn [!UICONTROL Email Order Confirmation] deaktiviert ist'
description: Wenden Sie den Patch ACSD-46770 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellbestätigungs-E-Mails gesendet werden, selbst wenn [!UICONTROL Email Order Confirmation] nicht ausgewählt ist.
feature: Communications, Orders
role: Admin
exl-id: d25ca121-7551-417c-b598-d8ed3a3da969
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-46770: Bestellbestätigungs-E-Mail wird gesendet, auch wenn **[!UICONTROL Email Order Confirmation]** deaktiviert ist

Der Patch ACSD-46770 behebt das Problem, dass Bestellungen über die REST-API als Gastbenutzer platziert werden können, selbst wenn **[!UICONTROL Email Order Confirmation]** nicht ausgewählt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-46770. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Bestellbestätigungs-E-Mail wird auch dann gesendet, wenn **[!UICONTROL Email Order Confirmation]** nicht ausgewählt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Order]** und klicken Sie auf **[!UICONTROL Create New Order]**.
1. Wählen Sie den Kunden aus, fügen Sie die Produkte zur Bestellung hinzu, geben Sie die Adresse ein und wählen Sie die Versand- und Zahlungsmethoden aus.
1. Deaktivieren Sie vor dem Senden der Bestellung das Kontrollkästchen **[!UICONTROL Email Order confirmation]** .
1. Klicken Sie auf **[!UICONTROL Submit Order]** , um die Bestellung zu erstellen.

<u>Erwartete Ergebnisse</u>:

Wenn die **[!UICONTROL Email Order Confirmation]** nicht ausgewählt ist, sollte keine E-Mail zur Bestellbestätigung gesendet werden.

<u>Tatsächliche Ergebnisse</u>:

Eine Bestätigungs-E-Mail für die Bestellung wird unabhängig vom nicht ausgewählten Kontrollkästchen **[!UICONTROL Email Order Confirmation]** gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
