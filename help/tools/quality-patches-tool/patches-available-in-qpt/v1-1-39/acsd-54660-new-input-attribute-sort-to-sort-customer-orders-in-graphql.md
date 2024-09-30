---
title: 'ACSD-54660: Neue Sortierung des Eingabeattributs zur Sortierung von Kundenbestellungen in [!DNL GraphQL]'
description: Wenden Sie den Patch ACSD-54660 an, um das Adobe Commerce-Problem zu beheben, bei dem das neue Eingabedatum `sort` hinzugefügt wurde, um Kundenaufträge in [!DNL GraphQL] nach `sort_field` und `sort_direction` zu sortieren.
feature: GraphQL, Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# ACSD-54660: Neue Eingabe-Attributsortierung hinzugefügt, um Kundenaufträge in [!DNL GraphQL] zu sortieren

Der Patch ACSD-54660 behebt das Problem, bei dem ein neues Eingabeattribut `sort` hinzugefügt wurde, um Kundenaufträge in [!DNL GraphQL] nach `sort_field` und `sort_direction` zu sortieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-54660. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das neue Eingabattribut `sort` wurde hinzugefügt, um Kundenaufträge in [!DNL GraphQL] nach `sort_field` und `sort_direction` zu sortieren.

<u>Zu reproduzierende Schritte</u>:

Abfragen von Kundenbestellungen mit [!DNL GraphQL]:

```
  {
    customerOrders {
      items {
        order_number
        id
        created_at
        grand_total
        status
      }
    }
  }
```

<u>Erwartete Ergebnisse</u>:

Dieser Patch fügt `sort` und `sort_direction` Argumente zu `customer.orders` hinzu.

<u>Tatsächliche Ergebnisse</u>:

Es ist nicht möglich, die Bestellungen mit [!DNL GraphQL] zu sortieren.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
