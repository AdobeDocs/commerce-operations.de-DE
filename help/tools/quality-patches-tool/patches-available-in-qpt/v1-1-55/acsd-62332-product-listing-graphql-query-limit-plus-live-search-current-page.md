---
title: 'ACSD-62332: GraphQL-Abfrage mit Produktliste ist auf 10.000 Produkte beschränkt und  [!DNL Live Search] setzt die aktuelle Seite auf 1'
description: Wenden Sie den Patch ACSD-62332 an, um die Adobe Commerce-Probleme zu beheben, bei denen die GraphQL-Abfrage mit der Produktliste auf eine Gesamtanzahl von 10.000 Produkten beschränkt ist und bei der [!DNL Live Search] die aktuelle Seite in den Suchkriterien auf *1* statt auf Seite *2* setzt, wenn die Anfrage über GraphQL erfolgt.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 276fe6ca8d1166a8f4254aca5d49cbb4b1aa607b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: GraphQL-Abfrage mit Produktliste ist auf 10.000 Produkte beschränkt und [!DNL Live Search] setzt die aktuelle Seite auf 1

>[!NOTE]
>
>Dieser Patch ist eine aktualisierte Version von [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) und ersetzt [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) in 2.4.6 - 2.4.6-p8-Versionen. Weitere Informationen finden Sie in den entsprechenden Artikeln .

Der Patch ACSD-62332 behebt die Probleme, bei denen die GraphQL-Abfrage mit Produktliste auf 10.000 Produkte beschränkt ist und bei der [!DNL Live Search] die aktuelle Seite in den Suchkriterien bei der Abfrage über GraphQL auf *1* anstelle von Seite *2* setzt. `total_count` Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-62332. Beachten Sie, dass die Probleme in Adobe Commerce 2.4.7 behoben wurden.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage mit der Produktliste ist auf eine Gesamtanzahl von 10.000 Produkten beschränkt und wobei [!DNL Live Search] die aktuelle Seite in den Suchkriterien auf *1* anstelle von Seite *2* festlegt, wenn die Abfrage über GraphQL erfolgt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
