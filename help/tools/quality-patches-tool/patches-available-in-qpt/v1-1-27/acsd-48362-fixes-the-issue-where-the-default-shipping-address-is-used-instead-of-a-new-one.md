---
title: 'ACSD-48362: Die Standard-Versandadresse wird anstelle einer neuen verwendet.'
description: Wenden Sie den Patch ACSD-48362 an, um das Adobe Commerce-Problem zu beheben, bei dem bei einer Bestellung mit einem verhandelbaren Angebot die standardmäßige Versandadresse anstelle einer neuen verwendet wird.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362: Die Standard-Versandadresse wird anstelle einer neuen verwendet

Mit dem Patch ACSD-48362 wird das Problem behoben, dass bei einer Bestellung mit einem verhandelbaren Angebot die Standard-Versandadresse anstelle der neu hinzugefügten Adresse verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48362. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die standardmäßige Lieferadresse wird anstelle der neu hinzugefügten Lieferadresse verwendet, wenn eine Bestellung mit einem verhandelbaren Angebot aufgegeben wird.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie das B2B-Angebot, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]** navigieren.
1. Melden Sie sich als Unternehmensbenutzer an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Gehen Sie zur Warenkorbseite und fordern Sie ein Angebot an.
1. Gehen Sie zur Seite **[!UICONTROL My Quotes]** des Kunden und wählen Sie das soeben erstellte Angebot aus.
1. Rufen Sie den Abschnitt **[!UICONTROL Shipping Information]** der Angebotsseite des Kunden auf.
   * Klicken Sie auf **[!UICONTROL Add New Address]**, füllen Sie das Formular aus und speichern Sie die Adresse (wählen Sie weder **[!UICONTROL Use as my default billing address]** noch **[!UICONTROL Use as my default shipping address]** aus).
1. Klicken Sie auf der Angebotsseite des Kunden auf **[!UICONTROL Send for Review]**.
1. Wechseln Sie zum Adobe Commerce-Administrator als Admin-Benutzer, öffnen Sie das soeben erstellte Angebot und klicken Sie auf **[!UICONTROL Send]**.
1. Gehen Sie nun zur Angebotsseite des Kunden, aktualisieren Sie die Seite und klicken Sie auf **[!UICONTROL Proceed to Checkout]**.
1. Auf der Kaufbestätigungsseite wird in den Daten die Standard-Versandadresse angezeigt, selbst wenn die neue Versandadresse ausgewählt ist.
1. Klicken Sie auf **[!UICONTROL Continue]** und geben Sie die Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Die Bestellung sollte die neue Adresse verwenden, ohne die Standardversandadresse auf der Kasse erneut auszuwählen.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird mit der Standard-Lieferadresse aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
