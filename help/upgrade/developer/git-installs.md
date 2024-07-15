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

In diesem Thema wird erläutert, wie ein beitragender Entwickler Adobe Commerce aktualisieren kann, ohne es erneut zu installieren. Wenn Sie kein Entwickler sind, lesen Sie [Durchführen einer Aktualisierung](../implementation/perform-upgrade.md).

So aktualisieren Sie, wenn Sie ein Entwickler sind:

{{$include /help/_includes/server-login.md}}

1. Speichern Sie alle Änderungen, die Sie an der Datei `composer.json` vorgenommen haben, da sie bei den nächsten Schritten überschrieben werden.

1. Erstellen Sie eine Sicherung Ihrer `composer.json` -Datei.

   ```bash
   cp composer.json composer.json.old
   ```

1. Aktualisieren Sie Ihr lokales Repository, um den neuesten Code zu erhalten:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Wenn `git pull origin develop` fehlschlägt, lesen Sie [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360034229872).

1. Verwechseln Sie Ihre `composer.json.old`-Datei und führen Sie sie mit der Datei `composer.json` zusammen.

1. Lösen Sie Abhängigkeiten auf und schreiben Sie exakte Versionen in die Datei &quot;`composer.lock`&quot;.

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
