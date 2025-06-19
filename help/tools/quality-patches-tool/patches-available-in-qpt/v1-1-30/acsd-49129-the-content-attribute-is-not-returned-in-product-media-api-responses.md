---
title: 'ACSD-49129: Attribut „Content“ wird in den Antworten der Medien-API des Produkts nicht zurückgegeben'
description: Wenden Sie den Patch ACSD-49129 an, um das Adobe Commerce-Problem zu beheben, bei dem das Attribut *content* (*base64-Bildcode*) in den Media-API-Antworten des Produkts „rest/V1/products/sku/media“ nicht zurückgegeben wird.
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
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
1. *GET REST API*-Anfrage an `rest/V1/products/<sku>/media` und `rest/V1/products/<sku>/media/<entryId>` senden.
1. Überprüfen Sie die API-Antworten.

<u>Erwartete Ergebnisse</u>

Das *content*-Attribut mit den Daten ist über die REST-API verfügbar.

<u>Tatsächliche Ergebnisse</u>

Das *content*-Attribut ist in den API-Antworten nicht vorhanden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
