---
title: 'ACSD-49822: Aktualisierungen auf der Seite der Anforderungsliste werden nicht in der Druckanforderungsliste angezeigt'
description: Wenden Sie den Patch ACSD-49822 an, um das Adobe Commerce-Problem zu beheben, bei dem Aktualisierungen auf der Seite „Anforderungsliste“ nicht in der Druckanforderungsliste angezeigt werden.
feature: Admin Workspace, B2B
role: Admin
exl-id: 053b8900-0900-4b7e-ba1b-ad4b88ca3f35
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
# ACSD-49822: Aktualisierungen in der Anforderungsliste werden nicht in der Druckanforderungsliste angezeigt

Mit dem Patch ACSD-49822 wird das Problem behoben, dass Aktualisierungen auf der Seite „Anforderungsliste“ nicht in der Druckanforderungsliste angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49822. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Aktualisierungen auf der Seite „Anforderungsliste“ werden nicht in der Druckanforderungsliste angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Anforderungsliste, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B-Funktionen]** navigieren.
1. Erstellen Sie ein Produkt.
1. Melden Sie sich als Kunde an und fügen Sie der Anforderungsliste zwei Produkte hinzu.
1. Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Anforderungsliste anzeigen.
1. Klicken Sie oben rechts auf **[!UICONTROL Print]** .
1. Schließen Sie das Druckfenster und drucken Sie die Seite „Anforderungsliste“.
1. Löschen Sie ein Element in der Liste oder aktualisieren Sie eine Menge eines Elements und versuchen Sie erneut, es zu drucken.
1. Sie werden feststellen, dass die Elemente im Druckfenster nicht aktualisiert werden.
1. Schließen Sie das Druckfenster.
1. Sie werden feststellen, dass die Artikel auf der Druckseite der Anforderungsliste nicht aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die zu druckende Liste wird nach jeder Änderung aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Aktualisierungen werden nicht auf der Druckseite der Anforderungsliste angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
