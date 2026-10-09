---
title: 'ACSD-66434: [!UICONTROL Customer ID] fehlt in [!DNL GraphQL]'
description: Wenden Sie den ACSD-66434-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem [!UICONTROL Customer ID] in den [!DNL GraphQL]-Abfragen des Unternehmens fehlt.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
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
source-wordcount: '324'
ht-degree: 0%
---
# ACSD-66434: [!UICONTROL Customer ID] fehlt in [!DNL GraphQL]

Mit dem Patch ACSD-66434 wird das Problem behoben, dass in [!DNL GraphQL]-Abfragen des Unternehmens **[!UICONTROL Customer ID]** fehlt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66434. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die [!DNL GraphQL] Unternehmensabfrage gibt `null` für die **[!UICONTROL Customer ID]** in der Unternehmensstruktur zurück.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce 2.4-develop mit B2B- und Inventar-Modulen.
1. Aktivieren Sie in Commerce Admin die B2B-Funktionen und erstellen Sie eine Testfirma.
1. Generieren Sie ein Bearer-Token für den Unternehmensadministrator mithilfe der folgenden [!DNL GraphQL]-Mutation:

```graphql
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Verwenden Sie das generierte Token, um die Unternehmensstruktur des Kunden mit der folgenden [!DNL GraphQL] Abfrage abzurufen:

```graphql
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>Erwartete Ergebnisse</u>:

**[!UICONTROL Customer ID]** sollte in der Abfrage „Unternehmen [!DNL GraphQL]&quot; zurückgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

**[!UICONTROL Customer ID]** gibt als `null` in der Abfrage „Unternehmen [!DNL GraphQL]&quot; zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
