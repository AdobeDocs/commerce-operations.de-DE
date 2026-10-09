---
title: 'MDVA-27456: Beim Laden von Swagger wird eine Fehlermeldung angezeigt'
description: Der Patch MDVA-27456 behebt das Problem, dass Benutzende einen Fehler erhalten, wenn sie versuchen, Swagger zu laden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-27456. Beachten Sie, dass das Problem in Adobe Commerce 2.3.7 behoben wurde.
feature: Tools and External Services
role: Admin
exl-id: a7d5dc7d-b916-4a09-9068-646f8474bba4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%
---
# MDVA-27456: Beim Laden von Swagger wird eine Fehlermeldung angezeigt

Der Patch MDVA-27456 behebt das Problem, dass Benutzende einen Fehler erhalten, wenn sie versuchen, Swagger zu laden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-27456. Beachten Sie, dass das Problem in Adobe Commerce 2.3.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende erhalten eine Fehlermeldung beim Laden von Swagger.

<u>Schritte zur Reproduktion</u>:

Zu `../swagger.`

<u>Erwartete Ergebnisse</u>:

Swagger wird fehlerfrei geladen.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten die folgende Fehlermeldung: *API-Definition konnte nicht geladen*. Das Fehlerprotokoll enthält:

*report.CRITICAL: Bericht-ID: webapi-5ea9c6da19cb1; Nachricht: Der &quot;\DateTime“-Parametertyp ist ungültig. Überprüfen Sie den Parameter und versuchen Sie es erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
