---
title: 'ACSD-63323: Löst [!UICONTROL Select All] Funktionalität auf und verbessert die Paginierung und Anzahl der Einträge im Produktkategorien-Popup'
description: Wenden Sie den Patch ACSD-63323 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option [!UICONTROL Select All] nicht funktioniert, wenn Produkte zu einer Kategorie hinzugefügt werden. Darüber hinaus wird sichergestellt, dass die Paginierung und die Beschriftung der Datensatzanzahl korrekt funktionieren, wenn Produkte über das Popup-Raster zu einer Kategorie hinzugefügt werden.
feature: Products
role: Admin, Developer
source-git-commit: f3f0cc93adf83b485ca50811adcc561638e3c5c2
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-63323: Löst [!UICONTROL Select All] Funktionalität auf und verbessert die Paginierung und Anzahl der Einträge im Produktkategorien-Popup

Mit dem Patch ACSD-63323 wird das Problem behoben, dass die Option **[!UICONTROL Select All]** beim Hinzufügen von Produkten zu einer Kategorie nicht funktioniert. Darüber hinaus wird sichergestellt, dass die Paginierung und die Beschriftung der Datensatzanzahl korrekt funktionieren, wenn Produkte über das Popup-Raster zu einer Kategorie hinzugefügt werden. Dieser Patch ist verfügbar, wenn die [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) installiert ist. Die Patch-ID ist ACSD-63323. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es wurde ein Problem behoben, bei dem die Option **[!UICONTROL Select All]** unter Admin > **[!UICONTROL Categories]** > Kategorie auswählen > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]** nicht funktionierte. Dies hilft auch bei der Paginierung und der ordnungsgemäßen Funktionsweise des Titels „Anzahl der Einträge“, wenn Produkte über das Popup-Raster zu einer Kategorie hinzugefügt werden.


<u>Schritte zur Reproduktion</u>:

1. Generieren Sie *1200*-Produkte mit dem Befehl :

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Öffnen Sie **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und sehen Sie die Anzahl der Produkte: *1200* Datensätze gefunden.
1. Öffnen Sie eine Standardkategorie > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**.
1. Klicken Sie auf **[!UICONTROL Assign]** > **[!UICONTROL Select All]**.
1. Ändern Sie die Anzahl der Produkte auf der Seite in den Wert = *5*.


**Erwartete Ergebnisse**:

*Die Nachricht sollte wie folgt lauten: 1200 Datensätze gefunden (1200 ausgewählt)*

**Tatsächliche Ergebnisse**:

* Paginierung funktioniert nicht.
* Die falsche Meldung wird angezeigt: *5* Datensätze gefunden (*20* ausgewählt)

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.


