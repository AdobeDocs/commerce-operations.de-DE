---
title: 'ACSD-62755: [!DNL TinyMCE] 7 benötigt Schriftgröße und Schriftart, die zu den Editor-Initialisierungseinstellungen hinzugefügt werden'
description: Wenden Sie den Patch ACSD-62755 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL TinyMCE] 7 erfordert, dass *font size* und *font family* speziell in den Editor-Initialisierungseinstellungen hinzugefügt werden.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '328'
ht-degree: 0%
---
# ACSD-62755: [!DNL TinyMCE] 7 benötigt Schriftgröße und Schriftart, die zu den Editor-Initialisierungseinstellungen hinzugefügt werden

Mit dem Patch ACSD-62755 wird das Problem behoben, dass [!DNL TinyMCE] 7 *Selektoren* Schriftgröße) und *Schriftfamilie* erfordert, die speziell in den Editor-Initialisierungseinstellungen hinzugefügt werden müssen. Dieser Patch ist ab dem [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) verfügbar, in dem 1.1.56 installiert ist. Die Patch-ID ist ACSD-62755. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p10

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL TinyMCE] 7 erfordert, *Selektoren für* Schriftgröße“ und *Schriftfamilie* in den Editor-Initialisierungseinstellungen speziell hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** und wählen Sie *[!UICONTROL Show Editor]* aus.

<u>Erwartete Ergebnisse</u>:

*Schriftgröße* und *Schriftfamilie* werden im WYSIWYG-Editor angezeigt.

<u>Tatsächliche Ergebnisse</u>:

*Schriftgröße*-Auswahl fehlt im WYSIWYG-Editor.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
