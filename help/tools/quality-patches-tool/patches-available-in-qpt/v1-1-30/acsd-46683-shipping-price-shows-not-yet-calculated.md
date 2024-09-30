---
title: "ACSD-46683: Versandpreis zeigt *Noch nicht berechnet* an."
description: Wenden Sie den Patch ACSD-46683 an, um das Adobe Commerce-Problem zu beheben, bei dem der Versandpreis *Noch nicht berechnet* anzeigt.
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-46683: Versandpreis zeigt *Noch nicht berechnet* an

Der Patch ACSD-46683 behebt das Problem, dass der Versandpreis *Noch nicht berechnet* anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-46683. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Versandpreis zeigt *Noch nicht berechnet* an.

<u>Voraussetzungen</u>:

Adobe Commerce Inventory management (MSI)-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt und setzen Sie seinen Preis auf *$34*.
1. Konfigurieren Sie die Versandmethode für den kostenlosen Versand.
1. Konfigurieren Sie mindestens eine weitere Versandmethode.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** und erstellen Sie eine neue Regel:
   * Name = *75more*
   * Coupon = Keine
   * Priorität = 1
   * Bedingungen: Die Zwischensumme ist gleich oder größer als *$75*
   * Aktionen:
      * Auf Versandbetrag anwenden = Ja
      * Nachfolgende Regeln verwerfen = Nein
      * Kostenloser Versand = für Sendungen mit übereinstimmenden Artikeln
1. Erstellen Sie eine weitere Preisregel für den Warenkorb:
   * Name = *35off*
   * Priorität = 0
   * Coupon = spezifischer Coupon
   * Couponcode = 35off
   * Aktionen:
      * Anwenden = Prozentsatz des Produktpreisrabatts
      * Rabattbetrag = 35
      * Anwenden auf Versandbetrag = Nein
      * Nachfolgende Regeln verwerfen = Ja
      * Kostenloser Versand = Nein
1. Öffnen Sie die Storefront und fügen Sie dem Warenkorb drei Produkte hinzu, sodass die Zwischensumme 75 USD überschreitet.
1. Fahren Sie fort, um als Gast auszuchecken.
1. Wählen Sie im Versandschritt **$0 - Free shipping** aus und fahren Sie mit dem Zahlungsschritt fort.
1. Überprüfen Sie die [!UICONTROL Order Summary] im Zahlungsschritt. Es wird *[!UICONTROL $0 - Free Shipping - Free]* angezeigt.
1. Wenden Sie den Couponcode *35off* an, er aktualisiert die Zwischensumme und macht sie weniger als 75 USD.
1. Überprüfen Sie [!UICONTROL Order Summary] auf den Zahlungsschritt.

<u>Erwartete Ergebnisse</u>:

Die folgende Meldung wird angezeigt: *Ausgewählte Versandmethode ist nicht verfügbar. Wählen Sie für diese Bestellung eine andere Versandmethode aus.*

<u>Tatsächliche Ergebnisse</u>:

Der Versandpreis zeigt *Noch nicht berechnet* an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
