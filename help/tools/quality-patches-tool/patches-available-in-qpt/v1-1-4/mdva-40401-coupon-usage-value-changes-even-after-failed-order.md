---
title: 'MDVA-40401: Änderungen des Couponnutzungswerts nach fehlgeschlagener Bestellung'
description: Der Patch MDVA-40401 behebt das Problem, dass sich der Couponnutzungswert auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Orders
role: Admin
exl-id: bc8eedd6-977f-4f21-bcd1-b5f6c4a6704f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%
---
# MDVA-40401: Änderungen des Couponnutzungswerts nach fehlgeschlagener Bestellung

Der Patch MDVA-40401 behebt das Problem, dass sich der Couponnutzungswert auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzer können den Coupon nicht erneut anwenden, nachdem sie ihn in einer fehlgeschlagenen Reihenfolge verwendet haben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Warenkorbregel mit automatisch generierten Coupons.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und wenden Sie den Gutschein an.
1. Navigieren Sie zu **Checkout**.
1. Machen Sie das hinzugefügte Produkt „nicht vorrätig“, bevor Sie die Bestellung aufgeben.
1. Es sollte ein Fehler *Nicht vorrätig* ausgegeben werden.
1. Cron ausführen.
1. Gehen Sie zum Warenkorb und entfernen Sie das Produkt.
1. Fügen Sie ein weiteres Produkt hinzu und wenden Sie den Gutschein an.

<u>Erwartete Ergebnisse</u>:

Der Gutscheincode sollte erfolgreich angewendet werden, da die vorherige Bestellung nicht aufgegeben wurde.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein Fehler *Gutscheincode ist ungültig* ausgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
