---
title: '"MDVA-39482: Das Produkt wird nicht vorrätig eingeführt, wenn es mit "0"Menge mit aktivierten Rückständen importiert wird."'
description: Der MDVA-39482 behebt das Problem, dass das Produkt nicht mehr vorrätig ist, wenn es mit "0"importiert wird, wenn MSI und Rückorder aktiviert sind und der Schwellenwert für nicht vorrätige Waren auf einen Minuswert gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-39482. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: Das Produkt wird nicht mehr vorrätig eingeführt, wenn es mit &quot;0&quot; Menge importiert wird und die Backorder aktiviert sind

Der MDVA-39482 behebt das Problem, dass das Produkt nicht mehr vorrätig ist, wenn es mit &quot;0&quot;importiert wird, wenn MSI und Rückorder aktiviert sind und der Schwellenwert für nicht vorrätige Waren auf einen Minuswert gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-39482. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt wird nicht mehr vorrätig, wenn es mit der Menge &quot;0&quot;importiert wird, wenn MSI und Rückorder aktiviert sind und der Schwellenwert für nicht vorrätige Produkte auf einen Minuswert gesetzt ist.

<u>Voraussetzungen</u>:

1. MSI und Beispieldaten müssen installiert sein.
1. Wechseln Sie zu **Stores** > **Konfigurationen** > **Katalog** > **Bestand**:
   * Legen Sie &quot;Rückläufe&quot;auf &quot;Menge unter 0 zulassen&quot;fest.
   * Nicht vorrätiger Schwellenwert auf &quot;-10&quot; setzen

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass die SKU **Auf Lager** ist und die Menge **24-MB01** aufweist.
1. Importieren Sie die CSV-Datei der Lagerquellen. Stellen Sie sicher, dass Sie unter Entitätstyp &quot;Stock Sources&quot;auswählen:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Überprüfen Sie den Lagerstatus des Produkts, nachdem die Lagerquellen importiert wurden.

<u>Erwartete Ergebnisse</u>:

24 MB01 ist **Auf Lager** im Storefront.

<u>Tatsächliche Ergebnisse</u>:

24 MB01 ist **nicht auf Lager** in der Storefront.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbare Patches.
