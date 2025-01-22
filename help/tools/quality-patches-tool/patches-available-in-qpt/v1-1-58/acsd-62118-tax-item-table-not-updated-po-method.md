---
title: 'ACSD-62118: Tabelle „sales_order_tax_item“ für B2B-Bestellungen, die mit der [!UICONTROL Purchase Order]-Methode aufgegeben wurden, wurde nicht vollständig aktualisiert'
description: Wenden Sie den Patch ACSD-62118 an, um das Adobe Commerce-Problem zu beheben, bei dem die Tabelle „sales_order_tax_item“ nicht vollständig aktualisiert wird, wenn B2B-Bestellungen mit der [!UICONTROL Purchase Order]-Methode platziert werden.
feature: Purchase Orders, B2B
role: Admin, Developer
source-git-commit: 5812b90fe07a084a1d3487784d0f36a2b7958286
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# ACSD-62118: `sales_order_tax_item` Tabelle wurde für B2B-Bestellungen, die mit der [!UICONTROL Purchase Order]-Methode aufgegeben wurden, nicht vollständig aktualisiert

Der Patch ACSD-62118 behebt das Problem, dass die `sales_order_tax_item` nicht vollständig aktualisiert wird, wenn eine B2B-Bestellung mit der *[!UICONTROL Purchase Order]*-Methode aufgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-62118. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn B2B-Bestellungen mit der *[!UICONTROL Purchase Order]*-Methode aufgegeben werden, wird die `sales_order_tax_item`-Tabelle nicht vollständig aktualisiert. Dieses Problem betrifft Steuerberechnungen und die Auftragsverarbeitung. Insbesondere ist das `applied_taxes`-Array leer, wenn die Bestellung über die API abgefragt wird, und sowohl `tax_item_amount` als auch `tax_item_percent` sind NULL.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie Steuerregeln für **[!UICONTROL Product]** und **[!UICONTROL Shipping]** hinzu.
1. Aktivieren Sie die **[!UICONTROL Purchase Order]** in den Unternehmenseinstellungen.
1. Melden Sie sich als Admin-Benutzerin bzw. -Benutzer des Unternehmens an.
1. Platzieren Sie eine **[!UICONTROL Purchase Order]** mit einer Offline-Zahlungsmethode.
1. Nachdem die [!UICONTROL Purchase Order] automatisch genehmigt und in eine Bestellung konvertiert wurde, überprüfen Sie die Steuerdaten in der `sales_order_tax_item` und über die REST-API.

<u>Erwartete Ergebnisse</u>:

* Die `sales_order_tax_item` sollte `tax_item` Daten enthalten.
* Das `applied_taxes`-Array sollte die korrekten Steuerinformationen in der API-Antwort für Bestellungen anzeigen, ähnlich wie bei anderen Zahlungsmethoden (z. B. Scheck-/Zahlungsanweisung).

<u>Tatsächliche Ergebnisse</u>:

* Die `sales_order_tax_item`-Tabelle enthält keine `tax_item`.
* Die Arrays `applied_taxes` und `item_applied_taxes` sind in der API-Antwort für die *[!UICONTROL Purchase Order]* leer.
* Bei Verwendung der *[!UICONTROL Purchase Order]* Zahlungsmethode werden keine Steuerdaten angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
