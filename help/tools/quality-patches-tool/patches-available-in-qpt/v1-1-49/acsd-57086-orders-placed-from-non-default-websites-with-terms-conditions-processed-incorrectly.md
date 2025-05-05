---
title: 'ACSD-57086: Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden falsch verarbeitet'
description: Wenden Sie den Patch ACSD-57086 an, um das Problem in Adobe Commerce zu beheben, bei dem Bestellungen, die von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen aufgegeben werden, nicht korrekt verarbeitet werden.
feature: Orders
role: Admin, Developer
exl-id: d9f2ef50-12c4-4a2d-b140-dfd0e8948fd3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-57086: Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden falsch verarbeitet

Mit dem Patch ACSD-57086 wird das Problem behoben, dass Bestellungen, die von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen aufgegeben werden, nicht korrekt verarbeitet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57086. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei Verwendung eines Multi-Store-Setups mit AsyncOrder-Verarbeitung werden Bestellungen, die auf anderen Websites/Stores als der Haupt-Website platziert werden, aufgrund von Problemen mit der Bereichsverarbeitung im Warteschlangen-Consumer-Code abgelehnt.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie [!DNL RabbitMQ] und führen Sie `bin/magento setup:upgrade` aus, um die Warteschlangen für die [!DNL RabbitMQ] zu erstellen.
1. Konfigurieren der AsyncOrder-Verarbeitung mit:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Erstellen Sie eine sekundäre Website, einen Store und eine Store-Ansicht.
1. Erstellen Sie ein Produkt, das von beiden Websites gemeinsam genutzt wird.
1. Geschäftsbedingungen aktivieren:
   1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Setzen Sie *[!UICONTROL Enable Terms And Conditions]* auf *Ja*.
1. Konfigurieren Sie die allgemeinen Geschäftsbedingungen für beide Websites:
   1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Verwenden Sie die folgenden Einstellungen:
      * *[!UICONTROL Condition Name]*: *alles*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Erstellen Sie eine weitere Bedingung für die zweite Website-/Store-Ansicht.
1. Wechseln Sie zur Standard-Website über **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Klicken Sie auf die zweite Website, aktivieren Sie *[!UICONTROL Set as Default]* und speichern Sie.
1. Löschen Sie den Cache mit:

   ```bash
   bin/magento cache:clear
   ```

1. Gehen Sie zur Storefront und fügen Sie ein Produkt zum Warenkorb hinzu. Gehen Sie zur Kasse und geben Sie eine Bestellung auf (Sie sollten ein Kontrollkästchen im Schritt Zahlungsmethode sehen, um die Nutzungsbedingungen zu akzeptieren).
1. Gehen Sie nach der Bestellung zurück zu Admin und ändern Sie die Standard-Website wieder in die ursprüngliche Haupt-Website und speichern Sie.
1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clear
   ```

1. Führen Sie den folgenden Befehl aus, um die Verbraucherwarteschlange zu starten:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird ausgeführt, aber nicht automatisch abgelehnt.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus wird *abgelehnt* mit folgendem Kommentar:

*Die Bestellung wurde nicht aufgegeben. Stimmen Sie zunächst den Nutzungsbedingungen zu und versuchen Sie dann, Ihre Bestellung erneut aufzugeben.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
