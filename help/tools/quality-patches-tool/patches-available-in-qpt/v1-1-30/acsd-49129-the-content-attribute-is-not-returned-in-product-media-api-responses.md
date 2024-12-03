---
title: 'ACSD-49129: Attribut "Inhalt"wird in den API-Antworten der Produktmedien nicht zurückgegeben'
description: Wenden Sie den Patch ACSD-49129 an, um das Adobe Commerce-Problem zu beheben, bei dem das Attribut *content* (*base64-Bildcode*) nicht in den "rest/V1/products/sku/media"-API-Antworten des Produkts zurückgegeben wird.
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49129: Attribut &quot;Inhalt&quot;wird in den API-Antworten der Produktmedien nicht zurückgegeben

Der Patch ACSD-49129 behebt das Problem, dass das Attribut *content* (*[!UICONTROL base64 image code]*) in den API-Antworten der `rest/V1/products/sku/media` Produktmedien nicht zurückgegeben wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.30 installiert ist. Die Patch-ID lautet ACSD-49129. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Attribut *content* (*[!UICONTROL base64 image code]*) wird nicht in den `rest/V1/products/sku/media` -Produkt-Medien-API-Antworten zurückgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit einem Bild.
1. Senden Sie die Anfrage *GET REST API* an `rest/V1/products/<sku>/media` und `rest/V1/products/<sku>/media/<entryId>`.
1. Überprüfen Sie die API-Antworten.

<u>Erwartete Ergebnisse</u>

Das Attribut *content* mit den Daten ist über die REST-API verfügbar.

<u>Tatsächliche Ergebnisse</u>

Das Attribut *content* ist nicht in den API-Antworten vorhanden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
