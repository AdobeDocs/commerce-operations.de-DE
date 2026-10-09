---
title: 'ACSD-52399: Produkt mit verkaufbarer Menge 0 auf Lager'
description: Wenden Sie den Patch ACSD-52399 an, um das Adobe Commerce-Problem zu beheben, bei dem die konfigurierbare Produktoption mit einer verkäuflichen Menge von 0 auf der Produktseite „Auf Lager“ anzeigt.
feature: Products, Configuration
role: Admin, Developer
exl-id: 7b7332bb-15ae-44b6-a347-38ac7c9001db
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '393'
ht-degree: 0%
---
# ACSD-52399: Produkt mit verkaufbarer Menge 0 auf Lager

Mit dem Patch ACSD-52399 wird das Problem behoben, dass die konfigurierbare Produktoption mit einer skalierbaren Menge von null (0) *Auf Lager* auf der Produktseite angezeigt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52399. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Konfigurierbare Produktoption mit einer verkaufbaren Menge von null (0) zeigt *Auf Lager* auf der Produktseite.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit der Produktoption Null (0) für skalierbare Mengen.
1. Wechseln Sie zur Produktseite in der Storefront und wählen Sie das konfigurierbare Produkt aus, um eine Variante/Konfiguration zu überprüfen.
1. Wählen Sie **[!UICONTROL Add to Cart]** aus.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Add to Cart]* Schaltfläche ist bei Auswahl der Produktkonfiguration *Nicht vorrätig* nicht verfügbar.

<u>Tatsächliche Ergebnisse</u>:

Konfigurierbare Varianten sind in der Storefront verfügbar und Sie können sie auswählen und zum Warenkorb hinzufügen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
