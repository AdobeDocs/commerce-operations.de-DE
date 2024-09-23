---
title: '"ACSD-51739: Fehler beim Anfordern von "structure_id"in "CompanyTeam"GraphQL-Anfrage"'
description: Wenden Sie den Patch ACSD-51739 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Fehler zurückgegeben wird, wenn in einer GraphQL-Anfrage "UnternehmenTeam"die "structure_id"angefordert wird.
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: Fehler beim Anfordern von `structure_id` in `CompanyTeam` GraphQL-Anfrage

Der Patch ACSD-51739 behebt das Problem, bei dem ein Fehler zurückgegeben wird, wenn in einer GraphQL-Anfrage `CompanyTeam` der Wert `structure_id` angefordert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-51739. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Fehler wird zurückgegeben, wenn in einer `CompanyTeam` GraphQL-Anfrage die `structure_id` angefordert wird.

<u>Zu reproduzierende Schritte</u>

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** und legen Sie *[!UICONTROL Enable Company]* auf *Ja* fest.
1. Erstellen Sie ein Unternehmen zusammen mit einem Unternehmensadministrator.
1. Erstellen Sie einen neuen Kunden (*customer1*) und weisen Sie diesem Kunden das (oben erstellte) Unternehmen zu.
1. Melden Sie sich am Frontend als Unternehmensadministrator an.
1. Erstellen Sie ein Unternehmensteam und weisen Sie dem Team mithilfe von Drag &amp; Drop *customer1* zu.
1. Führen Sie die folgende GraphQl-Abfrage des Unternehmens aus, die `CompanyTeam` mit `structure_id` enthält:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Überprüfen Sie die GraphQL-Antwort.

<u>Erwartete Ergebnisse</u>:

Es werden keine Fehler zurückgegeben und alle angeforderten Daten sind in der GraphQL-Antwort vorhanden.

<u>Tatsächliche Ergebnisse</u>:

* Die Antwort enthält einen *internen Server-Fehler*.
* `var/log/exception.log` enthält:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
