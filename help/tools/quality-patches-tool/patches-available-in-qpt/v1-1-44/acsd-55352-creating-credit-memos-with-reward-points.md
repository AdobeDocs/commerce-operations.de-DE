---
title: 'ACSD-55352: Erstellen von Gutschriften mit Belohnungspunkten'
description: Wenden Sie den Patch von ACSD-55352 an, um das Problem in Adobe Commerce zu beheben, bei dem sich nach dem Erstellen einer teilweisen Gutschrift mit Kundenbelohnungspunkten der Bestellstatus in „Geschlossen“ ändert und die Optionen für die Gutschrift von der Admin-Bestellseite verschwinden.
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-55352: Erstellen von Gutschriften mit Belohnungspunkten

Mit dem Patch des ACSD-55352 wird das Problem behoben, dass nach dem Erstellen einer teilweisen Gutschrift mit Belohnungspunkten für Kunden der Bestellstatus in &quot;*&quot;* und die Optionen für Gutschriften von der Admin-Bestellseite verschwinden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55352. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nachdem Sie eine teilweise Gutschrift mit Belohnungspunkten für Kunden erstellt haben, ändert sich der Bestellstatus in *Geschlossen* und die Optionen für Gutschriften verschwinden auf der Seite „Admin-Bestellung“.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Adobe Commerce Admin an.
2. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Fügen Sie zwei Tarife hinzu:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Punkte auf Währung*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Währung zu Punkten*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Erstellen Sie ein einfaches Produkt zum Preis von *$100* und mit *Qty* : *100*.
5. Erstellen Sie einen Kunden aus der Storefront.
6. Gehen Sie erneut zum Backend: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > *100* und speichern Sie den Kunden.
7. Wechseln Sie zur Storefront und melden Sie sich als zuvor vom Kunden erstellter Benutzer an.
8. Fügen Sie das Produkt mit *Qty* : *10* in den Warenkorb.
9. Wechseln Sie zu **[!UICONTROL Checkout]** und verwenden Sie die verfügbaren *100* Belohnungspunkte, wenn Sie dazu aufgefordert werden, und geben Sie die Bestellung auf.
10. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** und versenden Sie diese Bestellung.
11. Wechseln Sie zu [!UICONTROL Credit Memo] und aktualisieren Sie die *Menge zur Erstattung* auf *8*.
12. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Refund Reward Points]** und klicken Sie auf **[!UICONTROL Refund offline]**.
13. Versuchen Sie, die anderen beiden verbleibenden Produkte aus der Bestellung zurückzuerstatten, indem Sie die [!UICONTROL Credit Memo] verwenden.

<u>Erwartete Ergebnisse</u>:

* Der Administrator erstellt [!UICONTROL Credit Memo], um die beiden verbleibenden Produkte zurückzugeben.
* Der Bestellstatus lautet *Abgeschlossen*.

<u>Tatsächliche Ergebnisse</u>:

* Es können keine weiteren [!UICONTROL Credit Memo] erstellt werden.
* Der Bestellstatus lautet *Geschlossen*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
