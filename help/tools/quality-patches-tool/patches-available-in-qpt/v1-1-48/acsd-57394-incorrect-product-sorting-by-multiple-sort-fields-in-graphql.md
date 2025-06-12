---
title: 'ACSD-57394: Falsche Sortierung nach mehreren Sortierattributen in [!DNL GraphQL]'
description: Wenden Sie den Patch ACSD-57394 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte bei Verwendung mehrerer Sortierattribute in nicht korrekt sortiert werden [!DNL GraphQL].
feature: GraphQL, Products
role: Admin, Developer
exl-id: 3e4ca535-37ed-4363-ba6c-968eb53b98b3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-57394: Falsche Produktsortierung nach mehreren Sortierattributen in [!DNL GraphQL]

Der Patch ACSD-57394 behebt das Problem, dass Produkte bei Verwendung mehrerer Sortierattribute in [!DNL GraphQL] falsch sortiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-57394. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produkte werden bei Verwendung mehrerer Sortierattribute in [!DNL GraphQL] falsch sortiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Produkte mit unterschiedlichen Preisen und Namen.
1. Erstellen Sie eine Kategorie und weisen Sie ihr die erstellten Produkte zu.
1. Senden Sie eine [!DNL GraphQL] Produktabfrage für die erstellte Kategorie mit einigen *sort*-Attributen. Beispiel:

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. Überprüfen Sie die Antwort nach der Erstellung *sort*-Attributen.

<u>Erwartete Ergebnisse</u>:

Die Produkte sollten in der richtigen Reihenfolge zurückgeschickt werden. Das Sortieren der Produkte nach mehreren Attributen sollte funktionieren.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht in der richtigen Reihenfolge zurückgegeben. Das Sortieren der Produkte nach mehreren Attributen funktioniert nicht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
