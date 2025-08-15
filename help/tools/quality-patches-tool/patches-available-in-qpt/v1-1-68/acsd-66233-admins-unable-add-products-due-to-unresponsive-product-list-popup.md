---
title: 'ACSD-66233: Administratoren können keine Produkte hinzufügen, da das Popup in der Produktliste nicht reagiert'
description: Wenden Sie den Patch ACSD-66233 an, um das Adobe Commerce-Problem zu beheben, bei dem Admins keine Produkte zu Kategorien hinzufügen können, da das [!UICONTROL Add Product]-Popup in Visual Merchandiser unbegrenzt geladen wird.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
source-git-commit: a1241f709fc1b7128d1d267c54586c60dadab436
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-66233: Administratoren können keine Produkte hinzufügen, da das Popup in der Produktliste nicht reagiert

Mit dem Patch ACSD-66233 wird ein Problem behoben, bei dem Admins keine Produkte zu Kategorien hinzufügen können, da das [!UICONTROL Add Product]-Popup in Visual Merchandiser unbegrenzt geladen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66233. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Problem, bei dem das [!UICONTROL Add Product]-Popup in Visual Merchandiser unbegrenzt geladen wird, sodass Administratoren keine Produkte zu Kategorien hinzufügen können.

<u>Schritte zur Reproduktion</u>:

1. Installieren und aktivieren Sie die Inventar-Module.
1. Erstellen Sie eine große Anzahl von Inventarquellen (z. B. 700).
1. Erstellen Sie mehrere Lagerbestände (z. B. 12) und weisen Sie ihnen die Lagerquellen zu.
1. Erstellen Sie einige Produkte und weisen Sie sie den Inventarquellen zu.
1. Erstellen Sie eine Kategorie.
1. Erweitern Sie den Abschnitt [!UICONTROL Products in Category] .
1. Klicken Sie auf die Schaltfläche [!UICONTROL Add Product] .
1. Sehen Sie sich das Popup-Fenster mit der Liste der Produkte an.

<u>Erwartete Ergebnisse</u>:

Die Produktliste wird innerhalb einer angemessenen Zeit im Popup-Fenster geladen.

<u>Tatsächliche Ergebnisse</u>:

Das Popup wird unbegrenzt geladen und zeigt die Produktliste nicht an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
