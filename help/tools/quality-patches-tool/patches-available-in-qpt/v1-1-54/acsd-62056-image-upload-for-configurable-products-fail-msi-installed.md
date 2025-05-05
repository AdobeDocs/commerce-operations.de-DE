---
title: 'ACSD-62056: Image-Upload für konfigurierbares Produkt schlägt fehl, wenn MSI installiert ist'
description: Wenden Sie den Patch ACSD-62056 an, um das Adobe Commerce-Problem zu beheben, dass Bilder für konfigurierbare Produkte nicht hinzugefügt werden, wenn MSI installiert ist.
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
source-git-commit: 14991f4c813b2ce76729472adb07fe9311615489
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: Image-Upload für konfigurierbares Produkt schlägt fehl, wenn MSI installiert ist

Mit dem Patch ACSD-62056 wird das Problem behoben, dass Bilder für konfigurierbare Produkte nicht hinzugefügt werden, wenn MSI installiert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-62056. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Bearbeiten eines konfigurierbaren Produkts mit aktiviertem [!UICONTROL Inventory Management/MSI] funktionieren die Optionen zum Hinzufügen von Bildern nicht. Dies wirkt sich sowohl auf die [!UICONTROL Apply a single set of images to all SKUs]- als auch auf die [!UICONTROL Apply unique images by attribute to each SKU] aus.

<u>Voraussetzungen</u>:

[!UICONTROL Inventory Management/MSI] Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager und weisen Sie die neue Quelle zu.
1. Bearbeiten Sie ein konfigurierbares Produkt.
1. Klicken Sie auf **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Wählen Sie eine der folgenden Optionen aus und fügen Sie ein Bild hinzu.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Erwartete Ergebnisse</u>:

Die Bilder werden hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Die Bilder werden nicht hinzugefügt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
