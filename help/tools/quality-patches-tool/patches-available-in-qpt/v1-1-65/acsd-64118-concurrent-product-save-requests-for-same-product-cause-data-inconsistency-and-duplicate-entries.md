---
title: 'ACSD-64118: Gleichzeitige Produktspeicherungsanfragen für dasselbe Produkt führen zu Dateninkonsistenz und doppelten Einträgen'
description: Wenden Sie den ACSD-64118 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem gleichzeitige Anfragen zum Speichern und Aktualisieren desselben Produkts zu Dateninkonsistenz oder doppelten Produkten führen.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: e014645e-72b2-4b3d-8b44-3daca502c950
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '419'
ht-degree: 0%
---
# ACSD-64118: Gleichzeitige Produktspeicherungsanfragen für dasselbe Produkt führen zu Dateninkonsistenz und doppelten Einträgen

Mit dem Patch ACSD-64118 wird das Problem behoben, dass gleichzeitige Anfragen zum Speichern und Aktualisieren desselben Produkts zu Dateninkonsistenz oder doppelten Produkten führen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-64118. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Gleichzeitige Anfragen zum Speichern und Aktualisieren desselben Produkts führen zu Dateninkonsistenzen oder doppelten Produkten.

<u>Schritte zur Reproduktion</u>:

1. Einrichten von Multi-Prozess-Lösungen für Verbraucher in `env.php`:

   ```text
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Fügen Sie der Haupt-Website einen zusätzlichen Store und eine neue Storeview hinzu.
1. Senden Sie eine Massen-API-Anfrage an den standardmäßigen StoreReview-Endpunkt `/rest/default/async/bulk/V1/products` mit der folgenden Payload, um ein Produkt zu erstellen:

   ```text
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Verwenden Sie dieselbe Payload, um eine Massen-API-Anfrage an den neuen StoreReview-Endpunkt `/rest/store/async/bulk/V1/products` zu senden und so das Produkt zu aktualisieren.
1. Cache leeren.
1. Cron-Aufträge ausführen.
1. Überprüfen Sie die `catalog_product_entity` Tabelle auf Einträge für das Produkt aus den vorherigen Schritten.

<u>Erwartete Ergebnisse</u>:

* Die `catalog_product_entity` Tabelle sollte einen einzelnen Eintrag für die Produkt-SKU enthalten.
* Die erste REST-API-Anfrage sollte einen Datenbankeintrag erstellen, und alle nachfolgenden Anfragen sollten diesen Datenbankeintrag aktualisieren.

<u>Tatsächliche Ergebnisse</u>:

In der `catalog_product_entity` Tabelle sind mehrere Einträge für dieselbe SKU vorhanden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
