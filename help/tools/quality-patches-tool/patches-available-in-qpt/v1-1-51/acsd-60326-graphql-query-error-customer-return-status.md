---
title: 'ACSD-60326: GraphQL-Abfrage zum Status [!UICONTROL Returns] des Kunden erzeugt einen Fehler'
description: Wenden Sie den Patch ACSD-60326 an, um das Adobe Commerce-Problem zu beheben, bei dem in der GraphQL-Abfrage für den Kundenstatus [!UICONTROL Returns] ein Fehler auftritt.
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: GraphQL-Abfrage zum Status [!UICONTROL Returns] des Kunden erzeugt einen Fehler

Der Patch ACSD-60326 behebt das Problem, dass in der GraphQL-Abfrage für den Status &quot;customer [!UICONTROL Returns]&quot;ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage zum Status [!UICONTROL Returns] des Kunden gibt einen Fehler zurück.

<u>Zu reproduzierende Schritte</u>:

1. Initialisieren Sie eine neue Instanz mit Beispieldaten.
1. Wechseln Sie auf der *[!UICONTROL Admin]* Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** und setzen Sie **[!UICONTROL Enable RMA on Storefront]** auf *Ja*.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** und füllen Sie die Adresse aus.
1. Ändern Sie das Kennwort für den Kunden `roni_cost@example.com`.
1. Melden Sie sich beim Admin Panel an und geben Sie eine Bestellung für den Kunden `roni_cost@example.com` mit den folgenden Produkten auf:
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Green*
1. Erstellen Sie eine *[!UICONTROL Invoice]* und eine *[!UICONTROL Shipment]* für diese Bestellung.
1. Wählen Sie **[!UICONTROL Create Returns]** aus.
1. Gehen Sie zu **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** und:
   * Wählen Sie *WSH12-32-Red* und *WSH12-32-Purple* aus.
   * Klicken Sie auf **[!UICONTROL Add Selected Products to returns]**:
      * Legen Sie **[!UICONTROL Requested]** = *1* fest
      * Setzen Sie **[!UICONTROL Return Reason]** auf *Nicht mehr verfügbar*
      * Setzen Sie **[!UICONTROL Item Condition]** auf *Geöffnet*
      * Setzen Sie **[!UICONTROL Resolution]** auf *Refund*
   * Klicken Sie auf **[!UICONTROL Submit Returns]**.
1. Öffnen Sie **[!UICONTROL Returns]** und wählen Sie links **[!UICONTROL Return Items]** aus.
   * Legen Sie **[!UICONTROL Authorized]** = *1* für beide Produkte fest
   * Setzen Sie **[!UICONTROL Status]** für *WSH12-32-Purple* auf *Authorized* .
   * Setzen Sie **[!UICONTROL Status]** für *WSH12-32-Red* auf *Denied* .
   * Klicken Sie auf **[!UICONTROL Save]**
1. Erstellen Sie eine neue Bestellung mit denselben Produkten.
1. Erstellen Sie eine *[!UICONTROL Invoice]*, *[!UICONTROL Shipment]* und *[!UICONTROL Returns]* für dieselben Produkte. Autorisieren Sie beide und fahren Sie bis zum Ende des [!UICONTROL Returns] -Prozesses fort.
1. Generieren Sie mithilfe der folgenden GraphQL-Abfrage ein Kunden-Token:

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

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
