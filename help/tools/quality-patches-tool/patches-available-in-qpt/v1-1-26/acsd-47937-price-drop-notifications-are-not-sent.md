---
title: 'ACSD-47937: Preisabfallbenachrichtigungen werden aufgrund von Caching auf Anwendungsebene nicht gesendet'
description: Wenden Sie den Patch ACSD-47937 an, um das Adobe Commerce-Problem zu beheben, bei dem aufgrund des Caching auf Anwendungsebene nicht immer Preisabfallbenachrichtigungen gesendet werden.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: Preisabfallbenachrichtigungen werden aufgrund von Caching auf Anwendungsebene nicht gesendet

Mit dem Patch ACSD-47937 wird das Problem behoben, dass aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabfallbenachrichtigungen gesendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-47937. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 und 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.5 und 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kunden erhalten keine E-Mail zu Produktpreisrückgängen für nachfolgende Produktpreisänderungen.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL Product Alert]** für *[!UICONTROL Price Changes]* und *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. **[!UICONTROL Display Out of Stock Products]** aktivieren.
1. Einfaches Produkt (ABC) mit Menge = 0 erstellen.
1. Erstellen Sie eine Kundin oder einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Produktbenachrichtigungen für Preisrückgänge zu erhalten.
1. Starten Sie den Warnhinweis für Kunden.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Senken Sie den Preis für das ABC-Produkt.
1. Trigger des Warnhinweiscron des Produkts.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Senken Sie den Preis für das ABC-Produkt erneut.
1. Trigger des Warnhinweiscron des Produkts.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Wenn Sie mit [!DNL n98] Tool nicht vertraut sind, können Sie `bin/magento cron:run command` wie gewohnt ausführen und `cron_schedule` Tabelle überwachen, um sicherzustellen, dass `catalog_product_alert` Auftrag den Status „Erfolg“ erhält.

<u>Erwartete Ergebnisse</u>:

Die zweite Preis-Dropdown-E-Mail wird gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die zweite Preis-Dropdown-E-Mail wird nicht gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
