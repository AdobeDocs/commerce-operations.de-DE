---
title: "ACSD-58446: Das Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL gibt eine informative Fehlermeldung."
description: Wenden Sie den Patch ACSD-58446 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL eine nicht informative Fehlermeldung zurückgegeben wird, die nicht mit der Benutzeroberfläche übereinstimmt.
feature: GraphQL
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-58446: Durch das Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL erhalten Sie eine informative Fehlermeldung.

Der Patch ACSD-58446 behebt das Adobe Commerce-Problem, bei dem beim Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL eine nicht informative Fehlermeldung zurückgegeben wird, die nicht mit der Benutzeroberfläche übereinstimmt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58446. Bitte beachten Sie, dass das Problem in Adobe Commerce B2B 1.5.1 behoben sein soll

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL wird eine nicht informative Fehlermeldung zurückgegeben, die mit der Benutzeroberfläche nicht konsistent ist.

## Voraussetzungen:

Adobe Commerce B2B-Module installiert.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Funktion &quot;*[!UICONTROL Company]*&quot;.
1. Erstellen Sie ein neues Unternehmenskonto.
1. Melden Sie sich bei **[!UICONTROL Admin]** an und aktivieren Sie das Unternehmenskonto.
1. Markieren Sie die E-Mail und legen Sie ein Kennwort für das neue Unternehmenskonto fest.
1. Erstellen Sie ein neues Team für das Unternehmen.
1. Melden Sie sich als Unternehmensbenutzer in der Storefront an und fügen Sie einen neuen Benutzer für das erstellte Team hinzu.
1. Melden Sie sich bei **[!UICONTROL Admin]** an, deaktivieren Sie den Unternehmensbenutzer und legen Sie *[!UICONTROL Customer Active]* = *Nein* fest.
1. Löschen Sie das erstellte Team unbedingt über GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Es wird eine informative Fehlermeldung zurückgegeben, die der Benutzeroberfläche entspricht.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine generische Fehlermeldung für den internen Server zurückgegeben, die nicht mit der Benutzeroberfläche konsistent ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
