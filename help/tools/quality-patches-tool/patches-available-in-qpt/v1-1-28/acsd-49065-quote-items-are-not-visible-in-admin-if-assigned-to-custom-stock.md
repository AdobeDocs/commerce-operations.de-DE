---
title: 'ACSD-49065: Angebotselemente sind in Admin nicht sichtbar'
description: Wenden Sie den ACSD-49065 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Angebotselemente in der Admin nicht sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%
---
# ACSD-49065: Angebotselemente sind in Admin nicht sichtbar

Mit dem Patch ACSD-49065 wird das Problem behoben, dass die Angebotselemente im Administrator nicht sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49065. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Angebotselemente sind im Admin nicht sichtbar, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.

Voraussetzungen:

**[!UICONTROL B2B]** und **[!UICONTROL Inventory]** Module müssen installiert werden.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL Company]** und **[!UICONTROL B2B Quote]** unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Erstellen Sie eine sekundäre **[!UICONTROL Inventory Source]** und weisen Sie sie einem sekundären **[!UICONTROL Inventory Stock]** zu.
1. Erstellen Sie ein neues Produkt, indem Sie nur das sekundäre (nicht standardmäßige) **[!UICONTROL Inventory Source]** zuweisen.
1. Gehen Sie zum StoreFront und erstellen Sie ein neues Unternehmenskonto. Melden Sie sich als **[!UICONTROL Company Admin]** an und fügen Sie das erstellte Produkt zum Warenkorb hinzu.
1. Navigieren Sie zum Warenkorb und *[!UICONTROL Request a Quote]* Sie .
1. Rufen Sie den Administrator auf und zeigen Sie das gewünschte Angebot unter **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** an.

<u>Erwartete Ergebnisse</u>:

In dem neuen Angebot, das mit neuen Produkten erstellt wurde, sind die Elemente sichtbar, ohne dass die Produkte erneut gespeichert werden müssen.

<u>Tatsächliche Ergebnisse</u>:

Der *[!UICONTROL Items Quoted]* ist leer. Wenn Sie das neu erstellte Produkt erneut speichern, werden die Elemente angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
