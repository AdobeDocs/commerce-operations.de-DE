---
title: 'ACSD-63326: Behebung eines Admin-Umleitungsproblems nach einer Bestellung über das Backend'
description: Wenden Sie den Patch „ACSD-63326“ an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator nach einer Bestellung über das Backend zu einer fehlerhaften Seite weitergeleitet wird.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-63326: Behebung eines Admin-Umleitungsproblems nach einer Bestellung über das Backend

Mit dem Patch ACSD-63326 wird das Problem behoben, dass der Administrator nach einer Bestellung über das Backend zu einer fehlerhaften Seite weitergeleitet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-63326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren werden zu einer Seite mit einem fehlerhaften Layout umgeleitet, nachdem sie erfolgreich eine Bestellung für einen Kunden über das Backend aufgegeben haben.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Abschnitt **[!UICONTROL Customers]** im Admin-Bedienfeld.
1. Wählen Sie einen beliebigen Kunden aus und klicken Sie auf **[!UICONTROL Edit]**.
1. Klicken Sie auf der Seite „Kundendetails“ im oberen Menü auf **[!UICONTROL Create Order]** .
1. Wählen Sie den [!UICONTROL FR French] Store aus und fügen Sie der Bestellung alle verfügbaren Produkte hinzu.
1. Füllen Sie an der Kasse die erforderlichen Details aus und klicken Sie auf **[!UICONTROL Get shipping methods and rates]**.
1. Klicken Sie **[Bestellung übermitteln]**, um die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Der Administrator wird zur Bestellbestätigungs- oder Dankeseite mit dem richtigen Layout weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator wird zu einer Seite mit fehlerhaftem Layout umgeleitet. Das Layout wird erst nach dem Aktualisieren der Seite korrigiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
