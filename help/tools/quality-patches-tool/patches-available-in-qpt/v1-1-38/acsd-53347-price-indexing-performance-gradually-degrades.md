---
title: 'ACSD-53347: Die Preisindizierungsleistung verschlechtert sich mit der Zeit allmählich'
description: Wenden Sie den Patch ACSD-53347 an, um das Adobe Commerce-Problem zu beheben, bei dem die Leistung bei einer Neuindizierung der Preise für einen großen Produktkatalog allmählich nachlässt.
feature: Price Indexer
role: Admin
exl-id: 8986b685-55e4-47c7-852c-aca18e3b02e9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-53347: Die Preisindizierungsleistung verschlechtert sich mit der Zeit allmählich

Mit dem Patch ACSD-53347 wird das Problem behoben, dass die Leistung bei der Neuindizierung eines großen Produktkatalogs allmählich nachlässt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 installiert ist. Die Patch-ID ist ACSD-53347. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Preise für einen großen Produktkatalog neu indiziert werden, verschlechtert sich die Leistung der Abfragen, die während des Indizierungsprozesses ausgeführt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen großen einfachen Katalog und weisen Sie diesen Produkten benutzerdefinierte Optionen zu (benutzerdefinierte Optionen verwenden während der Indizierung eine temporäre Tabelle).
1. Erstellen Sie mindestens 200 oder mehr Kundengruppen, um das Problem besser bekannt zu machen.
1. Erstellen Sie zehn oder mehr Websites und weisen Sie jedem von ihnen alle Produkte zu.
1. Beachten Sie, dass die importierten Produkte nahezu identisch sind und sich nur nach SKU und Namen unterscheiden.
1. **[!UICONTROL DB Logging]** aktivieren.
1. Führen Sie den `bin/magento index:reindex catalog_product_price` Befehl aus.
1. Auf *DELETE VON`catalog_product_index_price_opt_agr_temp`* im `db.log` prüfen.

<u>Erwartete Ergebnisse</u>:

Die Ausführung der *DB-Abfragen* läuft effizient.

<u>Tatsächliche Ergebnisse</u>:

Die Leistung der *DB-Abfragen* auf temporären Tabellen wird im Laufe der Zeit langsam, daher dauert es sehr lange, bis die Preisindizierungstabelle abgeschlossen ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
