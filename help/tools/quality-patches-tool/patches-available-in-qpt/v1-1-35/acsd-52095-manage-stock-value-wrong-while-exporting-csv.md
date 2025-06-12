---
title: 'ACSD-52095: Verwalten des Lagerwerts ist beim Exportieren von CSV falsch'
description: Wenden Sie den Patch ACSD-52095 an, um das Adobe Commerce-Problem zu beheben, bei dem der Lagerwert des Produkts „Verwalten“ beim Exportieren von CSV falsch ist.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] Wert ist beim Exportieren von CSV falsch

Mit dem Patch ACSD-52095 wird das Problem behoben, dass beim Exportieren von CSV der Wert des `manage_stock` falsch ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52095. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der `manage_stock` wird in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** und setzen Sie **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Ein neues Produkt erstellen und speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Wählen Sie *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* aus und exportieren Sie die Produkte.
1. Überprüfen Sie die generierte CSV-Datei: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Wechseln Sie erneut zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** und legen Sie **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]* fest.
1. Navigieren Sie **System** > **Export**.
Wählen Sie *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Überprüfen Sie die generierte CSV-Datei: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Öffnen Sie das Produkt im Admin-Bereich, navigieren Sie zu **[!UICONTROL Advanced Inventory]** und überprüfen Sie den **[!UICONTROL Manage Stock]**.

<u>Erwartete Ergebnisse</u>

Der **[!UICONTROL Manage Stock]** ist *1* wenn er für die Produkte aktiviert ist.

<u>Tatsächliche Ergebnisse</u>

Der **[!UICONTROL Manage Stock]** ist *0*, wenn er für die Produkte aktiviert ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
