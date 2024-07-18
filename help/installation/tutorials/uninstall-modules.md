---
title: Module deinstallieren
description: Führen Sie die folgenden Schritte aus, um ein Adobe Commerce-Modul zu deinstallieren.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Module deinstallieren

In diesem Abschnitt wird beschrieben, wie Sie ein oder mehrere Module deinstallieren. Bei der Deinstallation können Sie optional den Code, das Datenbankschema und die Datenbankdaten der Module entfernen. Sie können zunächst Backups erstellen, um die Daten später wiederherzustellen.

Sie sollten ein Modul nur deinstallieren, wenn Sie sicher sind, dass Sie es nicht verwenden werden. Anstatt ein Modul zu deinstallieren, können Sie es deaktivieren, wie unter [Module aktivieren oder deaktivieren](manage-modules.md) beschrieben.

>[!NOTE]
>
>Dieser Befehl überprüft, ob nur Abhängigkeiten in der Datei &quot;`composer.json`&quot;deklariert wurden. Wenn Sie ein Modul deinstallieren, das in der `composer.json` -Datei definiert ist, deinstalliert dieser Befehl das Modul, ohne nach Abhängigkeiten zu suchen. __ Mit diesem Befehl wird _nicht_ ausgeführt, der Code des Moduls wird jedoch aus dem Dateisystem entfernt. Sie müssen Dateisystemwerkzeuge verwenden, um den Code des Moduls zu entfernen (z. B. `rm -rf <path to module>`). Alternativ können Sie [disable](manage-modules.md) non-Composer-Module deaktivieren.

Befehlsverwendung:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Dabei gibt `{ModuleName}` den Modulnamen im Format `<VendorName>_<ModuleName>` an. Beispielsweise lautet der Name des Kundenmoduls `Magento_Customer`. Um eine Liste der Modulnamen zu erhalten, geben Sie `magento module:status` ein.

Der Befehl zur Deinstallation des Moduls führt die folgenden Aufgaben aus:

1. Stellt sicher, dass die angegebenen Module in der Codebasis vorhanden sind und Pakete sind, die von Composer installiert werden.

   Dieser Befehl funktioniert _nur_ mit Modulen, die als Composer-Pakete definiert sind.

1. Prüft mit anderen Modulen auf Abhängigkeiten und beendet den Befehl, wenn es nicht erfüllte Abhängigkeiten gibt.

   Um dies zu umgehen, können Sie entweder alle Module gleichzeitig deinstallieren oder die abhängigen Module zuerst deinstallieren.

1. Fordert eine Bestätigung an, um fortzufahren.
1. Setzt den Speicher in den Wartungsmodus.
1. Verarbeitet die folgenden Befehlsoptionen.

   | Option | Bedeutung | Name und Speicherort der Sicherungsdatei |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Sichert das Dateisystem (außer den Verzeichnissen `var` und `pub/static`). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Sichert das Verzeichnis pub/media . | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Sichert die Datenbank. | `var/backups/<timestamp>_db.gz` |

1. Wenn `--remove-data` angegeben ist, entfernen Sie das Datenbankschema und die Daten, die in den `Uninstall` -Klassen des Moduls definiert sind.

   Ruft für jedes angegebene Modul, das deinstalliert werden soll, die `uninstall` -Methode in ihrer `Uninstall`-Klasse auf. Diese Klasse muss von [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php) übernehmen.

1. Entfernt die angegebenen Module aus der Datenbanktabelle `setup_module`.
1. Entfernt die angegebenen Module aus der Modulliste in der [Bereitstellungskonfiguration](../../configuration/reference/deployment-files.md).
1. Entfernt Code mit `composer remove` aus der Codebasis.

   >[!NOTE]
   >
   >Beim Deinstallieren eines Moduls wird _always_ mit `composer remove` ausgeführt. Die Option `--remove-data` entfernt Datenbankdaten und Schemas, die durch die `Uninstall` -Klasse des Moduls definiert sind.

