---
title: "ACSD-47292: Nicht vorrätige gebündelte Produkte sind in der GraphQL-Antwort nicht verfügbar"
description: Wenden Sie den Patch ACSD-47292 an, um das Adobe Commerce-Problem zu beheben, bei dem die nicht vorrätigen gebündelten Produkte nicht in der GraphQL-Antwort verfügbar sind, selbst wenn "Nicht vorrätige Produkte anzeigen"auf "Ja"eingestellt ist.
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292: Nicht vorrätige gebündelte Produkte sind in der GraphQL-Antwort nicht verfügbar

Der Patch ACSD-47292 behebt das Problem, dass die nicht vorrätig gebündelten Produkte nicht in der GraphQL-Antwort verfügbar sind, selbst wenn der Wert [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-47292. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die nicht vorrätigen gebündelten Produkte sind in der GraphQL-Antwort nicht verfügbar, selbst wenn [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* gesetzt ist.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** und legen Sie die [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* fest.
1. Erstellen Sie zwei einfache Produkte: s1 und s2.
1. Machen Sie s1 nicht vorrätig und nicht einzeln sichtbar und s2 ist vorrätig und nicht einzeln sichtbar, und weisen Sie sie einer Kategorie zu.
1. Erstellen Sie ein gebündeltes Produkt mit mindestens einem Optionsprodukt und weisen Sie dieser Option s1 und s2 zu (Eingabetyp &quot;RadioButton&quot;).
1. Speichern Sie das gebündelte Produkt und weisen Sie es einer Kategorie zu.
1. Gehen Sie zur Storefront und öffnen Sie dieses gebündelte Produkt. Sie sehen, dass die nicht vorrätige Option s1 grau, aber sichtbar ist.
1. Senden einer GraphQL-Anforderung:

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

Die Option &quot;s1 Bundle&quot;wird in der GraphQL-Antwort aufgeführt, da [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* festgelegt ist und auf der Storefront sichtbar ist.

<u>Tatsächliche Ergebnisse</u>:

Die Option &quot;s1 Bundle&quot;wird in der GraphQL-Antwort nicht aufgeführt.

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

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
