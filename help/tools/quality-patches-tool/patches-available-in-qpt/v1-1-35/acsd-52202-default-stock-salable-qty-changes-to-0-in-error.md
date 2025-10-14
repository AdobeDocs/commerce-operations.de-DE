---
title: 'ACSD-52202: Die standardmäßige verkaufsfähige Lagermenge ändert sich irrtümlich auf 0, wenn die nicht standardmäßige Lagermenge in der richtigen Reihenfolge auf 0 gesetzt wird'
description: Wenden Sie den Patch ACSD-52202 an, um das Adobe Commerce-Problem zu beheben, bei dem sich eine standardmäßige Lagerverkaufsmenge irrtümlicherweise in 0 ändert, wenn der nicht standardmäßige Lagerbestand in einer Bestellung auf 0 Menge festgelegt ist.
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-52202: Die Standardlagermenge ändert sich irrtümlich auf 0, wenn eine nicht standardmäßige Lagermenge in einem Auftrag auf 0 gesetzt wird

Mit dem Patch ACSD-52202 wird das Problem behoben, dass eine standardmäßige Lagerverkaufsmenge (Menge) irrtümlich auf 0 geändert wird, wenn die nicht standardmäßige Lagermenge in einer Bestellung auf 0 Menge eingestellt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52202. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Standardlagerverkaufsmenge ändert sich irrtümlich auf 0, wenn eine nicht standardmäßige Lagermenge in einem Auftrag auf 0 Menge eingestellt ist.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim [!DNL Admin] an.
1. Erstellen Sie **website2**.
1. Erstellen Sie benutzerdefiniertes **source2**.
1. Erstellen Sie benutzerdefiniertes **stock2**.
1. Weisen Sie **source2** und **stock2** der **website1** und die Standardquelle und den Standardbestand der Standardwebsite zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie **qty** = *10* für die Standardquelle und **qty** = *1* für die **source2** Quelle zu.
1. Bestellung mit **qty** = *1* für **website2**.
1. Erstellen Sie eine Rechnung und eine Lieferung.
1. Überprüfen Sie das einfache Produkt **verkaufsfähige Menge**.

<u>Erwartete Ergebnisse</u>:

Die **verkaufbare Menge** = *10* für **source2**.

<u>Tatsächliche Ergebnisse</u>:

Die **verkaufbare Menge** = *0* für beide Quellen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
