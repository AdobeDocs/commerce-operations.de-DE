---
title: 'ACSD-57588: Fehler bei der Verarbeitung der Regions-ID beim Versand an mehrere Adressen'
description: Wenden Sie den Patch ACSD-57588 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Versand einer Bestellung an mehrere Trigger während der Verarbeitung der Regions-ID ein Fehler auftritt.
feature: Orders, Shipping/Delivery
role: Admin, Developer
exl-id: 9a455d32-47d3-4d29-b12e-068bbee98f89
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57588: Fehler bei der Verarbeitung der Regions-ID beim Versand an mehrere Adressen

Mit dem Patch ACSD-57588 wird das Problem behoben, dass beim Versand einer Bestellung an mehrere Adressen Trigger während der Verarbeitung der Regions-ID einen Fehler ausgegeben haben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57588. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Fehler, der bei der Verarbeitung der Regions-ID beim Versand an mehrere Adressen ausgelöst wurde.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie die [!DNL Braintree] Zahlungsmethode.
1. Melden Sie sich als Kunde in der Storefront an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Anzeigen und Bearbeiten des Warenkorbs fort.
1. Fügen Sie während des Checkout-Prozesses mehrere *(z. B. UK, US* CA) hinzu und überprüfen Sie die Bestellung.
1. Wählen Sie auf der Checkout-Seite die Option Kreditkartenzahlung aus, geben Sie die erforderlichen Anmeldeinformationen ein und geben Sie die Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Bestellung kann erfolgreich aufgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
