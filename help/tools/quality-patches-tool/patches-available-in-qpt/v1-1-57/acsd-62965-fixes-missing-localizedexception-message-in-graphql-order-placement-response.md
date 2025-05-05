---
title: 'ACSD-62965: Behebt das Fehlen der LocalizedException-Nachricht in der GraphQL-Antwort zur Bestellplatzierung'
description: Wenden Sie den Patch „ACSD-62965“ an, um die Adobe Commerce-Probleme zu beheben, bei denen die Nachricht „LocalizedException“ während der Auftragserteilung nicht in der GraphQL-Antwort enthalten war.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965: Behebt `LocalizedException` fehlende Nachricht in der GraphQL-Antwort zur Bestellplatzierung

Mit dem Patch ACSD-62965 wird das Problem behoben, dass die `LocalizedException` während der Bestellplatzierung nicht in der GraphQL-Antwort enthalten war. Dieser Patch ist ab dem [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 verfügbar. Die Patch-ID ist ACSD-62965. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Antwort für die Bestellplatzierung enthält keine `LocalizedException`, was zu unzureichenden Fehlerdetails für das Debugging führt.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue **[!DNL Adobe Commerce]**.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Schritt Bestellplatzierung fort.
1. Fügen Sie in `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php` eine `LocalizedException` zu `Magento\Framework\Exception\LocalizedException` hinzu.
1. Fügen Sie die Ausnahme nach der folgenden Zeile ein:

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Fügen Sie die Ausnahme hinzu:

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Ausführen der GraphQL-Anforderung „Bestellung aufgeben“:

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Beobachten Sie die Antwort:
   1. Die Antwort enthält nicht die `LocalizedException`.
   1. Beispiel für die falsche Antwort:

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>Erwartete Ergebnisse</u>:

Wenn ein `LocalizedException` auftritt, sollte die Ausnahmemeldung in die GraphQL-Antwort zur Bestellplatzierung aufgenommen werden, um die Fehlerbehandlung zu verbessern.

<u>Tatsächliche Ergebnisse</u>:

Wenn ein `LocalizedException` auftritt, wird die Ausnahmemeldung nicht in die GraphQL-Antwort zur Bestellplatzierung aufgenommen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
