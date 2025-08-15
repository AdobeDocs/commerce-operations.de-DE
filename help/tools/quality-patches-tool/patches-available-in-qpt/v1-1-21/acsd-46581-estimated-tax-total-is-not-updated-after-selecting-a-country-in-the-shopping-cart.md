---
title: 'ACSD-46581: Die geschätzte Steuersumme wird nach Auswahl eines Landes im Warenkorb nicht aktualisiert'
description: Wenden Sie den ACSD-46581 Patch an, um das Adobe Commerce-Problem zu lösen, bei dem der Steuersatz nach einem Wechsel des Landes im Warenkorb nicht aktualisiert wird.
feature: Orders, Shopping Cart
role: Admin
exl-id: 45800055-8556-4f87-8938-c6be5d82938d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-46581: Die geschätzte Steuersumme wird nach Auswahl eines Landes im Warenkorb nicht aktualisiert

Dieser Patch von ACSD-46581 löst das Problem, dass der Steuersatz nach einem Wechsel des Landes im Warenkorb nicht aktualisiert wird. Sie wird erst nach Auswahl der Versandmethode aktualisiert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46581. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Steuersatz wird nicht aktualisiert, nachdem das Land im Warenkorb gewechselt wurde.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie in Adobe Commerce Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Erstellen Sie einen neuen Steuersatz für **[!UICONTROL Country]** = _Vereinigte Staaten_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Erstellen Sie einen neuen Steuersatz für **[!UICONTROL Country]** = _Indien_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Erstellen Sie eine Steuerregel mit Steuersätzen für die USA und Indien.
1. Navigieren Sie zu **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** und aktivieren Sie mehr als eine Versandmethode (_z. B._ und _Kostenloser Versand_).
1. Erstellen Sie ein einfaches Produkt mit der **[!UICONTROL Taxable Goods]** Steuerklasse.
1. Fügen Sie das Produkt dem Warenkorb auf der Storefront hinzu.
1. Öffnen Sie den Warenkorb und überprüfen Sie den Steuerbetrag.
1. Es werden die standardmäßigen Steuereinstellungen für die Vereinigten Staaten angewendet und die Steuer wird auf der Grundlage eines Steuersatzes von 8,25 % berechnet.
1. Wechselt das Land nach Indien.

<u>Erwartete Ergebnisse</u>:

Der Steuerbetrag änderte sich auf 10 %, als das Land nach Indien wechselte.

<u>Tatsächliche Ergebnisse</u>:

Der Steuerbetrag bleibt im Gesamtabschnitt des Warenkorbs gleich.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
