---
title: 'ACSD-56415: Leistung der [!UICONTROL Partial Price Indexing] aufgrund der Abfrage "DELETE" verlangsamt'
description: Wenden Sie den Patch ACSD-56415 an, um das Adobe Commerce-Problem zu beheben, bei dem die Leistung der [!UICONTROL Partial Price Indexing] aufgrund einer "DELETE"-Abfrage verlangsamt wird, wenn die Datenbank viele partielle Preisdaten zu indizieren hat.
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4273989f-0bf2-5361-a17a-6909488d18ab
    internal-label: Catalog Service
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
source-wordcount: '414'
ht-degree: 0%
---
# ACSD-56415: Die [!UICONTROL Partial Price Indexing] ist aufgrund `DELETE` Abfrage verlangsamt

Mit dem Patch ACSD-56415 wird das Problem behoben, dass die Leistung der [!UICONTROL Partial Price Indexing] aufgrund einer `DELETE`-Abfrage verlangsamt wird, wenn die Datenbank viele partielle Preisdatenindizes hat. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56023. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Leistung von [!UICONTROL Partial Price Indexing] wird aufgrund einer `DELETE` Abfrage verlangsamt, wenn die Datenbank viele partielle Preisdatenindizes hat.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie *300000 Produkte* und *10-Websites* dem großen Leistungsprofil.
1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie *10 Kundengruppen*.
1. Führen Sie die folgende Abfrage aus, um Produkte zur `_cl`-Tabelle hinzuzufügen:

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. Führen Sie den folgenden Befehl aus, um den partiellen Preisindizierungsprozess Trigger:

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>Erwartete Ergebnisse</u>:

Die SQL-Abfrage DELETE `main_table` FROM `catalog_product_index_price` wird schnell ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

Die SQL-Abfrage DELETE `main_table` FROM `catalog_product_index_price` wird sehr langsam ausgeführt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
