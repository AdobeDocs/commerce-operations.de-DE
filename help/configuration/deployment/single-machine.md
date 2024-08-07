---
title: Einzelmaschinenimplementierung
description: Erfahren Sie, wie Sie mithilfe der Befehlszeile Updates auf einem Produktionsserver für Commerce bereitstellen.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# Einzelmaschinenbereitstellung

In diesem Thema finden Sie Anweisungen zur Bereitstellung von Updates für Commerce auf einem Produktionsserver mithilfe der Befehlszeile. Dieser Prozess gilt für technische Benutzer, die für Geschäfte verantwortlich sind, die auf einem einzigen Computer mit einigen Designs und Gebietsschemas ausgeführt werden.

## Annahmen

- Sie haben Commerce mit [Composer](../../installation/composer.md) installiert.
- Sie wenden Aktualisierungen direkt auf den Server an.

>[!WARNING]
>
>Dieses Handbuch gilt nicht, wenn Sie mit `git clone` Commerce installiert haben.
>Beitragende Entwickler sollten [dieses Handbuch][install] verwenden, um ihre Commerce-Installation zu aktualisieren.

## Implementierungsschritte

1. Melden Sie sich bei Ihrem Produktionsserver als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.

1. Ändern Sie den Ordner in den Commerce-Basisordner:

   ```bash
   cd <Commerce base directory>
   ```

1. Aktivieren Sie den Wartungsmodus mit dem Befehl:

   ```bash
   bin/magento maintenance:enable
   ```

1. Wenden Sie mithilfe des folgenden Befehlsmusters Aktualisierungen auf Commerce oder seine Komponenten an:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **package**: Der Name des Pakets, das Sie aktualisieren möchten.

   Beispiel:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: Die Zielversion des Pakets, das Sie aktualisieren möchten.

1. Komponenten mit Composer aktualisieren:

   ```bash
   composer update
   ```

1. Datenbankschema und Daten aktualisieren:

   ```bash
   bin/magento setup:upgrade
   ```

1. Kompilieren Sie den Code:

   ```bash
   bin/magento setup:di:compile
   ```

1. Statischen Inhalt bereitstellen:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```

1. Wartungsmodus beenden:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
