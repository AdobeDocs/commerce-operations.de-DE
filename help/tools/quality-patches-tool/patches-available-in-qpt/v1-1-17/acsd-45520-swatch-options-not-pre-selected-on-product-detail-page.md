---
title: 'ACSD-45520: Auf der Produktdetailseite sind keine Farbfeldoptionen ausgewählt'
description: Mit dem Patch ACSD-45520 wird das Problem behoben, dass Farbfeldoptionen auf der Produktdetailseite nicht vorausgewählt sind, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45520. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Products
role: Admin
exl-id: a8b37dba-5a02-45a9-8e43-5288352a9d75
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%
---
# ACSD-45520: Auf der Produktdetailseite sind keine Farbfeldoptionen ausgewählt

Mit dem Patch ACSD-45520 wird das Problem behoben, dass Farbfeldoptionen auf der Produktdetailseite nicht vorausgewählt sind, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45520. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Musteroptionen werden auf der Produktdetailseite nicht ausgewählt, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit Produktoptionen (z. B. Farbe).
1. Fügen Sie das konfigurierbare Produkt zum Warenkorb hinzu.
1. Navigieren Sie zur Seite Mein Warenkorb .
1. Klicken Sie auf die Schaltfläche Bearbeiten für das konfigurierbare Produkt, das in Schritt 1 hinzugefügt wurde.
1. Beobachten Sie die Produktoptionen auf der Bearbeitungsseite.

<u>Erwartete Ergebnisse</u>:

Produktoptionen sind ausgewählt.

<u>Tatsächliche Ergebnisse</u>:

Es sind keine Produktoptionen ausgewählt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
