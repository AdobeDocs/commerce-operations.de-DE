---
title: 'ACSD-58566: Interner GraphQL-Server-Fehler bei Bestellkommentaren'
description: Wenden Sie den Patch ACSD-58566 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL bei der Abfrage des Felds „created_at“ in der Mutation „addPurchaseOrderComment“ einen internen Server-Fehler zurückgibt.
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
source-git-commit: ffa9b7151f226087b62a8b2e265a96de2e4caedf
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: Interner GraphQL-Server-Fehler bei Bestellkommentaren

Mit dem Patch „ACSD-58566“ wird das Problem behoben, dass die Abfrage des `created_at` Felds in der `addPurchaseOrderComment`-Mutation einen Nullwert anstelle des erwarteten Datums-/Uhrzeitwerts zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58566. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL gibt bei der Abfrage des `created_at` in der `addPurchaseOrderComment`-Mutation einen internen Server-Fehler zurück.

<u>Voraussetzungen</u>:

B2B-Module werden installiert und Firmen- und Bestellungen sind aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Generieren eines Kunden-Tokens für einen Firmenbenutzer.
1. Führen Sie die folgende Abfolge von GraphQL-Anfragen durch:
   1. Erstellen Sie einen *Warenkorb* mithilfe von `customerCart`.
   1. Fügen Sie mit `addProductsToCart` ein Produkt zum *Warenkorb* hinzu.
   1. Bestellung mit `placePurchaseOrder` aufgeben.
   1. Fügen Sie der Bestellung mithilfe von `addPurchaseOrderComment` einen Kommentar hinzu.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Das Feld `created_at` gibt das Datum und die Uhrzeit des Bestellkommentars zurück.

<u>Tatsächliche Ergebnisse</u>:

Zeigt null anstelle des `created_at` an.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
