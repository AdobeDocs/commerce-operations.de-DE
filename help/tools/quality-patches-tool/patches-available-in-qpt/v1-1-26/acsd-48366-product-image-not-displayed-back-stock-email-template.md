---
title: 'ACSD-48366: Produktbild wird nicht in [!UICONTROL Back to Stock] E-Mail-Vorlage angezeigt'
description: Wenden Sie den Patch ACSD-48366 an, um das Adobe Commerce-Problem zu beheben, bei dem das Miniaturbild des Produkts nicht in der E-Mail mit der Warnmeldung des Produkts angezeigt wird.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%
---
# ACSD-48366: Produktbild wird nicht in [!UICONTROL Back to Stock] E-Mail-Vorlage angezeigt

Mit dem Patch ACSD-48366 wird das Problem behoben, dass das Miniaturbild des Produkts nicht in der Stock-Benachrichtigungs-E-Mail des Produkts angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48366. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Produktbild wird nicht in der [!UICONTROL Back to Stock] E-Mail-Vorlage angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie *[!UICONTROL Product Alert]* für *[!UICONTROL Back in Stock]*, indem Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]* gehen.
1. Aktivieren Sie *[!UICONTROL Display Out of Stock Products]*, indem Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]* gehen.
1. Einfaches Produkt mit Menge = 0 erstellen.
1. Erstellen Sie eine Kundin oder einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Produktwarnungen zu erhalten, wenn es vorrätig ist.
1. Machen Sie das Produkt auf Lager.
1. Ausführen des Warnhinweiscron für das Produkt.

   ```text
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Starten Sie den Warnhinweis für das Produkt für den Kunden.

   ```shell
   bin/magento queue:consumers:start product_alert
   ```

1. Überprüfen Sie die E-Mail. Die E-Mail mit den Meldebeständen sollte jetzt im E-Mail-Catcher verfügbar sein.

<u>Erwartete Ergebnisse</u>:

Das Produktbild wird in der E-Mail mit der Benachrichtigung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produktbild ist in der E-Mail mit der Stock-Benachrichtigung nicht verfügbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
