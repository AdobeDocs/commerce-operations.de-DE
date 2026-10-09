---
title: 'ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_-Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4'
description: Wenden Sie den Patch ACSD-47444 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4 der Fehler _[!UICONTROL Trying to access array offset on value of type bool]_ auftritt.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%
---
# ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4

Der Patch ACSD-47444 löst das Problem, dass _[!UICONTROL Trying to access array offset on value of type bool]_Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4 auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.22 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es tritt folgender Fehler auf: _[!UICONTROL Trying to access array offset on value of type bool]_beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte, unter PHP 7.4.

<u>Voraussetzungen</u>:

PHP 7.4.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues Produkt - mit dem Namen „test“.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nein_.
1. Wechseln Sie zur Storefront und besuchen Sie die URL wie ../abc/test.html („abc“ - sollte nicht vorhanden sein).

<u>Erwartete Ergebnisse</u>:

404 Seite.

<u>Tatsächliche Ergebnisse</u>:

500-Fehler:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
