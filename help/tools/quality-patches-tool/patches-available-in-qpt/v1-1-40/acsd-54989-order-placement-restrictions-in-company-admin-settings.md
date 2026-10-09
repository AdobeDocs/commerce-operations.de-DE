---
title: 'ACSD-54989: Der Unternehmensadministrator kann nicht bestellen, wenn [!UICONTROL Enable Purchase Orders] auf „Ja“ und [!UICONTROL Purchase Order] auf „Nein“ gesetzt ist'
description: Wenden Sie den Patch ACSD-54989 an, um das Adobe Commerce-Problem zu beheben, bei dem der Unternehmensadministrator keine Bestellungen aufgeben kann, wenn [!UICONTROL Enable Purchase Orders] auf „Ja“ und [!UICONTROL Purchase Order] auf „Nein“ gesetzt ist.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '413'
ht-degree: 0%
---
# ACSD-54989: Der Unternehmensadministrator kann nicht bestellen, wenn *[!UICONTROL Enable Purchase Orders]* auf *Ja* und *[!UICONTROL Purchase Order]* auf *Nein* eingestellt ist

Der Patch ACSD-54989 behebt das Problem, dass Bestellungen nicht aufgegeben werden können, wenn **[!UICONTROL Enable Purchase Orders]** auf *Ja* und **[!UICONTROL Purchase Order]** auf *Nein* eingestellt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54989. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Firmenadministratoren können keine Bestellungen aufgeben, wenn **[!UICONTROL Enable Purchase Orders]** auf *Ja* und **Bestellung** auf *Nein* eingestellt ist.

<u>Voraussetzungen</u>:

Installieren Sie [!DNL B2B] Module.

<u>Schritte zur Reproduktion</u>:

1. Firma aktivieren und [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Nein* verlassen.
1. Erstellen Sie ein einfaches Produkt mit einem Preis von 100.
1. Erstellen Sie über den Administrator eine neue Firma.
1. Legen Sie [!UICONTROL **Bestellungen aktivieren**] auf *Ja* fest.
1. Melden Sie sich als Unternehmensadministrator in der Storefront an.
1. Fügen Sie das erstellte einfache Produkt zum Warenkorb hinzu.
1. Wechseln Sie zur Kasse und klicken Sie auf **[!UICONTROL Place Order]** , um den Kauf abzuschließen.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung erfolgreich aufgeben.

<u>Tatsächliche Ergebnisse</u>:

Die **[!UICONTROL My Account]** wird geöffnet und die Bestellung wird nicht aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
