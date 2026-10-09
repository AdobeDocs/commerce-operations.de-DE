---
title: 'ACSD-48070: Ausnahme beim Bearbeiten einer geplanten Aktualisierung'
description: Wenden Sie den ACSD-48070 Patch an, um das Problem in Adobe Commerce zu beheben, bei dem beim Bearbeiten eines geplanten Updates ein Ausnahmefehler ausgelöst wird.
feature: Catalog Management, Categories
role: Admin
exl-id: cebed18d-d213-4a5e-bc3b-8abcb52d45d0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%
---
# ACSD-48070: Ausnahme beim Bearbeiten einer geplanten Aktualisierung

Mit dem Patch „ACSD-48070“ wird das Problem behoben, dass beim Bearbeiten einer geplanten Aktualisierung eine Ausnahme ausgelöst wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-48070. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Bearbeiten einer geplanten Aktualisierung wird eine Ausnahme ausgelöst.

<u>Schritte zur Reproduktion</u>:

1. Beliebige Kategorie öffnen.
2. Erstellen Sie ein neues **[!UICONTROL Scheduled Update]** und speichern Sie es.
3. Klicken Sie im erstellten **[!UICONTROL Scheduled Update]** auf **[!UICONTROL View/Edit]** .
4. Speichern Sie sie erneut.

<u>Erwartete Ergebnisse</u>

Die **[!UICONTROL Scheduled Update]** wird gespeichert.

<u>Tatsächliche Ergebnisse</u>

Ein Fehler tritt auf: *Fehler: : Beim Speichern von Magento\Catalog\Api\Data\CategoryInterface ist ein Fehler aufgetreten.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
