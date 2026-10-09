---
title: 'MDVA-42269: Administratorbenutzer kann sich aufgrund des Fehlers „TypeError“ nicht bei Admin anmelden'
description: Der Patch MDVA-42269 behebt das Problem, dass sich Admin-Benutzer aufgrund von TypeError nicht bei Admin anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 installiert ist.  Die Patch-ID lautet MDVA-42269.  Das neueste Patch-Update ist in QPT 1.1.15. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace
role: Admin
exl-id: 42ad4bb5-950f-476d-bf55-931b38bcb937
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%
---
# MDVA-42269: Administratorbenutzer kann sich aufgrund des Fehlers „TypeError“ nicht bei Admin anmelden

Der Patch MDVA-42269 behebt das Problem, dass sich Admin-Benutzer aufgrund von TypeError nicht bei Admin anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist.  Die Patch-ID lautet MDVA-42269.  Das neueste Patch-Update ist in QPT 1.1.15. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1, 2.3.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratorbenutzer können sich aufgrund des folgenden Fehlers nicht bei Admin anmelden: *TypeError: strtotime() erwartet, dass Parameter 1 eine Zeichenfolge ist, null angegeben.*

<u>Schritte zur Reproduktion</u>:

Melden Sie sich bei Commerce Admin an.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann sich mit dem richtigen Benutzernamen und Kennwort anmelden.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator kann sich nicht anmelden. Der folgende Fehler wird protokolliert: *TypeError: strtotime() erwartet, dass Parameter 1 eine Zeichenfolge ist, null angegeben.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
