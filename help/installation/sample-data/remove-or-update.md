---
title: Beispieldatenmodule entfernen oder aktualisieren
description: Führen Sie diese Schritte aus, um Adobe Commerce-Beispieldatenmodule zu verwalten.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Beispieldatenmodule entfernen oder aktualisieren

In diesem Thema wird beschrieben, wie Sie:

* [Entfernen Sie Beispieldatenmodule](#remove-sample-data-modules) aus einer Adobe Commerce-Installation `composer.json`. Diese Option entfernt *nicht* Beispieldaten aus der Datenbank.

* [Vorbereiten der Aktualisierung von Beispieldaten](#prepare-to-update-sample-data) (z. B. vor der Aktualisierung der Magento-Anwendung).

## Beispieldatenmodule entfernen

Geben Sie den folgenden Befehl ein:

```bash
bin/magento sampledata:remove
```

Die vollständige Liste der Beispieldatenmodule lautet wie folgt:

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

## Vorbereiten der Aktualisierung von Beispieldaten

Mit diesem Befehl können Sie Beispieldaten aktualisieren, bevor Sie Adobe Commerce aktualisieren.

Geben Sie den folgenden Befehl ein, um Beispieldaten für die Aktualisierung vorzubereiten:

```bash
bin/magento sampledata:reset
```

Danach aktualisiert [die Anwendung](../tutorials/uninstall.md#update-the-application).
