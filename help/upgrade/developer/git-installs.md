---
title: Aktualisieren einer Git-basierten Installation
description: Aktualisieren Sie eine Adobe Commerce-Installation, die Sie aus einem Git-Repository geklont haben.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# Aktualisieren einer Git-basierten Installation

In diesem Abschnitt wird beschrieben, wie beitragende Entwicklerinnen und Entwickler Adobe Commerce aktualisieren können, ohne es erneut zu installieren. Wenn Sie kein beitragender Entwickler sind, lesen Sie [Durchführen eines Upgrades](../implementation/perform-upgrade.md).

So aktualisieren Sie, wenn Sie Entwickler sind:

{{$include /help/_includes/server-login.md}}

1. Speichern Sie alle Änderungen, die Sie an der `composer.json`-Datei vorgenommen haben, da sie in den nächsten Schritten überschrieben wird.

1. Erstellen Sie eine Sicherungskopie Ihrer `composer.json`.

   ```shell
   cp composer.json composer.json.old
   ```

1. Aktualisieren Sie Ihr lokales Repository, um den neuesten Code zu erhalten:

   ```shell
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Wenn `git pull origin develop` fehlschlägt, siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360034229872).

1. Vergleichen und Zusammenführen der `composer.json.old` mit der `composer.json`.

1. Auflösen von Abhängigkeiten und Schreiben exakter Versionen in die `composer.lock`.

   ```shell
   composer update
   ```

1. Datenbank aktualisieren:

   ```shell
   bin/magento setup:upgrade
   ```

1. Cache leeren:

   ```shell
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
