---
title: 'ACSD-51305: Nicht vorrätige zusammengesetzte untergeordnete Produkte sind in der GraphQL-Antwort nicht verfügbar'
description: Wenden Sie den ACSD-51305-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem nicht vorrätige zusammengesetzte untergeordnete Produkte in der GraphQL-Antwort nicht verfügbar sind.
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51305: Nicht vorrätige zusammengesetzte untergeordnete Produkte sind in der GraphQL-Antwort nicht verfügbar

Mit dem Patch ACSD-51305 wird das Problem behoben, dass nicht mehr vorrätige zusammengesetzte untergeordnete Produkte in der GraphQL-Antwort nicht verfügbar sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51305. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nicht vorrätige zusammengesetzte untergeordnete Produkte sind in der GraphQL-Antwort nicht verfügbar.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei der Admin-Website an.
1. Erstellen Sie eine Kategorie (CAT1, ID=3).
1. Erstellen Sie ein *simple1*-Produkt (nicht vorrätig, nicht einzeln sichtbar, zugewiesen zu *cat1*).
1. Erstellen Sie ein *simple2*-Produkt (auf Lager, nicht einzeln sichtbar, zugewiesen zu *cat1*).
1. Erstellen Sie ein *Bundle1*-Produkt mit *simple1*- und *simple2*-untergeordneten Produkten als Optionsfeld *option1*-Produkte und weisen Sie es der Kategorie *cat1* zu.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Setzen Sie **[!UICONTROL Display Out of Stock Products]** auf *Ja*.

1. Öffnen Sie das Produkt *Bundle1* in der Storefront und stellen Sie sicher, dass darin sowohl *simple1* als auch *simple2* untergeordneten Produkte angezeigt werden.
1. Führen Sie die folgende GraphQL-Abfrage aus:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Der **[!UICONTROL Product]** Abschnitt innerhalb des **[!UICONTROL Options]** ist nicht leer.

<u>Tatsächliche Ergebnisse</u>:

Der **[!UICONTROL Product]** Abschnitt innerhalb des **[!UICONTROL Options]** ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
