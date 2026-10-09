---
title: 'ACSD-51984: Nicht aktivierte [!UICONTROL Use Default Value] und nicht standardmäßige Produktfeldwerte werden für die zweite Website-, Store- und Store-Ansicht nicht gespeichert'
description: Wenden Sie den Patch ACSD-51984 an, um das Adobe Commerce-Problem zu beheben, bei dem die nicht aktivierten [!UICONTROL Use Default Value]- und Nicht-Standardproduktfeldwerte nicht für die zweite Website-, Store- und Store-Ansicht gespeichert werden.
feature: Products
role: Admin
exl-id: 51a810fa-d416-4b37-b5bd-66eed9fe4626
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-51984: Nicht aktivierte *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfeldwerte werden nicht gespeichert

>[!NOTE]
>
>Dieser Patch ist veraltet und wurde durch den Patch [ACSD-54776](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) ersetzt, der in der Version 1.1.39 QPT hinzugefügt wurde.

Mit dem Patch ACSD-51984 wird das Problem behoben, dass die nicht aktivierten **[!UICONTROL Use Default Value]** und nicht standardmäßigen Produktfeldwerte für die zweite Website-, Store- und Store-Ansicht nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51984. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Deaktivierte *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfeldwerte werden für die zweite Website-, Store- und Store-Ansicht nicht gespeichert.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zum Backend, navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** und erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, erstellen Sie ein einfaches Produkt und speichern Sie es, und weisen Sie das Produkt über die **[!UICONTROL Product in Websites]** beiden Websites zu.
1. Ändern Sie in Schritt 2 den Bereich in die neu erstellte Store-Ansicht.
1. Gehen Sie zu **[!UICONTROL Search Engine Optimization]** und deaktivieren Sie die Kontrollkästchen **[!UICONTROL Use Default Value]** für [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] und [!UICONTROL Meta Description].
1. Bereinigen Sie den Text in den Feldern *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* und *[!UICONTROL Meta Description]* und klicken Sie auf **[!UICONTROL Save]**.
1. Gehe noch einmal zu **[!UICONTROL Search Engine Optimization]**.

<u>Erwartete Ergebnisse</u>

Die Werte für die Felder und für die Kontrollkästchen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>

Die Werte für die Felder und für die Kontrollkästchen werden nicht gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
