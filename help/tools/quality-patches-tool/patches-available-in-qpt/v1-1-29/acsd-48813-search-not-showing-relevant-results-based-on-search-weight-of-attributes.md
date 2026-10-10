---
title: 'ACSD-48813: Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an'
description: Wenden Sie den Patch ACSD-48813 an, um das Adobe Commerce-Problem zu beheben, bei dem die Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute anzeigt.
feature: Admin Workspace, Attributes, Search
role: Admin
exl-id: 98ef7eb1-c13e-4c56-9a25-8e61cfb5fade
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%
---
# ACSD-48813: Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an

Mit dem Patch ACSD-48813 wird das Problem behoben, dass die Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-48813. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce mit Beispieldaten.
1. Legen Sie die Suchmaschine als [!DNL Elasticsearch] fest.
1. Melden Sie sich als Administrator an.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Öffnen Sie das *name*-Attribut.
1. Öffnen Sie die Registerkarte Storefront-*[!UICONTROL Properties]* .
1. Wählen Sie [!UICONTROL Search Weight] = *10* aus dem Dropdown-Wert aus.
1. Klicken Sie auf **[!UICONTROL Save Attribute]**.
1. Öffnen Sie nun die Storefront und suchen Sie nach dem Wort *Zurück*.

<u>Erwartete Ergebnisse</u>:

Rucksackprodukte werden oben in den Suchergebnissen zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Rucksackprodukte werden mitten in den Suchergebnissen zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
