---
title: 'ACSD-53925: CMS-Block kann nicht mit [!UICONTROL Product Carousel] gespeichert werden'
description: Wenden Sie den Patch ACSD-53925 an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator einen CMS-Block mit dem Produktkarussell nicht speichern kann, wenn der Dimensionsmodus für „CATALOG_PRODUCT_PRICE“ auf „Website“ festgelegt ist.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-53925: CMS-Block kann nicht mit *[!UICONTROL Product Carousel]* gespeichert werden

Mit dem Patch „ACSD-53925“ wird das Problem behoben, dass der Administrator einen CMS-Block nicht mit *[!UICONTROL Product Carousel]* speichern kann, wenn der Dimensionsmodus für `catalog_product_price` auf „Website“ festgelegt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.43 installiert ist. Die Patch-ID ist ACSD-53925. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator kann einen CMS-Block nicht mit *[!UICONTROL Product Carousel]* speichern, wenn der Dimensionsmodus für `catalog_product_price` auf „Website“ festgelegt ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei einfache Produkte:
   * simple1 - $10
   * simple2 - $20
1. Erstellen Sie das Bundle &quot;*bundle1-dyn*&quot; mit zwei Optionen auf der Grundlage einfacher Produkt-SKUs.
1. Festlegen des Dimensionsmodus für den Produktpreisindexer:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Wechseln Sie zu **[!UICONTROL Content]** > **[!UICONTROL Blocks]** und erstellen Sie einen neuen CMS-Block.
1. Bearbeiten Sie den Inhalt mithilfe von [!DNL Page Builder]:
   * *[!UICONTROL Row]* hinzufügen
   * *[!UICONTROL Products]* hinzufügen
   * *[!UICONTROL Product Carousel]* auswählen
   * Produkt-SKU eingeben - *bundle1-dyn*
1. Speichern Sie den CMS-Block.

<u>Erwartete Ergebnisse</u>:

Benutzende können ohne Fehler ein Produktkarussell hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

* In der Benutzeroberfläche wird eine Meldung angezeigt: *Beim Generieren dieses Inhalts ist leider ein Fehler aufgetreten*
* `var/log/exception.log` enthält den folgenden Fehler:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
