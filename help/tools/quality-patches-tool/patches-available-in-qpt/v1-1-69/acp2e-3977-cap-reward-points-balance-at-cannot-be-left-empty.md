---
title: 'ACP2E-3977: [!UICONTROL Cap Reward Points Balance At] Feld darf nicht leer bleiben'
description: Wenden Sie den Patch ACP2E-3977 an, um das Adobe Commerce-Problem zu beheben, bei dem das Feld **[!UICONTROL Cap Reward Points Balance At]** beim Festlegen des Felds **[!UICONTROL Rewards Points Balance Redemption Threshold]** nicht leer gelassen werden konnte, was einen Validierungsfehler verursachte.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
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
source-wordcount: '323'
ht-degree: 0%
---
# ACP2E-3977: **[!UICONTROL Cap Reward Points Balance At]** Feld darf nicht leer bleiben

Der Patch ACP2E-3977 behebt das Problem, dass **[!UICONTROL Cap Reward Points Balance At]** Feld nicht leer gelassen werden kann, auch wenn es erlaubt sein sollte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID lautet ACP2E-3977. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p10

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn **[!UICONTROL Cap Reward Points Balance At]** Trigger leer bleiben, wird ein Validierungsfehler ausgegeben, obwohl die Begrenzung deaktiviert werden sollte, wenn sie leer gelassen wird.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**.
1. **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Lassen Sie **[!UICONTROL Cap Reward Points Balance At]** leer.
1. Speichern.

<u>Erwartete Ergebnisse</u>:

Ein leerer Wert für **[!UICONTROL Cap Reward Points Balance At]** ist zulässig und deaktiviert die Einschränkung.

<u>Tatsächliche Ergebnisse</u>:

*Der Punktestand für die Obergrenze ist ungültig. Der Saldo muss eine positive Zahl sein oder leer bleiben. Überprüfen und erneut versuchen.* Der Fehler wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
