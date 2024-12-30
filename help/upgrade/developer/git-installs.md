---
title: Aktualisieren einer Git-basierten Installation
description: Aktualisieren Sie eine Adobe Commerce-Installation, die Sie aus einem Git-Repository geklont haben.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Aktualisieren einer Git-basierten Installation

In diesem Abschnitt wird beschrieben, wie beitragende Entwicklerinnen und Entwickler Adobe Commerce aktualisieren können, ohne es erneut zu installieren. Wenn Sie kein beitragender Entwickler sind, lesen Sie [Durchführen eines Upgrades](../implementation/perform-upgrade.md).

So aktualisieren Sie, wenn Sie Entwickler sind:

{{$include /help/_includes/server-login.md}}

1. Speichern Sie alle Änderungen, die Sie an der `composer.json`-Datei vorgenommen haben, da sie in den nächsten Schritten überschrieben wird.

1. Erstellen Sie eine Sicherungskopie Ihrer `composer.json`.

   ```bash
   cp composer.json composer.json.old
   ```

1. Aktualisieren Sie Ihr lokales Repository, um den neuesten Code zu erhalten:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Wenn `git pull origin develop` fehlschlägt, siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360034229872).

1. Vergleichen und Zusammenführen der `composer.json.old` mit der `composer.json`.

1. Auflösen von Abhängigkeiten und Schreiben exakter Versionen in die `composer.lock`.

   ```bash
   composer update
   ```

1. Datenbank aktualisieren:

   ```bash
   bin/magento setup:upgrade
   ```

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```
