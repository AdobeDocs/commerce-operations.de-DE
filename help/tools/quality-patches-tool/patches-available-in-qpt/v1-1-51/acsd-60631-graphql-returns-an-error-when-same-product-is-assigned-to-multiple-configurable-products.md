---
title: "ACSD-60631: GraphQL gibt einen Fehler zurück, wenn dasselbe Produkt mehreren konfigurierbaren Produkten zugewiesen ist."
description: Wenden Sie den Patch ACSD-60631 an, um das Adobe Commerce-Problem zu beheben, bei dem eine GraphQL-Abfrage einen Fehler zurückgibt, wenn dasselbe Produkt mehreren konfigurierbaren Produkten zugewiesen ist.
feature: Attributes, GraphQL
role: Admin, Developer
source-git-commit: 093c5d030d38a108d8acb6e59455513db147dfdf
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-60631: GraphQL-Abfrage gibt einen Fehler zurück, wenn dasselbe Produkt mehreren konfigurierbaren Produkten zugewiesen ist

Der Patch ACSD-60631 behebt das Problem, bei dem eine GraphQL-Abfrage einen Fehler zurückgibt, wenn dasselbe Produkt mehreren konfigurierbaren Produkten zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60631. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine GraphQL-Abfrage gibt einen Fehler zurück, wenn dasselbe Produkt mehreren konfigurierbaren Produkten zugewiesen ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit dem Attribut *Farbe*.
1. Erstellen Sie *2* konfigurierbare Produkte und weisen Sie das einfache Produkt aus Schritt *1* zu.
1. Führen Sie die GraphQL-Abfrage aus (filtern Sie die Produkte nach dem Wert `url_key` der konfigurierbaren Produkte).

```GraphQL
{
  products(filter: { url_key: { in : ["configurable-1", "configurable-2"] } }) {
    items {
      id
      attribute_set_id
      name
      sku
      __typename
      price_range{
        minimum_price{
          regular_price{
            value
            currency
          }
        }
      }
      categories {
        id
      }
      ... on ConfigurableProduct {
        configurable_options {
          id
          attribute_id_v2
          label
          position
          use_default
          attribute_code
          values {
            value_index
            label
          }
          product_id
        }
        variants {
          product {
            id
            name
            sku
            attribute_set_id
            ... on PhysicalProductInterface {
              weight
            }
            price_range{
              minimum_price{
                regular_price{
                  value
                  currency
                }
              }
            }
          }
          attributes {
            uid
            label
            code
            value_index
          }
        }
      }
    }
  }
}
```

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage gibt keine Fehler zurück.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage gibt einen Fehler zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.