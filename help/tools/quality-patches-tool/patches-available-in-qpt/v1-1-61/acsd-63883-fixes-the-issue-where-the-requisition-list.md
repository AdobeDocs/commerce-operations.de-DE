---
title: 'ACSD-63883: Beheben von falschen „items_count“ in [!DNL GraphQL] Antwort für [!UICONTROL Requisition List]'
description: Wenden Sie den Patch „ACSD-63883“ an, um das Problem zu beheben, bei dem der [!UICONTROL Requisition List] in der [!DNL GraphQL]-Antwort einen falschen „items_count“ zurückgibt.
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%
---
# ACSD-63883: Beheben falscher `items_count` in [!DNL GraphQL] Antwort für [!UICONTROL Requisition List]

Mit dem Patch „ACSD-63883“ wird das Problem behoben, dass der **[!UICONTROL Requisition List]** eine falsche `items_count` in der [!DNL GraphQL] Antwort zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-63883. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce B2B 1.5.3 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die **[!UICONTROL Requisition List]** gibt eine falsche `items_count` in der [!DNL GraphQL] Antwort zurück.


<u>Schritte zur Reproduktion</u>:

1. Aktivieren der B2B-**[!UICONTROL Requisition List]**-Funktion.
1. Erstellen Sie einige Produkte.
1. Kundenkonto erstellen.
1. Klicken Sie auf **[!UICONTROL Create new Requisition List]**.
1. Senden Sie die `addProductsToRequisitionList` [!DNL GraphQL] Mutationsanfrage mit einem Produkt, um es der [!UICONTROL Requisition List] hinzuzufügen.

   ```graphql
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Senden Sie die Anfrage auf `addProductsToRequisitionList` [!DNL GraphQL]-Mutation mit drei anderen Produkten, um sie der [!UICONTROL Requisition List] hinzuzufügen.
1. Überprüfen Sie die `items_count` in der Antwort.

**Erwartete Ergebnisse**:

* `items_count`: 4 sollte in der Antwort zurückgegeben werden.

**Tatsächliche Ergebnisse**:

* `items_count`: 2 wird in der Antwort zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
