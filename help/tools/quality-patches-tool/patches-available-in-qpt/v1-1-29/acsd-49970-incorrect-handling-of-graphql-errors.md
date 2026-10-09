---
title: 'ACSD-49970: Falsche Behandlung von GraphQL-Fehlern'
description: Wenden Sie den Patch ACSD-49970 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL-Fehler falsch verarbeitet werden, wenn [!UICONTROL New Relic Reporting] aktiviert ist.
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%
---
# ACSD-49970: Falsche Behandlung von GraphQL-Fehlern

Mit dem Patch ACSD-49970 wird das Problem behoben, dass GraphQL-Fehler falsch verarbeitet werden, wenn *[!UICONTROL New Relic Reporting]* aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49970. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`GraphQLOperationNames` Schlüssel wird nicht korrekt verarbeitet, unabhängig davon, ob die `logDataHelper` diesen Schlüssel enthält oder nicht.

<u>Schritte zur Reproduktion</u>:

1. `bin/magento deploy:mode:set developer` ausführen.
1. Melden Sie sich beim Administrator an.
1. **[!UICONTROL New Relic Integration]** über **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** aktivieren **[!UICONTROL New Relic Reporting]**
(Hinweis: Auch wenn eine Fehlermeldung angezeigt wird, dass die [!DNL New Relic] nicht verfügbar ist, wird die Konfiguration gespeichert).
1. Führen Sie diese *GraphQL*-Mutation aus, um vom *[!DNL Altair]*-Client, einem anderen Client oder über cURL zu `http://yourMagentoDomain/graphql`.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Hinweis: Stellen Sie den **[!UICONTROL Header]** auf [!UICONTROL Content-Currency:CA] ein, bevor Sie ihn ausführen).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Erwartete Ergebnisse</u>:

Es gibt keine *500* Ausnahme in Protokollen. `GraphQLOperationNames` Schlüssel wird korrekt verarbeitet.

<u>Tatsächliche Ergebnisse</u>:

Es gibt eine *500* Ausnahme in Protokollen. `GraphQLOperationNames` Schlüssel wird nicht korrekt verarbeitet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
