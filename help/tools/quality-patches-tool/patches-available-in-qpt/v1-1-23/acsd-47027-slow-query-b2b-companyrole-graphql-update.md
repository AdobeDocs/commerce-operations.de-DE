---
title: 'ACSD-47027: Langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Aktualisierung'
description: Wenden Sie den ACSD-47027-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem eine langsame B2B-Aktualisierung [!UICONTROL CompanyRole] [!DNL GraphQL]  Abfrage vorliegt.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: Langsame B2B-[!UICONTROL CompanyRole]-[!DNL GraphQL]-Aktualisierung der Abfrage

Mit dem Patch ACSD-47027 wird das Problem behoben, dass die Aktualisierung der langsamen Abfrage B2B-[!UICONTROL CompanyRole] [!DNL GraphQL] nicht wie erwartet funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47027. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Aktualisierung der langsamen B2B-[!UICONTROL CompanyRole]-[!DNL GraphQL] funktioniert nicht wie erwartet.

<u>Voraussetzungen</u>:

Installieren Sie das B2B-Modul.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie in Adobe Commerce Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** und setzen Sie **[!UICONTROL Enable Company]** auf _Ja_.
1. Wechseln Sie zum Frontend und erstellen Sie eine Firma.
1. Nachdem Sie sich als Unternehmensbenutzer angemeldet haben, gehen Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** und fügen Sie eine neue Rolle hinzu.
1. Aktivieren Sie [!UICONTROL dev] Abfrageprotokoll mithilfe von `bin/magento dev:que:enab`.
1. Senden Sie nun die folgende [!DNL GraphQL]-Anfrage (ID ist die [!UICONTROL base64] Rollen-ID):

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Überprüfen Sie das Abfrageprotokoll.
1. Sie können sehen, dass die obige Abfrage ausgeführt wird. Diese Abfrage wird in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` ausgeführt.

<u>Erwartete Ergebnisse</u>:

Die `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` muss optimiert werden, um zu vermeiden, dass alle in der **[!UICONTROL company_permissions]** DB-Tabelle verfügbaren Daten geladen werden.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce führt eine Abfrage ohne Filter aus. Wenn eine große Anzahl von Datensätzen vorhanden ist, dauert es sehr lange, bis Adobe Commerce die Datenerfassung vorbereitet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
