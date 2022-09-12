---
title: Einzelmaschinenimplementierung
description: Erfahren Sie, wie Sie mithilfe der Befehlszeile Updates für Commerce auf einem Produktionsserver bereitstellen.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Einzelmaschinenbereitstellung

Dieses Thema enthält Anweisungen zur Bereitstellung von Aktualisierungen für Commerce auf einem Produktionsserver mithilfe der Befehlszeile. Dieser Prozess gilt für technische Benutzer, die für Geschäfte verantwortlich sind, die auf einem einzigen Computer mit einigen Designs und Gebietsschemas ausgeführt werden.

## Annahmen

- Sie haben Commerce mithilfe von installiert. [Verfasser].
- Sie wenden Aktualisierungen direkt auf den Server an.

>[!WARNING]
>
>Dieses Handbuch gilt nicht, wenn Sie `git clone` , um Commerce zu installieren.
>Beitragende Entwickler sollten [diesem Handbuch][install] , um ihre Commerce-Installation zu aktualisieren.

## Implementierungsschritte

1. Melden Sie sich bei Ihrem Produktionsserver an oder wechseln Sie zu dem [Dateisysteminhaber][file-owner].

1. Wechseln Sie zum Basisverzeichnis &quot;Commerce&quot;:

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
[composer]: ../../installation/composer.md
[file-owner]: ../../installation/prerequisites/file-system/overview.md
