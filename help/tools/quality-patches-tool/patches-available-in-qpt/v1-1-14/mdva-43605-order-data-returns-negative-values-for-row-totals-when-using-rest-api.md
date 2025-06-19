---
title: 'MDVA-43605: Bestelldaten geben bei Verwendung der REST-API negative Werte für Zeilensummen zurück'
description: Der Patch MDVA-43605 behebt das Problem, dass die Bestelldaten bei Verwendung der REST-API negative Werte für Zeilensummen zurückgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43605. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605: Bestelldaten geben bei Verwendung der REST-API negative Werte für Zeilensummen zurück

Der Patch MDVA-43605 behebt das Problem, dass die Bestelldaten bei Verwendung der REST-API negative Werte für Zeilensummen zurückgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43605. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestelldaten geben bei Verwendung der REST-API negative Werte für Zeilensummen zurück.

<u>Schritte zur Reproduktion</u>:

1. Kostenlosen Versand aktivieren.
1. Navigieren Sie **Konfiguration** > **Katalog** > **Preis** > und legen Sie Katalogpreis Umfang = Website fest.
1. Navigieren Sie zu **Konfiguration** > **Verkauf** > **Steuer** und aktualisieren Sie:
   * Steuerklasse für den Versand = steuerpflichtige Waren
   * Berechnungsparameter:
      * Katalogpreis = inkl. MwSt
      * Versandpreis = inkl. Preis
      * Preisnachlass = inkl. Steuer
   * Einstellungen für die Preisanzeige: Einschließlich Steuer (alle Felder)
   * Anzeigeeinstellungen für den Warenkorb: Einschließlich Steuer (alle Felder)
   * Bestellungen, Rechnungen, Gutschriften:
      * Versandbetrag anzeigen = einschließlich MwSt
1. Steuersatz für USA erstellen (Bundesland = &#39;*&#39;), Steuersatz Prozent = 24,00
1. Erstellen Sie eine Steuerregel mit dem obigen Steuersatz.
1. Erstellen Sie eine Warenkorb-Preisregel mit einem bestimmten Coupon und Rabatt = 50 $ des Festbetrags für den gesamten Warenkorb.
1. Erstellen Sie vier Produkte zu folgenden Preisen: $8.90, $5.90, $6.90 und $5.95.
1. Erstellen Sie eine Admin-Bestellung mit vier dieser Produkte unter Verwendung des im vorherigen Schritt erstellten Couponcodes. Verwenden Sie den kostenlosen Versand.
1. Die Zahlung sollte nicht erforderlich sein, da der Couponcode die Gesamtsumme des Warenkorbs abdeckt.
1. Rufen Sie die gerade über den REST-API-Endpunkt erstellte Reihenfolge ab:

   ```json
   GET rest/V1/orders/1
   ```

<u>Erwartete Ergebnisse</u>:

Die Werte von `base_row_total` und `base_row_total_incl_tax` in der Antwort sind null.

<u>Tatsächliche Ergebnisse</u>:

Die Felder `base_row_total` und `base_row_total_incl_tax` in der Antwort haben negative Werte.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
