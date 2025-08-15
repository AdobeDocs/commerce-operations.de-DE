---
title: 'MDVA-38447: Konfigurierbare untergeordnete Produkte, die einzeln nicht sichtbar sind, werden in der GraphQL-Antwort und in der langsamen MySQL-Abfrage zurückgegeben'
description: Der Patch für MDVA-38447 Adobe Commerce behebt das Problem, dass in der GraphQL-Antwort konfigurierbare untergeordnete Produkte mit der Meldung „Nicht einzeln sichtbar“ zurückgegeben werden und die langsame MySQL-Abfrage für GraphQL-Produkte mit dem Kategoriefilter läuft. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447: Konfigurierbare untergeordnete Produkte, die einzeln nicht sichtbar sind, werden in der GraphQL-Antwort und in der langsamen MySQL-Abfrage zurückgegeben

Der Patch für MDVA-38447 Adobe Commerce behebt das Problem, dass in der GraphQL-Antwort konfigurierbare untergeordnete Produkte mit der Meldung „Nicht einzeln sichtbar“ zurückgegeben werden und die langsame MySQL-Abfrage für GraphQL-Produkte mit dem Kategoriefilter läuft. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Konfigurierbare untergeordnete Produkte, die „einzeln nicht sichtbar“ sind, werden in der GraphQL-Antwort zurückgegeben, und die langsame MySQL-Abfrage für die Abfrage von GraphQL-Produkten mit dem Kategoriefilter.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einfachen Produkten, die auf **Nicht einzeln sichtbar** eingestellt sind.
1. Führen Sie eine **vollständige Neuindizierung** aus.
1. Eine **GraphQL-Abfrage ausführen** z. B.:

<pre>query getFilteredProducts(
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: Zeichenfolge
  $pageSize: Int!
  $currentPage: int!
) {
  PRODUCT(
    Filter: $filter
    sort: $sort
    Suche: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    items {
      -Name
      SKU
    }
  }
}</pre>

Variablen:

<pre>{„filter“:{„user_group“:{„eq“:“"}},„search“:„config-100“,„sort“:{},„pageSize“:200,„currentPage“:1}
</pre>

<u>Erwartete Ergebnisse</u>:

Produkte mit der Sichtbarkeitseinstellung „Nicht einzeln sichtbar“ werden nicht als Antwort zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Produkte mit der Einstellung „Sichtbarkeit nicht einzeln sichtbar“ werden als Antwort zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
