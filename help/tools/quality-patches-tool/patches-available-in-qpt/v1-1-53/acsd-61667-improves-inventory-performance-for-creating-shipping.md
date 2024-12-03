---
title: 'ACSD-61667: Verbessert die Lagerbestandsleistung für die Erstellung von Versandaktionen'
description: Wenden Sie den Patch ACSD-60584 an, um die Lagerbestandsleistung für die Erstellung des Versands bei vielen Quellen mit In-Store-Abholung zu verbessern.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
source-git-commit: c32684a09e4a99733feb198b1d353b090c68a7f5
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: Verbessert die Lagerbestandsleistung für die Erstellung von Versandaktionen

Der Patch ACSD-61667 behebt das Problem, dass der Händler die Bestellung nicht versenden kann, wenn der [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) (ehemals MSI) Pickup Store mit mehreren Quellen aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61667. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Sie können die Bestellung nicht versenden, wenn der MSI-Abruf-Store mit mehreren Quellen aktiviert ist. Dieser Patch verbessert die Lagerbestandsleistung, um den Versand zu erstellen, falls viele Quellen über die In-Store-Abholung verfügen.

<u>Voraussetzungen:</u>:

Adobe Commerce Inventory-Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie mehr als *10* Quellen und aktivieren Sie deren Abnahmeorte.
1. Der Pickup-Store ist unter **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** aktiviert.
1. Erstellen Sie eine große Anzahl von Abholbestellungen.
1. Gehen Sie zu **[!UICONTROL Admin login]** und wählen Sie **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]** aus.
1. Filtern und suchen Sie nach ausstehenden Bestellungen.
1. Klicken Sie auf **[!UICONTROL Ship]**.

<u>Erwartete Ergebnisse</u>:

Die Versandseite wird erwartungsgemäß geladen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den Fehler *503 Maximale Ausführungsdauer*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
