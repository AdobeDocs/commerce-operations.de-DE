---
title: 'ACSD-47937: aufgrund von Caching auf Anwendungsebene nicht gesendete Preisabsturzbenachrichtigungen'
description: Wenden Sie den Patch ACSD-47937 an, um das Adobe Commerce-Problem zu beheben, bei dem aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabbruchbenachrichtigungen gesendet werden.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: aufgrund von Caching auf Anwendungsebene nicht gesendete Preisabsturzbenachrichtigungen

Der Patch ACSD-47937 behebt das Problem, dass aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabbruchbenachrichtigungen gesendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-47937. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 und 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.5 und 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden erhalten keine E-Mail zum Produktpreisverfall für nachfolgende Produktpreisänderungen.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL Product Alert]** sowohl für *[!UICONTROL Price Changes]* als auch für *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Aktivieren Sie **[!UICONTROL Display Out of Stock Products]**.
1. Erstellen Sie ein einfaches Produkt (ABC) mit qty = 0.
1. Erstellen Sie einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Produktwarnungen für Preisrückgänge zu erhalten.
1. Starten Sie die Produktwarnung für Kunden.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Legen Sie den Preis für das ABC-Produkt ab.
1. Trigger des Produkt-Warnhinweis-Crons.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Legen Sie den Preis für das ABC-Produkt erneut ab.
1. Trigger des Produkt-Warnhinweis-Crons.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Wenn Sie nicht mit dem [!DNL n98]-Tool vertraut sind, können Sie `bin/magento cron:run command` wie gewohnt ausführen und die `cron_schedule`-Tabelle überwachen, um sicherzustellen, dass `catalog_product_alert` Auftrag den Erfolgsstatus erhält.

<u>Erwartete Ergebnisse</u>:

Die zweite Preissenkungs-E-Mail wird gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die zweite Preissenkungs-E-Mail wird nicht gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
