---
title: 'ACP2E-3789: Mediendateien bei Produktaktualisierung über WebAPI dupliziert'
description: Wenden Sie den ACP2E-3789-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Produktaktualisierungen über die WebAPI doppelte Mediendateien enthalten, wenn eine Medien-ID bereitgestellt wird.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 1eaa8ed0-fde6-47c4-9339-8f5e7bce7b19
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '380'
ht-degree: 0%
---
# ACP2E-3789: Mediendateien bei Produktaktualisierung über WebAPI dupliziert

Mit dem Patch ACP2E-3789 wird das Problem behoben, dass Produktaktualisierungen über WebAPI doppelte Mediendateien enthalten, wenn eine Medien-ID bereitgestellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID lautet ACP2E-3789. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie ein Produkt über die Web-API mit einer Medien-ID aktualisieren, dupliziert das System Mediendateien, anstatt sie zu ersetzen. Dabei werden mit jedem API-Aufruf neue Dateien erstellt, was zu einer Bildauffüllung führt, die das `/pub/media/catalog/products/cache/`-Verzeichnis überlädt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt und fügen Sie ein Bild hinzu.
1. Rufen Sie Produktdetails mithilfe der REST-API unter `base_url/rest/V1/products/<sku>` ab.
1. Führen Sie eine PUT-Anfrage durch, um das Produkt zu aktualisieren, wobei der `media_gallery_entrie` unverändert bleibt (gleicher Bildname und Datei).
1. Überprüfen Sie das `pub/media/catalog/product/xx/yy` vor und nach dem Update.

<u>Erwartete Ergebnisse</u>:

Die Bilddatei wird ersetzt, wenn die Medien-ID in der Anfrage enthalten ist.

<u>Tatsächliche Ergebnisse</u>:

Das Bild wird mit einem neuen Namen (z. B. wb04-blue-1.jpg) dupliziert, was einen unnötigen Dateiaufbau verursacht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
