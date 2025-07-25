---
title: 'ACSD-66041: Postleitzahlen Irland (IE) können wegen fehlender Länder-ID nicht nach Abholorten durchsucht werden'
description: Wenden Sie den Patch ACSD-66041 an, um das Adobe Commerce-Problem zu beheben, bei dem Postleitzahlen in Irland (IE) aufgrund einer fehlenden Länder-ID nicht nach Abholorten durchsucht werden konnten.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1f69d00e0ad0caf15643d0c218e1a2c264d3ad4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# ACSD-66041: Postleitzahlen Irland (IE) können wegen fehlender `CountryID` nicht nach Abholorten durchsucht werden

Mit dem Patch ACSD-66041 wird das Problem behoben, dass Postleitzahlen in Irland (IE) aufgrund eines fehlenden `CountryID` nicht nach Abholorten durchsucht werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-66041. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Irland (IE) Postleitzahlen können aufgrund eines fehlenden `CountryID` nicht nach Abholorten durchsucht werden.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie die folgende GraphQL-Abfrage aus:

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. Verwenden Sie die folgenden Variablen:

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>Erwartete Ergebnisse</u>:

Postleitzahlen für Irland sind verfügbar, um Abholstandorte zu suchen.

<u>Tatsächliche Ergebnisse</u>:

* Ein *Interner Server-Fehler* wird zurückgegeben.
* `var/log/exception.log` enthält den folgenden Fehler:

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
