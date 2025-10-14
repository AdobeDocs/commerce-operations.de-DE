---
title: 'ACSD-67264: Layout von Bundles und herunterladbaren Produktseiten ist auf allen Geräten inkonsistent'
description: Wenden Sie den ACSD-67264-Patch an, um das Adobe Commerce-Bundle und herunterladbare Seiten zu beheben, bei denen Layout-Probleme aufgrund einer Neuanordnung des Produktinformations-Medienblocks aufgetreten sind.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: Layout von Bundles und herunterladbaren Produktseiten ist auf allen Geräten inkonsistent

Mit dem Patch ACSD-67264 wird das Problem behoben, dass die Layouts von Bundles und herunterladbaren Produktseiten auf allen Geräten inkonsistent sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-67264. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei Bundle- und herunterladbaren Produktseiten traten Layout-Probleme aufgrund einer Neuanordnung des Produktinfo-Medienblocks auf.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie die Beispieldaten.
1. Öffnen Sie die Bundle-Produktseite und überprüfen Sie das Layout auf dem Desktop.
1. Fügen Sie die Bundle-Produktseite zur Wunschliste hinzu, navigieren Sie zur Wunschliste, klicken Sie auf das Bearbeitungssymbol und überprüfen Sie das Layout.
1. Wiederholen Sie die Schritte 2 und 3 für ein herunterladbares Produkt.

<u>Erwartete Ergebnisse</u>:

Die Bundle-Produkt-PDP wird ohne Probleme gerendert.

<u>Tatsächliche Ergebnisse</u>:

Die Bundle-Produkt-PDP wird mit zufälligen Leerzeichen gerendert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
