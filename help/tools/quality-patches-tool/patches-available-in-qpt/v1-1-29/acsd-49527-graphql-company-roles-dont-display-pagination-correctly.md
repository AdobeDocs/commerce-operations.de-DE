---
title: "ACSD-49527: GraphQL-Unternehmensrollen zeigen die Paginierung nicht korrekt an."
description: Wenden Sie den Patch ACSD-49527 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Unternehmensrollen die Paginierung nicht korrekt anzeigen.
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-49527: GraphQL-Unternehmensrollen zeigen die Paginierung nicht korrekt an

Der Patch ACSD-49527 behebt das Problem, dass die GraphQL-Unternehmensrollen die Paginierung nicht korrekt anzeigen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49527. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

GraphQL-Unternehmensrollen zeigen die Paginierung nicht richtig an.

<u>Zu reproduzierende Schritte</u>:

1. B2B-Unternehmen aktivieren.
1. Erstellen Sie auf der Storefront ein neues Unternehmen.
1. Erstellen Sie mindestens zwei neue Rollen für dieses Unternehmen, sodass es insgesamt drei Rollen gibt, da eine Rolle die Standardrolle ist.
1. Senden Sie eine GraphQL-Anfrage, um Rollen mit der Angabe [!UICONTROL pageSize]: 2 zu erhalten.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. Überprüfen Sie die GraphQL-Antwort.

<u>Erwartete Ergebnisse</u>:

`total_count: 3` und `total_pages: 2` werden in der GraphQL-Antwort zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

`total_count: 2` und `total_pages: 1` werden in der GraphQL-Antwort zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
