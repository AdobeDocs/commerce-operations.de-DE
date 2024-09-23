---
title: '''ACSD-52606: Fehlermeldung angezeigt, wenn der Benutzer auf "Auftrag für Abruf benachrichtigen"klickt'
description: Wenden Sie den Patch ACSD-52606 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Fehlermeldung angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.
feature: Orders, User Account
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52606: Fehlermeldung angezeigt, wenn der Benutzer auf &quot;Auftrag wird für Abruf bereit benachrichtigt&quot;klickt

Der Patch ACSD-52606 behebt das Problem, bei dem die Fehlermeldung *Ihre Bestellung ist nicht bereit zum Aufheben* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-52606. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Fehlermeldung *Ihre Bestellung ist noch nicht bereit für die Abholung* wird auf dem Bildschirm angezeigt, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.

<u>Voraussetzungen</u>:

Inventarmodule werden installiert.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie eine neue Instanz.
1. Erstellen Sie eine neue Quelle und ein neues Lager.
1. Weisen Sie die neue Quelle der Standardwebsite zu.
1. Aktivieren Sie den Abholspeicherort für die neu erstellte Quelle.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** und aktivieren Sie **[!UICONTROL In-Store Delivery]**.
1. Erstellen Sie ein einfaches Produkt *In Stock* mit *QTY=0* für alle Bestände und *[!UICONTROL Manage Stock = No]* und weisen Sie es beiden Quellen zu.
1. Erstellen Sie eine Bestellung vom Frontend mit dem im vorherigen Schritt erstellten Produkt und wählen Sie als Versandmethode *[!UICONTROL In-Store Pickup]* aus.
1. Gehen Sie in Admin zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Klicken Sie auf **[!UICONTROL Notify order is ready for pickup]**.

<u>Erwartete Ergebnisse</u>:

Sie werden ohne Fehler benachrichtigt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Ihre Bestellung ist nicht bereit zur Übernahme*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
