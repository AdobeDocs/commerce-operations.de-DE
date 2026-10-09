---
title: 'ACSD-62415: Adobe Commerce-Backend lädt [!UICONTROL Categories] sehr langsam'
description: Wenden Sie den Patch ACSD-62415 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Categories] im [!UICONTROL Admin] sehr langsam geladen wird, wenn eine große Anzahl von Ankerkategorien vorhanden ist.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 3101723d-dcc0-49fa-a823-2a2d37037534
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# ACSD-62415: Das Adobe Commerce-Backend **[!UICONTROL Categories]** sehr langsam geladen, wenn Ankerkategorien vorhanden sind

Mit dem Patch ACSD-62415 wird das Problem behoben, dass die Leistung der **[!UICONTROL Categories]** Seite im **[!UICONTROL Admin]** Bedienfeld sehr langsam geladen wird, wenn eine große Anzahl von Ankerkategorien vorhanden ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-62415. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die **[!UICONTROL Categories]** Seite im **[!UICONTROL Admin]** wird nur sehr langsam geladen, wenn eine große Anzahl von Ankerkategorien vorhanden ist.

<u>Schritte zur Reproduktion</u>:

1. Generieren von 3K-Ankerkategorien.
1. Öffnen Sie **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** im **[!UICONTROL Admin]**.

<u>Erwartete Ergebnisse</u>:

Die **[!UICONTROL Categories]** Seite wird schnell geladen und die Abfrage sollte nicht 1K-mal wiederholt werden.

<u>Tatsächliche Ergebnisse</u>:

Das Laden dauert 7 bis 20 Sekunden, und die Abfrage wird mehr als 1K-mal ausgeführt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
