---
title: "MDVA-40609: Produktdaten in Kataloginventory_stock_status-Tabelle deaktiviert"
description: Der Patch MDVA-40609 behebt das Problem, dass die Daten zu deaktivierten Produkten nicht in der Indextabelle "cataloginventory_stock_status"angezeigt werden, was zur Anzeige falscher Produktmengen führte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40609. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609: Produktdaten in Kataloginventory_stock_status-Tabelle wurden deaktiviert.

Der Patch MDVA-40609 behebt das Problem, dass die Daten zu deaktivierten Produkten nicht in der Indextabelle `cataloginventory_stock_status` angezeigt werden, was dazu führt, dass falsche Produktmengen angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40609. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Deaktivierte Produktdaten werden nicht in der Indextabelle `cataloginventory_stock_status` angezeigt, was dazu führt, dass falsche Produktmengen angezeigt werden.

<u>Voraussetzungen</u>:

Das Lagerbestandsmodul ist installiert.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie zwei Websites mit Geschäften und Store-Ansichten ein.
1. Erstellen Sie eine zusätzliche Quelle und ein weiteres Lager.
1. Fügen Sie ein einfaches Produkt hinzu:
   * Setzen Sie &quot;Produkt aktivieren&quot;auf &quot;*Nein*&quot;.
   * Weisen Sie zwei Quellen mit Source Item Status = Instock und Menge größer als null zu.
1. Speichern Sie das Produkt.
1. Überprüfen Sie die Registerkarte **Produktverkaufsmenge**.

<u>Erwartete Ergebnisse</u>:

Beide Bestände haben Werte über null eingegeben.

<u>Tatsächliche Ergebnisse</u>:

Ein Bestand hat einen Nullwert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
