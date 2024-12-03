---
title: 'ACSD-52613: Cache und Indizes werden ohne Aktualisierungen aktualisiert'
description: Wenden Sie den Patch ACSD-52613 an, um das Adobe Commerce-Problem zu beheben, bei dem der Cache und die Indizes aktualisiert werden, wenn bis  [!DNL REST API] keine Aktualisierungen an den Elementen "Inventory_source"vorgenommen werden.
feature: REST
role: Admin
exl-id: 18878161-da4e-4d6e-9f58-706519f837f8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-52613: Cache und Indizes werden aktualisiert, auch wenn keine Updates verfügbar sind

Der Patch ACSD-52613 behebt das Problem, bei dem das Adobe Commerce-Problem auftritt, bei dem der Cache und die Indizes aktualisiert werden, wenn keine Aktualisierungen von `Inventory_source` -Elementen durch [!DNL REST API] vorgenommen werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-52613. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Cache und Indizes werden aktualisiert, wenn von [!DNL REST API] keine Aktualisierungen an `Inventory_source` Elementen vorgenommen werden.

<u>Voraussetzungen</u>:

Installierte Inventarmodule

<u>Zu reproduzierende Schritte</u>:

1. Ändern Sie den Entwicklermodus auf `debug.log`.
1. Bereiten Sie die Importdatei mit 100 Produkten vor - import.csv:

   ```
   sku    name    product_type    attribute_set_code    price
   test_sku_1    test_sku_1    simple    Default    10
   test_sku_2    test_sku_2    simple    Default    10
   ...
   test_sku_100    test_sku_100    simple    Default    10
   ```

1. Importieren von Produkten aus `import.csv`
1. Erstellen Sie ein neues Lager und eine neue Quelle mit den Namen **test_stock** und **test_source**.
1. Weisen Sie der Website einen neuen Bestand zu und weisen Sie ihm eine Quelle zu.
1. Erstellen Sie eine neue Integration mit Zugriff auf alle, aktivieren Sie sie und kopieren Sie das Zugriffstoken.
1. Wechseln Sie zu **Stores** > **Konfiguration** > **Dienste** > **OAuth** > **Verbrauchereinstellungen** und aktivieren Sie die Option **Zulassen von OAuth-Zugriffstoken als eigenständige Trägertoken**.
1. Leeren Sie den Cache.
1. Setzen Sie Indexer auf **Aktualisiert durch Zeitplan**
1. API-Anfrage ausführen

   `POST ../rest/V1/inventory/source-items`

   Verwendung dieses Zeichens als Haupttext

   ```
   {
    "sourceItems": [
        {
            "sku": "test_sku_1",
            "source_code": "test_source",
            "quantity": 24,
            "status": 1
        },
        {
            "sku": "test_sku_2",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_3",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_4",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_5",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_6",
            "source_code": "test_source",
            "quantity": 19,
            "status": 1
        },
        {
            "sku": "test_sku_7",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_8",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_9",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_10",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_11",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_12",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_13",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_14",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_15",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_16",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_17",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_18",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_19",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_20",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_21",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_22",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_23",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_24",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_25",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_26",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_27",
            "source_code": "test_source",
            "quantity": 13,
            "status": 1
        },
        {
            "sku": "test_sku_28",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_29",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_30",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_31",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_32",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_33",
            "source_code": "test_source",
            "quantity": 49,
            "status": 1
        },
        {
            "sku": "test_sku_34",
            "source_code": "test_source",
            "quantity": 12,
            "status": 1
        },
        {
            "sku": "test_sku_35",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_36",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_37",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_38",
            "source_code": "test_source",
            "quantity": 10,
            "status": 1
        },
        {
            "sku": "test_sku_39",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_40",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_41",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_42",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_43",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_44",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_45",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_46",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_47",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_48",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_49",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_50",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_51",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_52",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_53",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_54",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_55",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_56",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_57",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_58",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_59",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_60",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_61",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_62",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_63",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_64",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_65",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_66",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_67",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_68",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_69",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_70",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_71",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_72",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_73",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_74",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_75",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_76",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_77",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_78",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_79",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_80",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_81",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_82",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_83",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_84",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_85",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_86",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_87",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_88",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_89",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_90",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_91",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_92",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_93",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_94",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_95",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_96",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_97",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_98",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_99",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_100",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        }
    ]
   }
   ```

1. Entfernen Sie alle Protokolle aus `var/log`
1. Führen Sie die [!DNL REST API] -Anfrage erneut aus.
1. Überprüfen Sie die `var/log/debug.log`.

<u>Erwartete Ergebnisse</u>:

Der Cache sollte nicht bereinigt werden und die Indizes sollten nach der zweiten Ausführung nicht ausgeführt werden, da nichts geändert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die `var/log/debug.log` enthält den Eintrag, der sich auf die Cache-Löschung bezieht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
