---
title: 'ACSD-62056: Bild-Upload für konfigurierbares Produkt schlägt fehl, wenn MSI installiert ist'
description: Wenden Sie den Patch ACSD-62056 an, um das Adobe Commerce-Problem zu beheben, bei dem Bilder für konfigurierbare Produkte nicht hinzugefügt werden, wenn MSI installiert ist.
feature: Products, Media
role: Admin, Developer
source-git-commit: 9c186e936492ebcab3903949f40d73745d2a28d3
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: Bild-Upload für konfigurierbares Produkt schlägt fehl, wenn MSI installiert ist

Der Patch ACSD-62056 behebt das Problem, dass Bilder für konfigurierbare Produkte nicht hinzugefügt werden, wenn MSI installiert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-62056. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Bearbeiten eines konfigurierbaren Produkts mit aktiviertem [!UICONTROL Inventory Management/MSI] funktionieren die Optionen zum Hinzufügen von Bildern nicht. Dies wirkt sich sowohl auf die Optionen [!UICONTROL Apply a single set of images to all SKUs] als auch [!UICONTROL Apply unique images by attribute to each SKU] aus.

<u>Voraussetzungen</u>:

[!UICONTROL Inventory Management/MSI] -Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

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

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
