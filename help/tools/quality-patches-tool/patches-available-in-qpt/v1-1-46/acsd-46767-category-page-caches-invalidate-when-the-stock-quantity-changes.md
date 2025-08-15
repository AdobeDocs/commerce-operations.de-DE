---
title: 'ACSD-46767: [!UICONTROL Category] Seiten-Caches werden ungültig, wenn sich die Lagermenge ändert'
description: Wenden Sie den Patch ACSD-46767 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Category]-Caches ungültig werden, wenn sich die Lagermenge ändert, auch wenn das Produkt noch auf Lager ist.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 5872dca7-fdef-47ad-8718-bf343cd3a42a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] Seiten-Caches werden ungültig, wenn sich die Lagermenge ändert

Mit dem Patch ACSD-46767 wird das Problem behoben, dass die [!UICONTROL Category]-Caches ungültig werden, wenn sich die Lagermenge ändert, auch wenn das Produkt noch auf Lager ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 installiert ist. Die Patch-ID ist ACSD-46767. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!UICONTROL Category] Seiten-Caches werden ungültig, wenn sich die Lagermenge ändert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Produkte und fügen Sie sie derselben Kategorie hinzu.
1. Öffnen Sie die *[!UICONTROL Category]* Seite in der Storefront, um sicherzustellen, dass die Seite zwischengespeichert wird.
1. Bestellung mit einem der Produkte aus der Kategorie *(Produktmenge wird geändert, aber Produkt ist noch auf Lager)*.
1. Öffnen Sie die [!UICONTROL Category]-Seite in der Storefront erneut.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird nicht aus dem Cache geladen. Er wird neu generiert.

<u>Erwartete Ergebnisse</u>:

Die Seite wird aus dem Cache geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
