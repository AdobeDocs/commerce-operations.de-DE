---
title: 'ACSD-49129: Attribut „Content“ wird in den Antworten der Medien-API des Produkts nicht zurückgegeben'
description: Wenden Sie den Patch ACSD-49129 an, um das Adobe Commerce-Problem zu beheben, bei dem das Attribut *content* (*base64-Bildcode*) in den Media-API-Antworten des Produkts „rest/V1/products/sku/media“ nicht zurückgegeben wird.
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%
---
# ACSD-49129: Attribut „Content“ wird in den Antworten der Medien-API des Produkts nicht zurückgegeben

Mit dem Patch ACSD-49129 wird das Problem behoben, dass *Attribut* content) (*[!UICONTROL base64 image code]*) in den Antworten der `rest/V1/products/sku/media` Media-API nicht zurückgegeben wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.30 installiert ist. Die Patch-ID ist ACSD-49129. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das *content*-Attribut (*[!UICONTROL base64 image code]*) wird nicht in den Antworten der `rest/V1/products/sku/media` Media-API zurückgegeben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit einem Bild.
1. Senden Sie *GET REST-API*-Anfrage an `rest/V1/products/<sku>/media` und `rest/V1/products/<sku>/media/<entryId>`.
1. Überprüfen Sie die API-Antworten.

<u>Erwartete Ergebnisse</u>

Das *content*-Attribut mit den Daten ist über die REST-API verfügbar.

<u>Tatsächliche Ergebnisse</u>

Das *content*-Attribut ist in den API-Antworten nicht vorhanden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
