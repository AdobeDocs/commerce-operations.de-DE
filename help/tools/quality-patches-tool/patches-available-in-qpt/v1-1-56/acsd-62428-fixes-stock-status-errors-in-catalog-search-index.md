---
title: 'ACSD-62428: Statusfehler im Katalogsuchindex'
description: Wenden Sie den Patch ACSD-62428 an, um das Problem zu beheben, bei dem der Wert "is_out_of_stock"im Katalogsuchindex falsch festgelegt ist, wenn die SKU nicht als durchsuchbares Attribut dient.
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: Statusfehler im Katalogsuchindex

Der Patch ACSD-62428 behebt das Problem, dass `is_out_of_stock` -Werte im Katalogsuchindex auf einen falschen Wert gesetzt werden, wenn das SKU-Attribut nicht als durchsuchbar festgelegt ist. Dieser Patch ist mit der Version [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 verfügbar. Die Patch-ID ist ACSD-62428. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Wert `is_out_of_stock` im Katalogsuchindex wird auf einen falschen Wert gesetzt, wenn die SKU nicht als durchsuchbares Attribut konfiguriert ist, was zu einer ungenauen Lagerdarstellung führt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine benutzerdefinierte [!UICONTROL Source] und benutzerdefinierte [!UICONTROL Stock].
1. Erstellen Sie drei einfache Produkte und weisen Sie ihr Inventar dem benutzerdefinierten [!UICONTROL Source] zu. Weisen Sie diese Produkte einer Kategorie zu.
1. Setzen Sie die *[!UICONTROL Inventory (MSI) Indexer]* zur einfacheren Replikation auf *[!UICONTROL Update on Save]*.
1. Setzen Sie die *[!UICONTROL Source Item Status]* auf *[!UICONTROL In Stock]* und weisen Sie eine *[!UICONTROL Quantity]* zu.
1. Speichern Sie das Produkt.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und öffnen Sie das Attribut **[!UICONTROL SKU]** .
1. Setzen Sie *[!UICONTROL Use In]* auf *[!UICONTROL No]*.
1. Ändern Sie die Produktmenge (stellen Sie sicher, dass sie nicht auf 0 gesetzt ist).
1. Speichern Sie das Produkt.

<u>Erwartete Ergebnisse</u>:

Der Wert `is_out_of_stock` gibt den Lagerstatus des Produkts genau an, selbst wenn die SKU kein durchsuchbares Attribut ist.

<u>Tatsächliche Ergebnisse</u>:

Der Wert `is_out_of_stock` ist falsch auf 1 gesetzt und das SKU-Attribut fehlt in den indizierten Daten.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
