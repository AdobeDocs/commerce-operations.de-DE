---
title: 'ACSD-52921: Fehler beim Anfordern von Warenkorbdetails von GraphQL für nicht vorrätiges konfigurierbares Produkt'
description: Wenden Sie den ACSD-52921-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem beim Anfordern von Warenkorbdetails von GraphQL für ein nicht vorrätiges konfigurierbares Produkt ein interner Fehler auftritt.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921: Fehler beim Anfordern von Warenkorbdetails von GraphQL für nicht vorrätiges konfigurierbares Produkt

Mit dem Patch ACSD-52921 wird das Problem behoben, dass beim Anfordern von Warenkorbdetails von GraphQL für ein nicht vorrätiges konfigurierbares Produkt ein interner Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52921. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein interner Fehler tritt beim Anfordern von Warenkorbdetails von GraphQL für ein nicht vorrätiges konfigurierbares Produkt auf.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einigen Optionen.
1. Fügen Sie eine Option für das oben konfigurierbare Produkt aus dem Frontend zum Warenkorb hinzu (Gast-Checkout).
1. Rufen Sie die `[ masked_id ]` aus der `[ quote_id_mask ]` DB-Tabelle für das oben erstellte Angebot ab.
1. Führen Sie die folgende GraphQL-Abfrage aus, um die obigen Details zum Gästekorb abzurufen.

   Fügen Sie die in Schritt 3 erhaltene `[ masked_id ]` in die Abfrage ein.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Dadurch werden die Angebotsdetails ohne Probleme zurückgegeben.
1. Wechseln Sie zum Backend und aktualisieren Sie die *[!UICONTROL Stock Status]* des konfigurierbaren Produkts auf *[!UICONTROL Out of Stock]*.
1. Führen Sie dieselbe GraphQL-Abfrage aus, wie in Schritt 4.

<u>Erwartete Ergebnisse</u>:

Die Fehlermeldung wird in der Antwort korrekt gesendet/behandelt.

<u>Tatsächliche Ergebnisse</u>:

*500 Internal Server*-Fehler wird als Antwort auf die GraphQL-Abfrage ausgelöst.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
