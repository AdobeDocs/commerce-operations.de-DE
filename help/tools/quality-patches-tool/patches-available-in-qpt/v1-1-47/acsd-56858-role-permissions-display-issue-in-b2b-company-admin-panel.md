---
title: 'ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmens-Admin'
description: Wenden Sie den Patch ACSD-56858 an, um das Adobe Commerce-Problem zu beheben, bei dem Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung falsch angezeigt werden.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmens-Admin

Mit dem Patch ACSD-56858 wird das Problem behoben, dass Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung falsch angezeigt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.47 installiert ist. Die Patch-ID ist ACSD-56858. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung werden falsch angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Beginnen Sie mit der Einrichtung einer Firma, indem Sie einen Unternehmensadministrator und Firmenbenutzer hinzufügen.
1. Melden Sie sich als Unternehmensadministrator an der Storefront an und erstellen Sie verschiedene Rollen für verschiedene Benutzer.
1. Weisen Sie diese Rollen nach Bedarf zu, z. B. indem Sie den Zugriff für einige Aufgaben einschränken und gleichzeitig anderen Benutzern vollständigen Zugriff gewähren.
1. Weisen Sie diese Rollen einem anderen Benutzer als dem Unternehmensadministrator mit vollem Zugriff zu.
1. Melden Sie sich bei einem Benutzer an, der kein Unternehmensadministrator ist, z. B. „company_manager“.
1. Navigieren Sie zu **[!UICONTROL Roles and permission]** und bearbeiten Sie die Rolle.
1. Beachten Sie, dass die angezeigten Berechtigungen nicht mit den in der Unternehmensdatenbank für diese Rollen-ID festgelegten Berechtigungen übereinstimmen.

<u>Erwartete Ergebnisse</u>:

Die Rollen und Berechtigungen werden für Benutzende ohne Unternehmensadministrator korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Rollen werden für den Benutzer, der kein Unternehmensadministrator ist, gemäß den Datenbankdatensätzen in der Berechtigungstabelle nicht korrekt angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
