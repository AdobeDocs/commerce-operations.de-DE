---
title: 'ACSD-66084: `row_total_incl_tax` gibt für vollständig reduzierte Elemente in der Antwort der Auftrags-API einen Restwert von nahezu 0,00 anstelle von 0,00 zurück'
description: Wenden Sie den Patch ACSD-66084 an, um das Adobe Commerce-Problem zu beheben, bei dem „row_total_incl_tax“ für vollständig reduzierte Elemente in der Antwort der Auftrags-API als Restwert von nahezu 0,00 zurückgegeben wurde.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 01f7059e53590c4ff6602c41eb980ac7c141af33
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# ACSD-66084: `row_total_incl_tax` gibt bei vollständig reduzierten Elementen in der API-Antwort für Bestellungen einen Restwert nahe null anstelle von 0,00 zurück

Mit dem Patch ACSD-66084 wird das Problem behoben, dass `row_total_incl_tax` in der Antwort der Auftrags-API als Restwert von nahezu null anstelle von 0,00 für vollständig reduzierte Artikel zurückgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66084. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der `row_total_incl_tax` wird in der Antwort der Auftrags-API als Restwert nahe null zurückgegeben statt als 0,00 für vollständig reduzierte Artikel.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit einem Preis und einem Sonderpreis. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Klicken Sie auf **[!UICONTROL Add Product]** > setzen Sie **[!UICONTROL Price]** auf $25 und **[!UICONTROL Special Price]** auf $16.99 unter **[!UICONTROL Advanced Pricing]**.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** und fügen Sie einen Satz von 20 % hinzu. Wechseln Sie dann zu **[!UICONTROL Tax Rules]** und erstellen Sie eine Regel und weisen Sie Folgendes zu
   **[!UICONTROL Taxable Goods]** als Produktsteuerklasse.
1. Erstellen Sie eine Verkaufsregel mit 100 % Rabatt und Coupon. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** und fügen Sie eine Regel mit einem 100 % Rabatt hinzu. Verwenden Sie dann **[!UICONTROL Specific Coupon]** und geben Sie Ihren Code ein.
1. Wechseln Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** und konfigurieren Sie die Steuereinstellungen.
1. Kostenlosen Versand aktivieren. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**. **[!UICONTROL Enabled]** auf **[!UICONTROL Yes]** setzen und Einstellungen anpassen.
1. Navigieren Sie zur Produktseite und wählen Sie **[!UICONTROL Add to Cart]** aus. Gehen Sie zum Warenkorb und wenden Sie den Gutscheincode an.
1. Bestellung mit der anwendbaren Steuerzone aufgeben.
1. Erstellen eines Admin-Tokens (API) über die REST-API.
1. Abrufen von Bestelldetails über die REST-API.
1. Überprüfen Sie `row_total_incl_tax` in der Antwort.

<u>Erwartete Ergebnisse</u>:

`row_total_incl_tax` sollte einen Währungswert wie `0.00` zurückgeben, wenn der Artikel vollständig diskontiert ist.

<u>Tatsächliche Ergebnisse</u>:

`row_total_incl_tax` gibt einen Gleitkommawert nahe null wie `3.5527136788005e-15` zurück, was für die Währungsanzeige nicht geeignet ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
