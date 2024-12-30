---
title: 'ACSD-61667: Verbessert die Inventarleistung für die Versanderstellung'
description: Wenden Sie den ACSD-60584 Patch an, um die Inventarleistung für die Versanderstellung zu verbessern, falls viele Quellen mit Abholung im Geschäft vorhanden sind.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
source-git-commit: c32684a09e4a99733feb198b1d353b090c68a7f5
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: Verbessert die Inventarleistung für die Versanderstellung

Mit dem Patch ACSD-61667 wird das Problem behoben, dass der Händler die Bestellung nicht versenden kann, wenn der [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) (ehemals MSI) Pickup Store mit mehreren Quellen aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61667. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Sie können die Bestellung nicht mit mehreren Quellen versenden, wenn der MSI Pickup Store aktiviert ist. Dieser Patch verbessert die Inventarleistung, um bei vielen Quellen mit Ladenabholung Versandkosten zu erstellen.

<u>Voraussetzungen:</u>:

Adobe Commerce Inventory-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie über *10* Quellen und aktivieren Sie deren Abholstandorte.
1. Der Pickup Store wird unter **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** aktiviert.
1. Erstellen Sie eine große Anzahl von Abholaufträgen.
1. Navigieren Sie zu **[!UICONTROL Admin login]** und wählen Sie **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]** aus.
1. Filtern und prüfen Sie auf ausstehende Bestellungen.
1. Klicken Sie auf **[!UICONTROL Ship]**.

<u>Erwartete Ergebnisse</u>:

Die Versandseite wird erwartungsgemäß geladen.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein *503-Fehler mit einer maximalen Ausführungszeitüberschreitung*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
