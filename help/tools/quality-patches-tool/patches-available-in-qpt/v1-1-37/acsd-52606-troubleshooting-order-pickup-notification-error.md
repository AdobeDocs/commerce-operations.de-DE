---
title: 'ACSD-52606: Fehlermeldung, wenn der Benutzer auf „Bestellung wird abgeholt“ klickt'
description: Wenden Sie den Patch ACSD-52606 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Fehlermeldung angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52606: Fehlermeldung, wenn der Benutzer auf „Bestellung wird abgeholt“ klickt

Der Patch von ACSD-52606 behebt das Problem, dass eine Fehlermeldung *Ihre Bestellung ist nicht abholbereit* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-52606. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Fehlermeldung *Ihre Bestellung ist nicht abholbereit* wird auf dem Bildschirm angezeigt, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]** klickt.

<u>Voraussetzungen</u>:

Inventarmodule sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Neue Instanz installieren.
1. Erstellen Sie eine neue Quelle und einen neuen Lagerbestand.
1. Weisen Sie die neue Quelle der Standard-Website zu.
1. Abholort für die neu erstellte Quelle aktivieren.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** und aktivieren Sie **[!UICONTROL In-Store Delivery]**.
1. Erstellen Sie ein *Auf Lager* einfaches Produkt mit *QTY=0* für alle Lager und *[!UICONTROL Manage Stock = No]* und weisen Sie es beiden Quellen zu.
1. Erstellen Sie eine Bestellung über das Frontend mit dem im vorherigen Schritt erstellten Produkt, wobei Sie *[!UICONTROL In-Store Pickup]* als Versandmethode auswählen.
1. Gehen Sie in Admin zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Klicken Sie auf **[!UICONTROL Notify order is ready for pickup]**.

<u>Erwartete Ergebnisse</u>:

Sie werden ohne Fehler benachrichtigt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten folgende Fehlermeldung: *Ihre Bestellung ist nicht abholbereit*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
