---
title: 'ACSD-63329: Datums- und Uhrzeitattribute werden beim Erstellen von Produkten mit der REST-API nicht festgelegt'
description: Wenden Sie den ACSD-63329-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem beim Erstellen von Produkten mit der REST-API keine Standardwerte für die Datums- und Uhrzeitfelder festgelegt sind.
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329: Beim Erstellen von Produkten mit der REST-API werden keine Standardwerte für Datums- und Uhrzeitfelder festgelegt

Mit dem Patch ACSD-63329 wird das Problem behoben, dass beim Erstellen eines neuen Produkts mit der REST-API keine Standardwerte für die Datums- und Uhrzeitfelder festgelegt wurden: `/rest/default/V1/products`. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63329. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Erstellen von Produkten mit der REST-API werden keine Standardwerte für die Felder „Datum“ und „Uhrzeit“ festgelegt: `/rest/default/V1/products`

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein **[!UICONTROL Product]**, legen Sie den Standardwert auf `12/31/2020` fest und legen Sie den **[!UICONTROL Catalog Input Type for Store Owner]** auf ***[!UICONTROL Date]*** oder ***[!UICONTROL Date and Time]*** fest.
1. Erstellen Sie ein weiteres Attribut vom Typ Text und setzen Sie den Standardwert auf ***Testwert***.
1. Erstellen Sie ein neues Produkt mithilfe einer REST-API-POST-Anfrage an `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Überprüfen Sie die für die oben genannten Attribute gespeicherten Werte.

<u>Erwartete Ergebnisse</u>:

Der Standardwert sollte bei der Erstellung eines Produkts mithilfe der API in **[!UICONTROL Date/Datetime]** Typattributen gespeichert werden.

<u>Tatsächliche Ergebnisse</u>:

Der Standardwert wird für das Attribut **[!UICONTROL Text]** gespeichert, nicht jedoch für das Attribut **[!UICONTROL Date type]** . Der Wert für das **[!UICONTROL Date]** ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
