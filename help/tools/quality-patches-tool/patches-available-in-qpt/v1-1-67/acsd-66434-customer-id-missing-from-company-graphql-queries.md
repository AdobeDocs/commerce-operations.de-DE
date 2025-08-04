---
title: 'ACSD-66434: [!UICONTROL Customer ID] fehlt in  [!DNL GraphQL] '
description: Wenden Sie den ACSD-66434-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem [!UICONTROL Customer ID] in den  [!DNL GraphQL]  fehlt.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 422e5a9eb9948032cccaac98415cf4b92895d5a9
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# ACSD-66434: [!UICONTROL Customer ID] fehlt in [!DNL GraphQL]

Mit dem Patch ACSD-66434 wird das Problem behoben, dass in **[!UICONTROL Customer ID]**-Abfragen des Unternehmens [!DNL GraphQL] fehlt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66434. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die [!DNL GraphQL] Unternehmensabfrage gibt `null` für die **[!UICONTROL Customer ID]** in der Unternehmensstruktur zurück.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce 2.4-develop mit B2B- und Inventar-Modulen.
1. Aktivieren Sie in Commerce Admin die B2B-Funktionen und erstellen Sie eine Testfirma.
1. Generieren Sie ein Bearer-Token für den Unternehmensadministrator mithilfe der folgenden [!DNL GraphQL]-Mutation:

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Verwenden Sie das generierte Token, um die Unternehmensstruktur des Kunden mit der folgenden [!DNL GraphQL] Abfrage abzurufen:

```
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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
