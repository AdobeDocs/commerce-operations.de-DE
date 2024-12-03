---
title: 'ACSD-52824: Deaktivierte Zahlungsmethoden für Unternehmenskunden'
description: Wenden Sie den Patch ACSD-52824 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] Zahlungsmethoden für Unternehmenskunden angezeigt werden, obwohl sie in den Unternehmenseinstellungen deaktiviert wurden.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824: Deaktivierte Zahlungsmethoden für Unternehmenskunden

Der Patch ACSD-52824 behebt das Problem, dass die Zahlungsmethoden [!DNL PayPal Express], [!DNL Google Pay] und [!DNL Apple Pay] für Unternehmenskunden angezeigt werden, obwohl sie in den Unternehmenseinstellungen deaktiviert wurden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-52824. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Für Unternehmenskunden werden deaktivierte Zahlungsmethoden angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren und aktivieren Sie [!DNL PayPal Express Checkout]. Navigieren Sie zu **[!UICONTROL Basic Settings]** > wählen Sie **[!DNL PayPal Express Checkout]** aus und legen Sie die Option für **[!UICONTROL Display on Shopping Cart]** auf *Ja* fest.
1. Konfigurieren Sie [!DNL Braintree] und aktivieren Sie [!DNL Apple Pay] und [!DNL Google Pay] bis [!DNL Braintree].
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und erstellen Sie ein neues Unternehmen.
1. Klicken Sie auf **[!UICONTROL Advanced Settings]**, suchen Sie die **[!UICONTROL Applicable Payment Methods]** und wählen Sie **[!UICONTROL Selected Payment Methods]** aus.
1. Wählen Sie unter **[!UICONTROL Selected Payment Methods]** Zahlungsmethoden aus, die aktiviert sind und nicht mit *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* oder *[!DNL Google Pay]* verknüpft sind. Wählen Sie beispielsweise &quot;**[!UICONTROL Check/Money Order]**&quot;.
1. Erstellen Sie nach Auswahl der entsprechenden Zahlungsmethoden einen neuen Kunden und verbinden Sie ihn mit dem zuvor erstellten Unternehmen.
1. Melden Sie sich mit dem Kundenkonto an, das dem Unternehmen zugeordnet ist, und fahren Sie mit dem Hinzufügen von Artikeln zum Warenkorb fort.
1. Beachten Sie beim Checkout-Prozess den Mini-Warenkorb, den Warenkorb und den Zahlungsschritt.

<u>Erwartete Ergebnisse</u>:

Zahlungsoptionen von [!DNL PayPal] und [!DNL Braintree] sind nicht im Mini-Warenkorb und -Warenkorb sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Zahlungsoptionen von [!DNL PayPal] und [!DNL Braintree] bleiben im Mini-Warenkorb und im Warenkorb sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
