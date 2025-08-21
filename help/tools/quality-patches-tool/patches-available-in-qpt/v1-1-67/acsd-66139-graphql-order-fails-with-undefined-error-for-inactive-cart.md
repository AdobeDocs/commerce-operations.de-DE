---
title: 'ACSD-66139: GraphQL-Bestellung schlägt für inaktiven Warenkorb mit dem Fehler „UNDEFINED“ fehl'
description: Wenden Sie den Patch ACSD-66139 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL bei der Bestellung eines nicht vorhandenen oder inaktiven Warenkorbs einen NICHT DEFINIERTEN Fehlercode anstelle eines bestimmten zurückgibt, wenn Fehlermeldungen übersetzt werden.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139: GraphQL-Bestellung schlägt mit Fehler „UNDEFINED“ für inaktiven Warenkorb fehl

Mit dem Patch ACSD-66139 wird das Problem behoben, dass GraphQL bei der Bestellung eines nicht vorhandenen oder inaktiven Warenkorbs einen Fehlercode *UNDEFINED* anstelle eines bestimmten zurückgibt, wenn Fehlermeldungen übersetzt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66139. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL gibt bei *Bestellung eines nicht vorhandenen oder inaktiven* einen Fehlercode (UNDEFINED) anstelle eines bestimmten zurück, wenn die Fehlermeldung übersetzt wird.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie `app/i18n/Magento/de_DE/de_DE.csv` hinzu und schließen Sie die folgende Fehlerzeichenfolgenübersetzung ein:

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. Erstellen Sie eine Store-Ansicht im Admin-Bedienfeld. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**. Klicken Sie auf **[!UICONTROL Create Store View]** und geben Sie **[!UICONTROL Code]** den Code `test` ein.
1. Weisen Sie der neu erstellten Store-Ansicht `german` Sprache zu.
1. `setup:upgrade` und `setup:static-content:deploy -f` ausführen.
1. Führen Sie die folgende GraphQL-Abfrage mit der Kopfzeile „Store:test aus:

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>Erwartete Ergebnisse</u>:

Richtige Fehlerantwort:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>Tatsächliche Ergebnisse</u>:

Der zurückgegebene `error_code` lautet *UNDEFINED*:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
