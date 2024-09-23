---
title: "ACSD-49970: Falsche Handhabung von GraphQL-Fehlern"
description: Wenden Sie den Patch ACSD-49970 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL-Fehler falsch verarbeitet werden, wenn [!UICONTROL New Relic Reporting] aktiviert ist.
feature: GraphQL, Observability
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: Falsche Handhabung von GraphQL-Fehlern

Der Patch ACSD-49970 behebt das Problem, bei dem GraphQL-Fehler falsch verarbeitet werden, wenn *[!UICONTROL New Relic Reporting]* aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49970. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Schlüssel `GraphQLOperationNames` wird nicht ordnungsgemäß verarbeitet, unabhängig davon, ob der Schlüssel `logDataHelper` diesen Schlüssel enthält oder nicht.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie `bin/magento deploy:mode:set developer` aus.
1. Melden Sie sich beim Administrator an.
1. **[!UICONTROL New Relic Integration]** von **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]** aktivieren
(Hinweis: Selbst wenn ein Fehler angezeigt wird, der besagt, dass die Erweiterung [!DNL New Relic] nicht verfügbar ist, wird die Konfiguration gespeichert.)
1. Führen Sie diese *GraphQL*-Mutation vom *[!DNL Altair]*-Client oder einem anderen Client oder über cURL zu `http://yourMagentoDomain/graphql` aus.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Hinweis: Setzen Sie die **[!UICONTROL Header]** auf [!UICONTROL Content-Currency:CA] , bevor Sie sie ausführen).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Erwartete Ergebnisse</u>:

Es gibt keine *500 Ausnahme* in Protokollen, `GraphQLOperationNames` Schlüssel wird korrekt verarbeitet.

<u>Tatsächliche Ergebnisse</u>:

Es gibt eine *500 Ausnahme* in den Protokollen, die `GraphQLOperationNames` -Taste wird nicht ordnungsgemäß verarbeitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
