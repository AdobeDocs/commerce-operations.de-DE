---
title: Beispieldatenmodule entfernen oder aktualisieren
description: Führen Sie diese Schritte aus, um Adobe Commerce und Magento Open Source-Beispieldatenmodule zu verwalten.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Beispieldatenmodule entfernen oder aktualisieren

In diesem Thema wird beschrieben, wie Sie:

* [Beispieldatenmodule entfernen](#remove-sample-data-modules) über eine Installation von Adobe Commerce oder Magento Open Sourcen `composer.json`. Diese Option *not* Beispieldaten aus der Datenbank entfernen.

* [Vorbereiten der Aktualisierung von Beispieldaten](#prepare-to-update-sample-data) (z. B. vor der Aktualisierung der Magento-Anwendung).

## Beispieldatenmodule entfernen

Geben Sie den folgenden Befehl ein:

```bash
bin/magento sampledata:remove
```

Die vollständige Liste der Beispieldatenmodule lautet wie folgt:

Adobe Commerce und Magento Open Source:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

Nur Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## Vorbereiten der Aktualisierung von Beispieldaten

Mit diesem Befehl können Sie Beispieldaten aktualisieren, bevor Sie Adobe Commerce oder die Magento Open Source aktualisieren.

Geben Sie den folgenden Befehl ein, um Beispieldaten für die Aktualisierung vorzubereiten:

```bash
bin/magento sampledata:reset
```

Danach [Anwendung aktualisieren](../tutorials/uninstall.md#update-the-application).
