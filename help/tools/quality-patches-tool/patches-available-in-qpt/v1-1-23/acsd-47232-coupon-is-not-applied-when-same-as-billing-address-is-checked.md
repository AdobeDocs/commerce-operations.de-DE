---
title: "ACSD-47232: Coupon wird nicht angewendet, wenn [!UICONTROL Same as Billing Address] aktiviert ist"
description: Wenden Sie den Patch ACSD-47232 an, um das Adobe Commerce-Problem zu beheben, bei dem Coupon nicht angewendet wird, wenn [!UICONTROL Same as Billing Address] aktiviert ist.
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: Gutschein wird nicht angewendet, wenn [!UICONTROL Same as Billing Address] aktiviert ist

Der Patch ACSD-47232 behebt das Problem, dass der Coupon nicht angewendet wird, wenn **[!UICONTROL Same as Billing Address]** aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47232. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Coupon wird nicht angewendet, wenn **[!UICONTROL Same as Billing Address]** aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Erstellen Sie ein einfaches Produkt mit Gewichtung = *8*.
1. Erstellen Sie einen neuen Kunden mit der standardmäßigen Abrechnungs- und Lieferadresse.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem Coupon.
   * Fügen Sie in den Abschnitten &quot;**[!UICONTROL Conditions]**&quot;den Wert &quot;*Gesamtgewicht&quot;oder größer als 5*&quot;hinzu.
1. Versuchen Sie, eine neue Bestellung in der [!UICONTROL Commerce] -Admin zu erstellen.
   * Verwenden des gerade erstellten Kunden
   * Produkt hinzufügen
   * Versuchen Sie, den Gutschein anzuwenden

<u>Erwartete Ergebnisse</u>:

Coupon wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten eine Fehlermeldung ähnlich der folgenden: *Der 123-Couponcode ist ungültig. Überprüfen Sie den Code und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
