---
title: "MDVA-44505: GraphQL-Abfrage zur Anwendung von Belohnungspunkten im Warenkorb aktualisiert Gesamtsumme nicht"
description: Der Patch MDVA-44505 behebt das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der belohnte Punkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505: GraphQL-Abfrage zur Anwendung von Belohnungspunkten im Warenkorb aktualisiert Gesamtsumme nicht

Der Patch MDVA-44505 behebt das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der belohnte Punkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage für einen Warenkorb, der belohnte Punkte anwendet, berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren von Belohnungspunkten.
1. Erstellen Sie einen Warenkorb und wenden Sie einige Belohnungspunkte an.
1. Rufen Sie die `GetCart` -Abfrage vom `GraphQL` -Endpunkt auf und rufen Sie Ihren Warenkorb ab:

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
1. Überprüfen Sie nun die Gesamtsumme des Warenkorbs des Kunden mithilfe der Rest-API (`/rest/V1/carts/mine/totals`).

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage für den Warenkorb gibt die korrekte Gesamtsumme zurück, die die Belohnungspunkte berücksichtigt.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
