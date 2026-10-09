---
title: 'ACSD-48234: Falsche Anzahl der Kategorieelemente im Katalogsuchergebnis, wenn aktiviert[!UICONTROL Display Out of Stock Products]'
description: Wenden Sie den Patch ACSD-48234 an, um das Adobe Commerce-Problem zu beheben, bei dem das Katalogsuchergebnis eine falsche Anzahl von Kategorieelementen anzeigt, wenn die Option [!UICONTROL Display Out of Stock Products] aktiviert ist.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%
---
# ACSD-48234: Das Ergebnis der Katalogsuche zeigt eine falsche Anzahl von Kategorieelementen **[!UICONTROL Display Out of Stock Products]** aktiviert an

Der Patch ACSD-48234 löst das Problem, dass das Katalogsuchergebnis eine falsche Anzahl von Kategorieelementen anzeigt, wenn die Option **[!UICONTROL Display Out of Stock Products]** aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48234. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Ergebnis der Katalogsuche zeigt eine falsche Anzahl von Kategorieelementen an, wenn die Option **[!UICONTROL Display Out of Stock Products]** aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und öffnen Sie **[!UICONTROL color]** Attribut .
1. Fügen Sie zwei Optionen hinzu, z. B. orange und grün. Speichern Sie das Attribut.
1. Wechseln Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** und fügen Sie dem **[!UICONTROL Default]** Attributsatz das Attribut **[!UICONTROL color]** hinzu.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** und setzen Sie **[!UICONTROL Display Out of Stock Products]** auf _Ja_.
1. Kategorie „cat1“ erstellen.
1. Erstellen Sie zwei Produkte:
   1. Name: prod1, Farbe: orange, Kategorien: cat1.
   1. Name: prod2, Farbe: grün, Kategorien: cat1.
1. Öffnen Sie die Kategorie „cat1“ in der Storefront.
1. Wählen Sie die orangefarbene Farbe in der mehrschichtigen Navigation aus.

<u>Erwartete Ergebnisse</u>:

Es wird nur das Produkt prod1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es werden sowohl prod1- als auch prod2-Produkte angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
