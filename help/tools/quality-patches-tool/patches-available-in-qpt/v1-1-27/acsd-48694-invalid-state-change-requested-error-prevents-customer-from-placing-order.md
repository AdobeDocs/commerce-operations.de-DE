---
title: "ACSD-48694: Ungültiger Statusänderungsfehler verhindert, dass der Kunde eine Bestellung aufgibt."
description: Wenden Sie den Patch ACSD-48694 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *Ungültige Statusänderung angefordert* verhindert, dass ein Kunde eine Bestellung aufgibt.
feature: Admin Workspace, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694: *Ungültige Statusänderung angefordert* -Fehler verhindert, dass der Kunde eine Bestellung aufgibt

Der Patch ACSD-48694 behebt das Problem, bei dem die Fehlermeldung *Ungültige Statusänderung angefordert* verhindert, dass ein Kunde eine Bestellung aufgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-48694. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Fehler *Ungültige Statusänderung angefordert* verhindert, dass ein Kunde eine Bestellung aufgibt.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie eine leichte Verzögerung während der `/estimate-shipping-methods` -Anfrage hinzu, indem Sie eine `sleep()` bei `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` -Funktion einbeziehen. Daher wird die `/estimate-shipping-methods` -Anfrage nach dem `/shipping-information` ausgeführt, wenn Sie vom Versandschritt zum Zahlungsschritt beim Checkout gehen.
1. Konfigurieren Sie die Sitzung so, dass [!DNL Redis] mit der Einstellung *disable_locking: 1* verwendet wird.
1. Öffnen Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** und aktivieren Sie *[!UICONTROL Persistent Shopping Cart]*.
1. Melden Sie sich als Kunde an und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Lassen Sie die Kundensitzung ablaufen. Persistentes Cookie und der Warenkorb bleiben weiterhin bestehen.
1. Gehen Sie nun zum Checkout, fügen Sie die Lieferadresse hinzu und navigieren Sie zum Zahlungsabschnitt.
1. Gehen Sie zurück zur Startseite oder einer anderen Seite und melden Sie sich mit dem Kundenkonto an.
1. Lassen Sie die Sitzung erneut ablaufen.
1. Gehen Sie jetzt direkt zur Checkout-Seite und navigieren Sie zum Zahlungsschritt.
1. Versuchen Sie, die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

* Es gibt keinen Fehler.
* Die Bestellung wurde erfolgreich platziert und eine *Dankeseite* wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler *Ungültige Statusänderung angefordert* wird angezeigt, aber die Reihenfolge wird platziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
