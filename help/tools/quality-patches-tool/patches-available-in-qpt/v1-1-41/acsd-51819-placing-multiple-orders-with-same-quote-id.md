---
title: "ACSD-51819: Platzierung mehrerer Bestellungen mit einer einzigen Anführungszeichen-ID"
description: Wenden Sie den Patch ACSD-51819 an, um das Adobe Commerce-Problem zu beheben, bei dem mehrere Bestellungen über dieselbe Angebots-ID platziert werden können.
feature: Orders, Checkout
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51819: Mehrere Bestellungen mit einer einzigen Anführungszeichen-ID platzieren

Der Patch ACSD-51819 behebt das Problem, dass mehrere Bestellungen über dieselbe Anführungszeichen-ID platziert werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-51819. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es können mehrere Bestellungen mit derselben Angebots-ID platziert werden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Benutzer an.
1. Fügen Sie Artikel zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Wählen Sie eine beliebige Zahlungsmethode aus, klicken Sie jedoch nicht auf die Schaltfläche **[!UICONTROL Place Order]** .
1. Melden Sie sich bei demselben Konto in einem anderen Browser an.
1. Fahren Sie mit denselben Elementen fort, ohne auf die Schaltfläche **[!UICONTROL Place Order]** zu klicken.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Place Order]** in beiden Systemen gleichzeitig.
1. Validieren Sie die Bestellungen in beiden Browsern.

<u>Erwartete Ergebnisse</u>:

Nur die erste von einem Browser aufgegebene Bestellung wurde erfolgreich verarbeitet.

<u>Tatsächliche Ergebnisse</u>:

Bestellungen wurden in beiden Browsern platziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
