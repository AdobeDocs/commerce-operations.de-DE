---
title: 'ACSD-46770: E-Mail zur Bestellbestätigung wird gesendet, auch wenn [!UICONTROL Email Order Confirmation] deaktiviert ist'
description: Wenden Sie den Patch ACSD-46770 an, um das Problem in Adobe Commerce zu beheben, bei dem E-Mails zur Bestellbestätigung gesendet werden, auch wenn [!UICONTROL Email Order Confirmation] nicht ausgewählt ist.
feature: Communications, Orders
role: Admin
exl-id: d25ca121-7551-417c-b598-d8ed3a3da969
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-46770: E-Mail zur Bestellbestätigung wird gesendet, auch wenn **[!UICONTROL Email Order Confirmation]** deaktiviert ist

Mit dem Patch ACSD-46770 wird das Problem behoben, dass Bestellungen als Gastbenutzer über die REST-API aufgegeben werden können, auch wenn die **[!UICONTROL Email Order Confirmation]** deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-46770. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine E-Mail zur Bestellbestätigung wird gesendet, auch wenn **[!UICONTROL Email Order Confirmation]** nicht ausgewählt ist.

<u>Schritte zur Reproduktion</u>:

1. Kundenkonto erstellen.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Order]** und klicken Sie auf **[!UICONTROL Create New Order]**.
1. Wählen Sie den Kunden aus, fügen Sie die Produkte zur Bestellung hinzu, geben Sie die Adresse ein und wählen Sie die Versand- und Zahlungsmethoden aus.
1. Deaktivieren Sie vor dem Absenden der Bestellung das Kontrollkästchen **[!UICONTROL Email Order confirmation]** .
1. Klicken Sie auf **[!UICONTROL Submit Order]** , um die Bestellung zu erstellen.

<u>Erwartete Ergebnisse</u>:

Eine E-Mail zur Bestellbestätigung sollte nicht gesendet werden, wenn die **[!UICONTROL Email Order Confirmation]** nicht ausgewählt ist.

<u>Tatsächliche Ergebnisse</u>:

Eine E-Mail zur Bestellbestätigung wird unabhängig vom deaktivierten **[!UICONTROL Email Order Confirmation]**-Kontrollkästchen gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
