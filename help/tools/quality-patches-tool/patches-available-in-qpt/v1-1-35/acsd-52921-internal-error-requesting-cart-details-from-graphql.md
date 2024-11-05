---
title: "ACSD-52921: Fehler beim Anfordern von Details zum Warenkorb von GraphQL für konfigurierbares nicht vorrätiges Produkt"
description: Wenden Sie den Patch ACSD-52921 an, um das Adobe Commerce-Problem zu beheben, bei dem ein interner Fehler auftritt, wenn bei GraphQL Warenkorbdetails für ein konfigurierbares nicht vorrätiges Produkt angefordert werden.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921: Fehler beim Anfordern von Details zum Warenkorb von GraphQL für konfigurierbare nicht vorrätige Produkte

Der Patch ACSD-52921 behebt das Problem, bei dem ein interner Fehler auftritt, wenn bei GraphQL Warenkorbdetails für ein konfigurierbares Nicht-Lager-Produkt angefordert werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52921. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Anfordern von Details zum Warenkorb von GraphQL für ein konfigurierbares nicht vorrätiges Produkt tritt ein interner Fehler auf.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einigen Optionen.
1. Fügen Sie eine Option für das oben konfigurierbare Produkt vom Frontend (Gast-Checkout) zum Warenkorb hinzu.
1. Rufen Sie die `[ masked_id ]` aus der Tabelle `[ quote_id_mask ]` db für das oben erstellte Anführungszeichen ab.
1. Führen Sie die folgende GraphQL-Abfrage aus, um die oben genannten Details zum Gastkarren abzurufen.

   Fügen Sie in der Abfrage die `[ masked_id ]` hinzu, die Sie aus Schritt 3 erhalten haben.

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

1. Dadurch werden die Anführungszeichendetails ohne Probleme zurückgegeben.
1. Wechseln Sie zum Backend und aktualisieren Sie die *[!UICONTROL Stock Status]* des konfigurierbaren Produkts auf *[!UICONTROL Out of Stock]*.
1. Führen Sie dieselbe GraphQL-Abfrage wie in Schritt 4 aus.

<u>Erwartete Ergebnisse</u>:

Die Fehlermeldung wird in der Antwort korrekt gesendet/behandelt.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler *500 Interner Server* wird als Antwort auf die GraphQL-Abfrage ausgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
