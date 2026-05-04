---
title: Aktualisieren einer Git-basierten Installation
description: Aktualisieren Sie eine Adobe Commerce-Installation, die Sie aus einem Git-Repository geklont haben.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
