---
title: 'ACSD-63062: Falsche Rabattberechnungen beim Warenkorb mit mehreren sich überlappenden Regeln'
description: Wenden Sie den Patch ACSD-63062 an, um das Adobe Commerce-Problem zu beheben, bei dem falsche Warenkorbabzinsberechnungen auftreten, wenn mehrere überlappende Regeln angewendet werden.
feature: Price Rules
role: Admin, Developer
exl-id: c4a93063-b640-444e-ba0e-552dd8d1895b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: Falsche Rabattberechnungen beim Warenkorb mit mehreren sich überlappenden Regeln

Der Patch ACSD-63062 behebt das Problem, dass falsche Warenkorbabzinsberechnungen auftreten, wenn mehrere überlappende Regeln angewendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-63062. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Falsche Berechnungen des Warenkorbabschlags treten auf, wenn mehrere überlappende Regeln angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Instanz mit Beispieldaten.
1. Erstellen Sie drei einfache Produkte:

   * simple1: $1080
   * simple2: $260
   * simple3: $280

1. Erstellen Sie vier *[!UICONTROL Cart Price Rules]* wie folgt:

   * Regel 1:

      * *[!UICONTROL Priority]*: 100
      * Registerkarte &quot;*[!UICONTROL Conditions]*&quot;: Verwenden Sie ein einfaches 2-Produkt (280 $), wenn die Gesamtmenge gleich oder größer als 3 ist
      * Registerkarte &quot;*[!UICONTROL Actions]*&quot;: SKU ist einfach2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * Regel 2:

      * *[!UICONTROL Priority]*: 200
      * Registerkarte &quot;*[!UICONTROL Actions]*&quot;: SKU ist einfach2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20 %

   * Artikel 3:

      * *[!UICONTROL Priority]*: 300
      * Registerkarte *[!UICONTROL Conditions]*: Zwischensumme ist gleich oder größer als $1000
      * *[!UICONTROL Fixed Amount Discount]* für den gesamten Warenkorb: $100

   * Artikel 4:

      * *[!UICONTROL Priority]*: 400
      * Registerkarte &quot;*[!UICONTROL Conditions]*&quot;: Verwenden Sie ein einfaches 1-Produkt ($1080), wenn die Gesamtmenge gleich oder größer als 2 ist
      * Registerkarte &quot;*[!UICONTROL Actions]*&quot;: SKU ist einfach1
      * *[!UICONTROL Fixed Amount Discount]* für den gesamten Warenkorb: $960

1. Gehen Sie zur Storefront und fügen Sie die folgenden Produkte mit der angegebenen Menge in den Warenkorb:

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Überprüfen Sie den Warenkorb.

<u>Erwartete Ergebnisse</u>:

Der angewendete Rabatt beträgt $1352.

<u>Tatsächliche Ergebnisse</u>:

Der angewendete Rabatt beträgt $1525,33.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
