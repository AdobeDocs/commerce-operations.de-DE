---
title: 'ACSD-51408: Status des Bestellartikels ist fälschlicherweise auf [!UICONTROL backordered] gesetzt'
description: Wenden Sie den Patch ACSD-51408 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bestellartikelstatus fälschlicherweise auf [!UICONTROL backordered] gesetzt wurde.
feature: B2B, Orders
role: Admin
exl-id: 51abb4c6-5618-43a5-89ca-a3879be2c3c4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-51408: Status des Bestellartikels ist fälschlicherweise auf *[!UICONTROL backordered]* gesetzt

Mit dem Patch ACSD-51408 wird das Problem behoben, dass der Bestellartikelstatus fälschlicherweise auf [!UICONTROL backordered] gesetzt wurde. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51408. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Bestellartikelstatus ist fälschlicherweise auf *[!UICONTROL backordered]* gesetzt.

<u>Voraussetzungen</u>:

Adobe Commerce B2B- und Inventory management (MSI)-Module sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie einen neuen Stock, der mit der neuen Website verknüpft ist, die in Schritt 1 erstellt wurde, und weisen Sie die in Schritt 2 erstellte Quelle zu.
1. Erstellen Sie eine Firma und weisen Sie sie der neuen Website zu, die in Schritt 1 erstellt wurde.
1. Erstellen Sie einen neuen Kunden und weisen Sie ihn dem in Schritt 4 erstellten Unternehmen zu.
1. Erstellen Sie ein Produkt, weisen Sie es der neuen Website zu, und legen Sie die **[!UICONTROL default stock]** = *0* und die **[!UICONTROL new stock]** auf mehr als *0*.
1. **[!UICONTROL backorders]** aktivieren.
1. Aktivieren Sie **[!UICONTROL Check/Money Order]** Zahlungsmethode für den neuen Website-Umfang.
1. Aktivieren Sie die **[!UICONTROL Flat Rate shipping method]** für den neuen Website-Umfang.
1. Erstellen Sie eine neue Bestellung über **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Wählen Sie den in Schritt 5 erstellten neuen Kunden aus.
1. Wählen Sie den in Schritt 1 erstellten neuen Store aus.
1. Wählen Sie das in Schritt 6 erstellte Produkt aus.
1. Füllen Sie die Bestellinformationen aus, einschließlich der Zahlungs- und Versandmethoden.
1. Senden Sie die Bestellung.
1. Überprüfen Sie *Elementstatus*.

<u>Erwartete Ergebnisse</u>

Der Artikel kann aus dem Bestand versendet werden. Der Elementstatus ist *[!UICONTROL ordered]*.

<u>Tatsächliche Ergebnisse</u>

Der Elementstatus ist *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[Der Bestellartikelstatus wird fälschlicherweise auf *[!UICONTROL Ordered]* gesetzt, wenn der Produktbestand 0,](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md) beträgt

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
