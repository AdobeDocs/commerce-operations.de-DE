---
title: "ACSD-61528: Rollen mit GraphQL abrufen liefert keine Ergebnisse"
description: Wenden Sie den Patch ACSD-61528 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Abrufen von Rollen vom Unternehmensadministrator mithilfe von GraphQL immer ein Null-Ergebnis zurückgegeben wird.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 4a02bb524fd8d1caae02d909bc9f2e3fc0112042
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528: Rollen mit GraphQL abrufen liefert keine Ergebnisse

Der Patch ACSD-61258 behebt das Problem, dass beim Abrufen von Rollen vom Administrator des Unternehmens, der GraphQL verwendet, immer ein Null-Ergebnis zurückgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61528. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Abrufen von Rollen vom Administrator des Unternehmens mithilfe von GraphQL war das Rollenergebnis immer null.

<u>Voraussetzungen:</u>:

Installieren und aktivieren Sie die Adobe Commerce B2B-Module.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Unternehmen.
1. Melden Sie sich als Unternehmensadministrator bei GraphQL mit der folgenden Mutation an:

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Fügen Sie das resultierende Token den Anforderungsheadern **Autorisierung** als `Bearer`-Token hinzu und führen Sie unterhalb der GraphQL-Abfrage aus:

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage gibt die Rolle zurück.

<u>Tatsächliche Ergebnisse</u>:

Die Rolle für das Unternehmen ist null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.