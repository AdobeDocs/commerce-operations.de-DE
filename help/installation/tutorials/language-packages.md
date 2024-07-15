---
title: Sprachpakete deinstallieren
description: Führen Sie die folgenden Schritte aus, um ein Sprachpaket für Adobe Commerce zu deinstallieren.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Sprachpakete deinstallieren

In diesem Abschnitt wird beschrieben, wie Sie ein oder mehrere Sprachpakete deinstallieren, einschließlich des Codes der Sprachpakete vom Dateisystem. Sie können zunächst Backups erstellen, um die Daten später wiederherzustellen.

Mit diesem Befehl werden Sprachpakete deinstalliert, die in `composer.json` angegeben sind, d. h. Sprachpakete, die als Composer-Pakete bereitgestellt werden. ** Wenn Ihr Sprachpaket kein Composer-Paket ist, müssen Sie es manuell deinstallieren, indem Sie den Sprachpaketcode aus dem Dateisystem entfernen.

Mit dem Befehl [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) können Sie jederzeit Backups wiederherstellen.

Befehlsverwendung:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Der Befehl zum Deinstallieren des Sprachpakets führt die folgenden Aufgaben aus:

1. Prüft auf Abhängigkeiten; wenn ja, wird der Befehl beendet.

   Um dies zu umgehen, können Sie entweder alle abhängigen Sprachpakete gleichzeitig deinstallieren oder die abhängigen Sprachpakete zuerst deinstallieren.

1. Wenn `--backup code` angegeben ist, sichern Sie das Dateisystem (außer den Verzeichnissen `var` und `pub/static`) auf `var/backups/<timestamp>_filesystem.tgz`.
1. Entfernt Sprachpaketdateien mit `composer remove` aus der Codebasis.
1. Löscht den Cache.

Wenn Sie beispielsweise versuchen, ein Sprachpaket zu deinstallieren, von dem ein anderes Sprachpaket abhängig ist, wird die folgende Meldung angezeigt:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Eine Alternative besteht darin, beide Sprachpakete nach der Sicherung der Codebase zu deinstallieren:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Meldungen, die der folgenden Anzeige ähneln:

```terminal
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
