---
title: Aktualisierung einer Git-basierten Installation
description: Aktualisieren Sie eine Adobe Commerce- oder Magento Open Source-Installation, die Sie aus einem Git-Repository geklont haben.
source-git-commit: 7bcfbc4483f4b6d4c1a5e852adbd1cd81bc136b7
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Aktualisierung einer Git-basierten Installation

In diesem Thema wird erläutert, wie ein beitragender Entwickler Adobe Commerce oder Magento Open Source aktualisieren kann, ohne sie neu zu installieren. Wenn Sie kein Entwickler sind, lesen Sie [Durchführen eines Upgrades](../implementation/perform-upgrade.md).

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

1. Diff und Mergen Sie Ihre `composer.json.old` -Datei mit `composer.json` -Datei.

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
