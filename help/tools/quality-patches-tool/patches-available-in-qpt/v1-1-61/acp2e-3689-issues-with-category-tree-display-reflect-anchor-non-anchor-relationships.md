---
title: 'ACP2E-3689: Mehrere Probleme mit der Anzeige der Kategoriestruktur auf tieferen Ebenen und mit Anker-/Nicht-Anker-Beziehungen'
description: Wenden Sie den Patch ACP2E-3689 an, um das Adobe Commerce-Problem mit der Kategoriestrukturanzeige in mehr als vier Verschachtelungen zu beheben und Anker-/Nicht-Anker-Beziehungen zu reflektieren.
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACP2E-3689: Mehrere Probleme mit der Anzeige der Kategoriestruktur auf tieferen Ebenen und mit Anker-/Nicht-Anker-Beziehungen

>[!NOTE]
>
>Dieser Patch ersetzt den [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) für die Versionen 2.4.7 und höher.

Der Patch ACP2E-3689 behebt mehrere Probleme mit der Anzeige der Kategoriestruktur in mehr als vier Verschachtelungen und reflektierenden Anker-/Nicht-Anker-Beziehungen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID lautet ACP2E-3689. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Kategoriestruktur auf tieferen Ebenen (4+) wird nicht korrekt angezeigt und spiegelt Anker-/Nicht-Anker-Beziehungen wider.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie eine Kategoriestruktur mit verschachtelten Kategorien mit mehr als vier Ebenen ein.
1. Erweitern Sie die Kategoriestruktur in Admin , die an verschiedenen Stellen angezeigt wird:
   1. Richten Sie eine [!UICONTROL Related Products Rule] ein und legen Sie eine Bedingung basierend auf Kategorien fest.
   1. Erstellen Sie ein Widget und wählen Sie in [!UICONTROL Layout Updates] [!UICONTROL Anchor categories] aus.

<u>Erwartete Ergebnisse</u>:

Alle Ebenen der Kategoriestruktur werden ordnungsgemäß angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Nur die ersten Ebenen (&lt;4) der Kategoriestruktur sind verfügbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
