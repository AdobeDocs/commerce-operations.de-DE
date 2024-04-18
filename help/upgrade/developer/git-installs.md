---
title: Aktualisierung einer Git-basierten Installation
description: Aktualisieren Sie eine Adobe Commerce-Installation, die Sie aus einem Git-Repository geklont haben.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Aktualisierung einer Git-basierten Installation

In diesem Thema wird erläutert, wie ein beitragender Entwickler Adobe Commerce aktualisieren kann, ohne es erneut zu installieren. Wenn Sie kein Entwickler sind, lesen Sie [Durchführen eines Upgrades](../implementation/perform-upgrade.md).

So aktualisieren Sie, wenn Sie ein Entwickler sind:

{{$include /help/_includes/server-login.md}}

1. Speichern Sie alle Änderungen, die Sie an der `composer.json` -Datei, da sie durch die nächsten Schritte überschrieben wird.

1. Erstellen Sie eine Sicherungskopie Ihrer `composer.json` -Datei.

   ```bash
   cp composer.json composer.json.old
   ```

1. Aktualisieren Sie Ihr lokales Repository, um den neuesten Code zu erhalten:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Wenn `git pull origin develop` schlägt fehl, siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360034229872).

1. Diff und Merge Ihre `composer.json.old` -Datei mit der `composer.json` -Datei.

1. Abhängigkeiten auflösen und exakte Versionen in die `composer.lock` -Datei.

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
