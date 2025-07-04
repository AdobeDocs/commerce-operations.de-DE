---
title: 'ACP2E-3789: Mediendateien bei Produktaktualisierung über WebAPI dupliziert'
description: Wenden Sie den ACP2E-3789-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Produktaktualisierungen über die WebAPI doppelte Mediendateien enthalten, wenn eine Medien-ID bereitgestellt wird.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
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
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie ein Produkt über die Web-API mit einer Medien-ID aktualisieren, dupliziert das System Mediendateien, anstatt sie zu ersetzen. Dabei werden mit jedem API-Aufruf neue Dateien erstellt, was zu einer Bildauffüllung führt, die das `/pub/media/catalog/products/cache/`-Verzeichnis überlädt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt und fügen Sie ein Bild hinzu.
1. Rufen Sie Produktdetails mithilfe der REST-API unter `base_url/rest/V1/products/<sku>` ab.
1. Führen Sie eine PUT-Anfrage aus, um das Produkt zu aktualisieren, wobei der `media_gallery_entrie` unverändert bleibt (gleicher Bildname und Datei).
1. Überprüfen Sie das `pub/media/catalog/product/xx/yy` vor und nach dem Update.

<u>Erwartete Ergebnisse</u>:

Die Bilddatei wird ersetzt, wenn die Medien-ID in der Anfrage enthalten ist.

<u>Tatsächliche Ergebnisse</u>:

Das Bild wird mit einem neuen Namen (z. B. wb04-blue-1.jpg) dupliziert, was einen unnötigen Dateiaufbau verursacht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
