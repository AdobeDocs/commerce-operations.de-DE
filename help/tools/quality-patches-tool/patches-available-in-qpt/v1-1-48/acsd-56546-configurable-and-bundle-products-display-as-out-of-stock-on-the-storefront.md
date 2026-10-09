---
title: 'ACSD-56546: Konfigurierbare und gebündelte Produkte werden in der Storefront als nicht vorrätig angezeigt'
description: Wenden Sie den Patch ACSD-56546 an, um das Adobe Commerce-Problem zu beheben, bei dem die konfigurierbaren - und -Bundle-Produkte als nicht vorrätig auf der Storefront angezeigt werden, wenn die Konfigurationsoption *[!UICONTROL Display Out of Stock Products]* deaktiviert ist.
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '454'
ht-degree: 0%
---
# ACSD-56546: Konfigurierbare und gebündelte Produkte werden in der Storefront als nicht vorrätig angezeigt

Mit dem Patch ACSD-56546 wird das Problem behoben, dass die konfigurierbaren - und -Bundle-Produkte in der Storefront als nicht vorrätig angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56546. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Konfigurierbare und gebündelte Produkte werden in der Storefront als nicht vorrätig angezeigt, wenn *[!UICONTROL Display Out of Stock Products]* Option deaktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie die Option **[!UICONTROL Display Out of Stock Products]** auf *Nein*.
1. Erstellen einer Website, eines Stores und einer Storeview.
1. Erstellen Sie eine Quelle und ein Lager und weisen Sie sie dann der zweiten Website zu.
1. Erstellen Sie ein *konfigurierbares Produkt* mit zwei untergeordneten Produkten. Weisen Sie sowohl die untergeordneten Produkte beiden Quellen als auch beiden Websites zu.
1. Aktualisieren Sie das erste untergeordnete Produkt so, dass es *qty=0* in beiden Quellen hat.
1. Aktualisieren Sie das zweite untergeordnete Produkt, und deaktivieren Sie es auf der zweiten Website.
1. Führen Sie eine vollständige Neuindizierung durch.
1. Überprüfen Sie die Kategorie, die das konfigurierbare Produkt auf der zweiten Website enthält.

<u>Erwartete Ergebnisse</u>:

Die nicht vorrätigen konfigurierbaren Produkte sind in der Storefront nicht sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Die nicht vorrätigen konfigurierbaren Produkte sind auch dann in der Storefront sichtbar, wenn die *[!UICONTROL Display Out of Stock Products]* Option deaktiviert ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
