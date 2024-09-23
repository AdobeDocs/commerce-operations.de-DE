---
title: "MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten, die nicht in der richtigen Preisspanne angezeigt werden"
description: Der Patch MDVA-40488 behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der richtigen Preisspanne angezeigt

Der Patch MDVA-40488 behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der korrekten Preisspanne angezeigt.

<u>Voraussetzungen</u>:

Gehen Sie zu Commerce Admin > **stores** > **configuration** > **catalog** > **Inventory** > **stock options** und stellen Sie die Konfiguration **Nicht vorrätige Produkte anzeigen** auf *Ja* ein.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen Produkten. Beispiel: einfache Produkte Rot und Braun.
1. Legen Sie den Bestand des einfachen Produkts Rot fest, legen Sie den Lagerstatus auf *Auf Lager* fest und setzen Sie dann den Status Produkt aktivieren auf *Nein*.
1. Legen Sie den Bestand des einfachen Produkts Braun fest und setzen Sie dann den Status Produkt aktivieren auf *Ja*.
1. Stellen Sie sicher, dass der konfigurierbare Produktspeicherstatus *Auf Lager* ist.
1. Ändern Sie den Lagerbestand des einfachen Produkts braun auf 0 und legen Sie den Lagerstatus auf *Nicht auf Lager* fest.
1. An dieser Stelle ist der konfigurierbare Produktspeicherstatus immer noch *Auf Lager*.
1. Führen Sie eine Neuindizierung durch.
1. Überprüfen Sie die `min_price` und `max_price` für das konfigurierbare Produkt in der `catalog_product_index_price` DB-Tabelle. Die beiden Werte sind auf 0 gesetzt.
1. Wenn wir jedoch den konfigurierbaren Produktstatus auf *Nicht vorrätig* setzen und eine Neuindizierung vornehmen, können wir die Werte ungleich null `min_price` und `max_price` des konfigurierbaren Produkts sehen.

<u>Erwartete Ergebnisse</u>:

Wenn alle untergeordneten Produkte *nicht auf Lager* sind und das konfigurierbare Produkt selbst ebenfalls *nicht auf Lager ist*, wird der Preis anhand aller untergeordneten Produkte berechnet.

<u>Tatsächliche Ergebnisse</u>:

Die Werte `min_price` und `max_price` für das konfigurierbare Produkt in der `catalog_product_index_price` DB-Tabelle werden auf 0 gesetzt, wenn der konfigurierbare Bestandsstatus *Auf Lager* ist, aber wenn es *Nicht auf Lager* ist, werden sie zu Werten ungleich null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
