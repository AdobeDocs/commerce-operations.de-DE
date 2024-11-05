---
title: "ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmensadministratoren"
description: Wenden Sie den Patch ACSD-56858 an, um das Adobe Commerce-Problem zu beheben, bei dem Rollenberechtigungen fälschlicherweise für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung angezeigt werden.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmensadministratoren

Der Patch ACSD-56858 behebt das Problem, dass Rollenberechtigungen fälschlicherweise für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung angezeigt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.47 installiert ist. Die Patch-ID ist ACSD-56858. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung werden ungenau angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Beginnen Sie mit der Einrichtung eines Unternehmens, dem Hinzufügen eines Unternehmens-Administrators und von Benutzern des Unternehmens.
1. Melden Sie sich als Unternehmensadministrator an der Storefront an und erstellen Sie verschiedene Rollen für verschiedene Benutzer.
1. Weisen Sie diese Rollen nach Bedarf zu, z. B. den Zugriff auf einige Aufgaben zu begrenzen und gleichzeitig den uneingeschränkten Zugriff für andere zu.
1. Weisen Sie diese Rollen einem anderen Benutzer als dem Unternehmensadministrator vollen Zugriff zu.
1. Melden Sie sich bei einem Benutzer an, der kein Unternehmens-Admin ist, z. B. bei einem company_manager.
1. Navigieren Sie zu **[!UICONTROL Roles and permission]** und bearbeiten Sie die Rolle.
1. Beachten Sie, dass die angezeigten Berechtigungen nicht mit den in der Datenbank des Unternehmens festgelegten Berechtigungen für diese Rollen-ID übereinstimmen.

<u>Erwartete Ergebnisse</u>:

Die Rollen und Berechtigungen werden für Benutzer ohne Unternehmens-Admin-Berechtigung korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Rollen werden für Benutzer ohne firmeneigene Administratorrechte nicht korrekt angezeigt, wie in den Datenbankdatensätzen in der Berechtigungstabelle angegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
