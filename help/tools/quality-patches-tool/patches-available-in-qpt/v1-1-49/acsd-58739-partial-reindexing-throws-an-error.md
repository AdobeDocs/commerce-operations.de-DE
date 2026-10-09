---
title: 'ACSD-58739: Bei der partiellen Neuindizierung wird ein Fehler ausgegeben'
description: Wenden Sie den Patch ACSD-55241 an, um das Adobe Commerce-Problem zu beheben, bei dem eine partielle Neuindizierung einen Fehler auslöst.
feature: Inventory, Products
role: Admin, Developer
exl-id: b4e6b8b4-43de-4434-94fb-6269a75e1c28
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%
---
# ACSD-58739: Bei der partiellen Neuindizierung wird ein Fehler ausgegeben

>[!NOTE]
>
>Dieser Patch wurde ersetzt durch [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md).

Der Patch ACSD-58739 behebt das Problem, dass die partielle Neuindizierung einen Fehler auslöst. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58739. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die partielle Neuindizierung gibt einen Fehler aus.

<u>Schritte zur Reproduktion</u>:

1. Slave-Verbindungseinstellungen zum `app/etc/env.php` hinzufügen.
1. Generieren Sie bis zu 10000 Produkte und führen Sie den folgenden Befehl aus:

   ```shell
   bin/magento index:reindex
   ```

1. Hinzufügen generierter Produkt-IDs in `catalogsearch_fulltext_cl` DB-Tabelle.

   ```sql
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. Führen Sie den folgenden Befehl aus, um die partielle Neuindizierung Trigger:

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. Überprüfen Sie die `var/log/support_report.log`.

<u>Erwartete Ergebnisse</u>

Kein Fehler.

<u>Tatsächliche Ergebnisse</u>:

*Basistabelle oder -ansicht nicht gefunden* tritt bei der Ausführung einer partiellen Neuindizierung ein Fehler auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
