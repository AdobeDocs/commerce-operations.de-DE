---
title: 'ACSD-64732: Controller von Drittanbietern werden nicht korrekt mit Kundensegmenten zwischengespeichert'
description: Wenden Sie den Patch ACSD-64732 an, um das Adobe Commerce-Problem zu beheben, bei dem Controller von Drittanbietern nicht korrekt mit Kundensegmenten zwischengespeichert werden.
feature: Cache
role: Admin, Developer
source-git-commit: 047de42098f711036f1f5252d2cbc4a329ebbfb2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# ACSD-64732: Controller von Drittanbietern werden nicht korrekt mit Kundensegmenten zwischengespeichert

Mit dem Patch ACSD-64732 wird das Problem behoben, dass die Controller von Drittanbietern nicht korrekt mit Kundensegmenten zwischengespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 installiert ist. Die Patch-ID ist ACSD-64732. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Controller von Drittanbietern werden nicht korrekt mit Kundensegmenten zwischengespeichert.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum benutzerdefinierten Controller (/catalog/category/variation).
1. Wechseln Sie zur Registerkarte **[!UICONTROL Network]** und überprüfen Sie den Wert von **[!DNL X-Magento-Vary]**.

<u>Erwartete Ergebnisse</u>:

Der **[!UICONTROL X-Magento-Vary]** sollte für den benutzerdefinierten Controller gleich sein.

<u>Tatsächliche Ergebnisse</u>:

Der Wert von **[!UICONTROL X-Magento-Vary]** ist unterschiedlich, was zu Cache-Fehlern führt. Dies bedeutet, dass der zuvor generierte Cache beim Besuch des benutzerdefinierten Controllers nicht verwendet werden kann.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
