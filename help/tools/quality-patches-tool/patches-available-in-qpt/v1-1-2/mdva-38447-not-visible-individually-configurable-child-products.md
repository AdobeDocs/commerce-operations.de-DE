---
title: 'MDVA-38447: Konfigurierbare untergeordnete Produkte, die einzeln nicht sichtbar sind, werden in der GraphQL-Antwort und in der langsamen MySQL-Abfrage zurückgegeben'
description: Der Patch für MDVA-38447 Adobe Commerce behebt das Problem, dass in der GraphQL-Antwort konfigurierbare untergeordnete Produkte mit der Meldung „Nicht einzeln sichtbar“ zurückgegeben werden und die langsame MySQL-Abfrage für GraphQL-Produkte mit dem Kategoriefilter läuft. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# MDVA-38447: Konfigurierbare untergeordnete Produkte, die einzeln nicht sichtbar sind, werden in der GraphQL-Antwort und in der langsamen MySQL-Abfrage zurückgegeben

Der Patch für MDVA-38447 Adobe Commerce behebt das Problem, dass in der GraphQL-Antwort konfigurierbare untergeordnete Produkte mit der Meldung „Nicht einzeln sichtbar“ zurückgegeben werden und die langsame MySQL-Abfrage für GraphQL-Produkte mit dem Kategoriefilter läuft. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
      name
      SKU
    }
  }
}</pre>

Variablen:

<pre>{„filter“:{„user_group“:{„eq“:“""}},„search“:„config-100“,„sort“:{},„pageSize“:200,„currentPage“:1}
</pre>

<u>Erwartete Ergebnisse</u>:

Produkte mit der Sichtbarkeitseinstellung „Nicht einzeln sichtbar“ werden nicht als Antwort zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Produkte mit der Einstellung „Sichtbarkeit nicht einzeln sichtbar“ werden als Antwort zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
