---
title: "ACSD-55100: [!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück, die über 10.000 hinausgehen."
description: Wenden Sie den Patch ACSD-55100 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL in den Suchergebnissen keine Produkte über *10 k* zurückgibt.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] gibt in den Suchergebnissen keine Produkte über 10.000 zurück

Der Patch ACSD-55100 behebt das Problem, dass [!DNL GraphQL] in den Suchergebnissen keine Produkte mehr als *10k* zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46 installiert ist. Die Patch-ID ist ACSD-55100. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück, die über *10k* hinausgehen.

<u>Voraussetzungen</u>:

Stellen Sie bei **[!DNL OpenSearch]** sicher, dass Sie die neueste verfügbare Version verwenden.

Um das gemeldete Problem zu beheben, wird die Funktion Point in Time eingeführt, die nach **[!DNL OpenSearch]** 2.5.0 verfügbar ist und Version 2.2 des `opensearch-project/opensearch-php`-Pakets erfordert.

Es gibt jedoch einen Konflikt mit dem `magento/magento-cloud-metapackage`, der eine Abhängigkeit vom `opensearch-project/opensearch-php`-Paket angibt, die kleiner als Version 2.0.1 sein sollte.


Diese Abhängigkeit verhindert, dass das Paket [opensearch-project/opensearch-php] auf die neueste Version 2.2 aktualisiert wird.

Daher tritt der folgende Fehler auf und gibt für Produkte mit mehr als *10.000* Null-Ergebnisse zurück.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

Aufgrund der bestehenden Abhängigkeit ist es schwierig, der Datei `composer.json` direkt eine Version hinzuzufügen und das Paket `opensearch-project/opensearch-php` auf Version 2.2 zu aktualisieren.

Um das Problem zu beheben, fügen Sie die folgende Zeile in Ihre Hauptdatei `composer.json` unter den erforderlichen Block ein. Stellen Sie anschließend erneut bereit, um das problematische Paket auf die neueste Version zu aktualisieren.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie den Katalog mit *15k* -Produkten.
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

Total_count = *15k*
Sie sollten in der Lage sein, alle Produkte anzuzeigen.

<u>Tatsächliche Ergebnisse</u>:

Total_count = *10k*
Sie können keine weiteren Produkte nach dem Batch *10k* anzeigen lassen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
