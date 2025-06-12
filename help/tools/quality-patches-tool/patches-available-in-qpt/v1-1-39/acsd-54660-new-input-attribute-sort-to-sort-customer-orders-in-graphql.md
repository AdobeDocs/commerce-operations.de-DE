---
title: 'ACSD-54660: Sortierung nach neuem Eingabeattribut, um Kundenaufträge zu sortieren [!DNL GraphQL]'
description: Wenden Sie den Patch ACSD-54660 an, um das Adobe Commerce-Problem zu beheben, bei dem ein neues Eingabeattribut „sort“ hinzugefügt wurde, um Kundenaufträge in " [!DNL GraphQL] _field“ und „sort_direction“ zu sortieren.
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 3962d4b6-634e-4164-adae-fa840ca7d869
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# ACSD-54660: Neues Eingabeattribut „sort“ wurde hinzugefügt, um Kundenaufträge in [!DNL GraphQL] zu sortieren

Mit dem Patch ACSD-54660 wird das Problem behoben, dass ein neues Eingabeattribut hinzugefügt `sort`, um Kundenaufträge in [!DNL GraphQL] nach `sort_field` und `sort_direction` zu sortieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-54660. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Neues Eingabeattribut `sort` hinzugefügt, um Kundenaufträge in [!DNL GraphQL] nach `sort_field` und `sort_direction` zu sortieren.

<u>Schritte zur Reproduktion</u>:

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

Dieser Patch fügt `customer.orders` `sort` und `sort_direction` Argumente hinzu.

<u>Tatsächliche Ergebnisse</u>:

Es ist nicht möglich, die Bestellungen mithilfe von [!DNL GraphQL] zu sortieren.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
