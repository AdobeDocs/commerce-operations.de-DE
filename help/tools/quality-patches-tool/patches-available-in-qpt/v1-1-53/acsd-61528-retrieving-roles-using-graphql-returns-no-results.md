---
title: 'ACSD-61528: Beim Abrufen von Rollen mit GraphQL werden keine Ergebnisse zurückgegeben'
description: Wenden Sie den ACSD-61528 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Abrufen von Rollen vom Unternehmensadministrator mithilfe von GraphQL immer ein Nullergebnis zurückgibt.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
source-git-commit: e6ba48b10918437df8846992d435d65db0669eda
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528: Beim Abrufen von Rollen mit GraphQL werden keine Ergebnisse zurückgegeben

Mit dem Patch ACSD-61258 wird das Problem behoben, dass beim Abrufen von Rollen vom Unternehmensadministrator mithilfe von GraphQL immer ein Nullergebnis zurückgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61528. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Abrufen von Rollen vom Administrator des Unternehmens mithilfe von GraphQL war das Rollenergebnis immer null.

<u>Voraussetzungen:</u>:

Installieren und Aktivieren von Adobe Commerce B2B-Modulen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Firma.
1. Melden Sie sich mit der folgenden Mutation als Unternehmensadministrator in GraphQL an:

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Fügen Sie das resultierende Token zu **Autorisierungs**-Anfragekopfzeilen als `Bearer`-Token hinzu und führen Sie es unterhalb der GraphQL-Abfrage aus:

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

Die Rolle für die Firma ist null.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
