---
title: 'MDVA-42969: Zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf alle eingestellt ist'
description: Der Patch MDVA-42969 behebt das Problem, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf "Alle"gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969: Zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf alle eingestellt ist

Der Patch MDVA-42969 behebt das Problem, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf &quot;Alle&quot;gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf &quot;Alle&quot;festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > **Konfiguration** > **Katalog** > **Regelbasierte Produktbeziehungen** und legen Sie **Zugehörige Produkte anzeigen** = **Nur regelbasiert** fest.
1. Gehen Sie zu **Kunden** > **Segmente** und erstellen Sie ein neues Segment: **Anwenden auf** = **Besucher und registrierte Kunden**.
1. Gehen Sie zu **Marketing** > **Zugehörige Produktregeln** und erstellen Sie eine neue Regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öffnen Sie das entsprechende Produkt auf der Storefront und überprüfen Sie, ob die anzuzeigenden Produkte angezeigt werden.
1. Ändern Sie die in Schritt 3 erstellte Regel und legen Sie **Kundensegmente** = **Spezifische** > **Segment** in Schritt 2 fest.
1. Öffnen Sie das entsprechende Produkt auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Regelbasierte verwandte Produkte werden auf der Storefront für Besucher des Produkts angezeigt, da das Kundensegment mit der folgenden Konfiguration erstellt wird:

**Anwenden auf** = **Besucher und registrierte Kunden**

<u>Tatsächliche Ergebnisse</u>:

Es werden keine verwandten Produkte angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