1. Löscht den Cache.
1. Aktualisierungen generierter Klassen.
1. Wenn `--clear-static-content` angegeben ist, löscht [generierte statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md).
1. Der Speicher wird nicht mehr im Wartungsmodus ausgeführt.

Wenn Sie beispielsweise versuchen, ein Modul zu deinstallieren, von dem ein anderes Modul abhängig ist, wird die folgende Meldung angezeigt:

```
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Eine Alternative besteht darin, beide Module nach dem Sichern des Moduldateisystems, der `pub/media`-Dateien und der Datenbanktabellen zu deinstallieren, wobei das Datenbankschema oder die Daten des Moduls jedoch _nicht_ entfernt werden:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Meldungen, die der folgenden Anzeige ähneln:

```
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Fehler werden angezeigt, wenn Sie versuchen, ein Modul mit einer Abhängigkeit von einem anderen Modul zu deinstallieren. In diesem Fall können Sie ein Modul nicht deinstallieren. Sie müssen beide deinstallieren.

## Zurücksetzen des Dateisystems, der Datenbank oder der Mediendateien

Verwenden Sie den folgenden Befehl, um die Codebase in dem Zustand wiederherzustellen, in dem Sie sie gesichert haben:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Wobei `<filename>` der Name der Sicherungsdatei im Verzeichnis `<app_root>/var/backups` ist. Um eine Liste der Sicherungsdateien anzuzeigen, geben Sie `magento info:backups:list` ein.

>[!WARNING]
>
>Mit diesem Befehl werden die angegebenen Dateien oder die Datenbank gelöscht, bevor sie wiederhergestellt werden. Beispielsweise löscht die Option `--media-file` Medien-Assets im Verzeichnis `pub/media` , bevor sie aus der angegebenen Rollback-Datei wiederhergestellt werden. Vergewissern Sie sich, dass Sie das Dateisystem oder die Datenbank, die Sie beibehalten möchten, nicht geändert haben, bevor Sie diesen Befehl verwenden.

>[!NOTE]
>
>Um eine Liste der verfügbaren Backup-Dateien anzuzeigen, geben Sie `magento info:backups:list` ein

Dieser Befehl führt die folgenden Aufgaben aus:

1. Setzt den Speicher in den Wartungsmodus.
1. Überprüft den Namen der Sicherungsdatei.
1. Wenn Sie eine Code-Rollback-Datei angeben:

   a. Stellt sicher, dass die Rollback-Zielspeicherorte schreibbar sind (beachten Sie, dass die Ordner `pub/static` und `var` ignoriert werden).

   b. Löscht alle Dateien und Ordner im Installationsverzeichnis der Anwendung.

   c. Extrahiert die Archivdatei an die Zielspeicherorte.

1. Wenn Sie eine Datenbank-Rollback-Datei angeben:

   a. Legt die gesamte Datenbank ab.

   b. Stellt die Datenbank mithilfe der Datenbanksicherung wieder her.

1. Wenn Sie eine Medien-Rollback-Datei angeben:

   a. Stellt sicher, dass die Rollback-Zielspeicherorte schreibbar sind.

   b. Löscht alle Dateien und Ordner unter `pub/media`

   c. Extrahiert die Archivdatei an die Zielspeicherorte.

1. Der Speicher wird nicht mehr im Wartungsmodus ausgeführt.

Um beispielsweise eine Sicherung des Codes (d. h. des Dateisystems) wiederherzustellen, geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein:

* Liste der Backups anzeigen:

  ```bash
  magento info:backups:list
  ```

* Wiederherstellen einer Dateisicherung mit dem Namen `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Meldungen, die der folgenden Anzeige ähneln:

  ```
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Um den Befehl `magento` erneut auszuführen, ohne die Verzeichnisse zu ändern, müssen Sie möglicherweise `cd pwd` eingeben.
