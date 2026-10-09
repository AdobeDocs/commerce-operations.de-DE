---
title: 'AC-15223: Die Storefront-Seite zeigt zwischengespeicherte Inhalte nach dem Wechsel des Stores an'
description: Wenden Sie den AC-15223-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem nach dem Wechsel des Speichers die Seite aus dem Cache bereitgestellt wird und der Speicher nicht wie erwartet gewechselt wird.
feature: Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 22257e94-8d59-4221-bf79-1d63b5600498
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '333'
ht-degree: 0%
---
# AC-15223: Die Storefront-Seite zeigt zwischengespeicherte Inhalte nach dem Wechsel des Stores an

Mit dem AC-15223-Patch wird das Problem behoben, dass die Seite nach dem Wechseln der Stores aus dem Cache bereitgestellt wird, da der Store Switcher nicht funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist AC-15223. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Wechsel des Stores wird die Seite aus dem Cache bereitgestellt (der Store-Umschalter funktioniert nicht).

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**.
2. Erstellen Sie eine neue Store-Ansicht.
3. Wechseln Sie zur Storefront und versuchen Sie, die Store-Ansichten zu wechseln.

<u>Erwartete Ergebnisse</u>:

Die Store-Ansicht wurde erfolgreich gewechselt.

<u>Tatsächliche Ergebnisse</u>:

Der Name der Store-Ansicht wird in der Kopfzeile erst geändert, wenn der Cache vom Backend bereinigt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
