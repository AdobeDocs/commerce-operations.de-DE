---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] Zahlungsmethode im Checkout-Workflow automatisch deaktiviert'
description: Wenden Sie den Patch ACSD-61134 an, um das Adobe Commerce-Problem zu beheben, bei dem die Zahlungsmethode *[!UICONTROL Braintree Vault]* im Checkout-Workflow automatisch deaktiviert wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem er das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]* Zahlungsmethode im Checkout-Workflow automatisch deaktiviert

Mit dem Patch ACSD-61134 wird das Problem behoben, dass die *[!UICONTROL Braintree Vault]* Zahlungsmethode im Checkout-Workflow automatisch deaktiviert wird, wenn ein Käufer seine Rechnungsadresse aktualisiert, indem er das Kontrollkästchen *[!UICONTROL My billing and shipping address are the same]* deaktiviert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61134. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.7-beta1 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

*[!UICONTROL Braintree Vault]* Zahlungsmethode wird im Checkout-Workflow automatisch deaktiviert.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie die *[!DNL Braintree]* Zahlungsmethode mit aktiviertem *[!UICONTROL Vault]*.
1. Checken Sie aus und speichern Sie eine Karte im *[!UICONTROL Vault]*.
1. Checken Sie ein anderes Produkt aus.
1. Fügen Sie auf der Seite *[!UICONTROL Shipping]* eine neue Versandadresse hinzu, sodass Sie zwei Adressen zur Auswahl haben.
1. Wählen Sie auf der Seite *[!UICONTROL Payment]* Ihre Zahlungsmethode aus und klicken Sie auf **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Erwartete Ergebnisse</u>:

Die ausgewählte Zahlungsmethode bleibt ausgewählt.

<u>Tatsächliche Ergebnisse</u>:

Die ausgewählte Zahlungsmethode ist deaktiviert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
