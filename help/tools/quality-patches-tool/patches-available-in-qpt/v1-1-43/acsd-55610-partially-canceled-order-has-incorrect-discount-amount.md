---
title: "ACSD-55610: Teilweise stornierte Bestellung hat falschen Rabattbetrag"
description: Wenden Sie den Patch ACSD-55610 an, um das Adobe Commerce-Problem zu beheben, bei dem eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-55610: Teilweise stornierte Bestellung hat falschen Rabattbetrag

Der Patch ACSD-55610 behebt das Problem, dass eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.43 installiert ist. Die Patch-ID ist ACSD-55610. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine teilweise stornierte Bestellung hat einen falschen Rabattbetrag.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Preisregel für den Warenkorb.

   * *[!UICONTROL Rule Name]*: *Winterverkauf*
   * *[!UICONTROL Active]* = *Ja*
   * *[!UICONTROL Websites]* = *Main website*
   * Wählen Sie alle Kundengruppen aus.
   * Wählen Sie einen bestimmten Gutschein aus.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotal(Excl. Steuern) gleich oder größer als 75*
   * Wenden Sie *[!UICONTROL Percent of product price discount]* an.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Ja*

1. Erstellen Sie drei Produkte mit Preisen von 100.
1. Fügen Sie die drei Produkte zum Warenkorb hinzu.
1. Wenden Sie den Gutschein an.
1. Platzieren Sie die Bestellung.
1. Invotieren Sie einen Artikel der Bestellung und schicken Sie ihn.
1. Abbrechen der beiden anderen Elemente.
1. Überprüfen Sie die Spalte `base_discount_canceled` .

<u>Erwartete Ergebnisse</u>:

Der Rabattbetrag in `base_discount_cancelled` spiegelt korrekt wider.

<u>Tatsächliche Ergebnisse</u>:

Die `base_discount_cancelled` ist nicht korrekt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
