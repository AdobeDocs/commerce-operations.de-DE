---
title: Bereitstellung auf einem Computer
description: Erfahren Sie, wie Sie Aktualisierungen für Commerce auf einem Produktionsserver mithilfe der Befehlszeile bereitstellen.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---

# Bereitstellung auf einem Computer

Dieses Thema enthält Anweisungen zum Bereitstellen von Aktualisierungen für Commerce auf einem Produktionsserver mithilfe der Befehlszeile. Dieser Prozess gilt für technische Benutzer, die für Stores verantwortlich sind, die auf einem einzelnen Computer mit einigen installierten Designs und Gebietsschemata ausgeführt werden.

## Annahmen

- Sie haben Commerce mit [Composer](../../installation/composer.md) installiert.
- Aktualisierungen werden direkt auf den Server angewendet.

>[!WARNING]
>
>Dieses Handbuch gilt nicht, wenn Sie `git clone` zur Installation von Commerce verwendet haben.
>Entwicklerinnen und Entwickler, die an der [ mitwirken, sollten dieses Handbuch ](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies), um ihre Commerce-Installation zu aktualisieren.

## Bereitstellungsschritte

1. Melden Sie sich bei Ihrem Produktions-Server als oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).

1. Wechseln Sie in das Commerce-Basisverzeichnis:

   ```shell
   cd <Commerce base directory>
   ```

1. Aktivieren Sie den Wartungsmodus mithilfe des Befehls :

   ```shell
   bin/magento maintenance:enable
   ```

1. Wenden Sie mithilfe des folgenden Befehlsmusters Aktualisierungen auf Commerce oder seine Komponenten an:

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **package**: Der Name des Pakets, das Sie aktualisieren möchten.

   Beispiel:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: Die Zielversion des Pakets, das Sie aktualisieren möchten.

1. Komponenten mit Composer aktualisieren:

   ```shell
   composer update
   ```

1. Datenbankschema und Daten aktualisieren:

   ```shell
   bin/magento setup:upgrade
   ```

1. Kompilieren Sie den Code:

   ```shell
   bin/magento setup:di:compile
   ```

1. Statischen Inhalt bereitstellen:

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. Cache leeren:

   ```shell
   bin/magento cache:clean
   ```

1. Wartungsmodus beenden:

   ```shell
   bin/magento maintenance:disable
   ```

