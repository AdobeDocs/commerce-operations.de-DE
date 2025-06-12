---
title: 'ACSD-49433: Standardwert, der als Zwischensumme im Warenkorb für die Geschenkkarte angezeigt wird“'
description: Wenden Sie den Patch ACSD-49433 an, um das Adobe Commerce-Problem zu beheben, bei dem der Standardbetrag als Zwischensumme im Warenkorb für Geschenkkarten mit einem offenen Betrag angezeigt wird.
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
exl-id: 22691e35-0491-4935-8e7c-148900706491
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-49433: Standardwert, der als Zwischensumme im Warenkorb für Geschenkkarte angezeigt wird

Der Patch ACSD-49433 behebt das Problem, dass der Standardbetrag als Zwischensumme im Warenkorb für die Geschenkkarte mit einem offenen Betrag angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49433. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Standardbetrag wird als Zwischensumme im Warenkorb für die Geschenkkarte mit einem offenen Betrag angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Geschenkkarte.
1. Stellen Sie sicher, dass der offene Betrag auf *[!UICONTROL Yes]* (zwischen 50 und 500 $) eingestellt ist.
1. Gehen Sie zum [!UICONTROL Gift Card] Produkt auf der Storefront und wählen Sie einen anderen Betrag aus der Dropdown-Liste.
1. Geben Sie 100 USD als Betrag in USD an.
1. Füllen Sie andere Felder aus und fügen Sie sie zum Warenkorb hinzu.
1. Gehen Sie zum Mini-Warenkorb oder zur Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Die Zwischensumme zeigt den Betrag an, den der Benutzer eingegeben hat.

<u>Tatsächliche Ergebnisse</u>:

Die Zwischensumme zeigt den standardmäßigen Geschenkkartenbetrag an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
