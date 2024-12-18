---
title: Sprachpakete deinstallieren
description: Führen Sie die folgenden Schritte aus, um ein Adobe Commerce-Sprachpaket zu deinstallieren.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Sprachpakete deinstallieren

In diesem Abschnitt wird beschrieben, wie Sie ein oder mehrere Sprachpakete deinstallieren, wobei Sie optional den Code der Sprachpakete aus dem Dateisystem einschließen. Sie können zunächst Sicherungskopien erstellen, damit Sie die Daten später wiederherstellen können.

Mit diesem Befehl werden *nur* Sprachpakete deinstalliert, die in `composer.json` angegeben sind, d. h. Sprachpakete, die als Composer-Pakete bereitgestellt werden. Wenn Ihr Sprachpaket kein Composer-Paket ist, müssen Sie es manuell deinstallieren, indem Sie den Sprachpaketcode aus dem Dateisystem entfernen.

Sie können Sicherungskopien jederzeit mit dem Befehl [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) wiederherstellen.

Befehlsverwendung:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Der Deinstallationsbefehl für Sprachpakete führt die folgenden Aufgaben aus:

1. Prüft auf Abhängigkeiten; wenn ja, wird der Befehl beendet.

   Um dies zu umgehen, können Sie entweder alle abhängigen Sprachpakete gleichzeitig deinstallieren oder die abhängigen Sprachpakete zuerst deinstallieren.

1. Wenn `--backup code` angegeben ist, sichern Sie das Dateisystem (ohne `var`- und `pub/static`) in `var/backups/<timestamp>_filesystem.tgz`
1. Entfernt Sprachpaketdateien aus der Codebasis mithilfe von `composer remove`.
1. Löscht den Cache.

Wenn Sie beispielsweise versuchen, ein Sprachpaket zu deinstallieren, von dem ein anderes Sprachpaket abhängig ist, wird die folgende Meldung angezeigt:

```
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Eine Alternative besteht darin, beide Sprachpakete nach dem Sichern der Code-Basis zu deinstallieren:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Meldungen ähnlich der folgenden werden angezeigt:

```
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
