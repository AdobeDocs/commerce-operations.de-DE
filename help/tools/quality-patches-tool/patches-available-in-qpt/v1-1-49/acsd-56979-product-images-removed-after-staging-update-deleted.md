---
title: 'ACSD-56979: Nach Staging-Update entfernte Produktbilder gelöscht'
description: Wenden Sie den ACSD-56979-Patch an, um das Adobe Commerce-Problem zu beheben, dass Produktbilder nach dem Löschen eines Staging-Updates entfernt werden
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '390'
ht-degree: 0%
---
# ACSD-56979: Nach Staging-Update entfernte Produktbilder gelöscht

Mit dem Patch ACSD-56979 wird das Problem behoben, dass Produktbilder nach dem Löschen einer Staging-Aktualisierung entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-56979. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produktbilder werden nach dem Löschen einer Staging-Aktualisierung entfernt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie in der Commerce Admin -Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein Produkt.
1. Laden Sie unter **[!UICONTROL Images and Videos]** ein Bild hoch und speichern Sie das Produkt.
1. Wählen Sie im **[!UICONTROL Scheduled Changes]** die Option **[!UICONTROL Schedule New Update]** aus.
   1. Wählen Sie ein Startdatum einige Minuten später aus.
   1. Kein Enddatum auswählen.
1. Klicken Sie im **[!UICONTROL Scheduled Changes]** auf den Link **[!UICONTROL View/Edit]** .
1. Navigieren Sie zu **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** und wählen Sie **[!UICONTROL Done]**.
1. Aktualisieren Sie die Seite.

<u>Erwartete Ergebnisse</u>:

Da das Update vor dem geplanten Startdatum entfernt wird, sollte das Produkt unverändert bleiben.

<u>Tatsächliche Ergebnisse</u>:

Der Bildinhalt geht verloren und zeigt null Bytes an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
