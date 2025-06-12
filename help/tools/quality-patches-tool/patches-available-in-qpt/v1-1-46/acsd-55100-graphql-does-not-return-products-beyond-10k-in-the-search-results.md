---
title: 'ACSD-55100: [!DNL GraphQL]  gibt in den Suchergebnissen keine Produkte zurück, die länger als 10 KB sind'
description: Wenden Sie den Patch ACSD-55100 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL in den Suchergebnissen keine Produkte zurückgibt, die über *10k* hinausgehen.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück, die länger als 10.000 sind

>[!NOTE]
>
>Ein aktualisierter Patch ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) wurde veröffentlicht, um dasselbe Problem für die Versionen 2.4.6 - 2.4.6-p8 zu beheben. Weitere Informationen finden Sie unter [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

Mit dem Patch ACSD-55100 wird das Problem behoben, dass [!DNL GraphQL] in den Suchergebnissen keine Produkte über *10k* zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 installiert ist. Die Patch-ID ist ACSD-55100. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück *die über 10* hinausgehen.

<u>Voraussetzungen</u>:

Stellen Sie im **[!DNL OpenSearch]** sicher, dass Sie die neueste verfügbare Version verwenden.

Um das gemeldete Problem zu beheben, wird die Point-in-Time-Funktion eingeführt, die nach **[!DNL OpenSearch]** 2.5.0 verfügbar ist und Version 2.2 des `opensearch-project/opensearch-php`-Pakets erfordert.

Es besteht jedoch ein Konflikt mit der `magento/magento-cloud-metapackage`, die eine Abhängigkeit vom `opensearch-project/opensearch-php` angibt, die kleiner als Version 2.0.1 sein sollte.


Diese Abhängigkeit verhindert, dass das Paket [opensearch-project/opensearch-php] auf die neueste Version 2.2 aktualisiert wird.

Daher tritt der folgende Fehler auf und gibt für Produkte mit einem Wert von mehr als *10.000 null*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

Die vorhandene Abhängigkeit macht es schwierig, der `composer.json`-Datei direkt eine Version hinzuzufügen und das `opensearch-project/opensearch-php`-Paket auf Version 2.2 zu aktualisieren.

Um das Problem zu beheben, fügen Sie die folgende Zeile in Ihre `composer.json`-Hauptdatei unter dem erforderlichen Block ein. Stellen Sie anschließend erneut bereit, um das problematische Paket auf die neueste Version zu aktualisieren.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie den Katalog mit *15k*-Produkten.
1. Senden Sie die [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Erwartete Ergebnisse</u>:

total_count = *15k*
Sie sollten alle Produkte anzeigen können.

<u>Tatsächliche Ergebnisse</u>:

total_count = *10k*
Es können keine weiteren Produkte mehr angezeigt werden, nachdem der *10k* Batch.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
