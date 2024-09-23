---
title: "ACSD-53925: CMS-Block kann nicht mit [!UICONTROL Product Carousel] gespeichert werden."
description: Wenden Sie den Patch ACSD-53925 an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator keinen CMS-Block mit dem Produktkarussell speichern kann, wenn der Dimensionsmodus für "catalog_product_price"auf "website"festgelegt ist.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-53925: CMS-Block kann nicht mit *[!UICONTROL Product Carousel]* gespeichert werden

Der Patch ACSD-53925 behebt das Problem, dass der Administrator keinen CMS-Block mit *[!UICONTROL Product Carousel]* speichern kann, wenn der Dimensionsmodus für `catalog_product_price` auf &quot;website&quot;festgelegt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.43 installiert ist. Die Patch-ID ist ACSD-53925. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator kann einen CMS-Block nicht mit &quot;*[!UICONTROL Product Carousel]*&quot;speichern, wenn der Dimensionsmodus für &quot;`catalog_product_price`&quot;auf &quot;Website&quot;festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei einfache Produkte:
   * simple1 - 10$
   * simple2 - 20$
1. Erstellen Sie ein Bundle-Produkt &quot;*bundle1-dyn*&quot;mit zwei Optionen, die auf einfachen Produkt-SKUs basieren.
1. Legen Sie den Dimensionsmodus für den Produktpreisindex fest:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Blocks]** und erstellen Sie einen neuen CMS-Block.
1. Bearbeiten Sie den Inhalt mit [!DNL Page Builder]:
   * Element *[!UICONTROL Row]* hinzufügen
   * Element *[!UICONTROL Products]* hinzufügen
   * Wählen Sie *[!UICONTROL Product Carousel]*
   * Produkt-SKU eingeben - *bundle1-dyn*
1. Speichern Sie den CMS-Block.

<u>Erwartete Ergebnisse</u>:

Benutzer können problemlos ein Produktkarussell hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

* In der Benutzeroberfläche wird eine Meldung ausgegeben: *Es tut uns leid, es ist ein Fehler beim Generieren dieses Inhalts aufgetreten*
* `var/log/exception.log` enthält den folgenden Fehler:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
