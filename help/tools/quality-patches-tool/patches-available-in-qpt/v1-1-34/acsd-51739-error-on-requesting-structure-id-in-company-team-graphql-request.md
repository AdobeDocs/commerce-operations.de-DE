---
title: 'ACSD-51739: Fehler bei der Anfrage von „structure_id“ in der GraphQL-Anfrage von „CompanyTeam“'
description: Wenden Sie den Patch „ACSD-51739“ an, um das Adobe Commerce-Problem zu beheben, bei dem ein Fehler zurückgegeben wird, wenn die „structure_id“ in einer GraphQL-Anfrage „CompanyTeam“ angefordert wird.
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: Fehler beim Anfordern von `structure_id` in `CompanyTeam` GraphQL-Anfrage

Mit dem Patch „ACSD-51739“ wird das Problem behoben, dass ein Fehler zurückgegeben wird, wenn der `structure_id` in einer `CompanyTeam` GraphQL-Anfrage angefordert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-51739. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die `structure_id` in einer `CompanyTeam` GraphQL-Anfrage angefordert wird, wird ein Fehler zurückgegeben.

<u>Schritte zur Reproduktion</u>

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** und setzen Sie *[!UICONTROL Enable Company]* auf *Ja*.
1. Erstellen Sie eine Firma zusammen mit einem Benutzer mit Firmenadministrator.
1. Erstellen Sie einen neuen Kunden (*customer1*) und weisen Sie diesem Kunden die Firma (oben erstellt) zu.
1. Melden Sie sich im Frontend als Admin-Benutzer des Unternehmens an.
1. Erstellen Sie ein Unternehmens-Team und weisen Sie *customer1* dem Team per Drag-and-Drop zu.
1. Führen Sie die folgende Unternehmens-GraphQL-Abfrage aus, die `CompanyTeam` mit `structure_id` enthält:

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

Es werden keine Fehler zurückgegeben, und alle angeforderten Daten sind in der GraphQL-Antwort vorhanden.

<u>Tatsächliche Ergebnisse</u>:

* Die Antwort enthält *Interner Server-Fehler*.
* `var/log/exception.log` enthält:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
