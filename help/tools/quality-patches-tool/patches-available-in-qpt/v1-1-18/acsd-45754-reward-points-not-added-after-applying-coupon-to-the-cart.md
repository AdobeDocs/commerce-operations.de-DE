---
title: 'ACSD-45754: Prämienpunkte werden nach Anwendung des Gutscheins auf den Warenkorb nicht hinzugefügt'
description: Der Patch des ACSD-45754 löst das Problem, dass Belohnungspunkte nicht hinzugefügt werden, nachdem ein Coupon auf den Warenkorb angewendet wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45754. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-45754: Prämienpunkte werden nach Anwendung des Gutscheins auf den Warenkorb nicht hinzugefügt

Der Patch des ACSD-45754 löst das Problem, dass Belohnungspunkte nicht hinzugefügt werden, nachdem ein Coupon auf den Warenkorb angewendet wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45754. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bonuspunkte werden nach dem Anwenden eines Coupons auf den Warenkorb nicht hinzugefügt.

<u>Voraussetzungen</u>:

Die PayPal-Zahlungsmethode ist konfiguriert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie die Prämienpunktwechselkurse unter **Speichern** > **Andere Einstellungen** > **Prämienwechselkurse**.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem Couponcode, um 100 Prämienpunkte für angemeldete Kunden anzuwenden.
1. Checken Sie ein Produkt als angemeldeter Kunde mit PayPal und dem Gutscheincode aus.
1. Überprüfen Sie den Verlauf der Belohnungspunkte unter dem Kundenkonto in der Admin Console.

<u>Erwartete Ergebnisse</u>:

Prämienpunkte werden dem Kunden gemäß der Preisregel hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Dem Kunden werden keine Prämienpunkte hinzugefügt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
