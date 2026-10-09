---
title: 'ACSD-53750: Fehler „Beschädigtes Rohr oder geschlossene Verbindung“ während der Neuindizierung des multithreadfähigen CATALOG_PRODUCT_PRICE'
description: Wenden Sie den Patch ACSD-53750 an, um das Adobe Commerce-Problem zu beheben, bei dem während der Neuindizierung des Katalogprodukts mit mehreren Threads der Fehler „Broken Pipe“ oder „Closed Connection“ auftritt.
feature: Products
role: Admin, Developer
exl-id: 6c2f092f-a98e-4990-839c-a7291635f8af
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%
---
# ACSD-53750: *Rohrbruch oder geschlossene Verbindung* Fehler bei der Neuindizierung von Multithread-`catalog_product_price`

Mit dem Patch ACSD-53750 wird das Problem behoben, dass bei der Neuindizierung von Multithread-`catalog_product_price` ein Fehler *Rohrbruch oder geschlossene*&quot; auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-53750. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

*Rohrbruch oder geschlossene Verbindung* Bei der Neuindizierung von Multithread-`catalog_product_price` tritt ein Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie RabbitMQ.
1. Generieren von Beispieldaten mithilfe der angehängten `small.xml`.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** und setzen Sie **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Legen Sie den Dimensionsmodus für Indizes fest, die diesen unterstützen. Z. B. `catalog_product_price_website_and_customer_group` oder `customer_group`.

   ```shell
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Zurücksetzen der Indexer für `catalog_product_price` ausführen.

   ```shell
   bin/magento indexer:reset catalog_product_price
   ```

1. Führen Sie den Indexer für den Reset-Indexer mit mehreren Threads aus.

   ```shell
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Erwartete Ergebnisse</u>:

Keine Fehler auftreten.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird durch eine AMQP-Verbindung verursacht: *Rohrbruch oder geschlossene Verbindung*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
