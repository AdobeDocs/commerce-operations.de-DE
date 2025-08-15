---
title: 'ACSD-62951: Behebt fehlende Elemente und Summen in [!UICONTROL Credit Memo] über REST-API gesendeten E-Mails'
description: Wenden Sie den Patch ACSD-62951 an, um das Adobe Commerce-Problem zu beheben, bei dem die E-[!UICONTROL Credit Memo]-Mail gesendet wird, ohne die Bestellelemente und Gesamtwerte einzubeziehen.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951: Behebt fehlende Elemente und Summen in *[!UICONTROL Credit Memo]* über REST-API gesendeten E-Mails

Mit dem Patch ACSD-62951 wird das Problem behoben, dass die E[!UICONTROL Credit Memo]Mail gesendet wird, ohne die Bestellelemente und Gesamtwerte einzubeziehen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62951. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p10

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die *[!UICONTROL Credit Memo]*-E-Mail, die gesendet wird, wenn eine Gutschrift über die REST-API erstellt wird, enthält `POST V1/order/:orderId/refund` Bestellelemente und Gesamtwerte.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit einem beliebigen Produkt.
1. Versand und Rechnung der Bestellung. Stellen Sie sicher, dass die Rechnung per E-Mail gesendet wird und die Produktdetails enthält.
1. Erstellen eines Admin-Tokens mithilfe des API-Clients.
1. Verwenden Sie das Token, um über die REST-API eine Gutschrift zu erstellen.
   1. Endpunkt: `POST V1/order/:orderId/refund`
   1. Anfrage-Payload:

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>Erwartete Ergebnisse</u>:

Die *[!UICONTROL Credit Memo]*-E-Mail sollte die erstatteten Artikel und Gesamtwerte enthalten

<u>Tatsächliche Ergebnisse</u>:

Die *[!UICONTROL Credit Memo]* E-Mail enthält keine Elemente oder Gesamtwerte, was zu unvollständigen Informationen führt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
