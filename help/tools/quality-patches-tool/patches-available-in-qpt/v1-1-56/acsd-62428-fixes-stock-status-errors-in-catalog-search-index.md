---
title: 'ACSD-62428: Stock-Statusfehler im Katalogsuchindex'
description: Wenden Sie den Patch ACSD-62428 an, um das Problem zu beheben, dass der Wert „is_out_of_stock“ im Katalogsuchindex falsch festgelegt ist, wenn die SKU nicht als durchsuchbares Attribut festgelegt ist.
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-62428: Stock-Statusfehler im Katalogsuchindex

Der Patch ACSD-62428 behebt das Problem, dass `is_out_of_stock` Werte im Katalogsuchindex auf einen falschen Wert eingestellt sind, wenn das SKU-Attribut nicht als durchsuchbar festgelegt ist. Dieser Patch ist ab dem [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 verfügbar. Die Patch-ID ist ACSD-62428. Das Problem wurde planmäßig in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der `is_out_of_stock` im Katalogsuchindex ist auf einen falschen Wert eingestellt, wenn die SKU nicht als durchsuchbares Attribut konfiguriert ist, was zu einer ungenauen Bestandsdarstellung führt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen eines benutzerdefinierten [!UICONTROL Source] und eines benutzerdefinierten [!UICONTROL Stock].
1. Erstellen Sie drei einfache Produkte und weisen Sie deren Inventar dem benutzerdefinierten [!UICONTROL Source] zu. Diese Produkte einer Kategorie zuweisen.
1. *[!UICONTROL Inventory (MSI) Indexer]* auf *[!UICONTROL Update on Save]* festgelegt, um die Replikation zu vereinfachen.
1. Legen Sie die *[!UICONTROL Source Item Status]* auf *[!UICONTROL In Stock]* fest und weisen Sie eine *[!UICONTROL Quantity]* zu.
1. Speichern Sie das Produkt.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und öffnen Sie das Attribut **[!UICONTROL SKU]** .
1. Legen Sie *[!UICONTROL Use In]* auf *[!UICONTROL No]* fest.
1. Ändern Sie die Produktmenge (stellen Sie sicher, dass sie nicht auf 0 gesetzt ist).
1. Speichern Sie das Produkt.

<u>Erwartete Ergebnisse</u>:

Der `is_out_of_stock`-Wert spiegelt den Lagerstatus des Produkts genau wider, auch wenn die SKU kein durchsuchbares Attribut ist.

<u>Tatsächliche Ergebnisse</u>:

Der `is_out_of_stock`-Wert wird fälschlicherweise auf 1 gesetzt, und das SKU-Attribut fehlt in den indizierten Daten.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
