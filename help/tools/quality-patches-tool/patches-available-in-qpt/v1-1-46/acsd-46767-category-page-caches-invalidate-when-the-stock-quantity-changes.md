---
title: 'ACSD-46767: [!UICONTROL Category] Seiten-Caches werden ungültig, wenn sich die Lagermenge ändert'
description: Wenden Sie den Patch ACSD-46767 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Category]-Caches ungültig werden, wenn sich die Lagermenge ändert, auch wenn das Produkt noch auf Lager ist.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 5872dca7-fdef-47ad-8718-bf343cd3a42a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-46767: [!UICONTROL Category] Seiten-Caches werden ungültig, wenn sich die Lagermenge ändert

Mit dem Patch ACSD-46767 wird das Problem behoben, dass die [!UICONTROL Category]-Caches ungültig werden, wenn sich die Lagermenge ändert, auch wenn das Produkt noch auf Lager ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46 installiert ist. Die Patch-ID ist ACSD-46767. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!UICONTROL Category] Seiten-Caches werden ungültig, wenn sich die Lagermenge ändert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Produkte und fügen Sie sie derselben Kategorie hinzu.
1. Öffnen Sie die *[!UICONTROL Category]* Seite in der Storefront, um sicherzustellen, dass die Seite zwischengespeichert wird.
1. Bestellung mit einem der Produkte aus der Kategorie *(Produktmenge wird geändert, aber Produkt ist noch auf Lager)*.
1. Öffnen Sie die [!UICONTROL Category]-Seite in der Storefront erneut.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird nicht aus dem Cache geladen. Er wird neu generiert.

<u>Erwartete Ergebnisse</u>:

Die Seite wird aus dem Cache geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
