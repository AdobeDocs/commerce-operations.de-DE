---
title: "ACSD-55241: **Verwendet** und **Verwendete Zeiten** Attribute zeigen falsche Werte für generierte Gutscheine an."
description: Wenden Sie den Patch ACSD-55241 an, um das Adobe Commerce-Problem zu beheben, bei dem die Attribute **Verwendet** und **Verwendete Zeiten** falsche Werte für generierte Gutscheine anzeigen
feature: Price Rules
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241: Attribute **Verwendet** und **Verwendete Zeiten** zeigen falsche Werte für generierte Gutscheine an

Der Patch ACSD-55241 behebt das Problem, dass die Attribute **Verwendet** und **Verwendet mal** falsche Werte für generierte Gutscheine anzeigen. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.47 installiert ist. Die Patch-ID ist ACSD-55241. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Attribute **Verwendet** und **Verwendet mal** zeigen falsche Werte für generierte Gutscheine an.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie **[!UICONTROL Cart Price Rules]** von **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** und fügen Sie alle Bedingungen hinzu, die beim Bestellen einer Bestellung übereinstimmen (Beispiel: Zwischensumme größer als *5$*)

   * Wenden Sie einen Rabatt an.
   * Wählen Sie **[!UICONTROL Auto Coupon]** aus.
   * Es werden einige Coupon-Codes aus **Couponcodes verwalten** generiert.
   * Neuindizieren und leeren Sie den Cache.

1. Erstellen Sie eine **[!UICONTROL customer account]** und melden Sie sich im Frontend an.
1. Fügen Sie ein Produkt mit mehr als *2* Mengen im Warenkorb hinzu und wenden Sie einen Gutschein an.
1. Klicken Sie auf **[!UICONTROL Check Out with Multiple Addresses]**.
1. Wählen Sie für jede Menge eine separate Adresse aus, geben Sie die Bestellung auf und schließen Sie den Checkout-Prozess ab.
1. Beobachten Sie die Bestellsumme vom Administrator und sehen Sie sich den angewendeten Rabatt an.
1. Platzieren Sie eine weitere Bestellung mit einem anderen Gutschein.
1. Führen Sie den Befehl `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` aus, um die Verwendung des Gutscheincodes zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Die richtige Anzahl sollte in den Spalten **Verwendete Zeit** und **Verwendet** mit dem Wert **Ja** für **[!UICONTROL manage coupon]** in den Spalten **[!UICONTROL cart price rule]** im Admin angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Anzahl der verwendeten Coupons-Codes wird in der Spalte **Verwendete Zeit** im Coupons-Raster nicht aktualisiert, und die Spalte **Verwendet** zeigt den Wert *Nein* an, wenn Sie eine Bestellung mit mehreren Versandadressen aufgeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
