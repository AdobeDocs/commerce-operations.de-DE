---
title: '"MDVA-38447: "Nicht einzeln sichtbar" konfigurierbare Kinderprodukte werden in der GraphQL-Antwort und langsamen MySQL-Abfrage zurückgegeben."'
description: Der MDVA-38447 Adobe Commerce-Patch behebt das Problem, dass konfigurierbare untergeordnete Produkte vom Typ "Nicht einzeln sichtbar"in der GraphQL-Antwort zurückgegeben werden und die MySQL-Abfrage für GraphQL-Produkte mit Kategoriefilter verlangsamt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-38447: Konfigurierbare Kinderprodukte werden in der GraphQL-Antwort und langsamen MySQL-Abfragen zurückgegeben.

Der MDVA-38447 Adobe Commerce-Patch behebt das Problem, dass konfigurierbare untergeordnete Produkte vom Typ &quot;Nicht einzeln sichtbar&quot;in der GraphQL-Antwort zurückgegeben werden und die MySQL-Abfrage für GraphQL-Produkte mit Kategoriefilter verlangsamt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare untergeordnete Produkte, die nicht einzeln sichtbar sind, werden in der GraphQL-Antwort zurückgegeben und die MySQL-Abfrage für die GraphQL-Produktabfrage mit Kategoriefilter verlangsamt.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert sein.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einfachen Produkten, die auf **Nicht einzeln sichtbar** eingestellt sind.
1. Führen Sie eine **vollständige Neuindizierung** aus.
1. Führen Sie eine **GraphQL-Abfrage** wie folgt aus:

<pre>query getFilteredProducts(
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) {
  products(
    filter: $filter
    sort: $sort
    search: $search
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
      sku
    }
  }
}</pre>

Variablen:

<pre>{"filter":{"user_group":{"eq":"},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Erwartete Ergebnisse</u>:

Produkte mit Sichtbarkeit, die auf &quot;Nicht einzeln sichtbar&quot;gesetzt sind, werden als Antwort nicht zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Produkte, deren Sichtbarkeit auf &quot;Nicht einzeln sichtbar&quot;festgelegt ist, werden als Antwort zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) verfügbare Patches.
