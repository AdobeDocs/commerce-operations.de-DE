---
title: 'ACSD-57337: Admin-Benutzende mit Zugriffsbeschränkungen konnten alle Unternehmen im Raster *Firmen* anzeigen'
description: Wenden Sie den Patch ACSD-57337 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im Raster *Unternehmen* anzeigen kann.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '427'
ht-degree: 0%
---
# ACSD-57337: Admin-Benutzende mit Zugriffsbeschränkungen konnten alle Unternehmen im Raster *Firmen* anzeigen

Mit dem Patch ACSD-57337 wird das Problem behoben, dass ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im Raster *Firmen* anzeigen konnte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-57337. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites kann Unternehmen von allen Websites im Raster *Firmen* anzeigen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeview.
1. Erstellen Sie einige Unternehmen, die verschiedenen Websites zugewiesen sind.
1. Erstellen Sie eine Admin-Benutzerrolle und legen Sie den Rollenbereich auf die erstellte Website fest.
1. Erstellen Sie einen Administrator und weisen Sie ihn der erstellten Rolle zu.
1. Melden Sie sich mit einem neuen Administrator an.
1. Öffnen Sie **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und sehen Sie sich die Liste der Gesellschaften an.

<u>Erwartete Ergebnisse</u>:

Die Firmen, die der zusätzlichen Website zugewiesen wurden, sind im Raster *Firmen* sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Alle Unternehmen sind im Raster *Firmen* sichtbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
