---
title: 'ACSD-65195: Die Mutation „createCompany“ in GraphQL gibt einen Fehler für ein Land ohne erforderliche Region zurück'
description: Wenden Sie den Patch ACSD-65195 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Mutation „createCompany“ einen Fehler für Länder auslöst, die keine Region benötigen.
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%
---
# ACSD-65195: Die GraphQL-`createCompany`-Mutation gibt einen Fehler für ein Land ohne erforderliche Region zurück

Mit dem Patch der ACSD-65195 wird das Problem behoben, dass die [!UICONTROL GraphQL] `createCompany`-Mutation für Länder, die keine Region benötigen, einen Fehler auslöst. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 installiert ist. Die Patch-ID ist ACSD-65195. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die [!UICONTROL GraphQL] `createCompany`-Mutation gibt einen Fehler zurück, wenn eine Region für ein Land angegeben wird, für das keine Region erforderlich ist.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL B2B Companies]** aktivieren.
1. Senden Sie die `createCompany` [!UICONTROL GraphQL]-Mutation mit einem angegebenen Regionsfeld für ein Land, das keine erfordert. Beispiel: [!UICONTROL country_id]: *AE* und [!UICONTROL region]: *Dubai*.
1. Überprüfen Sie die GraphQL-Antwort.

<u>Erwartete Ergebnisse</u>:

Die Firma sollte erfolgreich erstellt werden, ohne einen Fehler zurückzugeben, wenn eine Region für ein Land angegeben wird, für das keine Region erforderlich ist.

<u>Tatsächliche Ergebnisse</u>:

Das Unternehmen wird nicht erstellt und der folgende Fehler wird zurückgegeben:
`Error: Invalid value of "Dubai" provided for the region field.`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
