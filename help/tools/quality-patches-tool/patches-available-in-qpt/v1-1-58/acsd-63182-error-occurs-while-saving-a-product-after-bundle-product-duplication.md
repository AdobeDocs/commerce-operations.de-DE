---
title: 'ACSD-63182: Fehler beim Speichern eines Produkts nach der Duplizierung eines Bundles'
description: Wenden Sie den Patch ACSD-63182 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Speichern eines Produkts ein Fehler auftritt, nachdem ein Produktpaket mit aktiviertem MSI dupliziert wurde.
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
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
source-wordcount: '365'
ht-degree: 0%
---
# ACSD-63182: Fehler beim Speichern eines Produkts nach der Duplizierung eines Bundles

Mit dem Patch ACSD-63182 wird das Problem behoben, dass ein einfaches Produkt, das als Bundle-Option verwendet wird, nach der Duplizierung des Bundles nicht gespeichert werden konnte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63182. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Speichern eines einfachen Produkts, das als Bundle-Option verwendet wird, nach dem Duplizieren des Bundle-Produkts tritt ein Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue MSI-Quelle und einen neuen Stock.
1. Erstellen Sie zwei einfache Produkte: **p1** und **p2**.
1. Erstellen Sie ein Bundle-Produkt **b1** mit **p1** und **p2** als gebündelte Optionen.
1. Bearbeiten Sie das **Bundle Produkt b1** und klicken Sie auf ***[!UICONTROL Save and Duplicate]***.
1. Bearbeiten Sie die **einfache Produkt-P1** und klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird angezeigt:
*Ausnahme: Element (Magento\Catalog\Model\Product\Interceptor) mit derselben ID „XXX“ ist bereits vorhanden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
