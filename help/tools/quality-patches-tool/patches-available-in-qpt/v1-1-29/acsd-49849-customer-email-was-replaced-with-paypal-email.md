---
title: 'ACSD-49849: Kunden-E-Mail wurde durch PayPal-E-Mail ersetzt'
description: Wenden Sie den Patch ACSD-49849 an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail des Kunden bei der Bestellung mit PayPal Express über GraphQL durch PayPal-E-Mails ersetzt wurde.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849: Kunden-E-Mail wird durch [!DNL PayPal] E-Mail ersetzt

Der Patch ACSD-49849 behebt das Problem, dass die E-Mail eines Kunden bei der Bestellung mit [!DNL PayPal Express] über GraphQL durch eine [!DNL PayPal's] -E-Mail ersetzt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die E-Mail eines Kunden wird durch eine [!DNL PayPal's] -E-Mail ersetzt, wenn über GraphQL eine Bestellung bei [!DNL PayPal Express] aufgegeben wird.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Aktivieren und konfigurieren Sie [!DNL PayPal Express] und legen Sie **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** fest.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein einfaches Produkt.
1. Schließen Sie den Gast-Checkout mit GraphQL ab. Weitere Informationen finden Sie im Tutorial [GraphQL Checkout-Tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in der Adobe Commerce Developer Documentation.
1. Verwenden Sie [!DNL PayPal Express] als Zahlungsmethode.
1. Beachten Sie die E-Mail, die Sie in dem Schritt verwendet haben, in dem Sie Ihre E-Mail für den Warenkorb einrichten ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) in der Adobe Commerce Developer Documentation.[
1. Nachdem die Bestellung aufgegeben wurde, gehen Sie zum Adobe Commerce-Administrator und überprüfen Sie die E-Mail in der erstellten Reihenfolge.

<u>Erwartete Ergebnisse</u>:

Die E-Mail entspricht der beim Checkout festgelegten.

<u>Tatsächliche Ergebnisse</u>:

Die während des Auscheckens festgelegte E-Mail wird durch die im Konto [!DNL PayPal] festgelegte E-Mail überschrieben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
