---
title: 'MDVA-41139: Konfigurierbares Produkt wird nach dem Produktimport nicht mehr vorrätig'
description: Mit dem Patch MDVA-41139 wird das Problem behoben, dass das konfigurierbare Produkt nach dem Produktimport nicht mehr vorrätig ist, wenn die Menge des einfachen Produkts für eine seiner Quellen = 0 ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-41139. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
exl-id: 7366230c-3b7f-4211-9f0d-55a528dffdbd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41139: Konfigurierbares Produkt wird nach dem Produktimport nicht mehr vorrätig

Mit dem Patch MDVA-41139 wird das Problem behoben, dass das konfigurierbare Produkt nach dem Produktimport nicht mehr vorrätig ist, wenn die Menge des einfachen Produkts für eine seiner Quellen = 0 ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-41139. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das konfigurierbare Produkt ist nach dem Produktimport nicht mehr vorrätig, wenn die Menge des einfachen Produkts für eine seiner Quellen = 0 ist.

<u>Voraussetzungen</u>:

Inventarmodule sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Quelle und einen neuen Lagerbestand.
1. Erstellen Sie ein konfigurierbares Produkt mit untergeordneten Produkten, die der Standardquelle und der neuen Quelle zugewiesen sind.
1. Legen Sie den Wert des standardmäßigen Lagers für jedes untergeordnete Produkt auf 0 und für andere Lager auf 0 fest.
1. Das konfigurierbare Produkt ist vorrätig.
1. Dieses Produkt exportieren und erneut importieren.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt ist auf Lager, da die zweite Quelle eine Menge von > 0 hat.

<u>Tatsächliche Ergebnisse</u>:

Das konfigurierbare Produkt ist nicht vorrätig.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
