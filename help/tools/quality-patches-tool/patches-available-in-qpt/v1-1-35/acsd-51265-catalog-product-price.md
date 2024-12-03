---
title: 'ACSD-51265: Optimieren der Neuindizierung für gebündelte Produkte'
description: Wenden Sie den Patch ACSD-51265 an, um das Adobe Commerce-Problem zu beheben, bei dem die Neuindizierungsleistung von "catalog_product_price"gering ist, wenn im System zu viele gebündelte Produkte vorhanden sind.
feature: Products, Price Indexer
role: Admin
exl-id: 1a173ca7-f99e-42d8-87d7-81a6b33f2d4d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-51265: Optimieren der Neuindizierung für gebündelte Produkte

Der Patch ACSD-51265 behebt das Problem, bei dem die Neuindizierungsleistung von `catalog_product_price` gering ist, wenn zu viele gebündelte Produkte im System vorhanden sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51265. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierungsleistung des Katalogproduktpreises ist gering, wenn im System zu viele gebündelte Produkte vorhanden sind.

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie einen Katalog mit mindestens *10.000* gebündelten Produkten mit dynamischen Preisoptionen.
1. Führen Sie eine Neuindizierung des Produktpreises durch.

<u>Erwartete Ergebnisse</u>

Die Neuindizierung des Produktpreises dauert weniger als 15 Minuten.

<u>Tatsächliche Ergebnisse</u>

Die Neuindizierung des Produktpreises dauert mehr als eine Stunde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
