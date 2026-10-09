---
title: 'ACSD-46519: [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] Abfrage gibt 0 für Ankerkategorien zurück.'
description: Wenden Sie den ACSD-46519-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem bei Verwendung der [!UICONTROL categoryList]-[!DNL GraphQL]-Methode zum Abrufen untergeordneter Kategorien der [!UICONTROL product_count] für übergeordnete Kategorien als 0 angezeigt wird.
feature: Categories, GraphQL, Products
role: Admin
exl-id: 7becaa4e-421a-4983-ac73-f5b58fc45d8f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%
---
# ACSD-46519: [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] Abfrage gibt 0 für Ankerkategorien zurück.

Der Patch ACSD-46519 löst das Problem, dass der [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] Abfrage für Ankerkategorien 0 zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23 installiert ist. Die Patch-ID ist ACSD-46519. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die [!UICONTROL categoryList] [!DNL GraphQL]-Methode verwendet wird, um untergeordnete Kategorien abzurufen, wird die [!UICONTROL product_count] für übergeordnete Kategorien als 0 angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Verwenden Sie die folgende [!DNL GraphQL]-Anfrage, um die Kategoriehierarchie mit [!UICONTROL product_count] abzurufen:

<pre><code>
{
  categoryList(filters: { ids: { eq: "2" } }) {
    id
    name
    product_count
    level
    children {
      name
      product_count
      level
      children {
        name
        product_count
        level
        children {
          name
          product_count
          level
          children {
            name
            product_count
            level
          }
        }
      }
    }
  }
}
</code></pre>

<u>Erwartete Ergebnisse</u>:

Wenn die übergeordnete Kategorie eine verankerte Kategorie ist, sollte die [!UICONTROL product_count] die Summe der Produktzahlen der untergeordneten Kategorie auf jeder Ebene anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Wenn die übergeordnete Kategorie eine verankerte Kategorie ist, werden die Produkte für die Kategorie 2 als 0 angezeigt und weiter unten.

<pre><code>
{
    "data": {
        "categoryList": [
            {
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": [
                    {
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    },
                    {
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": [
                            {
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            },
                            {
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            }
                        ]
                    },
                    ...
                ]
            }
        ]
    }
}
</code></pre>

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
