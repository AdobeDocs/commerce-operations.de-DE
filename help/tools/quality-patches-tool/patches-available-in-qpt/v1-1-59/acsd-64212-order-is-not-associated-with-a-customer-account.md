---
title: 'ACSD-64212: Bestellung, die nicht mit einem Kundenkonto verknüpft ist, das nach  [!DNL GraphQL]  Bestellung über erstellt wurde'
description: Adobe Commerce Wenden Sie den Patch ACSD-64212 an, um das Problem zu beheben, dass eine Bestellung nicht mit einem Kundenkonto verknüpft wird, das nach der Bestellung  [!DNL GraphQL]  erstellt wurde.
feature: GraphQL, Checkout, Customers
role: Admin, Developer
source-git-commit: d1d5214293f3bb38b787f80172aabf9cd0bf808b
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-64212: Bestellung, die nicht mit einem Kundenkonto verknüpft ist, das nach der Bestellung über [!DNL GraphQL] erstellt wurde

Mit dem Patch ACSD-64212 wird das Problem behoben, dass eine Bestellung nicht mit einem Kundenkonto verknüpft wird, das nach der Bestellung über [!DNL GraphQL] erstellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-64212. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestellung ist nicht mit einem Kundenkonto verknüpft, wenn das Konto nach der Bestellung über [!DNL GraphQL] erstellt wird.

<u>Schritte zur Reproduktion</u>:

1. Platzieren Sie eine Gastbestellung im Frontend.
1. Senden Sie die folgende Anfrage, um das Konto zu erstellen:

```
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u>Erwartete Ergebnisse</u>:

Die Gastbestellung wird mit dem Kunden verknüpft, nachdem das Kundenkonto erstellt wurde.

<u>Tatsächliche Ergebnisse</u>:

Kundenkonto wurde erstellt, aber die Gastbestellung ist nicht mit dem Kunden verknüpft.


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
