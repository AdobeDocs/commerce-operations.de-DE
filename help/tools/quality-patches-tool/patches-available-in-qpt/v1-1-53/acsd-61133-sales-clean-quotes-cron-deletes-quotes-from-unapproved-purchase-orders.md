---
title: 'ACSD-61133: `sales_clean_quotes` cron löscht Angebote aus nicht genehmigten Bestellungen'
description: Wenden Sie den Patch ACSD-61133 an, um das Adobe Commerce-Problem zu beheben, bei dem „sales_clean_quotes“ cron Angebote aus nicht genehmigten Bestellungen löscht.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-61133: `sales_clean_quotes` cron löscht Angebote aus nicht genehmigten Bestellungen

Der Patch ACSD-61133 behebt das Problem, dass der `sales_clean_quotes` Cron Angebote aus nicht genehmigten Bestellungen löscht. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist. Die Patch-ID ist ACSD-61133. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 und 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`sales_clean_quotes` Cron löscht Angebote aus nicht genehmigten Bestellungen. Die *[B2B-Bestellung]* kann nicht in die Bestellung des mit der gekauften Bestellung verknüpften Angebots konvertiert werden, da die Cron sie löscht.

<u>Voraussetzungen</u>:

Adobe Commerce [!UICONTROL B2B]-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. *[!UICONTROL B2B Purchase Order]* aktivieren.
1. Erstellen Sie eine Firma.
1. Erstellen Sie eine *[!UICONTROL Purchase Order]*.
1. Warten Sie, bis das Angebot abläuft und vom Cron gelöscht wird. Der Ablaufzeitraum für Angebote kann über **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]** festgelegt werden.
1. Konvertieren Sie *[!UICONTROL Purchase Order]* über *[!UICONTROL My Purchase Order in Customer Dashboard]* oder mit [!DNL GraphQL] `placeOrderForPurchaseOrder`-Mutation in die Reihenfolge.

<u>Erwartete Ergebnisse</u>:

Das mit dem aktiven *[!UICONTROL Purchase Order]* verknüpfte Zitat wird vom Cron nicht gelöscht, da es abgelaufen ist. Die Bestellung wurde erfolgreich entweder in der Storefront oder über [!DNL GraphQL] aufgegeben.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht aufgegeben und ein Fehler wird in der Storefront angezeigt oder in der [!DNL GraphQL] Antwort zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
