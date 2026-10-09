---
title: 'ACSD-63286: Produkte, die einem freigegebenen Katalog zugewiesen sind, müssen manuell neu indiziert werden'
description: Wenden Sie den Patch ACSD-63286 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte, die über die API einem freigegebenen Katalog zugewiesen sind, erst dann in der Storefront angezeigt werden, wenn eine manuelle Neuindizierung ausgeführt wird.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '424'
ht-degree: 0%
---
# ACSD-63286: Produkte, die einem freigegebenen Katalog zugewiesen sind, müssen manuell neu indiziert werden

Mit dem Patch ACSD-63286 wird das Problem behoben, dass Produkte, die einem freigegebenen Katalog über die API zugewiesen sind, erst dann in der Storefront angezeigt werden, wenn eine manuelle Neuindizierung ausgeführt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-63286. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Produkte über die API einem freigegebenen Katalog zugewiesen werden, werden sie nach Ausführung der partiellen Indexer- und Cron-Verbraucheraufträge nicht mehr im Frontend angezeigt. Sie werden jedoch nach einer manuellen vollständigen Neuindizierung angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie [!DNL RabbitMQ] als Warteschlangendienst ein.
1. Erstellen Sie einen freigegebenen Katalog und weisen Sie ihm eine Firma zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es einer Kategorie zu.
1. Führen Sie eine partielle Neuindizierung aus.

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Verwenden Sie die folgende API-Anfrage, um das erstellte Produkt dem freigegebenen `pub/rest/all/V1/sharedCatalog/<id>/assignProducts` zuzuweisen:

   ```json
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Führen Sie den folgenden Cron aus, um die Warteschlangen zu leeren und die partielle Neuindizierung auszuführen.

   ```shell
   bin/magento cron:run --group=consumers
   ```

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Melden Sie sich beim Frontend als Firmenbenutzer an.
1. Überprüfen Sie die Frontend-Kategorieseite. Die neu zugewiesenen Produkte sind nicht sichtbar.
1. Führen Sie eine manuelle Neuindizierung aus:

   ```shell
   bin/magento index:reindex
   ```

<u>Erwartete Ergebnisse</u>:

Das Produkt wird im Frontend ohne manuelle Neuindizierung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird im Frontend nur nach manueller Neuindizierung angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
