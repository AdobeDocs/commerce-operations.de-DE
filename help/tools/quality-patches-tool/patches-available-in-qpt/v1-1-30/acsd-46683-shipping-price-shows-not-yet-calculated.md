---
title: 'ACSD-46683: Versandpreis wird angezeigt *Noch nicht berechnet*'
description: Wenden Sie den Patch ACSD-46683 an, um das Adobe Commerce-Problem zu beheben, bei dem der Versandpreis „Noch nicht berechnet“ anzeigt.
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ebd79187-2835-403b-945d-80ac34d6fb9c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-46683: Versandpreis wird angezeigt *noch nicht berechnet*

Mit dem Patch ACSD-46683 wird das Problem behoben, dass der Versandpreis &quot;*noch nicht berechnet“*. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-46683. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Versandpreis wird angezeigt *Noch nicht berechnet*.

<u>Voraussetzungen</u>:

Adobe Commerce Inventory management (MSI)-Module sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt und setzen Sie seinen Preis auf *$ 34*.
1. Konfigurieren Sie die Versandmethode Kostenloser Versand .
1. Konfigurieren Sie mindestens eine weitere Versandmethode.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** und erstellen Sie eine neue Regel:
   * Name = *75more*
   * Coupon = keine
   * Priorität = 1
   * Bedingungen: Zwischensumme ist gleich oder größer als *$75*
   * Aktionen:
      * Auf Versandbetrag anwenden = Ja
      * Nachfolgende Regeln verwerfen = Nein
      * Kostenloser Versand = Für Lieferungen mit passenden Artikeln
1. Erstellen Sie eine weitere Warenkorb-Preisregel:
   * Name = *35off*
   * Priorität = 0
   * Coupon = spezifischer Coupon
   * Couponcode = 35off
   * Aktionen:
      * Anwenden = Prozentsatz des Produktpreisrabatts
      * Rabattbetrag = 35
      * Auf Versandbetrag anwenden = Nein
      * Nachfolgende Regeln verwerfen = Ja
      * Kostenloser Versand = Nein
1. Öffnen Sie die Storefront und fügen Sie drei Produkte zum Warenkorb hinzu, sodass die Zwischensumme 75 USD überschreitet.
1. Zur Kasse als Gast.
1. Wählen Sie im Schritt Versand die Option **$0 - Kostenloser** aus und fahren Sie mit dem Schritt Zahlung fort.
1. Überprüfen Sie die [!UICONTROL Order Summary] des Zahlungsschritts. Es zeigt *[!UICONTROL $0 - Free Shipping - Free]*.
1. Wenden Sie den Couponcode *35off* an, aktualisiert er die Zwischensumme und macht sie weniger als $75.
1. Überprüfen Sie die [!UICONTROL Order Summary] des Zahlungsschritts.

<u>Erwartete Ergebnisse</u>:

Daraufhin wird folgende Meldung angezeigt: *Ausgewählte Versandart ist nicht verfügbar. Bitte wählen Sie eine andere Versandart für diese Bestellung.*

<u>Tatsächliche Ergebnisse</u>:

Der Versandpreis wird angezeigt *Noch nicht berechnet*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
