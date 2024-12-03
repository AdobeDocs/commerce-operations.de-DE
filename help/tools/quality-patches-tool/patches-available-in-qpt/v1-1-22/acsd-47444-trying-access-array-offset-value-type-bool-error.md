---
title: 'ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4'
description: Wenden Sie den Patch ACSD-47444 an, um das Adobe Commerce-Problem zu beheben, bei dem ein _[!UICONTROL Trying to access array offset on value of type bool]_ -Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4 auftritt.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4

Der Patch ACSD-47444 löst das Problem, dass beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4 der Fehler _[!UICONTROL Trying to access array offset on value of type bool]_angezeigt wird. Dieser Patch ist verfügbar, wenn der [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der folgende Fehler tritt auf: _[!UICONTROL Trying to access array offset on value of type bool]_beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte in PHP 7.4.

<u>Voraussetzungen</u>:

PHP 7.4.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Produkt mit dem Namen &quot;test&quot;.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > legen Sie **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nein_ fest.
1. Gehen Sie zur Storefront und besuchen Sie die URL wie ../abc/test.html (&quot;abc&quot; - sollte nicht vorhanden sein).

<u>Erwartete Ergebnisse</u>:

404 Seite.

<u>Tatsächliche Ergebnisse</u>:

500-Fehler:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
