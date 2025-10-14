---
title: 'ACSD-47292: Nicht vorrätige gebündelte Produkte sind in der GraphQL-Antwort nicht verfügbar'
description: Wenden Sie den ACSD-47292-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die nicht vorrätigen gebündelten Produkte in der GraphQL-Antwort nicht verfügbar sind, selbst wenn die Option „Nicht vorrätige Produkte anzeigen“ auf „Ja“ gesetzt ist.
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292: Nicht vorrätige gebündelte Produkte sind in der GraphQL-Antwort nicht verfügbar

Mit dem Patch ACSD-47292 wird das Problem behoben, dass die nicht vorrätigen gebündelten Produkte in der GraphQL-Antwort nicht verfügbar sind, selbst wenn die [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-47292. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die nicht vorrätigen gebündelten Produkte sind in der GraphQL-Antwort nicht verfügbar, selbst wenn die [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* festgelegt ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** und legen Sie die [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* fest.
1. Erstellen Sie zwei einfache Produkte, s1 und s2.
1. Machen Sie S1 als nicht vorrätig und nicht einzeln sichtbar und S2 als vorrätig und nicht einzeln sichtbar und weisen Sie sie einer Kategorie zu.
1. Erstellen Sie ein gebündeltes Produkt mit mindestens einem Optionsprodukt und weisen Sie dieser Option s1 und s2 zu (Eingabetyp „RadioButton„).
1. Speichern Sie das gebündelte Produkt und weisen Sie es einer Kategorie zu.
1. Gehen Sie zur Storefront und öffnen Sie dieses gebündelte Produkt. Die nicht vorrätige Option S1 ist grau, aber sichtbar.
1. Senden einer GraphQL-Anfrage:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Erwartete Ergebnisse</u>:

Die Option S1-Bundle wird in der GraphQL-Antwort aufgeführt, da [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* festgelegt ist, und sie ist in der Storefront sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Die Bundle-Option S1 wird in der GraphQL-Antwort nicht aufgeführt.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
