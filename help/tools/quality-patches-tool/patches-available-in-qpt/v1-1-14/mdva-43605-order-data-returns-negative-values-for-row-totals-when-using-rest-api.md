---
title: 'MDVA-43605: Auftragsdaten geben bei Verwendung der Rest-API negative Werte für Zeilensummen zurück'
description: Der Patch MDVA-43605 behebt das Problem, dass die Bestelldaten bei Verwendung der Rest-API negative Werte für Zeilensummen zurückgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43605. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605: Auftragsdaten geben bei Verwendung der Rest-API negative Werte für Zeilensummen zurück

Der Patch MDVA-43605 behebt das Problem, dass die Bestelldaten bei Verwendung der Rest-API negative Werte für Zeilensummen zurückgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43605. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bestelldaten geben bei Verwendung der Rest-API negative Werte für Zeilensummen zurück.

<u>Zu reproduzierende Schritte</u>:

1. Kostenlosen Versand aktivieren.
1. Navigieren Sie zu **Konfiguration** > **Katalog** > **Preis** > und legen Sie den Katalogpreisumfang = Website fest.
1. Navigieren Sie zu **Konfiguration** > **Verkauf** > **Steuern** und aktualisieren Sie:
   * Steuerklasse für die Beförderung = steuerpflichtige Waren
   * Berechnungseinstellungen:
      * Katalogpreis = inkl. Steuern
      * Versandpreis = inkl. Preis
      * Anwenden von Rabatten auf Preise = inkl. Steuern
   * Preisanzeigeeinstellungen: Einschließlich Steuern (alle Felder)
   * Anzeigeeinstellungen für Warenkorb: Einschließlich Steuern (alle Felder)
   * Bestellungen, Rechnungen, Kreditkarten:
      * Versandbetrag anzeigen = inkl. Steuern
1. Erstellen Sie einen Steuersatz für US (Staat = &#39;*&#39;), Steuersatz Prozent = 24,00
1. Erstellen Sie eine Steuerregel mit dem obigen Steuersatz.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem bestimmten Coupon und einen Rabatt = 50 USD des Festbetrags für den gesamten Warenkorb.
1. Erstellen Sie vier Produkte mit den folgenden Preisen: 8,90 USD, 5,90 USD, 6,90 USD und 5,95 USD.
1. Erstellen Sie mit dem im vorherigen Schritt erstellten Gutscheincode eine Administratorbestellung mit vier dieser Produkte. Verwenden Sie den kostenlosen Versand.
1. Die Zahlung sollte nicht erforderlich sein, da der Gutscheincode die Gesamtsumme des Warenkorbs abdeckt.
1. Rufen Sie die gerade über den REST-API-Endpunkt erstellte Reihenfolge ab:

   ```json
   GET rest/V1/orders/1
   ```

<u>Erwartete Ergebnisse</u>:

Die Werte von `base_row_total` und `base_row_total_incl_tax` in der Antwort sind null.

<u>Tatsächliche Ergebnisse</u>:

Die Felder `base_row_total` und `base_row_total_incl_tax` in der Antwort weisen negative Werte auf.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
