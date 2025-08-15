---
title: 'MDVA-39482: Produkt ist nicht vorrätig, wenn es mit ''0'' Menge und aktivierten Nachbestellungen importiert wird'
description: Der MDVA-39482 behebt das Problem, dass das Produkt nicht vorrätig ist, wenn es mit der Menge „0“ importiert wird, wenn MSI und Nachbestellungen aktiviert sind und der Schwellenwert für nicht vorrätige Artikel auf einen Minuswert festgelegt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-39482. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Data Import/Export, Orders, Products
role: Admin
exl-id: 9d705ebf-2372-4e59-b447-cdb5b0db32f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: Produkt ist nicht vorrätig, wenn es mit &#39;0&#39; Menge und aktivierten Nachbestellungen importiert wird

Der MDVA-39482 behebt das Problem, dass das Produkt nicht vorrätig ist, wenn es mit der Menge „0“ importiert wird, wenn MSI und Nachbestellungen aktiviert sind und der Schwellenwert für nicht vorrätige Artikel auf einen Minuswert festgelegt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-39482. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Produkt ist nicht vorrätig, wenn es mit der Menge „0“ importiert wird, wenn MSI und Nachbestellungen aktiviert sind und der Schwellenwert für nicht vorrätige Artikel auf einen Minuswert festgelegt ist.

<u>Voraussetzungen</u>:

1. MSI- und Beispieldaten müssen installiert sein.
1. Navigieren Sie **Stores** > **Konfigurationen** > **Katalog** > **Inventar**:
   * Rückstände auf „Menge unter 0 zulassen“ einstellen
   * Setzen Sie den Schwellenwert für Nicht vorrätige Artikel auf &quot;-10“

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass die SKU **Auf Lager** ist und die Menge **24-MB01** hat.
1. Importieren Sie die CSV-Datei der Stock-Quellen. Stellen Sie sicher, dass Sie im Entitätstyp „Lagerquellen“ auswählen:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Überprüfen Sie den Lagerstatus des Produkts, nachdem die Lagerquellen importiert wurden.

<u>Erwartete Ergebnisse</u>:

24-MB01 ist **Auf Lager** in Storefront.

<u>Tatsächliche Ergebnisse</u>:

24-MB01 ist **Nicht vorrätig** in der Storefront.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de).
