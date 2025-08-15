---
title: 'MDVA-39181: Zugehörige Produktregeln zeigen Produkte aus der Kategorie in der Regel nicht definiert an'
description: Der Patch MDVA-39181 löst das Problem, dass verwandte Produktregeln Produkte aus einer Kategorie anzeigen, die in der Regel nicht definiert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-39181. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181: Zugehörige Produktregeln zeigen Produkte aus der Kategorie in der Regel nicht definiert an

Der Patch MDVA-39181 löst das Problem, dass verwandte Produktregeln Produkte aus einer Kategorie anzeigen, die in der Regel nicht definiert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-39181. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Verwandte Produktregeln zeigen Produkte aus Kategorien an, die in der Regel nicht definiert sind.

<u>Voraussetzungen</u>:

Installieren von Beispieldaten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Attributmarke und fügen Sie sie zum &quot;**-Attributsatz“**.
1. Wählen Sie **Josie**, **Augusta** und **Ingrid** Jacken, die Sie der Marke Kitty aus der Kategorie **Damen** > **Tops** > **jacken hinzufügen**.
1. Wählen Sie **Beaumont**, **Hyperion** und **Kenobi** Jacken, die Sie der Marke Kitty aus **Men** > **Tops** > **Jackenkategorie**.
1. Erstellen eines zugehörigen Produkts mit:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Passende Produkte:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Anzuzeigende Produkte:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Öffnen Sie SKU WJ04 vom Frontend und überprüfen Sie die zugehörigen Produkte.
1. Aktualisieren Sie die Kategorie-ID von **Damen** > **Oberteile** > **Jackets**, falls sie sich von dieser unterscheidet.

<u>Erwartete Ergebnisse</u>:

Nur Produkte derselben Marke und derselben untergeordneten Kategorie werden in verwandten Produkten angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Verwandte Produkte werden von derselben Marke, aber von einer zufälligen übergeordneten Kategorie angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
