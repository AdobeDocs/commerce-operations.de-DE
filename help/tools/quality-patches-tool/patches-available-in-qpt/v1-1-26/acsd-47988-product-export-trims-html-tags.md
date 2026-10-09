---
title: 'ACSD-47988: Der Produktexport schneidet HTML-Tags aus der Produktbeschreibung von Page Builder zurück'
description: Wenden Sie den Patch ACSD-47988 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktexport HTML-Tags aus der Page Builder-Produktbeschreibung kürzt.
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
exl-id: 2cb3b4ac-38df-4832-b894-b34bb3d7bbc6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%
---
# ACSD-47988: Der Produktexport schneidet HTML-Tags aus der Produktbeschreibung von Page Builder zurück

Mit dem Patch „ACSD-47988“ wird das Problem behoben, dass der Produktexport HTML-Tags aus der Produktbeschreibung des Page Builders zuschneidet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-47988. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktexport schneidet HTML-Tags aus der Page Builder-Produktbeschreibung aus.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie Produkte mit HTML in der Beschreibung. Verwenden Sie das HTML-Element von Page Builder, um HTML-Tags einzufügen.
1. Exportieren Sie die Produkte mit der Import-/Exportfunktion von Adobe Commerce.
1. Exportierte CSV-Datei importieren.
1. Öffnen Sie das Produkt und überprüfen Sie die HTML-Elemente unter der Beschreibung.

<u>Erwartete Ergebnisse</u>:

HTML-Tags verbleiben in der Produktbeschreibung, nachdem sie denselben Inhalt importiert haben.

<u>Tatsächliche Ergebnisse</u>:

HTML-Tags werden nach dem Import entfernt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
