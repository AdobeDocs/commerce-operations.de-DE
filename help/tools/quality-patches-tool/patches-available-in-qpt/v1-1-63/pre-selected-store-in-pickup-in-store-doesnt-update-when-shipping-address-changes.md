---
title: Vorausgewählter Store in „Abholung im Store“ wird nicht aktualisiert, wenn sich die Versandadresse ändert
description: Wenden Sie den Patch ACSD-64753 an, um das Adobe Commerce-Problem zu beheben, bei dem der vorausgewählte Shop nicht aktualisiert wurde, wenn eine neue Lieferadresse außerhalb des Serviceradius des ausgewählten Shops eingegeben wurde.
feature: Inventory
role: Admin, Developer
source-git-commit: 9d76014fb86fd92b2fffbf2de35b25a7f6d1cbae
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# ACSD-64753: Vorausgewählter Store in „Abholung im Store“ wird nicht aktualisiert, wenn sich die Versandadresse ändert

Mit dem Patch ACSD-64753 wird das Problem behoben, dass der vorausgewählte Shop nicht aktualisiert wurde, wenn eine neue Lieferadresse außerhalb des Serviceradius des ausgewählten Shops eingegeben wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 installiert ist. Die Patch-ID ist ACSD-64753. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der vorausgewählte Store wurde nicht aktualisiert, wenn eine neue Versandadresse außerhalb des Service-Radius des ausgewählten Stores eingegeben wurde.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL In-Store Delivery]**, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** navigieren.
1. Geben Sie einen gültigen [!DNL Google]-API-Schlüssel für die [!DNL Google Distance Provider] an. Navigieren Sie dazu zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Fügen Sie eine neue Quelle hinzu (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**) und legen Sie die folgenden Werte fest:
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Ja*
   * **[!UICONTROL Country United]**: *States*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Carol Stream*
   * **[!UICONTROL Postcode]**: *60188*
1. Fügen Sie einen neuen Stock hinzu (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**), weisen Sie ihm die neue Quelle und die Haupt-Website zu.
1. Bearbeiten Sie ein beliebiges Produkt, weisen Sie das Produkt dem neuen Source zu, Auf Lager und Menge > *0*.
1. Warten Sie, bis die Neuindizierung abgeschlossen ist.
1. Erstellen Sie in der Storefront einen neuen Kunden und fügen Sie dann eine kalifornische Adresse als Standard für Abrechnung und Versand hinzu.
1. Fügen Sie diesem Kunden eine weitere nicht standardmäßige Adresse für Illinois hinzu.
1. Fügen Sie das Produkt zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
1. Lassen Sie die Versandadresse „Kalifornien“ ausgewählt und wählen Sie **[!UICONTROL Pick in Store]** Versandart aus. Klicken Sie auf **[!UICONTROL Next]**.

<u>Erwartete Ergebnisse</u>:

Da die kalifornische Adresse außerhalb des maximalen Suchradius (200 km) liegt, sollte der Illinois Source für den Kunden nicht verfügbar sein.

<u>Tatsächliche Ergebnisse</u>:

Die Quelle in Illinois kann ausgewählt werden und der Kunde kann zur Kasse gehen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
