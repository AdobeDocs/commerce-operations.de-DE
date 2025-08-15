---
title: 'ACSD-65331: Ausgewählter Store in [!UICONTROL Pick in Store] nach der Rückkehr zum Checkout gelöscht'
description: Wenden Sie den Patch ACSD-65331 an, um das Adobe Commerce-Problem zu beheben, bei dem der unter der Option [!UICONTROL Pick In Store] ausgewählte Store gelöscht wird, wenn Benutzer wiederholt zur Kaufbestätigungsseite zurückkehren.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331: Ausgewählter Store in **[!UICONTROL Pick in Store]** nach der Rückkehr zum Checkout gelöscht

Der Patch ACSD-65331 behebt das Problem, dass der ausgewählte Store unter der Option **[!UICONTROL Pick In Store]** gelöscht wird, wenn Benutzer wiederholt zur Kaufbestätigungsseite zurückkehren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-65331. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der unter der Option **[!UICONTROL Pick In Store]** ausgewählte Store wird gelöscht, wenn Benutzer wiederholt zur Kaufbestätigungsseite zurückkehren.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL In-Store Delivery]**, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** navigieren.
1. Konfigurieren Sie einen gültigen [!DNL Google]-API-Schlüssel für [!UICONTROL Google Distance Provider], indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]** navigieren.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** , um eine neue Quelle mit den folgenden Details hinzuzufügen:

   * **[!UICONTROL Latitude]**: *,917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Ja*
   * **[!UICONTROL Country]**: *Vereinigte Staaten*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Carol Stream*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** , um ein neues Lager zu erstellen.

   Weisen Sie diesem Bestand die neu erstellte Quelle und die Haupt-Website zu.
1. Bearbeiten Sie ein beliebiges Produkt und:

   1. Weisen Sie sie der neu erstellten Quelle zu.
   1. Setzen Sie den Status auf *[!UICONTROL In Stock]* und die Menge auf mehr als 0.

1. Führen Sie Ihre Neuindizierungen aus.
1. Erstellen Sie in der Storefront einen neuen Kunden und legen Sie eine kalifornische Adresse als standardmäßige Rechnungs- und Lieferadresse fest.
1. Hinzufügen einer zusätzlichen Adresse für Illinois zum selben Kunden (nicht standardmäßig).
1. Fügen Sie das konfigurierte Produkt zum Warenkorb hinzu und fahren Sie mit der **[!UICONTROL Checkout]** fort.
1. Wählen Sie die Adresse von Illinois aus, wählen Sie **[!UICONTROL Pick In Store]** als Versandmethode und klicken Sie auf **[!UICONTROL Next]**.
1. Warten Sie, bis die Quelle geladen ist, und klicken Sie auf **[!UICONTROL Next]**.
1. Navigieren Sie zurück zur Homepage.
1. Kehren Sie zur Seite **[!UICONTROL Checkout]** zurück.

<u>Erwartete Ergebnisse</u>:

Der ausgewählte Store sollte unter **[!UICONTROL Pick In Store]** verfügbar bleiben.

<u>Tatsächliche Ergebnisse</u>:

Der Versandschritt wird geladen und zu **[!UICONTROL Pick In Store]** umgeleitet, es ist jedoch kein Store sichtbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
