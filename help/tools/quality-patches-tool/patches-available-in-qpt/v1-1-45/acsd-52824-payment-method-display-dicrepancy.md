---
title: 'ACSD-52824: Deaktivierte Zahlungsmethoden für Firmenkunden angezeigt'
description: Wenden Sie den Patch ACSD-52824 an, um das Adobe Commerce-Problem zu beheben [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay]  bei dem Zahlungsmethoden für Unternehmenskunden angezeigt werden, obwohl sie in den Unternehmenseinstellungen deaktiviert sind.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824: Deaktivierte Zahlungsmethoden für Firmenkunden angezeigt

Mit dem Patch ACSD-52824 wird das Problem behoben, dass [!DNL PayPal Express]-, [!DNL Google Pay]- und [!DNL Apple Pay]-Zahlungsmethoden für Unternehmenskunden angezeigt werden, obwohl sie in den Unternehmenseinstellungen deaktiviert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-52824. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Für Firmenkunden werden deaktivierte Zahlungsmethoden angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren und aktivieren Sie [!DNL PayPal Express Checkout]. Navigieren Sie zu **[!UICONTROL Basic Settings]** und wählen Sie **[!DNL PayPal Express Checkout]** aus. Legen Sie für die Option **[!UICONTROL Display on Shopping Cart]** &quot;*&quot;*.
1. Konfigurieren Sie [!DNL Braintree] und aktivieren Sie [!DNL Apple Pay] und [!DNL Google Pay] über [!DNL Braintree].
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und erstellen Sie eine neue Firma.
1. Klicken Sie auf **[!UICONTROL Advanced Settings]**, suchen Sie die **[!UICONTROL Applicable Payment Methods]** und wählen Sie **[!UICONTROL Selected Payment Methods]**.
1. Wählen Sie unter **[!UICONTROL Selected Payment Methods]** die Zahlungsmethoden aus, die aktiviert und nicht mit *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* oder *[!DNL Google Pay]* verknüpft sind. Wählen Sie beispielsweise **[!UICONTROL Check/Money Order]** aus.
1. Erstellen Sie nach Auswahl der entsprechenden Zahlungsmethoden einen neuen Kunden und verknüpfen Sie ihn mit dem zuvor erstellten Unternehmen.
1. Melden Sie sich bei dem mit dem Unternehmen verbundenen Kundenkonto an und fahren Sie mit dem Hinzufügen von Artikeln zum Warenkorb fort.
1. Achten Sie beim Checkout auf den Mini-Warenkorb, den Warenkorb und den Zahlungsschritt.

<u>Erwartete Ergebnisse</u>:

Zahlungsoptionen von [!DNL PayPal] und [!DNL Braintree] sind im Mini-Warenkorb und Warenkorb nicht sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Zahlungsoptionen von [!DNL PayPal] und [!DNL Braintree] bleiben im Mini-Warenkorb und im Warenkorb sichtbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
