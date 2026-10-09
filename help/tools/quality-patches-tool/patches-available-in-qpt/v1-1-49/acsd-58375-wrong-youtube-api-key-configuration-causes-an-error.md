---
title: 'ACSD-58375: Falsch konfigurierter YouTube-API-Schlüssel verursacht Fehler beim Hinzufügen von Videos auf Store-Ansichtsebene'
description: Wenden Sie den Patch ACSD-58375 an, um das Adobe Commerce-Problem zu beheben, bei dem eine falsche Konfiguration des YouTube-API-Schlüssels einen Fehler verursacht, wenn ein YouTube-Video auf Store-Ansichtsebene hinzugefügt wird.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '431'
ht-degree: 0%
---
# ACSD-58735: Falsch konfigurierter YouTube-API-Schlüssel verursacht Fehler beim Hinzufügen von Videos auf Store-Ansichtsebene

Der Patch ACSD-58735 behebt das Problem, dass eine falsche Konfiguration des YouTube-API-Schlüssels einen Fehler verursacht, wenn ein YouTube-Video auf Store-Ansichtsebene hinzugefügt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58735. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine falsche Konfiguration des YouTube-API-Schlüssels verursacht einen Fehler, wenn ein YouTube-Video auf Store-Ansichtsebene hinzugefügt wird.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zu Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Ändern Sie *Umfang* auf *[!UICONTROL Main Website]*.
1. Fügen Sie den YouTube-API-Schlüssel hinzu.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Wählen Sie ein beliebiges Produkt aus und scrollen Sie zu *[!UICONTROL Images and Video]*. Klicken Sie auf **[!UICONTROL Add Video]**.
1. Kopieren Sie einen YouTube-Video-Link und fügen Sie ihn in das Feld Video-Link ein. Aus dem Feld aussteigen.

<u>Erwartete Ergebnisse</u>:

Der YouTube-API-Schlüssel hat einen globalen Gültigkeitsbereich und wird auf Website-Ebene ausgeblendet.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird ausgelöst: *Video wird aus folgendem Grund nicht angezeigt: API-Schlüssel ist ungültig. Bitte einen gültigen API-Schlüssel*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
