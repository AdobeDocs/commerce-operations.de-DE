---
title: "ACSD-57086: Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden falsch verarbeitet"
description: Wenden Sie den Patch ACSD-57086 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen nicht korrekt verarbeitet werden.
feature: Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-57086: Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden falsch verarbeitet

Der Patch ACSD-57086 behebt das Problem, dass Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen nicht korrekt verarbeitet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57086. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei der Verwendung eines Multi-Store-Setups mit AsyncOrder-Verarbeitung werden Bestellungen, die auf anderen Websites/Stores als der Haupt-Website aufgegeben werden, aufgrund von Problemen mit der Perimeter-Verarbeitung im Warteschlangen-Verbrauchercode abgelehnt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie [!DNL RabbitMQ] und führen Sie `bin/magento setup:upgrade` aus, um die Warteschlangen für [!DNL RabbitMQ] zu erstellen.
1. Konfigurieren der Verarbeitung von AsyncOrder mit:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Erstellen Sie eine sekundäre Website, einen Store und eine Store-Ansicht.
1. Erstellen Sie ein Produkt, das auf beiden Websites freigegeben ist.
1. Nutzungsbedingungen aktivieren:
   1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Setzen Sie *[!UICONTROL Enable Terms And Conditions]* auf *Ja*.
1. Konfigurieren Sie die Geschäftsbedingungen für beide Websites:
   1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Verwenden Sie die folgenden Einstellungen:
      * *[!UICONTROL Condition Name]*: *beliebiger*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Erstellen Sie eine weitere Bedingung für die zweite Website-/Store-Ansicht.
1. Ändern Sie die Standardwebsite, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** gehen. Klicken Sie auf die zweite Website, aktivieren Sie *[!UICONTROL Set as Default]* und speichern Sie.
1. Löschen Sie den Cache mit:

   ```bash
   bin/magento cache:clear
   ```

1. Gehen Sie zur Storefront und fügen Sie dem Warenkorb ein Produkt hinzu. Fahren Sie mit dem Checkout fort und geben Sie eine Bestellung auf (im Schritt Zahlungsmethode sollte ein Kontrollkästchen angezeigt werden, um die Bedingungen zu akzeptieren).
1. Gehen Sie nach der Bestellung zurück zum Administrator, ändern Sie die Standardwebsite zurück zur ursprünglichen Haupt-Website und speichern Sie sie.
1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clear
   ```

1. Führen Sie den folgenden Befehl aus, um den Warteschlangen-Consumer zu starten:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Erwartete Ergebnisse</u>:

Bestellung ist erfüllt, wird nicht automatisch zurückgewiesen.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus lautet *rejected* mit folgendem Kommentar:

*Die Bestellung wurde nicht platziert. Einverständnis mit den Geschäftsbedingungen, dann versuchen Sie, Ihre Bestellung erneut aufzugeben.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
