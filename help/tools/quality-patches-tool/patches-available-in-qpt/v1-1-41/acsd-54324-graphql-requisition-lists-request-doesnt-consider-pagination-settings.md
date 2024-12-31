---
title: 'ACSD-54324: Die Anfrage "GraphQL requisition_lists“ berücksichtigt keine Paginierungseinstellungen'
description: Wenden Sie den Patch „ACSD-54324“ an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Anfrage „requirement_lists“ die Paginierungseinstellungen nicht berücksichtigt und alle Ergebnisse zurückgibt.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-54324: Die GraphQL-`requisition_lists` berücksichtigt keine Paginierungseinstellungen

Mit dem Patch „ACSD-54324“ wird das Problem behoben, dass die GraphQL-`requisition_lists`-Anfrage die Paginierungseinstellungen nicht berücksichtigt und alle Ergebnisse zurückgibt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.41 installiert ist. Die Patch-ID ist ACSD-54324. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL `requisition_lists`-Anfrage berücksichtigt keine Paginierungseinstellungen und gibt alle Ergebnisse zurück.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin an und navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Setzen Sie *[!UICONTROL Enable Requisition List]* auf *Ja*.

1. Melden Sie sich beim Frontend an und gehen Sie über das obere Menü oder über **[!UICONTROL My Account]** zu **[!UICONTROL My Requisition Lists]** und erstellen Sie mehrere Anforderungen (Beispiel: 7).
1. Nachdem Sie ein Kunden-Token generiert haben, führen Sie die folgende GraphQL-`requisition_lists`-Abfrage für den Kunden aus.

   * Stellen Sie sicher, dass die Seitengröße kleiner ist als die Gesamtzahl der von Ihnen erstellten Anforderungslisten (Beispiel: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Beachten Sie, dass der Wert des `total_count` Felds 7 anzeigt, obwohl es 4 anzeigen sollte.

   Die Anzahl der Elemente zeigt auch 7 an, wenn es mit der *Seitengröße* übereinstimmen sollte.

<u>Erwartete Ergebnisse</u>:

* Die als *Seitengröße“ aufgelistete* wird unter `total_count` zurückgegeben und nicht die Gesamtzahl der Datensätze.
* Die Anzahl der Elemente entspricht der *Seitengröße*.

<u>Tatsächliche Ergebnisse</u>:

Die Gesamtzahl der Datensätze wird unter `total_count` zurückgegeben, auch wenn *Seitengröße* angegeben wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
