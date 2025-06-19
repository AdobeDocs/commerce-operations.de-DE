---
title: 'ACSD-55610: Teilweise stornierte Bestellung hat falschen Rabattbetrag'
description: Wenden Sie den Patch ACSD-55610 an, um das Adobe Commerce-Problem zu beheben, bei dem eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55610: Teilweise stornierte Bestellung hat falschen Rabattbetrag

Mit dem Patch ACSD-55610 wird das Problem behoben, dass eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.43 installiert ist. Die Patch-ID ist ACSD-55610. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine teilweise stornierte Bestellung hat einen falschen Rabattbetrag.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Preisregel für den Warenkorb.

   * *[!UICONTROL Rule Name]*: *Winterverkauf*
   * *[!UICONTROL Active]* = *Ja*
   * *[!UICONTROL Websites]* = *Haupt-Website*
   * Wählen Sie alle Kundengruppen.
   * Wählen Sie einen bestimmten Gutschein aus.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Zwischensumme(exkl. (Steuer) ist gleich oder größer als 75*
   * *[!UICONTROL Percent of product price discount]* anwenden.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Ja*

1. Erstellen Sie drei Produkte mit Preisen von 100.
1. Die drei Produkte zum Warenkorb hinzufügen.
1. Wenden Sie den Gutschein an.
1. Bestellung aufgeben.
1. Rechnen Sie einen Artikel der Bestellung aus und versenden Sie ihn.
1. Bricht die beiden anderen Elemente ab.
1. Überprüfen Sie die Spalte `base_discount_canceled` .

<u>Erwartete Ergebnisse</u>:

Der Rabattbetrag in `base_discount_cancelled` wird korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die `base_discount_cancelled` ist falsch.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
