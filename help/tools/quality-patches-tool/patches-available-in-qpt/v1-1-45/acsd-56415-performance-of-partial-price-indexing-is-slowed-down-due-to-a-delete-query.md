---
title: '"ACSD-56415: Leistung von [!UICONTROL Partial Price Indexing] aufgrund der Abfrage "DELETE" verlangsamt.'
description: Wenden Sie den Patch ACSD-56415 an, um das Adobe Commerce-Problem zu beheben, bei dem die Performance von [!UICONTROL Partial Price Indexing] aufgrund einer "DELETE"-Abfrage verlangsamt wird, wenn die Datenbank über viele partielle Preisdaten zu indizieren hat.
feature: Catalog Service
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56415: Die Leistung von [!UICONTROL Partial Price Indexing] wird aufgrund der `DELETE`-Abfrage verlangsamt

Der Patch ACSD-56415 behebt das Problem, bei dem die Leistung von [!UICONTROL Partial Price Indexing] aufgrund einer `DELETE` -Abfrage verlangsamt wird, wenn die Datenbank über einen großen Teil des Preisdatenindex verfügt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56023. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Leistung von [!UICONTROL Partial Price Indexing] wird aufgrund einer `DELETE` -Abfrage verlangsamt, wenn die Datenbank über einen großen Teil des Preisdatenindex verfügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie *300000 Produkte* und *10 Websites* mit dem großen Leistungsprofil.
1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie *10 Kundengruppen*.
1. Führen Sie die folgende Abfrage aus, um Produkte zur Tabelle `_cl` hinzuzufügen:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Führen Sie den folgenden Befehl aus, um die partielle Preisindizierung Trigger:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Erwartete Ergebnisse</u>:

Das SQL-Abfrage-DELETE `main_table` FROM `catalog_product_index_price` wird schnell ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

Das SQL-Abfrage-DELETE `main_table` FROM `catalog_product_index_price` wird sehr langsam ausgeführt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
