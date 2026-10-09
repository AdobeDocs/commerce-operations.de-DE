---
title: 'ACSD-58790: Korrigiert die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobilansicht auf [!DNL Chrome]'
description: ACSD-58790 behebt das Adobe Commerce-Problem, dass das Bild in der mobilen Ansicht auf [!DNL Chrome] nicht wie erwartet vergrößert wurde.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '416'
ht-degree: 0%
---
# ACSD-58790: Korrigiert die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobilansicht auf [!DNL Chrome]

Mit dem Patch „ACSD-58790“ wird das Adobe Commerce-Problem behoben, bei dem das Bild in der mobilen Ansicht auf [!DNL Chrome] nicht wie erwartet vergrößert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58790. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Korrigiert die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobile-Ansicht auf [!DNL Chrome].

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit einem Bild.
1. Öffnen Sie das Produkt in einem [!DNL Chrome].
1. Klicken Sie auf das Bild und stellen Sie sicher, dass das Bild beim Doppelklicken vergrößert wird.
1. Wechseln Sie mithilfe der [!DNL Chrome] Entwickler-Tools zur mobilen Ansicht.
1. Klicken Sie auf das Bild.
1. Doppeltippen.

<u>Erwartete Ergebnisse</u>:

Das Bild wird beim Doppelklicken vergrößert.

<u>Tatsächliche Ergebnisse</u>:

Das Bild wird beim Doppelklicken nicht vergrößert. Dieses Problem tritt nur bei [!DNL Chrome] in der Mobilansicht auf, da die Zoom-Funktion in [!DNL Firefox] wie erwartet funktioniert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
