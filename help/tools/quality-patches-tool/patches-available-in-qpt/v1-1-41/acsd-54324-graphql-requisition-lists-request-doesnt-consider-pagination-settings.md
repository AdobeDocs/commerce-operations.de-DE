---
title: '"ACSD-54324: GraphQL-Anfrage "Requisition_lists"berücksichtigt keine Paginierungseinstellungen."'
description: Wenden Sie den Patch ACSD-54324 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Anfrage "Requisition_lists"keine Paginierungseinstellungen berücksichtigt und alle Ergebnisse zurückgibt.
feature: B2B, Customers, GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists`-Anfrage berücksichtigt keine Paginierungseinstellungen

Der Patch ACSD-54324 behebt das Problem, dass bei der GraphQL `requisition_lists` -Anfrage keine Paginierungseinstellungen berücksichtigt werden und alle Ergebnisse zurückgegeben werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.41 installiert ist. Die Patch-ID ist ACSD-54324. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL `requisition_lists` -Anfrage berücksichtigt keine Paginierungseinstellungen und gibt alle Ergebnisse zurück.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an und navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Setzen Sie *[!UICONTROL Enable Requisition List]* auf *Ja*.

1. Melden Sie sich beim Frontend an, wechseln Sie vom oberen Menü oder von **[!UICONTROL My Account]** zu **[!UICONTROL My Requisition Lists]** und erstellen Sie mehrere Anforderungen (Beispiel: 7).
1. Führen Sie nach dem Generieren eines Kunden-Tokens die folgende GraphQL `requisition_lists`-Abfrage für den Kunden aus.

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

1. Beachten Sie, dass der Wert des Felds `total_count` 7 anzeigt, wenn 4 angezeigt werden soll.

   Die Anzahl der Elemente zeigt auch 7 an, wenn sie mit der *Seitengröße* übereinstimmen sollte.

<u>Erwartete Ergebnisse</u>:

* Die Zahl, die als *Seitengröße* aufgeführt ist, wird unter `total_count` und nicht unter der Gesamtzahl der Datensätze zurückgegeben.
* Die Anzahl der Elemente entspricht der *Seitengröße*.

<u>Tatsächliche Ergebnisse</u>:

Die Gesamtzahl der Datensätze wird unter `total_count` zurückgegeben, selbst wenn *Seitengröße* angegeben ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
