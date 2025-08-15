---
title: 'ACSD-52801: GraphQL-Produktfilterabfrage zeigt keine Ergebnisse für teilweise Übereinstimmung'
description: Wenden Sie den ACSD-52801-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Produktfilterabfrage keine Ergebnisse für teilweise Übereinstimmungen zeigt.
feature: Products
role: Admin, Developer
exl-id: 946a7189-60b2-4812-92ca-ed7ba35b2488
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-52801: GraphQL-Produktfilterabfrage zeigt keine Ergebnisse für teilweise Übereinstimmung

>[!NOTE]
>
>Ein aktualisierter Patch ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) wurde veröffentlicht, um dasselbe Problem für die Versionen 2.4.6 - 2.4.6-p8 zu beheben. Er ersetzt den ACSD-52801 Patch ab Version 2.4.6. Weitere Informationen finden Sie unter [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

Der Patch ACSD-52801 behebt das Problem, dass die GraphQL-Produktfilterabfrage keine Ergebnisse zu teilweisen Übereinstimmungen anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-52801. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2, 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Produktfilterabfrage zeigt keine Ergebnisse für Teilübereinstimmung.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Instanz mit Beispieldaten.
1. Führen Sie die folgende GraphQL-Abfrage aus.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u>Erwartete Ergebnisse</u>:

Sie ermöglicht ähnliche Übereinstimmungsergebnisse wie bei der erweiterten Suche in der Storefront, indem das Attribut `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL]) hinzugefügt wird, um die erforderlichen Ergebnisse zu steuern. [!UICONTROL FULL] entspricht vollständigen Wörtern, und [!UICONTROL PARTIAL] stimmt mit partiellen Wörtern überein, wie im Leben enthalten.

<u>Tatsächliche Ergebnisse</u>:

Die Produktfilterabfrage gibt keine Ergebnisse von Teilübereinstimmungen für Suchbegriffe zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
