---
title: 'ACSD-64149: Kundensegment mit einer [!UICONTROL Date range] Bedingung kann gespeichert werden, wenn nur ein Datum bearbeitet wird'
description: Wenden Sie den Patch ACSD-64149 an, um das Adobe Commerce-Problem zu beheben, bei dem Kundensegmente mit einer **[!UICONTROL Date range]**-Bedingung gespeichert werden können, wenn nur eines der Daten bearbeitet wird.
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-64149: Kundensegment mit einer [!UICONTROL Date range] Bedingung kann gespeichert werden, wenn nur ein Datum bearbeitet wird

Mit dem Patch ACSD-64149 wird das Problem behoben, dass ein Kundensegment mit einer Bedingung für den Datumsbereich gespeichert werden kann, wenn nur eines der Daten bearbeitet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 installiert ist. Die Patch-ID ist ACSD-64149. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Bearbeiten eines bestehenden Kundensegments mit einer Bedingung für Produkte innerhalb des Warenkorbs, die durch einen Datumsbereich angegeben wird, schlägt die `matchCustomerSegmentProcessor` mit einem SQL-Fehler fehl.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass die `matchCustomerSegmentProcessor` ausgeführt wird:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Gehen Sie zum **[!UICONTROL Magento backend]**.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Klicken Sie auf **[!UICONTROL Add Segment]**.
1. Geben Sie einen **[!UICONTROL Segment Name]** ein, wählen Sie eine Website unter **[!UICONTROL Assigned to Website]** aus und stellen Sie sicher, dass die **[!UICONTROL Status]** auf *Aktiv* eingestellt ist.
1. Klicken Sie auf **[!UICONTROL Save and Continue Edit]**.
1. Wechseln Sie zur Registerkarte &quot;**[!UICONTROL Conditions]**&quot; und fügen Sie eine neue Bedingung hinzu: *Produkte{} > {}Produktliste*{*}*.
1. Fügen Sie eine Unterbedingung für die **[!UICONTROL Date range]** hinzu und legen Sie eine gültige **[!UICONTROL Date range]** fest.
1. Klicken Sie auf die grüne Bestätigungsschaltfläche neben dem **[!UICONTROL Date range]**.
1. Klicken Sie erneut auf die **[!UICONTROL Date range]**, wählen Sie die Datumsauswahl aus, bearbeiten Sie einen der Datumswerte und bestätigen Sie den Vorgang, indem Sie auf die grüne Schaltfläche klicken.

<u>Erwartete Ergebnisse</u>:

Der **[!UICONTROL Date range]**-Selektor sollte beim Bearbeiten keine Zeit zum Datum hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

* Mit dem **[!UICONTROL Date range]**-Selektor wird dem Datum Zeit hinzugefügt:
   * Ein Datum enthält nur das Datum, während das andere sowohl das Datum als auch die Uhrzeit enthält.
* Der folgende Fehler wird in den Protokollen angezeigt:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
