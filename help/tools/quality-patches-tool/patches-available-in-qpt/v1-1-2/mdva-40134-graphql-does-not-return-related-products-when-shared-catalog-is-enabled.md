---
title: 'MDVA-40134: GraphQL gibt keine verwandten Produkte zurück, wenn der freigegebene Katalog aktiviert ist'
description: Der Patch MDVA-40134 behebt das Problem, dass GraphQL keine verwandten Produkte zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%
---
# MDVA-40134: GraphQL gibt keine verwandten Produkte zurück, wenn der freigegebene Katalog aktiviert ist

Der Patch MDVA-40134 behebt das Problem, dass GraphQL keine verwandten Produkte zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL gibt keine verwandten Produkte zurück, wenn der freigegebene Katalog aktiviert ist.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert werden.
Die Instanz darf nur mit den Beispieldaten sauber sein.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Allgemein** > **B2B-Funktionen** und aktivieren Sie **Unternehmens- und freigegebenen Katalog**.
1. Navigieren Sie **Katalog** > **Freigegebener Katalog** und fügen Sie alle Produkte zum **Allgemeiner Katalog** hinzu.
1. Verwenden Sie die Beispieldaten und modifizieren Sie den Joust Duffle Bag (SKU 24-MB01).
1. Fügen **unter „Verwandte Produkte** die beiden Reisetaschen (ID 7 und 13) hinzu.
1. Senden einer **POST**-Anfrage:

<pre>&lbrace;
  products(filter: {sku: {eq: „24-MB01“}&#x200B;}, sort: {name: ASC}) &lbrace;
    items &lbrace;
      related_products &lbrace;
        UID
        name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Erwartete Ergebnisse</u>:

In der GraphQL-Antwort werden verwandte Produkte angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten die folgende Fehlermeldung:

<pre>Der Rückgabewert von Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() muss vom Typ int sein, null zurückgegeben &lbrace;„Exception“:“[Objekt] (GraphQL\\Error\\Error(Code: 0): Der Rückgabewert von Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() muss vom Typ int sein, null zurückgegeben </pre>

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
