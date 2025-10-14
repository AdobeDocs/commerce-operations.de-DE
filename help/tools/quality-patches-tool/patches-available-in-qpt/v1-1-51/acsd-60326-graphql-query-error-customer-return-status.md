---
title: 'ACSD-60326: Die GraphQL-Abfrage zum [!UICONTROL Returns] des Kunden gibt einen Fehler aus'
description: Wenden Sie den Patch ACSD-60326 an, um das Adobe Commerce-Problem zu beheben, bei dem in der GraphQL-Abfrage zum [!UICONTROL Returns] ein Fehler auftritt.
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: Die GraphQL-Abfrage zum [!UICONTROL Returns] des Kunden gibt einen Fehler aus

Mit dem Patch ACSD-60326 wird das Problem behoben, dass in der GraphQL-Abfrage zum [!UICONTROL Returns] ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL-Abfrage zum [!UICONTROL Returns] des Kunden gibt einen Fehler aus.

<u>Schritte zur Reproduktion</u>:

1. Initialisieren einer neuen Instanz mit Beispieldaten
1. Navigieren Sie in der *[!UICONTROL Admin]* Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** und setzen Sie **[!UICONTROL Enable RMA on Storefront]** auf *Ja*.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** und füllen Sie die Adresse aus.
1. Ändern Sie das Kennwort für die `roni_cost@example.com`.
1. Melden Sie sich beim Admin-Bedienfeld an und geben Sie eine Bestellung für die `roni_cost@example.com` mit den folgenden Produkten auf:
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Green*
1. *[!UICONTROL Invoice]* und *[!UICONTROL Shipment]* für diese Bestellung erstellen.
1. Wählen Sie **[!UICONTROL Create Returns]** aus.
1. Navigieren Sie zu **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** und:
   * Wählen Sie *WSH12-32-Red* und *WSH12-32-Purple*
   * Klicken Sie auf **[!UICONTROL Add Selected Products to returns]**:
      * **[!UICONTROL Requested]** = *1*
      * Setzen Sie **[!UICONTROL Return Reason]** auf *Out of Service*
      * **[!UICONTROL Item Condition]** auf *Geöffnet*
      * **[!UICONTROL Resolution]** auf *Rückerstattung*
   * Klicken Sie auf **[!UICONTROL Submit Returns]**.
1. Öffnen Sie **[!UICONTROL Returns]** und wählen Sie links **[!UICONTROL Return Items]** aus.
   * Setzen Sie **[!UICONTROL Authorized]** für beide *=* 1
   * **[!UICONTROL Status]** als *Autorisiert* für *WSH12-32-Purple*
   * Legen Sie **[!UICONTROL Status]** als *Verweigert* für *WSH12-32-Red* fest
   * **[!UICONTROL Save]** klicken
1. Erstellen Sie eine neue Bestellung mit denselben Produkten.
1. Erstellen Sie einen *[!UICONTROL Invoice]*, einen *[!UICONTROL Shipment]* und einen *[!UICONTROL Returns]* für dieselben Produkte. Autorisieren Sie beide und fahren Sie bis zum Ende des [!UICONTROL Returns] fort.
1. Generieren Sie ein Kunden-Token mithilfe der folgenden GraphQL-Abfrage:

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autorisieren Sie mit dem empfangenen Token und führen Sie die folgende Abfrage durch:

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Abfrage zeigt keinen Fehler an. Der Status der zweiten Rückgabe ist nicht *null*.

<u>Tatsächliche Ergebnisse</u>:

Die Abfrage gibt einen internen Server-Fehler zurück:

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
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
