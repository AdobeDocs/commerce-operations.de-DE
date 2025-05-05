---
title: 'ACSD-62332: Die GraphQL-Abfrage zur Produktliste ist auf 10.000 Produkte beschränkt und  [!DNL Live Search]  die aktuelle Seite auf 1'
description: Wenden Sie den Patch ACSD-62332 an, um die Adobe Commerce-Probleme zu beheben, bei denen die GraphQL-Abfrage zur Produktliste auf eine Gesamtzahl von 10.000 Produkten beschränkt ist und  [!DNL Live Search] die aktuelle Seite bei der Abfrage über GraphQL auf *1* statt auf Seite *2* setzt.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
source-git-commit: ee0d0afc6231a08f0fbae29b5be2078cf7a4f940
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: Die GraphQL-Abfrage für die Produktliste ist auf 10.000 Produkte beschränkt und [!DNL Live Search] die aktuelle Seite auf 1

>[!NOTE]
>
>Dieser Patch ist eine aktualisierte Version von [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) und ersetzt [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) in den Versionen 2.4.6 bis 2.4.6-p8. Weitere Einzelheiten finden Sie in den entsprechenden Artikeln.

Mit dem Patch ACSD-62332 werden die Probleme behoben, bei denen die GraphQL-Abfrage zur Produktliste auf eine `total_count` von 10.000 Produkten beschränkt ist und [!DNL Live Search] die aktuelle Seite bei der Abfrage über die GraphQL auf *1* anstelle von *2* setzt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-62332. Beachten Sie, dass die Probleme in Adobe Commerce 2.4.7 behoben wurden.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage zur Produktliste ist auf eine Gesamtzahl von 10.000 Produkten beschränkt. Dabei setzt [!DNL Live Search] in den Suchkriterien bei der Abfrage über GraphQL die aktuelle Seite auf ** statt *2*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
