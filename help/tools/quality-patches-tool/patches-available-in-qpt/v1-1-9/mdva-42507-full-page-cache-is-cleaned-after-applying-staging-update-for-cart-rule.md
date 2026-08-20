---
title: 'MDVA-42507: Der Vollseiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt'
description: Der Patch MDVA-42507 löst das Problem, dass der Vollseiten-Cache nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42507. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
exl-id: 19f61e31-67da-4bd6-bce7-a9250f3946c7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-42507: Der Vollseiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt

Der Patch MDVA-42507 löst das Problem, dass der Vollseiten-Cache nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42507. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der vollständige Seiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie den Entwicklermodus.
1. Öffnen Sie mehrere Produkt- und Kategorieseiten und überprüfen Sie (über Kopfzeilen), ob sie aus dem Cache geladen werden.
1. Wenden Sie eine beliebige Staging-Aktualisierung für die Warenkorbregel an.
1. Überprüfen Sie, ob die Kategorie- und Produktseiten weiterhin aus dem Cache geladen werden.

<u>Erwartete Ergebnisse</u>:

Der vollständige Seiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel NICHT bereinigt.

<u>Tatsächliche Ergebnisse</u>:

Der vollständige Seiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
