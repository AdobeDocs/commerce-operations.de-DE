---
title: 'ACSD-48216: *AUTO_INCREMENT der Tabelle inventory_source_item* erhöht sich bei *UPDATE*-Vorgang'
description: Wenden Sie den Patch ACSD-48216 an, um das Adobe Commerce-Problem zu beheben, bei dem *AUTO_INCREMENT der Tabelle inventory_source_item* beim Vorgang *UPDATE* zunimmt.
feature: Admin Workspace, Inventory, Orders
role: Admin
exl-id: acb956c8-75d4-4764-8b8d-250bc8620b29
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-48216: *AUTO_INCREMENT* der Tabelle *inventory_source_item* erhöht sich beim Vorgang *UPDATE*

Der Patch ACSD-48216 behebt das Problem, dass *AUTO_INCREMENT* der Tabelle *inventory_source_item* beim Vorgang *UPDATE* zunimmt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-48216. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`AUTO_INCREMENT` der `inventory_source_item` Tabelle erhöht sich beim `UPDATE`-Vorgang.

<u>Zu reproduzierende Schritte</u>:

1. Überprüfen Sie den aktuellen Wert von `AUTO_INCREMENT` der Tabelle `inventory_source_item`:

```bash
MySQL > show create table inventory_source_item;
```

```SQL
CREATE TABLE `inventory_source_item` (
  `source_item_id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `source_code` varchar(255) NOT NULL,
  `sku` varchar(64) NOT NULL,
  `quantity` decimal(12,4) NOT NULL DEFAULT '0.0000',
  `status` smallint(5) unsigned NOT NULL DEFAULT '0',
  PRIMARY KEY (`source_item_id`),
  UNIQUE KEY `INVENTORY_SOURCE_ITEM_SOURCE_CODE_SKU` (`source_code`,`sku`),
  KEY `INVENTORY_SOURCE_ITEM_SKU_SOURCE_CODE_QUANTITY` (`sku`,`source_code`,`quantity`),
  CONSTRAINT `INVENTORY_SOURCE_ITEM_SOURCE_CODE_INVENTORY_SOURCE_SOURCE_CODE` FOREIGN KEY (`source_code`) REFERENCES `inventory_source` (`source_code`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=2048 DEFAULT CHARSET=utf8
```

1. Stellen Sie eine API-Anfrage für ein bestimmtes Produkt:

`Endpoint: /rest/V1/inventory/source-items`\
`Method: POST`\
`Headers: Authorization: Bearer <admin_token>`

Nutzlast:

```JSON
{
    "sourceItems": [
        {
            "sku": "24-MB01",
            "source_code": "default",
            "quantity": 200,
            "status": 1
        }
    ]
}
```

1. Überprüfen Sie erneut den `AUTO_INCREMENT` -Wert der `inventory_source_item` -Tabelle.

<u>Erwartete Ergebnisse</u>:

Der `AUTO_INCREMENT` -Wert der `inventory_source_item`-Tabelle wird nach jedem Aktualisierungsvorgang nicht erhöht.

<u>Tatsächliche Ergebnisse</u>:

Der `AUTO_INCREMENT` -Wert der `inventory_source_item`-Tabelle erhöht sich nach jedem Aktualisierungsvorgang.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
