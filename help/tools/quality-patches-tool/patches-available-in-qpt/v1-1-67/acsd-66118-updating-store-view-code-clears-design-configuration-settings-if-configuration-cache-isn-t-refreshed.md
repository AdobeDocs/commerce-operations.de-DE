---
title: 'ACSD-66118: Durch die Aktualisierung von [!UICONTROL Store View Code] werden [!UICONTROL Design Configuration] Einstellungen gelöscht, wenn [!UICONTROL Configuration Cache] nicht aktualisiert wird'
description: Wenden Sie den ACSD-66118-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem durch die Aktualisierung des [!UICONTROL Store View Code] der [!UICONTROL Design Configuration] (Design- und benutzerdefinierte Einstellungen) gelöscht wird, wenn die [!UICONTROL Configuration Cache] nicht ordnungsgemäß aktualisiert wird.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '347'
ht-degree: 0%
---
# ACSD-66118: Durch die Aktualisierung von **[!UICONTROL Store View Code]** werden **[!UICONTROL Design Configuration]** Einstellungen gelöscht, wenn **[!UICONTROL Configuration Cache]** nicht aktualisiert wird

Mit dem Patch ACSD-66118 wird das Problem behoben, dass bei Aktualisierung des **[!UICONTROL Store View Code]** **[!UICONTROL Design Configuration]** Einstellungen gelöscht werden, wenn der **[!UICONTROL Configuration Cache]** nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66118. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

**[!UICONTROL Design Configuration]** Einstellungen (wie Design- und benutzerdefinierte Einstellungen) werden beim Aktualisieren des **[!UICONTROL Store View Code]** gelöscht, wenn die **[!UICONTROL Configuration Cache]** nicht aktualisiert wird.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei **[!UICONTROL Admin]** Panel an.
2. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**.
3. Bearbeiten Sie eine Store-Ansicht, in der unter **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** ein benutzerdefiniertes Design konfiguriert ist.
4. Ändern Sie das **[!UICONTROL Code]** Feld (z. B. von `storeview_1` zu `storeview_main`).
5. Klicken Sie auf **[!UICONTROL Save Store View]** , um die Änderungen zu speichern.
6. Aktualisieren oder öffnen Sie die Seite **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** für die aktualisierte **[!UICONTROL Store View]** erneut, und es wird kein Design ausgewählt.

<u>Erwartete Ergebnisse</u>:

Nach dem Aktualisieren der **[!UICONTROL Store View Code]** sollte die **[!UICONTROL Design Configuration]** (einschließlich Design und benutzerdefinierten Einstellungen) intakt bleiben.

<u>Tatsächliche Ergebnisse</u>:

Der **[!UICONTROL Design Configuration]** wird gelöscht. Das Design wird auf den Standard zurückgesetzt und benutzerdefinierte Einstellungen gehen verloren.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
