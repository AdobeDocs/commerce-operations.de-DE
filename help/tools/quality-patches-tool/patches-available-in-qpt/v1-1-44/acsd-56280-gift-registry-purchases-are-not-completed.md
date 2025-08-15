---
title: 'ACSD-56280: Käufe im Geschenkgutschein werden nicht abgeschlossen'
description: Wenden Sie den Patch ACSD-56280 an, um das Adobe Commerce-Problem zu beheben, bei dem der Kauf von Geschenkgutscheinen nicht abgeschlossen ist
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-56280: Käufe im Geschenkgutschein werden nicht abgeschlossen

>[!NOTE]
>
>Dieser Patch wurde durch [ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md) ersetzt.

Mit dem Patch ACSD-56280 wird das Problem behoben, dass der Kauf von Geschenkregistrierungen nicht abgeschlossen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56280. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Einkäufe im Geschenkgutschein werden nicht abgeschlossen.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Kunde an und fügen Sie eine **[!UICONTROL product]** zur Geschenkregistrierung hinzu.
1. Geben Sie den Link zur Geschenkregistrierung frei.
1. Öffnen Sie den Link für die Geschenkregistrierung in einem anderen Browser-/Inkognito-Fenster.
1. Fügen Sie die Menge hinzu und fügen Sie die Artikel zum Warenkorb hinzu.
1. Navigieren Sie zur **[!UICONTROL Checkout Page]** und wählen Sie **[!UICONTROL shipping method]**(da die Versandadresse bereits ausgewählt und vom Registrierenden angegeben ist).
1. Wählen Sie die Zahlungsmethode aus.
1. Klicken Sie auf die Schaltfläche Bestellung aufgeben .

<u>Erwartete Ergebnisse</u>:

Die Bestellung sollte aufgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht aufgegeben und der angezeigte Fehler lautet `Call to a member function getUpdatedQty() on null`.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
