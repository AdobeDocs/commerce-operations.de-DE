---
title: "ACSD-61133: `sales_clean_quotes` cron löscht Anführungszeichen aus nicht genehmigten Bestellungen"
description: Wenden Sie den Patch ACSD-61133 an, um das Adobe Commerce-Problem zu beheben, bei dem `sales_clean_quotes` cron Anführungszeichen aus nicht genehmigten Bestellungen löscht.
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 67b1dd3d4814b487d47a25697ed21d60f1e4e378
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: `sales_clean_quotes` cron löscht Anführungszeichen aus nicht genehmigten Bestellungen

Der Patch ACSD-61133 behebt das Problem, dass der `sales_clean_quotes`-Cron Anführungszeichen aus nicht genehmigten Bestellungen löscht. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist. Die Patch-ID ist ACSD-61133. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 und 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`sales_clean_quotes` cron löscht Anführungszeichen aus nicht genehmigten Bestellungen. Der *[B2B-Kaufauftrag]* kann nicht in die Reihenfolge des mit der gekauften Bestellung verknüpften Angebots konvertiert werden, da der Cron ihn löscht.

<u>Voraussetzungen</u>:

Adobe Commerce [!UICONTROL B2B] -Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Funktion *[!UICONTROL B2B Purchase Order]* .
1. Erstellen Sie ein Unternehmen.
1. Erstellen Sie eine *[!UICONTROL Purchase Order]*.
1. Warten Sie, bis das Anführungszeichen abläuft und vom Cron gelöscht wird. Der Ablaufzeitraum für das Zitat kann mit **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]** eingestellt werden.
1. Konvertieren Sie *[!UICONTROL Purchase Order]* über *[!UICONTROL My Purchase Order in Customer Dashboard]* oder mit [!DNL GraphQL] `placeOrderForPurchaseOrder` Mutation in die Reihenfolge.

<u>Erwartete Ergebnisse</u>:

Das mit aktiven *[!UICONTROL Purchase Order]* verknüpfte Anführungszeichen wird nicht gelöscht, da es durch den Cron abgelaufen ist. Die Bestellung wird entweder auf der Storefront oder über [!DNL GraphQL] erfolgreich platziert.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird nicht platziert und ein Fehler wird auf der Storefront angezeigt oder in der Antwort [!DNL GraphQL] zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
