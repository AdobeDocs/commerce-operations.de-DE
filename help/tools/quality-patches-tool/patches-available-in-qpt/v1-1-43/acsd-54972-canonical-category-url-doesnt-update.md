---
title: 'ACSD-54972: Kanonische Kategorie-URL wird nicht aktualisiert'
description: Wenden Sie den Patch ACSD-54972 an, um das Adobe Commerce-Problem zu beheben, bei dem die kanonische Kategorie-URL nach dem Ändern der Kategorie-URL nicht aktualisiert wird.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: c4b17c08-9a2b-44a2-925e-f4c5cce7b760
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '366'
ht-degree: 0%
---
# ACSD-54972: Kanonische Kategorie-URL wird nach Änderung der Kategorie-URL nicht aktualisiert

Der Patch ACSD-54972 behebt das Problem, dass die kanonische Kategorie-URL nach einer Änderung der Kategorie-URL nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54972. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die kanonische Kategorie-URL wird nach dem Ändern der Kategorie-URL nicht aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *JA*

2. Erstellen Sie eine Kategorie (z. B. *Name*: *Category 01*, *URL Key*: *category-01*).
3. Aktualisieren Sie den *URL-Schlüssel* auf einen anderen Wert als den ursprünglichen, während Sie das **[!UICONTROL Create Permanent Redirect for old URL]** Kontrollkästchen aktiviert lassen.
4. Reinigen Sie den Cache.
5. Gehen Sie zum *[!UICONTROL Category Page]* im Frontend.
6. Überprüfen Sie die Seitenquelle und suchen Sie nach dem Tag *canonical*.

<u>Erwartete Ergebnisse</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Tatsächliche Ergebnisse</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
