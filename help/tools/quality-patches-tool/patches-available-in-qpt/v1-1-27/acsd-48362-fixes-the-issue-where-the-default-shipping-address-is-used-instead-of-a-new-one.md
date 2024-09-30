---
title: 'ACSD-48362: Die standardmäßige Versandadresse wird anstelle einer neuen verwendet.'
description: Wenden Sie den Patch ACSD-48362 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Platzieren einer Bestellung mit einem verhandelbaren Angebot die standardmäßige Versandadresse anstelle einer neuen verwendet wird.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362: Die standardmäßige Versandadresse wird anstelle einer neuen verwendet.

Der Patch ACSD-48362 behebt das Problem, bei dem bei der Bestellung mit einem verhandelbaren Angebot anstelle der neu hinzugefügten Adresse die standardmäßige Versandadresse verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48362. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei Bestellung mit einem verhandelbaren Angebot wird anstelle der neu hinzugefügten Lieferadresse die Standard-Lieferadresse verwendet.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie das Anführungszeichen B2B, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]** navigieren.
1. Melden Sie sich als Unternehmensbenutzer an.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Gehen Sie zur Warenkorbseite und fordern Sie ein Angebot an.
1. Wählen Sie auf der Seite &quot;**[!UICONTROL My Quotes]**&quot;des Kunden das soeben erstellte Angebot aus.
1. Gehen Sie zum Abschnitt &quot;**[!UICONTROL Shipping Information]**&quot; der Anführungsseite des Kunden.
   * Klicken Sie auf &quot;**[!UICONTROL Add New Address]**&quot;, füllen Sie das Formular aus und speichern Sie die Adresse (wählen Sie nicht &quot;**[!UICONTROL Use as my default billing address]**&quot; oder &quot;**[!UICONTROL Use as my default shipping address]**&quot;).
1. Klicken Sie auf der Anführungsseite des Kunden auf **[!UICONTROL Send for Review]**.
1. Navigieren Sie zum Adobe Commerce-Administrator als Administrator, öffnen Sie das soeben erstellte Angebot und klicken Sie auf **[!UICONTROL Send]**.
1. Gehen Sie nun zur Anführungsseite des Kunden, aktualisieren Sie die Seite und klicken Sie auf **[!UICONTROL Proceed to Checkout]**.
1. Auf der Checkout-Seite zeigen die Daten die standardmäßige Lieferadresse an, selbst wenn die neue Lieferadresse ausgewählt ist.
1. Klicken Sie auf **[!UICONTROL Continue]** und platzieren Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

Die Bestellung sollte die neue Adresse verwenden, ohne die standardmäßige Versandadresse auf der Checkout-Seite erneut auszuwählen.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird mit der standardmäßigen Lieferadresse aufgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
