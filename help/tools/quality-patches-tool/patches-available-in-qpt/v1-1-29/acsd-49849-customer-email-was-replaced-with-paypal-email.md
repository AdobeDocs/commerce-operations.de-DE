---
title: 'ACSD-49849: Kunden-E-Mail wurde durch PayPal-E-Mail ersetzt'
description: Adobe Commerce Wenden Sie den ACSD-49849 Patch an, um das Problem zu beheben, bei dem die Kunden-E-Mail durch die PayPal-E-Mail ersetzt wurde, wenn Sie über GraphQL eine Bestellung mit PayPal Express aufgeben.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849: Kunden-E-Mail wird durch [!DNL PayPal] E-Mail ersetzt

Mit dem Patch ACSD-49849 wird das Problem behoben, dass die E-Mail-Adresse eines Kunden durch eine [!DNL PayPal's]-E-Mail ersetzt wird, wenn eine Bestellung über GraphQL bei [!DNL PayPal Express] aufgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die E-Mail-Adresse eines Kunden wird durch eine [!DNL PayPal's]-E-Mail ersetzt, wenn über GraphQL eine Bestellung bei [!DNL PayPal Express] aufgegeben wird.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Aktivieren und konfigurieren Sie [!DNL PayPal Express] und legen Sie **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** fest.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein einfaches Produkt.
1. Schließen Sie den Gast-Checkout mit GraphQL ab. Weitere Informationen finden Sie im Tutorial zum [GraphQL-Checkout](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in der Dokumentation für Adobe Commerce-Entwickler.
1. Verwenden Sie [!DNL PayPal Express] als Zahlungsmethode.
1. Beachten Sie die E-Mail-Adresse, die Sie in dem Schritt verwendet haben, in dem Sie [Ihre E-Mail für den Warenkorb einrichten](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) in der Entwicklerdokumentation von Adobe Commerce.
1. Nachdem die Bestellung aufgegeben wurde, wenden Sie sich an den Adobe Commerce-Administrator und überprüfen Sie die E-Mail in der erstellten Bestellung.

<u>Erwartete Ergebnisse</u>:

Die E-Mail entspricht der E-Mail-Adresse, die beim Auschecken festgelegt wurde.

<u>Tatsächliche Ergebnisse</u>:

Die E-Mail-Adresse, die während des Checkouts festgelegt wurde, wird durch die E-Mail-Adresse überschrieben, die im [!DNL PayPal] festgelegt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
