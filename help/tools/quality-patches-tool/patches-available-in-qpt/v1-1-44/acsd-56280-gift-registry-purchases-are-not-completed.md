---
title: "ACSD-56280: Geschenkkäufe in der Registrierung sind nicht abgeschlossen."
description: Wenden Sie den Patch ACSD-56280 an, um das Adobe Commerce-Problem zu beheben, bei dem die Käufe der Geschenkregistrierung nicht abgeschlossen sind.
feature: Checkout
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-56280: Geschenkkäufe in der Registrierung sind nicht abgeschlossen

Der Patch ACSD-56280 behebt das Problem, dass die Käufe der Geschenkregistrierung nicht abgeschlossen sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56280. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Käufe der Geschenkregistrierung sind noch nicht abgeschlossen.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an und fügen Sie eine **[!UICONTROL product]** zur Geschenkregistrierung hinzu.
1. Geben Sie den Link zur Geschenkregistrierung frei.
1. Öffnen Sie den Link zur Geschenkregistrierung in einem anderen Browser/Inkognito-Fenster.
1. Fügen Sie die Menge hinzu und fügen Sie die Artikel zum Warenkorb hinzu.
1. Klicken Sie auf &quot;**[!UICONTROL Checkout Page]**&quot;, wählen Sie &quot;**[!UICONTROL shipping method]**&quot;(Da die Versandadresse bereits ausgewählt ist, wird sie vom Registrierenden bereitgestellt).
1. Wählen Sie die Zahlungsmethode aus.
1. Klicken Sie auf die Schaltfläche Bestellung platzieren .

<u>Erwartete Ergebnisse</u>:

Die Bestellung sollte aufgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird nicht platziert, und der angezeigte Fehler lautet `Call to a member function getUpdatedQty() on null`.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
