---
title: 'MDVA-42969: Die Regel für verwandte Produkte funktioniert nur, wenn das Kundensegment auf „Alle“ festgelegt ist'
description: Mit dem Patch MDVA-42969 wird das Problem behoben, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf „Alle“ festgelegt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969: Die Regel für verwandte Produkte funktioniert nur, wenn das Kundensegment auf „Alle“ festgelegt ist

Mit dem Patch MDVA-42969 wird das Problem behoben, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf „Alle“ festgelegt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf „Alle“ festgelegt ist.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie **Stores** > **Konfiguration** > **Katalog** > **Regelbasierte Produktbeziehungen** und **Zugehörige Produkte anzeigen** = **Nur regelbasierte**.
1. Gehen Sie zu **Kunden** > **Segmente** und erstellen Sie ein neues Segment: **Anwenden auf** = **Besucher und registrierte Kunden**.
1. Gehen Sie zu **Marketing** > **Zugehörige Produktregeln** und erstellen Sie eine neue Regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öffnen Sie das entsprechende Produkt in der Storefront und überprüfen Sie, ob die anzuzeigenden Produkte angezeigt werden.
1. Ändern Sie die in Schritt 3 erstellte Regel und setzen Sie **Kundensegmente** = **spezifisch** > **Segment** aus Schritt 2.
1. Öffnen Sie das entsprechende Produkt in der Storefront.

<u>Erwartete Ergebnisse</u>:

Regelbasierte verwandte Produkte werden für Besucher auf dem Produkt in der Storefront angezeigt, da das Kundensegment mit der folgenden Konfiguration erstellt wird:

**Apply To** = **Besucher und registrierte Kunden**

<u>Tatsächliche Ergebnisse</u>:

Es werden keine verwandten Produkte angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
