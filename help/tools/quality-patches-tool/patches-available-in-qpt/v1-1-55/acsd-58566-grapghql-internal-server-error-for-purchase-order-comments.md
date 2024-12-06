---
title: 'ACSD-58566: Interner GraphQL-Serverfehler für Bestellkommentare'
description: Wenden Sie den Patch ACSD-58566 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL einen internen Serverfehler zurückgibt, wenn das Feld "created_at"in der Mutation "addPurchaseOrderComment"abgefragt wird.
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
source-git-commit: 3b8cc44ea8d71982b8a2eb76d9d7ec2a5c3180b0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: Interner GraphQL-Serverfehler für Bestellkommentare

Der Patch ACSD-58566 behebt das Problem, bei dem beim Abfragen des Felds `created_at` in der `addPurchaseOrderComment`-Mutation ein Nullwert anstelle des erwarteten Datums zurückgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58566. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

GraphQL gibt einen internen Server-Fehler zurück, wenn das Feld `created_at` in der Mutation `addPurchaseOrderComment` abgefragt wird.

<u>Voraussetzungen</u>:

B2B-Module werden installiert und Unternehmen und Kaufaufträge sind aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie ein Kunden-Token für einen Unternehmensbenutzer.
1. Führen Sie die folgende Reihenfolge von GraphQL-Anforderungen aus:
   1. Erstellen Sie einen *Warenkorb* mit `customerCart`.
   1. Fügen Sie dem *Warenkorb* mithilfe von `addProductsToCart` ein Produkt hinzu.
   1. Platzieren Sie die Reihenfolge mit &quot;`placePurchaseOrder`&quot;.
   1. Fügen Sie der Bestellung einen Kommentar mit `addPurchaseOrderComment` hinzu.

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

Das Feld `created_at` gibt den Zeitpunkt des Bestellkommentars zurück.

<u>Tatsächliche Ergebnisse</u>:

Zeigt null anstelle des `created_at` -Datums an.

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

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
