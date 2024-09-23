---
title: "ACSD-55352: Erstellen von Kreditkarten mit Bonuspunkten"
description: Wenden Sie den Patch ACSD-55352 an, um das Adobe Commerce-Problem zu beheben, bei dem nach dem Erstellen eines partiellen Kreditmemo mit Kundenbelohnungspunkten der Auftragsstatus zu *geschlossen* geändert wird und die Kreditmemo-Optionen auf der Seite "Admin-Bestellung"nicht mehr angezeigt werden.
feature: Checkout, Orders
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Erstellen von Kreditkarten mit Bonuspunkten

Der Patch ACSD-55352 behebt das Problem, dass nach dem Erstellen eines partiellen Kreditmemo mit Kundenbelohnungspunkten der Auftragsstatus zu *closed* geändert wird und die Kreditmemo-Optionen auf der Seite &quot;Admin-Bestellung&quot;ausgeblendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55352. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nachdem Sie ein Teil-Kreditmemo mit Kundenbelohnungspunkten erstellt haben, ändert sich der Auftragsstatus in *closed* und die Kreditmemo-Optionen werden auf der Seite &quot;Admin-Bestellung&quot;nicht mehr angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Adobe Commerce Admin an.
2. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Fügen Sie zwei Raten hinzu:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Punkte auf Währung*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Währung bis Punkte*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Erstellen Sie ein einfaches Produkt mit dem Preis *$100* und mit *Menge* : *100*.
5. Erstellen Sie einen Kunden aus der Storefront.
6. Gehen Sie erneut zum Backend: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Hinzufügen von *100* und speichern Sie den Kunden.
7. Gehen Sie zur Storefront und melden Sie sich als zuvor vom Kunden erstellter Kunde an.
8. Fügen Sie das Produkt dem Warenkorb mit *Menge* : *10* hinzu.
9. Wechseln Sie zu **[!UICONTROL Checkout]** und verwenden Sie die verfügbaren Belohnungspunkte für *100*, wenn Sie dazu aufgefordert werden, und platzieren Sie die Bestellung.
10. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** und schicken Sie diese Bestellung aus.
11. Gehen Sie zu [!UICONTROL Credit Memo] und aktualisieren Sie die *Menge an Rückerstattungssatz* auf *8*.
12. Tippen Sie auf das Kontrollkästchen **[!UICONTROL Refund Reward Points]** und klicken Sie auf **[!UICONTROL Refund offline]**.
13. Versuchen Sie, die beiden anderen verbleibenden Produkte aus der Bestellung mit dem Wert [!UICONTROL Credit Memo] zurückzuerstatten.

<u>Erwartete Ergebnisse</u>:

* Der Administrator erstellt [!UICONTROL Credit Memo] , um die beiden verbleibenden Produkte zurückzugeben.
* Der Bestellstatus lautet *Abgeschlossen*.

<u>Tatsächliche Ergebnisse</u>:

* Kann nicht mehr [!UICONTROL Credit Memo] erstellen.
* Der Bestellstatus lautet *Geschlossen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
