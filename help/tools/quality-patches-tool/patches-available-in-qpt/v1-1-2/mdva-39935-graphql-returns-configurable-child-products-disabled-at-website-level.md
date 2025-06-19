---
title: 'MDVA-39935: GraphQL gibt konfigurierbare untergeordnete Produkte zurück, die auf Website-Ebene deaktiviert sind'
description: Mit dem Patch für MDVA-39935 Adobe Commerce wird das Problem behoben, dass GraphQL konfigurierbare untergeordnete Produkte zurückgibt, die auf Website-Ebene deaktiviert sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39935. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: b86b1595-ddd5-41ce-b126-287046462561
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-39935: GraphQL gibt konfigurierbare untergeordnete Produkte zurück, die auf Website-Ebene deaktiviert sind

Mit dem Patch für MDVA-39935 Adobe Commerce wird das Problem behoben, dass GraphQL konfigurierbare untergeordnete Produkte zurückgibt, die auf Website-Ebene deaktiviert sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39935. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL gibt konfigurierbare untergeordnete Produkte zurück, selbst wenn sie auf Website-Ebene deaktiviert wurden.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Option Nicht vorrätige Produkte anzeigen unter **Store** > **Configuration** > **Catalog** > **Inventory** > **Stock-Optionen** > **Nicht vorrätige Produkte anzeigen** > **Ja**.
1. Wählen Sie ein **konfigurierbares Produkt** aus, das mehr als zwei **Einfache Produkte** aufweist.
1. Deaktivieren Sie **Einfaches Produkt** und speichern Sie das **konfigurierbare Produkt**.
1. Rufen Sie die **Konfigurierbares Produkt**-Daten mithilfe von GraphQL ab.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Deaktivierte Produkte werden NICHT in den Variantenergebnissen angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Daten zu deaktivierten Produkten werden in den Variantenergebnissen abgerufen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
