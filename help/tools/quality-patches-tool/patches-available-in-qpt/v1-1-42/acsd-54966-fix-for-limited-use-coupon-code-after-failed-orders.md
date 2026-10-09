---
title: 'ACSD-54966: Fehlerbehebung bei der Wiederverwendung von Gutscheincodes nach fehlgeschlagenen Bestellungen'
description: Wenden Sie den Patch ACSD-54966 an, um das Adobe Commerce-Problem zu beheben, das die Wiederverwendung von Gutscheincodes verhindert, die nach einer zuvor fehlgeschlagenen Bestellung pro Werbeaktion und Warenkorb begrenzt sind.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 19d9b313-1a3c-5bed-9da7-4364f71c3a28
    internal-label: Promotions/Events
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-54966: Fehlerbehebung bei der Wiederverwendung von Gutscheincodes nach fehlgeschlagenen Bestellungen

Mit dem Patch ACSD-54966 wird das Problem behoben, das die Wiederverwendung von Couponcodes pro Kunde nach einer zuvor fehlgeschlagenen Bestellung verhindert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54966. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p10, 2.4.6 - 2.4.6-p8
* Adobe Commerce: 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Couponcode, der auf den einmaligen Gebrauch pro Kunde beschränkt ist, kann nach einer fehlgeschlagenen vorherigen Bestellung nicht wiederverwendet werden.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie eine Warenkorb-Preisregel mit *[!UICONTROL Uses per Customer]* = *1* ein.
1. Machen Sie einen Kauf mit dem zugewiesenen Gutscheincode.
1. Stornieren Sie die Bestellung im Admin-Panel oder führen Sie die Bestellung mit einem Zahlungsfehler aus.
1. Führen Sie den folgenden Befehl aus: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Versuchen Sie, eine nachfolgende Bestellung mit demselben Couponcode für denselben Kunden aufzugeben.

<u>Erwartete Ergebnisse</u>:

Nach Stornierung der Bestellung oder einem Zahlungsfehler kann der Kunde den Couponcode erfolgreich für einen neuen Kauf wiederverwenden.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde kann den Gutscheincode nicht wiederverwenden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
