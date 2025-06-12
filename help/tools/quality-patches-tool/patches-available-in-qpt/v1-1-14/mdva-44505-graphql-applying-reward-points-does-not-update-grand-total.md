---
title: 'MDVA-44505: Die GraphQL-Abfrage für die Anwendung von Prämienpunkten beim Warenkorb aktualisiert nicht die Gesamtsumme'
description: Der MDVA-44505 Patch löst das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der Belohnungspunkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505: Die GraphQL-Abfrage für die Anwendung von Prämienpunkten beim Warenkorb aktualisiert nicht die Gesamtsumme

Der MDVA-44505 Patch löst das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der Belohnungspunkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage für einen Warenkorb, in dem Belohnungspunkte angewendet werden, berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

<u>Schritte zur Reproduktion</u>:

1. Prämienpunkte konfigurieren.
1. Erstellen Sie einen Warenkorb und wenden Sie einige Prämienpunkte an.
1. Rufen Sie die `GetCart` Abfrage vom `GraphQL`-Endpunkt auf und rufen Sie Ihren Warenkorb ab:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Überprüfen Sie den Gesamteintrag.
1. Überprüfen Sie nun mit der REST-API (`/rest/V1/carts/mine/totals`) die Gesamtsumme des Warenkorbs des Kunden.

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage für den Warenkorb gibt die richtige Gesamtsumme zurück, die die Belohnungspunkte berücksichtigt.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
