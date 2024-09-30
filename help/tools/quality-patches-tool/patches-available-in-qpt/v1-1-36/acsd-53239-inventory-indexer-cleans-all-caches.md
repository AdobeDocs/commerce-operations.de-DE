---
title: "ACSD-53239: Inventarindexer löscht alle Caches"
description: Wenden Sie den Patch ACSD-53239 an, um das Adobe Commerce-Problem zu beheben, bei dem der Inventarindexer alle Caches im Modus [!UICONTROL Update on Schedule] löscht.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-53239: Der Inventarindexer löscht alle Caches im Modus [!UICONTROL Update on Schedule]

Der Patch ACSD-53239 behebt das Problem, bei dem der Inventarindexer alle Caches im Modus [!UICONTROL Update on Schedule] löscht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36 installiert ist. Die Patch-ID ist ACSD-53239. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Inventarindexer bereinigt alle Caches im Modus [!UICONTROL Update on Schedule] .

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** und wählen Sie ungefähr *1200* Produkte aus.
2. Aktualisieren Sie *[!UICONTROL Qty]* auf einen neuen Wert und klicken Sie auf **[!UICONTROL Save]**.
3. Führen Sie `bin/magento cron:run` unmittelbar nach dem Speichern aus.
4. Führen Sie die folgende GraphQL-Abfrage aus:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Erwartete Ergebnisse</u>

Die Abfrage wird innerhalb der üblichen Zeit verarbeitet.

<u>Tatsächliche Ergebnisse</u>

Die Abfrage wird ungewöhnlich langsam verarbeitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
