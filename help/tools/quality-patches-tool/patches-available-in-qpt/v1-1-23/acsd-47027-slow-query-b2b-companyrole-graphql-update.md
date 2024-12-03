---
title: 'ACSD-47027: langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Update'
description: Wenden Sie den Patch ACSD-47027 an, um das Adobe Commerce-Problem zu beheben, bei dem eine langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] aktualisiert wird.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Update

Der Patch ACSD-47027 behebt das Problem, dass die langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Update nicht wie erwartet funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47027. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Update funktioniert nicht erwartungsgemäß.

<u>Voraussetzungen</u>:

Installieren Sie das B2B-Modul.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie im Adobe Commerce-Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** und legen Sie **[!UICONTROL Enable Company]** auf _Ja_ fest.
1. Gehen Sie zum Frontend und erstellen Sie ein Unternehmen.
1. Nachdem Sie sich als Unternehmensbenutzer angemeldet haben, gehen Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** und fügen Sie eine neue Rolle hinzu.
1. Aktivieren Sie das [!UICONTROL dev]-Abfrageprotokoll mit `bin/magento dev:que:enab`.
1. Senden Sie nun die unten stehende [!DNL GraphQL] -Anfrage (id ist die [!UICONTROL base64] -kodierte Rollen-ID):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Überprüfen Sie das Abfrageprotokoll.
1. Sie können sehen, dass die obige Abfrage ausgeführt wird. Diese Abfrage wird in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` ausgeführt.

<u>Erwartete Ergebnisse</u>:

Der `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` muss optimiert werden, damit nicht alle in der **[!UICONTROL company_permissions]** DB-Tabelle verfügbaren Daten geladen werden.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce führt eine Abfrage ohne Filter aus. Bei einer großen Anzahl von Datensätzen dauert es sehr lange, bis Adobe Commerce die Datenerfassung vorbereitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
