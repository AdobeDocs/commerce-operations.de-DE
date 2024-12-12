---
title: 'ACSD-63062: Falsche Berechnung des Rabatts für den Warenkorb mit mehreren überlappenden Regeln'
description: Wenden Sie den Patch ACSD-63062 an, um das Adobe Commerce-Problem zu beheben, bei dem bei Anwendung mehrerer überlappender Regeln falsche Rabattberechnungen auftreten.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: Falsche Berechnung des Rabatts für den Warenkorb mit mehreren überlappenden Regeln

Der Patch ACSD-63062 behebt das Problem, dass falsche Rabattberechnungen für den Warenkorb auftreten, wenn mehrere überlappende Regeln angewendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-63062. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn mehrere überlappende Regeln angewendet werden, treten falsche Rabattberechnungen auf.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie eine neue Instanz mit Beispieldaten.
1. Erstellen Sie drei einfache Produkte:

   * simple1: 1080 $
   * simple2: 260$
   * simple3: 280$

1. Erstellen Sie vier *[!UICONTROL Cart Price Rules]* wie folgt:

   * Regel 1:

      * *[!UICONTROL Priority]*: 100
      * Registerkarte *[!UICONTROL Conditions]*: Verwenden Sie ein einfaches2-Produkt ($280), wenn die Gesamtmenge gleich oder größer als 3 ist.
      * Registerkarte *[!UICONTROL Actions]*: SKU ist einfach2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * Regel 2:

      * *[!UICONTROL Priority]*: 200
      * Registerkarte *[!UICONTROL Actions]*: SKU ist einfach2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20 %

   * Regel 3:

      * *[!UICONTROL Priority]*: 300
      * Registerkarte *[!UICONTROL Conditions]*: Zwischensumme gleich oder größer als $1000
      * *[!UICONTROL Fixed Amount Discount]* für den gesamten Warenkorb: $100

   * Regel 4:

      * *[!UICONTROL Priority]*: 400
      * Registerkarte *[!UICONTROL Conditions]*: Verwenden Sie das Produkt &quot;simple1&quot;($1080), wenn die Gesamtmenge gleich oder größer als 2 ist.
      * Registerkarte *[!UICONTROL Actions]*: SKU ist einfach1
      * *[!UICONTROL Fixed Amount Discount]* für den gesamten Warenkorb: 960 USD

1. Gehen Sie zur Storefront und fügen Sie dem Warenkorb die folgenden Produkte mit der angegebenen Menge hinzu:

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Überprüfen Sie den Warenkorb.

<u>Erwartete Ergebnisse</u>:

Der angewendete Rabatt beträgt 1352 USD.

<u>Tatsächliche Ergebnisse</u>:

Der angewendete Rabatt beträgt 1525,33 USD.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
