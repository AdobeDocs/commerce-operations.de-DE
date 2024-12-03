---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] Zahlungsmethode wird im Checkout-Workflow automatisch deaktiviert'
description: Wenden Sie den Patch ACSD-61134 an, um das Adobe Commerce-Problem zu beheben, bei dem die Zahlungsmethode *[!UICONTROL Braintree Vault]* im Checkout-Workflow automatisch deaktiviert wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem er das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert.
feature: Checkout
role: Admin, Developer
source-git-commit: 459f1e70464e4df04dc306ee403730798f0f9b9e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]* Zahlungsmethode wird im Checkout-Workflow automatisch deaktiviert

Der Patch ACSD-61134 behebt das Problem, dass die Zahlungsmethode *[!UICONTROL Braintree Vault]* im Checkout-Workflow automatisch deaktiviert wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61134. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.7-Beta1 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

*[!UICONTROL Braintree Vault]* Die Zahlungsmethode wird im Checkout-Workflow automatisch deaktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie die Zahlungsmethode *[!DNL Braintree]* mit aktiviertem *[!UICONTROL Vault]*.
1. Checkout und speichern Sie eine Karte im *[!UICONTROL Vault]*.
1. Sehen Sie sich ein anderes Produkt an.
1. Fügen Sie auf der Seite *[!UICONTROL Shipping]* eine neue Versandadresse hinzu, damit Sie zwei Adressen auswählen können.
1. Wählen Sie auf der Seite *[!UICONTROL Payment]* Ihre Zahlungsmethode aus und klicken Sie auf **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Erwartete Ergebnisse</u>:

Die ausgewählte Zahlungsmethode bleibt ausgewählt.

<u>Tatsächliche Ergebnisse</u>:

Die ausgewählte Zahlungsmethode ist deaktiviert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

