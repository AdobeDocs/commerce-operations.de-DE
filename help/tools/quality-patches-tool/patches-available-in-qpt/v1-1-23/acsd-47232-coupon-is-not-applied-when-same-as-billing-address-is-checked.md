---
title: 'ACSD-47232: Coupon wird nicht angewendet, wenn [!UICONTROL Same as Billing Address] aktiviert ist'
description: Wenden Sie den Patch ACSD-47232 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Aktivieren der [!UICONTROL Same as Billing Address] kein Coupon angewendet wird.
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-47232: Coupon wird nicht angewendet, wenn [!UICONTROL Same as Billing Address] aktiviert ist

Mit dem Patch ACSD-47232 wird das Problem behoben, dass der Coupon nicht angewendet wird, wenn **[!UICONTROL Same as Billing Address]** aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47232. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Coupon wird nicht angewendet, wenn **[!UICONTROL Same as Billing Address]** aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce.
1. Erstellen Sie ein einfaches Produkt mit Gewicht = *8*.
1. Erstellen Sie einen neuen Kunden mit der standardmäßigen Rechnungs- und Lieferadresse.
1. Erstellen Sie eine Warenkorb-Preisregel mit einem Coupon.
   * Fügen Sie in **[!UICONTROL Conditions]** Abschnitten *Gesamtgewicht gleich oder größer als 5“*
1. Versuchen Sie, eine neue Bestellung im [!UICONTROL Commerce] Admin zu erstellen.
   * Den soeben erstellten Kunden verwenden
   * Produkt hinzufügen
   * Gutschein anwenden

<u>Erwartete Ergebnisse</u>:

Der Coupon wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein Fehler ähnlich dem folgenden angezeigt: *Der Gutscheincode 123 ist ungültig. Überprüfen Sie den Code und versuchen Sie es erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
