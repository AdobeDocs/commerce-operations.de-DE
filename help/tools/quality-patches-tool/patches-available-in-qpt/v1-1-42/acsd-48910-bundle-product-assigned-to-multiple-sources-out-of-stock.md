---
title: 'ACSD-48910: Gebündeltes Produkt, dem mehrere Quellen zugewiesen sind, wird nach Rechnung und Versand nicht mehr vorrätig sein'
description: Wenden Sie den Patch ACSD-48910 an, um das Adobe Commerce-Problem zu beheben, bei dem das gebündelte Produkt, das mehreren Bezugsquellen zugewiesen ist, nach der Rechnungsstellung und dem Versand nicht mehr vorrätig ist, auch wenn es noch eine Menge ungleich null aufweist.
feature: Products, Inventory
role: Admin, Developer
exl-id: c8d86531-2db5-4115-92d5-a8d391c4f75d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-48910: Gebündeltes Produkt, dem mehrere Quellen zugewiesen sind, wird nach Rechnung und Versand nicht mehr vorrätig sein

Mit dem Patch ACSD-48910 wird das Problem behoben, dass das gebündelte Produkt, das mehreren Quellen zugeordnet ist, nach der Rechnungsstellung und dem Versand nicht mehr vorrätig ist, auch wenn es noch eine Menge ungleich null aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-48910. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das gebündelte Produkt, das mehreren Quellen zugewiesen wurde, ist nach der Rechnungsstellung und dem Versand nicht mehr vorrätig, auch wenn es noch verfügbar ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites.
1. Erstellen Sie zwei Stores/Store-Ansichten (einen pro Website).
1. Erstellen Sie zwei einfache Produkte (Menge = 10) und weisen Sie sie sowohl Lagern als auch Websites zu.
1. Erstellen Sie ein gebündeltes Produkt und fügen Sie ihm diese einfachen Produkte hinzu. Weisen Sie das gebündelte Produkt beiden Websites zu.
1. Gehen Sie zur Storefront und fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Checken Sie aus und geben Sie die Bestellung auf.
1. Rechnungen und versenden Sie die Bestellung über den Administrator.

<u>Erwartete Ergebnisse</u>:

Das gebündelte Produkt bleibt auf Lager, da wir nur 1 von 10 Artikeln gekauft haben.

<u>Tatsächliche Ergebnisse</u>:

Das gebündelte Produkt ändert seinen Status in „Nicht vorrätig“.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
