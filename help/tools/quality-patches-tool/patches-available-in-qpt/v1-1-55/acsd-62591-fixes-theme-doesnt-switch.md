---
title: 'ACSD-62591: Design wechselt nicht, wenn **[!UICONTROL User Agent Rules]** konfiguriert ist'
description: Wenden Sie den Patch ACSD-62591 an, um das Adobe Commerce-Problem zu beheben, bei dem das Design nicht richtig wechselt, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind.
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
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
source-wordcount: '326'
ht-degree: 0%
---
# ACSD-62591: Design wechselt nicht richtig, wenn es konfiguriert [!UICONTROL User Agent Rules]

Der Patch ACSD-62591 behebt das Problem, dass das Design nicht richtig wechselt, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-62591. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Design wechselt nicht richtig, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Bearbeiten eines Store-Ansichtsdesigns.
1. Legen Sie `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` in **[!UICONTROL User Agent Rules]** fest und wählen Sie ein anderes Design.
1. Änderungen speichern und Caches löschen.
1. Öffnen Sie eine Storefront-Seite auf einem Mobilgerät.
1. Öffnen Sie dieselbe Seite über einen Desktop-Browser.

<u>Erwartete Ergebnisse</u>:

Der Desktop-Browser und das Mobilgerät zeigen Seiten mit ihren jeweiligen Designs an.

<u>Tatsächliche Ergebnisse</u>:

Der Desktop-Browser zeigt die zwischengespeicherte Seite mit dem mobilen Design an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

