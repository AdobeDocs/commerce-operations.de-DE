---
title: Entfernen oder Aktualisieren von Beispieldatenmodulen
description: Führen Sie diese Schritte aus, um Beispieldatenmodule für Adobe Commerce zu verwalten.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Entfernen oder Aktualisieren von Beispieldatenmodulen

In diesem Thema wird Folgendes erläutert:

* [Entfernen von Beispieldatenmodulen](#remove-sample-data-modules) aus einer Adobe Commerce-`composer.json`. Mit dieser Option werden *Beispieldaten* der Datenbank entfernt.

* [Bereiten Sie die Aktualisierung der Beispieldaten vor](#prepare-to-update-sample-data) (z. B. vor der Aktualisierung des Magento-Programms).

## Entfernen von Beispieldatenmodulen

Geben Sie den folgenden Befehl ein:

```bash
bin/magento sampledata:remove
```

Die vollständige Liste der Beispieldatenmodule folgt:

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

## Vorbereiten der Aktualisierung der Beispieldaten

Mit diesem Befehl können Sie Beispieldaten aktualisieren, bevor Sie Adobe Commerce aktualisieren.

Um Beispieldaten für die Aktualisierung vorzubereiten, geben Sie den folgenden Befehl ein:

```bash
bin/magento sampledata:reset
```

Aktualisieren Sie anschließend [die Anwendung](../tutorials/uninstall.md#update-the-application).
