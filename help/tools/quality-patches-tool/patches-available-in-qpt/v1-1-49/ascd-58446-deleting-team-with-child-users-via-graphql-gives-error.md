---
title: 'ACSD-58446: Beim Löschen eines Teams mit untergeordneten Benutzenden oder Teams über GraphQL wird eine informative Fehlermeldung angezeigt'
description: Wenden Sie den Patch ACSD-58446 an, um das Adobe Commerce-Problem zu beheben, bei dem das Löschen eines Teams mit untergeordneten Benutzenden oder Teams über GraphQL eine informative Fehlermeldung zurückgibt, die nicht mit der Benutzeroberfläche übereinstimmt.
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-58446: Beim Löschen eines Teams mit untergeordneten Benutzenden oder Teams über GraphQL wird eine informative Fehlermeldung angezeigt

Der Patch ACSD-58446 behebt das Adobe Commerce-Problem, dass beim Löschen eines Teams mit untergeordneten Benutzenden oder Teams über GraphQL eine nicht informative Fehlermeldung zurückgegeben wird, die nicht mit der Benutzeroberfläche übereinstimmt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58446. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce B2B 1.5.1 behoben wird

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Löschen eines Teams mit untergeordneten Benutzenden oder Teams über GraphQL wird eine informative Fehlermeldung zurückgegeben, die nicht mit der Benutzeroberfläche übereinstimmt.

## Voraussetzungen:

Adobe Commerce B2B-Module installiert.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die *[!UICONTROL Company]*.
1. Erstellen Sie ein neues Unternehmenskonto.
1. Melden Sie sich bei der **[!UICONTROL Admin]** an und aktivieren Sie das Unternehmenskonto.
1. Überprüfen Sie die E-Mail und legen Sie ein Kennwort für das neue Unternehmenskonto fest.
1. Erstellen Sie ein neues Team für die Firma.
1. Melden Sie sich als Unternehmensbenutzer an der Storefront an und fügen Sie einen neuen Benutzer für das erstellte Team hinzu.
1. Melden Sie sich bei der **[!UICONTROL Admin]** an, deaktivieren Sie den Firmenbenutzer und legen Sie *[!UICONTROL Customer Active]* = *Nein* fest
1. Stellen Sie sicher, dass Sie das erstellte Team über GraphQL löschen.

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

Eine informative Fehlermeldung, die mit der Benutzeroberfläche konsistent ist, wird zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine generische interne Server-Fehlermeldung zurückgegeben, die nicht mit der Benutzeroberfläche übereinstimmt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
