---
title: 'ACSD-45781: Feld für die Storefront-Suche wird auf Mobilgerät nicht angezeigt'
description: Der Patch MDVA-45781 löst das Problem, dass das Suchfeld „Storefront“ auf Mobilgeräten nicht angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 installiert ist. Die Patch-ID lautet MDVA-45781. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Cache, Native Luma Frontend Development, Search
role: Admin
exl-id: f761461b-2dd0-45d2-b80d-57793f6f0924
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: aa64eb87-f03e-49eb-a367-66fa1adc2192
    internal-label: Native Luma Frontend Development
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
source-wordcount: '413'
ht-degree: 0%
---
# ACSD-45781: Feld für die Storefront-Suche wird auf Mobilgerät nicht angezeigt

Der Patch MDVA-45781 löst das Problem, dass das Suchfeld „Storefront“ auf Mobilgeräten nicht angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.19 installiert ist. Die Patch-ID lautet MDVA-45781. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Suchfeld „Storefront“ wird auf einem Mobilgerät nicht angezeigt

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu Commerce Admin > **Stores** > **Configuration** > **Catalog** > **Catalog Search** und legen Sie Folgendes fest:
   * Suchempfehlungen aktivieren auf *Nein*
   * Aktivieren von Suchvorschlägen auf *Nein*
1. Klicken Sie auf die Schaltfläche **Konfiguration speichern**.
1. Cache bereinigen.
1. Verwenden Sie das Standard-Luma-Design, um mit Mobile zu suchen.
1. Klicken Sie auf die Schaltfläche **Suchen**.

<u>Erwartete Ergebnisse</u>:

Das Eingabesuchformular wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Nichts passiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
